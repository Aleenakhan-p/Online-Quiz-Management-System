```markdown
# 📝 Quiz Management System

A simple yet powerful quiz platform built with JavaScript, PHP, HTML, and CSS. No login hassle—just choose your role and start managing or attempting quizzes instantly.

## ✨ Features

- Role-Based Access – No registration/login required  
  - 👨‍🎓 Student – Attempt any available quiz  
  - 👨‍🏫 Teacher – Create quizzes & view results  
- Dynamic Quiz Creation – Add as many questions as you want in a single view (no separate quiz IDs)  
- Instant Quiz Attempt – Students see all questions on one page  
- Results Tracking – Teachers can view student performance with names and year/section  

## 🚀 How It Works

1. Landing Page – Choose your role (Student or Teacher)  
2. Student View – List of available quizzes → Enter name & section → Attempt quiz → Submit → View score  
3. Teacher View – Create quiz (add unlimited questions) → Manage existing quizzes → See results  

## 🛠️ Tech Stack

| Layer       | Technology                          |
|-------------|-------------------------------------|
| Frontend    | HTML5, CSS3, JavaScript (ES6)       |
| Backend     | PHP 7.4+ (with PDO)                 |
| Database    | MySQL / MariaDB                     |
| Styling     | Custom CSS (responsive)             |


## 🗄️ Database Setup

1. Create a MySQL database named `online_quiz_db`
2. Import the following schema:

```sql
-- Table structure for table `tbl_quiz`
CREATE TABLE `tbl_quiz` (
  `tbl_quiz_id` int(11) NOT NULL AUTO_INCREMENT,
  `quiz_question` text NOT NULL,
  `option_a` text NOT NULL,
  `option_b` text NOT NULL,
  `option_c` text NOT NULL,
  `option_d` text NOT NULL,
  `correct_answer` text NOT NULL,
  PRIMARY KEY (`tbl_quiz_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;

-- Sample data
INSERT INTO `tbl_quiz` (`tbl_quiz_id`, `quiz_question`, `option_a`, `option_b`, `option_c`, `option_d`, `correct_answer`) VALUES
(1, 'What is HTML stands for?', 'How To Make Lumpia', 'Hyper Tronic Mongo Logic', 'Hard To Make Love', 'HyperText Markup Language', 'D'),
(2, 'What is the original acronym of PHP?', 'Hypertext Preprocessor', 'Personal Home Page', 'Programming Happy Pill', 'None of the above', 'B'),
(3, 'CSS is fundamental to?', 'Databases', 'Web design', 'Server-side', 'None of the above', 'B');

-- Table structure for table `tbl_result`
CREATE TABLE `tbl_result` (
  `tbl_result_id` int(11) NOT NULL AUTO_INCREMENT,
  `quiz_taker` text NOT NULL,
  `year_section` text NOT NULL,
  `total_score` int(11) NOT NULL,
  `date_taken` timestamp NOT NULL DEFAULT current_timestamp() ON UPDATE current_timestamp(),
  PRIMARY KEY (`tbl_result_id`)
) ENGINE=InnoDB DEFAULT CHARSET=utf8mb4 COLLATE=utf8mb4_general_ci;
```

3. Configure `includes/db.php` with your database credentials:

```php
<?php 
$servername = "localhost";
$username = "root";
$password = "";
$dbname = "online_quiz_db";

try {
    $conn = new PDO("mysql:host=$servername;dbname=$dbname", $username, $password);
    $conn->setAttribute(PDO::ATTR_ERRMODE, PDO::ERRMODE_EXCEPTION);
} catch (PDOException $e) {
    echo "Failed " . $e->getMessage();
}
?>
```

## 🧪 Installation

1. **Clone or download** this repository into your web server directory (e.g., `htdocs` for XAMPP)
2. **Start** Apache & MySQL (if using XAMPP/WAMP)
3. **Create database** `online_quiz_db` using phpMyAdmin or MySQL CLI
4. **Import the schema** above into your database
5. **Update** `includes/db.php` with your database credentials if different
6. **Open browser** and navigate to `http://localhost/quiz-management-system`

## 📖 Usage Guide

### For Students
1. On home page, click **"Student"**
2. Enter your **Name** and **Year/Section** (these will appear in results)
3. Select a quiz from the list
4. Answer all questions (all shown on one page)
5. Click **Submit** → Instant score display

### For Teachers
1. On home page, click **"Teacher"**
2. Click **"Create New Quiz"**
3. Keep adding questions (unlimited) using the **"Add Question"** button
4. Each question requires:
   - Question text
   - 4 options (A, B, C, D)
   - Correct answer selection (A, B, C, or D)
5. Save quiz → Ready for students
6. Click **"View Results"** to see:
   - Student name
   - Year/Section
   - Total score
   - Date taken

## ⚙️ Configuration Notes

- **Single table design** – All questions stored in `tbl_quiz` (no separate quiz grouping)
- **Single-page attempt** – Students see all questions at once (no pagination)
- **Simple scoring** – Each correct answer = 1 point
- **PDO connection** – Secure database interactions with prepared statements
- **No separate quiz IDs** – Add questions continuously in one view

## 🔧 Customization Ideas

- Add timer for each quiz
- Export results as CSV
- Shuffle questions/options
- Add image support for questions
- Basic password protection for teacher role
- Group questions into different quiz categories

## 📊 Database Structure Reference

| Table | Description |
|-------|-------------|
| `tbl_quiz` | Stores all quiz questions, options, and correct answers |
| `tbl_result` | Stores student attempt results with name, section, score, and timestamp |

## 🤝 Contributing

Feel free to fork this project and enhance it. Pull requests are welcome!

## 📄 License

MIT License – Use freely for learning and teaching purposes.

## 📧 Support

For issues or suggestions, please open a GitHub issue or contact the project maintainer.

---

**Made with ❤️ using JS, PHP (PDO), HTML & CSS**
```
