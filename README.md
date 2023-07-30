# HotelManagement
ABSTRACT

This project aims at creating on Hotel Management System which can be used by Admin and Customers. The admin to advise/publish the availability of rooms in different hotels and customers are checking the availability of room in required hotel. Customers should be able to know the availability of the rooms on a particular date to reserve in hotel. They should be able to reserve the available rooms according to their need in advance to make their stay comfortable. The Admin hands the booking information of customers. The users can register and log into the system. The administrator will know the details of reservation and feedbacks. The hotel department maintain the seat availability and booking details in certain database. This project provides high security to Admin and user information.
The main objective of this project is to design a hotel management system for running a hotel business. The system should be as flexible as possible so that it can be used for different hotels. You have to find out which procedures hotels have used for different hotels. You have to find out which procedures hotels have and based on that information, you should create a system which makes it efficient. We need to find out how a hotel system works on the internet, use our own experience or directly talk to people in the hotel business. The more diverse the sources of information are, the better will be the resulting system.

INTRODUCTION

The project, Hotel Management System is an application that allows the hotel manager to handle all hotel activities online. And, the ability to manage various hotel bookings and rooms make this system very flexible and convenient. The hotel manager is a very busy person and does not have the time to sit and manage the entire activities manually on paper. This application gives him the power and flexibility to manage the entire system from a single online system. Hotel management project provides room bookings, checkouts and other necessary hotel management features. The system allows the manager to post available rooms in the system. Customers can book room online. Admin has the power of checking the customer’s booking request. The system is hence useful for both customers and managers to portable manage the hotel activities.
The mission is to facilitate easy management and administration of a hotel with capabilities to do Booking or reservations of the rooms, checkouts, complaints etc. using the automated hotel management software. One can keep detailed records or info on an unlimited amount of customers. This makes the Booking considerably faster. And thus helps the hotel in better management and reduce a lot of paper work as well as manpower.

SYSTEM REQUIREMENTS
 
HARDWARE: The hardware requirement actually depends on the version of java you want to use. The java 8 version requires following hardware configuration :
•	RAM : At least 128 MB
•	Disk Space : 124 MB for JRE, 2 MB for Java Update
•	Processor : Minimum Pentium 2 266 MHz processor

SOFTWARE: 
•	An editor like notepad, notepad++, TextPad, etc. for windows operating system and Vim, Notepadqq, Geany etc. for linux based operating system to write the java program. The notepad editor comes by default with windows operating system. The programmer can choose the editor of their choice.
•	 Any terminal like cmd, shell etc. to compile and run java program. By default CMD is available in windows OS while shell is available in linux based OS. Programmer can use PowerShell(if available) as well in windows to compile and run java programs.
•	 Java development kit(JDK). JDK is a software that is used in development and execution of java programs or applications. If JDK is not already installed in your system then download and install it(JDK as per your OS) first.

CODE

import java.io.*;
import java.util.InputMismatchException;
import java.util.Scanner;
import java.io.FileWriter;

