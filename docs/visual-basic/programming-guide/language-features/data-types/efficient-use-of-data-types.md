---
title: Účinné používání datových typů (Visual Basic)
ms.date: 07/20/2015
helpviewer_keywords:
- performance, data type efficiency
- data types [Visual Basic], weak typing
- AscW function [Visual Basic], preferred to Asc
- data types [Visual Basic], using efficiently
- optimization [Visual Basic], data types
- data types [Visual Basic], strong typing
- strong typing
- typing, strong
- data types [Visual Basic], optimizing
- ChrW function [Visual Basic], preferred to Chr
ms.assetid: 28f5e4ba-ec24-4f37-b90a-e8ee822f778a
ms.openlocfilehash: 0b517bca3a9e296eb891e30df91c1d32eb357432
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58830120"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="ba252-102">Účinné používání datových typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ba252-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="ba252-103">Jsou přiřazeny nedeklarované proměnné a proměnné deklarované bez datový typ `Object` datového typu.</span><span class="sxs-lookup"><span data-stu-id="ba252-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="ba252-104">To usnadňuje psaní programů rychle, ale může to způsobit je ke spuštění pomaleji.</span><span class="sxs-lookup"><span data-stu-id="ba252-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>  
  
## <a name="strong-typing"></a><span data-ttu-id="ba252-105">Silné typování</span><span class="sxs-lookup"><span data-stu-id="ba252-105">Strong Typing</span></span>  
 <span data-ttu-id="ba252-106">Určení typů dat pro všechny proměnné se označuje jako *silné typování*.</span><span class="sxs-lookup"><span data-stu-id="ba252-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="ba252-107">Pomocí silných typů má několik výhod:</span><span class="sxs-lookup"><span data-stu-id="ba252-107">Using strong typing has several advantages:</span></span>  
  
-   <span data-ttu-id="ba252-108">Umožňuje podporu technologie IntelliSense pro proměnných.</span><span class="sxs-lookup"><span data-stu-id="ba252-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="ba252-109">To umožňuje zobrazit jejich vlastnosti a ostatní členové při psaní v kódu.</span><span class="sxs-lookup"><span data-stu-id="ba252-109">This allows you to see their properties and other members as you type in the code.</span></span>  
  
-   <span data-ttu-id="ba252-110">Využívá kontrola typu v kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="ba252-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="ba252-111">To zachycuje příkazy, které může selhat v době běhu z důvodu chyby jako např. přetečení.</span><span class="sxs-lookup"><span data-stu-id="ba252-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="ba252-112">Také zachytí volání metod na objekty, které je nepodporují.</span><span class="sxs-lookup"><span data-stu-id="ba252-112">It also catches calls to methods on objects that do not support them.</span></span>  
  
-   <span data-ttu-id="ba252-113">To má za následek rychlejší provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="ba252-113">It results in faster execution of your code.</span></span>  
  
## <a name="most-efficient-data-types"></a><span data-ttu-id="ba252-114">Nejúčinnější datové typy</span><span class="sxs-lookup"><span data-stu-id="ba252-114">Most Efficient Data Types</span></span>  
 <span data-ttu-id="ba252-115">Pro proměnné, které obsahují nikdy zlomky jsou účinnější než nonintegral typy celočíselnými datovými typy.</span><span class="sxs-lookup"><span data-stu-id="ba252-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="ba252-116">V jazyce Visual Basic `Integer` a `UInteger` nejúčinnější číselné typy.</span><span class="sxs-lookup"><span data-stu-id="ba252-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>  
  
 <span data-ttu-id="ba252-117">Pro desetinná čísla `Double` je nejúčinnější datového typu, protože procesory na aktuální platformy provádět operace s plovoucí desetinnou čárkou v dvojité přesnosti.</span><span class="sxs-lookup"><span data-stu-id="ba252-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="ba252-118">Nicméně operace s `Double` nejsou tak rychle, stejně jako u celočíselných typů, jako `Integer`.</span><span class="sxs-lookup"><span data-stu-id="ba252-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
## <a name="specifying-data-type"></a><span data-ttu-id="ba252-119">Určení datového typu</span><span class="sxs-lookup"><span data-stu-id="ba252-119">Specifying Data Type</span></span>  
 <span data-ttu-id="ba252-120">Použití [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) k deklaraci proměnné určitého typu.</span><span class="sxs-lookup"><span data-stu-id="ba252-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="ba252-121">Najednou můžete zadat jeho úroveň přístupu s použitím [veřejné](../../../../visual-basic/language-reference/modifiers/public.md), [chráněné](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), nebo [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo, jako v Následující příklad.</span><span class="sxs-lookup"><span data-stu-id="ba252-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a><span data-ttu-id="ba252-122">Převod znaků</span><span class="sxs-lookup"><span data-stu-id="ba252-122">Character Conversion</span></span>  
 <span data-ttu-id="ba252-123">`AscW` a `ChrW` funkce pracují v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="ba252-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="ba252-124">Jejich preference pro použití `Asc` a `Chr`, které musí překládat do proměnné a z kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="ba252-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba252-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ba252-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="ba252-126">Datové typy</span><span class="sxs-lookup"><span data-stu-id="ba252-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="ba252-127">Číselné datové typy</span><span class="sxs-lookup"><span data-stu-id="ba252-127">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [<span data-ttu-id="ba252-128">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="ba252-128">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="ba252-129">Používání atributu IntelliSense</span><span class="sxs-lookup"><span data-stu-id="ba252-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
