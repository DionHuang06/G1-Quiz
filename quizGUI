import javax.swing.*;
import javax.swing.border.Border;

import java.awt.*;
import java.io.File;
import java.io.*;
import java.util.Random;
//import java.awt.event.ActionEvent;
//import java.awt.event.ActionListener;
import java.text.*;
import java.awt.event.*;

public class quizGUI extends JFrame implements ActionListener{

  static JFrame quizframe = new JFrame("");
  
//Instance Variables
  JButton clickStart;
  JButton mute;
  JButton back;

  static JTextArea quesText;
  static JButton pausebutton;
  static JTextArea opt1Text;
  static JTextArea opt2Text;
  static JTextArea opt3Text;
  static JTextArea opt4Text;
  static JButton ques;
  static JButton opt1;
  static JButton opt2;
  static JButton opt3;
  static JButton opt4;
  static JButton next;
  static int answerstotal = 0;
  boolean clickable = false;
  int correct;
  static int order = 0;
  Randomized temp1;
  Question[] array1;

  
  
  
  static Dimension Max = Toolkit.getDefaultToolkit().getScreenSize();
  
  public quizGUI(){
	//Setting Dimensions of JFrame
	  quizframe.setMaximumSize(Max);
	  quizframe.setBounds(-10,30,2000,100);
	  quizframe.setSize(2000,450);
	  quizframe.setUndecorated(true);
	  quizframe.getContentPane().setBackground(new Color(247, 255, 252));
	  quizframe.setLayout(null);

    //Creating the quiz
    array1 = FileToQues(); //Grabs questions from .txt file
    shuffleArray(array1); //Shuffles the order of the questions
    Border emptyBorder = BorderFactory.createEmptyBorder();
    pausebutton = new JButton("Pause");
    pausebutton.setBackground(new Color(247, 255, 252));
    pausebutton.setForeground(new Color(70, 184, 141));
    pausebutton.setFocusPainted(false);
    pausebutton.setFont(new Font("Tahoma", Font.BOLD, 40));
    pausebutton.setBounds(-10,0,400,100);
    pausebutton.addActionListener(this);
    pausebutton.setBorder(emptyBorder);
    pausebutton.setContentAreaFilled(false);

    //Displaying the question on the GUI
    temp1 = displayQues(array1[order]); //Creating object with all variables(question, option1, option 2, option 3, option 4, correct answer, and image)
    	quizframe.add(pausebutton);
        //Question
        ques = temp1.getQuestion();
        //.add(ques);
        quesText = temp1.getQuesText();
        quizframe.add(quesText);
        //Option 1
        opt1 = temp1.getOp1(); //Grabbing variable of first option from the previously created object (temp1), repeat for each option.
        quizframe.add(opt1);
        opt1.addActionListener(this);
        opt1Text = temp1.getOpt1Text();
        quizframe.add(opt1Text);
        //Option 2
        opt2 = temp1.getOp2();
        quizframe.add(opt2);
        opt2.addActionListener(this);
        opt2Text = temp1.getOpt2Text();
        quizframe.add(opt2Text);
        //Option 3
        opt3 = temp1.getOp3();
        quizframe.add(opt3);
        opt3.addActionListener(this);
        opt3Text = temp1.getOpt3Text();
        quizframe.add(opt3Text);
        //Option 4
        opt4 = temp1.getOp4();
        quizframe.add(opt4);
        opt4.addActionListener(this);
        opt4Text = temp1.getOpt4Text();
        quizframe.add(opt4Text);
        //Correct
        correct = temp1.getCor();
        //Next button
        next = new JButton("NEXT");
        next.setBounds(1150,200,150,50);
        quizframe.add(next);
        next.addActionListener(this);
  }

