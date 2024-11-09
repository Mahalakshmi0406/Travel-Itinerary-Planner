import java.util.ArrayList;
import java.util.List;
import java.util.Scanner;

// Class representing a single travel destination
class Destination {
    private String name;
    private String date;
    private String accommodation;
    private List<String> activities;

    public Destination(String name, String date) {
        this.name = name;
        this.date = date;
        this.accommodation = "";
        this.activities = new ArrayList<>();
    }

    // Add an activity to the destination
    public void addActivity(String activity) {
        activities.add(activity);
    }

    // Set accommodation details
    public void setAccommodation(String accommodation) {
        this.accommodation = accommodation;
    }

    @Override
    public String toString() {
        StringBuilder sb = new StringBuilder();
        sb.append("Destination: ").append(name).append("\n");
        sb.append("Date: ").append(date).append("\n");
        sb.append("Accommodation: ").append(accommodation.isEmpty() ? "Not set" : accommodation).append("\n");
        sb.append("Activities: ");
        if (activities.isEmpty()) {
            sb.append("None");
        } else {
            for (String activity : activities) {
                sb.append(activity).append(", ");
            }
            sb.setLength(sb.length() - 2); // Remove last comma
        }
        sb.append("\n");
        return sb.toString();
    }
}

// Class representing the entire itinerary
class Itinerary {
    private List<Destination> destinations;

    public Itinerary() {
        destinations = new ArrayList<>();
    }

    // Add a new destination to the itinerary
    public void addDestination(String name, String date) {
        destinations.add(new Destination(name, date));
    }

    // Find a destination by name
    public Destination getDestination(String name) {
        for (Destination destination : destinations) {
            if (destination.toString().contains(name)) {
                return destination;
            }
        }
        return null;
    }

    // Remove a destination by name
    public boolean removeDestination(String name) {
        return destinations.removeIf(destination -> destination.toString().contains(name));
    }

    // Display the full itinerary
    public void viewItinerary() {
        if (destinations.isEmpty()) {
            System.out.println("Your itinerary is empty.");
        } else {
            for (Destination destination : destinations) {
                System.out.println(destination);
                System.out.println("-------------");
            }
        }
    }
}

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Itinerary itinerary = new Itinerary();

        while (true) {
            System.out.println("Travel Itinerary Planner");
            System.out.println("1. Add a Destination");
            System.out.println("2. View Itinerary");
            System.out.println("3. Add Activity to a Destination");
            System.out.println("4. Set Accommodation for a Destination");
            System.out.println("5. Remove Destination");
            System.out.println("6. Exit");
            System.out.print("Choose an option: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // Consume the newline character

            if (choice == 1) {
                // Add a new destination
                System.out.print("Enter destination name: ");
                String name = scanner.nextLine();
                System.out.print("Enter the travel date (e.g., 2024-11-05): ");
                String date = scanner.nextLine();
                itinerary.addDestination(name, date);
                System.out.println("Destination added successfully.");
            } else if (choice == 2) {
                // View the full itinerary
                itinerary.viewItinerary();
            } else if (choice == 3) {
                // Add activity to a destination
                System.out.print("Enter the destination name: ");
                String destinationName = scanner.nextLine();
                Destination destination = itinerary.getDestination(destinationName);
                if (destination != null) {
                    System.out.print("Enter activity: ");
                    String activity = scanner.nextLine();
                    destination.addActivity(activity);
                    System.out.println("Activity added.");
                } else {
                    System.out.println("Destination not found.");
                }
            } else if (choice == 4) {
                // Set accommodation for a destination
                System.out.print("Enter the destination name: ");
                String destinationName = scanner.nextLine();
                Destination destination = itinerary.getDestination(destinationName);
                if (destination != null) {
                    System.out.print("Enter accommodation details: ");
                    String accommodation = scanner.nextLine();
                    destination.setAccommodation(accommodation);
                    System.out.println("Accommodation set.");
                } else {
                    System.out.println("Destination not found.");
                }
            } else if (choice == 5) {
                // Remove a destination
                System.out.print("Enter the destination name to remove: ");
                String destinationName = scanner.nextLine();
                if (itinerary.removeDestination(destinationName)) {
                    System.out.println("Destination removed.");
                } else {
                    System.out.println("Destination not found.");
                }
            } else if (choice == 6) {
                // Exit the program
                System.out.println("Goodbye!");
                break;
            } else {
                System.out.println("Invalid choice. Please try again.");
            }
        }

        scanner.close();
    }
}
