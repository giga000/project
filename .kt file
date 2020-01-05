package example.javatpoint.com.kotlinsharedpreference

import android.content.Context
import android.content.SharedPreferences
import android.support.v7.app.AppCompatActivity
import android.os.Bundle
import android.view.View
import android.widget.Button
import android.widget.EditText
import android.widget.TextView



class MainActivity : AppCompatActivity() {

    private val sharedPrefFile = "kotlinsharedpreference"

    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val inputName = findViewById<EditText>(R.id.editName)
        val inputAge = findViewById<EditText>(R.id.editAge)
        val inputGender = findViewById<EditText>(R.id.editGender)
        val outputName = findViewById<TextView>(R.id.textViewShowName)
        val outputAge = findViewById<TextView>(R.id.textViewShowAge)
        val outputGender = findViewById<EditText>(R.id.textViewShowGender)

        val btnSave = findViewById<Button>(R.id.save)
        val btnView = findViewById<Button>(R.id.view)
        val btnClear = findViewById<Button>(R.id.clear)
        val sharedPreferences: SharedPreferences = this.getSharedPreferences(sharedPrefFile,Context.MODE_PRIVATE)
        btnSave.setOnClickListener(View.OnClickListener {
            val name:String = inputName.text.toString()
            val age:Int = Integer.parseInt(inputAge.text.toString())
            val gender = inputGender.text.toString()
            val editor:SharedPreferences.Editor =  sharedPreferences.edit()
            editor.putString("name_key",name)
            editor.putInt("age_key",age)
            editor.putString("gender_key",gender)
            editor.apply()
            editor.commit()
        })
        btnView.setOnClickListener {

            val sharedNameValue = sharedPreferences.getString("name_key","defaultname")
            val sharedAgeValue = sharedPreferences.getInt("age_key",0)
            val sharedGenderValue = sharedPreferences.getString("gender_key","defaultgender")
            if(sharedAgeValue.equals(0) && sharedNameValue.equals("defaultname") && sharedGenderValue.equals("defaultgender")){
                outputName.setText("default name: ${sharedNameValue}").toString()
                outputAge.setText("default age: ${sharedAgeValue}").toString()
                outputGender.setText("default gender ${sharedGenderValue}").toString()
            }else{
                outputName.setText(sharedNameValue).toString()
                outputAge.setText(sharedAgeValue.toString())
                outputGender.setText(sharedGenderValue).toString()
            }

        }
        btnClear.setOnClickListener(View.OnClickListener {
            val editor = sharedPreferences.edit()
            editor.clear()
            editor.apply()
            outputName.setText("").toString()
            outputAge.setText("").toString()
            outputGender.setText("").toString()
        })
    }
}
