---
title: 'Postupy: Přístup k proměnné skryté odvozenou třídou (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: e840c83d7969eeb0322034f0f274fb19ca2b8e7e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54622842"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Postupy: Přístup k proměnné skryté odvozenou třídou (Visual Basic)
Když kód v odvozené třídě získá přístup k proměnné, obvykle přeloží kompilátor odkaz na nejbližší dostupné verzi, to znamená, že dostupné verze nejmíň derivational kroky zpětně ze třídy přístup. Pokud je proměnná definovaná v odvozené třídě, kód obvykle přistupuje k tuto definici.  
  
 Pokud proměnná odvozené třídy zastiňuje proměnná v základní třídě, skryje verze základní třídy. Však může přistupovat k proměnné základní třídy s kvalifikaci `MyBase` – klíčové slovo.  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Pro přístup k základní třídě proměnné skryté odvozenou třídou  
  
-   Ve výrazu nebo příkazu přiřazení, zadejte před název proměnné `MyBase` – klíčové slovo a tečku (`.`).  
  
     Přeloží kompilátor odkaz na verzi základní třídy proměnné.  
  
     Následující příklad ukazuje stínový provoz prostřednictvím dědičnosti. Umožňuje dva odkazy, ten, který přistupuje k stínového provozu proměnné a ten, který obchází stínováním.  
  
    ```  
    Public Class shadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class shadowDerivedClass  
        Inherits shadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub showStrings()  
            Dim s As String = "Unqualified shadowString: " & shadowString &  
                vbCrLf & "MyBase.shadowString: " & MyBase.shadowString  
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     Předchozí příklad deklaruje proměnnou `shadowString` v základní třídě a stíní v odvozené třídě. Postup `showStrings` v odvozené třídě Zobrazí verzi stínového provozu řetězce při název `shadowString` není kvalifikován. Potom zobrazí stínovaný verze při `shadowString` je kvalifikována `MyBase` – klíčové slovo.  
  
## <a name="robust-programming"></a>Robustní programování  
 Chcete-li snížit riziko odkazující na stínové proměnné a nežádoucí verzi, plně kvalifikovat všechny odkazy na stínové proměnné. Stínový provoz přináší více než jedna verze proměnné se stejným názvem. Když příkaz kódu odkazuje na název proměnné, verze, na který přeloží kompilátor odkaz na závisí na faktorech, jako je například umístění příkaz kódu a přítomnost oprávněným řetězec. To může zvýšit riziko odkazující na nesprávnou verzi proměnné.  
  
## <a name="see-also"></a>Viz také:
- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Stínění v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Rozdíly mezi stínováním a přepsáním](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Postupy: Skrytí zděděné proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
