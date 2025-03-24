import 'package:flutter/material.dart';
import 'package:cloud_firestore/cloud_firestore.dart';

class UsersListPage extends StatefulWidget {
  @override
  _UsersListPageState createState() => _UsersListPageState();
}

class _UsersListPageState extends State<UsersListPage> {
  TextEditingController searchController = TextEditingController();
  String searchQuery = "";

  @override
  Widget build(BuildContext context) {
    return Scaffold(
      body: Stack(
        children: [
          // Background Image
          Container(
            decoration: BoxDecoration(
              image: DecorationImage(
                image: AssetImage("assets/img4.jpg"),
                fit: BoxFit.cover,
              ),
            ),
          ),
          Column(
            children: [
              // Header
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
                      "المستخدمين",
                      style: TextStyle(
                        fontSize: 24,
                        color: Colors.white,
                        fontWeight: FontWeight.bold, // Bold text
                      ),
                    ),
                    Spacer(),
                  ],
                ),
              ),


              // Search Bar (Aligned to the Right)
              Padding(
                padding: const EdgeInsets.all(15.0),
                child: TextField(
                  textAlign: TextAlign.right, // Align text to the right
                  controller: searchController,
                  onChanged: (value) {
                    setState(() {
                      searchQuery = value.toLowerCase();
                    });
                  },
                  decoration: InputDecoration(
                    filled: true,
                    fillColor: Colors.white.withOpacity(0.9),
                    hintText: "...البحث عن مستخدم",
                    hintStyle: TextStyle(color: Colors.grey, fontSize: 16),
                    prefixIcon: Icon(Icons.search),
                    border: OutlineInputBorder(
                        borderRadius: BorderRadius.circular(10)),
                  ),
                ),
              ),

              // Table Headers (Bold)
              Padding(
                padding: const EdgeInsets.symmetric(horizontal: 20, vertical: 5),
                child: Row(
                  mainAxisAlignment: MainAxisAlignment.spaceBetween,
                  children: [
                    Text(
                      "البريد الإلكتروني",
                      style: TextStyle(
                        fontSize: 20,
                        fontWeight: FontWeight.bold, // Bold text
                        color: Colors.white,
                      ),
                    ),
                    Text(
                      "اسم المستخدم",
                      style: TextStyle(
                        fontSize: 20,
                        fontWeight: FontWeight.bold, // Bold text
                        color: Colors.white,
                      ),
                    ),
                  ],
                ),
              ),

              // User List
              Expanded(
                child: StreamBuilder<QuerySnapshot>(
                  stream: FirebaseFirestore.instance.collection('User').snapshots(),
                  builder: (context, snapshot) {
                    if (!snapshot.hasData) {
                      return Center(child: CircularProgressIndicator());
                    }

                    var users = snapshot.data!.docs;

                    // Filter users based on search input
                    var filteredUsers = users.where((user) {
                      String username = (user['username'] ?? '').toLowerCase();
                      String email = (user['email'] ?? '').toLowerCase();
                      return username.contains(searchQuery) || email.contains(searchQuery);
                    }).toList();

                    return ListView.builder(
                      itemCount: filteredUsers.length,
                      itemBuilder: (context, index) {
                        var user = filteredUsers[index];
                        return Padding(
                          padding: const EdgeInsets.symmetric(horizontal: 15, vertical: 5),
                          child: Container(
                            padding: EdgeInsets.all(15),
                            decoration: BoxDecoration(
                              color: Colors.white.withOpacity(0.9),
                              borderRadius: BorderRadius.circular(10),
                            ),
                            child: Row(
                              mainAxisAlignment: MainAxisAlignment.spaceBetween,
                              children: [
                                Text(
                                  user['email'] ?? 'No Email',
                                  style: TextStyle(fontSize: 16, color: Colors.black),
                                ),
                                Text(
                                  user['username'] ?? 'No Name',
                                  style: TextStyle(
                                    fontSize: 16,
                                    color: Colors.black,
                                    fontWeight: FontWeight.bold, // Bold usernames
                                  ),
                                ),
                              ],
                            ),
                          ),
                        );
                      },
                    );
                  },
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
        currentIndex: 3,
        items: [
          BottomNavigationBarItem(icon: Icon(Icons.home, color: Colors.white), label: ""),
          BottomNavigationBarItem(icon: Icon(Icons.checklist, color: Colors.white), label: ""),
          BottomNavigationBarItem(icon: Icon(Icons.person, color: Colors.white), label: ""),
          BottomNavigationBarItem(icon: Icon(Icons.settings, color: Colors.blue), label: ""),
        ],
      ),
    );
  }
}
