# OOP
import java.util.ArrayList;
import java.util.Date;

// Part 1 - Base class
class HealthProfessional {
    private int ID;
    private String name;
    private String specialty; // For everyone

    public HealthProfessional() {
    }

    public HealthProfessional(int ID, String name, String specialty) {
        this.ID = ID;
        this.name = name;
        this.specialty = specialty;
    }

    public void printDetails() {
        System.out.println("ID: " + ID + ", Name: " + name + ", Specialty: " + specialty);
    }

    // Getters and Setters
    public int getID() {
        return ID;
    }

    public String getName() {
        return name;
    }

    public String getSpecialty() {
        return specialty;
    }
}
