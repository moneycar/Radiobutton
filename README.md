import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class RadioButtonDemo extends JFrame implements ActionListener {

    private JRadioButton birdButton, catButton, dogButton, rabbitButton, pigButton;
    private ButtonGroup group;
    private JLabel petLabel;
    private ImageIcon birdIcon, catIcon, dogIcon, rabbitIcon, pigIcon;

    public RadioButtonDemo() {
        setTitle("Pet Selector");
        setSize(400, 300);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new FlowLayout());

        // Load images from URLs
        birdIcon = loadImage("https://example.com/bird.png");
        catIcon = loadImage("https://example.com/cat.png");
        dogIcon = loadImage("https://example.com/dog.png");
        rabbitIcon = loadImage("https://example.com/rabbit.png");
        pigIcon = loadImage("https://example.com/pig.png");

        // Create radio buttons
        birdButton = new JRadioButton("Bird");
        catButton = new JRadioButton("Cat");
        dogButton = new JRadioButton("Dog");
        rabbitButton = new JRadioButton("Rabbit");
        pigButton = new JRadioButton("Pig");

        // Create button group
        group = new ButtonGroup();
        group.add(birdButton);
        group.add(catButton);
        group.add(dogButton);
        group.add(rabbitButton);
        group.add(pigButton);

        // Add action listeners
        birdButton.addActionListener(this);
        catButton.addActionListener(this);
        dogButton.addActionListener(this);
        rabbitButton.addActionListener(this);
        pigButton.addActionListener(this);

        // Create a label to display the selected pet image
        petLabel = new JLabel();

        // Add components to the frame
        add(birdButton);
        add(catButton);
        add(dogButton);
        add(rabbitButton);
        add(pigButton);
        add(petLabel);

        // Set the initial pet image, if loaded
        if (pigIcon != null) {
            petLabel.setIcon(pigIcon); // Start with Pig image
        }

        setVisible(true);
    }

    // Method to load image icons with error handling
    private ImageIcon loadImage(String path) {
        ImageIcon icon = new ImageIcon(path);
        if (icon.getImageLoadStatus() != MediaTracker.COMPLETE) {
            System.out.println("Error loading image: " + path);
            return null; // Return null if the image failed to load
        }
        return icon;
    }

    // Handle radio button selections
    public void actionPerformed(ActionEvent e) {
        // Check the source of the action and set the icon accordingly, if loaded
        if (e.getSource() == birdButton && birdIcon != null) {
            petLabel.setIcon(birdIcon);
        } else if (e.getSource() == catButton && catIcon != null) {
            petLabel.setIcon(catIcon);
        } else if (e.getSource() == dogButton && dogIcon != null) {
            petLabel.setIcon(dogIcon);
        } else if (e.getSource() == rabbitButton && rabbitIcon != null) {
            petLabel.setIcon(rabbitIcon);
        } else if (e.getSource() == pigButton && pigIcon != null) {
            petLabel.setIcon(pigIcon);
        }
    }

    public static void main(String[] args) {
        new RadioButtonDemo();
    }
}# Radiobutton
