//imports
import java.io.*;

import java.util.Random;
import java.awt.Color;
import javax.swing.UIManager;
import java.awt.Dimension;
import java.awt.EventQueue;
import java.awt.Graphics;
import java.awt.Graphics2D;
import java.awt.GridBagLayout;
import java.text.SimpleDateFormat;
import javax.swing.JPanel;
import javax.swing.Timer;
import javax.swing.UIManager;
import javax.swing.UnsupportedLookAndFeelException;
import java.awt.event.MouseAdapter;
import java.awt.event.MouseEvent;
import java.text.SimpleDateFormat;
import java.util.concurrent.TimeUnit;
import java.net.URL;
import java.util.Arrays;
import java.util.Scanner;
import javax.swing.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.awt.image.BufferedImage;
import java.awt.image.ImageObserver;
import javax.swing.border.Border;
import javax.swing.border.LineBorder;
import java.awt.*;
import javax.imageio.ImageIO;
import javax.sound.sampled.*;
import java.util.ArrayList;
import java.util.List;
import java.util.concurrent.ThreadLocalRandom;

//This program is suppose to produce a game GUI with a quiz containing randomized questions and each question answered correctly will move the car and if you get the car to the end of the screen you win
class Firstclass extends JFrame implements ActionListener {
	// declaration of audio and the quiz object
	static quizGUI quiz1;
	static NquizGUI quiz2;
	static AudioInputStream ais;
	static Clip c;
	static int y;
	static Clip c2;

	public static void main(String[] args) {
		new Firstclass();
// This is code to allow for the program to have access to audio inside the                   file.
		String path = new File("").getAbsolutePath() + "\\Overworldnew3.wav";
		File sound = new File(path);
		try {
			ais = AudioSystem.getAudioInputStream(sound);
			c = AudioSystem.getClip();
			c.open(ais);
		} catch (Exception e) {
			System.out.println(e.getMessage());
		}
		String path2 = new File("").getAbsolutePath() + "\\countdown2.wav";
		File sound2 = new File(path2);
		try {
			ais = AudioSystem.getAudioInputStream(sound2);
			c2 = AudioSystem.getClip();
			c2.open(ais);

			c.start();
		} catch (Exception e) {
			System.out.println(e.getMessage());
		}
	}

	// Start of the action performed if statements
	@Override
	public void actionPerformed(ActionEvent e) {
		//Goes from homepage to start screen
		if (e.getSource() == start) {
			OpenStartScreen();
			try {
				Thread.sleep(200);
			} catch (InterruptedException ex) {
				ex.printStackTrace();
			}
			frame1.setVisible(false);
		}
		//Closes game
		if (e.getSource() == exit) {
			System.exit(0);
		}
		//Returns user from start screen back to homepage
		if (e.getSource() == back) {
			OpenHomepage();
			try {
				Thread.sleep(200);
			} catch (InterruptedException ex) {
				ex.printStackTrace();
			}
			frame2.setVisible(false);

		}
		//mutes the audio
		if (e.getSource() == mute) {
			mute.setVisible(false);
			c.stop();
			unmute.setVisible(true);
		}
		//Unmutes the audio
		if (e.getSource() == unmute) {
			mute.setVisible(true);
			c.start();
			unmute.setVisible(false);
		}
		//Sets variables and opens countdown for road signs quiz
		if (e.getSource() == RoadSign) {
			y = 2;
			c.stop();
			CountDown();
			try {
				Thread.sleep(200);
			} catch (InterruptedException ex) {
				ex.printStackTrace();
			}
			frame2.setVisible(false);

		}
		Sets variable and opens countdown for roadrules quiz
		if (e.getSource() == RoadRules) {
			y = 1;
			c.stop();
			CountDown();
			try {
				Thread.sleep(200);
			} catch (InterruptedException ex) {
				ex.printStackTrace();
			}
			frame2.setVisible(false);
		}
		//Exit from the pause menu
		if (e.getSource() == exit2) {
			OpenHomepage();
			c.start();
			try {
				Thread.sleep(200);
			} catch (InterruptedException ex) {
				ex.printStackTrace();
			}
			frame3.setVisible(false);

		}
		
		//Resumes game from pause menu
		if (e.getSource() == resume) {
			menu.setVisible(false);
			carframe.setVisible(true);
			if (y ==1) {
				quizGUI.quizframe.setVisible(true);
			}
			if(y ==2) {
				NquizGUI.frame1.setVisible(true);
			}

		}
		//Exit to homepage from end screen
		if (e.getSource() == exit3) {
			OpenHomepage();
			c.start();
			menu.setVisible(false);

		}
		//Restart the game from pause menu
		if (e.getSource() == restart) {
			menu.setVisible(false);
			CountDown();

		}
		//Restart game from end screen
		if (e.getSource() == playagain) {
			frame3.setVisible(false);
			CountDown();

		}
	}

