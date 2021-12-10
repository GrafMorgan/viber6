1. Создаём новый проект
2. Добавляем поле EditText типа textMultiLine
3. Добавляем 2 кнопки: Получить данные, Сохранить данные
4. Добавляем поле TextView
![image](https://user-images.githubusercontent.com/38504787/145619666-0a817735-394e-4c43-9e4b-9aa123f2ab83.png)
5. Создаём для кнопок обработчики событий
~~~ Java
public void restoreField(View view) {
        TextView nameView = (TextView) findViewById(R.id.textView);
        nameView.setText(name);
    }

    public void saveField(View view) {
        TextView nameBox = (TextView)
                findViewById(R.id.editTextTextMultiLine);
        name = nameBox.getText().toString();
    }
~~~
6. Пишем код для MainActivity
~~~ Java
String name ="неопределено";
    final static String nameVariableKey = "NAME_VAR";
    final static String textViewTexKey = "TEXT_VIEW";
    @Override
    protected void onCreate(Bundle savedInstanceState)
    {
        super.onCreate(savedInstanceState);
        setContentView(R.layout.activity_main);
    }
    @Override
    protected void onSaveInstanceState(Bundle outState)
    {
        outState.putString(nameVariableKey, name);
        TextView nameView = (TextView) findViewById(R.id.textView);

        outState.putString(textViewTexKey,
                nameView.getText().toString());
        super.onSaveInstanceState(outState);
    }
    @Override
    protected void onRestoreInstanceState(Bundle savedInstanceState)
    {
        super.onRestoreInstanceState(savedInstanceState);
        name = savedInstanceState.getString(nameVariableKey);
        String textViewText=
                savedInstanceState.getString(textViewTexKey);
        TextView nameView = (TextView) findViewById(R.id.textView);
        nameView.setText(textViewText);
    }
~~~
7. Проверяем
![image](https://user-images.githubusercontent.com/38504787/145619945-93c3e005-db1e-4497-8368-06abf6d2102b.png)
