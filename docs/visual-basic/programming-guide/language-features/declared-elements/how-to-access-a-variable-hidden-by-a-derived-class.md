---
title: 'Postupy: Přístup k proměnné skryté odvozenou třídou'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
ms.openlocfilehash: 276cb1411c66e1f7205507a1b1053cc8642c7cb0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345397"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Postupy: Přístup k proměnné skryté odvozenou třídou (Visual Basic)

Když kód v odvozené třídě přistupuje k proměnné, kompilátor obvykle vyřeší odkaz na nejbližší dostupnou verzi, to znamená, že dostupná verze je nejmenší odvozený postup zpět od třídy přístupu. Pokud je proměnná definována v odvozené třídě, kód obvykle přistupuje k této definici.

Pokud proměnná odvozené třídy Stínuje proměnnou v základní třídě, skryje verzi základní třídy. K proměnné základní třídy ale můžete přistupovat tak, že ji zařadíte pomocí klíčového slova `MyBase`.

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Přístup k proměnné základní třídy skryté odvozenou třídou

- V příkazu výrazu nebo přiřazení před název proměnné s klíčovým slovem `MyBase` a periodou (`.`).

    Kompilátor vyřeší odkaz na verzi základní třídy proměnné.

    Následující příklad znázorňuje stínování prostřednictvím dědičnosti. Vytvoří dva odkazy, jeden, který přistupuje ke stínové proměnné a druhý, který obchází stín.

    ```vb
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

    Předchozí příklad deklaruje proměnnou `shadowString` v základní třídě a nastínuje ji v odvozené třídě. Procedura `showStrings` v odvozené třídě zobrazuje stínovou verzi řetězce, když název `shadowString` není kvalifikován. Když je `shadowString` kvalifikován pomocí klíčového slova `MyBase`, zobrazí se stínovaná verze.

## <a name="robust-programming"></a>Robustní programování

Chcete-li snížit riziko odkazování na neúmyslnou verzi stínové proměnné, můžete plně kvalifikovat všechny odkazy na stínovou proměnnou. Stíning zavádí více než jednu verzi proměnné se stejným názvem. Pokud příkaz kódu odkazuje na název proměnné, verze, na kterou kompilátor vyřeší odkaz, závisí na faktorech, jako je například umístění příkazu kódu a přítomnost opravňujícího řetězce. To může zvýšit riziko odkazování na nesprávnou verzi proměnné.

## <a name="see-also"></a>Viz také:

- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Stínování v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Rozdíly mezi stínováním a přepsáním](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Postupy: Skrytí zděděné proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Shadows](../../../../visual-basic/language-reference/modifiers/shadows.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