	// These are static declarations of almost every single component inside the GUI.
	static JFrame frame1;
	static JFrame frame2;
	static JFrame frame3;
	static JFrame carframe;
	static JPanel panel;
	static JFrame timerframe;
	static JFrame buttonframe1;
	static JButton start;
	static JButton exit;
	static JButton exit2;
	static JButton exit3;
	static JButton back;
	static JButton RoadSign;
	static JButton RoadRules;
	static JButton mute;
	static JButton begin1;
	static JButton startroadrules;
	static JButton unmute;
	static JLabel picture2label;
	static JButton playagain;
	static JFrame menu;
	static JButton resume;
	static JButton restart;
	static URL url;
	static JFrame traindemo;
	static JFrame raceframe;
	static float x1;
	static float lastX1;
	static float x;
	static float lastX;
	static float x2;
	static float lastX2;
	static int numtest = 0;
	static int n = 0;
	static JLabel questions;
	static int q = 0;
	static JLabel place;
	static Dimension Max = Toolkit.getDefaultToolkit().getScreenSize();
	static boolean carmover = false;

	public Firstclass() {
		// This is the start of the firstclass object which first uses the homepage
		// method and the popupmenu method
		OpenHomepage();
		popupmenu();
		menu.setVisible(false);
	}

	// This method creates and opens the homepage
	public void OpenHomepage() {
		//import images
		String path = "picture3resize.png";
		File file = new File(path);
		BufferedImage image = null;
		try {
			image = ImageIO.read(file);
		} catch (IOException e) {
			e.printStackTrace();
		}
		JLabel picture1 = new JLabel(new ImageIcon(image));
		picture1.setBounds(700, 100, 1000, 1000);

		String path2 = "picture5resize.png";
		File file2 = new File(path2);
		BufferedImage image2 = null;
		try {
			image2 = ImageIO.read(file2);
		} catch (IOException e) {
			e.printStackTrace();
		}
		JLabel picture2 = new JLabel(new ImageIcon(image2));
		picture2.setBounds(-100, 125, 1000, 1000);

		//Homepage frame, buttons after a named accordingly
		frame1 = new JFrame("");
		frame1.setMaximumSize(Max);
		frame1.setExtendedState(JFrame.MAXIMIZED_BOTH);
		frame1.getContentPane().setBackground(new Color(247, 255, 252));
		frame1.setLayout(null);
		frame1.setVisible(true);

		JLabel title1 = new JLabel("G1 race quiz");
		title1.setBounds(650, 150, 1000, 60);
		title1.setFont(new Font("Calibri", Font.BOLD, 50));
		frame1.add(title1);
		frame1.add(picture1);
		frame1.add(picture2);

		start = new JButton("Start");
		Border emptyBorder = BorderFactory.createEmptyBorder();
		start.setBackground(new Color(70, 184, 141));
		start.setForeground(new Color(70, 184, 141));
		start.setFocusPainted(false);
		start.setFont(new Font("Tahoma", Font.BOLD, 22));
		start.setBounds(625, 225, 300, 100);
		start.setBorder(emptyBorder);
		start.addActionListener(this);
		start.setContentAreaFilled(false);
		start.setBorder(new LineBorder(Color.BLACK));
		frame1.add(start);

		exit = new JButton("EXIT TO DESKTOP");
		exit.setBackground(new Color(247, 255, 252));
		exit.setForeground(new Color(70, 184, 141));
		exit.setFocusPainted(false);
		exit.setFont(new Font("Tahoma", Font.BOLD, 22));
		exit.setBounds(625, 350, 300, 100);
		exit.addActionListener(this);
		exit.setContentAreaFilled(false);
		exit.setBorder(emptyBorder);
		exit.setBorder(new LineBorder(Color.BLACK));
		frame1.add(exit);

		mute = new JButton("mute");
		mute.setBackground(new Color(247, 255, 252));
		mute.setForeground(new Color(70, 184, 141));
		mute.setFocusPainted(false);
		mute.setFont(new Font("Tahoma", Font.BOLD, 30));
		mute.setBounds(1300, 25, 200, 100);
		mute.addActionListener(this);
		mute.setContentAreaFilled(false);
		mute.setBorder(new LineBorder(Color.BLACK));
		frame1.add(mute);

		unmute = new JButton("unmute");
		unmute.setBackground(new Color(247, 255, 252));
		unmute.setForeground(new Color(70, 184, 141));
		unmute.setFocusPainted(false);
		unmute.setFont(new Font("Tahoma", Font.BOLD, 30));
		unmute.setBounds(1300, 25, 200, 100);
		unmute.setContentAreaFilled(false);
		unmute.addActionListener(this);
		frame1.add(unmute);
		unmute.setBorder(new LineBorder(Color.BLACK));
		unmute.setVisible(false);

	}

