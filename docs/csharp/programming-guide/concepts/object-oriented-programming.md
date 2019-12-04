---
title: Objektově orientované programování (C#)
ms.date: 07/20/2015
ms.assetid: 89574786-65ef-4335-88bc-fbacd094f183
ms.openlocfilehash: 1de150f6eb4be893ca1afce6bd16afde5752c986
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711824"
---
# <a name="object-oriented-programming-c"></a>Objektově orientované programování (C#)

C#poskytuje úplnou podporu pro objektově orientované programování včetně zapouzdření, dědičnosti a polymorfismu.

*Zapouzdření* znamená, že skupina souvisejících vlastností, metod a dalších členů je považována za jednu jednotku nebo objekt.

*Dědičnost* popisuje možnost vytvářet nové třídy na základě existující třídy.

*Polymorfismus* znamená, že můžete mít více tříd, které lze použít zaměnitelné, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.

Tato část popisuje následující koncepty:

- [Třídy a objekty](#Classes)

  - [Členové třídy](#Members)

    - [Vlastnosti a pole](#Properties)

    - [Metody](#Methods)

    - [Konstruktory](#Constructors)

    - [Finalizační metody](#Finalizers)

    - [Události](#Events)

    - [Vnořené třídy](#NestedClasses)

  - [Modifikátory přístupu a úrovně přístupu](#AccessModifiers)

  - [Vytváření instancí tříd](#InstantiatingClasses)

  - [Statické třídy a členy](#Static)

  - [Anonymní typy](#AnonymousTypes)

- [Dědičnost](#Inheritance)

  - [Přepisování členů](#Overriding)

- [Rozhraní](#Interfaces)

- [Obecné typy](#Generics)

- [Delegáty](#Delegates)

## <a name="Classes"></a>Třídy a objekty

*Třída* terms a *Object* se někdy používají zaměnitelné, ale ve skutečnosti třídy popisují *typ* objektů, zatímco objekty jsou použitelné *instance* tříd. To znamená, že vytvoření objektu se nazývá vytváření *instancí*. Pomocí analogie podrobného plánu je třída plán a objekt je sestaven z tohoto podrobného plánu.

Definování třídy:

```csharp
class SampleClass
{
}
```

C#poskytuje také světlou verzi tříd nazvaných *struktury* , které jsou užitečné v případě, že potřebujete vytvořit velké pole objektů a nechcete pro ně spotřebovat příliš mnoho paměti.

Definování struktury:

```csharp
struct SampleStruct
{
}
```

Další informace najdete v části .

- [class](../../language-reference/keywords/class.md)

- [struct](../../language-reference/keywords/struct.md)

### <a name="Members"></a>Členové třídy

Každá třída může mít různé *členy třídy* , které obsahují vlastnosti, které popisují data třídy, metody, které definují chování třídy, a události, které poskytují komunikaci mezi různými třídami a objekty.

#### <a name="Properties"></a>Vlastnosti a pole

Pole a vlastnosti reprezentují informace, které objekt obsahuje. Pole jsou jako proměnné, protože je lze číst nebo nastavit přímo.

Definování pole:

```csharp
class SampleClass
{
    public string sampleField;
}
```

Vlastnosti mají procedury Get a set, které poskytují větší kontrolu nad tím, jak jsou hodnoty nastaveny nebo vraceny.

C#umožňuje vytvořit soukromé pole pro uložení hodnoty vlastnosti nebo použít automaticky implementované vlastnosti, které vytváří toto pole automaticky na pozadí a poskytuje základní logiku pro procedury vlastností.

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
        get { return _sample; }
        // Store the value in the field.
        set { _sample = value; }
    }
}
```

Většina vlastností má metody nebo postupy pro nastavení a získání hodnoty vlastnosti. Můžete však vytvořit vlastnosti jen pro čtení nebo jen pro zápis a omezit tak jejich úpravu nebo čtení. V C#nástroji můžete vynechat metodu vlastnosti `get` nebo `set`. Automaticky implementované vlastnosti ale nemůžou být jen pro čtení nebo jen pro zápis.

Další informace najdete v části .

- [get](../../language-reference/keywords/get.md)

- [set](../../language-reference/keywords/set.md)

#### <a name="Methods"></a>Způsobů

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

Ve většině případů deklarujete metodu v rámci definice třídy. Nicméně podporuje C# také *metody rozšíření* , které umožňují přidat metody do existující třídy mimo skutečnou definici třídy.

Další informace najdete v části .

- [Metody](../classes-and-structs/methods.md)

- [Rozšiřující metody](../classes-and-structs/extension-methods.md)

#### <a name="Constructors"></a>Konstruktory

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

#### <a name="Finalizers"></a>Finalizační metody

Finalizační metody slouží k destrukci instancí tříd. V .NET Framework systém uvolňování paměti automaticky spravuje přidělování a uvolňování paměti pro spravované objekty ve vaší aplikaci. Nicméně stále budete potřebovat finalizační metody k vyčištění všech nespravovaných prostředků, které vaše aplikace vytvoří. Pro třídu může existovat pouze jeden finalizační metoda.

Další informace o finalizační a uvolňování paměti v .NET Framework naleznete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).

#### <a name="Events"></a>Událost

Události umožňují třídě nebo objektu upozornit jiné třídy nebo objekty, když dojde k nějakému zájmu. Třída, která odesílá (nebo vyvolává) událost, se nazývá *Vydavatel* a třídy, které přijmou (nebo zpracovávají) událost se nazývají *předplatitelé*. Další informace o událostech, jak jsou vyvolány a zpracovávány, naleznete v tématu [events](../../../standard/events/index.md).

- Chcete-li deklarovat událost ve třídě, použijte klíčové slovo [Event](../../language-reference/keywords/event.md) .

- Chcete-li vyvolat událost, vyvolejte delegáta události.

- K přihlášení k odběru události použijte operátor `+=`; Chcete-li zrušit odběr události, použijte operátor `-=`.

#### <a name="NestedClasses"></a>Vnořené třídy

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

### <a name="AccessModifiers"></a>Modifikátory přístupu a úrovně přístupu

Všechny třídy a členy třídy mohou určit, jakou úroveň přístupu poskytují jiné třídě, pomocí *modifikátorů přístupu*.

K dispozici jsou následující modifikátory přístupu:

|C#Upravující|Definice|
|------------------|----------------|
|[public](../../language-reference/keywords/public.md)|Na daný typ nebo člen je možné přistupovat jakýkoli jiný kód ve stejném sestavení nebo jiném sestavení, které na něj odkazuje.|
|[private](../../language-reference/keywords/private.md)|Typ nebo člen je k dispozici pouze pomocí kódu ve stejné třídě.|
|[protected](../../language-reference/keywords/protected.md)|Typ nebo člen je k dispozici pouze pomocí kódu ve stejné třídě nebo v odvozené třídě.|
|[internal](../../language-reference/keywords/internal.md)|K typu nebo členu může být přistup libovolným kódem ve stejném sestavení, ale nikoli z jiného sestavení.|
|[protected internal](../../language-reference/keywords/protected-internal.md)|K typu nebo členu může být přistup libovolným kódem ve stejném sestavení nebo libovolnou odvozenou třídou v jiném sestavení.|
|[private protected](../../language-reference/keywords/private-protected.md)|Typ nebo člen je k dispozici v kódu ve stejné třídě nebo v odvozené třídě v rámci sestavení základní třídy.|

Další informace najdete v tématu [modifikátory přístupu](../classes-and-structs/access-modifiers.md).

### <a name="InstantiatingClasses"></a>Vytváření instancí tříd

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

Další informace najdete v části .

- [new – operátor](../../language-reference/operators/new-operator.md)

- [Inicializátory objektu a kolekce](../classes-and-structs/object-and-collection-initializers.md)

### <a name="Static"></a>Statické třídy a členy

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

Statické třídy v C# mají pouze statické členy a nelze je vytvořit z instance. Statické členy také nemají přístup k nestatickým vlastnostem, polím nebo metodám.

Další informace naleznete zde: [static](../../language-reference/keywords/static.md).

### <a name="AnonymousTypes"></a>Anonymní typy

Anonymní typy umožňují vytvářet objekty bez psaní definice třídy pro datový typ. Místo toho kompilátor vygeneruje třídu za vás. Třída nemá žádný použitelný název a obsahuje vlastnosti, které zadáte v deklaraci objektu.

Vytvoření instance anonymního typu:

```csharp
// sampleObject is an instance of a simple anonymous type.
var sampleObject =
    new { FirstProperty = "A", SecondProperty = "B" };
```

Další informace najdete v tématech: [anonymní typy](../classes-and-structs/anonymous-types.md).

## <a name="Inheritance"></a>Dědičnost

Dědičnost umožňuje vytvořit novou třídu, která znovu používá, rozšiřuje a upravuje chování, které je definováno v jiné třídě. Třída, jejíž členové jsou zděděni, se nazývají *základní třídu*a třída, která dědí tyto členy, se nazývá *odvozená třída*. Nicméně všechny třídy v C# implicitně dědí z třídy <xref:System.Object>, která podporuje hierarchii tříd .NET a poskytuje služby nižší úrovně pro všechny třídy.

> [!NOTE]
> C#nepodporuje vícenásobnou dědičnost. To znamená, že můžete zadat pouze jednu základní třídu pro odvozenou třídu.

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

Další informace najdete v části .

- [sealed](../../language-reference/keywords/sealed.md)

- [abstract](../../language-reference/keywords/abstract.md)

### <a name="Overriding"></a>Přepisování členů

Ve výchozím nastavení zdědí odvozená třída všechny členy ze své základní třídy. Pokud chcete změnit chování zděděného člena, je nutné ho přepsat. To znamená, že můžete definovat novou implementaci metody, vlastnosti nebo události v odvozené třídě.

Následující modifikátory slouží k řízení způsobu přepsání vlastností a metod:

|C#Upravující|Definice|
|------------------|----------------|
|[virtual](../../language-reference/keywords/virtual.md)|Umožňuje přepsat člena třídy v odvozené třídě.|
|[override](../../language-reference/keywords/override.md)|Přepíše virtuální (overridabled) člen definovaný v základní třídě.|
|[abstract](../../language-reference/keywords/abstract.md)|Vyžaduje, aby byl člen třídy přepsán v odvozené třídě.|
|[new – modifikátor](../../language-reference/keywords/new-modifier.md)|Skryje člena zděděného ze základní třídy.|

## <a name="Interfaces"></a>Interfaces

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

Další informace najdete v části .

[Rozhraní](../interfaces/index.md)

[interface](../../language-reference/keywords/interface.md)

## <a name="Generics"></a>Obecné typy

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

Další informace najdete v části .

- [Obecné typy](../../../standard/generics/index.md)

- [Obecné typy](../generics/index.md)

## <a name="Delegates"></a>Deleguje

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

Další informace najdete v části .

- [Delegáty](../delegates/index.md)

- [delegate](../../language-reference/builtin-types/reference-types.md)

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce C#](../index.md)
