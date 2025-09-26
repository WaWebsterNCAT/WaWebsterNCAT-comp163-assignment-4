# ==============================
# Student Path Simulator
# Demonstrates Python control flow (if/elif/else, logical operators, 'not in', 'is')
# Reference: Concepts adapted from zyBooks Chapter 3 and standard Python documentation
# ==============================

# ==============================
# Initial Setup
# ==============================
student_name = "Will Webster"   # Student's name
current_gpa = 3.5               # Starting GPA
study_hours = 5                 # Starting study hours
social_points = 25              # Starting social points
stress_level = 25               # Starting stress level

# Display initial stats
print(f"Welcome, {student_name}! Starting stats:")
print(f"Study Hours: {study_hours}, Social Points: {social_points}, Stress Level: {stress_level}")

# ==============================
# Path Choice (Easy, Medium, Hard)
# ==============================
choice = input("Choose Your Path: A(Easy), B(Medium), or C(Hard): ").upper()

# Adjust stats based on chosen path and GPA
if choice == "A":  # Easy Path
    if current_gpa >= 3.5:
        study_hours -= 6
        stress_level -= 30
    elif (current_gpa <= 3.4) and (current_gpa > 2.5):
        study_hours -= 3
        stress_level -= 20
    elif current_gpa < 2.4:
        print("Harder Path Recommended")
        study_hours -= 6
        stress_level -= 30
    else:  # current_gpa <= 2.5
        print("Harder Path Recommended")

elif choice == "B":  # Medium Path
    if current_gpa >= 3.5:
        study_hours -= 4
        stress_level -= 20
    elif (current_gpa <= 3.4) and (current_gpa > 2.5):
        study_hours -= 2
        stress_level -= 10
    elif current_gpa < 2.4:
        study_hours += 1
        stress_level -= 5
    else:
        study_hours += 1
        stress_level -= 5

elif choice == "C":  # Hard Path
    if current_gpa >= 3.5:
        study_hours += 8
        stress_level += 5
    elif (current_gpa <= 3.4) and (current_gpa > 2.5):
        study_hours += 4
        stress_level += 10
    elif current_gpa < 2.4:
        study_hours += 10
        stress_level += 20
    else:
        study_hours += 10
        stress_level += 20
else:
    # Invalid input fallback
    print("Invalid path choice. Defaulting to Medium Path (B).")
    choice = "B"

# ==============================
# Study Strategy / Class Selection
# ==============================
Easy_Classes = ["English", "History"]
Medium_Classes = ["Math", "Chemistry", "Biology"]
Hard_Classes = ["Programming", "Calculus", "Psychology"]

all_classes = Easy_Classes + Medium_Classes + Hard_Classes

print(f"Classes: Easy: {Easy_Classes} | Medium: {Medium_Classes} | Hard: {Hard_Classes}")
Choosen_Classes = input("Pick Your Class: ")

# Invalid class check using 'not in'
if Choosen_Classes not in all_classes:
    print("Invalid class selection! No changes applied.")

# Class-specific outcomes
if Choosen_Classes in Medium_Classes and current_gpa >= 3.5:
    study_hours += 3
    stress_level += 5
    social_points += 20
    print("Taking on a challenge while maintaining a high GPA!")

elif Choosen_Classes in Easy_Classes:
    if current_gpa <= 2.4:
        study_hours += 1
        stress_level += 2
        social_points += 30
        print("Put some EFFORT in it!")
    else:
        social_points += 5

elif Choosen_Classes in Hard_Classes:
    study_hours += 8
    stress_level += 30
    social_points += 10
    print("Brace yourself! This class will push your limits.")

# ==============================
# Final Assessment
# ==============================
final_choice = None
final_stats = (study_hours, social_points, stress_level, current_gpa)

# Use 'is' for precise None check
if final_choice is None:
    final_choice = "Burnout Risk"

# Final outcome determination
if Choosen_Classes in all_classes:
    if social_points > 40 and stress_level < 10:
        final_choice = "Social Butterfly Scholar"
    elif study_hours > 15 and stress_level < 40:
        final_choice = "Dedicated Student"
    elif study_hours > 15 and stress_level >= 40:
        final_choice = "Extremely Hard Working Student"
    elif study_hours < 5 and social_points < 20:
        final_choice = "Relaxed Learner"
    else:
        final_choice = "Balanced Student"
else:
    print("Invalid, Pick Your Classes!")

# ==============================
# Results
# ==============================
print(f"\nFinal Outcome: {final_choice}")
print(f"Final Stats (Study Hours, Social Points, Stress Level, GPA): {final_stats}")

