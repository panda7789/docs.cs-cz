---
title: "Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- qualification [Visual Basic], of element names
- declarations [Visual Basic], elements
- element names [Visual Basic], qualification
- references [Visual Basic], declared elements
- declaration statements [Visual Basic], declared elements
- declaring elements [Visual Basic]
- referencing declared elements [Visual Basic]
- declared elements [Visual Basic], referencing
- declared elements [Visual Basic], about declared elements
ms.assetid: e39c0752-f19f-4d2e-a453-00df1b5fc7ee
caps.latest.revision: "25"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: af031f3ef134b2a509922e6ada28aa5b2b80d641
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná (Visual Basic)
Můžete skrýt proměnné podle *stínový provoz* ho, který je ve předefinování s proměnné se stejným názvem. Můžete stínové proměnnou, kterou chcete skrýt dvěma způsoby:  
  
-   **Stínový provoz prostřednictvím oboru.** Můžete ho stínové prostřednictvím oboru podle redeclaring uvnitř podoblasti oblasti obsahující proměnnou, kterou chcete skrýt.  
  
-   **Stínový provoz prostřednictvím dědičnosti.** Pokud chcete skrýt proměnné definovanou na úrovni třídy, vám může stínové ji prostřednictvím dědičnosti podle její redeclaring [stínů](../../../../visual-basic/language-reference/modifiers/shadows.md) – klíčové slovo v odvozené třídě.  
  
## <a name="two-ways-to-hide-a-variable"></a>Dva způsoby, jak skrýt proměnné  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>Chcete-li skrýt proměnné tak, že stínování prostřednictvím rozsahu  
  
1.  Určit oblasti definování proměnné, které chcete skrýt a určit podoblasti, ve kterém znovu definovat s vaše proměnná.  
  
    |Oblast proměnné|Povolená podoblasti pro jeho opětovná definice|  
    |-----------------------|-------------------------------------------|  
    |Modul|Třídu v rámci modulu|  
    |Třída|Podtřídy v rámci třídy<br /><br /> Postup v rámci třídy|  
  
     Nelze upravit postup proměnné v bloku v rámci tohoto postupu, například v `If`... `End If` konstrukce nebo `For` smyčky.  
  
2.  Pokud ještě neexistuje, vytvořte podoblasti.  
  
3.  V rámci podoblasti, zápisu [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarace proměnnou stínového provozu.  
  
     Pokud kód podoblasti odkazuje na název proměnné, kompilátor vyřeší odkaz na proměnnou stínového provozu.  
  
     Následující příklad ilustruje, stínový provoz prostřednictvím oboru, jakož i odkaz, který obchází stínový provoz.  
  
    ```  
    Module shadowByScope  
        ' The following statement declares num as a module-level variable.  
        Public num As Integer  
        Sub show()  
            ' The following statement declares num as a local variable.  
            Dim num As Integer  
            ' The following statement sets the value of the local variable.  
            num = 2  
            ' The following statement displays the module-level variable.  
            MsgBox(CStr(shadowByScope.num))  
        End Sub  
        Sub useModuleLevelNum()  
            ' The following statement sets the value of the module-level variable.  
            num = 1  
            show()  
        End Sub  
    End Module  
    ```  
  
     V předchozím příkladu deklaruje proměnnou `num` na úrovni modulu i na úrovni postupu (v postupu `show`). Místní proměnná `num` shadows proměnnou úroveň modulu `num` v rámci `show`, takže místní proměnná je nastavená na 2. Neexistuje však žádný místní proměnné na stínové `num` v `useModuleLevelNum` postupu. Proto `useModuleLevelNum` nastaví hodnotu úroveň modulu proměnné na hodnotu 1.  
  
     `MsgBox` Volání uvnitř `show` obchází stínového provozu mechanismus kvalifikováním `num` s názvem modulu. Proto se zobrazí proměnnou úroveň modulu místo místní proměnné.  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>Chcete-li skrýt proměnné tak, že stínování prostřednictvím dědičnosti  
  
1.  Ujistěte se, že proměnnou, kterou chcete skrýt je deklarovaná ve třídě a na úrovni třídy (mimo jakéhokoli postupu). V opačném případě nemůže stínové prostřednictvím dědičnosti.  
  
2.  Definice třídy odvozené od třídy proměnné, pokud ještě neexistuje.  
  
3.  V odvozené třídě, zápisu `Dim` příkaz deklarace vaše proměnná. Zahrnout [stínů](../../../../visual-basic/language-reference/modifiers/shadows.md) – klíčové slovo v deklaraci.  
  
     Když kód v odvozené třídě odkazuje na název proměnné, kompilátor vyřeší odkaz na vaše proměnná.  
  
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
 Stínový provoz zavádí více než jedna verze proměnné se stejným názvem. Pokud příkaz kódu odkazuje na název proměnné, verze, do které kompilátor vyřeší odkaz závisí na faktorech, jako je například umístění příkaz kódu a přítomnost opravňující řetězec. To může zvýšit riziko napadení odkazující na nezamýšleným verzi stíněné proměnné. Plně kvalifikovaný všechny odkazy na proměnnou stíněné můžete snížit rizika.  
  
## <a name="see-also"></a>Viz také  
 [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)  
 [Stínový provoz v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Rozdíly mezi stínováním a přepsáním](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)  
 [Postupy: skrytí zděděné proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)  
 [Postupy: přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)  
 [Přepsání](../../../../visual-basic/language-reference/modifiers/overrides.md)  
 [ME, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)  
 [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
