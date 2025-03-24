import 'package:flutter/material.dart';

class SoundSettingsPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Stack(
        children: [
          // Background Image
          Container(
            decoration: BoxDecoration(
              image: DecorationImage(
                image: AssetImage("assets/img4.jpg"), // Ensure this path is correct
                fit: BoxFit.cover,
              ),
            ),
          ),
          Column(
            crossAxisAlignment: CrossAxisAlignment.center,
            children: [
              // Header with Back Button
              Padding(
                padding: const EdgeInsets.only(top: 50, left: 15, right: 15),
                child: Row(
                  children: [
                    IconButton(
                      icon: Icon(Icons.arrow_back, color: Colors.white, size: 30),
                      onPressed: () => Navigator.pop(context),
                    ),
                    Spacer(),
                    Text(
                      "تعديل أصوات الخلفية",
                      style: TextStyle(fontSize: 24, color: Colors.white, fontWeight: FontWeight.bold),
                    ),
                  ],
                ),
              ),

              SizedBox(height: 20),

              // Sound Options List
              Expanded(
                child: Padding(
                  padding: EdgeInsets.symmetric(horizontal: 20),
                  child: Column(
                    crossAxisAlignment: CrossAxisAlignment.start,
                    children: [
                      soundOption("أمواج (إفتراضي)"),
                      SizedBox(height: 10), // Space between items

                      // "أساسي" as plain text
                      Align(
                        alignment: Alignment.centerRight, // Align the text to the right
                        child: Padding(
                          padding: const EdgeInsets.symmetric(vertical: 5),
                          child: Text(
                            "أساسي",
                            style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold, color: Colors.white),
                          ),
                        ),
                      ),

                      SizedBox(height: 10),
                      soundOption("شلال"),
                      SizedBox(height: 10),
                      soundOption("قطرات المطر"),
                      SizedBox(height: 10),
                      soundOption("فقاعات"),
                      SizedBox(height: 10),
                      // Space before "إضافة"

                      // "إضافة" as plain text
                      Align(
                        alignment: Alignment.centerRight, // Align the text to the right
                        child: Padding(
                          padding: const EdgeInsets.symmetric(vertical: 5),
                          child: Text(
                            "إضافة",
                            style: TextStyle(fontSize: 18, fontWeight: FontWeight.bold, color: Colors.white),
                          ),
                        ),
                      ),

                      SizedBox(height: 10),

                      // "إضافة صوت جديد" Button
                      GestureDetector(
                        onTap: () {
                          Navigator.push(
                            context,
                            MaterialPageRoute(builder: (context) => AddNewSoundPage()),
                          );
                        },
                        child: Container(
                          padding: EdgeInsets.symmetric(vertical: 15, horizontal: 20),
                          decoration: BoxDecoration(
                            color: Colors.white.withOpacity(0.9),
                            borderRadius: BorderRadius.circular(10),
                          ),
                          child: Center(
                            child: Text(
                              "إضافة صوت جديد",
                              style: TextStyle(fontSize: 18, color: Colors.black),
                            ),
                          ),
                        ),
                      ),
                    ],
                  ),
                ),
              ),
            ],
          ),
        ],
      ),

      // Bottom Navigation Bar
      bottomNavigationBar: BottomNavigationBar(
        type: BottomNavigationBarType.fixed,
        backgroundColor: Colors.amber,
        selectedItemColor: Colors.white,
        unselectedItemColor: Colors.white70,
        currentIndex: 3, // Settings icon selected
        onTap: (index) {
          // Handle navigation if needed
        },
        items: [
          BottomNavigationBarItem(icon: Icon(Icons.home, color: Colors.white), label: ""),
          BottomNavigationBarItem(icon: Icon(Icons.checklist, color: Colors.white), label: ""),
          BottomNavigationBarItem(icon: Icon(Icons.person, color: Colors.white), label: ""),
          BottomNavigationBarItem(icon: Icon(Icons.settings, color: Colors.blue), label: ""),
        ],
      ),
    );
  }

  Widget soundOption(String title) {
    return Container(
      padding: EdgeInsets.symmetric(vertical: 15, horizontal: 20),
      decoration: BoxDecoration(
        color: Colors.white.withOpacity(0.9),
        borderRadius: BorderRadius.circular(10),
      ),
      child: Center(
        child: Text(
          title,
          style: TextStyle(fontSize: 18, color: Colors.black),
        ),
      ),
    );
  }
}

// New Page for Adding a Sound
class AddNewSoundPage extends StatelessWidget {
  @override
  Widget build(BuildContext context) {
    return Scaffold(
      appBar: AppBar(
        title: Text("إضافة صوت جديد"),
        backgroundColor: Colors.blue,
      ),
      body: Center(
        child: Text("صفحة إضافة الصوت الجديد"),
      ),
    );
  }
}
