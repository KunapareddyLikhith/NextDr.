# NextDr.
# Health & Nutrition App Database

## Overview
The **Health & Nutrition App Database** is designed to store and manage user health data, meal tracking, fitness progress, and insights. This relational database is built using **MySQL** and ensures efficient storage and retrieval of user health records.

## Database Schema
The database consists of the following tables:

### **Users Table** (`Users`)
Stores user profile information.
| Column Name  | Data Type  | Description  |
|-------------|-----------|-------------|
| user_id    | CHAR(36) (PK) | Unique user identifier |
| name       | VARCHAR(255) | User's full name |
| email      | VARCHAR(255) | Unique email ID |
| password   | VARCHAR(255) | Hashed password |
| age        | INT | User's age |
| weight     | FLOAT | User's weight in kg |
| height     | FLOAT | User's height in cm |
| bmi        | FLOAT | Body Mass Index |
| preferences | JSON | Stores goals and ayurvedic preference |

### **Meals Table** (`Meals`)
Stores meal details, including photos and nutritional data.
| Column Name  | Data Type  | Description  |
|-------------|-----------|-------------|
| meal_id    | CHAR(36) (PK) | Unique meal identifier |
| user_id    | CHAR(36) (FK) | References Users table |
| image_url  | TEXT | Image of the meal |
| timestamp  | DATETIME | Meal entry time |
| nutrition  | JSON | Stores meal nutrition details |

### **Fitness Data Table** (`FitnessData`)
Tracks user fitness activities.
| Column Name  | Data Type  | Description  |
|-------------|-----------|-------------|
| fitness_id | CHAR(36) (PK) | Unique fitness data ID |
| user_id    | CHAR(36) (FK) | References Users table |
| steps      | INT | Steps taken |
| calories_burned | FLOAT | Calories burned |
| heart_rate | FLOAT | Heart rate (bpm) |
| activity_date | TIMESTAMP | Date of activity |

### **Health Goals Table** (`HealthGoals`)
Stores user-defined health goals.
| Column Name  | Data Type  | Description  |
|-------------|-----------|-------------|
| goal_id    | CHAR(36) (PK) | Unique goal identifier |
| user_id    | CHAR(36) (FK) | References Users table |
| goal_description | TEXT | Goal details |
| target_weight | FLOAT | Target weight goal |
| deadline   | DATE | Deadline to achieve the goal |

### **Insights Table** (`Insights`)
Stores health trend insights.
| Column Name  | Data Type  | Description  |
|-------------|-----------|-------------|
| insight_id | CHAR(36) (PK) | Unique insight identifier |
| user_id    | CHAR(36) (FK) | References Users table |
| insight_text | TEXT | Insight or recommendation |
| created_at  | TIMESTAMP | Date of insight generation |

## Database Setup
### **1. Clone the Repository**
```bash
git clone https://github.com/KunapareddyLikhith/NextDr..git
cd NextDr.
```

### **2. Import Database**
1. Open MySQL and create the database:
   ```sql
   CREATE DATABASE health_nutrition_app;
   USE health_nutrition_app;
   ```
2. Execute the schema SQL file:
   ```bash
   mysql -u your_user -p health_nutrition_app < schema.sql
   ```

## Sample Queries
### **Insert Sample User**
```sql
INSERT INTO Users (user_id, name, email, password, age, weight, height, bmi, preferences)
VALUES ('uuid1', 'John Doe', 'john@example.com', 'hashedpassword', 30, 75.5, 180, 23.3, '{"goals": ["fitness", "nutrition"], "ayurveda": true}');
```

### **Retrieve User Meals**
```sql
SELECT * FROM Meals WHERE user_id = 'uuid1';
```

## Security & Best Practices
✅ **Use UUIDs** instead of auto-incremented IDs for security.
✅ **Hash passwords** using bcrypt before storing.
✅ **Set Foreign Key Constraints** for data consistency.
✅ **Use Role-Based Access Control (RBAC)** for restricted database access.
✅ **Automate Daily Backups** to prevent data loss.

## Contributions
Feel free to fork this repository and contribute improvements!

## License
This project is licensed under the MIT License.

