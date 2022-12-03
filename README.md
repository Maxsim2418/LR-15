# LR-15[LR-15.zip](https://github.com/Maxsim2418/LR-15/files/10146035/LR-15.zip)

Борнеман М.А

ЭВТ-70

Игровой движок:Unity

Лабораторная работа №15

Тема: Изучение Tilemap

Ход работы:

1.Выполнение работы

Разделили спрайт на плитки, для дальнейшего их использования в построении сцены.

![image](https://user-images.githubusercontent.com/119674602/205432863-91f9846c-f99f-445f-bd2e-2a09fc4f9e36.png)

Рисунок 15.1 – Постройка сцены.

Построили сцену, добавили коллайдеры окружающим объектам.

Добавили игрока и скрипт к нему: осуществили передвижение на клавиши, сделали взаимодействие с объектами на клавишу E, чтобы персонаж говорил что это такое.

Листинг 15.1 Player.cs

using System.Collections;
using System.Collections.Generic;
using UnityEngine;
using UnityEngine.UI;

public class Player : MonoBehaviour
{
    private Rigidbody2D rb2d;
    public float playerSpeed;
    private Vector2 playerDirection;
    private GameObject player;
    [SerializeField]private Text _infoScreen;

    void Start()
    {
        player = GameObject.FindGameObjectWithTag("Player");
        rb2d = GetComponent<Rigidbody2D>();
    }
    private void Update()
    {
        float directionX = Input.GetAxisRaw("Horizontal");
        float directionY = Input.GetAxisRaw("Vertical");
        playerDirection = new Vector2(directionX, directionY).normalized;
    }
    private void FixedUpdate()
    {
        rb2d.velocity = new Vector2(playerDirection.x * playerSpeed, playerDirection.y * playerSpeed);
    }
    private void OnTriggerStay2D(Collider2D collision)
    {
        if (collision.tag == "Tree")
        {
            if (Input.GetKeyDown(KeyCode.E))
            {
                _infoScreen.text = "Это дерево";
            }
        }
        else if (collision.tag == "Kyst")
        {
            if (Input.GetKeyDown(KeyCode.E))
            {
                _infoScreen.text = "Это куст";
            }
        }
        else if (collision.tag == "Water")
        {
            if (Input.GetKeyDown(KeyCode.E))
            {
                _infoScreen.text = "Это озеро";
            }
        }
        else if (collision.tag == "Penek")
        {
            if (Input.GetKeyDown(KeyCode.E))
            {
                _infoScreen.text = "Это пень";
            }
        }
    }
}

![image](https://user-images.githubusercontent.com/119674602/205432881-654c805a-147b-4ca4-a441-83a312b20927.png)

Рисунок 15.2 – Настройка игрока.

2. Вывод.

В ходе проделанной работы мы изучили Tilemap и создали персонажа, который реагирует на окружение.
