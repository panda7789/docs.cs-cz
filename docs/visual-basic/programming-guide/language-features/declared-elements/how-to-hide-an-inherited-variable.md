---
title: 'Postupy: Skrytí zděděné proměnné (Visual Basic)'
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
ms.openlocfilehash: ee147ecd00b88b538ace32844c42ac9c5022b2ef
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61794690"
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>Postupy: Skrytí zděděné proměnné (Visual Basic)
Odvozené třídy dědí všechny definice své základní třídy. Pokud chcete k definování proměnné pomocí stejného názvu jako prvek základní třídy, můžete skrýt, nebo *stínové*, základní třída prvku při definování proměnné v odvozené třídě. Pokud to uděláte, kód v odvozené třídě přistupuje ke vaše proměnná, pokud explicitně obchází mechanismu stínového provozu.  
  
 Dalším důvodem, že kdy je vhodné pro skrytí zděděné proměnné je ochrana proti revizi základních tříd. Základní třídy, může být ke změně, která mění prvek, na který se dědí. Pokud se to stane, `Shadows` modifikátor vynutí odkazy z odvozené třídy, které chcete přeložit na proměnnou, místo na prvek základní třídy.  
  
### <a name="to-hide-an-inherited-variable"></a>Chcete-li skrytí zděděné proměnné  
  
1. Ujistěte se, že je deklarována, které chcete skrýt proměnné na úrovni třídy (mimo všechny procedury). V opačném případě není potřeba skryli.  
  
2. Uvnitř vaší odvozené třídě, zápisu [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarování proměnné. Použijte stejný název jako zděděné proměnné.  
  
3. Zahrnout [stíny](../../../../visual-basic/language-reference/modifiers/shadows.md) – klíčové slovo v deklaraci.  
  
     Když kód v odvozené třídě odkazuje na název proměnné, přeloží kompilátor odkaz na vaše proměnná.  
  
     Následující příklad ukazuje stínováním zděděné proměnné.  
  
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
 Stínový provoz přináší více než jedna verze proměnné se stejným názvem. Když příkaz kódu odkazuje na název proměnné, verze, na který přeloží kompilátor odkaz na závisí na faktorech, jako je například umístění příkaz kódu a přítomnost oprávněným řetězec. To může zvýšit riziko odkazující na stínové proměnné a nežádoucí verzi. Plně kvalifikovaný všechny odkazy na stínové proměnné můžete snížit rizika.  
  
## <a name="see-also"></a>Viz také:

- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Stínění v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Rozdíly mezi stínováním a přepsáním](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)
- [Postupy: Přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
