import java.util.*;

class Patient {
    int id;
    String name;
    int age;
    String disease;

    Patient(int id, String name, int age, String disease) {
        this.id = id;
        this.name = name;
        this.age = age;
        this.disease = disease;
    }
}

class Doctor {
    int id;
    String name;
    String specialty;

    Doctor(int id, String name, String specialty) {
        this.id = id;
        this.name = name;
        this.specialty = specialty;
    }
}

class Appointment {
    int id;
    int patientId;
    int doctorId;
    String date;

    Appointment(int id, int patientId, int doctorId, String date) {
        this.id = id;
        this.patientId = patientId;
        this.doctorId = doctorId;
        this.date = date;
    }
}

public class HospitalManagementSystem {
    static Scanner sc = new Scanner(System.in);
    static ArrayList<Patient> patients = new ArrayList<>();
    static ArrayList<Doctor> doctors = new ArrayList<>();
    static ArrayList<Appointment> appointments = new ArrayList<>();

    static int patientIdCounter = 1;
    static int doctorIdCounter = 1;
    static int appointmentIdCounter = 1;

    public static void addPatient() {
        System.out.print("Name: ");
        String name = sc.nextLine();
        System.out.print("Age: ");
        int age = Integer.parseInt(sc.nextLine());
        System.out.print("Disease: ");
        String disease = sc.nextLine();
        patients.add(new Patient(patientIdCounter++, name, age, disease));
    }

    public static void viewPatients() {
        for (Patient p : patients) {
            System.out.println(p.id + " " + p.name + " " + p.age + " " + p.disease);
        }
    }

    public static void addDoctor() {
        System.out.print("Name: ");
        String name = sc.nextLine();
        System.out.print("Specialty: ");
        String specialty = sc.nextLine();
        doctors.add(new Doctor(doctorIdCounter++, name, specialty));
    }

    public static void viewDoctors() {
        for (Doctor d : doctors) {
            System.out.println(d.id + " " + d.name + " " + d.specialty);
        }
    }

    public static void addAppointment() {
        System.out.print("Patient ID: ");
        int pid = Integer.parseInt(sc.nextLine());
        System.out.print("Doctor ID: ");
        int did = Integer.parseInt(sc.nextLine());
        System.out.print("Date: ");
        String date = sc.nextLine();
        appointments.add(new Appointment(appointmentIdCounter++, pid, did, date));
    }

    public static void viewAppointments() {
        for (Appointment a : appointments) {
            System.out.println(a.id + " Patient:" + a.patientId + " Doctor:" + a.doctorId + " Date:" + a.date);
        }
    }

    public static void main(String[] args) {
        while (true) {
            System.out.println("\n1 Add Patient\n2 View Patients\n3 Add Doctor\n4 View Doctors\n5 Add Appointment\n6 View Appointments\n7 Exit");
            String c = sc.nextLine();

            if (c.equals("1")) addPatient();
            else if (c.equals("2")) viewPatients();
            else if (c.equals("3")) addDoctor();
            else if (c.equals("4")) viewDoctors();
            else if (c.equals("5")) addAppointment();
            else if (c.equals("6")) viewAppointments();
            else if (c.equals("7")) break;
            else System.out.println("Invalid");
        }
    }
}
