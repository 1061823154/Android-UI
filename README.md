#Android-UI
android UI组件
@ [TOC]（第三次测试）

＃第三个实验
## Android UI组件
运行主界面：
![](https://github.com/1061823154/Android-UI/blob/master/%E7%85%A7%E7%89%87/1.jpg)

1.Android ListView的用法：
![](ttps://github.com/1061823154/Android-UI/blob/master/%E7%85%A7%E7%89%87/2.png)

核心代码：
```的java
public class AnimalsActivity扩展AppCompatActivity {
// private List <Animals> animalsList = new ArrayList <>（）;
    private List <Map <String，Object >> listItems;
    private String [] names = new String []
        {“狮子”，“老虎”，“猴子”，“狗”，“猫”，“大象”};
    private int [] imageIds = new int []
            {R.drawable.lion，R.drawable.tiger，R.drawable.monkey，
                    R.drawable.dog，R.drawable.cat，R.drawable.elephant};
    @覆盖
    protected void onCreate（@Nullable Bundle savedInstanceState）{
        this.setTitle（“Android ListView”）;
        super.onCreate（savedInstanceState）;
        的setContentView（R.layout.activity_main）;
        listItems = new ArrayList <Map <String，Object >>（）;
        for（int i = 0; i <names.length; i ++）
        {
            Map <String，Object> listItem = new HashMap <String，Object>（）;
            listItem.put（“animalName”，names [i]）;
            listItem.put（“image”，imageIds [i]）;
            listItems.add（的listItem）;
        }
        //创建一个SimpleAdapter
        SimpleAdapter simpleAdapter = new SimpleAdapter（this，listItems，
                R.layout.animals_layout，
                new String [] {“animalName”，“image”}，
                new int [] {R.id.animals_name，R.id.animals_image}）;
// initAnimals（）;
// AnimalsAdapter adapter = new AnimalsAdapter（AnimalsActivity.this，R.layout.animals_layout，animalsList）;
        ListView listView =（ListView）findViewById（R.id.list_view）;
        listView.setAdapter（simpleAdapter）;
        listView.setOnItemClickListener（new AdapterView.OnItemClickListener（）{
            @覆盖
            public void onItemClick（AdapterView <？> parent，View视图，int position，long id）{
                Toast.makeText（AnimalsActivity.this，名称[位置]，Toast.LENGTH_SHORT）.show（）;
//动物动物=（动物）listItems.get（position）;
// Toast.makeText（AnimalsActivity.this，animals.getName（），Toast.LENGTH_SHORT）.show（）;
            }
        }）;
    }

```
运行截图：
![](ttps://github.com/1061823154/Android-UI/blob/master/%E7%85%A7%E7%89%87/3.jpg)


2.创建自定义布局的AlertDial：
![](ttps://github.com/1061823154/Android-UI/blob/master/%E7%85%A7%E7%89%87/4.png)
核心代码：
```的java
公共类AlterDialog扩展AppCompatActivity {

    @覆盖
    protected void onCreate（Bundle savedInstanceState）{
        this.setTitle（ “AlterDialog”）;
        super.onCreate（savedInstanceState）;
        的setContentView（R.layout.button）;
        按钮=（按钮）findViewById（R.id.button）;
        button.setOnClickListener（new View.OnClickListener（）{
            @覆盖
            public void onClick（查看v）{
                AlertDialog builder = new AlertDialog.Builder（AlterDialog.this）
                        .setView（R.layout.dialog_layout）
                        .setNegativeButton（ “取消”，NULL）
                        .setPositiveButton（“登录”，null）
                        。创建（）;
                builder.show（）;
            }
        }）;
    }
}
```
dialog_layout.xml
```的java
<LinearLayout xmlns：android =“http://schemas.android.com/apk/res/android”
    机器人：方向=“垂直”
    机器人：layout_width = “match_parent”
    机器人：layout_height = “match_parent”
    机器人：layout_gravity = “中心”>
    <ImageView的
        机器人：layout_width = “match_parent”
        机器人：layout_height = “WRAP_CONTENT”
        机器人：scaleType = “centerCrop”
        机器人：SRC = “@绘制/ header_logo”/>
    <的EditText
        机器人：layout_width = “match_parent”
        机器人：layout_height = “WRAP_CONTENT”
        机器人：提示= “用户名”/>
    <的EditText
        机器人：layout_width = “match_parent”
        机器人：layout_height = “WRAP_CONTENT”
        安卓的inputType = “textPassword”
        机器人：提示=“密码”
        />

</的LinearLayout>

```
运行截图：
![](ttps://github.com/1061823154/Android-UI/blob/master/%E7%85%A7%E7%89%87/5.jpg)
3.使用XML定义菜单：
![](tps://github.com/1061823154/Android-UI/blob/master/%E7%85%A7%E7%89%87/6.png)
核心代码：
```的java
公共类MenuActivity扩展AppCompatActivity {

    @覆盖
    public boolean onCreateOptionsMenu（Menu menu）{
        。getMenuInflater（）膨胀（R.menu.main，菜单）;
        返回true;
    }

    @覆盖
    protected void onCreate（Bundle savedInstanceState）{
        this.setTitle（ “XML定义菜单”）;
        super.onCreate（savedInstanceState）;
        的setContentView（R.layout.menu_layout）;
    }

    @覆盖
    public boolean onOptionsItemSelected（MenuItem item）{
        TextView textView =（TextView）findViewById（R.id.text）;
        switch（item.getItemId（））{
            案例R.id.z1：
                textView.setTextSize（10）;打破;
            案例R.id.z2：
                textView.setTextSize（16）;打破;
            案例R.id.z3：
                textView.setTextSize（20）;打破;
            案例R.id.y1：
                textView.setTextColor（Color.RED）;打破;
            案例R.id.y2：
                textView.setTextColor（Color.BLACK）;打破;
            案例R.id.p：
                Toast.makeText（这一点， “这是普通单击项”，Toast.LENGTH_SHORT）.show（）;
                打破;
             默认：
        }
        返回true;
    }
}

```
menu_layout.xml
```的java
<menu xmlns：android =“http://schemas.android.com/apk/res/android”>
    <项目
        机器人：ID = “@ + ID / z” 的
        机器人：标题= “字体大小”
        >
        <菜单>
            <组>
                <项目
                    机器人：ID = “@ + ID / Z1”
                    机器人：标题= “10号字体”
                    />
                <项目
                    机器人：ID = “@ + ID / Z2”
                    机器人：标题= “16号字体”
                    />
                <项目
                    机器人：ID = “@ + ID / Z3”
                    机器人：标题= “20号字体”
                    />
            </组>
        </菜单>
    </项目>
    <项目
        机器人：ID = “@ + ID / P”
        机器人：标题= “普通菜单项”
        >
    </项目>
    <项目
        机器人：ID = “@ + ID / y” 的
        机器人：标题= “字体颜色”>
        <菜单>
            <组>
                <项目
                    机器人：ID = “@ + ID / Y1”
                    机器人：标题= “红色”
                    />
                <项目
                    机器人：ID = “@ + ID / Y2”
                    机器人：标题= “黑色”
                    />
            </组>
        </菜单>
    </项目>

</菜单>
```

运行截图：
![](ttps://github.com/1061823154/Android-UI/blob/master/%E7%85%A7%E7%89%87/7.jpg)
20号字体：
![](ttps://github.com/1061823154/Android-UI/blob/master/%E7%85%A7%E7%89%87/8.jpg)
![](ttps://github.com/1061823154/Android-UI/blob/master/%E7%85%A7%E7%89%87/9.jpg)
红色：
![](ttps://github.com/1061823154/Android-UI/blob/master/%E7%85%A7%E7%89%87/10.jpg)
![](ttps://github.com/1061823154/Android-UI/blob/master/%E7%85%A7%E7%89%87/11.jpg)
普通选项：
![](ttps://github.com/1061823154/Android-UI/blob/master/%E7%85%A7%E7%89%87/12.jpg)
4.创建上下文操作模式（ActionMode）的上下文菜单
![](ttps://github.com/1061823154/Android-UI/blob/master/%E7%85%A7%E7%89%87/13.png)
核心代码：
```的java
公共类ActionMode扩展AppCompatActivity {
    private ListView listView;
    private List <Number> numberList = new ArrayList <>（）;
    @覆盖
    protected void onCreate（@Nullable Bundle savedInstanceState）{
        this.setTitle（ “ActionMode”）;
        super.onCreate（savedInstanceState）;
        的setContentView（R.layout.actionmode_layout）;
        initNumber（）;
        NumberAdapter adapter = new NumberAdapter（ActionMode.this，R.layout.number_layout，numberList）;
        listView =（ListView）findViewById（R.id.list_view2）;
        listView.setAdapter（适配器）;
        listView.setChoiceMode（ListView.CHOICE_MODE_MULTIPLE_MODAL）;
        listView.setMultiChoiceModeListener（new AbsListView.MultiChoiceModeListener（）{
            @覆盖
            public boolean onCreateActionMode（android.view.ActionMode mode，Menu menu）{
                MenuInflater inflater = mode.getMenuInflater（）;
                inflater.inflate（R.menu.actionmode，menu）;
                返回true;
            }

            @覆盖
            public boolean onPrepareActionMode（android.view.ActionMode mode，Menu menu）{
                返回false;
            }

            @覆盖
            public boolean onActionItemClicked（android.view.ActionMode mode，MenuItem item）{
                mode.finish（）;
                返回false;
            }

            @覆盖
            public void onDestroyActionMode（android.view.ActionMode mode）{

            }

            @覆盖
            public void onItemCheckedStateChanged（android.view.ActionMode mode，int position，long id，boolean checked）{
                mode.setTitle（listView.getCheckedItemCount（）+“selected”）;
            }
        }）;
        listView.setOnItemClickListener（new AdapterView.OnItemClickListener（）{
            @覆盖
            public void onItemClick（AdapterView <？> parent，View视图，
                                    int position，long id）{

            }
        }）;
    }

    private void initNumber（）{
        for（int i = 0; i <2; i ++）{
            第一名=新号码（“One”，R.mipmap.ic_launcher）;
            numberList.add（之一）;
            第二个=新号码（“Two”，R.mipmap.ic_launcher）;
            numberList.add（二）;
            三号=新号码（“三号”，R.mipmap.ic_launcher）;
            numberList.add（3）;
            四号=新号码（“四号”，R.mipmap.ic_launcher）;
            numberList.add（4）;
            五号=新号码（“五号”，R.mipmap.ic_launcher）;
            numberList.add（5）;
        }
    }
}
```
NumberAdapter
```的java
public class NumberAdapter extends ArrayAdapter <Number> {
    private int resourceId;
    public NumberAdapter（@NonNull Context context，int resource，@ NonNull List <Number> objects）{
        超级（上下文，资源，对象）;
        resourceId = resource;
    }

    @NonNull
    @覆盖
    public View getView（int position，@ Nullable View convertView，@ NonNull ViewGroup parent）{
        Number number = getItem（position）;
        View view = LayoutInflater.from（getContext（））。inflate（resourceId，parent，false）;
        ImageView numberImage =（ImageView）view.findViewById（R.id.num_image）;
        TextView numberName =（TextView）view.findViewById（R.id.num_name）;
        numberImage.setImageResource（number.getImageId（））;
        numberName.setText（number.getName（））;
        返回视图;
    }
}
```
运行截图：
![](ttps://github.com/1061823154/Android-UI/blob/master/%E7%85%A7%E7%89%87/14.jpg)
