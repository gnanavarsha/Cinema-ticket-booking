import java.util.Scanner;

class MovieReservationSystem {
    static final int MAX_ROWS = 5;
    static final int MAX_SEATS_PER_ROW = 10;
    static final int MAX_MOVIES = 6;
    static final int MAX_LOCATIONS = 5;
    static final int MAX_SNACKS = 4;
    static final int MAX_RESERVATIONS = 10;
    static final int TICKET_PRICE = 200;

    static int[][] seats = new int[MAX_ROWS][MAX_SEATS_PER_ROW];

    static String[] movies = {
        "LEO", "Jailer", "Irugapatru", "Jigarthanda Doublex", "Adiye", "Mark Antony"
    };

    static String[] locations = {
        "Trichy-LA", "Chennai-IMAX", "Madurai-INOX", "Coimbatore-IMAX", "Salem-PVR"
    };

    static String[] snacks = {
        "Popcorn", "Soda", "Candy", "None"
    };

    static class Reservation {
        String movie;
        String location;
        String snack;
        int row;
        int seat;
        int numTickets;
        int totalCost;

        Reservation(String movie, String location, String snack, int row, int seat, int numTickets, int totalCost) {
            this.movie = movie;
            this.location = location;
            this.snack = snack;
            this.row = row;
            this.seat = seat;
            this.numTickets = numTickets;
            this.totalCost = totalCost;
        }
    }

    static Reservation[] reservations = new Reservation[MAX_RESERVATIONS];
    static int reservationCount = 0;

    public static void initializeSeats() {
        for (int i = 0; i < MAX_ROWS; i++) {
            for (int j = 0; j < MAX_SEATS_PER_ROW; j++) {
                seats[i][j] = 0;
            }
        }
    }

    public static void displayMovies() {
        System.out.println("Available Movies:");
        for (int i = 0; i < MAX_MOVIES; i++) {
            System.out.println((i + 1) + ". " + movies[i]);
        }
    }

    public static void displayLocations() {
        System.out.println("Available Theater Locations:");
        for (int i = 0; i < MAX_LOCATIONS; i++) {
            System.out.println((i + 1) + ". " + locations[i]);
        }
    }

    public static void displaySnacks() {
        System.out.println("Available Snacks:");
        for (int i = 0; i < MAX_SNACKS; i++) {
            System.out.println((i + 1) + ". " + snacks[i]);
        }
    }

    public static void displayAvailableSeats(int movieIndex) {
        System.out.println("Available Seats for " + movies[movieIndex] + ":");
        for (int i = 0; i < MAX_ROWS; i++) {
            System.out.print("Row " + (i + 1) + ": ");
            for (int j = 0; j < MAX_SEATS_PER_ROW; j++) {
                if (seats[i][j] == 0) {
                    System.out.print((j + 1) + " ");
                }
            }
            System.out.println();
        }
    }

    public static void displayReservations() {
        if (reservationCount == 0) {
            System.out.println("You have no reservations.");
        } else {
            System.out.println("Your Reservations:");
            for (int i = 0; i < reservationCount; i++) {
                Reservation res = reservations[i];
                System.out.println("**");
                System.out.println("Reservation " + (i + 1) + ": " + res.movie + " - " + res.location +
                                   " - Row " + res.row + ", Seat " + res.seat + " - Snack: " + res.snack +
                                   " - Tickets: " + res.numTickets + " - Total Cost: Rs. " + res.totalCost);
                System.out.println("**");
            }
        }
    }

