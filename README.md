package com.yayarh.rpsgame

import android.annotation.SuppressLint
import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.widget.ImageView
import android.widget.TextView
import kotlin.random.Random




class MainActivity : AppCompatActivity() {

    private lateinit var resultTextView: TextView
    private lateinit var computerChoiceImageView: ImageView
    private lateinit var rockImageView: ImageView
    private lateinit var paperImageView: ImageView
    private lateinit var scissorsImageView: ImageView


    @SuppressLint("MissingInflatedId")
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)


        resultTextView = findViewById(R.id.resultTextView)
        computerChoiceImageView = findViewById(R.id.computerChoiceImageView)
        rockImageView = findViewById(R.id.rockImageView)
        paperImageView = findViewById(R.id.paperImageView)
        scissorsImageView = findViewById(R.id.scissorsImageView)


        attachClickListener(rockImageView, "rock")
        attachClickListener(paperImageView, "paper")
        attachClickListener(scissorsImageView, "Scissors")




    }


    private fun attachClickListener(imageView: ImageView, choice: kotlin.String) {
        imageView.setOnClickListener {
            playGame(choice)
        }
    }

    private fun playGame(Choice: String) {
        val choices = listOf("Rock", "Paper", "Scissors")
        val computerChoice = choices[ Random.nextInt(3)]



        //set computer Choice image
        when(computerChoice){
            "rock"->computerChoiceImageView.setImageResource(R.drawable.rockImageView)
        }
        when(computerChoice){
            "paper"->computerChoiceImageView.setImageResource(R.drawable.paperImageView)
        }
        when(computerChoice){
            "scissors"->computerChoiceImageView.setImageResource(R.drawable.scissorsImageView)
        }
        computerChoiceImageView.setImageResource(computerChoice)


        val result = when {
            Choice == computerChoice -> "It's a tie!"
            Choice == "Rock" && computerChoice == "Scissors" ||
                    Choice == "Paper" && computerChoice == "Rock" ||
                    Choice == "Scissors" && computerChoice == "Paper" -> "You win!"

            else -> "You lose!"
        }


        resultTextView.text = result
    }


}

private fun ImageView.setImageResource(computerChoice: String) {

}

private fun getImageResource(choice: String): Int {
    return when (choice) {
        "rock" -> R.drawable.rockImageView
        "Paper" -> R.drawable.paperImageView
        "Scissors" -> R.drawable.scissorsImageView
        else -> throw IllegalArgumentException("Invalid choice")
    }
}

<?xml version="1.0" encoding="utf-8"?>
<androidx.constraintlayout.widget.ConstraintLayout xmlns:android="http://schemas.android.com/apk/res/android"
    xmlns:app="http://schemas.android.com/apk/res-auto"
    xmlns:tools="http://schemas.android.com/tools"
    android:layout_width="match_parent"
    android:layout_height="match_parent"
    tools:context=".MainActivity">

<TextView
       android:id="@+id/resultTextView"
       android:layout_width="wrap_content"
       android:layout_height="wrap_content"
       android:layout_marginStart="32dp"
       android:layout_marginTop="48dp"
       android:layout_marginEnd="32dp"
       android:text="Display result of winner"
       android:textSize="32dp"
       app:layout_constraintEnd_toEndOf="parent"
       app:layout_constraintHorizontal_bias="0.0"
       app:layout_constraintStart_toStartOf="parent"
       app:layout_constraintTop_toTopOf="parent" />

   <Button
       android:id="@+id/RockButton"
       android:layout_width="wrap_content"
       android:layout_height="wrap_content"
       android:layout_marginStart="32dp"
       android:layout_marginEnd="32dp"
       android:text="Rock"
       android:textSize="24dp"
       app:layout_constraintBottom_toBottomOf="parent"
       app:layout_constraintEnd_toEndOf="parent"
       app:layout_constraintHorizontal_bias="0.0"
       app:layout_constraintStart_toStartOf="parent"
       app:layout_constraintTop_toTopOf="parent"
       app:layout_constraintVertical_bias="0.807" />

   <Button
       android:id="@+id/PaperButton"
       android:layout_width="wrap_content"
       android:layout_height="wrap_content"
       android:layout_marginStart="32dp"
       android:layout_marginEnd="32dp"
       android:text="Paper"
       android:textSize="24dp"
       app:layout_constraintBottom_toBottomOf="parent"
       app:layout_constraintEnd_toEndOf="parent"
       app:layout_constraintHorizontal_bias="0.88"
       app:layout_constraintStart_toStartOf="parent"
       app:layout_constraintTop_toTopOf="parent"
       app:layout_constraintVertical_bias="0.991" />

   <Button
       android:id="@+id/scissorsButton"
       android:layout_width="wrap_content"
       android:layout_height="wrap_content"
       android:layout_marginStart="32dp"
       android:layout_marginEnd="32dp"
       android:text="Scissors"
       android:textSize="24dp"
       app:layout_constraintBottom_toBottomOf="parent"
       app:layout_constraintEnd_toEndOf="parent"
       app:layout_constraintHorizontal_bias="0.266"
       app:layout_constraintStart_toStartOf="parent"
       app:layout_constraintTop_toTopOf="parent"
       app:layout_constraintVertical_bias="0.914" />

   <ImageView
        android:id="@+id/ComputerChoiceImage"
        android:layout_width="wrap_content"
        android:layout_height="wrap_content"
        android:layout_marginStart="32dp"
        android:layout_marginEnd="32dp"
        app:layout_constraintBottom_toBottomOf="parent"
        app:layout_constraintEnd_toEndOf="parent"
        app:layout_constraintStart_toStartOf="parent"
        app:layout_constraintTop_toTopOf="parent"
        app:layout_constraintVertical_bias="0.0"
        app:srcCompat="@drawable/avatars" />
</androidx.constraintlayout.widget.ConstraintLayout>




