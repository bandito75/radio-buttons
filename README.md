# radio-buttons
import javafx.application.Application;
import javafx.event.EventHandler;
import javafx.stage.Stage;
import javafx.scene.Group;
import javafx.scene.Scene;
import javafx.scene.control.RadioButton;
import javafx.scene.control.ToggleGroup;
import javafx.scene.layout.HBox;

//by Michael Revilla
//Creates radio buttons
//and pritns out a messge 
public class radioButtons extends Application {

	public static void main(String[] args) {
		Application.launch(args);

	}

	public void start(Stage primaryStage) {
		Scene scene = new Scene(new Group());
		primaryStage.setTitle("Toggle Button Sample");
		primaryStage.setWidth(250);
		primaryStage.setHeight(75);
		HBox pane = new HBox(10);
		ToggleGroup gro = new ToggleGroup();

		RadioButton rbYes = new RadioButton();
		RadioButton rbMabye = new RadioButton();
		RadioButton rbNo = new RadioButton();

		rbYes.setText("Yes");
		rbMabye.setText("Mabye");
		rbNo.setText("No");

		rbYes.setToggleGroup(gro);
		rbMabye.setToggleGroup(gro);
		rbNo.setToggleGroup(gro);

		MAbHandlerClass mabHand = new MAbHandlerClass();
		NoHandlerClass noHand = new NoHandlerClass();
		YesHandlerClass yesHand = new YesHandlerClass();
		rbMabye.setOnAction(mabHand);
		rbYes.setOnAction(yesHand);
		rbNo.setOnAction(noHand);

		pane.getChildren().add(rbYes);
		pane.getChildren().add(rbMabye);
		pane.getChildren().add(rbNo);
		((Group) scene.getRoot()).getChildren().add(pane);

		primaryStage.setScene(scene);
		primaryStage.setResizable(false);
		primaryStage.setTitle("Attending?");
		primaryStage.show();
	}

	class MAbHandlerClass implements EventHandler<javafx.event.ActionEvent> {
		@Override
		public void handle(javafx.event.ActionEvent arg0) {
			System.out.println("You are mabye going!");
		}
	}

	class NoHandlerClass implements EventHandler<javafx.event.ActionEvent> {
		@Override
		public void handle(javafx.event.ActionEvent arg0) {
			System.out.println("You are NOT going!");
		}
	}

	class YesHandlerClass implements EventHandler<javafx.event.ActionEvent> {
		@Override
		public void handle(javafx.event.ActionEvent arg0) {
			System.out.println("You are going!");
		}
	}
}
