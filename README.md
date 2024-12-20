Вариант №24<br/>
Задание №2<br/>
Разработать инструмент командной строки для визуализации графа
зависимостей, включая транзитивные зависимости. Сторонние средства для
получения зависимостей использовать нельзя.
Зависимости определяются по имени пакета языка JavaScript (npm). Для
описания графа зависимостей используется представление Mermaid.
Визуализатор должен выводить результат на экран в виде кода.
Конфигурационный файл имеет формат xml и содержит:
• Путь к программе для визуализации графов.
• Имя анализируемого пакета.
• Путь к файлу-результату в виде кода.
Все функции визуализатора зависимостей должны быть покрыты тестами.

Описание функций<br/>
1. recreate_temp_folder(folder_path)<br/>
Назначение:<br/>
Удаляет папку, если она существует, и создает её заново. Используется для подготовки временной директории перед установкой пакета.<br/>

Параметры:  <br/>
folder_path (str): Путь к папке, которую необходимо пересоздать.<br/>

Возвращает: <br/>
Ничего не возвращает.<br/>


3. load_package_json(package_json_path)<br/>
Назначение: Извлекает зависимости из секции dependencies файла package.json.<br/>
Параметры:package_json_path (dict): Содержимое package.json в виде словаря.<br/>
Возвращает:  Данные из package.json в виде словаря.<br/>

4. fetch_package_json_from_repo(package_name)<br/>
Назначение: Считывает содержимое файла package.json и возвращает его как словарь Python.<br/>
Параметры: package_name (str): Имя пакета, для которого необходимо загрузить package.json.<br/>
Возвращает: Словарь зависимостей, где ключи — названия пакетов, а значения — их версии.<br/>

5. build_dependency_graph(package_name, lock_file_path)<br/>
Назначение: Создает граф зависимостей пакета, используя информацию из файла package-lock.json. Учитывает циклические зависимости.<br/>
Параметры: package_name (str): Имя корневого пакета, для которого строится граф.<br/>
Возвращает: Граф зависимостей в виде словаря, где ключи — это названия пакетов, а значения — списки их зависимостей.<br/>

6.generate_mermaid(graph)<br/>
Назначение: Сохраняет сгенерированный код Mermaid в указанный файл.<br/>
Параметры: ГКод Mermaid для записи в файл.<br/>
Возвращает:  Код Mermaid для графа зависимостей.<br/>

7.save_mermaid_to_file(content, output_file)<br/>
Назначение: Генерирует код в формате Mermaid для визуализации графа зависимостей.<br/>
Параметры: Граф зависимостей в виде словаря.<br/>
Возвращает:  Код Mermaid для графа зависимостей.<br/>

8.read_config(file_path)<br/>
Назначение: Считывает XML-конфигурацию для получения путей и параметров, необходимых для работы скрипта.<br/>
Параметры: file_path (str): Путь к XML-файлу конфигурации.<br/>
Возвращает:  Кортеж из трёх элементов: <br/>
1. visualizer_path (str): Путь к инструменту визуализации. <br/>
2. package_name (str): Имя целевого пакета.<br/>
3. output_file (str): Путь к выходному файлу для Mermaid-кода.<br/>


***
НАСТРОЙКИ<br/>
config.xml<br/>
Файл конфигурации должен содержать следующие параметры:<br/>

    <visualizerPath>/usr/local/bin/mermaid-cli</visualizerPath><br/>
     <packageName>lodash</packageName><br/>
     <outputFile>D:/dz_config_2/dependency_graph_lodash.mmd</outputFile><br/>
ПРИМЕРЫ<br/>
![image](https://github.com/user-attachments/assets/3e2d5b02-63fe-43bc-a858-7847981c6d76) <br/>
Граф для пакета express
![image](https://github.com/user-attachments/assets/44ec84e5-49a3-4e72-a5ce-1a3e7af4077c) <br/>
Граф для пакета lodash
![image](https://github.com/user-attachments/assets/8ad78887-fdb9-4eaa-9d67-54e027c19a6a)
Граф для пакета request



