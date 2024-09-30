# Работа 1 - Компонент физики Rigidbody в Unity
Отчет по лабораторной работе #1 выполнил(а):
- Лошаков Данил Евгеньевич
- РИ-320930
- АТ-01
# Цель работы: изучить свойства компонента Rigidbody, освоить реализацию игровых механик с применением свойств этого компонента

![image](https://github.com/user-attachments/assets/269a5c64-0d18-4b4e-be9e-59d721a95636)

Рекомендуемые источники для изучения:
1.	Rigidbody Unity Documentation
2.	Тема Rigidbogy в материалах лекции

# Задания к работе
1.1 Создайте сцену, изображенную на рисунке ниже:


## Создание сцены
![image](https://github.com/user-attachments/assets/a2987337-a441-4d1e-933d-d476957a0000)


2.2 Добавьте компонент Rigidbody на объекты CubeSid и CubeNancy. Запустите сцену, проверьте что кубики падают вниз и останавливаются на земле.
## Rigidbody для CubeSid

![image](https://github.com/user-attachments/assets/1bb3255a-0f28-41c8-bbd9-b85f814e3bf0)


## Rigidbody для CubeNancy

![image](https://github.com/user-attachments/assets/f8cd7979-eb36-4c6d-8b8e-161ffb7b5c71)


2.3 Установите массу для объекта CubeSid = 1 кг, для объекта CubeNancy = 100 кг. Запустите сцену. Какой из двух кубов быстрее достигнет земли и почему? Дайте развернутый ответ:

------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Кубы упадут одновременно, так как mass не влияет на скорость падения объектов, он влияет лишь на то, как тело взаимодействует с другими RigidBody.
------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2.5 Измените значение свойства Drag внутри компонента Rigidbody так, чтобы CubeSid достигал земли быстрее чем CubeNancy.

![image](https://github.com/user-attachments/assets/3a0ce245-442e-4d10-98c6-7006e5c8f849)

2.6 Дополните сцену сферой и эстокадой, по которой будет скатываться сфера с компонентом физии твердого тела Rigidbody. Установите массу сферы равную 100 кг, размер оставьте по умолчанию. Поместите сферу в верхней части эстокады, а кубы Sid & Nancy будут помещаться в нижней части с целью тестирования механики:

![image](https://github.com/user-attachments/assets/c992cf7a-2f78-4d78-b459-058ad9e11844)

![image](https://github.com/user-attachments/assets/ad796f4d-3471-4cdc-b064-aaaa13e47204)


2.7 Протестируйте наезд сферы на кубы разной массы (1 и 100 кг). Опишите характер столкновения, влияет ли параметр Drag (если да, — то как?)
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Сфера массой 100 кг наезжая на куб массой 1 кг сдвигает куб и едет дальше. Сфера массой 100 кг наезжая на куб массой 100 кг отскакивает назад, а куб переворачивается. Поэксперементировав с параметроом drag, я понял, что он добавляет какое то сопротивление и замедляет объект.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2.8 Модифицируйте сцену для тестирования параметров Drag и Angular Drag:

![image](https://github.com/user-attachments/assets/327e3dda-6220-441c-a763-b6f90903c6c0)

## Модификация сцены

![image](https://github.com/user-attachments/assets/5312de27-051c-40c8-9673-1662180cd541)


2.9 Протестируйте, что произойдет если указать разные значения для Drag и Angular Drag. Имеет ли это какую-то практическую ценность? Почему по умолчанию значение Angular Drag близко к нулю, но не равно ему? Проверьте что произойдет, если указать значение Angular Drag = 0. Дайте развернутый ответ:

-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Я считаю то что drag отвечает за сопротивление а angular drag за вращение объекта. Ими можно воспользоваться чтобы показать перемещение объектов из одной среды, например воздуха, в другую, например воду, и будет наглядно показано, что сопротивление жидкости > сопротивлению газа. 
Я думаю, что значение Angular Drag близко к нулю, но не равно ему, потому что Angular Drag влияет на вращения объекта, потому что небольшое значение вращения объекта, создает более реалистичное движение.
Если поставить значие 0 у angular drug объект начнет больше вращаться, как будто перестало действовать сопротивление.
-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2.10 Назначьте на платформу Stage компонент Rigidbody и отключите гравитацию (Use Gravity). Проверьте, что произойдет при запуске сцены.

## Отключил гравитацию

![image](https://github.com/user-attachments/assets/9f10cb1e-9610-47bd-868e-e432dddeea05)


2.11 Во вкладке Project Settings - Physics увеличьте значение силы гравитации. Подберите такое значение силы, при котором скорость падения достаточно большая для того, чтобы движок не успел обработать столкновение кубов Sid & Nancy с платформами Stage и Ground. В некоторых случаях можно добавиться интересного эффекта:


Напишите найденное значение и от чего оно зависит (по вашему мнению):
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Если поставить значение physics меньше, чем -300, куб с массой 100 кг пройдет через ground, а после значения -7000 куб проходит через stage из за того что обработчик не успевает обработать их столкновение.
--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2.12 Верните значение гравитации к настройкам по умолчанию.

## Вернул

2.13 Для объекта Stage зафиксируйте свойство FreezePosition внутри компонента Rigidbody таким образом, чтобы объект вращался вокруг оси, не падая вниз. Укажите, как должна выглядеть настройка FreezePosition?

![image](https://github.com/user-attachments/assets/3011d4e7-b2c7-4c32-89ac-f5b3817a5758)


-------------------------------------------------------------------------------------------------------------------------------------------------------------
Нужно поставить freezeposition по всем осям, и тогда объект будет крутиться на месте, но не перемещаться.
-------------------------------------------------------------------------------------------------------------------------------------------------------------

2.14 isKinematic позволяет сделать объект нефизическим. Если поставить галочку isKinematic, — то объект будет жестко стоять на месте. При этом управлять кинематическими свойствами объекта можно во время выполнения сцены. Запустите сцену повторно и активируйте свойство isKinematic на объекте Stage во время вращения. Что произойдет, если галочку вновь отключить при запущенной сцене? Продолжит ли платформа своё вращение?

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
При включении галочки на параметре после запуска сцены вращение платформы прекратится, при этом и если галочку снова отключить, платформа не будет вращаться.
---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2.15 Поднимете объект SidCube на высоту 1000 метров и запустите сцену. Дождитесь момента, когда куб достигнет земли Ground при падении. По какой причине куб проскакивает землю, не останавливаясь? Какие могут быть способы решения этой проблемы?

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
Куб проскакивает ground потому что не успевает просчитаться физика. Данная проблема решается с помощью настройки коллизии Collision Detection, которая позволяет настроить RigidBody для непрерывного обнаружения столкновений.
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------

2.16 В скрипт файле ниже приведён пример, в котором происходит управление свойствами компонента RigidBody при нажатии на кнопку Space. Для работы созданный скрипт-файл следует подключить к объекту, свойствами которого планируется управлять при нажатии на клавишу Space:

```C#

using UnityEngine;

public class RigidbodyMod : MonoBehaviour
{
    private Rigidbody _rb;

    void Start()
    {
        _rb = GetComponent<Rigidbody>();
    }

    void Update()
    {
        if(Input.GetKeyDown(KeyCode.Space)) 
        {
            //_rb.isKinematic = true;
            _rb.mass= 1.0f;
            _rb.drag = 0;
            _rb.angularDrag = 0.05f;
            _rb.useGravity= true;
        }
    }
}

```
2.17 Используя этот сценарий и знания, полученные в работе, доработайте игровую сцену и создайте “уникальный интерактив”. Часть действий на сцене должны запускаться при нажатии клавиш клавиатуры.

# Скрипт для сферы.

![image](https://github.com/user-attachments/assets/b4fd0021-c67c-43de-8049-46dec515302c)


# Cкрипт для куба CubeNancy.

![image](https://github.com/user-attachments/assets/76aa3c8e-0630-4da0-81b6-7487521ba71f)


2.18 Напишите развернутый вывод по проделанной работе. Как знания свойств компонентов RigidBody помогут в создании интерактивных приложений, игр и симуляторов?

----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
В ходе данной работы я познакомился с компонентом RigidBody. Я изменял его компоненты, проводя различные эксперименты и на практическом опыте понял, как они работают и для чего их использовать. Знания свойств, изученных в этой работе, помогут при реализации различных физических механик, например взаимодействия тел и переход тела из одной среды в другую.
----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
