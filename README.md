import random
students = ['Аполлон', 'Ярослав', 'Александра', 'Дарья', 'Ангелина']
students.sort()
classes = ['Математика', 'Русский язык', 'Информатика']
students_marks = {}
for student in students:
    students_marks[student] = {}
    for class_ in classes:
        marks = [random.randint(1, 5) for i in range(3)]
        students_marks[student][class_] = marks
for student in students:
    print(f'''{student} {students_marks[student]}''')

while True:
    command = int(input('Введите команду:'))
    if command == 1:
        print('1. Добавить оценку ученика по предмету')
        student = input('Введите имя ученика:')
        class_ = input('Введите предмет:')
        mark = int(input('Введите оценку:'))
        if student in students_marks.keys() and class_ in students_marks[student].keys():
            students_marks[student][class_].append(mark)
            print(f': {student},{class_},{mark}')
            print(f'''{student} {students_marks[student]}''')
        else:
            print('Неверное имя ученика или названия предмета')
    elif command == 2:
        print('2.Добавить ученика')
        new_student = input('Введите имя: ')
        students.append(new_student)
        print('Новый ученик добавлен')
        print()
        print(f':{students}')

        students_marks[new_student] = {
            'Математика': [random.randint(1, 5) for i in range(3)],
            'Русский язык': [random.randint(1, 5) for i in range(3)],
            'Информатика': [random.randint(1, 5) for i in range(3)],
        }
        students.sort()

    elif command == 3:

        print('3.Добавить предмет')
        classes = ['Математика', 'Русский язык', 'Информатика']
        new_class_ = input('Введите новый предмет: ')
        classes.append(new_class_)
        print(f':{classes}')
        print('Новый предмет добавлен')

        print()
    elif command == 4:
        print('.Найти студента в списке')
        student = input('Введите имя:')
        if student in students_marks.keys():
            print('Выводим оценки по предметам')
            print(f'''{student} {students_marks[student]}''')
        else:
            print('ОШИБКА: неверное имя ученика')

    elif command == 5:
        print('5.Удалить ученика')
        end_student = input('Введите ученика, которого хотите удалить: ')
        if end_student in students_marks:
            del students_marks[end_student]
            print(students_marks)
        else:
            print('Этого ученика в списке нет')
    elif command == 6:
        print('6.Вывести средний балл по всем предметам по каждому ученику')
        for student in students:
            print(student)
            for class_ in classes:
                marks_sum = sum(students_marks[student][class_])
                marks_count = len(students_marks[student][class_])
                print(f'{class_} - {marks_sum // marks_count}')

    elif command == 7:
        print('7. Вывести все оценки по всем ученикам')
        for student in students:
            print(student)
            for class_ in classes:
                print(f'\t{class_}-{students_marks[student][class_]}')

    elif command == 8:
        print('8. Выход из программы')
        break

