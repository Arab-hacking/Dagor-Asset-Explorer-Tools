# Dagor Asset Explorer Tools — Blender 4.5 Fork

[Русский](#русский) | [English](#english)

---

## Русский

Импортер для файлов Dagor Model File (`.dmf`) и Dagor Prop Layout (`.dpl`), созданных через Dagor Asset Explorer.

**Эта версия адаптирована для Blender 4.5.**

📢 **Наш Telegram-канал:** [pingvinCr](https://t.me/pingvinCr) — заходите для обсуждения, обновлений и фидбека!

<div align="center">
	<img src="https://i.postimg.cc/1tVm7XL3/image-(8).png" alt="Screenshot of the main window in action" width="80%" />
</div>

### Установка

1. Скачайте или соберите ZIP-архив аддона.
2. В Blender откройте:
   `Edit → Preferences → Add-ons → Install...`
3. Выберите архив:
   `Dagor-Asset-Explorer-Tools-Blender-4.5.zip`
4. Включите аддон в списке дополнений.
5. Импорт будет доступен через:
   `File → Import → Dagor Model File (.dmf)` или `Dagor Prop Layout (.dpl)`.

### Выбор языка в аддоне

В этой версии добавлен выбор языка интерфейса аддона:
* `English`
* `Русский`

**Где переключить язык:**
1. Перейдите в `Edit → Preferences → Add-ons`
2. Найдите **Dagor Asset Explorer Tools**
3. В настройках аддона выберите пункт `Language / Язык`

> 💡 Выбор языка также отображается непосредственно в боковой панели импорта файлов Blender.

### Возможности

* Поддержка скелета и анимационного рига.
* Масштабирование и преобразование модели под координаты Blender/Source.
* Импорт `.dmf` моделей и `.dpl` layout-файлов.
* Отключение автосохранения при загрузке `.dpl` (чтобы Blender не создавал огромные временные файлы).
* Автоматическое создание shader graph для материалов.
* Поддержка текстур из папки `textures`, находящейся рядом с моделью.
* Полная совместимость с Blender 4.5.

### Исправления для Blender 4.5

Эта версия учитывает изменения Python API и shader API в актуальных версиях Blender:
* `Principled BSDF: Specular` ➡️ **`Specular IOR Level`**
* `Principled BSDF: Emission` ➡️ **`Emission Color`**
* `Separate RGB` / `Combine RGB` ➡️ **`Separate Color`** / **`Combine Color`**
* Более безопасная обработка `mesh.from_pydata(..., shade_flat)`.
* Безопасная обработка custom normals (импорт не падает на битых/нулевых нормалях).

### Если детали самолета не на своих местах

Некоторые модели Dagor (особенно авиация) могут специфически хранить подвижные или отделяемые детали: закрылки, шасси, пилоны, винты, элементы кокпита и т.п.

Если детали появляются в центре сцены или смещены, попробуйте импортировать модель заново с такими настройками:

1. Включите `Force skinned bone transforms` / `Применять трансформации костей к skinned-деталям`.
2. Если модель всё ещё повернута или смещена неправильно, дополнительно включите `Legacy -90° Z rotation` / `Старый поворот Z -90°`.

**Рекомендуемый порядок проверки настроек:**

```ini
[Вариант 1]
Fix transform                 = ON
Relative parenting            = ON
Force skinned bone transforms = ON
Legacy -90° Z rotation        = OFF

[Вариант 2]
Fix transform                 = ON
Relative parenting            = ON
Force skinned bone transforms = ON
Legacy -90° Z rotation        = ON
