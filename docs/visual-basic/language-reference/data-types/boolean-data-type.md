---
title: Datový typ Boolean
ms.date: 07/20/2015
f1_keywords:
- vb.FALSE
- vb.TRUE
- vb.Boolean
helpviewer_keywords:
- Boolean data type
- Boolean values [Visual Basic], False keyword
- False keyword [Visual Basic]
- True keyword [Visual Basic]
- Boolean values [Visual Basic], True keyword
ms.assetid: 4858e630-4813-4216-a55e-f4d0feb884e4
ms.openlocfilehash: 5d05514207c5d07e81aab897f40f728570f6bd87
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347851"
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="75a95-102">Boolean – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="75a95-102">Boolean Data Type (Visual Basic)</span></span>

<span data-ttu-id="75a95-103">Holds values that can be only `True` or `False`.</span><span class="sxs-lookup"><span data-stu-id="75a95-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="75a95-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span><span class="sxs-lookup"><span data-stu-id="75a95-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="75a95-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="75a95-105">Remarks</span></span>  

 <span data-ttu-id="75a95-106">Use the [Boolean Data Type (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span><span class="sxs-lookup"><span data-stu-id="75a95-106">Use the [Boolean Data Type (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="75a95-107">The default value of `Boolean` is `False`.</span><span class="sxs-lookup"><span data-stu-id="75a95-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="75a95-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span><span class="sxs-lookup"><span data-stu-id="75a95-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="75a95-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span><span class="sxs-lookup"><span data-stu-id="75a95-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="75a95-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span><span class="sxs-lookup"><span data-stu-id="75a95-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="75a95-111">Převody typu</span><span class="sxs-lookup"><span data-stu-id="75a95-111">Type Conversions</span></span>  

 <span data-ttu-id="75a95-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span><span class="sxs-lookup"><span data-stu-id="75a95-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="75a95-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span><span class="sxs-lookup"><span data-stu-id="75a95-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="75a95-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span><span class="sxs-lookup"><span data-stu-id="75a95-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="75a95-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span><span class="sxs-lookup"><span data-stu-id="75a95-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="75a95-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="75a95-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="75a95-117">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="75a95-117">Programming Tips</span></span>  
  
- <span data-ttu-id="75a95-118">**Negative Numbers.**</span><span class="sxs-lookup"><span data-stu-id="75a95-118">**Negative Numbers.**</span></span> <span data-ttu-id="75a95-119">`Boolean` is not a numeric type and cannot represent a negative value.</span><span class="sxs-lookup"><span data-stu-id="75a95-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="75a95-120">In any case, you should not use `Boolean` to hold numeric values.</span><span class="sxs-lookup"><span data-stu-id="75a95-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
- <span data-ttu-id="75a95-121">**Type Characters.**</span><span class="sxs-lookup"><span data-stu-id="75a95-121">**Type Characters.**</span></span> <span data-ttu-id="75a95-122">`Boolean` has no literal type character or identifier type character.</span><span class="sxs-lookup"><span data-stu-id="75a95-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
- <span data-ttu-id="75a95-123">**Framework Type.**</span><span class="sxs-lookup"><span data-stu-id="75a95-123">**Framework Type.**</span></span> <span data-ttu-id="75a95-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span><span class="sxs-lookup"><span data-stu-id="75a95-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="75a95-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="75a95-125">Example</span></span>  

 <span data-ttu-id="75a95-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span><span class="sxs-lookup"><span data-stu-id="75a95-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="75a95-127">Viz také:</span><span class="sxs-lookup"><span data-stu-id="75a95-127">See also</span></span>

- <xref:System.Boolean?displayProperty=nameWithType>
- [<span data-ttu-id="75a95-128">Datové typy</span><span class="sxs-lookup"><span data-stu-id="75a95-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/index.md)
- [<span data-ttu-id="75a95-129">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="75a95-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)
- [<span data-ttu-id="75a95-130">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="75a95-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)
- [<span data-ttu-id="75a95-131">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="75a95-131">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="75a95-132">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="75a95-132">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="75a95-133">Funkce CType</span><span class="sxs-lookup"><span data-stu-id="75a95-133">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