	// This method creates and opens the start screen
	public void OpenStartScreen() {
		//Imports image
		String path3 = "flag2.png";
		File file3 = new File(path3);
		BufferedImage image3 = null;
		try {
			image3 = ImageIO.read(file3);
		} catch (IOException e) {
			e.printStackTrace();
		}
		JLabel picture3 = new JLabel(new ImageIcon(image3));
		picture3.setBounds(275, 100, 1000, 1000);

		//Creates the frame for the start screen other buttons are named accordingly.

		frame2 = new JFrame("");
		Border emptyBorder = BorderFactory.createEmptyBorder();
		frame2.setMaximumSize(Max);
		frame2.setExtendedState(JFrame.MAXIMIZED_BOTH);
		frame2.getContentPane().setBackground(new Color(247, 255, 252));
		frame2.setLayout(null);
		frame2.setVisible(true);
		frame2.add(picture3);

		JLabel title2 = new JLabel("Start screen");
		title2.setBounds(650, 150, 1000, 60);
		title2.setFont(new Font("Calibri", Font.BOLD, 50));
		frame2.add(title2);

		back = new JButton("back");
		back.setBackground(new Color(247, 255, 252));
		back.setForeground(new Color(70, 184, 141));
		back.setFocusPainted(false);
		back.setFont(new Font("Tahoma", Font.BOLD, 30));
		back.setBounds(0, 0, 300, 100);
		back.addActionListener(this);
		back.setBorder(emptyBorder);
		back.setContentAreaFilled(false);
		frame2.add(back);

		RoadSign = new JButton("Roadsigns");
		RoadSign.setBackground(new Color(70, 184, 141));
		RoadSign.setFocusPainted(false);
		RoadSign.setFont(new Font("Tahoma", Font.BOLD, 22));
		RoadSign.setBounds(350, 300, 300, 100);
		RoadSign.setBorder(emptyBorder);
		RoadSign.setContentAreaFilled(false);
		RoadSign.addActionListener(this);
		RoadSign.setForeground(new Color(70, 184, 141));
		RoadSign.setBorder(new LineBorder(Color.BLACK));
		frame2.add(RoadSign);

		RoadRules = new JButton("Roadrules");
		RoadRules.setBackground(new Color(70, 184, 141));
		RoadRules.setFocusPainted(false);
		RoadRules.setFont(new Font("Tahoma", Font.BOLD, 22));
		RoadRules.setBounds(900, 300, 300, 100);
		RoadRules.setBorder(emptyBorder);
		RoadRules.setContentAreaFilled(false);
		RoadRules.addActionListener(this);
		RoadRules.setForeground(new Color(70, 184, 141));
		RoadRules.setBorder(new LineBorder(Color.BLACK));
		frame2.add(RoadRules);

		frame2.add(mute);
		frame2.add(unmute);
		unmute.setVisible(false);
	}

