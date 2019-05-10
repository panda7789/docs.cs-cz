---
title: Typ '<variablename>' nelze odvodit, protože omezení cyklu a proměnnou kroku nelze rozšířit na stejný typ.
ms.date: 07/20/2015
f1_keywords:
- bc30982
- vbc30982
helpviewer_keywords:
- BC30982
ms.assetid: 741e85d9-a747-42ad-a1e1-a3f1928aaff5
ms.openlocfilehash: 2dc7793a837c588b98365a97ada58c67dc07fa03
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64664255"
---
# <a name="type-of-variablename-cannot-be-inferred-because-the-loop-bounds-and-the-step-variable-do-not-widen-to-the-same-type"></a><span data-ttu-id="253a8-102">Typ '\<NázevProměnné >' nelze odvodit, protože omezení cyklu a klauzuli kroku nejde rozšířit na stejný typ.</span><span class="sxs-lookup"><span data-stu-id="253a8-102">Type of '\<variablename>' cannot be inferred because the loop bounds and the step variable do not widen to the same type</span></span>
<span data-ttu-id="253a8-103">Jste napsali `For...Next` smyčku, ve kterém kompilátor nemůže odvodit typ dat pro řídicí proměnná smyčky for vzhledem k tomu, že jsou splněny následující podmínky:</span><span class="sxs-lookup"><span data-stu-id="253a8-103">You have written a `For...Next` loop in which the compiler cannot infer a data type for the loop control variable because the following conditions are true:</span></span>  
  
- <span data-ttu-id="253a8-104">Není zadaný datový typ řídicí proměnná smyčky s `As` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="253a8-104">The data type of the loop control variable is not specified with an `As` clause.</span></span>  
  
- <span data-ttu-id="253a8-105">Omezení cyklu a klauzuli kroku obsahovat aspoň dva datové typy.</span><span class="sxs-lookup"><span data-stu-id="253a8-105">The loop bounds and step variable contain at least two data types.</span></span>  
  
- <span data-ttu-id="253a8-106">Neexistuje žádný standardní převod mezi datovými typy.</span><span class="sxs-lookup"><span data-stu-id="253a8-106">No standard conversions exist between the data types.</span></span>  
  
 <span data-ttu-id="253a8-107">Proto kompilátor nelze odvodit datový typ řídicí proměnná smyčky.</span><span class="sxs-lookup"><span data-stu-id="253a8-107">Therefore, the compiler cannot infer the data type of a loop's control variable.</span></span>  
  
 <span data-ttu-id="253a8-108">V následujícím příkladu krok proměnná je znak, a omezení cyklu jsou obě celá čísla.</span><span class="sxs-lookup"><span data-stu-id="253a8-108">In the following example, the step variable is a character and the loop bounds are both integers.</span></span> <span data-ttu-id="253a8-109">Protože neexistuje žádný standardní převod mezi znaky a celá čísla, tato chyba se nahlásí.</span><span class="sxs-lookup"><span data-stu-id="253a8-109">Because there is no standard conversion between characters and integers, this error is reported.</span></span>  
  
```vb  
Dim stepVar = "1"c  
Dim m = 0  
Dim n = 20  
  
' Not valid.  
' For i = 1 To 10 Step stepVar  
    ' Loop processing  
' Next  
```  
  
 <span data-ttu-id="253a8-110">**ID chyby:** BC30982</span><span class="sxs-lookup"><span data-stu-id="253a8-110">**Error ID:** BC30982</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="253a8-111">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="253a8-111">To correct this error</span></span>  
  
- <span data-ttu-id="253a8-112">Změňte typy omezení cyklu a klauzuli kroku podle potřeby tak, aby aspoň jeden z nich je typ, který ostatní rozšířit na.</span><span class="sxs-lookup"><span data-stu-id="253a8-112">Change the types of the loop bounds and step variable as necessary so that at least one of them is a type that the others widen to.</span></span> <span data-ttu-id="253a8-113">V předchozím příkladu, změňte typ `stepVar` k `Integer`.</span><span class="sxs-lookup"><span data-stu-id="253a8-113">In the preceding example, change the type of `stepVar` to `Integer`.</span></span>  
  
    ```  
    Dim stepVar = 1  
    ```  
  
     <span data-ttu-id="253a8-114">—nebo—</span><span class="sxs-lookup"><span data-stu-id="253a8-114">—or—</span></span>  
  
    ```  
    Dim stepVar As Integer = 1  
    ```  
  
- <span data-ttu-id="253a8-115">Převést na odpovídající typy omezení cyklu a klauzuli kroku pomocí funkce pro explicitní převod.</span><span class="sxs-lookup"><span data-stu-id="253a8-115">Use explicit conversion functions to convert the loop bounds and step variable to the appropriate types.</span></span> <span data-ttu-id="253a8-116">V předchozím příkladu platí `Val` funkce `stepVar`.</span><span class="sxs-lookup"><span data-stu-id="253a8-116">In the preceding example, apply the `Val` function to `stepVar`.</span></span>  
  
    ```  
    For i = 1 To 10 Step Val(stepVar)  
        ' Loop processing  
    Next  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="253a8-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="253a8-117">See also</span></span>

- <xref:Microsoft.VisualBasic.Conversion.Val%2A>
- [<span data-ttu-id="253a8-118">Příkaz For...Next</span><span class="sxs-lookup"><span data-stu-id="253a8-118">For...Next Statement</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)
- [<span data-ttu-id="253a8-119">Implicitní a explicitní převody</span><span class="sxs-lookup"><span data-stu-id="253a8-119">Implicit and Explicit Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [<span data-ttu-id="253a8-120">Odvození místního typu</span><span class="sxs-lookup"><span data-stu-id="253a8-120">Local Type Inference</span></span>](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
- [<span data-ttu-id="253a8-121">Příkaz Option Infer</span><span class="sxs-lookup"><span data-stu-id="253a8-121">Option Infer Statement</span></span>](../../../visual-basic/language-reference/statements/option-infer-statement.md)
- [<span data-ttu-id="253a8-122">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="253a8-122">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="253a8-123">Rozšíření a zúžení převodů</span><span class="sxs-lookup"><span data-stu-id="253a8-123">Widening and Narrowing Conversions</span></span>](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
