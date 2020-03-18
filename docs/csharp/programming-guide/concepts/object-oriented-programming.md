---
title: Objektově orientované programování (C#)
ms.date: 02/08/2020
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 01d6f55bf0752f902f351675c4596abbb8ac85c2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77627887"
---
# <a name="object-oriented-programming-c"></a>Objektově orientované programování (C#)

C# poskytuje plnou podporu pro objektově orientované programování včetně zapouzdření, dědičnosti a polymorfismu.

- *Zapouzdření* znamená, že skupina souvisejících vlastností, metod a dalších členů je považována za jednu jednotku nebo objekt.
- *Dědičnost* popisuje schopnost vytvářet nové třídy založené na existující třídě.
- *Polymorfismus* znamená, že můžete mít více tříd, které lze použít zaměnitelně, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.

## <a name="classes-and-objects"></a>Třídy a objekty

Termíny *třídy* a *objektu* popisují *typ* objektů a *instance* tříd. Takže akt vytvoření objektu se nazývá *inkaso*. Pomocí analogie podrobného plánu je třída podrobný plán a objekt je budova vyrobená z tohoto podrobného plánu.

Definování třídy:

```csharp
class SampleClass
{
}
```

C# také poskytuje typy nazývané *struktury,* které jsou užitečné, když nepotřebujete podporu dědičnosti nebo polymorfismu.

Definování struktury:

```csharp
struct SampleStruct
{
}
```

Další informace naleznete v článcích o klíčových [slovech třídy](../../language-reference/keywords/class.md) a [struktury.](../../language-reference/builtin-types/struct.md)

### <a name="class-members"></a>Členové třídy

Každá třída může mít různé *členy třídy,* které obsahují vlastnosti, které popisují data třídy, metody, které definují chování třídy a události, které poskytují komunikaci mezi různými třídami a objekty.

#### <a name="properties-and-fields"></a>Vlastnosti a pole

Pole a vlastnosti představují informace, které objekt obsahuje. Pole jsou jako proměnné, protože je lze číst nebo nastavit přímo, s výhradou příslušných modifikátorů přístupu.

Chcete-li definovat pole, které lze přistupovat z instancí třídy:

```csharp
public class SampleClass
{
    string sampleField;
}
```

Vlastnosti `get` `set` mají a přistupující objekty, které poskytují větší kontrolu nad tím, jak jsou hodnoty nastaveny nebo vráceny.

C# umožňuje buď vytvořit soukromé pole pro ukládání hodnoty vlastnosti nebo použít automaticky implementované vlastnosti, které vytvářejí toto pole automaticky na pozadí a poskytují základní logiku pro procedury vlastností.

Definování automaticky implementované vlastnosti:

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

Pokud potřebujete provést některé další operace pro čtení a zápis hodnoty vlastnosti, definujte pole pro ukládání hodnoty vlastnosti a zadejte základní logiku pro ukládání a načítání:

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

Většina vlastností má metody nebo postupy pro nastavení i získání hodnoty vlastnosti. Můžete však vytvořit vlastnosti jen pro čtení nebo jen pro zápis, které jim zabrání v jejich úpravách nebo čtení. V c#, můžete vynechat `get` metodu nebo `set` vlastnost. Automaticky implementované vlastnosti však nelze pouze pro zápis. Automaticky implementované vlastnosti jen pro čtení lze nastavit v konstruktorech obsahující třídy.

Další informace naleznete v tématu:

- [get](../../language-reference/keywords/get.md)

- [Nastavit](../../language-reference/keywords/set.md)

#### <a name="methods"></a>Metody

*Metoda* je akce, kterou může objekt provést.

Definování metody třídy:

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

Třída může mít několik implementací nebo *přetížení*stejné metody, které se liší v počtu parametrů nebo typů parametrů.

Přetížení metody:

```csharp
public int sampleMethod(string sampleParam) {}
public int sampleMethod(int sampleParam) {}
```

Ve většině případů deklarujete metodu v rámci definice třídy. Však C# také podporuje *metody rozšíření,* které umožňují přidat metody do existující třídy mimo skutečnou definici třídy.

Další informace naleznete v tématu:

- [Metody](../classes-and-structs/methods.md)
- [Metody rozšíření](../classes-and-structs/extension-methods.md)

#### <a name="constructors"></a>Konstruktory

Konstruktory jsou metody třídy, které jsou prováděny automaticky při vytvoření objektu daného typu. Konstruktory obvykle inicializovat datové členy nového objektu. Konstruktor lze spustit pouze jednou při vytvoření třídy. Kromě toho kód v konstruktoru vždy spustí před jakýkoli jiný kód ve třídě. Můžete však vytvořit více přetížení konstruktoru stejným způsobem jako pro jakoukoli jinou metodu.

Definování konstruktoru pro třídu:

```csharp
public class SampleClass
{
    public SampleClass()
    {
        // Add code here
    }
}
```

Další informace naleznete v tématu [Konstruktory](../classes-and-structs/constructors.md).

#### <a name="finalizers"></a>Finalizační metody

Finalizační metody se používají k zničení instancí tříd. V rozhraní .NET Framework systém uvolňování paměti automaticky spravuje přidělení a uvolnění paměti pro spravované objekty ve vaší aplikaci. Však stále může být nutné finalizační metody vyčistit všechny nespravované prostředky, které vaše aplikace vytvoří. Pro třídu může být pouze jedna finalizační metoda.

Další informace o finalizačních metodách a uvolňování paměti v rozhraní .NET Framework naleznete v tématu [Garbage Collection](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Akce

Události umožňují třídy nebo objekt upozorňovat jiné třídy nebo objekty, když dojde k něčemu zajímavého. Třída, která odesílá (nebo vyvolává) událost se nazývá *vydavatel* a třídy, které přijímají (nebo zpracovávají) událost se nazývají *předplatitelé*. Další informace o událostech, jak jsou vyvolány a zpracovány, naleznete v [tématu Události](../../../standard/events/index.md).

- Chcete-li deklarovat událost ve třídě, použijte klíčové slovo [události.](../../language-reference/keywords/event.md)

- Chcete-li vyvolat událost, vyvolat delegáta události.

- Chcete-li se přihlásit `+=` k odběru události, použijte operátor; odhlásit se z události, `-=` použijte operátora.

#### <a name="nested-classes"></a>Vnořené třídy

Třída definovaná v rámci jiné třídy se nazývá *vnořené*. Ve výchozím nastavení je vnořená třída soukromá.

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

Chcete-li vytvořit instanci vnořené třídy, použijte název třídy kontejneru následovaný tečkou a poté název vnořené třídy:

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Modifikátory přístupu a úrovně přístupu

Všechny třídy a členové třídy můžete určit, jakou úroveň přístupu poskytují ostatním třídám pomocí *modifikátorů přístupu*.

K dispozici jsou následující modifikátory přístupu:

|Modifikátor Jazyka C#|Definice|
|------------------|----------------|
|[Veřejné](../../language-reference/keywords/public.md)|Typ nebo člen lze přistupovat libovolný jiný kód ve stejném sestavení nebo jiné sestavení, které odkazuje na něj.|
|[Soukromé](../../language-reference/keywords/private.md)|Typ nebo člen lze přistupovat pouze podle kódu ve stejné třídě.|
|[protected](../../language-reference/keywords/protected.md)|Typ nebo člen lze přistupovat pouze podle kódu ve stejné třídě nebo v odvozené třídě.|
|[Vnitřní](../../language-reference/keywords/internal.md)|Typ nebo člen lze přistupovat libovolný kód ve stejném sestavení, ale ne z jiného sestavení.|
|[protected internal](../../language-reference/keywords/protected-internal.md)|Typ nebo člen lze přistupovat libovolný kód ve stejném sestavení nebo jakékoli odvozené třídy v jiném sestavení.|
|[private protected](../../language-reference/keywords/private-protected.md)|Typ nebo člen lze přistupovat podle kódu ve stejné třídě nebo v odvozené třídě v rámci sestavení základní třídy.|

Další informace naleznete [v tématu Access Modifiers](../classes-and-structs/access-modifiers.md).

### <a name="instantiating-classes"></a>Vytváření vytváření konkrecí tříd

Chcete-li vytvořit objekt, musíte vytvořit instanci třídy nebo vytvořit instanci třídy.

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

Chcete-li přiřadit hodnoty vlastnostem během procesu instanování třídy, použijte inicializační metody objektu:

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

Další informace naleznete v tématu:

- [new – operátor](../../language-reference/operators/new-operator.md)
- [Inicializátory objektu a kolekce](../classes-and-structs/object-and-collection-initializers.md)

### <a name="static-classes-and-members"></a>Statické třídy a členy

Statický člen třídy je vlastnost, postup nebo pole, které jsou sdíleny všemi instancemi třídy.

Chcete-li definovat statický člen:

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

Statické třídy v C# mají pouze statické členy a nelze vytvořit instanci. Statické členy také nemají přístup k nestatickým vlastnostem, polím nebo metodám.

Další informace naleznete v tématu: [static](../../language-reference/keywords/static.md).

### <a name="anonymous-types"></a>Anonymní typy

Anonymní typy umožňují vytvářet objekty bez zápisu definice třídy pro datový typ. Místo toho kompilátor generuje třídu pro vás. Třída nemá žádný použitelný název a obsahuje vlastnosti, které zadáte při deklarování objektu.

Vytvoření instance anonymního typu:

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

Další informace naleznete v tématu [Anonymní typy](../classes-and-structs/anonymous-types.md).

## <a name="inheritance"></a>Dědičnost

Dědičnost umožňuje vytvořit novou třídu, která opakovaně používá, rozšiřuje a upravuje chování, které je definováno v jiné třídě. Třída, jejíž členové jsou zděděni, se nazývá *základní třída*a třída, která tyto členy dědí, se nazývá *odvozená třída*. Všechny třídy v jazyce C# <xref:System.Object> však implicitně dědí z třídy, která podporuje hierarchii třídy .NET a poskytuje služby nižší úrovně pro všechny třídy.

> [!NOTE]
> C# nepodporuje vícenásobné dědičnosti. To znamená, že můžete zadat pouze jednu základní třídu pro odvozenou třídu.

Dědit ze základní třídy:

```csharp
class DerivedClass:BaseClass {}
```

Ve výchozím nastavení mohou být zděděny všechny třídy. Můžete však určit, zda třída nesmí být použita jako základní třída, nebo vytvořit třídu, kterou lze použít pouze jako základní třídu.

Chcete-li určit, že třídu nelze použít jako základní třídu:

```csharp
public sealed class A { }
```

Chcete-li určit, že třídu lze použít pouze jako základní třídu a nelze vytvořit instanci:

```csharp
public abstract class B { }
```

Další informace naleznete v tématu:

- [sealed](../../language-reference/keywords/sealed.md)

- [Abstraktní](../../language-reference/keywords/abstract.md)

### <a name="overriding-members"></a>Převažující členové

Ve výchozím nastavení odvozená třída dědí všechny členy ze své základní třídy. Pokud chcete změnit chování zděděného člena, je třeba jej přepsat. To znamená, že můžete definovat novou implementaci metody, vlastnosti nebo události v odvozené třídě.

Následující modifikátory se používají k řízení, jak jsou přepsány vlastnosti a metody:

|Modifikátor Jazyka C#|Definice|
|------------------|----------------|
|[virtual](../../language-reference/keywords/virtual.md)|Umožňuje přepsání člena třídy v odvozené třídě.|
|[override](../../language-reference/keywords/override.md)|Přepíše virtuální (overridable) člen definovaný v základní třídě.|
|[Abstraktní](../../language-reference/keywords/abstract.md)|Vyžaduje, aby člen třídy přepsán v odvozené třídě.|
|[new – modifikátor](../../language-reference/keywords/new-modifier.md)|Skryje člena zděděného ze základní třídy.|

## <a name="interfaces"></a>Rozhraní

Rozhraní, jako jsou třídy, definují sadu vlastností, metod a událostí. Ale na rozdíl od tříd, rozhraní neposkytují implementaci. Jsou implementovány třídami a definovány jako samostatné entity od tříd. Rozhraní představuje smlouvu v tom, že třída, která implementuje rozhraní musí implementovat každý aspekt tohoto rozhraní přesně tak, jak je definována.

Chcete-li definovat rozhraní:

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

Chcete-li implementovat rozhraní ve třídě:

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

Další informace naleznete v článku průvodce programováním [rozhraní](../interfaces/index.md) a článek s referenčním [jazykem](../../language-reference/keywords/interface.md) na klíčovéslovo rozhraní.

## <a name="generics"></a>Obecné typy

Třídy, struktury, rozhraní a metody v rozhraní .NET Framework mohou zahrnovat *parametry typu,* které definují typy objektů, které mohou ukládat nebo používat. Nejběžnějším příkladem obecných typů je kolekce, kde můžete určit typ objektů, které mají být uloženy v kolekci.

Definování obecné třídy:

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

Chcete-li vytvořit instanci obecné třídy:

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

Další informace naleznete v tématu:

- [Obecné typy](../../../standard/generics/index.md)

- [Obecné typy](../generics/index.md)

## <a name="delegates"></a>Delegáty

*Delegát* je typ, který definuje podpis metody a může poskytnout odkaz na libovolnou metodu s kompatibilním podpisem. Můžete vyvolat (nebo volat) metodu prostřednictvím delegáta. Delegáty se používají pro předávání metod jako argumentů jiným metodám.

> [!NOTE]
> Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů. Další informace o použití delegátů při zpracování událostí naleznete v [tématu Události](../../../standard/events/index.md).

Vytvoření delegáta:

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

Další informace naleznete v článku průvodce programováním [delegátů](../delegates/index.md) a v článku s referenčním jazykem na klíčové slovo [delegáta.](../../language-reference/builtin-types/reference-types.md)

## <a name="see-also"></a>Viz také

- [Programovací příručka jazyka C#](../index.md)