	// This method creates and opens the end screen
	public void Openendscreen() {
		frame3 = new JFrame("");
		Border emptyBorder = BorderFactory.createEmptyBorder();
		frame3.setMaximumSize(Max);
		frame3.setExtendedState(JFrame.MAXIMIZED_BOTH);
		frame3.getContentPane().setBackground(new Color(247, 255, 252));
		frame3.setLayout(null);
		frame3.setVisible(true);
		//y is a static int that changes depending on if the user presses road signs and road rules and these if statement determine what the end screen will look like depending on if they pressed road signs or road rules 
		if (y == 1 && q == 0) {
			questions = new JLabel("Correct: " + Question.rights + " / " + quizGUI.answerstotal);
			place = new JLabel("You got " + n + " place!");
		}
		if (y == 2 && q == 0) {
			questions = new JLabel("Correct: " + NQuestion.rights + " / " + NquizGUI.answerstotal);
			place = new JLabel("You got " + n + " place!");
		}
		if (q == 1) {
			if(y==2) {
				questions = new JLabel("Correct: " + NQuestion.rights + " / " + "20");
			}
			if(y==1) {
				questions = new JLabel("Correct: " + Question.rights + " / " + "20");
			}
			place = new JLabel("Your car broke!");
		}
		questions.setBounds(625, 250, 400, 100);
		questions.setFont(new Font("Calibri", Font.BOLD, 50));
		frame3.add(questions);

		place.setBounds(600, 150, 500, 100);
		place.setFont(new Font("Calibri", Font.BOLD, 50));
		frame3.add(place);

		playagain = new JButton("Play again");
		emptyBorder = BorderFactory.createEmptyBorder();
		playagain.setBackground(new Color(70, 184, 141));
		playagain.setForeground(new Color(70, 184, 141));
		playagain.setFocusPainted(false);
		playagain.setContentAreaFilled(false);
		playagain.setFont(new Font("Tahoma", Font.BOLD, 22));
		playagain.setBounds(625, 350, 300, 100);
		playagain.setBorder(emptyBorder);
		playagain.addActionListener(this);
		playagain.setBorder(new LineBorder(Color.BLACK));
		frame3.add(playagain);

		exit2 = new JButton("EXIT TO HOMEPAGE");
		exit2.setBackground(new Color(247, 255, 252));
		exit2.setForeground(new Color(70, 184, 141));
		exit2.setContentAreaFilled(false);
		exit2.setFocusPainted(false);
		exit2.setFont(new Font("Tahoma", Font.BOLD, 22));
		exit2.setBounds(625, 475, 300, 100);
		exit2.addActionListener(this);
		exit2.setBorder(emptyBorder);
		exit2.setBorder(new LineBorder(Color.BLACK));
		frame3.add(exit2);
	}

	// This method creates and opens popupmenu
	public void popupmenu() {
		carmover = true;
		menu = new JFrame("");
		Border emptyBorder = BorderFactory.createEmptyBorder();
		menu.setMaximumSize(Max);
		menu.setExtendedState(JFrame.MAXIMIZED_BOTH);
		menu.getContentPane().setBackground(new Color(247, 255, 252));
		menu.setLayout(null);

		resume = new JButton("Resume");
		resume.setBackground(new Color(247, 255, 252));
		resume.setForeground(new Color(70, 184, 141));
		resume.setFocusPainted(false);
		resume.setFont(new Font("Tahoma", Font.BOLD, 40));
		resume.setBounds(425, 225, 700, 100);
		resume.addActionListener(this);
		resume.setBorder(emptyBorder);
		resume.setContentAreaFilled(false);
		menu.add(resume);

		restart = new JButton("Restart");
		restart.setBackground(new Color(247, 255, 252));
		restart.setForeground(new Color(70, 184, 141));
		restart.setFocusPainted(false);
		restart.setFont(new Font("Tahoma", Font.BOLD, 40));
		restart.setBounds(625, 350, 300, 100);
		restart.addActionListener(this);
		restart.setBorder(emptyBorder);
		restart.setContentAreaFilled(false);
		menu.add(restart);

		exit3 = new JButton("Exit To Homepage");
		exit3.setBackground(new Color(247, 255, 252));
		exit3.setForeground(new Color(70, 184, 141));
		exit3.setFocusPainted(false);
		exit3.setFont(new Font("Tahoma", Font.BOLD, 40));
		exit3.setBounds(435, 475, 700, 100);
		exit3.addActionListener(this);
		exit3.setBorder(emptyBorder);
		exit3.setContentAreaFilled(false);
		menu.add(exit3);
		menu.add(new TrainCanvas());
		menu.setVisible(true);
	}

