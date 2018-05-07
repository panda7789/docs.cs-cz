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
ms.openlocfilehash: c59fdd8c6c6d2444b8d687c78c61f4e0d4bf9a52
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hide-an-inherited-variable-visual-basic"></a>Postupy: Skrytí zděděné proměnné (Visual Basic)
Odvozené třídy dědí všechny definice své základní třídy. Pokud chcete k definování proměnné pomocí stejný název jako element základní třídy, můžete skrýt, nebo *stínové*, základní třída prvku při definování vaše proměnná v odvozené třídě. Pokud to uděláte, kód v odvozené třídě přistupuje vaše proměnná, pokud ji explicitně obchází stínového provozu mechanismus.  
  
 Dalším důvodem, že chcete skrytí zděděné proměnné je k ochraně proti základní třída revize. Základní třída může ke změně, která mění na element, který se dědí. V takovém případě `Shadows` modifikátor vynutí odkazy z odvozené třídy vyřešen do proměnné, místo do elementu základní třídy.  
  
### <a name="to-hide-an-inherited-variable"></a>Skrytí zděděné proměnné  
  
1.  Ujistěte se, že je deklarovaná, které chcete skrýt proměnné na úrovni třídy (mimo jakéhokoli postupu). Jinak není potřeba ho skrýt.  
  
2.  V odvozené třídě, zápisu [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarace vaše proměnná. Použijte stejný název jako u zděděné proměnné.  
  
3.  Zahrnout [stínů](../../../../visual-basic/language-reference/modifiers/shadows.md) – klíčové slovo v deklaraci.  
  
     Když kód v odvozené třídě odkazuje na název proměnné, kompilátor vyřeší odkaz na vaše proměnná.  
  
     Následující příklad ilustruje, stínový provoz zděděné proměnné.  
  
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
  
     V předchozím příkladu deklaruje proměnnou `shadowString` v základní třídě a stín v odvozené třídě. Postup `showStrings` v odvozené třídě zobrazí stínového provozu verzi řetězec při název `shadowString` není kvalifikován. Potom zobrazí stíněné verze při `shadowString` je kvalifikovaný s `MyBase` – klíčové slovo.  
  
## <a name="robust-programming"></a>Robustní programování  
 Stínový provoz zavádí více než jedna verze proměnné se stejným názvem. Pokud příkaz kódu odkazuje na název proměnné, verze, do které kompilátor vyřeší odkaz závisí na faktorech, jako je například umístění příkaz kódu a přítomnost opravňující řetězec. To může zvýšit riziko napadení odkazující na nezamýšleným verzi stíněné proměnné. Plně kvalifikovaný všechny odkazy na proměnnou stíněné můžete snížit rizika.  
  
## <a name="see-also"></a>Viz také  
 [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Stínový provoz v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Rozdíly mezi stínováním a přepsáním](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Postupy: Přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