  public static Randomized displayQues(Question q){ //Taking the randomized object and saving it

    String[] array = Question.scramble(q);
    String question = array[0];
    String op1 = array[1];
    String op2 = array[2];
    String op3 = array[3];
    String op4 = array[4];
    int correct = Integer.valueOf(array[5]);

    //Creating the bounds of all the components in the GUI
    JTextArea quesText = new JTextArea(question);
      quesText.setBounds(550,50,400,74);
      quesText.setLineWrap(true);
      quesText.setWrapStyleWord(true);
      quesText.setEditable(false);

    JButton option1 = new JButton("A");
      option1.setBounds(400,135,50,75);
    JTextArea opt1Text = new JTextArea(op1);
    opt1Text.setBounds(450,135,250,75);
    opt1Text.setLineWrap(true);
    opt1Text.setWrapStyleWord(true);
    opt1Text.setEditable(false);
      
    JButton option2 = new JButton("B");
      option2.setBounds(400,250,50,75);
    JTextArea opt2Text = new JTextArea(op2);
    opt2Text.setBounds(450,250,250,75);
    opt2Text.setLineWrap(true);
    opt2Text.setWrapStyleWord(true);
    opt2Text.setEditable(false);

    JButton option3 = new JButton("C");
      option3.setBounds(810,135,50,75);
    JTextArea opt3Text = new JTextArea(op3);
    opt3Text.setBounds(860,135,250,75);
    opt3Text.setLineWrap(true);
    opt3Text.setWrapStyleWord(true);
    opt3Text.setEditable(false);

    JButton option4 = new JButton("D");
      option4.setBounds(810,250,50,75);
    JTextArea opt4Text = new JTextArea(op4);
    opt4Text.setBounds(860,250,250,75);
    opt4Text.setLineWrap(true);
    opt4Text.setWrapStyleWord(true);
    opt4Text.setEditable(false);

    Randomized temp = new Randomized(ques,option1,option2,option3,option4,correct,question,op1,op2,op3,op4, quesText,opt1Text,opt2Text,opt3Text,opt4Text);
    return temp;
  }

  //String to Question object - Takes the strings from the txt file and turns them into Question objects
  public static Question questionMaker(String s){
    String ask = s.substring(0,s.indexOf('%'));
    String temp = s.substring(s.indexOf('%')+1,s.length());
    String correct = temp.substring(0,temp.indexOf('%'));
    String temp2 = temp.substring(temp.indexOf('%')+1,temp.length());
    String w1 = temp2.substring(0,temp2.indexOf('%'));
    String temp3 = temp2.substring(temp2.indexOf('%')+1,temp2.length());
    String w2 = temp3.substring(0,temp3.indexOf('%'));
    String temp4 = temp3.substring(temp3.indexOf('%')+1,temp3.length());
    String w3 = temp4.substring(0,temp4.indexOf('%'));
     
    Question ques = new Question(ask,correct,w1,w2,w3);
    return ques; 
  }

  //Read Text file and make array of Questions
  public static Question[] FileToQues(){
    try{
    FileReader fr = new FileReader("Questions.txt");
    BufferedReader reader = new BufferedReader(fr);
    String a = reader.readLine();
    int lines = Integer.parseInt(a);
    Question[] arr = new Question[lines];

      String temp = reader.readLine();
      int i = 0;
      while (temp != null) {
        arr[i] = questionMaker(temp);
        temp = reader.readLine();
        i++;
      }
      reader.close();

        return arr;

    } catch (IOException e) {
     System.out.println("Error in File writing");
   }
    Question[] arr2 = new Question[1];
    return arr2;
  }

  public static void shuffleArray(Question[] array){ // Shuffles the order of objects in the array
    int index;
    Question temp;
    Random random = new Random();
    for (int i = array.length - 1; i > 0; i--)
    {
        index = random.nextInt(i + 1);
        temp = array[index];
        array[index] = array[i];
        array[i] = temp;
    }
  }//Stack Overflow - 3rd solution - https://stackoverflow.com/questions/1519736/random-shuffling-of-an-array

