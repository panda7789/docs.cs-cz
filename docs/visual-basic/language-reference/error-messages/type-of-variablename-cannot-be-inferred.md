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
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="7936d-102">Typ '\<Variable > ' nelze odvodit, protože meze smyčky a proměnnou kroku nelze rozšířit na stejný typ</span><span class="sxs-lookup"><span data-stu-id="7936d-102">Type of '\<variablename>' cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>

<span data-ttu-id="7936d-103">Napsali `For...Next` jste smyčku, ve které kompilátor nemůže odvodit datový typ pro řídicí proměnnou smyčky, protože jsou splněné následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="7936d-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>

- <span data-ttu-id="7936d-104">Datový typ řídicí proměnné smyčky není specifikován s `As` klauzulí.</span><span class="sxs-lookup"><span data-stu-id="7936d-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>

- <span data-ttu-id="7936d-105">Meze smyčky a proměnná kroku obsahují alespoň dva datové typy.</span><span class="sxs-lookup"><span data-stu-id="7936d-105">The loop bounds and step variable contain at least two data types.</span></span>

- <span data-ttu-id="7936d-106">Mezi datovými typy neexistují žádné standardní převody.</span><span class="sxs-lookup"><span data-stu-id="7936d-106">No standard conversions exist between the data types.</span></span>

 <span data-ttu-id="7936d-107">Proto kompilátor nemůže odvodit datový typ kontrolní proměnné smyčky.</span><span class="sxs-lookup"><span data-stu-id="7936d-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>

 <span data-ttu-id="7936d-108">V následujícím příkladu je proměnná kroku znak a hranice smyčky jsou obě celá čísla.</span><span class="sxs-lookup"><span data-stu-id="7936d-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="7936d-109">Vzhledem k tomu, že neexistuje žádný standardní převod mezi znaky a celými čísly, je tato chyba hlášena.</span><span class="sxs-lookup"><span data-stu-id="7936d-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>

```vb
Dim stepVar = "1"c
Dim m = 0
Dim n = 20

' Not valid.
' For i = 1 To 10 Step stepVar
    ' Loop processing
' Next
```

<span data-ttu-id="7936d-110">**ID chyby:** BC30982</span><span class="sxs-lookup"><span data-stu-id="7936d-110">**Error ID:** BC30982</span></span>

## <a name="to-correct-this-error"></a><span data-ttu-id="7936d-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="7936d-111">To correct this error</span></span>

- <span data-ttu-id="7936d-112">V případě potřeby změňte typy hranic smyčky a proměnnou kroku tak, aby alespoň jedna z nich byla typu, ke kterému se ostatní rozšíří.</span><span class="sxs-lookup"><span data-stu-id="7936d-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="7936d-113">V předchozím příkladu změňte typ `stepVar` na. `Integer`</span><span class="sxs-lookup"><span data-stu-id="7936d-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>

  ```vb
  Dim stepVar = 1
  ```

  <span data-ttu-id="7936d-114">-nebo-</span><span class="sxs-lookup"><span data-stu-id="7936d-114">-or-</span></span>

  ```vb
  Dim stepVar As Integer = 1
  ```

- <span data-ttu-id="7936d-115">Pomocí explicitních funkcí pro převod můžete převést hranice smyčky a proměnnou kroku na příslušné typy.</span><span class="sxs-lookup"><span data-stu-id="7936d-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="7936d-116">V předchozím příkladu použijte `Val` funkci na. `stepVar`</span><span class="sxs-lookup"><span data-stu-id="7936d-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>

  ```vb
  For i = 1 To 10 Step Val(stepVar)
      ' Loop processing
  Next
  ```

## <a name="see-also"></a><span data-ttu-id="7936d-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7936d-117">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="7936d-118">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="7936d-118">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="7936d-119">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="7936d-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="7936d-120">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="7936d-120">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="7936d-121">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="7936d-121">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="7936d-122">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="7936d-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="7936d-123">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="7936d-123">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
