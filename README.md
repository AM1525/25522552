# 25522552


import javafx.application.Application;
import javafx.scene.Scene;
import javafx.stage.Stage;

public class Main extends Application {

    @Override
    public void start(Stage primaryStage) {
        LoginScreen login = new LoginScreen(primaryStage);
        Scene scene = new Scene(login.getView(), 400, 300);
        primaryStage.setTitle("Company Management - Login");
        primaryStage.setScene(scene);
        primaryStage.show();
    }

    public static void main(String[] args) {
        launch(args);
    }
}



import javafx.scene.Scene;
import javafx.scene.control.*;
import javafx.scene.layout.*;
import javafx.scene.text.Text;
import javafx.stage.Stage;

public class LoginScreen {
    private VBox layout;
    private Stage stage;

    public LoginScreen(Stage stage) {
        this.stage = stage;
        layout = new VBox(10);
        layout.setStyle("-fx-padding: 20;");

        // استخدمنا Text بدل Label هنا
        Text label = new Text("Enter your name and ID:");
        TextField nameField = new TextField();
        nameField.setPromptText("Name");

        TextField idField = new TextField();
        idField.setPromptText("ID");

        Button loginButton = new Button("Login");
        Label msg = new Label();

        loginButton.setOnAction(e -> {
            String name = nameField.getText();
            String id = idField.getText();

            if (!name.isEmpty() && !id.isEmpty() && id.matches("\\d+")) {
                MenuScreen menu = new MenuScreen(stage);
                stage.setScene(new Scene(menu.getView(), 500, 400));
            } else {
                msg.setText("Please enter valid name and numeric ID.");
            }
        });

        layout.getChildren().addAll(label, nameField, idField, loginButton, msg);
    }

    public VBox getView() {
        return layout;
    }
}

import javafx.scene.control.Button;
import javafx.scene.layout.VBox;
import javafx.stage.Stage;

public class MenuScreen {
    private VBox layout;
    private Stage stage;

    public MenuScreen(Stage stage) {
        this.stage = stage;
        layout = new VBox(15);
        layout.setStyle("-fx-padding: 20;");

        Button addBtn = new Button("Add Employee");
        Button deleteBtn = new Button("Delete Employee");
        Button searchBtn = new Button("Search Employee");
        Button compareBtn = new Button("Compare Employees");
        Button displayBtn = new Button("Display All");

        // Just placeholder actions
        addBtn.setOnAction(e -> System.out.println("Add Employee clicked"));
        deleteBtn.setOnAction(e -> System.out.println("Delete clicked"));
        searchBtn.setOnAction(e -> System.out.println("Search clicked"));
        compareBtn.setOnAction(e -> System.out.println("Compare clicked"));
        displayBtn.setOnAction(e -> System.out.println("Display clicked"));

        layout.getChildren().addAll(addBtn, deleteBtn, searchBtn, compareBtn, displayBtn);
    }

    public VBox getView() {
        return layout;
    }
}


