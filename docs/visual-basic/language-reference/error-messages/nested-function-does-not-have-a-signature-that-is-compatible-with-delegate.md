---
title: Vnořená funkce nemá stejný podpis kompatibilní s delegátem '<delegatename>'.
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: 28d07f01c0fd467cb68d73749988273eee95edf4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409423"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>Vnořená funkce nemá stejný podpis kompatibilní s delegátem '\<delegatename>'.

K delegátovi, který má nekompatibilní signaturu, byl přiřazen výraz lambda. Například v následujícím kódu `Del` má delegát dva celočíselné parametry.

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

Tato chyba je vyvolána, pokud je výraz lambda s jedním argumentem deklarován jako typ `Del` :

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

**ID chyby:** BC36532

## <a name="to-correct-this-error"></a>Oprava této chyby

Upravte buď definici delegáta, nebo přiřazený výraz lambda tak, aby signatury byly kompatibilní.

## <a name="see-also"></a>Viz také

- [Volný převod delegáta](../../programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Výrazy lambda](../../programming-guide/language-features/procedures/lambda-expressions.md)