	// This function is responsible for the car component and creates the frame with the cars
	public void race() {
		lastX = 0;
		lastX1 = 0;
		x = 0;
		x1 = 0;
		x2 = 0;
		lastX2 = 0;
		carframe = new JFrame("");
		Border emptyBorder = BorderFactory.createEmptyBorder();
		carframe.setMaximumSize(Max);
		carframe.setSize(2000, 2000);
		carframe.setExtendedState(JFrame.MAXIMIZED_BOTH);
		carframe.getContentPane().setBackground(new Color(247, 255, 252));
		carframe.setVisible(true);
		carframe.add(new TrainCanvas()); // was frame
		carframe.setVisible(true);

	}

	// The traincanvas class is used for importing the car images then moving the cars by using repaint() while changing car positions
	class TrainCanvas extends JComponent {
		static Graphics2D gg;
		static Graphics2D gg1;
		static Graphics2D gg2;

		public TrainCanvas() {
			Thread animationThread = new Thread(new Runnable() {
				public void run() {
					// This while loop repaints the carframe so each 100 miliseconds it updates the position of the car
					while (true) {

						repaint();

						try {
							Thread.sleep(100);
						} catch (Exception ex) {
						}
					}
				}
			});

			animationThread.start();
		}

		// This part is responsible for importing the car images then deciding the car positions
		public void paintComponent(Graphics g) {
			gg = (Graphics2D) g;
			gg1 = (Graphics2D) g;
			gg2 = (Graphics2D) g;
			String path = "picture3resize.png";
			File file = new File(path);
			BufferedImage image = null;
			try {
				image = ImageIO.read(file);
			} catch (IOException e) {
				e.printStackTrace();
			}
			String path1 = "new1.png";
			File file1 = new File(path1);
			BufferedImage image1 = null;
			try {
				image1 = ImageIO.read(file1);
			} catch (IOException e) {
				e.printStackTrace();
			}

			String path2 = "picture5resize.png";
			File file2 = new File(path2);
			BufferedImage image2 = null;
			try {
				image2 = ImageIO.read(file2);
			} catch (IOException e) {
				e.printStackTrace();
			}
			int w = getWidth();
			int h = getHeight();

			int trainW = 50;
			int trainH = 50;
			int trainSpeed = 5;

			// These decide how much distance it changes per 100 miliseconds and the x1 is player car and the threadlocal random makes the car speed of the bot cars vary

			x = lastX + ThreadLocalRandom.current().nextInt(1, 4);
			x1 = lastX1 + 85;
			x2 = lastX2 + ThreadLocalRandom.current().nextInt(1, 2);
			//This is one of two ways the end screen triggers this is by seeing if the position of the car is out of the screen and if it is, the endscreen appears.
			if (x1 > 1586) {
				//The n variable is used to determine what place the screen says they got.
				if (x1 > x2 && x1 > x) {
					n = 1;
				}
				if (x1 < x2 && x1 < x) {
					n = 3;
				}
				if ((x1 < x2 && x1 > x) || (x1 > x2 && x1 < x)) {
					n = 2;
				}

				Openendscreen();
				carframe.setVisible(false);
				//all variables reset in preparation for the restart or play again
				x = 0;
				x1 = 0;
				x2 = 0;
				lastX = 0;
				lastX1 = 0;
				lastX2 = 0;
				return;

			}
			//This is the second end screen trigger and occurs when the user does not finish the quiz in 20 questions
			if (NquizGUI.answerstotal == 20 || quizGUI.answerstotal == 20) {
				q = 1;
				Openendscreen();
				quizGUI.answerstotal = 0;
				NquizGUI.answerstotal = 0;
			}

			// This is how the images are declared and what position they are in
			ImageObserver paintingChild = null;
			gg.drawImage(image, (int) (x - 1), h / 2 + trainH, trainW, trainH, paintingChild);
			gg1.drawImage(image1, (int) (x1 - 85), h / 2 + 90, trainW, trainH, paintingChild);
			gg2.drawImage(image2, (int) (x2 - 3), h / 2 + 150, trainW, trainH, paintingChild);
			lastX = x;
			lastX2 = x2;
		}
	}