    public static boolean processPayment() {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Enter your credit card number: ");
        String cardNumber = scanner.next();
        System.out.print("Enter your CVV: ");
        String cvv = scanner.next();

        if (cardNumber.length() == 16 && cvv.length() == 3) {
            System.out.println("**");
            System.out.println("Payment successful! Your seats are reserved.");
            System.out.println("Total Cost: Rs. " + reservations[reservationCount - 1].totalCost);
            System.out.println("**");
            return true;
        } else {
            System.out.println("Payment failed. Please check your card information and try again.");
            return false;
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        initializeSeats();

        while (true) {
            System.out.println("\n1. Display Available Movies\n2. Select a Movie\n3. Reserve Seats\n4. View Reservations\n5. Select Theater Location\n6. Select Snacks\n7. Make Payment\n8. Exit\nEnter your choice: ");
            int choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    displayMovies();
                    break;
                case 2: {
                    int selectedMovie;
                    displayMovies();
                    System.out.print("Select a movie by entering its number: ");
                    selectedMovie = scanner.nextInt();

                    if (selectedMovie < 1 || selectedMovie > MAX_MOVIES) {
                        System.out.println("Invalid movie selection. Please choose a valid number.");
                    } else {
                        displayAvailableSeats(selectedMovie - 1);
                    }
                    break;
                }
                case 3: {
                    int selectedMovie;
                    displayMovies();
                    System.out.print("Select a movie by entering its number: ");
                    selectedMovie = scanner.nextInt();

                    if (selectedMovie < 1 || selectedMovie > MAX_MOVIES) {
                        System.out.println("Invalid movie selection. Please choose a valid number.");
                    } else {
                        displayAvailableSeats(selectedMovie - 1);

                        System.out.print("Enter the number of tickets to be booked: ");
                        int numTickets = scanner.nextInt();

                        if (numTickets < 1) {
                            System.out.println("Invalid number of tickets. Please book at least one ticket.");
                            break;
                        }

                        displayLocations();
                        System.out.print("Select a theater location by entering its number: ");
                        int locationChoice = scanner.nextInt();
                        String selectedLocation;
                        if (locationChoice < 1 || locationChoice > MAX_LOCATIONS) {
                            System.out.println("Invalid location selection. Please choose a valid number.");
                            break;
                        } else {
                            selectedLocation = locations[locationChoice - 1];
                        }

                        for (int i = 0; i < numTickets; i++) {
                            System.out.print("Enter the row and seat number you want to reserve (e.g., 1 3): ");
                            int row = scanner.nextInt();
                            int seat = scanner.nextInt();

                            if (row < 1 || row > MAX_ROWS || seat < 1 || seat > MAX_SEATS_PER_ROW) {
                                System.out.println("Invalid row or seat number. Please choose valid values.");
                                break;
                            } else if (seats[row - 1][seat - 1] == 1) {
                                System.out.println("Seat " + seat + " in Row " + row + " is already reserved. Please choose another seat.");
                                break;
                            } else {
                                seats[row - 1][seat - 1] = 1;

                                displaySnacks();
                                System.out.print("Select a snack by entering its number: ");
                                int snackChoice = scanner.nextInt();
                                String selectedSnack;
                                if (snackChoice < 1 || snackChoice > MAX_SNACKS) {
                                    System.out.println("Invalid snack selection. Please choose a valid number.");
                                    seats[row - 1][seat - 1] = 0;
                                    break;
                                } else {
                                    selectedSnack = snacks[snackChoice - 1];
                                }

                                reservations[reservationCount] = new Reservation(movies[selectedMovie - 1], selectedLocation, selectedSnack, row, seat, numTickets, numTickets * TICKET_PRICE);
                                reservationCount++;

                                System.out.println("Reserved " + numTickets + " seat(s) in Row " + row + " for " + movies[selectedMovie - 1] + " at " + selectedLocation + " with " + selectedSnack + " successfully!");
                            }
                        }
                    }
                    break;
                }
                case 4:
                    displayReservations();
                    break;
                case 5:
                    displayLocations();
                    break;
                case 6:
                    displaySnacks();
                    break;
                case 7:
                    if (reservationCount == 0) {
                        System.out.println("You don't have any reservations. Please reserve seats first.");
                    } else {
                        boolean paymentSuccess = processPayment();
                        if (paymentSuccess) {
                            reservationCount = 0;
                            initializeSeats();
                        }
                    }
                    break;
                case 8:
                    System.out.println("Thank you. Exiting the program.");
                    scanner.close();
                    return;
                default:
                    System.out.println("Invalid choice. Please enter a valid option.");
            }
        }
    }
}
