# -5.-
Урок 5. Тонкости работы


Предположить, что числа в исходном массиве из 9 элементов имеют диапазон [0,
3], и представляют собой, например, состояния ячеек поля для игры в крестикинолики, где 0 – это пустое поле, 1 – это поле с крестиком, 2 – это поле с ноликом, 3
– резервное значение. Такое предположение позволит хранить в одном числе типа
int всё поле 3х3. Записать в файл 9 значений так, чтобы они заняли три байта.


import java.io.FileOutputStream;
import java.io.IOException;

public class Main {
    public static void main(String[] args) {
        short[] field = {1, 0, 2, 0, 3, 1, 2, 0, 0}; // Пример массива значений

        try (FileOutputStream fos = new FileOutputStream("field.txt")) {
            for (short value : field) {
                fos.write(value & 0xFF); // Записываем младший байт значения
                fos.write(value >> 8); // Записываем старший байт значения
            }
        } catch (IOException e) {
            e.printStackTrace();
        }
    }
}
