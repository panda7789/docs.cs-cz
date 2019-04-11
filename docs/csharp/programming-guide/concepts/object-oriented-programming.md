---
title: Objektově orientované programování (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: a7a3ce1b33d040b337087dfede90b58906c95cbd
ms.sourcegitcommit: 859b2ba0c74a1a5a4ad0d59a3c3af23450995981
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/11/2019
ms.locfileid: "59481168"
---
# <a name="object-oriented-programming-c"></a>Objektově orientované programování (C#)

C# poskytuje plnou podporu pro objektově orientované programování včetně zapouzdření, dědičnosti a polymorfismu.

*Zapouzdření* znamená, že skupina souvisejících vlastností, metod a ostatní členové jsou považovány za jednu jednotku nebo objekt.

*Dědičnost* popisuje schopnost vytvářet nové třídy na základě existující třídy.

*Polymorfismus* znamená, že můžete mít více tříd, které můžete používat Zaměnitelně, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.

Tato část popisuje následující pojmy:

- [Třídy a objekty](#Classes)

  - [Členy třídy](#Members)

        [Properties and Fields](#Properties)

        [Methods](#Methods)

        [Constructors](#Constructors)

        [Finalizers](#Finalizers)

        [Events](#Events)

        [Nested Classes](#NestedClasses)

  - [Modifikátory přístupu a úrovně přístupu](#AccessModifiers)

  - [Vytvoření instance třídy](#InstantiatingClasses)

  - [Statické třídy a členové](#Static)

  - [Anonymní typy](#AnonymousTypes)

- [Dědičnost](#Inheritance)

  - [Obejití členů](#Overriding)

- [Rozhraní](#Interfaces)

- [Obecné typy](#Generics)

- [Delegáty](#Delegates)

## <a name="Classes"></a> Třídy a objekty

Podmínky *třídy* a *objekt* se někdy používají vzájemné záměně, ale ve skutečnosti třídy popisují *typ* objektů, zatímco objekty jsou použitelné  *instance* tříd. Ano, je volána při vytvoření objektu *instance*. Při použití analogie matric, třída je podrobný plán a objekt je vytvořen z této matrice budovy.

Definování třídy:

```csharp
class SampleClass
{
}
```

C# obsahuje také jednodušší verzi tříd pojmenovanou *struktury* , které jsou užitečné, když budete chtít vytvořit velké pole objektů a proveďte k tomu k tomu spotřebovat příliš mnoho paměti.

Definování struktury:

```csharp
struct SampleStruct
{
}
```

Další informace naleznete v tématu:

- [třída](../../../csharp/language-reference/keywords/class.md)

- [struct ](../../../csharp/language-reference/keywords/struct.md)

### <a name="Members"></a> Členy třídy

Každá třída může mít různé *členy třídy* obsahující vlastnosti, které popisují data třídy, metody, které určují chování třídy a události, které umožňují komunikaci mezi různými třídami a objekty.

#### <a name="Properties"></a> Vlastnosti a pole

Pole a vlastnosti představují informace, které obsahuje objekt. Pole jsou jako proměnné, protože mohou být čtena nebo nastavena přímo.

Definování pole:

```csharp
class SampleClass
{
    public string sampleField;
}
```

Vlastnosti mají get a nastavte postupy, které poskytují větší kontrolu toho, jak jsou hodnoty nastavena nebo vrácena.

C# můžete buď vytvořit soukromé pole pro uložení hodnoty vlastnosti nebo použít takzvané automaticky implementované vlastnosti, které vytvořit toto pole automaticky na pozadí a poskytnou základní logiku pro procedury vlastností.

Chcete-li definovat automaticky implementovanou vlastnost:

```csharp
class SampleClass
{
    public int SampleProperty { get; set; }
}
```

Pokud je potřeba provést některé další operace čtení a zápisu hodnoty vlastnosti, definujte pole pro uložení hodnoty vlastnosti a poskytněte základní logiku pro ukládání a načítání:

```csharp
class SampleClass
{
    private int _sample;
    public int Sample
    {
        // Return the value stored in a field.
        get { return _sample; }
        // Store the value in the field.
        set { _sample = value; }
    }
}
```

Většina vlastností má metody nebo postupy, jak nastavit a získat hodnotu vlastnosti. Můžete však vytvořit vlastnosti jen pro čtení nebo jen pro zápis, abyste omezili je číst nebo upravovat. V jazyce C# můžete vynechat `get` nebo `set` metoda vlastnosti. Automaticky implementované vlastnosti nemůže být ale jen pro čtení nebo jen pro zápis.

Další informace naleznete v tématu:

- [get](../../../csharp/language-reference/keywords/get.md)

- [set](../../../csharp/language-reference/keywords/set.md)

#### <a name="Methods"></a> Metody

A *metoda* je akce, které může objekt provádět.

Chcete-li definovat metodu pro třídu:

```csharp
class SampleClass
{
    public int sampleMethod(string sampleParam)
    {
        // Insert code here
    }
}
```

Třída může mít několik implementací, nebo *přetížení*, stejné metody, která se liší v počtu parametrů nebo typů parametrů.

Chcete-li přetížit metodu:

```csharp
public int sampleMethod(string sampleParam) {};
public int sampleMethod(int sampleParam) {}
```

Ve většině případů deklarujete metodu v rámci definice třídy. Ale jazyka C# také podporuje *rozšiřující metody* , které umožňují přidat metody do existující třídy mimo skutečnou definici třídy.

Další informace naleznete v tématu:

- [Metody](../../../csharp/programming-guide/classes-and-structs/methods.md)

- [Metody rozšíření](../../../csharp/programming-guide/classes-and-structs/extension-methods.md)

#### <a name="Constructors"></a> Konstruktory

Konstruktory jsou metody třídy, které jsou spouštěny automaticky, když je vytvořen objekt daného typu. Konstruktory obvykle inicializují datové členy nového objektu. Konstruktor lze spustit pouze jednou při vytvoření třídy. Kromě toho kód v konstruktoru se vždy spouští před ostatním kódem ve třídě. Můžete však vytvořit více přetížení konstruktoru stejným způsobem jako u jakékoliv jiné metody.

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

Další informace naleznete v tématu:

[Konstruktory](../../../csharp/programming-guide/classes-and-structs/constructors.md).

#### <a name="Finalizers"></a> Finalizační metody

Finalizační metody se používají k destrukci instancí tříd. V rozhraní .NET Framework systému uvolňování paměti automaticky spravuje přidělování a uvolňování paměti pro spravované objekty v aplikaci. Může však stále zapotřebí finalizační metody pro vyčištění všech nespravovaných prostředků, které vytváří vaše aplikace. Může existovat pouze jeden finalizační metody pro třídu.

Další informace o finalizační metody a systém kolekce paměti v rozhraní .NET Framework najdete v tématu [uvolňování](../../../standard/garbage-collection/index.md).

#### <a name="Events"></a> Události

Události umožňují třídám nebo objektům upozornit ostatní třídy nebo objekty, když něco, které vás zajímají. Třída, která odesílá (nebo vyvolává) událost je volána *vydavatele* a třídy, které zobrazí (nebo zpracování) události, se nazývají *předplatitele*. Další informace o událostech, jak jejich vyvolávání a zpracování viz [události](../../../standard/events/index.md).

- Chcete-li deklarovat událost v třídě, použijte [události](../../../csharp/language-reference/keywords/event.md) – klíčové slovo.

- K vyvolání události vyvolejte delegáta události.

- Chcete-li přihlásit odběr události, použijte `+=` operátor; Chcete-li zrušit odběr události, použijte `-=` operátor.

#### <a name="NestedClasses"></a> Vnořené třídy

Třída definována v rámci jiné třídy se nazývá *vnořené*. Ve výchozím nastavení vnořené třídy je privátní.

```csharp
class Container
{
    class Nested
    {
        // Add code here.
    }
}
```

Chcete-li vytvořit instanci vnořené třídy, použijte název třídy kontejneru následovaného tečkou a pak následovaného názvem vnořené třídy:

```csharp
Container.Nested nestedInstance = new Container.Nested()
```

### <a name="AccessModifiers"></a> Modifikátory přístupu a úrovně přístupu

Všechny třídy a členy třídy můžete určit úroveň přístupu poskytují dalším třídám, pomocí *modifikátorů přístupu*.

K dispozici jsou následující modifikátory přístupu:

|Modifikátor C#|Definice|
|------------------|----------------|
|[public](../../../csharp/language-reference/keywords/public.md)|Tento typ nebo člen je přístupný libovolnému jinému kódu ve stejném sestavení nebo libovolnému sestavení která na něj odkazuje.|
|[private](../../../csharp/language-reference/keywords/private.md)|Tento typ nebo člen je přístupný pouze kódu ve stejné třídě.|
|[protected](../../../csharp/language-reference/keywords/protected.md)|Tento typ nebo člen je přístupný pouze kódu ve stejné třídě nebo v odvozené třídě.|
|[internal](../../../csharp/language-reference/keywords/internal.md)|Tento typ nebo člen je přístupný libovolnému kódu ve stejném sestavení, ale ne z jiného sestavení.|
|[protected internal](../../../csharp/language-reference/keywords/protected-internal.md)|Tento typ nebo člen je přístupný libovolnému kódu ve stejném sestavení, nebo kterékoli odvozené třídě v jiném sestavení.|
|[private protected](../../../csharp/language-reference/keywords/private-protected.md)|Tento typ nebo člen je přístupný pomocí kódu ve stejné třídě nebo v odvozené třídě v rámci sestavení základní třídy.|

Další informace najdete v tématu [modifikátory přístupu](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md).

### <a name="InstantiatingClasses"></a> Vytvoření instance třídy

Pro vytvoření objektu, budete muset vytvořit instanci třídy, nebo vytvořit instanci třídy.

```csharp
SampleClass sampleObject = new SampleClass();
```

Po vytvoření instance třídy, můžete přiřadit hodnoty k vlastnosti a pole instance a volat metody třídy.

```csharp
// Set a property value.
sampleObject.sampleProperty = "Sample String";
// Call a method.
sampleObject.sampleMethod();
```

Chcete-li přiřadit hodnoty vlastností během procesu vytváření instance třídy, použijte inicializátory objektů:

```csharp
// Set a property value.
SampleClass sampleObject = new SampleClass
    { FirstProperty = "A", SecondProperty = "B" };
```

Další informace naleznete v tématu:

- [new – operátor](../../../csharp/language-reference/keywords/new-operator.md)

- [Inicializátory objektu a kolekce](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)

### <a name="Static"></a> Statické třídy a členové

Statický člen třídy je vlastnost, procedura nebo pole, která je sdílena všemi instancemi třídy.

Chcete-li definovat statický člen:

```csharp
static class SampleClass
{
    public static string SampleString = "Sample String";
}
```

Pro přístup k statický člen, použijte název třídy bez vytvoření objektů této třídy:

```csharp
Console.WriteLine(SampleClass.SampleString);
```

Statické třídy v jazyce C# mít jenom statické členy a nelze vytvořit instanci. Statické členy také nelze přistupovat k vlastnosti nestatické, polím nebo metodám

Další informace najdete v tématu: [statické](../../../csharp/language-reference/keywords/static.md).

### <a name="AnonymousTypes"></a> Anonymní typy

Anonymní typy umožňují vytvářet objekty bez psaní definice třídy datového typu. Místo toho kompilátor vygeneruje třídu za vás. Třída nemá žádný použitelný název a obsahuje vlastnosti, které jste zadali v rámci deklarace objektu.

Chcete-li vytvořit instanci anonymního typu:

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

Další informace naleznete v tématu: [Anonymní typy](../../../csharp/programming-guide/classes-and-structs/anonymous-types.md).

## <a name="Inheritance"></a> Dědičnost

Dědičnost umožňuje vytvořit novou třídu, která opakovaně používá, rozšiřuje a upravuje chování, které je definováno v jiné třídě. Třídy, jejíž členové jsou zdědění, se nazývá *základní třída*, a názvem třídy, která dědí tyto členy *odvozené třídy*. Nicméně všechny třídy v jazyce C# implicitně dědí z <xref:System.Object> třídu, která podporuje hierarchii tříd .NET a poskytuje služby nižší úrovně všem třídám.

> [!NOTE]
> C# nepodporuje vícenásobnou dědičnost. To znamená můžete zadat pouze jednu základní třídu pro odvozenou třídu.

Chcete-li dědit ze základní třídy:

```csharp
class DerivedClass:BaseClass {}
```

Ve výchozím nastavení je možné zdědit všechny třídy. Můžete však určit, zda třída nesmí používat jako základní třída nebo vytvořit třídu, která lze použít jako základní třídu.

Chcete-li určit, že třídu nelze použít jako základní třídu:

```csharp
public sealed class A { }
```

Určíte, že třída může sloužit jako základní třídu a nelze vytvořit instanci:

```csharp
public abstract class B { }
```

Další informace naleznete v tématu:

- [sealed](../../../csharp/language-reference/keywords/sealed.md)

- [abstract](../../../csharp/language-reference/keywords/abstract.md)

### <a name="Overriding"></a> Obejití členů

Ve výchozím nastavení dědí odvozená třída všechny členy ze své základní třídy. Pokud chcete změnit chování zděděného člena, musíte ho potlačit. To znamená můžete definovat novou implementaci metody, vlastnosti nebo události v odvozené třídě.

Následující modifikátory umožňují určit, jak přepsat vlastnosti a metody:

|Modifikátor C#|Definice|
|------------------|----------------|
|[virtual](../../../csharp/language-reference/keywords/virtual.md)|Umožňuje člen třídy k přepsání v odvozené třídě.|
|[override](../../../csharp/language-reference/keywords/override.md)|Přepsání virtuální (s možností přepsání) člena definovaného v základní třídě.|
|[abstract](../../../csharp/language-reference/keywords/abstract.md)|Vyžaduje, aby člen třídy k přepsání v odvozené třídě.|
|[new – modifikátor](../../../csharp/language-reference/keywords/new-modifier.md)|Skryje člena zděděného ze základní třídy|

## <a name="Interfaces"></a> Rozhraní

Rozhraní, stejně jako třídy, definují sadu vlastností, metody a události. Ale na rozdíl od tříd, rozhraní neposkytují implementace. Jsou implementované třídami a definovány jako samostatné subjekty ze tříd. Rozhraní představuje smlouvu v tom, že třídu, která implementuje rozhraní musí implementovat všechny aspekty tohoto rozhraní přesně tak, jak je definována.

Definování rozhraní:

```csharp
interface ISampleInterface
{
    void doSomething();
}
```

Pro implementaci rozhraní ve třídě:

```csharp
class SampleClass : ISampleInterface
{
    void ISampleInterface.doSomething()
    {
        // Method implementation.
    }
}
```

Další informace naleznete v tématu:

[Rozhraní](../../../csharp/programming-guide/interfaces/index.md)

[rozhraní](../../../csharp/language-reference/keywords/interface.md)

## <a name="Generics"></a> Obecné typy

Třídy, struktury, rozhraní a metody v rozhraní .NET Framework může zahrnovat *parametry typu* , které definují typy objektů, které lze uložit nebo použít. Nejběžnějším příkladem obecných typů je kolekce, kde můžete určit typ objektu, který bude uložen do kolekce.

Chcete-li definovat obecnou třídu:

```csharp
public class SampleGeneric<T>
{
    public T Field;
}
```

Vytvoření instance generické třídy:

```csharp
SampleGeneric<string> sampleObject = new SampleGeneric<string>();
sampleObject.Field = "Sample string";
```

Další informace naleznete v tématu:

- [Obecné typy](~/docs/standard/generics/index.md)

- [Obecné typy](../../../csharp/programming-guide/generics/index.md)

## <a name="Delegates"></a> Delegáti

A *delegovat* je typ, který definuje podpis metody a může poskytnout odkaz na jakoukoli metodu s kompatibilním podpisem. Můžete vyvolat (nebo volat) metodu prostřednictvím delegáta. Delegáty se používají pro předávání metod jako argumentů jiným metodám.

> [!NOTE]
> Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů. Další informace o použití delegátů při zpracování událostí naleznete v tématu [události](../../../standard/events/index.md).

K vytvoření delegáta:

```csharp
public delegate void SampleDelegate(string str);
```

Chcete-li vytvořit odkaz na metodu, která odpovídá podpisu zadanému delegátem:

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

Další informace naleznete v tématu:

- [Delegáty](../../../csharp/programming-guide/delegates/index.md)

- [delegát](../../../csharp/language-reference/keywords/delegate.md)

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v C#](../../../csharp/programming-guide/index.md)
