package advancedjava;

import javax.swing.*;
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;

public class Main {
	
    public static void main(String[] args) {
        // This prompts for the name. 
        String fileName = JOptionPane.showInputDialog("Enter the file name (e.g., Markus_Rodgers_Resident_Picture_Identification_Policy_2025-14-1):");

        if (fileName == null || fileName.isEmpty()) {
            JOptionPane.showMessageDialog(null, "File name cannot be empty.");
            return;
        }

        // This asks the user if they want to update or create a new file. 
        String[] options = {"Update", "Create New File"};
        int choice = JOptionPane.showOptionDialog(null,
                "Are you updating a file or creating a new one?",
                "File Action",
                JOptionPane.DEFAULT_OPTION,
                JOptionPane.QUESTION_MESSAGE,
                null,
                options,
                options[0]);

        if (choice == -1) {
            JOptionPane.showMessageDialog(null, "No action selected.");
            return;
        }

        String action = options[choice];

        // This gathers the details that will be placed on the .txt file. 
        String residentName = JOptionPane.showInputDialog("Enter Resident Name:");
        String residentSignature = JOptionPane.showInputDialog("Enter Resident Signature:");
        String date = JOptionPane.showInputDialog("Enter Date:");
        String guardianName = JOptionPane.showInputDialog("Enter Guardian Name:");
        String guardianSignature = JOptionPane.showInputDialog("Enter Guardian Signature:");

        // Here the content that was prompted is generated. 
        String content = "Resident Name: " + residentName + "\n"
                + "Resident Signature: " + residentSignature + "   Date: " + date + "\n"
                + "Guardian Name: " + guardianName + "\n"
                + "Guardian Signature: " + guardianSignature + "   Date: " + date;

        // Here the directory to save the file is determined. 
        String baseDir = System.getProperty("user.home") + File.separator + "Desktop" + File.separator + "Electronic Filing System" + File.separator + "Admin Filing System" + File.separator + "Book 1";

        // Create a new folder based on the file name for new files
        File targetDirectory;
        if (action.equals("Create New File")) {
            targetDirectory = new File(baseDir + File.separator + fileName);
            if (!targetDirectory.exists()) {
                boolean folderCreated = targetDirectory.mkdirs();
                if (!folderCreated) {
                    JOptionPane.showMessageDialog(null, "Failed to create directory: " + targetDirectory.getPath());
                    return;
                }
            }
        } else {
            targetDirectory = new File(baseDir); // Use existing directory for updates.
        }

        // Save the file inside the target directory.
        try {
            String filePath = targetDirectory.getPath() + File.separator + fileName + ".txt";
            FileWriter writer = new FileWriter(filePath);
            writer.write(content);
            writer.close();

            // Show the file path.
            JOptionPane.showMessageDialog(null, "File saved successfully at:\n" + filePath);
            System.out.println("File saved at: " + filePath);
        } catch (IOException e) {
            JOptionPane.showMessageDialog(null, "Error saving file: " + e.getMessage());
        }
    }
}
