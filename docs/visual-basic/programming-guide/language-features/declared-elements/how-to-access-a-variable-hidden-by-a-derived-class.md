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
ms.openlocfilehash: c5ff802a0f6e081acd00d7cdfab4a8296b4daad9
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392854"
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Postupy: Přístup k proměnné skryté odvozenou třídou (Visual Basic)

Když kód v odvozené třídě přistupuje k proměnné, kompilátor obvykle vyřeší odkaz na nejbližší dostupnou verzi, to znamená, že dostupná verze je nejmenší odvozený postup zpět od třídy přístupu. Pokud je proměnná definována v odvozené třídě, kód obvykle přistupuje k této definici.

Pokud proměnná odvozené třídy Stínuje proměnnou v základní třídě, skryje verzi základní třídy. K proměnné základní třídy ale můžete přistupovat tak, že ji zařadíte pomocí `MyBase` klíčového slova.

### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Přístup k proměnné základní třídy skryté odvozenou třídou

- V příkazu výrazu nebo přiřazení uveďte před názvem proměnné `MyBase` klíčové slovo a tečku ( `.` ).

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

    Předchozí příklad deklaruje proměnnou `shadowString` v základní třídě a nastínuje ji v odvozené třídě. Procedura `showStrings` v odvozené třídě zobrazuje stínovou verzi řetězce, pokud název není `shadowString` kvalifikován. Pak zobrazí stínovou verzi, pokud `shadowString` je kvalifikován pomocí `MyBase` klíčového slova.

## <a name="robust-programming"></a>Robustní programování

Chcete-li snížit riziko odkazování na neúmyslnou verzi stínové proměnné, můžete plně kvalifikovat všechny odkazy na stínovou proměnnou. Stíning zavádí více než jednu verzi proměnné se stejným názvem. Pokud příkaz kódu odkazuje na název proměnné, verze, na kterou kompilátor vyřeší odkaz, závisí na faktorech, jako je například umístění příkazu kódu a přítomnost opravňujícího řetězce. To může zvýšit riziko odkazování na nesprávnou verzi proměnné.

## <a name="see-also"></a>Viz také

- [Odkazy na deklarované elementy](references-to-declared-elements.md)
- [Stínění v jazyce Visual Basic](shadowing.md)
- [Rozdíly mezi stínováním a přepsáním](differences-between-shadowing-and-overriding.md)
- [Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Postupy: Skrytí zděděné proměnné](how-to-hide-an-inherited-variable.md)
- [Shadows](../../../language-reference/modifiers/shadows.md)
- [Přepsání](../../../language-reference/modifiers/overrides.md)
- [Me, My, MyBase a MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [Základní informace o dědičnosti](../objects-and-classes/inheritance-basics.md)
