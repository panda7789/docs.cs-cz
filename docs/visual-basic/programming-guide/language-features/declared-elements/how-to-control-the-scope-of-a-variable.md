---
title: 'Postupy: Řízení rozsahu proměnné (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- variables [Visual Basic], scope
- declared elements [Visual Basic], scope
- visibility [Visual Basic], declared elements
- variables [Visual Basic], visibility
- scope [Visual Basic], declared elements
- scope [Visual Basic], variables
- scope [Visual Basic], Visual Basic
- declared elements [Visual Basic], visibility
- visibility [Visual Basic], variables
ms.assetid: 44b7f62a-cb5c-4d50-bce9-60ae68f87072
ms.openlocfilehash: 24a7ae3b8f3400beeaedb20ea6352ea44bdb7597
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59324315"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Postupy: Řízení rozsahu proměnné (Visual Basic)
Za normálních okolností je proměnná v *oboru*, nebo viditelné pro použití v rámci oblasti, ve kterém se deklaruje. V některých případech je proměnná společnosti *úroveň přístupu* mohou mít vliv na svém oboru.  
  
 Další informace najdete v tématu [obor v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="scope-at-block-or-procedure-level"></a>Obor bloku nebo úroveň procedury  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Aby byla proměnná viditelná pouze v rámci bloku  
  
-   Místo [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) proměnné mezi zahájení a ukončení příkazy deklarace tohoto bloku, například mezi `For` a `Next` prohlášení o `For` smyčky.  
  
     Mohou odkazovat na proměnné pouze z v rámci bloku.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Aby byla proměnná viditelná pouze v rámci procedury  
  
-   Místo `Dim` příkaz pro proměnnou uvnitř procesu, ale mimo všechny bloky (například `With`... `End With` bloku).  
  
     Mohou odkazovat na proměnné pouze z v rámci procedury, stejně jako dovnitř všechny bloky obsažené v postupu.  
  
## <a name="scope-at-module-or-namespace-level"></a>Obor na úrovni Namespace nebo modul  
 Pro usnadnění práce, jeden výraz *úroveň modulu* vztahuje stejnou měrou na moduly, třídy a struktury. Úroveň přístupu modulu úrovně proměnné určuje její obor. Obor názvů obsahující modulu, třídy nebo struktury také ovlivňuje oboru.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Ke zviditelnění proměnné v rámci modulu, třídy nebo struktury  
  
1. Místo `Dim` příkaz pro proměnné v modulu, třídy nebo struktury, ale mimo všechny procedury.  
  
2. Zahrnout [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo v `Dim` příkazu.  
  
3. Můžete se podívat do proměnné z kamkoli v modulu, třídy nebo struktury, ale ne z mimo něj.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Aby byla proměnná viditelná v celém oboru názvů  
  
1. Místo `Dim` příkaz pro proměnné v modulu, třídy nebo struktury, ale mimo všechny procedury.  
  
2. Zahrnout [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) nebo [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo v `Dim` příkaz.  
  
3. Můžete se podívat do proměnné z libovolného místa v rámci oboru názvů obsahujícím modulu, třídy nebo struktury.  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje proměnnou na úrovni modulu a omezuje viditelnost kódu v rámci modulu.  
  
```  
Module demonstrateScope  
    Private strMsg As String  
    Sub initializePrivateVariable()  
        strMsg = "This variable cannot be used outside this module."  
    End Sub  
    Sub usePrivateVariable()  
        MsgBox(strMsg)  
    End Sub  
End Module  
```  
  
 V předchozím příkladu všechny postupy definované v modulu `demonstrateScope` může odkazovat `String` proměnnou `strMsg`. Když `usePrivateVariable` volání procedury, zobrazí se obsah proměnné řetězce `strMsg` v dialogovém okně.  
  
 S následující změnou v předchozím příkladu, Řetězcová hodnota `strMsg` lze odkazovat pomocí kódu kdekoli v deklaraci oboru názvů.  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Robustní programování  
 Čím užší obor proměnné, méně možností, které máte pro omylem odkazující na jeho místo další proměnnou se stejným názvem. Můžete také minimalizovat problémy odpovídající odkaz.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Čím užší obor proměnné, čím menší pravděpodobnost, že škodlivý kód může být nesprávné použití ho.  
  
## <a name="see-also"></a>Viz také:

- [Rozsah v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Doba platnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Úrovně přístupu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md)
