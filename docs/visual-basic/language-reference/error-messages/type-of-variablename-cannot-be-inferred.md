---
title: Typ '<variablename>' nelze odvodit, protože omezení cyklu a proměnnou kroku nelze rozšířit na stejný typ.
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: c3086f79fb71693810bc8f14e8c0f493aa1e6515
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512711"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Typ '\<Variable > ' nelze odvodit, protože meze smyčky a proměnnou kroku nelze rozšířit na stejný typ

Napsali `For...Next` jste smyčku, ve které kompilátor nemůže odvodit datový typ pro řídicí proměnnou smyčky, protože jsou splněné následující podmínky:

- Datový typ řídicí proměnné smyčky není specifikován s `As` klauzulí.

- Meze smyčky a proměnná kroku obsahují alespoň dva datové typy.

- Mezi datovými typy neexistují žádné standardní převody.

 Proto kompilátor nemůže odvodit datový typ kontrolní proměnné smyčky.

 V následujícím příkladu je proměnná kroku znak a hranice smyčky jsou obě celá čísla. Vzhledem k tomu, že neexistuje žádný standardní převod mezi znaky a celými čísly, je tato chyba hlášena.

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

**ID chyby:** BC30982

## <a name="to-correct-this-error"></a>Oprava této chyby

- V případě potřeby změňte typy hranic smyčky a proměnnou kroku tak, aby alespoň jedna z nich byla typu, ke kterému se ostatní rozšíří. V předchozím příkladu změňte typ `stepVar` na. `Integer`

  ```vb
  Dim stepVar = 1
  ```

  -nebo-

  ```vb
  Dim stepVar As Integer = 1
  ```

- Pomocí explicitních funkcí pro převod můžete převést hranice smyčky a proměnnou kroku na příslušné typy. V předchozím příkladu použijte `Val` funkci na. `stepVar`

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a>Viz také:

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [Příkaz For...Next](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [Implicitní a explicitní převody](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [Příkaz Option Infer](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [Funkce pro převod typů](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [Rozšíření a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
