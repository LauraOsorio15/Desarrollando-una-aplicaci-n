# Desarrollando-una-aplicaci-n
<?xml version="1.0" encoding="utf-8"?>
<RelativeLayout xmlns:android="http://schemas.android.com/apk/res/android"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    android:padding="16dp">

    <EditText
        android:id="@+id/editTextFullName"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Nombre completo"
        android:inputType="textPersonName"
        android:layout_marginBottom="16dp"/>

    <EditText
        android:id="@+id/editTextPhone"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Teléfono"
        android:inputType="phone"
        android:layout_below="@id/editTextFullName"
        android:layout_marginBottom="16dp"/>

    <EditText
        android:id="@+id/editTextEmail"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Email"
        android:inputType="textEmailAddress"
        android:layout_below="@id/editTextPhone"
        android:layout_marginBottom="16dp"/>

    <DatePicker
        android:id="@+id/datePicker"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:layout_below="@id/editTextEmail"
        android:layout_marginBottom="16dp"/>

    <EditText
        android:id="@+id/editTextDescription"
        android:layout_width="match_parent"
        android:layout_height="wrap_content"
        android:hint="Descripción del contacto"
        android:inputType="textMultiLine"
        android:layout_below="@id/datePicker"
        android:layout_marginBottom="16dp"/>

    <Button
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:text="Enviar"
        android:layout_below="@id/editTextDescription"
        android:onClick="submitForm"/>
</RelativeLayout>

import android.os.Bundle;
import android.view.View;
import android.widget.Button;
import android.widget.DatePicker;
import android.widget.EditText;
import android.widget.Toast;

import androidx.appcompat.app.AppCompatActivity;

import java.util.Calendar;

public class MainActivity extends AppCompatActivity {

    private EditText editTextFullName, editTextPhone, editTextEmail, editTextDescription;
    private DatePicker datePicker;

    @Override
    protected void onCreate(Bundle savedInstanceState) {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);

        // Inicializa los componentes de la interfaz
        editTextFullName = findViewById(R.id.editTextFullName);
        editTextPhone = findViewById(R.id.editTextPhone);
        editTextEmail = findViewById(R.id.editTextEmail);
        editTextDescription = findViewById(R.id.editTextDescription);
        datePicker = findViewById(R.id.datePicker);
    }

    // Método para manejar el clic en el botón "Enviar"
    public void submitForm(View view) {
        String fullName = editTextFullName.getText().toString();
        String phone = editTextPhone.getText().toString();
        String email = editTextEmail.getText().toString();
        String description = editTextDescription.getText().toString();

        // Obtén la fecha seleccionada del DatePicker
        int day = datePicker.getDayOfMonth();
        int month = datePicker.getMonth();
        int year = datePicker.getYear();

        // Formatea la fecha
        String dateOfBirth = day + "/" + (month + 1) + "/" + year;

        // Puedes realizar acciones adicionales aquí, como enviar los datos a un servidor

        // Muestra un mensaje de éxito
        String message = "Formulario enviado:\nNombre: " + fullName +
                "\nFecha de nacimiento: " + dateOfBirth +
                "\nTeléfono: " + phone +
                "\nEmail: " + email +
                "\nDescripción: " + description;

        Toast.makeText(this, message, Toast.LENGTH_LONG).show();
    }
}
