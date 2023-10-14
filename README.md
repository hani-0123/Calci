# Calci
Calculator
import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.io.*;
/**
*Author:E.Hanija
*/
public class ComplexCalculator implements ActionListener
{
 BufferedWriter file;
 // Creating JFrame instances for our calculator and
 // previous results frames
 JFrame f=new JFrame();
 JFrame o;
 // Creating some appropriate labels by creating JFrame
 // instances
 JLabel l1=new JLabel("First Number");
4. IMPLEMENTATION

 JLabel l2=new JLabel("Second Number");
 JLabel l3=new JLabel("Result");
 JLabel l4=new JLabel("real:");
 JLabel l5=new JLabel("imaginary:");
 JLabel l6=new JLabel("real:");
 JLabel l7=new JLabel("imaginary:");
 JLabel l8=new JLabel("Previous Results");
 // Creating JTextField instances to take input from
 // our GUI application and displaying the output
 JTextField t1=new JTextField();
 JTextField t2=new JTextField();
 JTextField t3=new JTextField();
 JTextField t4=new JTextField();
 JTextField t5=new JTextField();
 // Creating buttons to perform Complex Arithmetic
 // operations, deletion, exit functionalities and
 // navigating through our GUI application
 JButton b1=new JButton("Add");
 JButton b2=new JButton("Sub");
 JButton b3=new JButton("Mul");
 JButton b4=new JButton("Div");
 JButton b5=new JButton("Previous Results");
 JButton b6=new JButton("exit");
 JButton b7=new JButton("Back");
 JButton b8=new JButton("Delete Results");
 JButton b9=new JButton("Open Notepad");
 ComplexCalculator() {
 // Setting the dimensions and position of our
 // labels
 l1.setBounds(50,100,100,20);
 l2.setBounds(50,140,100,20);
 l3.setBounds(50,180,100,20);
 l4.setBounds(200,100,30,20);
 l5.setBounds(320,100,60,20);
 l6.setBounds(200,140,30,20);

 l7.setBounds(320,140,60,20);
 l8.setBounds(50, 50,150,20);
 // Setting the dimensions and position of our
 // text fields
 t1.setBounds(240,100,50,20);
 t2.setBounds(390,100,50,20);
 t3.setBounds(240,140,50,20);
 t4.setBounds(390,140,50,20);
 t5.setBounds(200,180,120,20);
 // Setting the dimensions and positions of our
 // various buttons
 b1.setBounds(50,250,60,20);
 b2.setBounds(130,250,60,20);
 b3.setBounds(210,250,60,20);
 b4.setBounds(290,250,60,20);
 b5.setBounds(350,180,120,20);
 b6.setBounds(370,250,60,20);
 b7.setBounds(50,500,100,20);
 b8.setBounds(170,500,150,20);
 b9.setBounds(340,500,130,20);
 // Adding our components to the JFrame instance f
 f.add(l1);
 f.add(l2);
 f.add(l3);
 f.add(l4);
 f.add(l5);
 f.add(l6);
 f.add(l7);
 f.add(t1);
 f.add(t2);
 f.add(t3);
 f.add(t4);
 f.add(t5);
 f.add(b1);

 f.add(b2);
 f.add(b3);
 f.add(b4);
 f.add(b5);
 f.add(b6);
 // Adding action listener to our buttons
 b1.addActionListener(this);
 b2.addActionListener(this);
 b3.addActionListener(this);
 b4.addActionListener(this);
 b5.addActionListener(this);
 b6.addActionListener(this);
 b7.addActionListener(this);
 b8.addActionListener(this);
 b9.addActionListener(this);
 // Setting the properties of our frame and
 // setting its visibility to true
 f.setLayout(null);
 f.setVisible(true);
 f.setTitle("Complex GUI");
 f.getContentPane().setBackground(new Color(151, 189, 189));
 f.setSize(600,600);
 }
 /**
 * The actionPerformed method is the overridden method of
 * action listener interface and it is called when any action
 * is performed on the GUI application and since the parameter
 * ActionEvent e therefore it only carries information of mouse
 * clicks and button press
 *
 * @param e It is the parameter that carries information
 * that invoked the actionPerformed method
 */
 @Override
 public void actionPerformed(ActionEvent e)
 {
 // calc variable is used to store the result
 // of each calculations
 String calc = "";

 // r1, i1, r2, i2 are used to store the complex
 // numbers
 int r1, i1, r2, i2;
 // If else-if else block to handle the events on
 // the basis of which button was pressed
 // Exits the program when 'exit' button is pressed
 if(e.getSource()==b6)
 {
 System.exit(0);
 }
 // Takes us to back Calculator screen when 'back'
 // button is pressed
 else if(e.getSource()==b7)
 {
 o.dispose();
 f.setVisible(true);
 }
 // Deletes the content of file when 'Delete Results'
 // is pressed
 else if(e.getSource()==b8)
 {
 o.dispose();
 try {
 // Deletes the content of file when we open it in write mode
 BufferedWriter bw = new BufferedWriter(new
FileWriter("C:\\Users\\shiva\\JavaPrograms\\AWT programming\\output.txt"));
 bw.close();
 } catch (IOException fileNotFoundException) {
 fileNotFoundException.printStackTrace();
 }
 // Setting the Source of current event 'e' to b5 and calling
 // actionPerformed to display the blank file in JTextArea
 e.setSource(b5);
 actionPerformed(e);

 }
 // Opens our text file in notepad using exec method
 else if(e.getSource() == b9) {
 Runtime runtime = Runtime.getRuntime();
 try {
 runtime.exec("C:\\Windows\\notepad.exe C:\\Users\\shiva\\JavaPrograms\\AWT
programming\\output.txt");
 } catch (IOException ioException) {
 ioException.printStackTrace();
 }
 }
 // It gets disposes the Calculator frame and displays
 // the frame with previous results when 'Previous Results'
 // or 'Delete Results' buttons are pressed
 else if(e.getSource()==b5)
 {
 // Creating new frame and disposing the frame 'f'
 // and setting its properties
 o = new JFrame();
 f.dispose();
 o.setLayout(null);
 o.setTitle("Complex GUI");
 o.getContentPane().setBackground(new Color(151, 189, 189));
 o.setSize(600,600);
 // Creating and setting properties of text area to display
 // previous results
 JTextArea textArea = new JTextArea ("");
 textArea.setBounds(50, 70, 420,400);
 textArea.setVisible(true);
 // Adding components to frame 'o'
 o.add(b7);
 o.add(b8);
 o.add(b9);
 o.add(l8);
 o.add(textArea);
 o.setVisible (true);

 // Appending the content of our file to the text area
 try {
 FileReader fr = new FileReader("C:\\Users\\shiva\\JavaPrograms\\AWT
programming\\output.txt");
 try (BufferedReader br = new BufferedReader(fr)) {
 String i;
 while ((i = br.readLine()) != null) {
 textArea.append(i + "\n");
 }
 }
 fr.close();
 } catch (IOException fileNotFoundException) {
 fileNotFoundException.printStackTrace();
 }
 }
 else {
 // Parsing inputs from the text fields
 r1 = Integer.parseInt(t1.getText());
 i1 = Integer.parseInt(t2.getText());
 r2 = Integer.parseInt(t3.getText());
 i2 = Integer.parseInt(t4.getText());
 // Performing Complex Arithmetic operations
 // according to the button pressed
 // Performing addition operation
 if(e.getSource()==b1)
 {
 String res = ((r1+r2) + " + " + (i1 + i2) + " i");
 t5.setText(res);
 calc = r1 + " + " + i1 + "i + " + r2 + " + " + i2 +"i = " + res;
 }
 // Performing subtraction operation
 if(e.getSource()==b2)
 {
 String res = (r1-r2) + " + " + (i1 - i2) + " i";
 t5.setText(res);
 calc = r1 + " + " + i1 + "i - " + r2 + " + " + i2 +"i = " + res;
 }

 // Performing multiplication operation
 if(e.getSource()==b3)
 {
 String res = (r1*r2 - i1*i2) + " + " + (r1*i2 + r2*i1) + " i";
 t5.setText(res);
 calc = r1 + " + " + i1 + "i * " + r2 + " + " + i2 +"i = " + res;
 }
 // Performing division operation
 if(e.getSource()==b4) {
 int div = r2*r2 + i2*i2;
 String res = ((r1*r2 + i1*i2) + "/" + div) + " + " + ((-r1*i2 + r2*i1) + "/" + div) + " i";
 t5.setText(res);
 calc = r1 + " + " + i1 + "i / " + r2 + " + " + i2 +"i = " + res;
 }
 // Storing the result in 'calc' in a file named output.txt
 // by appending it in the new line
 try {
 file = new BufferedWriter(new FileWriter("C:\\Users\\shiva\\JavaPrograms\\AWT
programming\\output.txt", true));
 file.append(calc);
 file.append('\n');
 file.flush();
 file.close();
 } catch (IOException ioException) {
 ioException.printStackTrace();
 }
 }
 }
 /**
 * This is the main method used to invoke the
 * ComplexCalculator() constructor and hence
 * starts the GUI application
 * @param args Unused.
 * @exception IOException On input error.
 * @see IOException
 */
 public static void main(String[] args)  {

 // Calling the ComplexCalculator() constructor to
 // start our GUI application
 new ComplexCalculator();
 }
}
