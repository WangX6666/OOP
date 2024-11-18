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

// Main class
public class AssignmentOne {
    public static void main(String[] args) {
        // Part 3 – Using classes and objects
        GeneralPractitioner gp1 = new GeneralPractitioner(1, "Dr. Smith", "General Health", "Family Medicine");
        GeneralPractitioner gp2 = new GeneralPractitioner(2, "Dr. Johnson", "General Health", "Pediatrics");
        GeneralPractitioner gp3 = new GeneralPractitioner(3, "Dr. Williams", "General Health", "Geriatrics");

        OtherHealthProfessional ohp1 = new OtherHealthProfessional(4, "Dr. Brown", "Dietitian", "Nutrition");
        OtherHealthProfessional ohp2 = new OtherHealthProfessional(5, "Dr. Davis", "Surgeon", "Orthopedics");

        gp1.printDetails();
        System.out.println("------------------------------");
        gp2.printDetails();
        System.out.println("------------------------------");
        gp3.printDetails();
        System.out.println("------------------------------");
        ohp1.printDetails();
        System.out.println("------------------------------");
        ohp2.printDetails();
        System.out.println("------------------------------");

        // Part 5 – Collection of appointments
        ArrayList<Appointment> appointments = new ArrayList<>();

        appointments.add(createAppointment("John Doe", "1234567890", "08:00", gp1));
        appointments.add(createAppointment("Jane Smith", "0987654321", "10:00", ohp1));
        appointments.add(createAppointment("Alice Johnson", "1112223333", "14:30", gp2));
        appointments.add(createAppointment("Bob Brown", "4445556666", "16:00", ohp2));

        printExistingAppointments(appointments);
        System.out.println("------------------------------");

        cancelBooking(appointments, "1234567890");
        printExistingAppointments(appointments);
    }

    private static void cancelBooking(ArrayList<Appointment> appointments, String mobilePhone) {
        Appointment appointmentToCancel = null;
        for (Appointment appointment : appointments) {
            if (appointment.getMobilePhone().equals(mobilePhone)) {
                appointmentToCancel = appointment;
                break;
            }
        }
        if (appointmentToCancel != null) {
            appointments.remove(appointmentToCancel);
            System.out.println("Appointment cancelled for mobile phone: " + mobilePhone);
        } else {
            System.out.println("No appointment found for mobile phone: " + mobilePhone);
        }
    }
}
