import random

# список учеников
students = ['Аполлон', 'Ярослав', 'Александра', 'Дарья', 'Ангелина']
# отсортируем список учеников
students.sort()
# список предметов
classes = ['Математика', 'Русский язык', 'Информатика']
# пустой словарь с оценками по каждому ученику и предмету
students_marks = {}
# сгенерируем данные по оценкам:
# цикл по ученикам
for student in students:
    students_marks[student] = {}
    for class_ in classes:
        marks = [random.randint(1, 5) for i in range(3)]
        students_marks[student][class_] = marks
# выводим получившийся словарь с оценками:
for student in students:
    print(f"{student}\n{students_marks[student]}")

print('''
Список команд:
1. Добавить оценки ученика по предмету
2. Вывести средний балл по всем предметам по каждому ученику
3. Вывести все оценки по всем ученикам
4. Удалить ученика
5. Внести нового ученика с предметами и оценками
6. Редактировать оценки
7. Вывести все оценки определенного ученика
8. Вывести средний балл по каждому предмету ученика
9. Добавить новый предмет для ученика
10. Удалить предмет у ученика
11. Выход из программы
''')

# функции для работы с данными
def delete_student():
    for student in students:
        print(student)
    student = input('Введите имя ученика для удаления: ')
    if student in students_marks:
        del students_marks[student]
        students.remove(student)
        print(f'Ученик {student} удален.')
    else:
        print('Ученик не найден.')

def edit_grades():
    student = input('Введите имя ученика: ')
    if student in students_marks:
        class_ = input('Введите предмет: ')
        if class_ in students_marks[student]:
            print(f'Текущие оценки: {students_marks[student][class_]}')
            new_marks = input('Введите новые оценки через пробел: ')
            students_marks[student][class_] = list(map(int, new_marks.split()))
            print(f'Оценки обновлены: {students_marks[student][class_]}.')
        else:
            print('Предмет не найден.')
    else:
        print('Ученик не найден.')

def view_student_grades():
    student = input('Введите имя ученика: ')
    if student in students_marks:
        print(f'Оценки ученика {student}:')
        for class_, marks in students_marks[student].items():
            print(f'  {class_}: {marks}')
    else:
        print('Ученик не найден.')

def average_per_subject():
    student = input('Введите имя ученика: ')
    if student in students_marks:
        print(f'Средний балл по предметам для ученика {student}:')
        for class_, marks in students_marks[student].items():
            avg = sum(marks) / len(marks)
            print(f'  {class_}: {avg:.2f}')
    else:
        print('Ученик не найден.')

def add_subject():
    student = input('Введите имя ученика: ')
    if student in students_marks:
        class_ = input('Введите название нового предмета: ')
        if class_ not in students_marks[student]:
            students_marks[student][class_] = []
            print(f'Предмет {class_} добавлен для ученика {student}.')
        else:
            print('Предмет уже существует.')
    else:
        print('Ученик не найден.')

def delete_subject():
    student = input('Введите имя ученика: ')
    if student in students_marks:
        class_ = input('Введите название предмета для удаления: ')
        if class_ in students_marks[student]:
            del students_marks[student][class_]
            print(f'Предмет {class_} удален у ученика {student}.')
        else:
            print('Предмет не найден.')
    else:
        print('Ученик не найден.')

def add_new_student():
    student = input('Введите имя нового ученика: ')
    if student not in students_marks:
        students.append(student)
        students.sort()
        students_marks[student] = {}
        print('Введите предметы и оценки для нового ученика.')
        while True:
            class_ = input('Введите название предмета (или оставьте пустым для завершения): ')
            if not class_:
                break
            marks = input(f'Введите оценки для предмета {class_} через пробел: ')
            students_marks[student][class_] = list(map(int, marks.split()))
        print(f'Ученик {student} добавлен с предметами и оценками.')
    else:
        print('Ученик с таким именем уже существует.')

while True:
    try:
        command = int(input('Введите команду: '))
    except ValueError:
        print('Ошибка: команда должна быть числом. Попробуйте снова.')
        continue

    if command == 1:
        print('1. Добавить оценку ученика по предмету')
        student = input('Введите имя ученика: ')
        class_ = input('Введите предмет: ')
        try:
            mark = int(input('Введите оценку: '))
        except ValueError:
            print('Ошибка: оценка должна быть числом.')
            continue
        if student in students_marks.keys() and class_ in students_marks[student].keys():
            students_marks[student][class_].append(mark)
            print(f'Для {student} по предмету {class_} добавлена оценка {mark}')
        else:
            print('ОШИБКА: неверное имя ученика или название предмета')
    elif command == 2:
        print('2. Вывести средний балл по всем предметам по каждому ученику')
        for student in students:
            print(student)
            for class_ in classes:
                marks_sum = sum(students_marks[student][class_])
                marks_count = len(students_marks[student][class_])
                avg = marks_sum // marks_count if marks_count > 0 else 0
                print(f'{class_} - {avg}')
            print()
    elif command == 3:
        print('3. Вывести все оценки по всем ученикам')
        for student in students:
            print(student)
            for class_ in classes:
                print(f'  {class_} - {students_marks[student][class_]}')
            print()
    elif command == 4:
        delete_student()
    elif command == 5:
        add_new_student()
    elif command == 6:
        edit_grades()
    elif command == 7:
        view_student_grades()
    elif command == 8:
        average_per_subject()
    elif command == 9:
        add_subject()
    elif command == 10:
        delete_subject()
    elif command == 11:
        print('4. Выход из программы')
        break
    else:
        print('Неверная команда.')
