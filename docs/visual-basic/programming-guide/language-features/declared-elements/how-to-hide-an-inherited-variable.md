---
title: 'Postupy: Skrytí zděděné proměnné'
ms.date: 07/20/2015
helpviewer_keywords:
- qualification [Visual Basic], of element names
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
- variables [Visual Basic], hiding inherited
ms.assetid: 765728d9-7351-4a30-999d-b5f34f024412
ms.openlocfilehash: c20c36b26c90c82da4e8836799f499498ccc40e4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345352"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>Postupy: Skrytí zděděné proměnné (Visual Basic)

Odvozená třída dědí všechny definice své základní třídy. Pokud chcete definovat proměnnou pomocí stejného názvu jako element základní třídy, můžete skrýt nebo vytvořit *stín*, který prvek základní třídy při definování proměnné v odvozené třídě. Pokud to uděláte, kód v odvozené třídě přistupuje k proměnné, pokud explicitně neobejde mechanismus stínování.

Dalším důvodem, proč je vhodné skrýt zděděnou proměnnou, je chránit před revizí základní třídy. Základní třída může podléhat změně, která mění prvek, který je děděn. Pokud k tomu dojde, modifikátor `Shadows` vynutí, aby byly odkazy z odvozené třídy přeloženy na vaši proměnnou namísto elementu základní třídy.

## <a name="to-hide-an-inherited-variable"></a>Skrytí zděděné proměnné

1. Ujistěte se, že proměnná, kterou chcete skrýt, je deklarována na úrovni třídy (mimo jakoukoliv proceduru). V opačném případě ji nemusíte skrývat.
  
2. V rámci odvozené třídy napište [příkaz Dim](../../../language-reference/statements/dim-statement.md) , který deklaruje vaši proměnnou. Použijte stejný název jako u zděděné proměnné.

3. Do deklarace zahrňte klíčové slovo [Shadows](../../../language-reference/modifiers/shadows.md) .

     Pokud kód v odvozené třídě odkazuje na název proměnné, kompilátor vyřeší odkaz na vaši proměnnou.

     Následující příklad znázorňuje stíny zděděné proměnné:
  
    ```vb  
    Public Class ShadowBaseClass  
        Public shadowString As String = "This is the base class string."  
    End Class  
    Public Class ShadowDerivedClass  
        Inherits ShadowBaseClass  
        Public Shadows shadowString As String = "This is the derived class string."  
        Public Sub ShowStrings()  
            Dim s As String = $"Unqualified shadowString: {shadowString}{vbCrLf}MyBase.shadowString: {MyBase.shadowString}"
            MsgBox(s)  
        End Sub  
    End Class  
    ```  
  
     Předchozí příklad deklaruje proměnnou `shadowString` v základní třídě a nastínuje ji v odvozené třídě. Procedura `ShowStrings` v odvozené třídě zobrazuje stínovou verzi řetězce, když název `shadowString` není kvalifikován. Když je `shadowString` kvalifikován pomocí klíčového slova `MyBase`, zobrazí se stínovaná verze.  
  
## <a name="robust-programming"></a>Robustní programování

Stíning zavádí více než jednu verzi proměnné se stejným názvem. Pokud příkaz kódu odkazuje na název proměnné, verze, na kterou kompilátor vyřeší odkaz, závisí na faktorech, jako je například umístění příkazu kódu a přítomnost opravňujícího řetězce. To může zvýšit riziko odkazování na neúmyslnou verzi stínové proměnné. Toto riziko můžete snížit tím, že plně zadáte všechny odkazy na stínovou proměnnou.

## <a name="see-also"></a>Viz také:

- [Odkazy na deklarované elementy](references-to-declared-elements.md)
- [Stínování v Visual Basic](shadowing.md)
- [Rozdíly mezi stínováním a přepsáním](differences-between-shadowing-and-overriding.md)
- [Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná](how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Postupy: Přístup k proměnné skryté odvozenou třídou](how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase a MyClass](../../program-structure/me-my-mybase-and-myclass.md)
- [Základní informace o dědičnosti](../objects-and-classes/inheritance-basics.md)
