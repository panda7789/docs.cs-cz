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
ms.openlocfilehash: fde6259b67a8d963ed8c30b87c94029fb2658664
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="shadowing-in-visual-basic"></a>Stínění v jazyce Visual Basic
Když dva programovací elementy sdílet stejný název, jednu z nich můžete skrýt, nebo *stínové*, jiný. V takové situaci stíněné element není k dispozici pro referenci; Místo toho že pokud váš kód používá název elementu, Visual Basic – kompilátor ho přeloží na stínového provozu elementu.  
  
## <a name="purpose"></a>Účel  
 Hlavním účelem stínový provoz je k ochraně definici členy vaší třídy. Základní třída může podstoupit změnu, která vytvoří element se stejným názvem jako jeden, který je již definován. V takovém případě `Shadows` modifikátor vynutí odkazuje prostřednictvím vaší třídy přeloží na člen definované, místo do nového elementu základní třídy.  
  
## <a name="types-of-shadowing"></a>Typy stínováním  
 Element můžete stínové jiný element dvěma různými způsoby. Element stínového provozu může být deklarována uvnitř podoblasti oblasti obsahující stíněné elementu, ve kterém se provádí stínový provoz – případ *prostřednictvím oboru*. Nebo odvozující třídě lze znovu definovat členem základní třídu, ve kterém se provádí stínový provoz – případ *prostřednictvím dědičnosti*.  
  
### <a name="shadowing-through-scope"></a>Stínový provoz prostřednictvím oboru  
 Je možné pro programování elementů ve stejném modulu, třídu nebo strukturu, do mají stejný název, ale jiný rozsah. Pokud jsou dva elementy deklarované tímto způsobem a kód odkazuje na název sdílejí, element s oboru užší shadows jiného elementu (je nejbližší rozsah bloku).  
  
 Například můžete definovat modul `Public` proměnné s názvem `temp`, a postupu v modulu můžou deklarovat místní proměnné také s názvem `temp`. Odkazuje na `temp` uvnitř postup přístup k místní proměnné, při odkazy na `temp` z mimo přístup procedur `Public` proměnné. V tomto případě proměnnou postup `temp` shadows proměnnou modulu `temp`.  
  
 Následující obrázek znázorňuje dvě proměnné, jak s názvem `temp`. Místní proměnná `temp` shadows členské proměnné `temp` přistupováno z v rámci vlastní procedury `p`. Ale `MyClass` – klíčové slovo stínový provoz obchází a přistupuje k členské proměnné.  
  
 ![Grafický diagram stínování prostřednictvím oboru](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowscope.gif "ShadowScope")  
Stínový provoz prostřednictvím oboru  
  
 Příklad stínování prostřednictvím rozsahu, naleznete v části [postupy: skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Stínový provoz prostřednictvím dědičnosti  
 Pokud odvozené třídy znovu definuje programovací element zděděn ze základní třídy, stín redefining element původní elementu. Žádný druh deklarovaný element nebo sadu přetížené elementů můžete stínové s žádným jiným typem. Například `Integer` můžete stínové proměnné `Function` postupu. Pokud jste stínové procedury s jinou proceduru, můžete seznam různých parametrů a jiné návratový typ.  
  
 Následující obrázek ukazuje základní třídu `b` a odvozená třída `d` který dědí z `b`. Definuje základní třídu s názvem procedury `proc`, a odvozené třídy jej shadows s jinou proceduru se stejným názvem. První `Call` příkaz přistupuje stínováním `proc` v odvozené třídě. Ale `MyBase` – klíčové slovo stínový provoz obchází a přistupuje k procesu stíněné v základní třídě.  
  
 ![Grafický diagram stínování prostřednictvím dědičnosti](../../../../visual-basic/programming-guide/language-features/declared-elements/media/shadowinherit.gif "ShadowInherit")  
Stínový provoz prostřednictvím dědičnosti  
  
 Příklad stínování prostřednictvím dědičnosti, naleznete v části [postupy: skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) a [postupy: skrytí zděděné proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Stínový provoz a úroveň přístupu  
 Element stínového provozu není vždy přístupné z kódu pomocí odvozené třídy. Například může deklarovat `Private`. V takovém případě stínový provoz je nepotlačí a kompilátor vyřeší všechny odkazy na stejný element by měla mít pokud by došlo bez stínový provoz. Tento element je přístupný element nejmenším počtem derivational kroky zpátky ze třídy stínového provozu. Pokud element stíněné procedury, řešení je na nejbližší dostupný verzi se stejným názvem, seznam parametrů a návratovým typem.  
  
 Následující příklad ukazuje hierarchie dědičnosti tří tříd. Každá třída definuje `Sub` postup `display`, a všechny odvozené třídy stínů `display` postup v její základní třída.  
  
```  
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
  
 V předchozím příkladu, odvozené třídy `secondClass` stínů `display` s `Private` postupu. Pokud modul `callDisplay` volání `display` v `secondClass`, volající kód je mimo `secondClass` a proto nemá přístup k privátní `display` postupu. Stínový provoz je nepotlačí a kompilátor přeloží odkaz na základní třídu `display` postupu.  
  
 Další však odvozené třídy `thirdClass` deklaruje `display` jako `Public`, takže kód v `callDisplay` k němu přístup.  
  
## <a name="shadowing-and-overriding"></a>Stínováním a přepsáním  
 Nezaměňujte stínový provoz s přepsání. Jak se používají při odvozené třídy dědí vlastnosti ze základní třídy a obě znovu definovat jeden deklarovaný element s jinou. Ale existují významné rozdíly mezi nimi. Porovnání najdete v tématu [rozdíly mezi stínováním a přepíše](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Stínový provoz a přetížení  
 Pokud jste v odvozené třídě stínové stejnou základní třídu element s více než jeden element, stanou se stínového provozu elementy přetížené verzích tohoto prvku. Další informace najdete v tématu [přetížení procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Přístup k stíněné Element  
 Při přístupu k elementu z odvozené třídy, je obvykle k tomu prostřednictvím aktuální instancí třídy odvozené třídy, kvalifikující název elementu s `Me` – klíčové slovo. Pokud odvozené třídy shadows element v základní třídě, dostanete prvku základní třídy kvalifikováním její `MyBase` – klíčové slovo.  
  
 Příklad přístup k prvku stíněné, naleznete v části [postupy: přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Deklarace proměnné objektu  
 Jak vytvořit proměnné objektu může ovlivnit také zda stínového provozu element nebo element stíněné přistupuje k odvozené třídy. Následující příklad vytvoří dva objekty z odvozené třídy, ale jeden objekt je deklarován jako základní třídy a další jako odvozené třídy.  
  
```  
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
  
 V předchozím příkladu, proměnná `basObj` je deklarován jako základní třídy. Přiřazení `dervCls` objektu k němu rozšiřující převod se považuje za a je proto platný. Základní třída však nelze přístup stínového provozu verzi proměnnou `z` v odvozené třídě, takže kompilátor přeloží `basObj.z` na původní hodnotu základní třídy.  
  
## <a name="see-also"></a>Viz také  
 [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Rozsah v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)  
 [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
