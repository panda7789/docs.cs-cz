---
title: "Postupy: Přístup k proměnné skryté odvozenou třídou (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- qualification [Visual Basic], of element names
- base classes [Visual Basic], accessing elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declared elements [Visual Basic], referencing
- variables [Visual Basic], accessing hidden
ms.assetid: ae21a8ac-9cd4-4fba-a3ec-ecc4321ef93c
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0f94e45fcb0a26b0d59789e101c37aceba219250
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-a-variable-hidden-by-a-derived-class-visual-basic"></a>Postupy: Přístup k proměnné skryté odvozenou třídou (Visual Basic)
Když kód v odvozené třídě získá přístup k proměnné, kompilátor normálně přeloží odkaz na nejbližší dostupné verze, který je přístupný verze nejmenšího derivational kroky zpětné z přístupu k třídě. Pokud je proměnná definovaná v odvozené třídě, kód normálně přistupuje k této definici.  
  
 Pokud proměnná odvozené třídy shadows proměnné v základní třídě, skryje verze základní třídy. Ale mají přístup k proměnné základní třída kvalifikováním její `MyBase` – klíčové slovo.  
  
### <a name="to-access-a-base-class-variable-hidden-by-a-derived-class"></a>Pro přístup k základní třída proměnné skryté odvozenou třídou  
  
-   Ve výrazu nebo příkazu přiřazení, zadejte před název proměnné `MyBase` – klíčové slovo a období (`.`).  
  
     Kompilátor vyřeší odkaz na základní třída verzi proměnnou.  
  
     Následující příklad ilustruje, stínový provoz prostřednictvím dědičnosti. Umožňuje dva odkazy, ten, který přistupuje k proměnnou stínového provozu a ten, který obchází stínový provoz.  
  
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
 Chcete-li snížit riziko odkazující na nezamýšleným verzi stíněné proměnné, můžete plnému určení všechny odkazy na proměnnou stíněné. Stínový provoz zavádí více než jedna verze proměnné se stejným názvem. Pokud příkaz kódu odkazuje na název proměnné, verze, do které kompilátor vyřeší odkaz závisí na faktorech, jako je například umístění příkaz kódu a přítomnost opravňující řetězec. To může zvýšit riziko napadení odkazuje na nesprávné verze proměnné.  
  
## <a name="see-also"></a>Viz také  
 [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Stínový provoz v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Rozdíly mezi stínováním a přepsáním](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [Postupy: skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Postupy: skrytí zděděné proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Stínů](../../../../visual-basic/language-reference/modifiers/shadows.md)  
 [Přepsání](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [ME, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
