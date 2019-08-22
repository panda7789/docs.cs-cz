---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: 1fa4c1fa0a2def02dd56fa3728a8df4b5ff16b7f
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666850"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Určuje, že argument je předán [hodnotou](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), takže volaná procedura nebo vlastnost nemůže změnit hodnotu proměnné podkladové hodnoty argumentu v volajícím kódu. Pokud není zadán žádný modifikátor, je jako výchozí použita hodnota ByVal.

> [!NOTE]
> Vzhledem k tomu, že je výchozí hodnota, není nutné explicitně zadat `ByVal` klíčové slovo v podpisech metody. Je v úmyslu způsobit vysokou úroveň kódu a často vede k přehlédnutí na jiné `ByRef` než výchozí klíčové slovo.

## <a name="remarks"></a>Poznámky
 V těchto kontextech lze použít Modifikátor:`ByVal`

 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)

 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a>Příklad
 Následující příklad ukazuje použití `ByVal` mechanismu předávání parametrů s argumentem typu odkazu. V příkladu je `c1`argumentem instance třídy `Class1`. `ByVal`zabraňuje kódu v postupech v změně podkladové hodnoty argumentu `c1`odkazu,,, ale nechrání dostupná pole a `c1`vlastnosti.

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>Viz také:

- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Předávání argumentů podle hodnoty a reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
