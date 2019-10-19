---
title: Vnořená funkce nemá stejný podpis kompatibilní s delegátem '<delegatename>'.
ms.date: 07/20/2015
f1_keywords:
- vbc36532
- bc36532
helpviewer_keywords:
- BC36532
ms.assetid: 493f292c-d81e-40ef-8b47-61f020571829
ms.openlocfilehash: d65c8eab661675c955ff6562098248c04036d6e7
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2019
ms.locfileid: "72580650"
---
# <a name="nested-function-does-not-have-a-signature-that-is-compatible-with-delegate-delegatename"></a>Vnořená funkce nemá signaturu, která je kompatibilní s delegátem ' \<delegatename > '.

K delegátovi, který má nekompatibilní signaturu, byl přiřazen výraz lambda. Například v následujícím kódu má delegát `Del` dva celočíselné parametry.

```vb
Delegate Function Del(ByVal p As Integer, ByVal q As Integer) As Integer
```

Tato chyba je vyvolána, pokud je výraz lambda s jedním argumentem deklarován jako typ `Del`:

```vb
' Neither of these is valid.
' Dim lambda1 As Del = Function(n As Integer) n + 1
' Dim lambda2 As Del = Function(n) n + 1
```

**ID chyby:** BC36532

## <a name="to-correct-this-error"></a>Oprava této chyby

Upravte buď definici delegáta, nebo přiřazený výraz lambda tak, aby signatury byly kompatibilní.

## <a name="see-also"></a>Viz také:

- [Volný převod delegáta](../../../visual-basic/programming-guide/language-features/delegates/relaxed-delegate-conversion.md)
- [Výrazy lambda](../../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md)