  @Override
  public void actionPerformed(ActionEvent e){//Start of action performed
	  
    if(e.getSource() == opt1){ //If option 1 is clicked in the quiz
      answerstotal = answerstotal+1;
      if(clickable != true){
      if(correct == 1){ //Checking if option 1 was the right answer
        quesText.setText("Correct!");
        Question.rights++;
        Firstclass.lastX1 = Firstclass.x1;
      }
      Else{ //Answer was not option 1
    	 
          //Creating a string with the correct answer, to display to the user so they know what the correct answer was so they know for next time. 
          String s = "";
          if(correct == 1){
            s = "A";
          }
          if(correct == 2){
            s = "B";
          }
          if(correct == 3){
            s = "C";
          }
          if(correct == 4){
            s = "D";
          }
          quesText.setText("Wrong! Correct Answer: "+s);

      }
      clickable = true; //This is to make sure the user can’t move onto the next question without answering the prior one
      order++; //Moving to next question
      temp1 = displayQues(array1[order]);
      }//if clickable = false
    }
    //Option2
    if(e.getSource() == opt2){
      answerstotal = answerstotal+1;
      if(clickable != true){
      if(correct == 2){
        quesText.setText("Correct!");
        Question.rights++;
        Firstclass.lastX1 = Firstclass.x1;
        
      }
      else{
    	  String s = "";
          if(correct == 1){
            s = "A";
          }
          if(correct == 2){
            s = "B";
          }
          if(correct == 3){
            s = "C";
          }
          if(correct == 4){
            s = "D";
          }
          quesText.setText("Wrong! Correct Answer: "+s);

      }
      clickable = true;
      order++;
      temp1 = displayQues(array1[order]);
      }
    }
    //Option3
    if(e.getSource() == opt3){
      answerstotal = answerstotal+1;
      if(clickable != true){
      if(correct == 3){
        quesText.setText("Correct!");
        Question.rights++;
        Firstclass.lastX1 = Firstclass.x1;
      }
      else{
    	  String s = "";
          if(correct == 1){
            s = "A";
          }
          if(correct == 2){
            s = "B";
          }
          if(correct == 3){
            s = "C";
          }
          if(correct == 4){
            s = "D";
          }
          quesText.setText("Wrong! Correct Answer: "+s);

      }
      clickable = true;
      order++;
      temp1 = displayQues(array1[order]);
      }
    }
    //Option4
    if(e.getSource() == opt4){
      answerstotal = answerstotal+1;
      if(clickable != true){
      if(correct == 4){
    	  
        quesText.setText("Correct!");
        Question.rights++;
        Firstclass.lastX1 = Firstclass.x1;
      }
      else{
    	  String s = "";
          if(correct == 1){
            s = "A";
          }
          if(correct == 2){
            s = "B";
          }
          if(correct == 3){
            s = "C";
          }
          if(correct == 4){
            s = "D";
          }
          quesText.setText("Wrong! Correct Answer: "+s);

      }
      clickable = true;
      order++;
      temp1 = displayQues(array1[order]);
      }
    }
	if (e.getSource() == pausebutton) { //Pause button
		Firstclass.menu.setVisible(true);
		quizframe.setVisible(false);
		Firstclass.carframe.setVisible(false);
	}
    //Next Button
    if(e.getSource() == next){
      if(clickable == true){//if the user has clicked on one of the options
       if(order != Question.numAsks+1){  //Checking if the user is on the last question
        //Setting up the next question (changing the question asked, the answers, etc)
        quesText.setText(temp1.getQuesString());
        opt1Text.setText(temp1.getOp1String());
        opt2Text.setText(temp1.getOp2String());
        opt3Text.setText(temp1.getOp3String());
        opt4Text.setText(temp1.getOp4String());
         
        correct = temp1.getCor();
        clickable = false;
        }
        else{//User has done the quiz. Hiding all the buttons and stuff
          opt1.setVisible(false);
          opt2.setVisible(false);
          opt3.setVisible(false);
          opt4.setVisible(false);
          next.setVisible(false);

          opt1Text.setVisible(false);
          opt2Text.setVisible(false);
          opt3Text.setVisible(false);
          opt4Text.setVisible(false);
        }
      }  
    }

    
  }//end of actionPerformed
  
}
