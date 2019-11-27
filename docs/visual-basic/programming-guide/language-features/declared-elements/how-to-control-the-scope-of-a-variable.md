---
title: 'Postupy: Řízení rozsahu proměnné'
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
ms.openlocfilehash: 0ee6ce183310aa836ecdbbc0bc819e0e83d1872d
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345380"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Postupy: Řízení rozsahu proměnné (Visual Basic)
V normálním případě je proměnná v *oboru*, nebo viditelná pro referenci, v celé oblasti, ve které ji deklarujete. V některých případech může mít *úroveň přístupu* proměnné vliv na svůj rozsah.  
  
 Další informace najdete v tématu věnovaném [oboru v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md).  
  
## <a name="scope-at-block-or-procedure-level"></a>Rozsah na úrovni bloku nebo procedury  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Chcete-li proměnnou zobrazit pouze v rámci bloku  
  
- Umístěte [příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) pro proměnnou mezi příkazy inicializace a ukončující deklarace tohoto bloku, například mezi příkazy `For` a `Next` `For` smyčky.  
  
     Na proměnnou můžete odkazovat pouze v rámci bloku.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Chcete-li proměnnou zobrazit pouze v rámci procedury  
  
- Umístěte příkaz `Dim` pro proměnnou uvnitř procedury, ale mimo libovolný blok (například `With`...`End With` blok).  
  
     Na proměnnou můžete odkazovat pouze v rámci procedury, včetně uvnitř libovolného bloku, který je obsažen v proceduře.  
  
## <a name="scope-at-module-or-namespace-level"></a>Rozsah na úrovni modulu nebo oboru názvů  
 Pro usnadnění práce se *úroveň modulu* s jedním termínem aplikuje rovnoměrně na moduly, třídy a struktury. Úroveň přístupu proměnné na úrovni modulu určuje její obor. Obor názvů, který obsahuje modul, třídu nebo strukturu, má vliv také na obor.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Chcete-li zviditelnit proměnnou v rámci modulu, třídy nebo struktury  
  
1. Umístěte příkaz `Dim` pro proměnnou uvnitř modulu, třídy nebo struktury, ale vně jakékoli procedury.  
  
2. Do příkazu `Dim` zahrňte klíčové slovo [Private](../../../../visual-basic/language-reference/modifiers/private.md) .  
  
3. Na proměnnou můžete odkazovat odkudkoli v rámci modulu, třídy nebo struktury, ale ne z vnějšku.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Chcete-li nastavit proměnnou v rámci oboru názvů jako viditelné  
  
1. Umístěte příkaz `Dim` pro proměnnou uvnitř modulu, třídy nebo struktury, ale vně jakékoli procedury.  
  
2. Do příkazu `Dim` zahrňte klíčové slovo [Friend](../../../../visual-basic/language-reference/modifiers/friend.md) nebo [Public](../../../../visual-basic/language-reference/modifiers/public.md) .  
  
3. Na proměnnou můžete odkazovat odkudkoli v rámci oboru názvů obsahujícího modul, třídu nebo strukturu.  
  
## <a name="example"></a>Příklad  
 Následující příklad deklaruje proměnnou na úrovni modulu a omezí její viditelnost na kód v rámci modulu.  
  
```vb  
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
  
 V předchozím příkladu můžou všechny procedury definované v modulu `demonstrateScope` odkazovat na `String` proměnnou `strMsg`. Když je volána procedura `usePrivateVariable`, zobrazí obsah řetězcové proměnné `strMsg` v dialogovém okně.  
  
 S následující změnou v předchozím příkladu lze řetězcové proměnné `strMsg` odkazovat pomocí kódu kdekoli v oboru názvů své deklarace.  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Robustní programování  
 Čím užší je rozsah proměnné, tím menší je počet příležitostí, které se na ni neodkazují na místo jiné proměnné se stejným názvem. Můžete také minimalizovat problémy s porovnáním odkazů.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Zúžení rozsahu proměnné, menší pravděpodobnost, že škodlivý kód může nevhodným způsobem používat.  
  
## <a name="see-also"></a>Viz také:

- [Obor v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/scope.md)
- [Doba života v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/lifetime.md)
- [Úrovně přístupu v Visual Basic](../../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Proměnné](../../../../visual-basic/programming-guide/language-features/variables/index.md)
- [Deklarace proměnné](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [Příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md)
