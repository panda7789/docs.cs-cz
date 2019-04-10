---
title: 'Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 744c7aed50690d5591d1e8248e121cb66ef39108
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296183"
---
# <a name="how-to-hide-a-variable-with-the-same-name-as-your-variable-visual-basic"></a>Postupy: Skrytí proměnné se stejným názvem jako má vaše proměnná (Visual Basic)
Můžete skrýt proměnné tak *stínováním* ho tedy předefinováním proměnnou se stejným názvem. Můžete stínové proměnné, které chcete skrýt dvěma způsoby:  
  
-   **Stínový provoz prostřednictvím oboru.** Můžete ho stínové prostřednictvím oboru ve změně deklarace je uvnitř podoblasti oblasti, který obsahuje proměnné, které chcete skrýt.  
  
-   **Stínový provoz prostřednictvím dědičnosti.** Pokud chcete skrýt proměnné je definován na úrovni třídy, je můžete stínové ji prostřednictvím dědičnosti ve změně deklarace s [stíny](../../../../visual-basic/language-reference/modifiers/shadows.md) – klíčové slovo v odvozené třídě.  
  
## <a name="two-ways-to-hide-a-variable"></a>Dva způsoby, jak skrýt proměnné  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-scope"></a>Chcete-li skrýt proměnné tak, že stínování prostřednictvím oboru  
  
1. Určit oblast definující proměnné, které chcete skrýt a určete podoblasti, ve kterém k předefinování se vaše proměnná.  
  
    |Proměnné oblasti|Pro předefinování ho povolený podoblast|  
    |-----------------------|-------------------------------------------|  
    |Modul|Třídy v rámci modulu|  
    |Třída|Podtřída v rámci třídy<br /><br /> Postup v rámci třídy|  
  
     Nelze předefinovat postupu proměnnou v bloku, v rámci tohoto postupu, například v `If`... `End If` konstrukce nebo `For` smyčky.  
  
2. Pokud ještě neexistuje, vytvořte podoblasti.  
  
3. V rámci podoblasti, zápisu [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarování proměnné stínového provozu.  
  
     Když kód uvnitř podoblasti odkazuje na název proměnné, přeloží kompilátor odkaz na proměnnou stínového provozu.  
  
     Následující příklad ukazuje stínování prostřednictvím oboru, stejně jako odkaz, který obchází stínováním.  
  
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
  
     Předchozí příklad deklaruje proměnnou `num` na úrovni modulu i na úrovni postup (v postupu `show`). Lokální proměnná `num` zastiňuje proměnnou úrovni modulu `num` v rámci `show`, takže místní proměnná je nastavená na 2. Neexistuje však žádný místní proměnnou stínové `num` v `useModuleLevelNum` postup. Proto `useModuleLevelNum` nastaví hodnotu proměnné úrovni modulu na 1.  
  
     `MsgBox` Volat v `show` obchází stínového provozu mechanismus kvalifikaci `num` s názvem modulu. Proto se zobrazí úrovni modulu proměnnou místo do místní proměnné.  
  
#### <a name="to-hide-a-variable-by-shadowing-it-through-inheritance"></a>Chcete-li skrýt proměnné tak, že stínování prostřednictvím dědičnosti  
  
1. Ujistěte se, že proměnné, které chcete skrýt je deklarovaná ve třídě a na úrovni třídy (mimo všechny procedury). V opačném případě nemůže zastiňovat prostřednictvím dědičnosti.  
  
2. Definujte třídu odvozenou z třídy proměnné, pokud ještě neexistuje.  
  
3. V odvozených třídách, zápisu `Dim` deklarace proměnné příkazu. Zahrnout [stíny](../../../../visual-basic/language-reference/modifiers/shadows.md) – klíčové slovo v deklaraci.  
  
     Když kód v odvozené třídě odkazuje na název proměnné, přeloží kompilátor odkaz na vaše proměnná.  
  
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
 Stínový provoz přináší více než jedna verze proměnné se stejným názvem. Když příkaz kódu odkazuje na název proměnné, verze, na který přeloží kompilátor odkaz na závisí na faktorech, jako je například umístění příkaz kódu a přítomnost oprávněným řetězec. To může zvýšit riziko odkazující na stínové proměnné a nežádoucí verzi. Plně kvalifikovaný všechny odkazy na stínové proměnné můžete snížit rizika.  
  
## <a name="see-also"></a>Viz také:

- [Odkazy na deklarované elementy](../../../../visual-basic/programming-guide/language-features/declared-elements/references-to-declared-elements.md)
- [Stínění v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Rozdíly mezi stínováním a přepsáním](../../../../visual-basic/programming-guide/language-features/declared-elements/differences-between-shadowing-and-overriding.md)
- [Postupy: Skrytí zděděné proměnné](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-hide-an-inherited-variable.md)
- [Postupy: Přístup k proměnné skryté odvozenou třídou](../../../../visual-basic/programming-guide/language-features/declared-elements/how-to-access-a-variable-hidden-by-a-derived-class.md)
- [Overrides](../../../../visual-basic/language-reference/modifiers/overrides.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
- [Základní informace o dědičnosti](../../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
