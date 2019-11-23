---
title: Stínění v jazyce Visual Basic
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
ms.openlocfilehash: 30c02cf367c461c3896a01538d03380627de294f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004864"
---
# <a name="shadowing-in-visual-basic"></a>Stínění v jazyce Visual Basic
Pokud dva programovací prvky mají stejný název, jeden z nich může skrýt nebo *stín*, druhý. V takové situaci není pro referenci k dispozici stínovaný element; místo toho, když kód používá název elementu, kompilátor Visual Basic ho přeloží na stínový element.  
  
## <a name="purpose"></a>Účel  
 Hlavním účelem stínování je chránit definici členů vaší třídy. Základní třída se může podrobit změně, která vytvoří element se stejným názvem jako ten, který jste už definovali. Pokud k tomu dojde, modifikátor `Shadows` vynutí, aby byly odkazy prostřednictvím vaší třídy přeloženy na člen, který jste definovali, místo na nový prvek základní třídy.  
  
## <a name="types-of-shadowing"></a>Typy stínování  
 Element může stínovat jiný element dvěma různými způsoby. Stínový element lze deklarovat v dílčí oblasti oblasti obsahující stínový element. v takovém případě je vytváření stínů provedeno *prostřednictvím rozsahu*. Nebo odvozená třída může předefinovat člen základní třídy, v takovém případě se stín provádí *prostřednictvím dědičnosti*.  
  
### <a name="shadowing-through-scope"></a>Stínování přes rozsah  
 Je možné, že programovací prvky ve stejném modulu, třídě nebo struktuře mají stejný název, ale jiný obor. Pokud jsou v tomto způsobu deklarovány dva prvky a kód odkazuje na název, který sdílí, element s úzkým rozsahem stínů ostatních prvků (rozsah bloku je nejužší).  
  
 Modul může například definovat `Public` proměnnou s názvem `temp`a procedura v rámci modulu může deklarovat místní proměnnou také s názvem `temp`. Odkazy na `temp` v rámci procedury přistupují k místní proměnné, zatímco odkazy na `temp` z vně procedury přistupují k proměnné `Public`. V tomto případě proměnná procedury `temp` Stínová proměnná modulu `temp`.  
  
 Následující ilustrace znázorňuje dvě proměnné, s názvem `temp`. Místní proměnná `temp` stínovou proměnnou `temp` při použití z vlastní procedury `p`. Nicméně klíčové slovo `MyClass` obchází stín a přistupuje k členské proměnné.  
  
 ![Obrázek, který zobrazuje stínování v rozsahu.](./media/shadowing/shadow-scope-diagram.gif)
  
 Příklad vytváření stínového rozsahu naleznete v tématu [How to: Hide a proměnná se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Stínování prostřednictvím dědičnosti  
 Předefinuje-li odvozená třída programový prvek zděděný ze základní třídy, element redefine původní prvek nastínuje. Můžete vytvořit stín libovolného typu deklarovaného prvku nebo sadu přetížených prvků s jakýmkoli jiným typem. Například proměnná `Integer` může nastínovat `Function` postup. Pokud vytvoříte stínovou proceduru pomocí jiného postupu, můžete použít jiný seznam parametrů a jiný návratový typ.  
  
 Následující ilustrace znázorňuje základní třídu `b` a odvozenou třídu `d`, která dědí z `b`. Základní třída definuje proceduru s názvem `proc`a odvozenou třídou ji nastínuje s jiným postupem stejného názvu. První příkaz `Call` přistupuje ke stínovým `proc` v odvozené třídě. Nicméně klíčové slovo `MyBase` obchází stín a přistupuje k stínované proceduře v základní třídě.  
  
 ![Grafický diagram stínování prostřednictvím dědičnosti](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Příklad stínování prostřednictvím dědičnosti naleznete v tématu [How to: Hide a proměnná se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) a [Postupy: skrytí zděděné proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Stínová a přístupná úroveň  
 Element Shadow není vždy přístupný z kódu pomocí odvozené třídy. Může být například deklarován `Private`. V takovém případě je stínový postup připraven a kompilátor překládá všechny odkazy na stejný prvek, který by měl být v případě, že se nevytvořila žádná Stínová kopie. Tento prvek je přístupný prvek nejmenším odvozením kroků zpět od stínové třídy. Pokud je stínovaný element procedurou, je rozlišením nejbližší dostupné verze se stejným názvem, seznamem parametrů a návratovým typem.  
  
 Následující příklad ukazuje hierarchii dědičnosti tří tříd. Každá třída definuje proceduru `Sub` `display`a každá odvozená třída Stínuje `display` proceduru v její základní třídě.  
  
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
  
 V předchozím příkladu odvozená třída `secondClass` stíny `display` pomocí `Private` procedury. Když modul `callDisplay` volá `display` v `secondClass`, je volající kód mimo `secondClass` a proto nemůže získat přístup k privátnímu `display` postupu. Stíning je připraven a kompilátor překládá odkaz na základní třídu `display` proceduře.  
  
 Nicméně další odvozená třída `thirdClass` deklaruje `display` jako `Public`, takže kód v `callDisplay` k němu má přístup.  
  
## <a name="shadowing-and-overriding"></a>Stínování a přepsání  
 Nezaměňujte stíny s přepsáním. Obě jsou použity, když odvozená třída dědí ze základní třídy a obě předefinování jednoho deklarovaného elementu s jiným. Existují však významné rozdíly mezi těmito dvěma. Porovnání najdete v tématu [rozdíly mezi stínováním a přepsáním](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Nastínování a přetížení  
 Pokud vytvoříte stín stejného prvku základní třídy s více než jedním prvkem v odvozené třídě, stínové prvky se stanou přetíženými verzemi tohoto prvku. Další informace najdete v tématu [přetížení procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Přístup k Stínovanému elementu  
 Při přístupu k elementu z odvozené třídy to obvykle provedete prostřednictvím aktuální instance této odvozené třídy – kvalifikováním názvu elementu s klíčovým slovem `Me`. Pokud je vaše odvozená třída stínem elementu v základní třídě, můžete přistupovat k elementu základní třídy tím, že ho zařadíte pomocí klíčového slova `MyBase`.  
  
 Příklad přístupu ke stínovým elementům naleznete v tématu [How to: Access a Hidden a Derived by odvozené třídy](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Deklarace objektové proměnné  
 Způsob, jakým vytvoříte proměnnou objektu, může také ovlivnit, zda odvozená třída přistupuje ke stínovým elementům nebo k stínovanému elementu. Následující příklad vytvoří dva objekty z odvozené třídy, ale jeden objekt je deklarován jako základní třída a druhý jako odvozená třída.  
  
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
  
 V předchozím příkladu je proměnná `basObj` deklarována jako základní třída. Přiřazení objektu `dervCls` představuje rozšiřující převod, který je proto platný. Základní třída však nemůže získat přístup k stínové verzi proměnné `z` v odvozené třídě, takže Kompilátor přeloží `basObj.z` na původní hodnotu základní třídy.  
  
## <a name="see-also"></a>Viz také:

- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Obor v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
