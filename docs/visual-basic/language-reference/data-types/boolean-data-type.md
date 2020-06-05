---
title: Boolean – datový typ
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
ms.openlocfilehash: 851c524a83c5f24b77a151634a96798249c5905e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84374418"
---
# <a name="boolean-data-type-visual-basic"></a><span data-ttu-id="ffb69-102">Boolean – datový typ (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ffb69-102">Boolean Data Type (Visual Basic)</span></span>

<span data-ttu-id="ffb69-103">Obsahuje hodnoty, které mohou být pouze `True` nebo `False` .</span><span class="sxs-lookup"><span data-stu-id="ffb69-103">Holds values that can be only `True` or `False`.</span></span> <span data-ttu-id="ffb69-104">Klíčová slova `True` a `False` odpovídají dvěma stavům `Boolean` proměnných.</span><span class="sxs-lookup"><span data-stu-id="ffb69-104">The keywords `True` and `False` correspond to the two states of `Boolean` variables.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ffb69-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ffb69-105">Remarks</span></span>  

 <span data-ttu-id="ffb69-106">Použijte [datový typ Boolean (Visual Basic)](boolean-data-type.md) k tomu, aby obsahovala hodnoty se dvěma stavy, jako je true/false, ano/ne nebo zapnuto/vypnuto.</span><span class="sxs-lookup"><span data-stu-id="ffb69-106">Use the [Boolean Data Type (Visual Basic)](boolean-data-type.md) to contain two-state values such as true/false, yes/no, or on/off.</span></span>  
  
 <span data-ttu-id="ffb69-107">Výchozí hodnota `Boolean` je `False` .</span><span class="sxs-lookup"><span data-stu-id="ffb69-107">The default value of `Boolean` is `False`.</span></span>  
  
 <span data-ttu-id="ffb69-108">`Boolean`hodnoty nejsou uloženy jako čísla a uložené hodnoty nejsou určeny pro ekvivalent čísel.</span><span class="sxs-lookup"><span data-stu-id="ffb69-108">`Boolean` values are not stored as numbers, and the stored values are not intended to be equivalent to numbers.</span></span> <span data-ttu-id="ffb69-109">Nikdy byste neměli psát kód, který spoléhá na ekvivalentní číselné hodnoty pro `True` a `False` .</span><span class="sxs-lookup"><span data-stu-id="ffb69-109">You should never write code that relies on equivalent numeric values for `True` and `False`.</span></span> <span data-ttu-id="ffb69-110">Kdykoli je to možné, měli byste omezit použití `Boolean` proměnných na logické hodnoty, pro které jsou navrženy.</span><span class="sxs-lookup"><span data-stu-id="ffb69-110">Whenever possible, you should restrict usage of `Boolean` variables to the logical values for which they are designed.</span></span>  
  
