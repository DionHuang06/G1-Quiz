//Question Object
package graphictest;

import java.util.Random;

public class Question{

  //Instance Variables
  private String ask; //Question
  private String correct;//Correct answer
  private String wrong1;//Wrong answer 1
  private String wrong2;//Wrong answer 2
  private String wrong3;//Wrong answer 3
  public static int rights;//# of correctly answered questions
  public static int numAsks = 1000;//# of questions
  public int ASK_ID;//Question ID


  //Constructor
  public Question(String a,String c,String w1, String w2, String w3){
    ask = a;
    correct = c;
    wrong1 = w1;
    wrong2 = w2;
    wrong3 = w3;
    numAsks++;
    ASK_ID = numAsks;
  }

  //Get methods
  public String getAsk(){
    return ask;
  }
  public String getCorrect(){
    return correct;
  }
  public String getWrong1(){
    return wrong1;
  }
  public String getWrong2(){
    return wrong2;
  }
  public String getWrong3(){
    return wrong3;
  }

  //Set methods
  public void setAsk(String a){
    ask = a;
  }
  public void setCorrect(String c){
    correct = c;
  }
  public void setWrong1(String w1){
    wrong1 = w1;
  }
  public void setWrong2(String w2){
    wrong2 = w2;
  }
  public void setWrong3(String w3){
    wrong3 = w3;
  }

  //Randomize
  public static String[] scramble(Question q){ //Changing which spot the correct answer is in. For example, this prevents the correct answer from always being option “A”
    String[] arr1 = new String[6];
    arr1[0] = q.getAsk();
    int temp1 = (int)(Math.random() *4+1); //Setting the correct answer to a random spot between 1-4
    arr1[5] = ""+temp1;
    arr1[temp1] = q.getCorrect();

//Assigns the 3 wrong options to one of the free spots out of the 4. If a spot is already taken, it loops and looks for another one. Eventually all the spots will be taken
    //Wrong 1
    boolean w1NotFound = true;
    int temp2 = 0;
    while(w1NotFound){
      temp2 = (int)(Math.random()*4+1);
      if(temp2 != temp1){
        arr1 [temp2] = q.getWrong1();
        w1NotFound = false;
      }
    }
    //Wrong 2
    boolean w2NotFound = true;
    int temp3 = 0;
    while(w2NotFound){
      temp3 = (int)(Math.random()*4+1);
      if(temp3 != temp1 && temp3 != temp2){
        arr1[temp3] = q.getWrong2();
        w2NotFound = false;
      }
    }

    //Wrong 3
    boolean w3NotFound = true;
    int temp4 = 0;
    while(w3NotFound){
      temp4 = (int)(Math.random()*4+1);
      if(temp4 != temp1 && temp4 != temp2 && temp4 != temp3){
        arr1[temp4] = q.getWrong3();
        w3NotFound = false;
      }
    }
    return arr1;
  }

  
}
