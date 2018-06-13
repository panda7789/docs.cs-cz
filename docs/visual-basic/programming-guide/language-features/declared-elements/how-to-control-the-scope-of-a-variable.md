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
ms.openlocfilehash: 6e8d1178398711226b88fee7e6defd5162b91fcb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33649188"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Postupy: Řízení rozsahu proměnné (Visual Basic)
Za normálních okolností je proměnná v *oboru*, nebo viditelné pro referenci v celé oblasti, ve kterém je deklarovat. V některých případech proměnnou na *úroveň přístupu* mohou mít vliv na svém oboru.  
  
 Další informace najdete v tématu [oboru v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="scope-at-block-or-procedure-level"></a>Obor bloku nebo úroveň procedury  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Chcete-li zobrazit pouze v rámci bloku proměnné  
  
-   Místní [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) pro proměnnou mezi zahájení a ukončení deklarační příkazy bloku, například mezi `For` a `Next` příkazů `For` smyčky.  
  
     Může být pouze z proměnné v bloku.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Chcete-li zobrazit pouze v rámci procedury proměnné  
  
-   Místní `Dim` příkaz pro proměnnou uvnitř postup, ale mimo všechny bloky (například `With`... `End With` bloku).  
  
     Najdete v postupu, včetně uvnitř bloku, všechny obsažené v postupu proměnnou pouze z.  
  
## <a name="scope-at-module-or-namespace-level"></a>Obor na úrovni Namespace nebo modulu  
 Pro usnadnění práce jeden termín *úroveň modulu* vztahuje stejnou měrou na moduly, třídy a struktury. Úroveň přístupu tohoto modulu úrovně proměnné určuje její obor. Obor názvů, který obsahuje modul, třídu nebo strukturu vliv také oboru.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Chcete-li zobrazit v rámci modulu, třídu nebo strukturu proměnné  
  
1.  Místo `Dim` příkaz pro proměnnou uvnitř modulu, třídu nebo strukturu, ale mimo jakéhokoli postupu.  
  
2.  Zahrnout [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo v `Dim` příkaz.  
  
3.  Můžete se podívat do proměnné z kamkoli v modulu, třídu nebo strukturu, ale nikoli z mimo něj.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Chcete-li zobrazit v rámci oboru názvů proměnné  
  
1.  Místo `Dim` příkaz pro proměnnou uvnitř modulu, třídu nebo strukturu, ale mimo jakéhokoli postupu.  
  
2.  Zahrnout [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) nebo [veřejné](../../../../visual-basic/language-reference/modifiers/public.md) – klíčové slovo v `Dim` příkaz.  
  
3.  Můžete se podívat do proměnné z libovolného místa v rámci oboru názvů, který obsahuje modul, třídu nebo strukturu.  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje proměnné na úrovni modulu a omezuje jeho viditelnost kódu v rámci modulu.  
  
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
  
 V předchozím příkladu, všechny postupy definované v modulu `demonstrateScope` najdete `String` proměnná `strMsg`. Když `usePrivateVariable` procedura je volána, zobrazí se obsah proměnnou řetězce `strMsg` v dialogovém okně.  
  
 S následující změnou v předcházejícím příkladu proměnnou řetězce `strMsg` lze odkazovat kódem kdekoli v oboru názvů jeho deklaraci.  
  
```  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Robustní programování  
 Čím užší rozsah proměnnou, méně možností, které jsou na omylem odkazující na jeho místo jiné proměnné se stejným názvem. Také můžete minimalizovat problémy odpovídajících odkaz.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Čím užší obor proměnné, tím menší pravděpodobnost, že škodlivý kód způsobit nesprávné použijte ho.  
  
## <a name="see-also"></a>Viz také  
 [Rozsah v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)  
 [Doba platnosti v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)  
 [Úrovně přístupu v jazyce Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
 [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)  
 [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [Příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
