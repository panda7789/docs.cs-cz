---
title: Objektově orientované programování (Visual Basic)
ms.date: 07/20/2015
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
ms.openlocfilehash: 058d8b932e50f784d4a5cefa9fadfb31953687f0
ms.sourcegitcommit: 35316b768394e56087483cde93f854ba607b63bc
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/26/2018
ms.locfileid: "52297085"
---
# <a name="object-oriented-programming-visual-basic"></a>Objektově orientované programování (Visual Basic)

Visual Basic poskytuje plnou podporu pro objektově orientované programování včetně zapouzdření, dědičnosti a polymorfismu.

 *Zapouzdření* znamená, že skupina souvisejících vlastností, metod a ostatní členové jsou považovány za jednu jednotku nebo objekt.

 *Dědičnost* popisuje schopnost vytvářet nové třídy na základě existující třídy.

 *Polymorfismus* znamená, že můžete mít více tříd, které můžete používat Zaměnitelně, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.

 Tato část popisuje následující pojmy:

- [Třídy a objekty](#classes-and-objects)
  - [Členy třídy](#class-members)
    - [Vlastnosti a pole](#properties-and-fields)
    - [Metody](#methods)
    - [Konstruktory](#constructors)
    - [Destruktory](#destructors)
    - [Události](#events)
    - [Vnořené třídy](#nested-classes)
  - [Modifikátory přístupu a úrovně přístupu](#access-modifiers-and-access-levels)
    - [Vytvoření instance třídy](#instantiating-classes)
    - [Sdílené třídy a členy](#shared-classes-and-members)
    - [Anonymní typy](#anonymous-types)
- [Dědičnost](#inheritance)
  - [Obejití členů](#overriding-members)
- [Rozhraní](#interfaces)
- [Obecné typy](#generics)
- [Delegáti](#delegates)

## <a name="classes-and-objects"></a>Třídy a objekty

Podmínky *třídy* a *objekt* se někdy používají vzájemné záměně, ale ve skutečnosti třídy popisují *typ* objektů, zatímco objekty jsou použitelné  *instance* tříd. Ano, je volána při vytvoření objektu *instance*. Při použití analogie matric, třída je podrobný plán a objekt je vytvořen z této matrice budovy.

Definování třídy:

```vb
Class SampleClass
End Class
```

Visual Basic také nabízí jednodušší verzi tříd pojmenovanou *struktury* , které jsou užitečné, když budete chtít vytvořit velké pole objektů a proveďte k tomu k tomu spotřebovat příliš mnoho paměti.

Definování struktury:

```vb
Structure SampleStructure
End Structure
```

Další informace naleznete v tématu:

- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a>Členy třídy

Každá třída může mít různé *členy třídy* obsahující vlastnosti, které popisují data třídy, metody, které určují chování třídy a události, které umožňují komunikaci mezi různými třídami a objekty.

#### <a name="properties-and-fields"></a>Vlastnosti a pole

Pole a vlastnosti představují informace, které obsahuje objekt. Pole jsou jako proměnné, protože mohou být čtena nebo nastavena přímo.

Definování pole:

```vb
Class SampleClass
    Public SampleField As String
End Class
```

Vlastnosti mají get a nastavte postupy, které poskytují větší kontrolu toho, jak jsou hodnoty nastavena nebo vrácena.

Visual Basic můžete buď vytvořit soukromé pole pro uložení hodnoty vlastnosti nebo použít takzvané automaticky implementované vlastnosti, které vytvořit toto pole automaticky na pozadí a poskytnou základní logiku pro procedury vlastností.

Chcete-li definovat automaticky implementovanou vlastnost:

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

Pokud je potřeba provést některé další operace čtení a zápisu hodnoty vlastnosti, definujte pole pro uložení hodnoty vlastnosti a poskytněte základní logiku pro ukládání a načítání:

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

Většina vlastností má metody nebo postupy, jak nastavit a získat hodnotu vlastnosti. Můžete však vytvořit vlastnosti jen pro čtení nebo jen pro zápis, abyste omezili je číst nebo upravovat. V jazyce Visual Basic můžete použít `ReadOnly` a `WriteOnly` klíčová slova. Automaticky implementované vlastnosti nemůže být ale jen pro čtení nebo jen pro zápis.

Další informace naleznete v tématu:

- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Get](../../../visual-basic/language-reference/statements/get-statement.md)
- [Příkaz Set](../../../visual-basic/language-reference/statements/set-statement.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)

#### <a name="methods"></a>Metody

 A *metoda* je akce, které může objekt provádět.

> [!NOTE]
> V jazyce Visual Basic existují dva způsoby, jak vytvořit metodu: `Sub` prohlášení se používá, pokud metoda nevrací hodnotu `Function` prohlášení se používá, pokud metoda vrátí hodnotu.

Chcete-li definovat metodu pro třídu:

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

Třída může mít několik implementací, nebo *přetížení*, stejné metody, která se liší v počtu parametrů nebo typů parametrů.

Chcete-li přetížit metodu:

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

Ve většině případů deklarujete metodu v rámci definice třídy. Ale také podporuje jazyka Visual Basic *rozšiřující metody* , které umožňují přidat metody do existující třídy mimo skutečnou definici třídy.

Další informace naleznete v tématu:

- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)
- [Overloads](../../../visual-basic/language-reference/modifiers/overloads.md)
- [Rozšiřující metody](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)

#### <a name="constructors"></a>Konstruktory

Konstruktory jsou metody třídy, které jsou spouštěny automaticky, když je vytvořen objekt daného typu. Konstruktory obvykle inicializují datové členy nového objektu. Konstruktor lze spustit pouze jednou při vytvoření třídy. Kromě toho kód v konstruktoru se vždy spouští před ostatním kódem ve třídě. Můžete však vytvořit více přetížení konstruktoru stejným způsobem jako u jakékoliv jiné metody.

Chcete-li definovat konstruktor pro třídu:

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class
```

Další informace najdete v tématu: [doba života objektu: jak objekty jsou vytvořená a Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

#### <a name="destructors"></a>Destruktory

Destruktory se používají k destrukci instancí tříd. V rozhraní .NET Framework systému uvolňování paměti automaticky spravuje přidělování a uvolňování paměti pro spravované objekty v aplikaci. Můžete však stále potřebovat destruktory pro vyčištění všech nespravovaných prostředků, které vytváří vaše aplikace. Může existovat pouze jeden destruktor třídy.

Další informace o destruktorech a uvolňování paměti v rozhraní .NET Framework najdete v tématu [uvolňování](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Události

Události umožňují třídám nebo objektům upozornit ostatní třídy nebo objekty, když něco, které vás zajímají. Třída, která odesílá (nebo vyvolává) událost je volána *vydavatele* a třídy, které zobrazí (nebo zpracování) události, se nazývají *předplatitele*. Další informace o událostech, jak jejich vyvolávání a zpracování viz [události](../../../standard/events/index.md).

- Chcete-li deklarovat události, použijte [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).

- Chcete-li vyvolat události, použijte [RaiseEvent – příkaz](../../../visual-basic/language-reference/statements/raiseevent-statement.md).

- Chcete-li určit obslužné rutiny událostí deklarativním způsobem, použijte [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) příkazu a [zpracovává](../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli.

- Aby bylo možné dynamicky přidat, odebrat a změnit obslužnou rutinu události, který je přidružený k události, použijte [AddHandler – příkaz](../../../visual-basic/language-reference/statements/addhandler-statement.md) a [RemoveHandler – příkaz](../../../visual-basic/language-reference/statements/removehandler-statement.md) spolu s [AddressOf Operátor](../../../visual-basic/language-reference/operators/addressof-operator.md).

#### <a name="nested-classes"></a>Vnořené třídy

Třída definována v rámci jiné třídy se nazývá *vnořené*. Ve výchozím nastavení vnořené třídy je privátní.

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

Chcete-li vytvořit instanci vnořené třídy, použijte název třídy kontejneru následovaného tečkou a pak následovaného názvem vnořené třídy:

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Modifikátory přístupu a úrovně přístupu

Všechny třídy a členy třídy můžete určit úroveň přístupu poskytují dalším třídám, pomocí *modifikátorů přístupu*.

K dispozici jsou následující modifikátory přístupu:

|Visual Basic modifikátor|Definice|
|---------------------------|----------------|
|[Public](../../../visual-basic/language-reference/modifiers/public.md)|Tento typ nebo člen je přístupný libovolnému jinému kódu ve stejném sestavení nebo libovolnému sestavení která na něj odkazuje.|
|[Private](../../../visual-basic/language-reference/modifiers/private.md)|Tento typ nebo člen je přístupný pouze kódu ve stejné třídě.|
|[Protected](../../../visual-basic/language-reference/modifiers/protected.md)|Tento typ nebo člen je přístupný pouze kódu ve stejné třídě nebo v odvozené třídě.|
|[Friend](../../../visual-basic/language-reference/modifiers/friend.md)|Tento typ nebo člen je přístupný libovolnému kódu ve stejném sestavení, ale ne z jiného sestavení.|
|`Protected Friend`|Tento typ nebo člen je přístupný libovolnému kódu ve stejném sestavení, nebo kterékoli odvozené třídě v jiném sestavení.|

Další informace najdete v tématu [úrovní v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

### <a name="instantiating-classes"></a>Vytvoření instance třídy

Pro vytvoření objektu, budete muset vytvořit instanci třídy, nebo vytvořit instanci třídy.

```vb
Dim sampleObject as New SampleClass()
```

Po vytvoření instance třídy, můžete přiřadit hodnoty k vlastnosti a pole instance a volat metody třídy.

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

Chcete-li přiřadit hodnoty vlastností během procesu vytváření instance třídy, použijte inicializátory objektů:

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

Další informace naleznete v tématu:

- [Operátor New](../../../visual-basic/language-reference/operators/new-operator.md)
- [Inicializátory objektů: pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

### <a name="shared-classes-and-members"></a>Sdílené třídy a členy

 Sdílenému členu třídy je vlastnost, procedura nebo pole, která je sdílena všemi instancemi třídy.

 Chcete-li definovat sdílenému členu:

```vb
Class SampleClass
    Public Shared SampleString As String = "Sample String"
End Class
```

 Chcete-li přístup ke sdílenému členu, použijte název třídy bez vytvoření objektů této třídy:

```vb
MsgBox(SampleClass.SampleString)
```

 Sdílené moduly v jazyce Visual Basic sdíleli pouze členy a nelze vytvořit instanci. Sdílené členy také nelze přistupovat k vlastnosti nesdílené, polím nebo metodám

 Další informace naleznete v tématu:

- [Shared](../../../visual-basic/language-reference/modifiers/shared.md)
- [Příkaz Module](../../../visual-basic/language-reference/statements/module-statement.md)

### <a name="anonymous-types"></a>Anonymní typy

Anonymní typy umožňují vytvářet objekty bez psaní definice třídy datového typu. Místo toho kompilátor vygeneruje třídu za vás. Třída nemá žádný použitelný název a obsahuje vlastnosti, které jste zadali v rámci deklarace objektu.

Chcete-li vytvořit instanci anonymního typu:

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

Další informace najdete v tématu: [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="inheritance"></a>Dědičnost

Dědičnost umožňuje vytvořit novou třídu, která opakovaně používá, rozšiřuje a upravuje chování, které je definováno v jiné třídě. Třídy, jejíž členové jsou zdědění, se nazývá *základní třída*, a názvem třídy, která dědí tyto členy *odvozené třídy*. Nicméně všechny třídy v jazyce Visual Basic implicitně dědí z <xref:System.Object> třídu, která podporuje hierarchii tříd .NET a poskytuje služby nižší úrovně všem třídám.

> [!NOTE]
> Visual Basic nepodporuje vícenásobnou dědičnost. To znamená můžete zadat pouze jednu základní třídu pro odvozenou třídu.

Chcete-li dědit ze základní třídy:

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

Ve výchozím nastavení je možné zdědit všechny třídy. Můžete však určit, zda třída nesmí používat jako základní třída nebo vytvořit třídu, která lze použít jako základní třídu.

Chcete-li určit, že třídu nelze použít jako základní třídu:

```vb
NotInheritable Class SampleClass
End Class
```

Určíte, že třída může sloužit jako základní třídu a nelze vytvořit instanci:

```vb
MustInherit Class BaseClass
End Class
```

Další informace naleznete v tématu:

- [Příkaz Inherits](../../../visual-basic/language-reference/statements/inherits-statement.md)
- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>Obejití členů

Ve výchozím nastavení dědí odvozená třída všechny členy ze své základní třídy. Pokud chcete změnit chování zděděného člena, musíte ho potlačit. To znamená můžete definovat novou implementaci metody, vlastnosti nebo události v odvozené třídě.

Následující modifikátory umožňují určit, jak přepsat vlastnosti a metody:

|Visual Basic modifikátor|Definice|
|---------------------------|----------------|
|[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)|Umožňuje člen třídy k přepsání v odvozené třídě.|
|[Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)|Přepsání virtuální (s možností přepsání) člena definovaného v základní třídě.|
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|Zabrání přepsání v dědičné třídě člena.|
|[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)|Vyžaduje, aby člen třídy k přepsání v odvozené třídě.|
|[Shadows](../../../visual-basic/language-reference/modifiers/shadows.md)|Skryje člena zděděného ze základní třídy|

## <a name="interfaces"></a>Rozhraní

Rozhraní, stejně jako třídy, definují sadu vlastností, metody a události. Ale na rozdíl od tříd, rozhraní neposkytují implementace. Jsou implementované třídami a definovány jako samostatné subjekty ze tříd. Rozhraní představuje smlouvu v tom, že třídu, která implementuje rozhraní musí implementovat všechny aspekty tohoto rozhraní přesně tak, jak je definována.

Definování rozhraní:

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

Pro implementaci rozhraní ve třídě:

```vb
Class SampleClass
    Implements ISampleInterface
    Sub DoSomething
        ' Method implementation.
    End Sub
End Class
```

Další informace naleznete v tématu:

- [Rozhraní](../../../visual-basic/programming-guide/language-features/interfaces/index.md)
- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)

## <a name="generics"></a>Obecné typy

Třídy, struktury, rozhraní a metody v rozhraní .NET může zahrnovat *parametry typu* , které definují typy objektů, které lze uložit nebo použít. Nejběžnějším příkladem obecných typů je kolekce, kde můžete určit typ objektu, který bude uložen do kolekce.

Chcete-li definovat obecnou třídu:

```vb
Class SampleGeneric(Of T)
    Public Field As T
End Class
```

Vytvoření instance generické třídy:

```vb
Dim sampleObject As New SampleGeneric(Of String)
sampleObject.Field = "Sample string"
```

Další informace naleznete v tématu:

- [Obecné typy](../../../standard/generics/index.md)
- [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a>Delegáty

 A *delegovat* je typ, který definuje podpis metody a může poskytnout odkaz na jakoukoli metodu s kompatibilním podpisem. Můžete vyvolat (nebo volat) metodu prostřednictvím delegáta. Delegáty se používají pro předávání metod jako argumentů jiným metodám.

> [!NOTE]
> Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů. Další informace o použití delegátů při zpracování událostí naleznete v tématu [události](../../../standard/events/index.md).

K vytvoření delegáta:

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

Chcete-li vytvořit odkaz na metodu, která odpovídá podpisu zadanému delegátem:

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

Další informace naleznete v tématu:

- [Delegáti](../../../visual-basic/programming-guide/language-features/delegates/index.md)
- [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [Operátor AddressOf](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>Viz také:

- [Průvodce programováním v jazyce Visual Basic](../../../visual-basic/programming-guide/index.md)
