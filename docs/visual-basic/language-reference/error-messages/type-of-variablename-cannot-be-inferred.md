---
title: Typ '<variablename>' nelze odvodit, protože omezení cyklu a proměnnou kroku nelze rozšířit na stejný typ.
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 74b690ce3dee87e481c629a254e629be4b40f8cd
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84387007"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a>Typ '\<variablename>' nelze odvodit, protože omezení cyklu a proměnnou kroku nelze rozšířit na stejný typ.

Napsali jste `For...Next` smyčku, ve které kompilátor nemůže odvodit datový typ pro řídicí proměnnou smyčky, protože jsou splněné následující podmínky:

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

- V případě potřeby změňte typy hranic smyčky a proměnnou kroku tak, aby alespoň jedna z nich byla typu, ke kterému se ostatní rozšíří. V předchozím příkladu změňte typ `stepVar` na `Integer` .

  ```vb
  Dim stepVar = 1
  ```

  -nebo-

  ```vb
  Dim stepVar As Integer = 1
  ```

- Pomocí explicitních funkcí pro převod můžete převést hranice smyčky a proměnnou kroku na příslušné typy. V předchozím příkladu použijte `Val` funkci na `stepVar` .

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a>Viz také

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [For...Next – příkaz](../statements/for-next-statement.md)
- [Implicitní a explicitní převody](../../programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Odvození místního typu](../../programming-guide/language-features/variables/local-type-inference.md)
- [Option Infer – příkaz](../statements/option-infer-statement.md)
- [Funkce pro převod typů](../functions/type-conversion-functions.md)
- [Rozšíření a zúžení převodů](../../programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
