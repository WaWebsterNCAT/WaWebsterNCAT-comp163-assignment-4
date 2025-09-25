student_name = "Will Webster"
current_gpa = 3.5
study_hours = 5
social_points = 25
stress_level = 25

print("Welcome, these are your Starting Stats", student_name, study_hours, social_points,)
print("Choose Your Path: A(Easy), B(Medium), or C(Hard)")


#Course Planning
choice = input("Choose Your Path: A(Easy), B(Medium), or C(Hard): ").upper()

if choice == "A":
    if current_gpa >= 3.5:
        study_hours = study_hours - 6
        stress_level = stress_level - 30
    elif (current_gpa <= 3.4) and (current_gpa > 2.5):
        study_hours = study_hours - 3
        stress_level = stress_level - 20
    elif current_gpa < 2.4:
        print("Harder Path Recommened")
       
elif choice == "B":
    if current_gpa >= 3.5:
        study_hours = study_hours - 4
        stress_level = stress_level - 20
    elif (current_gpa <= 3.4) and (current_gpa > 2.5):
        study_hours = study_hours - 2
        stress_level = stress_level - 10
    elif current_gpa < 2.4:
        study_hours = study_hours + 1
        stress_level = stress_level - 5
       
elif choice == "C":
    if current_gpa >= 3.5:
        study_hours = study_hours + 8
        stress_level = stress_level + 5
    elif (current_gpa <= 3.4) and (current_gpa > 2.5):
        study_hours = study_hours + 4
        stress_level = stress_level + 10
    elif current_gpa < 2.4:
        study_hours = study_hours + 10
        stress_level = stress_level + 20
else:
    print("Invalid")
#Study Strat
Easy_Classes = ["English", "History"]
Medium_Classes =["Math","Chemistry", "Biology"]
Hard_Classes = ["Programming", "Calculus", "Psychology"]
all_classes = Easy_Classes + Medium_Classes + Hard_Classes

print(f"Classes: Easy: {Easy_Classes} Medium: {Medium_Classes} Hard: {Hard_Classes}")
Choosen_Classes = input("Pick Your Classes:")

if Choosen_Classes in Easy_Classes and current_gpa <= 2.4:
    study_hours = study_hours + 1
    stress_level = stress_level + 2
    social_points = social_points + 30
    print("Put some EFFORT in it!")

if Choosen_Classes in Medium_Classes and current_gpa >= 3.5:
    study_hours = study_hours + 3
    stress_level = stress_level + 5
    social_points = social_points + 20
    print("Taking on a challenge while maintaining a high GPA!")

elif Choosen_Classes in Hard_Classes or Medium_Classes:
    study_hours = study_hours + 8
    stress_level = stress_level + 30
    social_points = social_points + 10

elif Choosen_Classes not in all_classes:
    print("Invalid, Pick Your Classes!")
