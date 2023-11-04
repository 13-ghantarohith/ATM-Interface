# OnlineExaminationSystem
import java.util.Scanner;
public class OnlineExamSystem {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        // Define questions and correct answers
        String[] questions = {
            "1. What is the capital of France?",
            "2. What is the largest planet in our solar system?",
            "3. Who wrote the play 'Romeo and Juliet'?"
        };
         String[] answers = {
            "Paris",
            "Jupiter",
            "William Shakespeare"
        };
    int totalQuestions = questions.length;
        int score = 0;
        System.out.println("Welcome to the Online Exam System!");
        for (int i = 0; i < totalQuestions; i++) {
            System.out.println(questions[i]);
            System.out.print("Your Answer: ");
            String userAnswer = scanner.nextLine();
              if (userAnswer.equalsIgnoreCase(answers[i])) {
                System.out.println("Correct!\n");
                score++;
            } else {
                System.out.println("Incorrect. The correct answer is: " + answers[i] + "\n");
            }
        }
         System.out.println("Your Score: " + score + " out of " + totalQuestions);
         // Determine pass or fail (e.g., passing score >= 2)
        if (score >= 2) {
            System.out.println("Congratulations! You have passed the exam.");
        } else {
            System.out.println("Sorry, you did not pass the exam.");
        }
         System.out.println("Thank you for using the Online Exam System!");
    }
}
