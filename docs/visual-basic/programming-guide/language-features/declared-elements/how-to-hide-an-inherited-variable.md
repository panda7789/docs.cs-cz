---
title: "Postupy: Skrytí zděděné proměnné (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d2059da873f8b9ec9ea51191139c652a9e01d92b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Postupy: skrytí proměnné se stejným názvem jako má vaše proměnná](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-a-variable-with-the-same-name-as-your-variable.md)  
 [Postupy: přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Přepsání](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [ME, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
