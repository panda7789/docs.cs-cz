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
ms.openlocfilehash: 8b21f22edea84448e3f2969c3e4b07c08a17a338
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84357345"
---
# <a name="how-to-control-the-scope-of-a-variable-visual-basic"></a>Postupy: Řízení rozsahu proměnné (Visual Basic)
V normálním případě je proměnná v *oboru*, nebo viditelná pro referenci, v celé oblasti, ve které ji deklarujete. V některých případech může mít *úroveň přístupu* proměnné vliv na svůj rozsah.  
  
 Další informace najdete v tématu věnovaném [oboru v Visual Basic](scope.md).  
  
## <a name="scope-at-block-or-procedure-level"></a>Rozsah na úrovni bloku nebo procedury  
  
#### <a name="to-make-a-variable-visible-only-within-a-block"></a>Chcete-li proměnnou zobrazit pouze v rámci bloku  
  
- Umístěte [příkaz Dim](../../../language-reference/statements/dim-statement.md) pro proměnnou mezi příkazy inicializace a ukončující deklarace tohoto bloku, například mezi `For` `Next` příkazy a `For` smyčky.  
  
     Na proměnnou můžete odkazovat pouze v rámci bloku.  
  
#### <a name="to-make-a-variable-visible-only-within-a-procedure"></a>Chcete-li proměnnou zobrazit pouze v rámci procedury  
  
- Do `Dim` procedury umístěte příkaz pro proměnnou, ale mimo libovolný blok (například `With` ... `End With` Block).  
  
     Na proměnnou můžete odkazovat pouze v rámci procedury, včetně uvnitř libovolného bloku, který je obsažen v proceduře.  
  
## <a name="scope-at-module-or-namespace-level"></a>Rozsah na úrovni modulu nebo oboru názvů  
 Pro usnadnění práce se *úroveň modulu* s jedním termínem aplikuje rovnoměrně na moduly, třídy a struktury. Úroveň přístupu proměnné na úrovni modulu určuje její obor. Obor názvů, který obsahuje modul, třídu nebo strukturu, má vliv také na obor.  
  
#### <a name="to-make-a-variable-visible-throughout-a-module-class-or-structure"></a>Chcete-li zviditelnit proměnnou v rámci modulu, třídy nebo struktury  
  
1. Umístěte `Dim` příkaz pro proměnnou uvnitř modulu, třídy nebo struktury, ale vně jakékoli procedury.  
  
2. Do příkazu zahrňte klíčové slovo [Private](../../../language-reference/modifiers/private.md) `Dim` .  
  
3. Na proměnnou můžete odkazovat odkudkoli v rámci modulu, třídy nebo struktury, ale ne z vnějšku.  
  
#### <a name="to-make-a-variable-visible-throughout-a-namespace"></a>Chcete-li nastavit proměnnou v rámci oboru názvů jako viditelné  
  
1. Umístěte `Dim` příkaz pro proměnnou uvnitř modulu, třídy nebo struktury, ale vně jakékoli procedury.  
  
2. Do příkazu zahrňte klíčové slovo [Friend](../../../language-reference/modifiers/friend.md) nebo [Public](../../../language-reference/modifiers/public.md) `Dim` .  
  
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
  
 V předchozím příkladu všechny procedury definované v modulu `demonstrateScope` mohou odkazovat na `String` proměnnou `strMsg` . Při `usePrivateVariable` volání procedury se zobrazí obsah proměnné řetězce `strMsg` v dialogovém okně.  
  
 S následující změnou v předchozím příkladu může být řetězcová proměnná `strMsg` odkazována pomocí kódu kdekoli v oboru názvů své deklarace.  
  
```vb  
Public strMsg As String  
```  
  
## <a name="robust-programming"></a>Robustní programování  
 Čím užší je rozsah proměnné, tím menší je počet příležitostí, které se na ni neodkazují na místo jiné proměnné se stejným názvem. Můžete také minimalizovat problémy s porovnáním odkazů.  
  
## <a name="net-framework-security"></a>Zabezpečení rozhraní .NET Framework  
 Zúžení rozsahu proměnné, menší pravděpodobnost, že škodlivý kód může nevhodným způsobem používat.  
  
## <a name="see-also"></a>Viz také

- [Rozsah v jazyce Visual Basic](scope.md)
- [Doba platnosti v jazyce Visual Basic](lifetime.md)
- [Úrovně přístupu v Visual Basic](access-levels.md)
- [Proměnné](../variables/index.md)
- [Deklarace proměnné](../variables/variable-declaration.md)
- [Dim – příkaz](../../../language-reference/statements/dim-statement.md)
