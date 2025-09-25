# ==============================
# Student Path Simulator with 'not in' and Full Branching
# ==============================

student_name = "Will Webster"
current_gpa = 3.5
study_hours = 5
social_points = 25
stress_level = 25

print(f"Welcome, {student_name}! Starting stats:")
print(f"Study Hours: {study_hours}, Social Points: {social_points}, Stress Level: {stress_level}")

# Path Choice
choice = input("Choose Your Path: A(Easy), B(Medium), or C(Hard): ").upper()

# Course Planning Adjustments
if choice == "A":
    if current_gpa >= 3.5:
        study_hours -= 6
        stress_level -= 30
    elif 2.5 < current_gpa <= 3.4:
        study_hours -= 3
        stress_level -= 20
    else:  # current_gpa <= 2.5
        print("Harder Path Recommended")

elif choice == "B":
    if current_gpa >= 3.5:
        study_hours -= 4
        stress_level -= 20
    elif 2.5 < current_gpa <= 3.4:
        study_hours -= 2
        stress_level -= 10
    else:
        study_hours += 1
        stress_level -= 5

elif choice == "C":
    if current_gpa >= 3.5:
        study_hours += 8
        stress_level += 5
    elif 2.5 < current_gpa <= 3.4:
        study_hours += 4
        stress_level += 10
    else:
        study_hours += 10
        stress_level += 20

else:
    print("Invalid path choice. Defaulting to Medium Path (B).")
    choice = "B"

# Study Strategy / Class Selection
Easy_Classes = ["English", "History"]
Medium_Classes = ["Math","Chemistry", "Biology"]
Hard_Classes = ["Programming", "Calculus", "Psychology"]
all_classes = Easy_Classes + Medium_Classes + Hard_Classes

print(f"Classes: Easy: {Easy_Classes} | Medium: {Medium_Classes} | Hard: {Hard_Classes}")
Choosen_Classes = input("Pick Your Class: ")

# Using 'not in' for invalid class selection
if Choosen_Classes not in all_classes:
    print("Invalid class selection! No changes applied.")

elif Choosen_Classes in Easy_Classes:
    if current_gpa <= 2.4:
        study_hours += 1
        stress_level += 2
        social_points += 30
        print("Put some EFFORT in it!")
    else:
        study_hours += 0
        stress_level += 0
        social_points += 5

elif Choosen_Classes in Medium_Classes:
    if current_gpa >= 3.5:
        study_hours += 3
        stress_level += 5
        social_points += 20
        print("Taking on a challenge while maintaining a high GPA!")
    else:
        study_hours += 5
        stress_level += 15
        social_points += 10

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

# Determine final outcome based on stats
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

# Print final outcome
if final_choice is not None:
    print(f"\nFinal Outcome: {final_choice}")
else:
    print("\nFinal Outcome: Undetermined (Probably due to invalid initial choice).")

print(f"Final Stats (Study Hours, Social Points, Stress Level, GPA): {final_stats}")
