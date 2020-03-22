---
title: Stínování
ms.date: 07/20/2015
helpviewer_keywords:
- inheritance [Visual Basic], shadowing
- overriding, and shadowing
- shadowing
- duplicate names [Visual Basic]
- shadowing, by inheritance
- declared elements [Visual Basic], referencing
- shadowing, by scope
- declared elements [Visual Basic], hiding
- naming conflicts, shadowing
- declared elements [Visual Basic], shadowing
- shadowing, and overriding
- scope [Visual Basic], shadowing
- Shadows keyword [Visual Basic], about
- objects [Visual Basic], names
- names [Visual Basic], shadowing
ms.assetid: 54bb4c25-12c4-4181-b4a0-93546053964e
ms.openlocfilehash: 20a33478f622fca6d3183772f53dcb3e72f79409
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/04/2020
ms.locfileid: "78266882"
---
# <a name="shadowing-in-visual-basic"></a>Stínění v jazyce Visual Basic
Pokud dva programovací prvky sdílejí stejný název, jeden z nich může skrýt nebo *stín*, druhý. V takové situaci stínovaný prvek není k dispozici pro referenci; místo toho při kódu používá název prvku, kompilátor jazyka jej přeloží na prvek stínování.  
  
## <a name="purpose"></a>Účel  
 Hlavním účelem stínových stínových stínů je chránit definici členů třídy. Základní třída může podstoupit změnu, která vytvoří prvek se stejným názvem jako ten, který jste již definovali. Pokud k tomu `Shadows` dojde, modifikátor vynutí odkazy prostřednictvím třídy, které mají být vyřešeny na člen, který jste definovali, namísto nového elementu základní třídy.  
  
## <a name="types-of-shadowing"></a>Typy stínových stínových objektů  
 Prvek může stínovat jiný prvek dvěma různými způsoby. Prvek stínování lze deklarovat uvnitř podoblasti oblasti obsahující stínový prvek, v takovém případě je stínování provedeno *prostřednictvím oboru*. Nebo odvozené třídy můžete předefinovat člen základní třídy, v takovém případě stínový provoz provádí *prostřednictvím dědičnosti*.  
  
