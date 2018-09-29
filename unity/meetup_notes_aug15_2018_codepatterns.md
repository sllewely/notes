# Unity meetup

[Jetbrains has an IDE for unity dev](https://www.jetbrains.com/dotnet/promo/unity/)
[Instead of built in text, use Text Mesh Pro](https://assetstore.unity.com/packages/essentials/beta-projects/textmesh-pro-84126)


## C# Code pattern

Item Object
```
// Doesn't inherit from monobehavior
[System.Serializable]
public class Item {
  public String name;
  
  Item(name) {
    this.name = name;
  }
}

// Drag onto _ItemManager GameObject in scene
public class ItemManager : Monobehavior {
  // This should also be singleton
  public Item[] items;
}
```

Singleton MenuManager
```
public class MenuManager : MonoBehavior {
  public static MenuManager singleton;
  public static MenuManager s{ get { return singleton; } }
  protected void Awake() {
    singleton = this;
  }
  
  ...
}

public class SomeScript() {
  void Start() {
    MenuManager.s;
  }
}
```

Speaker recommends writing your own scene loader instead of using Unity's.

Technicallly the above isn't a real singleton because it's possible to change it, but I like this mimic.


