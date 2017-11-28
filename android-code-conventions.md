# Android code conventions
* [Acknowledgments](#acknowledgments)
* [File names](#file-names)
  * [Souce files](#source-files)
  * [Resource files](#resource-files)
* [Code style](#code-styles)
  * [Indentation](#indentation)
  * [Class internal order](#class-internal-order)
  * [Field names](#field-names)
  * [Resource names](#resource-names)

## Acknowledgments
It is recommended to apply immediately when developing new projects. 
In case of working in or contributing to existing projects, developers should show respect to existing code style, only make changes if it is allowed.

## File names

### Source files
- Android related files: `***Activity.java`, `***Fragment.java`, `***BroadcastReceiver.java`, `***Service.java`, and etc. i.e: `NoteDetailsActivity.java`, `NoteDetailsFragment.java`, or `MusicPlayerService.java`.
- Utils: Multiple specific utility files are better than one general one. We may have `TimeUtils.java`, `StringUtils.java`, `ViewUtils.java`, `NetworkUtils.java` instead of only one huge `Utility.java`.

### Resource files
- Layouts: Add prefix as their base types. 
  - Activity: `activity_***.xml`
  - Fragment: `fragment_***.xml`
  - ListView or GridView items: `item_***.xml`
  - Others: `dialog_***.xml`, `toolbar_****.xml`, `view_***.xml`, and etc.
- Drawables:
  - icons: `ic_***.png`, `ic_***.xml`, etc.
  - backgrounds: `bg_***.png`, `bg_***.xml`, etc.
- Menus: Name it as layout file **without** `menu` prefix because it will be called in Java file like that `R.menu.***` and already under `res/menu` folder.
  - Activity menu: `activity_***.xml`
  - Fragment menu: `fragment_***.xml`
- Preferences:`preference_***.xml`. i.e: `preference_general.xml`. It is put under `res/xml` folder.

## Code styles

### Indentation
2 spaces

### Class internal order
  1. Constants
  2. Fields
  3. Constructors
  3. @Override methods
  4. Public methods
  5. Protected methods
  5. Private methods
```java
  public class NoteActivity extends AppCompatActivity {
    public static final String EXTRA_NOTE_ID = "note_id";
    
    private TextView titleText;
    private ImageView backgroundImage;
    private Button saveButton;
    
    @Override public boolean onCreateOptionsMenu(Menu menu) {}

    @Override protected void onCreate(Bundle savedInstance) {}
    
    @Override protected void onResume() {}
    
    private void showNote() {}
  }
```

### Field names
Hungarian notation: **No**.
```java
  // Don't write like this.
  private String mName;
  private static int sAge;

  // It looks better.
  private String name;
  private static int age;
```

### Resource names
  - view id under layout files: Button(`@+id/button_****`), TextView(`@+id/text_`), EditText(`@+id/edit_`), ImageView(`@+id/image_`), etc.
  - string name in `strings.xml`: message content (`name = "msg_***"`), preference (`name = "pref_***"`).
  - menu item: `@+id/menu_***`
  - color name in `colors.xml`: it should be named as in pallete. i.e: `name = "green"`, `name = "red"`, or `name = "blue"`.