### <a name="shadowing-through-scope"></a>Stínový provoz prostřednictvím oboru  
 Je možné, že programovací prvky ve stejném modulu, třídy nebo struktury mají stejný název, ale jiný obor. Když dva prvky jsou deklarovány tímto způsobem a kód odkazuje na název, který sdílejí, prvek s užší mašle stíny další prvek (blok obor je nejužší).  
  
 Modul může například definovat `Public` proměnnou s názvem `temp`a postup v rámci `temp`modulu může deklarovat místní proměnnou také pojmenovanou . Odkazy na `temp` z v rámci postupu přístup k `temp` místní proměnné, zatímco `Public` odkazy na mimo postup přístup proměnné. V tomto případě proměnná `temp` procedura `temp`stíny proměnné modulu .  
  
 Následující obrázek znázorňuje dvě `temp`proměnné, obě s názvem . Místní proměnná `temp` stíny `temp` členské proměnné při přístupu `p`z vlastní postup . `MyClass` Klíčové slovo však obchází stínování a přistupuje k členské proměnné.  
  
 ![Grafika, která zobrazuje stínování v oboru.](./media/shadowing/shadow-scope-diagram.gif)
  
 Příklad stínování v oboru najdete v [tématu Jak: Skrýt proměnnou se stejným názvem jako proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Stínování prostřednictvím dědičnosti  
 Pokud odvozená třída předefinuje programovací prvek zděděný ze základní třídy, předefinování element stíny původní prvek. Můžete stín ovat libovolný typ deklarovaného prvku nebo sadu přetížených prvků s jiným typem. Proměnná `Integer` může například `Function` stínovat proceduru. Pokud stín postup s jiným postupem, můžete použít jiný seznam parametrů a jiný návratový typ.  
  
 Následující obrázek znázorňuje základní třídu `b` a odvozenou třídu, `d` která dědí z `b`. Základní třída definuje proceduru `proc`s názvem a odvozená třída ji stíní jiným postupem se stejným názvem. První `Call` příkaz přistupuje k stínování `proc` v odvozené třídě. `MyBase` Klíčové slovo však obchází stínování a přistupuje k stínované procedury v základní třídě.  
  
 ![Grafický diagram stínování prostřednictvím dědičnosti](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Příklad stínování prostřednictvím dědičnosti najdete v [tématu Jak: Skrýt proměnnou se stejným názvem jako proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) a [Jak skrýt zděděnou proměnnou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Stínování a úroveň přístupu  
 Prvek stínování není vždy přístupný z kódu pomocí odvozené třídy. Může být například `Private`deklarována . V takovém případě je stínování poraženo a kompilátor vyřeší jakýkoli odkaz na stejný prvek, který by měl, kdyby nedošlo k žádnému stínový provoz. Tento prvek je přístupný prvek nejmenší odvozenické kroky zpět od třídy stínování. Pokud stínovaný prvek je procedura, rozlišení je nejbližší přístupné verze se stejným názvem, seznam parametrů a návratový typ.  
  
 Následující příklad ukazuje hierarchii dědičnosti tří tříd. Každá třída definuje `Sub` `display`proceduru a každá odvozená `display` třída stíny postup v jeho základní třídy.  
  
```vb  
Public Class firstClass  
    Public Sub display()  
        MsgBox("This is firstClass")  
    End Sub  
End Class  
Public Class secondClass  
    Inherits firstClass  
    Private Shadows Sub display()  
        MsgBox("This is secondClass")  
    End Sub  
End Class  
Public Class thirdClass  
    Inherits secondClass  
    Public Shadows Sub display()  
        MsgBox("This is thirdClass")  
    End Sub  
End Class  
Module callDisplay  
    Dim first As New firstClass  
    Dim second As New secondClass  
    Dim third As New thirdClass  
    Public Sub callDisplayProcedures()  
        ' The following statement displays "This is firstClass".  
        first.display()  
        ' The following statement displays "This is firstClass".  
        second.display()  
        ' The following statement displays "This is thirdClass".  
        third.display()  
    End Sub  
End Module  
```  
  
 V předchozím příkladu jsou odvozené `display` třídy `Private` `secondClass` stíny s procedurou. Při `callDisplay` volání `display` `secondClass`modulu je volající `secondClass` kód mimo a `display` proto nemůže získat přístup k privátní procedurě. Stínový provoz je poražen a kompilátor řeší odkaz `display` na proceduru základní třídy.  
  
 Další odvozené třídy `thirdClass` však deklaruje `display` jako `Public`, takže kód v aplikaci `callDisplay` přístup.  
  
## <a name="shadowing-and-overriding"></a>Stínování a přepsání  
 Nezaměňujte stínování s přepsáním. Oba se používají, když odvozené třídy dědí ze základní třídy a oba předefinovat jeden deklarovaný prvek s jiným. Ale existují významné rozdíly mezi těmito dvěma. Porovnání naleznete v tématu [Rozdíly mezi stínovým a přepsáním](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Stínování a přetížení  
 Pokud stín stejný element základní třídy s více než jeden prvek v odvozené třídy, stínování prvky stanou přetížené verze tohoto prvku. Další informace naleznete [v tématu Přetížení procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Přístup k prvku stínového stínu  
 Při přístupu k prvku z odvozené třídy, obvykle tak provedete prostřednictvím aktuální instance této `Me` odvozené třídy tím, že kvalifikuje název prvku s klíčovým slovem. Pokud vaše odvozené třídy stíny prvek v základní třídě, můžete získat přístup `MyBase` k elementu základní třídy kvalifikující se s klíčovým slovem.  
  
 Příklad přístupu k stínovému prvku naleznete v tématu [How to: Access a Variable Hidden by a Derived Class](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Deklarace proměnné objektu  
 Způsob vytvoření proměnné objektu může také ovlivnit, zda odvozená třída přistupuje k prvku stínování nebo stínovému prvku. Následující příklad vytvoří dva objekty z odvozené třídy, ale jeden objekt je deklarován jako základní třída a druhý jako odvozená třída.  
  
```vb  
Public Class baseCls  
    ' The following statement declares the element that is to be shadowed.  
    Public z As Integer = 100  
End Class  
Public Class dervCls  
    Inherits baseCls  
    ' The following statement declares the shadowing element.  
    Public Shadows z As String = "*"  
End Class  
Public Class useClasses  
    ' The following statement creates the object declared as the base class.  
    Dim basObj As baseCls = New dervCls()  
    ' Note that dervCls widens to its base class baseCls.  
    ' The following statement creates the object declared as the derived class.  
    Dim derObj As dervCls = New dervCls()  
    Public Sub showZ()
    ' The following statement outputs 100 (the shadowed element).  
        MsgBox("Accessed through base class: " & basObj.z)  
    ' The following statement outputs "*" (the shadowing element).  
        MsgBox("Accessed through derived class: " & derObj.z)  
    End Sub  
End Class  
```  
  
 V předchozím příkladu je `basObj` proměnná deklarována jako základní třída. Přiřazení objektu `dervCls` k němu představuje rozšiřující převod a je proto platný. Základní třída však nemůže získat přístup k `z` verzi stínového vysílání proměnné v `basObj.z` odvozené třídě, takže kompilátor se překládá na původní hodnotu základní třídy.  
  
## <a name="see-also"></a>Viz také

- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Rozsah v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
