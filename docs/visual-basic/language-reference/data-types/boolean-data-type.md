---
title: "Boolean – datový typ (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "18"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: bdc106f1ec874c1a2165df069d5f3485fe5b2e43
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="a3b6b-102">Boolean – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a3b6b-102">Boolean Data Type (Visual Basic)</span></span>
<span data-ttu-id="a3b6b-103">Blokování hodnoty, které může být pouze `True` nebo `False`.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="a3b6b-104">Klíčová slova `True` a `False` odpovídají dva stavy `Boolean` proměnné.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="a3b6b-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="a3b6b-105">Remarks</span></span>  
 <span data-ttu-id="a3b6b-106">Použití [logický datový typ (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) tak, aby obsahovala hodnoty dvou stavů například true nebo false, Ano/Ne, nebo zapnutí nebo vypnutí.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-106">Use the [Boolean Data Type (Visual Basic)](../../../visual-basic/language-reference/data-types/boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="a3b6b-107">Výchozí hodnota `Boolean` je `False`.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="a3b6b-108">`Boolean`hodnoty nejsou uložené jako čísla a uložené hodnoty nejsou určeny jako ekvivalentní na čísla.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="a3b6b-109">Nikdy byste měli zapsat kód, který závisí na ekvivalentní číselné hodnoty pro `True` a `False`.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="a3b6b-110">Kdykoli je to možné, měli byste omezit využití `Boolean` proměnné logické hodnoty, pro které jsou navrženy.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="a3b6b-111">Převody typu</span><span class="sxs-lookup"><span data-stu-id="a3b6b-111">Type Conversions</span></span>  
 <span data-ttu-id="a3b6b-112">Když jazyka Visual Basic převádí hodnoty číselný datový typ pro `Boolean`, stane 0 `False` a všechny ostatní hodnoty přestat `True`.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="a3b6b-113">Když Visual Basic převede `Boolean` hodnot na číselné typy `False` se změní na 0 a `True` se změní na hodnotu -1.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="a3b6b-114">Při převodu mezi `Boolean` hodnoty a číselné datové typy, mějte na paměti, že conversion metod rozhraní .NET Framework vždy nevedou stejné výsledky jako klíčová slova převodu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="a3b6b-115">To je proto, že conversion jazyka Visual Basic uchovává chování, které jsou kompatibilní s předchozími verzemi.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="a3b6b-116">Další informace najdete v tématu "Logický typ nemá není převést na číselný typ přesně" v [řešení potíží s datovými typy](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="a3b6b-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="a3b6b-117">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="a3b6b-117">Programming Tips</span></span>  
  
-   <span data-ttu-id="a3b6b-118">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="a3b6b-118">**Negative Numbers.**</span></span> <span data-ttu-id="a3b6b-119">`Boolean`není číselného typu a nesmí představovat zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="a3b6b-120">V každém případě byste neměli používat `Boolean` pro uložení číselné hodnoty.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
-   <span data-ttu-id="a3b6b-121">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="a3b6b-121">**Type Characters.**</span></span> <span data-ttu-id="a3b6b-122">`Boolean`nemá žádnou – znak typu literálu nebo – znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
-   <span data-ttu-id="a3b6b-123">**Typ Framework.**</span><span class="sxs-lookup"><span data-stu-id="a3b6b-123">**Framework Type.**</span></span> <span data-ttu-id="a3b6b-124">Typ odpovídající v rozhraní .NET Framework je <xref:System.Boolean?displayProperty=nameWithType> struktura.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a3b6b-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="a3b6b-125">Example</span></span>  
 <span data-ttu-id="a3b6b-126">V následujícím příkladu `runningVB` je `Boolean` proměnné, která ukládá jednoduché nastavení Ano/Ne.</span><span class="sxs-lookup"><span data-stu-id="a3b6b-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="a3b6b-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="a3b6b-127">See Also</span></span>  
 <xref:System.Boolean?displayProperty=nameWithType>  
 [<span data-ttu-id="a3b6b-128">Datové typy</span><span class="sxs-lookup"><span data-stu-id="a3b6b-128">Data Types</span></span>](../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [<span data-ttu-id="a3b6b-129">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="a3b6b-129">Type Conversion Functions</span></span>](../../../visual-basic/language-reference/functions/type-conversion-functions.md)  
 [<span data-ttu-id="a3b6b-130">Souhrn konverze</span><span class="sxs-lookup"><span data-stu-id="a3b6b-130">Conversion Summary</span></span>](../../../visual-basic/language-reference/keywords/conversion-summary.md)  
 [<span data-ttu-id="a3b6b-131">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="a3b6b-131">Efficient Use of Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/efficient-use-of-data-types.md)  
 [<span data-ttu-id="a3b6b-132">Řešení potíží s datové typy</span><span class="sxs-lookup"><span data-stu-id="a3b6b-132">Troubleshooting Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/troubleshooting-data-types.md)  
 [<span data-ttu-id="a3b6b-133">CType – funkce</span><span class="sxs-lookup"><span data-stu-id="a3b6b-133">CType Function</span></span>](../../../visual-basic/language-reference/functions/ctype-function.md)
