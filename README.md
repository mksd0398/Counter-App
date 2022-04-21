# Counter-App

## MainActivity.kt

package com.parta.counterapp

import androidx.appcompat.app.AppCompatActivity
import android.os.Bundle
import android.os.Handler
import android.os.Looper
import kotlinx.android.synthetic.main.activity_main.*

class MainActivity : AppCompatActivity() {
    override fun onCreate(savedInstanceState: Bundle?) {
        super.onCreate(savedInstanceState)
        setContentView(R.layout.activity_main)

        val mainHandler = Handler(Looper.getMainLooper())

        var count = 0

        start.setOnClickListener{
            mainHandler.post(object : Runnable {
                override fun run() {

                    counter.text = count.toString()
                    count++
                    mainHandler.postDelayed(this, 1000) //1 second delay for demo can increase or decrease

                }
            })
        }

        stop.setOnClickListener { mainHandler.removeCallbacksAndMessages(null) }


    }
}
