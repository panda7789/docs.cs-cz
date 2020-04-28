---
title: Objektově orientované programování (C#)
ms.date: 02/08/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 2b6be3384f76fa210c2b52c55ecf9bd865df43a6
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2020
ms.locfileid: "82200090"
---
# <a name="object-oriented-programming-c"></a>Objektově orientované programování (C#)

Jazyk C# poskytuje úplnou podporu pro objektově orientované programování, včetně zapouzdření, dědičnosti a polymorfismu.

- *Zapouzdření* znamená, že skupina souvisejících vlastností, metod a dalších členů je považována za jednu jednotku nebo objekt.
- *Dědičnost* popisuje možnost vytvářet nové třídy na základě existující třídy.
- *Polymorfismus* znamená, že můžete mít více tříd, které lze použít zaměnitelné, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.

## <a name="classes-and-objects"></a>Třídy a objekty

Výrazy *Třída* a *Object* popisují *typ* objektů a *instance* tříd, v uvedeném pořadí. To znamená, že vytvoření objektu se nazývá vytváření *instancí*. Pomocí analogie podrobného plánu je třída plán a objekt je sestaven z tohoto podrobného plánu.

Definování třídy:

```csharp
class SampleClass
{
}
```

Jazyk C# také poskytuje typy označované jako *struktury* , které jsou užitečné, pokud nepotřebujete podporu dědičnosti nebo polymorfismu.

Definování struktury:

```csharp
struct SampleStruct
{
}
```

Další informace najdete v článcích o klíčových slovech [třídy](../../language-reference/keywords/class.md) a [struktury](../../language-reference/builtin-types/struct.md) .

### <a name="class-members"></a>Členové třídy

Každá třída může mít různé *členy třídy* , které obsahují vlastnosti, které popisují data třídy, metody, které definují chování třídy, a události, které poskytují komunikaci mezi různými třídami a objekty.

#### <a name="properties-and-fields"></a>Vlastnosti a pole

Pole a vlastnosti reprezentují informace, které objekt obsahuje. Pole jsou jako proměnné, protože je lze číst nebo nastavit přímo v souladu s platnými modifikátory přístupu.

Chcete-li definovat pole, ke kterému lze přistupovat v rámci instancí třídy:

```csharp
public class SampleClass
{
    string sampleField;
}
```

Vlastnosti `get` a `set` přistupující objekty, které poskytují větší kontrolu nad tím, jak jsou hodnoty nastaveny nebo vraceny.

Jazyk C# umožňuje vytvořit soukromé pole pro uložení hodnoty vlastnosti nebo použít automaticky implementované vlastnosti, které automaticky vytvoří toto pole na pozadí a poskytnou základní logiku pro procedury vlastností.

Definování automaticky implementované vlastnosti:

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

Pokud potřebujete provést některé další operace pro čtení a zápis hodnoty vlastnosti, definujte pole pro uložení hodnoty vlastnosti a poskytněte základní logiku pro uložení a načtení:

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get => _sample;
        // Store the value in the field.
        set =>  _sample = value;
    }
}
```

Většina vlastností má metody nebo postupy pro nastavení a získání hodnoty vlastnosti. Můžete však vytvořit vlastnosti jen pro čtení nebo jen pro zápis a omezit tak jejich úpravu nebo čtení. V jazyce C# můžete vynechat metodu `get` nebo. `set` Automaticky implementované vlastnosti však nemohou být pouze pro zápis. Automaticky implementované vlastnosti jen pro čtení lze nastavit v konstruktorech obsahující třídy.

Další informace naleznete v tématu:

- [get](../../language-reference/keywords/get.md)

- [stanovenými](../../language-reference/keywords/set.md)

#### <a name="methods"></a>Metody

*Metoda* je akce, kterou může objekt provádět.

Chcete-li definovat metodu třídy:

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

Třída může mít několik implementací nebo *přetížení*stejné metody, která se liší v počtu parametrů nebo typů parametrů.

Přetížení metody:

```csharp
public int sampleMethod(string sampleParam) {}
public int sampleMethod(int sampleParam) {}
```

Ve většině případů deklarujete metodu v rámci definice třídy. Jazyk C# však podporuje také *metody rozšíření* , které umožňují přidat metody do existující třídy mimo skutečnou definici třídy.

Další informace naleznete v tématu:

- [Metody](../classes-and-structs/methods.md)
- [Metody rozšíření](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a>Konstruktory

Konstruktory jsou metody třídy, které jsou spouštěny automaticky, když je vytvořen objekt daného typu. Konstruktory obvykle inicializují datové členy nového objektu. Konstruktor lze spustit pouze jednou při vytvoření třídy. Kromě toho kód v konstruktoru se vždy spouští před jakýmkoli jiným kódem ve třídě. Můžete však vytvořit více přetížení konstruktoru stejným způsobem jako u jakékoli jiné metody.

Chcete-li definovat konstruktor pro třídu:

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

Další informace naleznete v tématu [konstruktory](../classes-and-structs/constructors.md).

#### <a name="finalizers"></a>Finalizační metody

Finalizační metoda se používá k destrukci instancí tříd. V .NET Framework systém uvolňování paměti automaticky spravuje přidělování a uvolňování paměti pro spravované objekty ve vaší aplikaci. Nicméně stále budete potřebovat finalizační metody k vyčištění všech nespravovaných prostředků, které vaše aplikace vytvoří. Pro třídu může existovat pouze jeden finalizační metoda.

Další informace o finalizační a uvolňování paměti v .NET Framework naleznete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Události

Události umožňují třídě nebo objektu upozornit jiné třídy nebo objekty, když dojde k nějakému zájmu. Třída, která odesílá (nebo vyvolává) událost, se nazývá *Vydavatel* a třídy, které přijmou (nebo zpracovávají) událost se nazývají *předplatitelé*. Další informace o událostech, jak jsou vyvolány a zpracovávány, naleznete v tématu [events](../../../standard/events/index.md).

- Chcete-li deklarovat událost ve třídě, použijte klíčové slovo [Event](../../language-reference/keywords/event.md) .

- Chcete-li vyvolat událost, vyvolejte delegáta události.

- K přihlášení k odběru události použijte `+=` operátor; Chcete-li zrušit odběr události, použijte `-=` operátor.

#### <a name="nested-classes"></a>Vnořené třídy

Třída definovaná v rámci jiné třídy se nazývá *vnořená*. Ve výchozím nastavení je vnořená třída soukromá.

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

Chcete-li vytvořit instanci vnořené třídy, použijte název třídy kontejneru následovaný tečkou a následně následovaný názvem vnořené třídy:

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Modifikátory přístupu a úrovně přístupu

Všechny třídy a členy třídy mohou určit, jakou úroveň přístupu poskytují jiné třídě, pomocí *modifikátorů přístupu*.

K dispozici jsou následující modifikátory přístupu:

|Modifikátor C#|Definice|
|------------------|----------------|
|[public](../../language-reference/keywords/public.md)|Na daný typ nebo člen je možné přistupovat jakýkoli jiný kód ve stejném sestavení nebo jiném sestavení, které na něj odkazuje.|
|[private](../../language-reference/keywords/private.md)|Typ nebo člen je k dispozici pouze pomocí kódu ve stejné třídě.|
|[protected](../../language-reference/keywords/protected.md)|Typ nebo člen je k dispozici pouze pomocí kódu ve stejné třídě nebo v odvozené třídě.|
|[internal](../../language-reference/keywords/internal.md)|K typu nebo členu může být přistup libovolným kódem ve stejném sestavení, ale nikoli z jiného sestavení.|
|[protected internal](../../language-reference/keywords/protected-internal.md)|K typu nebo členu může být přistup libovolným kódem ve stejném sestavení nebo libovolnou odvozenou třídou v jiném sestavení.|
|[private protected](../../language-reference/keywords/private-protected.md)|Typ nebo člen je k dispozici v kódu ve stejné třídě nebo v odvozené třídě v rámci sestavení základní třídy.|

Další informace najdete v tématu [modifikátory přístupu](../classes-and-structs/access-modifiers.md).

### <a name="instantiating-classes"></a>Vytváření instancí tříd

Chcete-li vytvořit objekt, je nutné vytvořit instanci třídy nebo vytvořit instanci třídy.

```csharp
SampleClass sampleObject = new SampleClass();
```

Po vytvoření instance třídy můžete přiřadit hodnoty vlastnostem a polím instance a vyvolat metody třídy.

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

Chcete-li přiřadit hodnoty vlastnostem během procesu vytváření instancí třídy, použijte Inicializátory objektů:

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

Další informace naleznete v tématu:

- [New – operátor](../../language-reference/operators/new-operator.md)
- [Inicializátory objektu a kolekce](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a>Statické třídy a členy

Statický člen třídy je vlastnost, procedura nebo pole, které jsou sdíleny všemi instancemi třídy.

Definování statického člena:

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

Chcete-li získat přístup ke statickému členu, použijte název třídy bez vytvoření objektu této třídy:

```csharp
Console.WriteLine(SampleClass.SampleString);
```

Statické třídy v jazyce C# mají pouze statické členy a nelze je vytvořit z instance. Statické členy také nemají přístup k nestatickým vlastnostem, polím nebo metodám.

Další informace naleznete zde: [static](../../language-reference/keywords/static.md).

### <a name="anonymous-types"></a>Anonymní typy

Anonymní typy umožňují vytvářet objekty bez psaní definice třídy pro datový typ. Místo toho kompilátor vygeneruje třídu za vás. Třída nemá žádný použitelný název a obsahuje vlastnosti, které zadáte v deklaraci objektu.

Vytvoření instance anonymního typu:

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

Další informace najdete v tématech: [anonymní typy](../classes-and-structs/anonymous-types.md).

## <a name="inheritance"></a>Dědičnost

Dědičnost umožňuje vytvořit novou třídu, která znovu používá, rozšiřuje a upravuje chování, které je definováno v jiné třídě. Třída, jejíž členové jsou zděděni, se nazývají *základní třídu*a třída, která dědí tyto členy, se nazývá *odvozená třída*. Nicméně všechny třídy v jazyce C# implicitně dědí z <xref:System.Object> třídy, která podporuje hierarchii tříd .NET a poskytuje služby nižší úrovně pro všechny třídy.

> [!NOTE]
> Jazyk C# nepodporuje vícenásobnou dědičnost. To znamená, že můžete zadat pouze jednu základní třídu pro odvozenou třídu.

Chcete-li dědit ze základní třídy:

```csharp
class DerivedClass:BaseClass {}
```

Ve výchozím nastavení mohou být děděny všechny třídy. Můžete však určit, zda třída nesmí být použita jako základní třída, nebo vytvořit třídu, která může být použita pouze jako základní třída.

Chcete-li určit, že třídu nelze použít jako základní třídu:

```csharp
public sealed class A { }
```

Chcete-li určit, že třída může být použita pouze jako základní třída a nemůže být vytvořena instance:

```csharp
public abstract class B { }
```

Další informace naleznete v tématu:

- [sealed](../../language-reference/keywords/sealed.md)

- [Výtah](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a>Přepisování členů

Ve výchozím nastavení zdědí odvozená třída všechny členy ze své základní třídy. Pokud chcete změnit chování zděděného člena, je nutné ho přepsat. To znamená, že můžete definovat novou implementaci metody, vlastnosti nebo události v odvozené třídě.

Následující modifikátory slouží k řízení způsobu přepsání vlastností a metod:

|Modifikátor C#|Definice|
|------------------|----------------|
|[virtual](../../language-reference/keywords/virtual.md)|Umožňuje přepsat člena třídy v odvozené třídě.|
|[override](../../language-reference/keywords/override.md)|Přepíše virtuální (overridabled) člen definovaný v základní třídě.|
|[Výtah](../../language-reference/keywords/abstract.md)|Vyžaduje, aby byl člen třídy přepsán v odvozené třídě.|
|[new – modifikátor](../../language-reference/keywords/new-modifier.md)|Skryje člena zděděného ze základní třídy.|

## <a name="interfaces"></a>Rozhraní

Rozhraní, jako jsou třídy, definují sadu vlastností, metod a událostí. Ale na rozdíl od tříd rozhraní neposkytuje implementaci. Jsou implementovány pomocí tříd a definovány jako samostatné entity ze tříd. Rozhraní představuje kontrakt, v tom smyslu, že třída, která implementuje rozhraní, musí implementovat všechny aspekty tohoto rozhraní přesně tak, jak je definováno.

Definování rozhraní:

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

Implementace rozhraní ve třídě:

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

Další informace najdete v článku Průvodce programováním v tématu [rozhraní](../interfaces/index.md) a referenční informace k jazyku na klíčovém slově [rozhraní](../../language-reference/keywords/interface.md) .

## <a name="generics"></a>Obecné typy

Třídy, struktury, rozhraní a metody v .NET Framework mohou zahrnovat *parametry typu* , které definují typy objektů, které mohou ukládat nebo používat. Nejběžnějším příkladem obecných typů je kolekce, kde můžete určit typ objektů, které mají být uloženy v kolekci.

Definování obecné třídy:

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

Vytvoření instance obecné třídy:

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

Další informace naleznete v tématu:

- [Obecné typy](../../../standard/generics/index.md)

- [Obecné typy](../generics/index.md)

## <a name="delegates"></a>Delegáty

*Delegát* je typ, který definuje signaturu metody a může poskytnout odkaz na libovolnou metodu s kompatibilní signaturou. Metodu můžete vyvolat (nebo volat) prostřednictvím delegáta. Delegáty se používají pro předávání metod jako argumentů jiným metodám.

> [!NOTE]
> Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů. Další informace o použití delegátů při zpracování událostí najdete v tématu [události](../../../standard/events/index.md).

Postup vytvoření delegáta:

```csharp
public delegate void SampleDelegate(string str);
```

Chcete-li vytvořit odkaz na metodu, která odpovídá podpisu určenému delegátem:

```csharp
class SampleClass
{
    // Method that matches the SampleDelegate signature.
    public static void sampleMethod(string message)
    {
        // Add code here.
    }
    // Method that instantiates the delegate.
    void SampleDelegate()
    {
        SampleDelegate sd = sampleMethod;
        sd("Sample string");
    }
}
```

Další informace najdete v článku Průvodce programováním u [delegátů](../delegates/index.md) a v článku referenční informace o jazyce na klíčovém slově [Delegate](../../language-reference/builtin-types/reference-types.md) .

## <a name="see-also"></a>Viz také

- [Průvodce programováním v C#](../index.md)
