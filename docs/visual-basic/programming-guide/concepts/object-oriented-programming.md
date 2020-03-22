---
title: Objektově orientované programování
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 3739919273f4cdd285d519c414c542f1a82a16d2
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400685"
---
# <a name="object-oriented-programming-visual-basic"></a>Objektově orientované programování (Visual Basic)

Visual Basic poskytuje plnou podporu pro objektově orientované programování včetně zapouzdření, dědičnosti a polymorfismu.

 *Zapouzdření* znamená, že skupina souvisejících vlastností, metod a dalších členů je považována za jednu jednotku nebo objekt.

 *Dědičnost* popisuje schopnost vytvářet nové třídy založené na existující třídě.

 *Polymorfismus* znamená, že můžete mít více tříd, které lze použít zaměnitelně, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.

 Tato část popisuje následující pojmy:

- [Třídy a objekty](#classes-and-objects)
  - [Členové třídy](#class-members)
    - [Vlastnosti a pole](#properties-and-fields)
    - [Metody](#methods)
    - [Konstruktory](#constructors)
    - [Destruktory](#destructors)
    - [Akce](#events)
    - [Vnořené třídy](#nested-classes)
  - [Modifikátory přístupu a úrovně přístupu](#access-modifiers-and-access-levels)
    - [Vytváření vytváření konkrecí tříd](#instantiating-classes)
    - [Sdílené třídy a členové](#shared-classes-and-members)
    - [Anonymní typy](#anonymous-types)
- [Dědičnost](#inheritance)
  - [Převažující členové](#overriding-members)
- [Rozhraní](#interfaces)
- [Obecné typy](#generics)
- [Delegáty](#delegates)

## <a name="classes-and-objects"></a>Třídy a objekty

Termíny *třídy* a *objektu* jsou někdy *používány* zaměnitelně, ale ve skutečnosti třídy popisují *typ* objektů, zatímco objekty jsou použitelné instance tříd. Takže akt vytvoření objektu se nazývá *inkaso*. Pomocí analogie podrobného plánu je třída podrobný plán a objekt je budova vyrobená z tohoto podrobného plánu.

Definování třídy:

```vb
Class SampleClass
End Class
```

Visual Basic také poskytuje světlo verzi tříd y nazývaných *struktury,* které jsou užitečné, když potřebujete vytvořit velké pole objektů a nechcete spotřebovávat příliš mnoho paměti pro to.

Definování struktury:

```vb
Structure SampleStructure
End Structure
```

Další informace naleznete v tématu:

- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a>Členové třídy

Každá třída může mít různé *členy třídy,* které obsahují vlastnosti, které popisují data třídy, metody, které definují chování třídy a události, které poskytují komunikaci mezi různými třídami a objekty.

#### <a name="properties-and-fields"></a>Vlastnosti a pole

Pole a vlastnosti představují informace, které objekt obsahuje. Pole jsou jako proměnné, protože je lze číst nebo nastavit přímo.

Definování pole:

```vb
Class SampleClass
    Public SampleField As String
End Class
```

Vlastnosti mají get a set postupy, které poskytují větší kontrolu nad tím, jak jsou hodnoty nastaveny nebo vráceny.

Visual Basic umožňuje buď vytvořit soukromé pole pro ukládání hodnoty vlastnosti nebo použít takzvané automaticky implementované vlastnosti, které vytvářejí toto pole automaticky na pozadí a poskytují základní logiku pro procedury vlastností.

Definování automaticky implementované vlastnosti:

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

Pokud potřebujete provést některé další operace pro čtení a zápis hodnoty vlastnosti, definujte pole pro ukládání hodnoty vlastnosti a zadejte základní logiku pro ukládání a načítání:

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

Většina vlastností má metody nebo postupy pro nastavení i získání hodnoty vlastnosti. Můžete však vytvořit vlastnosti jen pro čtení nebo jen pro zápis, které jim zabrání v jejich úpravách nebo čtení. V jazyce Visual `ReadOnly` `WriteOnly` Basic můžete použít klíčová slova. Automaticky implementované vlastnosti však nelze jen pro čtení nebo jen pro zápis.

Další informace naleznete v tématu:

- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Get](../../../visual-basic/language-reference/statements/get-statement.md)
- [Příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a>Metody

 *Metoda* je akce, kterou může objekt provést.

> [!NOTE]
> V jazyce Visual Basic existují dva způsoby, jak vytvořit metodu: `Sub` příkaz se používá, pokud metoda nevrátí hodnotu; příkaz `Function` se používá, pokud metoda vrátí hodnotu.

Definování metody třídy:

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

Třída může mít několik implementací nebo *přetížení*stejné metody, které se liší v počtu parametrů nebo typů parametrů.

Přetížení metody:

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

Ve většině případů deklarujete metodu v rámci definice třídy. Visual Basic však také podporuje *metody rozšíření,* které umožňují přidat metody do existující třídy mimo skutečnou definici třídy.

Další informace naleznete v tématu:

- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Přetížení](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Metody rozšíření](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a>Konstruktory

Konstruktory jsou metody třídy, které jsou prováděny automaticky při vytvoření objektu daného typu. Konstruktory obvykle inicializovat datové členy nového objektu. Konstruktor lze spustit pouze jednou při vytvoření třídy. Kromě toho kód v konstruktoru vždy spustí před jakýkoli jiný kód ve třídě. Můžete však vytvořit více přetížení konstruktoru stejným způsobem jako pro jakoukoli jinou metodu.

Definování konstruktoru pro třídu:

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

Další informace naleznete v [tématu: Životnost objektu: Jak jsou objekty vytvořeny a zničeny](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

#### <a name="destructors"></a>Destruktory

Destruktory se používají k destrukci instancí tříd. V rozhraní .NET Framework systém uvolňování paměti automaticky spravuje přidělení a uvolnění paměti pro spravované objekty ve vaší aplikaci. Však stále může být nutné destruktory vyčistit všechny nespravované prostředky, které vytvoří vaše aplikace. Pro třídu může existovat pouze jeden destruktor.

Další informace o destruktorech a uvolňování paměti v rozhraní .NET Framework naleznete v [tématu Garbage Collection](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Akce

Události umožňují třídy nebo objekt upozorňovat jiné třídy nebo objekty, když dojde k něčemu zajímavého. Třída, která odesílá (nebo vyvolává) událost se nazývá *vydavatel* a třídy, které přijímají (nebo zpracovávají) událost se nazývají *předplatitelé*. Další informace o událostech, jak jsou vyvolány a zpracovány, naleznete v [tématu Události](../../../standard/events/index.md).

- Chcete-li deklarovat události, použijte [příkaz události](../../../visual-basic/language-reference/statements/event-statement.md).

- Chcete-li vyvolat události, použijte [RaiseEvent prohlášení](../../../visual-basic/language-reference/statements/raiseevent-statement.md).

- Chcete-li určit obslužné rutiny událostí pomocí deklarativního způsobu, použijte příkaz [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) a klauzuli [Handles.](../../../visual-basic/language-reference/statements/handles-clause.md)

- Chcete-li dynamicky přidávat, odebírat a měnit obslužnou rutinu události přidruženou k události, použijte [příkaz AddHandler](../../../visual-basic/language-reference/statements/addhandler-statement.md) a [příkaz RemoveHandler](../../../visual-basic/language-reference/statements/removehandler-statement.md) společně s [operátorem AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md).

#### <a name="nested-classes"></a>Vnořené třídy

Třída definovaná v rámci jiné třídy se nazývá *vnořené*. Ve výchozím nastavení je vnořená třída soukromá.

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

Chcete-li vytvořit instanci vnořené třídy, použijte název třídy kontejneru následovaný tečkou a poté název vnořené třídy:

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Modifikátory přístupu a úrovně přístupu

Všechny třídy a členové třídy můžete určit, jakou úroveň přístupu poskytují ostatním třídám pomocí *modifikátorů přístupu*.

K dispozici jsou následující modifikátory přístupu:

|Modifikátor jazyka Visual Basic|Definice|
|---------------------------|----------------|
|[Public](../../../visual-basic/language-reference/modifiers/public.md)|Typ nebo člen lze přistupovat libovolný jiný kód ve stejném sestavení nebo jiné sestavení, které odkazuje na něj.|
|[Private](../../../visual-basic/language-reference/modifiers/private.md)|Typ nebo člen lze přistupovat pouze podle kódu ve stejné třídě.|
|[Chráněné](../../../visual-basic/language-reference/modifiers/protected.md)|Typ nebo člen lze přistupovat pouze podle kódu ve stejné třídě nebo v odvozené třídě.|
|[Friend](../../../visual-basic/language-reference/modifiers/friend.md)|Typ nebo člen lze přistupovat libovolný kód ve stejném sestavení, ale ne z jiného sestavení.|
|`Protected Friend`|Typ nebo člen lze přistupovat libovolný kód ve stejném sestavení nebo jakékoli odvozené třídy v jiném sestavení.|

Další informace naleznete [v tématu Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

### <a name="instantiating-classes"></a>Vytváření vytváření konkrecí tříd

Chcete-li vytvořit objekt, musíte vytvořit instanci třídy nebo vytvořit instanci třídy.

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

Chcete-li přiřadit hodnoty vlastnostem během procesu instanování třídy, použijte inicializační metody objektu:

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

Další informace naleznete v tématu:

- [Nový operátor](../../../visual-basic/language-reference/operators/new-operator.md)
- [Inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

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

 Sdílené moduly v jazyce Visual Basic mají pouze sdílené členy a nelze vytvořit instanci. Sdílené členy také nemají přístup k nesdíleným vlastnostem, polím nebo metodám.

 Další informace naleznete v tématu:

- [Sdílená](../../../visual-basic/language-reference/modifiers/shared.md)
- [Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a>Anonymní typy

Anonymní typy umožňují vytvářet objekty bez zápisu definice třídy pro datový typ. Místo toho kompilátor generuje třídu pro vás. Třída nemá žádný použitelný název a obsahuje vlastnosti, které zadáte při deklarování objektu.

Vytvoření instance anonymního typu:

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

Další informace naleznete v tématu [Anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="inheritance"></a>Dědičnost

Dědičnost umožňuje vytvořit novou třídu, která opakovaně používá, rozšiřuje a upravuje chování, které je definováno v jiné třídě. Třída, jejíž členové jsou zděděni, se nazývá *základní třída*a třída, která tyto členy dědí, se nazývá *odvozená třída*. Všechny třídy v jazyce Visual <xref:System.Object> Basic však implicitně dědí z třídy, která podporuje hierarchii tříd .NET a poskytuje služby nižší úrovně pro všechny třídy.

> [!NOTE]
> Visual Basic nepodporuje vícenásobné dědičnosti. To znamená, že můžete zadat pouze jednu základní třídu pro odvozenou třídu.

Dědit ze základní třídy:

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

Ve výchozím nastavení mohou být zděděny všechny třídy. Můžete však určit, zda třída nesmí být použita jako základní třída, nebo vytvořit třídu, kterou lze použít pouze jako základní třídu.

Chcete-li určit, že třídu nelze použít jako základní třídu:

```vb
NotInheritable Class SampleClass
End Class
```

Chcete-li určit, že třídu lze použít pouze jako základní třídu a nelze vytvořit instanci:

```vb
MustInherit Class BaseClass
End Class
```

Další informace naleznete v tématu:

- [Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>Převažující členové

Ve výchozím nastavení odvozená třída dědí všechny členy ze své základní třídy. Pokud chcete změnit chování zděděného člena, je třeba jej přepsat. To znamená, že můžete definovat novou implementaci metody, vlastnosti nebo události v odvozené třídě.

Následující modifikátory se používají k řízení, jak jsou přepsány vlastnosti a metody:

|Modifikátor jazyka Visual Basic|Definice|
|---------------------------|----------------|
|[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)|Umožňuje přepsání člena třídy v odvozené třídě.|
|[Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)|Přepíše virtuální (overridable) člen definovaný v základní třídě.|
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|Zabrání člen přepsána v dědění třídy.|
|[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)|Vyžaduje, aby člen třídy přepsán v odvozené třídě.|
|[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)|Skryje člena zděděného ze základní třídy.|

## <a name="interfaces"></a>Rozhraní

Rozhraní, jako jsou třídy, definují sadu vlastností, metod a událostí. Ale na rozdíl od tříd, rozhraní neposkytují implementaci. Jsou implementovány třídami a definovány jako samostatné entity od tříd. Rozhraní představuje smlouvu v tom, že třída, která implementuje rozhraní musí implementovat každý aspekt tohoto rozhraní přesně tak, jak je definována.

Chcete-li definovat rozhraní:

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

Chcete-li implementovat rozhraní ve třídě:

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

Další informace naleznete v tématu:

- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a>Obecné typy

Třídy, struktury, rozhraní a metody v rozhraní .NET mohou zahrnovat *parametry typu,* které definují typy objektů, které mohou ukládat nebo používat. Nejběžnějším příkladem obecných typů je kolekce, kde můžete určit typ objektů, které mají být uloženy v kolekci.

Definování obecné třídy:

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

Chcete-li vytvořit instanci obecné třídy:

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

Další informace naleznete v tématu:

- [Obecné typy](../../../standard/generics/index.md)
- [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a>Delegáty

 *Delegát* je typ, který definuje podpis metody a může poskytnout odkaz na libovolnou metodu s kompatibilním podpisem. Můžete vyvolat (nebo volat) metodu prostřednictvím delegáta. Delegáty se používají pro předávání metod jako argumentů jiným metodám.

> [!NOTE]
> Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů. Další informace o použití delegátů při zpracování událostí naleznete v [tématu Události](../../../standard/events/index.md).

Vytvoření delegáta:

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

- [Delegáty](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>Viz také

- [Příručka k programování v jazyce Visual Basic](../../../visual-basic/programming-guide/index.md)
