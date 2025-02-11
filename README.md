# TravelBookingSystem.java
import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

public class TravelBookingSystem {
    private List<Travel> travels;
    private Scanner scanner;

    public TravelBookingSystem() {
        travels = new ArrayList<>();
        scanner = new Scanner(System.in);
    }

    public void run() {
        while (true) {
            System.out.println("Travel Booking System");
            System.out.println("1. Book Travel");
            System.out.println("2. View Travels");
            System.out.println("3. Exit");
            System.out.print("Choose an option: ");
            int option = scanner.nextInt();
            scanner.nextLine(); // Consume newline left-over

            switch (option) {
                case 1:
                    bookTravel();
                    break;
                case 2:
                    viewTravels();
                    break;
                case 3:
                    System.out.println("Exiting...");
                    return;
                default:
                    System.out.println("Invalid option. Please choose again.");
            }
        }
    }

    private void bookTravel() {
        System.out.print("Enter travel name: ");
        String name = scanner.nextLine();
        System.out.print("Enter travel destination: ");
        String destination = scanner.nextLine();
        System.out.print("Enter travel date: ");
        String date = scanner.nextLine();

        Travel travel = new Travel(name, destination, date);
        travels.add(travel);
        System.out.println("Travel booked successfully!");
    }

    private void viewTravels() {
        if (travels.isEmpty()) {
            System.out.println("No travels booked.");
        } else {
            System.out.println("Travels:");
            for (Travel travel : travels) {
                System.out.println(travel);
            }
        }
    }

    public static void main(String[] args) {
        TravelBookingSystem system = new TravelBookingSystem();
        system.run();
    }
}


*Travel.java*

public class Travel {
    private String name;
    private String destination;
    private String date;

    public Travel(String name, String destination, String date) {
        this.name = name;
        this.destination = destination;
        this.date = date;
    }

    @Override
    public String toString() {
        return "Travel{" +
                "name='" + name + '\'' +
                ", destination='" + destination + '\'' +
                ", date='" + date + '\'' +
                '}';
    }
}