## <a name="type-conversions"></a><span data-ttu-id="ffb69-111">Převody typu</span><span class="sxs-lookup"><span data-stu-id="ffb69-111">Type Conversions</span></span>  

 <span data-ttu-id="ffb69-112">Když Visual Basic převede hodnoty číselného datového typu na, vrátí se `Boolean` 0 a zobrazí se `False` všechny ostatní hodnoty `True` .</span><span class="sxs-lookup"><span data-stu-id="ffb69-112">When Visual Basic converts numeric data type values to `Boolean`, 0 becomes `False` and all other values become `True`.</span></span> <span data-ttu-id="ffb69-113">Když Visual Basic převede `Boolean` hodnoty na číselné typy, `False` změní se na 0 a `True` změní se na 1.</span><span class="sxs-lookup"><span data-stu-id="ffb69-113">When Visual Basic converts `Boolean` values to numeric types, `False` becomes 0 and `True` becomes -1.</span></span>  
  
 <span data-ttu-id="ffb69-114">Pokud převedete mezi `Boolean` hodnotami a číselnými datovými typy, pamatujte, že metody převodu .NET Framework nevytváří vždy stejné výsledky jako klíčová slova převodu Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="ffb69-114">When you convert between `Boolean` values and numeric data types, keep in mind that the .NET Framework conversion methods do not always produce the same results as the Visual Basic conversion keywords.</span></span> <span data-ttu-id="ffb69-115">Důvodem je to, že převod Visual Basic zachovává chování kompatibilní s předchozími verzemi.</span><span class="sxs-lookup"><span data-stu-id="ffb69-115">This is because the Visual Basic conversion retains behavior compatible with previous versions.</span></span> <span data-ttu-id="ffb69-116">Další informace naleznete v tématu "logický typ nepřeváděný na číselný typ přesně" v článku [řešení potíží s datovými typy](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span><span class="sxs-lookup"><span data-stu-id="ffb69-116">For more information, see "Boolean Type Does Not Convert to Numeric Type Accurately" in [Troubleshooting Data Types](../../programming-guide/language-features/data-types/troubleshooting-data-types.md).</span></span>  
  
## <a name="programming-tips"></a><span data-ttu-id="ffb69-117">Tipy k programování</span><span class="sxs-lookup"><span data-stu-id="ffb69-117">Programming Tips</span></span>  
  
- <span data-ttu-id="ffb69-118">**Záporná čísla.**</span><span class="sxs-lookup"><span data-stu-id="ffb69-118">**Negative Numbers.**</span></span> <span data-ttu-id="ffb69-119">`Boolean`není numerický typ a nemůže představovat zápornou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ffb69-119">`Boolean` is not a numeric type and cannot represent a negative value.</span></span> <span data-ttu-id="ffb69-120">V žádném případě byste neměli používat `Boolean` k ukládání číselných hodnot.</span><span class="sxs-lookup"><span data-stu-id="ffb69-120">In any case, you should not use `Boolean` to hold numeric values.</span></span>  
  
- <span data-ttu-id="ffb69-121">**Znaky typu.**</span><span class="sxs-lookup"><span data-stu-id="ffb69-121">**Type Characters.**</span></span> <span data-ttu-id="ffb69-122">`Boolean`nemá žádný znak typu literálu nebo znak typu identifikátoru.</span><span class="sxs-lookup"><span data-stu-id="ffb69-122">`Boolean` has no literal type character or identifier type character.</span></span>  
  
- <span data-ttu-id="ffb69-123">**Typ rozhraní.**</span><span class="sxs-lookup"><span data-stu-id="ffb69-123">**Framework Type.**</span></span> <span data-ttu-id="ffb69-124">Odpovídající typ v .NET Framework je <xref:System.Boolean?displayProperty=nameWithType> Struktura.</span><span class="sxs-lookup"><span data-stu-id="ffb69-124">The corresponding type in the .NET Framework is the <xref:System.Boolean?displayProperty=nameWithType> structure.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ffb69-125">Příklad</span><span class="sxs-lookup"><span data-stu-id="ffb69-125">Example</span></span>  

 <span data-ttu-id="ffb69-126">V následujícím příkladu `runningVB` je `Boolean` Proměnná, která ukládá jednoduché nastavení ano/ne.</span><span class="sxs-lookup"><span data-stu-id="ffb69-126">In the following example, `runningVB` is a `Boolean` variable, which stores a simple yes/no setting.</span></span>  
  
```vb  
Dim runningVB As Boolean  
' Check to see if program is running on Visual Basic engine.  
If scriptEngine = "VB" Then  
    runningVB = True  
End If  
```  
  
## <a name="see-also"></a><span data-ttu-id="ffb69-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="ffb69-127">See also</span></span>

- <xref:System.Boolean?displayProperty=nameWithType>
- [<span data-ttu-id="ffb69-128">Datové typy</span><span class="sxs-lookup"><span data-stu-id="ffb69-128">Data Types</span></span>](index.md)
- [<span data-ttu-id="ffb69-129">Funkce pro převod typů</span><span class="sxs-lookup"><span data-stu-id="ffb69-129">Type Conversion Functions</span></span>](../functions/type-conversion-functions.md)
- [<span data-ttu-id="ffb69-130">Souhrn převodu</span><span class="sxs-lookup"><span data-stu-id="ffb69-130">Conversion Summary</span></span>](../keywords/conversion-summary.md)
- [<span data-ttu-id="ffb69-131">Účinné používání datových typů</span><span class="sxs-lookup"><span data-stu-id="ffb69-131">Efficient Use of Data Types</span></span>](../../programming-guide/language-features/data-types/efficient-use-of-data-types.md)
- [<span data-ttu-id="ffb69-132">Řešení potíží s datovými typy</span><span class="sxs-lookup"><span data-stu-id="ffb69-132">Troubleshooting Data Types</span></span>](../../programming-guide/language-features/data-types/troubleshooting-data-types.md)
- [<span data-ttu-id="ffb69-133">CType – funkce</span><span class="sxs-lookup"><span data-stu-id="ffb69-133">CType Function</span></span>](../functions/ctype-function.md)
