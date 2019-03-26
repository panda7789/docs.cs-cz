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
ms.openlocfilehash: 15c7112f7e318542859162655c78e19558178e5a
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58411002"
---
# <a name="shadowing-in-visual-basic"></a>Stínění v jazyce Visual Basic
Když dva programovací prvky sdílí se stejným názvem, jeden z nich můžete skrýt, nebo *stínové*, druhou. V takové situaci stínovaný prvek není k dispozici pro referenci; Místo toho se při váš kód používá název elementu, kompilátor jazyka Visual Basic se přeloží na elementu stínového provozu.  
  
## <a name="purpose"></a>Účel  
 Stínový provoz hlavním účelem je chránit definice členů třídy. Základní třídy může být změnu, která vytvoří element se stejným názvem jako ten, který je již definován. Pokud k tomu dojde, `Shadows` modifikátor vynutí odkazuje prostřednictvím vaší třídy, které je potřeba vyřešit členovi definované, namísto nový prvek základní třídy.  
  
## <a name="types-of-shadowing"></a>Typy stínování  
 Element můžete stínové jiný element dvěma různými způsoby. Element stínového provozu mohou být deklarovány uvnitř podoblasti oblasti obsahující stínovaný element, ve kterém se provádí případ, stínováním *prostřednictvím oboru*. Nebo odvozená třída může předefinovat člena základní třídy, ve kterém se provádí případ, stínováním *prostřednictvím dědičnosti*.  
  
### <a name="shadowing-through-scope"></a>Stínový provoz prostřednictvím oboru  
 Je možné pro vaše programovací prvky ve stejném modulu, třídy nebo struktury mají stejný název, ale jiného oboru. Když kód odkazuje na název sdílejí tímto způsobem jsou deklarovány dva prvky, element s oborem užší zastiňuje jiného elementu (rozsah bloku je nejbližší).  
  
 Například můžete definovat modulu `Public` proměnnou s názvem `temp`, a postup v rámci modulu lze deklarovat lokální proměnná i s názvem `temp`. Odkazy na `temp` v rámci postupu přístup k místní proměnné při odkazy na `temp` z mimo řízení přístupu `Public` proměnné. V takovém případě proměnnou postup `temp` zastiňuje proměnná modulu `temp`.  
  
 Následující obrázek znázorňuje dvě proměnné, oba s názvem `temp`. Lokální proměnná `temp` zastiňuje členskou proměnnou `temp` při přístupu z v rámci své vlastní procedury `p`. Ale `MyClass` – klíčové slovo stínový provoz obchází a přistupuje k členské proměnné.  
  
 ![Obrázek znázorňující, stínování prostřednictvím oboru.](./media/shadowing/shadow-scope-diagram.gif)
  
 Příklad stínování prostřednictvím oboru, naleznete v tématu [jak: Skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md).  
  
### <a name="shadowing-through-inheritance"></a>Stínový provoz prostřednictvím dědičnosti  
 Pokud odvozené třídy předefinuje programovací element zděděné ze základní třídy, prvku redefining zastiňuje původní elementu. Jakýkoli element deklarovaný typ nebo sadu přetížených elementů můžete stínové s žádným jiným typem. Například `Integer` můžete stínové proměnné `Function` postup. Pokud jste stínové procedury s jinou proceduru, můžete použít seznam různých parametrů a jiným návratovým typem.  
  
 Následující obrázek ukazuje základní třídu `b` a odvozená třída `d` , která dědí z `b`. Základní třída definuje proceduru s názvem `proc`, a odvozená třída zastiňuje ho pomocí jiné proceduře se stejným názvem. První `Call` příkaz přistupuje stínováním `proc` v odvozené třídě. Ale `MyBase` – klíčové slovo stínový provoz obchází a budou k dispozici stínovaný postup v základní třídě.  
  
 ![Grafický diagram stínový provoz prostřednictvím dědičnosti](./media/shadowing/shadowing-inherit-diagram.gif)  
  
 Příklad stínový provoz prostřednictvím dědičnosti, naleznete v tématu [jak: Skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md) a [jak: Skrytí zděděné proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md).  
  
#### <a name="shadowing-and-access-level"></a>Stínový provoz a úroveň přístupu  
 Element stínového provozu vždy není přístupné z kódu pomocí odvozené třídy. Například může být deklarován `Private`. V takovém případě stínováním není zrušena a přeloží kompilátor všechny odkazy na stejný prvek by měl mít pokud byla žádné stínováním. Tento prvek je přístupný prvek derivational nejmenším počtem kroků zpět ze třídy stínového provozu. Postup při stínovaný element řešení je nejbližší dostupné verze se stejným názvem, seznam parametrů a návratový typ.  
  
 Následující příklad ukazuje tři třídy hierarchie dědičnosti. Každá třída definuje `Sub` postup `display`, a každý odvozené třídy stínů `display` postup v její základní třídě.  
  
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
  
 V předchozím příkladu, odvozené třídy `secondClass` stíny `display` s `Private` postup. Pokud modul `callDisplay` volání `display` v `secondClass`, volající kód je mimo `secondClass` a proto nemůže přistupovat k privátní `display` postup. Stínový provoz není zrušena a přeloží kompilátor odkaz na základní třídu `display` postup.  
  
 Však další odvozené třídy `thirdClass` deklaruje `display` jako `Public`, takže kód v `callDisplay` k němu máte přístup.  
  
## <a name="shadowing-and-overriding"></a>Stínováním a přepsáním  
 Nepleťte si stínový provoz pomocí přepsání. Jak se používají při odvozená třída dědí ze základní třídy, a obě znovu definovat jeden element deklarovaný s jiným. Ale existují významné rozdíly mezi nimi. Porovnání najdete v tématu [rozdíly mezi stínováním a přepíše](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md).  
  
## <a name="shadowing-and-overloading"></a>Stínový provoz a přetížení  
 Pokud stínové prvek základní třídy s více než jeden prvek v odvozené třídě, stanou se stínového provozu prvky přetížené verze daného prvku. Další informace najdete v tématu [přetížení procedury](../../../../visual-basic/programming-guide/language-features/procedures/procedure-overloading.md).  
  
## <a name="accessing-a-shadowed-element"></a>Přístup k prvku stínovaný  
 Při přístupu k elementu z odvozené třídy, obvykle tak učiníte prostřednictvím aktuální instanci odvozené třídy, kvalifikaci pomocí názvu elementu `Me` – klíčové slovo. Pokud odvozené třídy zastiňuje elementu v základní třídě, dostanete základní třída prvku kvalifikaci s `MyBase` – klíčové slovo.  
  
 Příklad přístup k prvku stínovaný, naleznete v tématu [jak: Přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md).  
  
### <a name="declaration-of-the-object-variable"></a>Deklarace proměnné objektu  
 Jak vytvořit objektové proměnné může ovlivnit také, zda stínového provozu element nebo element stínovaný přistupuje k odvozené třídě. Následující příklad vytvoří dva objekty z odvozené třídy, ale jeden objekt je deklarován jako základní třídu a druhá jako odvozené třídy.  
  
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
  
 V předchozím příkladu je proměnná `basObj` je deklarován jako základní třídy. Přiřazení `dervCls` objektu představuje rozšiřující převod a proto je platná. Však základní třídy nedaří stínového provozu verze proměnné `z` v odvozené třídě, takže přeloží kompilátor `basObj.z` na původní hodnotu základní třídy.  
  
## <a name="see-also"></a>Viz také:
- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Obor v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
