---
layout: default
title: Syllabus
nav_order: 1
---

# Instructor

{% assign instructors = site.staffers | where: 'role', 'Instructor' %} {% for staffer in instructors %} {{ staffer }} {% endfor %}


# Meeting Times

| Session | Day | Time | Location |
|---------|-----|------|----------|
| Lecture | TH | 9:00AM-10:15AM | NB 236 |
| Lab | W | 1:30PM-4:30PM | NB 112 |


# Course description 

Fundamental electric-circuit techniques including: time domain transient responses for 1st and 2nd order circuits, Laplace transforms, Fourier series, and filters.  Lecture and lab combination.


# Learning outcomes

The student will:
- A knowledge of transient responses for 1st and 2nd order circuits.
- An understanding of how Laplace transforms apply to circuits.
- An understanding of how Fourier series and transforms apply to signals.
- An ability to construct simple passive filters.



# Textbook 

Electric Circuits, 10th Edition, by James W. Nilsson and Susan Riedel, [any edition will work]


NOTE:  The lectures will follow this text \emph{very} closely.  I strongly advise you to read the book as we go through the course.  Assignments will not be based on problems on from the book, so if you can find a 1\textsuperscript{st} edition of the book, you can save some money.

# Assignments 

You will have weekly homework assignments based on the material covered in class.  These assignments will not be collected in class.  However, each week in lab or lecture, you will be given a short quiz based on one homework problem.  You will have 15 minutes to complete the quiz.  The quizzes will be closed book and closed notes.  The quizzes will be graded for correctness and completeness.  There are no makeup quizzes.  The lowest two quiz grades will be dropped.



# Laboratory assignments 

Laboratory assignments will be done individually if there is insufficient lab equipment, in which case the hardware portion may be done in pairs.  Each lab will, generally, require a submitted lab report and associated code written for the lab.  The lab report must be completed using the provided \LaTeX\ template.

Most labs will have a programming component.  You must be proficient in numerical Python (NumPy, SciPy, Matplotlib) at the level of ECE 1400.  You are welcome to use lab computers for your programming.  Furthermore, you may use your personal machines if they are configured so that you can do the assignments.  All unit tests will use Python 3.12.  We will use GitHub for code submission, so ensure you have a GitHub account.  This course will require some level of Python programming, but it will be at a relatively basic level (e.g., making plots, solving equations numerically, etc.).  The programming intensity will scale with the progress of ECE 1400 as it is a corequisite.  

The lab due dates and times will generally be the Friday the week indicated on the schedule.



# Late work policy 

Late work will not be accepted after the due date.  Once the GitHub repository is closed, you will not be able to submit your work.  Similarly, once the Canvas assignment is closed, you will not be able to submit your lab reports.



# Exams 

There will be two midterm examinations during the semester.  There will also be a comprehensive final examination.  The objective of the examinations will be to test your knowledge of fundamentals and your ability to apply the concepts learned in the class in situations you may not have encountered before.  You may bring one sheet of formulas for the first exam, two sheets of formulas for the second exam, and three sheets of formulas to the final exam.


# Grading

As shown below, grades are based on the weighted average of the exams, homework, and laboratory assignments.

| Item | Percentage |
|------|------------|
| homework | 15% |
| labs | 20% |
| midterms | 20% |
| final | 25% |

Letter grades are assigned according to the scale below. These are the maximum cutoffs for each letter.  As an instructor, I reserve the right to lower the percentage cutoffs at the end of the semester as appropriate.

| Letter | Percentage |
|--------|------------|
| A | 93% |
| A- | 90% |
| B+ | 86% |
| B | 83% |
| B- | 80% |
| C+ | 76% |
| C | 73% |
| C- | 70% |
| D+ | 66% |
| D | 63% |


# Campus closure 

