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

// Part 2 – Child classes
class GeneralPractitioner extends HealthProfessional {
    private String practiceArea; // For Doctor

    public GeneralPractitioner() {
    }

    public GeneralPractitioner(int ID, String name, String specialty, String practiceArea) {
        super(ID, name, specialty);
        this.practiceArea = practiceArea;
    }

    @Override
    public void printDetails() {
        super.printDetails();
        System.out.println("Practice Area: " + practiceArea);
    }
}

class OtherHealthProfessional extends HealthProfessional {
    private String specificSkill; // another

    public OtherHealthProfessional() {
    }

    public OtherHealthProfessional(int ID, String name, String specialty, String specificSkill) {
        super(ID, name, specialty);
        this.specificSkill = specificSkill;
    }

    @Override
    public void printDetails() {
        super.printDetails();
        System.out.println("Specific Skill: " + specificSkill);
    }
}

// Part 4 – Class Appointment
class Appointment {
    private String patientName;
    private String mobilePhone;
    private String preferredTimeSlot;
    private HealthProfessional selectedDoctor;

    public Appointment() {
    }

    public Appointment(String patientName, String mobilePhone, String preferredTimeSlot, HealthProfessional selectedDoctor) {
        this.patientName = patientName;
        this.mobilePhone = mobilePhone;
        this.preferredTimeSlot = preferredTimeSlot;
        this.selectedDoctor = selectedDoctor;
    }

    public void printDetails() {
        System.out.println("Patient Name: " + patientName + ", Mobile Phone: " + mobilePhone + ", Time Slot: " + preferredTimeSlot);
        selectedDoctor.printDetails();
    }

    // Getters and Setters
    public String getMobilePhone() {
        return mobilePhone;
    }
}
