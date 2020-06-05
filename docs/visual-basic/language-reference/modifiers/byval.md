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
ms.openlocfilehash: c4cdafafa6bae3246c0512e28f94fde7e88d230b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84373021"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Určuje, že argument je předán [hodnotou](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md), takže volaná procedura nebo vlastnost nemůže změnit hodnotu proměnné podkladové hodnoty argumentu v volajícím kódu. Pokud není zadán žádný modifikátor, je jako výchozí použita hodnota ByVal.

> [!NOTE]
> Vzhledem k tomu, že je výchozí hodnota, není nutné explicitně zadat `ByVal` klíčové slovo v podpisech metody. Je v úmyslu způsobit vysokou úroveň kódu a často vede k přehlédnutí na jiné než výchozí `ByRef` klíčové slovo.

## <a name="remarks"></a>Poznámky
 `ByVal`V těchto kontextech lze použít modifikátor:

 [Declare – příkaz](../statements/declare-statement.md)

 [Function – příkaz](../statements/function-statement.md)
  
 [Operator – příkaz](../statements/operator-statement.md)
  
 [Property – příkaz](../statements/property-statement.md)
  
 [Sub – příkaz](../statements/sub-statement.md)

## <a name="example"></a>Příklad
 Následující příklad ukazuje použití `ByVal` mechanismu předávání parametrů s argumentem typu odkazu. V příkladu je argumentem `c1` instance třídy `Class1` . `ByVal`zabraňuje kódu v postupech v změně podkladové hodnoty argumentu odkazu, `c1` ,, ale nechrání dostupná pole a vlastnosti `c1` .

 [!code-vb[VbVbalrKeywords#10](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/Class5.vb#10)]

## <a name="see-also"></a>Viz také

- [Klíčová slova](../keywords/index.md)
- [Předávání argumentů podle hodnoty a reference](../../programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