class new1{
    public static void main(String[] args)throws IOException
    {
        Scanner s=new Scanner(System.in);
        File fch=new File("C:\\java\\HMS\\checkout.txt");
        File fc = new File("C:\\java\\HMS\\complains.txt");
        File f = new File("C:\\java\\HMS\\book.txt");
        // C:\java\HMS\book.txt
int x,n=50;
        int []av= new int[n];
        //room no's (0-49)
        for (int i = 0; i < n ; i++) {
            av[i]=i;
        }

        System.out.println("Welcome to Hotel Management System!\nWe are always here to help you :)");
        System.out.println("-Enter 1 for customer services\n-0 for manager services:");
        try {
            x = s.nextInt();

            switch (x) {
                case 1:
                    System.out.println("Dear customer, How can we help you?");
                    System.out.println("-Enter I for Hotel Booking or Check out\n-R for requests or complains:");
                    char ch;
                    Scanner sc = new Scanner(System.in);
                    ch = sc.next().charAt(0);

                    int rn;
                    switch (ch) {
                        case 'I':

                            char c;
                            System.out.println("enter B for booking\nenter C for checkout");

                            c = s.next().charAt(0);
                            if (c == 'B') {
                                String name;
                                String place;
                                int people;
                                System.out.println("Hotel Booking:");

                                int ac = 2500, pay, corr;
                                System.out.println("Pay Rs 2500");
                                pay = s.nextInt();
                                if (pay < 2500 && pay > 0) {
                                    System.out.println("please pay the left amount i.e " + (ac - pay));
                                    corr = s.nextInt();
                                    System.out.println("Transaction successful...");

                                } else if (pay == 2500) {
                                    System.out.println("Transaction successful...");

                                } else {
                                    System.out.println("invalid amount, Transaction unsuccessful...");
                                    return;
                                }

                                System.out.println("enter which room no you want to book (1-49):");
                                rn = s.nextInt();

                                System.out.println("enter your name:");
                                s.nextLine();
                                name = s.nextLine();

                                String book = "Room no " + rn + " is booked by " + name  ;

                                //append the content into the new file
                                FileWriter fw = new FileWriter("C:\\java\\HMS\\book.txt", true);
                                fw.write(book + "\n");
                                fw.close();

                                System.out.println("enter no of person:");
                                people = s.nextInt();
                                if (people > 3) {
                                    System.out.println("MORE THAN 3 PEOPLE NOT ALLOWED IN ONE ROOM");
                                } else if (people <= 0) {
                                    System.out.println("INVALID INPUT");
                                } else {
                                    System.out.println("Room booked Successfully");
                                }
                            } else if (c == 'C') {
                                System.out.println("Check out");

                                System.out.println("Enter your room no:");
                                int room;
                                room = s.nextInt();
                                String namech;
                                System.out.println("enter your name:");
                                s.nextLine();   //to handle buffer
                                namech = s.nextLine();

                                String avail_after_checkout = "Room no " + room + "is left by " + namech ;

                                FileWriter fwc = new FileWriter("C:\\java\\HMS\\checkout.txt", true);
                                fwc.write(avail_after_checkout);
                                fwc.close();
                                System.out.println("You are ready for check out :)");

                            } else {
                                System.out.println("Invalid character");
                            }

                            break;
                        case 'R':
                            System.out.println("Enter your Requests/Complains");
                            String comp;
                            s.nextLine();
                            comp = s.nextLine();
                            System.out.println("enter your name_roomno:");
                            String nrm;
                            nrm = s.next();
                            FileWriter fwcp = new FileWriter("C:\\java\\HMS\\complains.txt", true);
                            fwcp.write(comp + "...    " + nrm + "\n");
                            fwcp.close();
                            break;

                        default:
                            System.out.println("Invalid Character");

                    }
                    break;

                case 0:
                    System.out.println("welcome to staff services : )");
                    System.out.println("-Enter C for viewing complains\n-Enter A for checking Availibility of rooms:");
                    char st = s.next().charAt(0);
                    switch (st) {
                        case 'C':
                            System.out.println("Complains:");

                            Scanner scomp = new Scanner(fc);

                            while (scomp.hasNext()) {
                                System.out.println(scomp.nextLine());
                            }
                            break;
                        case 'A':
                            System.out.println("Avalibility (booked and checked out)");
                            Scanner scn = new Scanner(f);
                            while (scn.hasNext()) {
                                System.out.println(scn.nextLine());
                            }
                            System.out.println("\n");

                            Scanner scn2 = new Scanner(fch);
                            while (scn2.hasNext()) {
                                System.out.println(scn2.nextLine());
                            }

                            break;
                        default:
                            System.out.println("Invalid character");
                    }
            }
        }
catch (InputMismatchException e)
{
    System.out.println("ERROR: You are required to enter an integer.");
}
                System.out.println("\n\nThanks for using HMS : ");

}

}

CONCLUSION

The conclusion of this project is A Hotel management system is a computerized management system. This system keeps the records of hardware assets besides software of this organization. The proposed system will keep a track of Workers, Residents, Accounts and generation of report regarding the present status. This project is files based software that will help in storing, updating and retrieving the information through various user-friendly menu-driven modules. The project “Hotel Management System” is aimed to develop to maintain the day-to-day state of admission/Vacation of Residents, payment details etc. Main objective of this project is to provide solution for hotel to manage most their work using computerized process. This software application will help admin to handle customers information, room allocation details, payment details, billing information, etc. Detailed explanation about modules and design are provided in project documentation. The existing system is a manually maintained system. All the Hotel records are to be maintained for the details of each customer, Fee details, Room Allocation, etc. All these details are entered and retrieved manually, because of this there are many disadvantages like Time Consuming, updating process, inaccuracy of data. For avoiding this we introduced or proposed a new system in proposed system the computerized version of the existing system. provides easy and quick access over the data.