	// This method makes the countdown responsible for starting the race
	public void CountDown() {
		EventQueue.invokeLater(new Runnable() {
			@Override
			public void run() {
				try {
					UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());
				} catch (ClassNotFoundException | InstantiationException | IllegalAccessException
						| UnsupportedLookAndFeelException ex) {
					ex.printStackTrace();
				}
				// frame for the countdown
				timerframe = new JFrame("");
				timerframe.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
				timerframe.add(new TestPane());
				timerframe.pack();
				timerframe.setLocationRelativeTo(null);
				timerframe.setExtendedState(JFrame.MAXIMIZED_BOTH);
				timerframe.setVisible(true);
			}
		});
	}

	// This sets the timer up including when it starts what is the duration and what does it say before the player touches the trigger button
	public class TestPane extends JPanel {

		static Timer timer;
		static long startTime = 0;
		static long duration = 4000;
		static JLabel label;
		static int n;

		public TestPane() {
			setLayout(new GridBagLayout());
			timer = new Timer(10, new ActionListener() {
				@Override
				public void actionPerformed(ActionEvent e) {
					if (startTime < 0) {
						startTime = System.currentTimeMillis();
					}
					long now = System.currentTimeMillis();
					long clockTime = now - startTime;
					// Methods and actions that occur after the countdown ends, most variable also have to be reset 
					if (clockTime >= duration) {
						c2.stop();
						clockTime = duration;
						NquizGUI.order = 0;
						quizGUI.order = 0;
						timer.stop();
						q = 0;
						Question.rights = 0;
						quizGUI.answerstotal = 0;
						NQuestion.rights = 0;
						NquizGUI.answerstotal = 0;
						race();
						n = n + 1;
						//This if statement is used so that the objects only get created once during the first instance of countdown thereby limiting bugs that can occur
						if (n == 1) {
							quiz1 = new quizGUI();
							quiz2 = new NquizGUI();
						}
//As mentioned previously the y value determines which frame gets created.
						if (y == 1) {
							quizGUI.quizframe.setVisible(true);
							NquizGUI.frame1.setVisible(false);

						}
						if (y == 2) {
							quizGUI.quizframe.setVisible(false);
							NquizGUI.frame1.setVisible(true);
						}
						timerframe.setVisible(false);

					}
					//This makes the countdown time intervals as seconds
					SimpleDateFormat df = new SimpleDateFormat("s");
					label.setText(df.format(duration - clockTime));
				}
			});
			timer.setInitialDelay(0);
			timerframe.addMouseListener(new MouseAdapter() {
				// The countdown starts if the mouseadapter reads a click
				public void mousePressed(MouseEvent e) {
					if (!timer.isRunning()) {
						c2.start();
						startTime = -1;
						timer.start();
					}

				}
			});
			Border emptyBorder = BorderFactory.createEmptyBorder();
			label = new JLabel("Are you ready?");
			label.setBorder(emptyBorder);
			label.setBounds(650, 150, 1000, 60);
			label.setFont(new Font("Calibri", Font.BOLD, 50));
			add(label);
		}
	}
}

