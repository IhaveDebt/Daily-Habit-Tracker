import java.util.*;

public class HabitTracker {
    static class Habit {
        String name;
        int streak;

        Habit(String name) {
            this.name = name;
            this.streak = 0;
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        List<Habit> habits = new ArrayList<>();

        System.out.println("📅 Daily Habit Tracker");
        while (true) {
            System.out.println("\n1. Add Habit");
            System.out.println("2. Mark Habit as Done");
            System.out.println("3. View Habits & Streaks");
            System.out.println("4. Exit");
            System.out.print("Choose: ");
            int choice = scanner.nextInt();
            scanner.nextLine(); // consume newline

            switch (choice) {
                case 1:
                    System.out.print("Enter habit name: ");
                    String habitName = scanner.nextLine();
                    habits.add(new Habit(habitName));
                    System.out.println("✅ Habit added!");
                    break;
                case 2:
                    if (habits.isEmpty()) {
                        System.out.println("⚠ No habits yet!");
                        break;
                    }
                    System.out.print("Enter habit number: ");
                    for (int i = 0; i < habits.size(); i++) {
                        System.out.println((i + 1) + ". " + habits.get(i).name);
                    }
                    int habitIndex = scanner.nextInt() - 1;
                    if (habitIndex >= 0 && habitIndex < habits.size()) {
                        habits.get(habitIndex).streak++;
                        System.out.println("🔥 Streak increased!");
                    } else {
                        System.out.println("❌ Invalid habit number.");
                    }
                    break;
                case 3:
                    if (habits.isEmpty()) {
                        System.out.println("⚠ No habits yet!");
                    } else {
                        System.out.println("\n📊 Your Habits:");
                        for (Habit h : habits) {
                            System.out.println(h.name + " — Streak: " + h.streak + " days");
                        }
                    }
                    break;
                case 4:
                    System.out.println("👋 Goodbye!");
                    return;
                default:
                    System.out.println("❌ Invalid choice.");
            }
        }
    }
}
