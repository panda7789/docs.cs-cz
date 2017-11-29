---
title: "Typ & č. 39; &lt;NázevProměnné&gt;& č. 39; nelze odvodit, protože hranice smyčky a proměnná krok není rozšíří do stejného typu"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords: BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
caps.latest.revision: "30"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 022e29e38a93d2880bbfa250e65a8b95b39ff140
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="type-of-39ltvariablenamegt39-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="ca8e2-102">Typ & č. 39; &lt;NázevProměnné&gt;& č. 39; nelze odvodit, protože hranice smyčky a proměnná krok není rozšíří do stejného typu</span><span class="sxs-lookup"><span data-stu-id="ca8e2-102">Type of &#39;&lt;variablename&gt;&#39; cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>
<span data-ttu-id="ca8e2-103">Jste napsali `For...Next` smyčky, ve kterém kompilátor nelze odvodit typ dat pro řídicí proměnná smyčky vzhledem k tomu, že jsou splněné následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="ca8e2-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>  
  
-   <span data-ttu-id="ca8e2-104">Datový typ řídicí proměnná smyčky není zadaný s `As` klauzule.</span><span class="sxs-lookup"><span data-stu-id="ca8e2-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>  
  
-   <span data-ttu-id="ca8e2-105">Rozsah smyčky a proměnnou krok obsahovat aspoň dva datové typy.</span><span class="sxs-lookup"><span data-stu-id="ca8e2-105">The loop bounds and step variable contain at least two data types.</span></span>  
  
-   <span data-ttu-id="ca8e2-106">Neexistují žádné standardní převody mezi datovými typy.</span><span class="sxs-lookup"><span data-stu-id="ca8e2-106">No standard conversions exist between the data types.</span></span>  
  
 <span data-ttu-id="ca8e2-107">Kompilátor proto nelze odvodit typ dat řídicí proměnná.</span><span class="sxs-lookup"><span data-stu-id="ca8e2-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>  
  
 <span data-ttu-id="ca8e2-108">V následujícím příkladu proměnnou krok je znak a hranice smyčky jsou obě celých čísel.</span><span class="sxs-lookup"><span data-stu-id="ca8e2-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="ca8e2-109">Protože neexistuje žádný standardní převod mezi znaky a celá čísla, tato chyba se nahlásí.</span><span class="sxs-lookup"><span data-stu-id="ca8e2-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 <span data-ttu-id="ca8e2-110">**ID chyby:** BC30982</span><span class="sxs-lookup"><span data-stu-id="ca8e2-110">**Error ID:** BC30982</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="ca8e2-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="ca8e2-111">To correct this error</span></span>  
  
-   <span data-ttu-id="ca8e2-112">Typy hranice smyčky a proměnná krok podle potřeby změňte tak, aby aspoň jeden z nich je typ, který ostatní rozšíří do.</span><span class="sxs-lookup"><span data-stu-id="ca8e2-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="ca8e2-113">V předchozím příkladu změnit typ `stepVar` k `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ca8e2-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     <span data-ttu-id="ca8e2-114">—nebo—</span><span class="sxs-lookup"><span data-stu-id="ca8e2-114">—or—</span></span>  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
-   <span data-ttu-id="ca8e2-115">Pomocí funkce pro explicitní převod můžete převést rozsah smyčky a proměnná krok na odpovídající typy.</span><span class="sxs-lookup"><span data-stu-id="ca8e2-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="ca8e2-116">V předchozím příkladu platí `Val` funkci, aby se `stepVar`.</span><span class="sxs-lookup"><span data-stu-id="ca8e2-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="ca8e2-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="ca8e2-117">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Conversion.Val%2A>  
 [<span data-ttu-id="ca8e2-118">Pro... Next – příkaz</span><span class="sxs-lookup"><span data-stu-id="ca8e2-118">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
 [<span data-ttu-id="ca8e2-119">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="ca8e2-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [<span data-ttu-id="ca8e2-120">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="ca8e2-120">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)  
 [<span data-ttu-id="ca8e2-121">Option Infer – příkaz</span><span class="sxs-lookup"><span data-stu-id="ca8e2-121">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)  
 [<span data-ttu-id="ca8e2-122">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="ca8e2-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="ca8e2-123">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="ca8e2-123">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
