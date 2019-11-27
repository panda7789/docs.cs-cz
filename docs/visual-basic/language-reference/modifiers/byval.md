---
title: ByVal
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: a96f871c6ce119f65ebbec54fdb1471ae105d504
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351585"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Určuje, že argument je předán [hodnotou](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), takže volaná procedura nebo vlastnost nemůže změnit hodnotu proměnné podkladové hodnoty argumentu v volajícím kódu. Pokud není zadán žádný modifikátor, je jako výchozí použita hodnota ByVal.

> [!NOTE]
> Vzhledem k tomu, že je výchozí hodnota, není nutné explicitně zadat klíčové slovo `ByVal` v podpisech metody. Je v úmyslu způsobit vysokou úroveň kódu a často vede k přehlédnutí na nevýchozí `ByRef` klíčová slova.

## <a name="remarks"></a>Poznámky
 V těchto kontextech lze použít modifikátor `ByVal`:

 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)

 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="example"></a>Příklad
 Následující příklad ukazuje použití mechanismu předávání parametrů `ByVal` s argumentem typu odkazu. V příkladu je argument `c1`, instance třídy `Class1`. `ByVal` zabraňuje kódu v postupech změnit podkladovou hodnotu argumentu odkazu, `c1`, ale nechrání přístupná pole a vlastnosti `c1`.

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>Viz také:

- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Předávání argumentů podle hodnoty a reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
