---
title: Objektově orientované programování
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: f7e222cde8ce80d4c52cc8b4b111c576eb4041b9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84413190"
---
# <a name="object-oriented-programming-visual-basic"></a>Objektově orientované programování (Visual Basic)

Visual Basic poskytuje úplnou podporu pro objektově orientované programování včetně zapouzdření, dědičnosti a polymorfismu.

 *Zapouzdření* znamená, že skupina souvisejících vlastností, metod a dalších členů je považována za jednu jednotku nebo objekt.

 *Dědičnost* popisuje možnost vytvářet nové třídy na základě existující třídy.

 *Polymorfismus* znamená, že můžete mít více tříd, které lze použít zaměnitelné, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.

 Tato část popisuje následující koncepty:

- [Třídy a objekty](#classes-and-objects)
  - [Členové třídy](#class-members)
    - [Vlastnosti a pole](#properties-and-fields)
    - [Metody](#methods)
    - [Konstruktory](#constructors)
    - [Destruktory](#destructors)
    - [Události](#events)
    - [Vnořené třídy](#nested-classes)
  - [Modifikátory přístupu a úrovně přístupu](#access-modifiers-and-access-levels)
    - [Vytváření instancí tříd](#instantiating-classes)
    - [Sdílené třídy a členové](#shared-classes-and-members)
    - [Anonymní typy](#anonymous-types)
- [Dědičnost](#inheritance)
  - [Přepisování členů](#overriding-members)
- [Rozhraní](#interfaces)
- [Obecné typy](#generics)
- [Delegáti](#delegates)

## <a name="classes-and-objects"></a>Třídy a objekty

*Třída* terms a *Object* se někdy používají zaměnitelné, ale ve skutečnosti třídy popisují *typ* objektů, zatímco objekty jsou použitelné *instance* tříd. To znamená, že vytvoření objektu se nazývá vytváření *instancí*. Pomocí analogie podrobného plánu je třída plán a objekt je sestaven z tohoto podrobného plánu.

Definování třídy:

```vb
Class SampleClass
End Class
```

Visual Basic také poskytuje světlou verzi tříd nazvaných *struktury* , které jsou užitečné v případě, že potřebujete vytvořit velké pole objektů a nechcete pro ně spotřebovat příliš mnoho paměti.

Definování struktury:

```vb
Structure SampleStructure
End Structure
```

Další informace naleznete v tématu:

- [Class – příkaz](../../language-reference/statements/class-statement.md)
- [Structure – příkaz](../../language-reference/statements/structure-statement.md)

### <a name="class-members"></a>Členové třídy

Každá třída může mít různé *členy třídy* , které obsahují vlastnosti, které popisují data třídy, metody, které definují chování třídy, a události, které poskytují komunikaci mezi různými třídami a objekty.

#### <a name="properties-and-fields"></a>Vlastnosti a pole

Pole a vlastnosti reprezentují informace, které objekt obsahuje. Pole jsou jako proměnné, protože je lze číst nebo nastavit přímo.

Definování pole:

```vb
Class SampleClass
    Public SampleField As String
End Class
```

Vlastnosti mají procedury Get a set, které poskytují větší kontrolu nad tím, jak jsou hodnoty nastaveny nebo vraceny.

Visual Basic umožňuje vytvořit soukromé pole pro uložení hodnoty vlastnosti, nebo použít automaticky implementované vlastnosti, které automaticky vytvoří toto pole na pozadí a poskytnou základní logiku pro procedury vlastností.

Definování automaticky implementované vlastnosti:

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

Pokud potřebujete provést některé další operace pro čtení a zápis hodnoty vlastnosti, definujte pole pro uložení hodnoty vlastnosti a poskytněte základní logiku pro uložení a načtení:

```vb
Class SampleClass
    Private m_Sample As String
    Public Property Sample() As String
        Get
            ' Return the value stored in the field.
            Return m_Sample
        End Get
        Set(ByVal Value As String)
            ' Store the value in the field.
            m_Sample = Value
        End Set
    End Property
End Class
```

Většina vlastností má metody nebo postupy pro nastavení a získání hodnoty vlastnosti. Můžete však vytvořit vlastnosti jen pro čtení nebo jen pro zápis a omezit tak jejich úpravu nebo čtení. V Visual Basic můžete použít `ReadOnly` `WriteOnly` klíčová slova a. Automaticky implementované vlastnosti ale nemůžou být jen pro čtení nebo jen pro zápis.

Další informace naleznete v tématu:

- [Property – příkaz](../../language-reference/statements/property-statement.md)
- [Get – příkaz](../../language-reference/statements/get-statement.md)
- [Set – příkaz](../../language-reference/statements/set-statement.md)
- [ReadOnly](../../language-reference/modifiers/readonly.md)
- [WriteOnly](../../language-reference/modifiers/writeonly.md)

#### <a name="methods"></a>Metody

 *Metoda* je akce, kterou může objekt provádět.

> [!NOTE]
> V Visual Basic existují dva způsoby, jak vytvořit metodu: `Sub` příkaz se používá, pokud metoda nevrací hodnotu `Function` . příkaz se používá, pokud metoda vrátí hodnotu.

Chcete-li definovat metodu třídy:

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

Třída může mít několik implementací nebo *přetížení*stejné metody, která se liší v počtu parametrů nebo typů parametrů.

Přetížení metody:

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

Ve většině případů deklarujete metodu v rámci definice třídy. Nicméně Visual Basic také podporuje *rozšiřující metody* , které umožňují přidat metody do existující třídy mimo skutečnou definici třídy.

Další informace naleznete v tématu:

- [Function – příkaz](../../language-reference/statements/function-statement.md)
- [Sub – příkaz](../../language-reference/statements/sub-statement.md)
- [Přetížení](../../language-reference/modifiers/overloads.md)
- [Metody rozšíření](../language-features/procedures/extension-methods.md)

#### <a name="constructors"></a>Konstruktory

Konstruktory jsou metody třídy, které jsou spouštěny automaticky, když je vytvořen objekt daného typu. Konstruktory obvykle inicializují datové členy nového objektu. Konstruktor lze spustit pouze jednou při vytvoření třídy. Kromě toho kód v konstruktoru se vždy spouští před jakýmkoli jiným kódem ve třídě. Můžete však vytvořit více přetížení konstruktoru stejným způsobem jako u jakékoli jiné metody.

Chcete-li definovat konstruktor pro třídu:

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

Další informace najdete v tématu: [Doba života objektu: vytváření a zničení objektů](../language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

#### <a name="destructors"></a>Destruktory

Destruktory se používají k destrukci instancí tříd. V .NET Framework systém uvolňování paměti automaticky spravuje přidělování a uvolňování paměti pro spravované objekty ve vaší aplikaci. Nicméně stále budete potřebovat destruktory k vyčištění všech nespravovaných prostředků, které vaše aplikace vytvoří. Pro třídu může existovat pouze jeden destruktor.

Další informace o destruktorech a uvolňování paměti v .NET Framework naleznete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Události

Události umožňují třídě nebo objektu upozornit jiné třídy nebo objekty, když dojde k nějakému zájmu. Třída, která odesílá (nebo vyvolává) událost, se nazývá *Vydavatel* a třídy, které přijmou (nebo zpracovávají) událost se nazývají *předplatitelé*. Další informace o událostech, jak jsou vyvolány a zpracovávány, naleznete v tématu [events](../../../standard/events/index.md).

- Chcete-li deklarovat události, použijte [příkaz Event](../../language-reference/statements/event-statement.md).

- Chcete-li vyvolat události, použijte [příkaz RaiseEvent](../../language-reference/statements/raiseevent-statement.md).

- Chcete-li určit obslužné rutiny událostí pomocí deklarativního způsobu, použijte příkaz [WithEvents](../../language-reference/modifiers/withevents.md) a klauzuli [Handles](../../language-reference/statements/handles-clause.md) .

- Aby bylo možné dynamicky přidávat, odebírat a měnit obslužné rutiny události přidružené k události, použijte příkaz [addHandler](../../language-reference/statements/addhandler-statement.md) a [příkaz removeHandler](../../language-reference/statements/removehandler-statement.md) spolu s [operátorem AddressOf](../../language-reference/operators/addressof-operator.md).

#### <a name="nested-classes"></a>Vnořené třídy

Třída definovaná v rámci jiné třídy se nazývá *vnořená*. Ve výchozím nastavení je vnořená třída soukromá.

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

Chcete-li vytvořit instanci vnořené třídy, použijte název třídy kontejneru následovaný tečkou a následně následovaný názvem vnořené třídy:

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Modifikátory přístupu a úrovně přístupu

Všechny třídy a členy třídy mohou určit, jakou úroveň přístupu poskytují jiné třídě, pomocí *modifikátorů přístupu*.

K dispozici jsou následující modifikátory přístupu:

|Modifikátor Visual Basic|Definice|
|---------------------------|----------------|
|[Republik](../../language-reference/modifiers/public.md)|Na daný typ nebo člen je možné přistupovat jakýkoli jiný kód ve stejném sestavení nebo jiném sestavení, které na něj odkazuje.|
|[Hlášen](../../language-reference/modifiers/private.md)|Typ nebo člen je k dispozici pouze pomocí kódu ve stejné třídě.|
|[Proti](../../language-reference/modifiers/protected.md)|Typ nebo člen je k dispozici pouze pomocí kódu ve stejné třídě nebo v odvozené třídě.|
|[Friend](../../language-reference/modifiers/friend.md)|K typu nebo členu může být přistup libovolným kódem ve stejném sestavení, ale nikoli z jiného sestavení.|
|`Protected Friend`|K typu nebo členu může být přistup libovolným kódem ve stejném sestavení nebo libovolnou odvozenou třídou v jiném sestavení.|

Další informace najdete v tématu [úrovně přístupu v Visual Basic](../language-features/declared-elements/access-levels.md).

### <a name="instantiating-classes"></a>Vytváření instancí tříd

Chcete-li vytvořit objekt, je nutné vytvořit instanci třídy nebo vytvořit instanci třídy.

```vb
Dim sampleObject as New SampleClass()
```

Po vytvoření instance třídy můžete přiřadit hodnoty vlastnostem a polím instance a vyvolat metody třídy.

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

Chcete-li přiřadit hodnoty vlastnostem během procesu vytváření instancí třídy, použijte Inicializátory objektů:

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

Další informace naleznete v tématu:

- [New – operátor](../../language-reference/operators/new-operator.md)
- [Inicializátory objektů: pojmenované a anonymní typy](../language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a>Sdílené třídy a členové

 Sdílený člen třídy je vlastnost, procedura nebo pole, které jsou sdíleny všemi instancemi třídy.

 Definování sdíleného člena:

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 Chcete-li získat přístup ke sdílenému členu, použijte název třídy bez vytvoření objektu této třídy:

```vb
MsgBox(SampleClass.SampleString)
```

 Sdílené moduly v Visual Basic mají pouze sdílené členy a nelze je vytvořit z instance. Sdílené členy nemají také přístup k nesdíleným vlastnostem, polím nebo metodám.

 Další informace naleznete v tématu:

- [Shared](../../language-reference/modifiers/shared.md)
- [Module – příkaz](../../language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a>Anonymní typy

Anonymní typy umožňují vytvářet objekty bez psaní definice třídy pro datový typ. Místo toho kompilátor vygeneruje třídu za vás. Třída nemá žádný použitelný název a obsahuje vlastnosti, které zadáte v deklaraci objektu.

Vytvoření instance anonymního typu:

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

Další informace najdete v tématech: [anonymní typy](../language-features/objects-and-classes/anonymous-types.md).

## <a name="inheritance"></a>Dědičnost

Dědičnost umožňuje vytvořit novou třídu, která znovu používá, rozšiřuje a upravuje chování, které je definováno v jiné třídě. Třída, jejíž členové jsou zděděni, se nazývají *základní třídu*a třída, která dědí tyto členy, se nazývá *odvozená třída*. Nicméně všechny třídy v Visual Basic implicitně dědí z <xref:System.Object> třídy, která podporuje hierarchii tříd .NET a poskytuje služby nižší úrovně pro všechny třídy.

> [!NOTE]
> Visual Basic nepodporuje vícenásobnou dědičnost. To znamená, že můžete zadat pouze jednu základní třídu pro odvozenou třídu.

Chcete-li dědit ze základní třídy:

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

Ve výchozím nastavení mohou být děděny všechny třídy. Můžete však určit, zda třída nesmí být použita jako základní třída, nebo vytvořit třídu, která může být použita pouze jako základní třída.

Chcete-li určit, že třídu nelze použít jako základní třídu:

```vb
NotInheritable Class SampleClass
End Class
```

Chcete-li určit, že třída může být použita pouze jako základní třída a nemůže být vytvořena instance:

```vb
MustInherit Class BaseClass
End Class
```

Další informace naleznete v tématu:

- [Inherits – příkaz](../../language-reference/statements/inherits-statement.md)
- [NotInheritable](../../language-reference/modifiers/notinheritable.md)
- [MustInherit](../../language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>Přepisování členů

Ve výchozím nastavení zdědí odvozená třída všechny členy ze své základní třídy. Pokud chcete změnit chování zděděného člena, je nutné ho přepsat. To znamená, že můžete definovat novou implementaci metody, vlastnosti nebo události v odvozené třídě.

Následující modifikátory slouží k řízení způsobu přepsání vlastností a metod:

|Modifikátor Visual Basic|Definice|
|---------------------------|----------------|
|[Overridable](../../language-reference/modifiers/overridable.md)|Umožňuje přepsat člena třídy v odvozené třídě.|
|[Přepsání](../../language-reference/modifiers/overrides.md)|Přepíše virtuální (overridabled) člen definovaný v základní třídě.|
|[NotOverridable](../../language-reference/modifiers/notoverridable.md)|Zabraňuje přepsání člena v dědičné třídě.|
|[MustOverride](../../language-reference/modifiers/mustoverride.md)|Vyžaduje, aby byl člen třídy přepsán v odvozené třídě.|
|[Shadows](../../language-reference/modifiers/shadows.md)|Skryje člena zděděného ze základní třídy.|

## <a name="interfaces"></a>Rozhraní

Rozhraní, jako jsou třídy, definují sadu vlastností, metod a událostí. Ale na rozdíl od tříd rozhraní neposkytuje implementaci. Jsou implementovány pomocí tříd a definovány jako samostatné entity ze tříd. Rozhraní představuje kontrakt, v tom smyslu, že třída, která implementuje rozhraní, musí implementovat všechny aspekty tohoto rozhraní přesně tak, jak je definováno.

Definování rozhraní:

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

Implementace rozhraní ve třídě:

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

Další informace naleznete v tématu:

- [Rozhraní](../language-features/interfaces/index.md)
- [Interface – příkaz](../../language-reference/statements/interface-statement.md)
- [Implements – Příkaz](../../language-reference/statements/implements-statement.md)

## <a name="generics"></a>Obecné typy

Třídy, struktury, rozhraní a metody v rozhraní .NET mohou zahrnovat *parametry typu* , které definují typy objektů, které mohou ukládat nebo používat. Nejběžnějším příkladem obecných typů je kolekce, kde můžete určit typ objektů, které mají být uloženy v kolekci.

Definování obecné třídy:

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

Vytvoření instance obecné třídy:

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

Další informace naleznete v tématu:

- [Obecné typy](../../../standard/generics/index.md)
- [Obecné typy v Visual Basic](../language-features/data-types/generic-types.md)

## <a name="delegates"></a>Delegáti

 *Delegát* je typ, který definuje signaturu metody a může poskytnout odkaz na libovolnou metodu s kompatibilní signaturou. Metodu můžete vyvolat (nebo volat) prostřednictvím delegáta. Delegáty se používají pro předávání metod jako argumentů jiným metodám.

> [!NOTE]
> Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů. Další informace o použití delegátů při zpracování událostí najdete v tématu [události](../../../standard/events/index.md).

Postup vytvoření delegáta:

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

Chcete-li vytvořit odkaz na metodu, která odpovídá podpisu určenému delegátem:

```vb
Class SampleClass
    ' Method that matches the SampleDelegate signature.
    Sub SampleSub(ByVal str As String)
        ' Add code here.
    End Sub
    ' Method that instantiates the delegate.
    Sub SampleDelegateSub()
        Dim sd As SampleDelegate = AddressOf SampleSub
        sd("Sample string")
    End Sub
End Class
```

Další informace naleznete v tématu:

- [Delegáti](../language-features/delegates/index.md)
- [Delegate – příkaz](../../language-reference/statements/delegate-statement.md)
- [AddressOf – operátor](../../language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>Viz také

- [Příručka k programování v jazyce Visual Basic](../index.md)
