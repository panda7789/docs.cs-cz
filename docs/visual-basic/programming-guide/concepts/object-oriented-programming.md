---
title: "Objektově orientované programování (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
ms.assetid: 49794de4-64c3-473c-b8ed-fe98835df69c
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 950f080949dce0fc1a2834825d2f7c945007fb7b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="object-oriented-programming-visual-basic"></a>Objektově orientované programování (Visual Basic)
Visual Basic poskytuje úplnou podporu pro objektově orientované programování včetně zapouzdření, dědičnost a polymorfismus.  
  
 *Zapouzdření* znamená, že skupina souvisejících vlastností, metod a ostatní členové jsou považovány za jednu jednotku nebo objekt.  
  
 *Dědičnost* popisuje schopnost vytvářet nové třídy založené na existující třídy.  
  
 *Polymorfismus* znamená, že můžete mít více tříd, které lze použít zcela zaměnitelným významem, i když každá třída implementuje stejné vlastnosti nebo metody různými způsoby.  
  
 Tato část popisuje následující koncepty:  
  
-   [Třídy a objekty](#classes-and-objects)  
  
    -   [Členy třídy](#members)  
  
         [Vlastnosti a pole](#properties-and-fields)  
  
         [Metody](#methods)  
  
         [Konstruktory](#constructors)  
  
         [Destruktory](#destructors)  
  
         [Události](#events)  
  
         [Vnořené třídy](#nested-classes)  
  
    -   [Modifikátory přístupu a úrovně přístupu](#access-modifiers-and-access-levels)  
  
    -   [Vytváření instancí třídy](#instantiating-classes)  
  
    -   [Sdílené třídy a členové](#shared-classes-and-members)  
  
    -   [Anonymní typy](#anonymous-types)  
  
-   [Dědičnost](#inheritance)  
  
    -   [Přepis členů](#overriding-members)  
  
-   [Rozhraní](#interfaces)  
  
-   [Obecné typy](#generics)  
  
-   [Delegáti](#delegates)  
  
## <a name="classes-and-objects"></a>Třídy a objekty  
Podmínky *třída* a *objekt* se někdy používají zcela zaměnitelným významem, ale ve skutečnosti třídy popisují *typ* objektů, zatímco objekty jsou použitelné  *instance* tříd. Ano, je volána v rámci vytvoření objektu *vytváření instancí*. Pomocí analogie plán, podle kterého, třída je plán, podle kterého a v budově z tento plán, podle kterého je objekt.

Chcete-li definovat třídu:

```vb  
Class SampleClass
End Class
```

Visual Basic také poskytuje světla verzi třídy názvem *struktury* , jsou užitečné, když potřebujete vytvořit velké pole objektů a proveďte využívat příliš mnoho paměti, pro který chcete.

Chcete-li definovat strukturu:  

```vb
Structure SampleStructure
End Structure
```

Další informace naleznete v tématu:

- [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)

- [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)

### <a name="class-members"></a>Členy třídy
Každá třída může mít různé *třídy členy* , zahrnout vlastnosti, které popisují data třídy, metody, které definují chování třídy a události, které zajišťují komunikaci mezi různými třídami a objekty.

#### <a name="properties-and-fields"></a>Vlastnosti a pole
Pole a vlastnosti představují informací, které obsahuje objekt. Pole jsou jako proměnné, protože můžou být číst nebo nastavovat přímo.

Chcete-li definovat pole:

```vb
Class SampleClass
    Public SampleField As String
End Class
```

Vlastnosti mají get a nastavte postupů, které poskytuje větší kontrolu na tom, jak nastavit nebo vrátil hodnoty.

Visual Basic můžete buď k vytvoření soukromé pole pro ukládání hodnota vlastnosti nebo takzvané automaticky implementované vlastnosti, které vytvořit toto pole automaticky na pozadí, které poskytují základní logiku pro vlastnost postupy.

Chcete-li definovat ve automaticky implementované vlastnosti:

```vb
Class SampleClass
    Public Property SampleProperty as String
End Class
```

Pokud potřebujete provést některé další operace pro čtení a zápis hodnota vlastnosti definice pole pro ukládání hodnota vlastnosti a poskytují základní logiku pro ukládání a načítání ho:

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

Většina vlastnosti mají metody nebo postupy, jak nastavit a získat hodnotu vlastnosti. Můžete však vytvořit vlastnosti jen pro čtení, nebo jen pro zápis je omezit změnit nebo načíst. V jazyce Visual Basic můžete použít `ReadOnly` a `WriteOnly` klíčová slova. Automaticky implementované vlastnosti však nemůže být jen pro čtení nebo jen pro zápis.

Další informace naleznete v tématu:
  
-   [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)  
  
-   [Get – příkaz](../../../visual-basic/language-reference/statements/get-statement.md)  
  
-   [Set – příkaz](../../../visual-basic/language-reference/statements/set-statement.md)  
  
-   [Jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md)  
  
-   [WriteOnly](../../../visual-basic/language-reference/modifiers/writeonly.md)  
  
#### <a name="methods"></a>Metody  
 A *metoda* je akce, která může provádět objekt.  

> [!NOTE]
>  V jazyce Visual Basic, existují dva způsoby vytvoření metodu: `Sub` se použije příkaz, pokud metoda nevrátí hodnotu `Function` se použije příkaz, pokud metoda vrátí hodnotu.

Definovat metodu třídy:

```vb
Class SampleClass
    Public Function SampleFunc(ByVal SampleParam As String)
        ' Add code here
    End Function
End Class
```

Třída může mít několik implementací, nebo *přetížení*, stejné metody, která se budou lišit v počtu parametry nebo typy parametrů.

Chcete-li přetížení metody:

```vb
Overloads Sub Display(ByVal theChar As Char)
    ' Add code that displays Char data.
End Sub
Overloads Sub Display(ByVal theInteger As Integer)
    ' Add code that displays Integer data.
End Sub
```

Ve většině případů deklarujte metodu v definici třídy. Však také podporuje jazyka Visual Basic *rozšiřující metody* které umožňují přidání metody do existující třídy mimo skutečné definice třídy.

Další informace naleznete v tématu:

- [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)  

- [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  

- [Přetížení](../../../visual-basic/language-reference/modifiers/overloads.md)  

- [Metody rozšíření](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)  

#### <a name="constructors"></a>Konstruktory  
Konstruktory jsou metody třídy, které jsou spouštěny automaticky, když je vytvořen objekt daného typu. Konstruktory obvykle inicializovat datových členů nového objektu. Konstruktor lze spustit pouze po vytvoření třídy. Kromě toho kód v konstruktoru vždy spouští před jakýkoli jiný kód v třídě. Můžete však vytvořit více přetížení konstruktor stejným způsobem jako u jakékoliv jiné metody.

Chcete-li definovat konstruktor pro třídu:

```vb
Class SampleClass
    Sub New(ByVal s As String)
        // Add code here.
    End Sub
End Class 
```

Další informace najdete v tématu: [doba života objektu: jak jsou objekty vytvořen a Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md).

#### <a name="destructors"></a>Destruktory
Destruktory se používají k destruct instance tříd. V rozhraní .NET Framework bude systém uvolňování automaticky spravuje přidělování a uvolňování paměti pro spravované objekty v aplikaci. Může však stále zapotřebí destruktory vyčistit všechny nespravovaných prostředků, které vytváří vaše aplikace. Může existovat jenom jeden destruktor pro třídu.

Další informace o destruktory a uvolňování paměti v rozhraní .NET Framework najdete v tématu [uvolňování paměti](../../../standard/garbage-collection/index.md).

#### <a name="events"></a>Události
Události povolit třídu nebo objekt, který chcete upozornit ostatní třídy nebo objekty, když něco zájmu dojde. Třída, která odešle (nebo vyvolá) událost je volána *vydavatele* a třídy, které zobrazí (nebo zpracování) události, se nazývají *Odběratelé, kteří*. Další informace o událostech, způsob jejich jsou vyvolány a zpracovávají, najdete v části [události](../../../standard/events/index.md).

- Chcete-li deklarovat události, použijte [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).

- Chcete-li vyvolávání událostí, použijte [RaiseEvent – příkaz](../../../visual-basic/language-reference/statements/raiseevent-statement.md).

- Pokud chcete zadat obslužných rutin událostí pomocí deklarativní způsob, použijte [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md) příkaz a [zpracovává](../../../visual-basic/language-reference/statements/handles-clause.md) klauzule.

- Abyste mohli dynamicky přidat, odebrat a změnit obslužné rutiny události přidružený k události, použijte [AddHandler – příkaz](../../../visual-basic/language-reference/statements/addhandler-statement.md) a [RemoveHandler – příkaz](../../../visual-basic/language-reference/statements/removehandler-statement.md) společně s [AddressOf Operátor](../../../visual-basic/language-reference/operators/addressof-operator.md).

#### <a name="nested-classes"></a>Vnořené třídy  
Třídy definované v rámci jiné třídy se nazývá *vnořené*. Ve výchozím nastavení je vnořené třídy soukromé.

```vb
Class Container
    Class Nested
    ' Add code here.
    End Class
End Class
```

K vytvoření instance třídy vnořené, použijte název třídy kontejneru, za nímž následuje tečky a po ní následuje název vnořené třídy:

```vb
Dim nestedInstance As Container.Nested = New Container.Nested()
```

### <a name="access-modifiers-and-access-levels"></a>Modifikátory přístupu a úrovně přístupu  
Všechny třídy a jejich členové můžete určit, jakou úroveň přístupu poskytují další třídy pomocí *přístup modifikátory*.

K dispozici jsou následující modifikátory přístupu:

|Modifikátor jazyka Visual Basic|Definice|
|---------------------------|----------------|
|[Veřejné](../../../visual-basic/language-reference/modifiers/public.md)|Typ nebo člen je přístupná jiným kódem ve stejném sestavení nebo jiné sestavení, které na ni odkazuje.|
|[Privátní](../../../visual-basic/language-reference/modifiers/private.md)|Typ nebo člen můžete přistupovat pouze kódu ve stejné třídě.|
|[Chráněný](../../../visual-basic/language-reference/modifiers/protected.md)|Typ nebo člen můžete přistupovat pouze kódu ve stejné třídě nebo v odvozené třídě.|
|[Friend](../../../visual-basic/language-reference/modifiers/friend.md)|Typ nebo člen je přístupný kód ve stejném sestavení, ale nikoli z jiné sestavení.|
|`Protected Friend`|Typ nebo člen je přístupná žádný kód ve stejném sestavení, nebo všechny odvozené třídy v jiném sestavení.|

Další informace najdete v tématu [úrovně v jazyce Visual Basic přístupu](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md).

### <a name="instantiating-classes"></a>Vytváření instancí třídy  
Pro vytvoření objektu, musíte vytvořit instanci třídy, nebo vytvořit instanci třídy.

```vb
Dim sampleObject as New SampleClass()
```

Po vytvoření instance třídy, můžete přiřadit hodnoty k vlastnosti a pole instance a vyvolání metody třídy.

```vb
' Set a property value.
sampleObject.SampleProperty = "Sample String"
' Call a method.
sampleObject.SampleMethod()
```

Chcete-li přiřadit hodnoty k vlastnosti během procesu vytváření instancí třídy, použijte inicializátory objektů:

```vb
Dim sampleObject = New SampleClass With
    {.FirstProperty = "A", .SecondProperty = "B"}
```

Další informace naleznete v tématu:

- [New – operátor](../../../visual-basic/language-reference/operators/new-operator.md)

- [Inicializátory objektů: Pojmenované a anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-initializers-named-and-anonymous-types.md)

###  <a name="Static"></a>Sdílené třídy a členové  
 Sdíleného člena třídy je vlastnost, postup nebo pole, které platí pro všechny instance třídy.  
  
 Chcete-li definovat sdíleného člena:  
  
```vb  
Class SampleClass  
    Public Shared SampleString As String = "Sample String"  
End Class  
```  
  
 Přístup sdíleného člena, použijte název třídy bez vytvoření objektu této třídy:  
  
```vb  
MsgBox(SampleClass.SampleString)  
```  
  
 Sdílené moduly v jazyce Visual Basic sdíleli pouze členy a nelze vytvořit instanci. Sdílení členové také přístup k vlastnosti nesdílené, pole a metody  
  
 Další informace naleznete v tématu:  
  
-   [Sdílené](../../../visual-basic/language-reference/modifiers/shared.md)  
  
-   [Module – příkaz](../../../visual-basic/language-reference/statements/module-statement.md)  
  
### <a name="anonymous-types"></a>Anonymní typy  
Anonymní typy umožňují vytvářet objekty bez nutnosti psaní definice třídy pro datový typ. Kompilátor místo, vygeneruje třídu pro vás. Třída nemá žádný použitelný název a obsahuje vlastnosti, které zadáte v deklarace objektu.

Chcete-li vytvořit instanci anonymního typu:

```vb
' sampleObject is an instance of a simple anonymous type.
Dim sampleObject =
    New With {Key .FirstProperty = "A", .SecondProperty = "B"}
```

Další informace najdete v tématu: [anonymní typy](../../../visual-basic/programming-guide/language-features/objects-and-classes/anonymous-types.md).

## <a name="inheritance"></a>Dědičnost
Dědičnost umožňuje vytvořit novou třídu, která opětovně používá rozšiřuje a mění chování, která je definována v jiné třídy. Je volána třídu, jejíž členové jsou děděné *základní třída*, a třídu, která dědí členů, se nazývá *odvozené třídy*. Ale všechny třídy v jazyce Visual Basic implicitně dědí z <xref:System.Object> třídu, která podporuje hierarchie tříd rozhraní .NET a poskytuje nižší úroveň služby pro všechny třídy.

> [!NOTE]
>  Visual Basic nepodporuje vícenásobná dědičnost. To znamená můžete zadat pouze jeden základní třídu pro odvozené třídy.

Chcete-li zdědit ze základní třídy:

```vb
Class DerivedClass
    Inherits BaseClass
End Class
```

Ve výchozím nastavení může být dědí všechny třídy. Však můžete určit, zda nesmí používat jako základní třída třídy, nebo vytvořte třídu, která lze použít jako základní třídy.

Chcete-li určit, že třídy nelze použít jako základní třída:

```vb
NotInheritable Class SampleClass
End Class
```

K určení, že třídy lze použít jako základní třída a nelze vytvořit instanci:

```vb
MustInherit Class BaseClass
End Class
```

Další informace naleznete v tématu:

- [Inherits – příkaz](../../../visual-basic/language-reference/statements/inherits-statement.md)

- [NotInheritable](../../../visual-basic/language-reference/modifiers/notinheritable.md)

- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)

### <a name="overriding-members"></a>Přepis členů
Ve výchozím nastavení odvozené třídy dědí všechny členy ze své základní třídy. Pokud chcete změnit chování zděděného členu, budete muset přepsat. To znamená můžete definovat nové implementace metoda, vlastnost nebo události v odvozené třídě.

Následující modifikátory je možné určit, jak jsou přepsaná vlastnosti a metody:

|Modifikátor jazyka Visual Basic|Definice|
|---------------------------|----------------|
|[Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)|Umožňuje člena třídy k přepsání v odvozené třídě.|
|[Přepsání](../../../visual-basic/language-reference/modifiers/overrides.md)|Přepsání člena virtuální (přepisovatelné) definované v základní třídě.|
|[NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)|Zabrání přepsání dědičných třídy členem.|
|[MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)|Vyžaduje, aby člena třídy k přepsání v odvozené třídě.|
|[Stínů](../../../visual-basic/language-reference/modifiers/shadows.md)|Skryje členem zděděn ze základní třídy|

## <a name="interfaces"></a>Rozhraní
Rozhraní, jako jsou třídy, definovat sadu vlastností, metod a události. Ale na rozdíl od třídy, rozhraní neposkytují implementace. Jsou implementované třídy a definován jako samostatné entity z tříd. Rozhraní představuje kontraktu, v tomto třídu, která implementuje rozhraní musí implementovat všechny aspekty tohoto rozhraní přesně tak, jak je definována.

Definice rozhraní:

```vb
Public Interface ISampleInterface
    Sub DoSomething()
End Interface
```

K implementaci rozhraní v třídě:

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

- [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md)  

- [Implements – příkaz](../../../visual-basic/language-reference/statements/implements-statement.md)  

## <a name="generics"></a>Obecné typy
Třídy, struktury, rozhraní a metody v rozhraní .NET může zahrnovat *parametry typu* , definování typů objektů, které lze uložit nebo použít. Nejčastější obecných typů je kolekce, kde můžete určit typ objektů, které chcete uložit v kolekci.  

Zadat obecné třídy:

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

Další informace naleznete v tématu:

- [Obecné typy](~/docs/standard/generics/index.md)

- [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)

## <a name="delegates"></a>Delegáty
 A *delegovat* je typ, který definuje podpis metody a může poskytnout odkaz na libovolnou metodu kompatibilní podpisem. Můžete vyvolat (nebo volání) metoda prostřednictvím delegáta. Delegáty se používají pro předávání metod jako argumentů jiným metodám.

> [!NOTE]
>  Ovladače událostí nejsou nic jiného než metody, které jsou vyvolány prostřednictvím delegátů. Další informace o použití delegátů při zpracování událostí najdete v tématu [události](../../../standard/events/index.md).

Pokud chcete vytvořit delegáta:

```vb
Delegate Sub SampleDelegate(ByVal str As String)
```

Pokud chcete vytvořit odkaz na metodu, která odpovídá podpis určeného delegát:

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

- [Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md)

- [AddressOf – operátor](../../../visual-basic/language-reference/operators/addressof-operator.md)

## <a name="see-also"></a>Viz také
 [Průvodce programováním v jazyce Visual Basic](../../../visual-basic/programming-guide/index.md)