If the class needs to be held virtually due to campus closure, sickness, or any other appropriate reason, you will receive a notification from your instructor via Canvas. Remember that attendance is just as important virtually as in the face-to-face option. During video conferencing, be present, avoid multitasking, and wait for your turn to speak and/or contribute to the class discussion. Be courteous and respectful of your classmates. As stated in the class recording policy, you may not record any segments and/or the full class unless you have authorization from the instructor. If you do not have the technology necessary for video conferencing, contact your instructor as soon as possible. This policy applies also to virtual office hours.



# Disability services 

If you require accommodations or services due to a disability, please contact Disability Services (DS) in room 181 of the Student Services Center (Ogden campus) or room 262 Building D2 (Davis Campus). Disability Services can arrange to provide course materials (including this syllabus) in alternative formats upon request.



# Professionalism and respect 

The sense of human dignity and belonging of all members of the Weber State community is a necessary part of a healthy learning environment. Therefore, you should practice civil deportment, and avoid treating others in a manner that is demeaning or derisive in any respect. Diverse viewpoints and opinions are welcome in this class, and we will practice the mutual deference so important in the world of work when expressing them. Thus, while I encourage you to share your opinions, you will be expected to do so in a manner that is respectful toward others.



# Recording 

The university prohibits students from recording class lectures unless the faculty member grants explicit permission (PPM 6-22.6.6). Any lectures recorded and posted on Canvas or shared to your Weber State University student email are for the exclusive use of students enrolled in the class and may not be shared without previous authorization. Violations will be referred to the Dean of Students for adjudication under the student code (PPM 6-22).



# Academic integrity 

As part of the student code (PPM 6-22), you are expected to be academically honest and ethical. Academic dishonesty includes cheating; plagiarizing; colluding with others to be dishonest; falsifying information; giving, selling, or receiving unauthorized course or test information; using a tool or other aid not explicitly permitted by your instructor such as generative AI (e.g. ChatGPT) to complete assignments or exams; or infringing on others' copyrights and intellectual property. Academic dishonesty can have serious consequences in the class and/or at WSU. Be sure, if you borrow an idea, to express it in language entirely your own and let the reader know the idea's source in a citation note.

For software submissions, I will routinely run your code through a plagiarism detection system.  If you are caught cheating, you will receive a zero for the assignment and may be reported to the Dean of Students.  A second infraction will result in a failing grade for the course.



# Core beliefs and challenging subject matter 

Faculty members teach in line with the best standards of their discipline and choose materials appropriate to help the class master expected course outcomes. A student may disagree with course content, but unless the content conflicts with a student's core beliefs, students are expected to engage professionally, as described above. If after reading the syllabus and class program, you expect there will be a conflict with your core beliefs, you should consider withdrawing from the class before the last day to drop classes without penalty. If you find this solution unworkable, you may request a resolution from the instructor, in writing with a copy to the department chair, explaining what burden the class requirement would place on your beliefs. Students who are not satisfied with the outcome may seek assistance through the Office of Equal Opportunity.



# Student responsibilities 

As a student at Weber State University, you are expected to act responsibly and appropriately as you attend a public institution of higher education. When you enroll as a student at WSU, you agree to abide by the standards of appropriate and responsible behavior outlined in the student code (PPM 6-22). This applies to your behavior as an individual when participating in group settings on campus and if you represent Weber State University at an off-campus event. Choosing to ignore these important student responsibilities could result in university disciplinary actions.



# Harassment, discrimination, and sexual misconduct 

Weber State University is committed to providing an environment free from harassment and other forms of discrimination based upon race, color, national origin, pregnancy, and pregnancy-related conditions such as childbirth, false pregnancy, miscarriage, abortion, or related conditions, (including recovery), genetics, disability (see PPM 3-34), religion, sex, sexual orientation, gender identity/expression, veteran, active military status, age (over 40 in employment discrimination), and other classifications protected by law. If you have questions regarding the university's policy against discrimination and harassment, or if you have questions about reporting discrimination or harassment, you may contact the university's Office of Equal Opportunity (OEO) by calling 801-626-6240 or visit the OEO website.


