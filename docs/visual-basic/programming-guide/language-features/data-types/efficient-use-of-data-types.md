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
ms.openlocfilehash: 68371a9f8d4dcc5d0a2b67955d5e88943a83b085
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/30/2019
ms.locfileid: "68631104"
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="2898c-102">Účinné používání datových typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2898c-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="2898c-103">Nedeklarované proměnné a proměnné deklarované bez datového typu jsou přiřazeny k `Object` datovému typu.</span><span class="sxs-lookup"><span data-stu-id="2898c-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="2898c-104">To usnadňuje psaní programů rychleji, ale může způsobit pomalejší spouštění.</span><span class="sxs-lookup"><span data-stu-id="2898c-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>

## <a name="strong-typing"></a><span data-ttu-id="2898c-105">Silné zadání</span><span class="sxs-lookup"><span data-stu-id="2898c-105">Strong Typing</span></span>
 <span data-ttu-id="2898c-106">Zadání datových typů pro všechny proměnné se označuje jako *silné zadání*.</span><span class="sxs-lookup"><span data-stu-id="2898c-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="2898c-107">Použití silného psaní má několik výhod:</span><span class="sxs-lookup"><span data-stu-id="2898c-107">Using strong typing has several advantages:</span></span>

- <span data-ttu-id="2898c-108">Umožňuje podporu technologie IntelliSense pro vaše proměnné.</span><span class="sxs-lookup"><span data-stu-id="2898c-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="2898c-109">To umožňuje zobrazit jejich vlastnosti a další členy při psaní do kódu.</span><span class="sxs-lookup"><span data-stu-id="2898c-109">This allows you to see their properties and other members as you type in the code.</span></span>

- <span data-ttu-id="2898c-110">Využívá kontrolu typu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2898c-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="2898c-111">Tato zachycení příkazy, které mohou selhat v době běhu z důvodu chyb, jako je například přetečení.</span><span class="sxs-lookup"><span data-stu-id="2898c-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="2898c-112">Také zachytí volání metod pro objekty, které je nepodporují.</span><span class="sxs-lookup"><span data-stu-id="2898c-112">It also catches calls to methods on objects that do not support them.</span></span>

- <span data-ttu-id="2898c-113">Výsledkem je rychlejší provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="2898c-113">It results in faster execution of your code.</span></span>

## <a name="most-efficient-data-types"></a><span data-ttu-id="2898c-114">Nejúčinnější datové typy</span><span class="sxs-lookup"><span data-stu-id="2898c-114">Most Efficient Data Types</span></span>
 <span data-ttu-id="2898c-115">Pro proměnné, které nikdy neobsahují zlomky, jsou integrální datové typy efektivnější než Neceločíselné typy.</span><span class="sxs-lookup"><span data-stu-id="2898c-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="2898c-116">V Visual Basic `Integer` a `UInteger` jsou nejúčinnější číselné typy.</span><span class="sxs-lookup"><span data-stu-id="2898c-116">In Visual Basic, `Integer` and `UInteger` are the most efficient numeric types.</span></span>

 <span data-ttu-id="2898c-117">Pro zlomková čísla `Double` je nejúčinnější datový typ, protože procesory na současných platformách provádějí operace s plovoucí desetinnou čárkou s dvojitou přesností.</span><span class="sxs-lookup"><span data-stu-id="2898c-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="2898c-118">Operace s `Double` ale nejsou stejně rychlé jako u integrálních typů `Integer`, jako je.</span><span class="sxs-lookup"><span data-stu-id="2898c-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>

## <a name="specifying-data-type"></a><span data-ttu-id="2898c-119">Určení datového typu</span><span class="sxs-lookup"><span data-stu-id="2898c-119">Specifying Data Type</span></span>
 <span data-ttu-id="2898c-120">Použijte [příkaz Dim](../../../../visual-basic/language-reference/statements/dim-statement.md) k deklaraci proměnné konkrétního typu.</span><span class="sxs-lookup"><span data-stu-id="2898c-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="2898c-121">Úroveň přístupu můžete určit současně pomocí klíčového slova [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md)nebo [Private](../../../../visual-basic/language-reference/modifiers/private.md) , jak je uvedeno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2898c-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>

```vb
Private x As Double
Protected s As String
```

## <a name="character-conversion"></a><span data-ttu-id="2898c-122">Převod znaků</span><span class="sxs-lookup"><span data-stu-id="2898c-122">Character Conversion</span></span>
 <span data-ttu-id="2898c-123">Funkce `AscW` a`ChrW` fungují v kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="2898c-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="2898c-124">Měli byste je používat v předvolbách `Asc` a `Chr`, které se musí překládat do kódování Unicode a z něj.</span><span class="sxs-lookup"><span data-stu-id="2898c-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>

## <a name="see-also"></a><span data-ttu-id="2898c-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2898c-125">See also</span></span>

- <xref:Microsoft.VisualBasic.Strings.Asc%2A>
- <xref:Microsoft.VisualBasic.Strings.AscW%2A>
- <xref:Microsoft.VisualBasic.Strings.Chr%2A>
- <xref:Microsoft.VisualBasic.Strings.ChrW%2A>
- [<span data-ttu-id="2898c-126">Datové typy</span><span class="sxs-lookup"><span data-stu-id="2898c-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="2898c-127">Číselné datové typy</span><span class="sxs-lookup"><span data-stu-id="2898c-127">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)
- [<span data-ttu-id="2898c-128">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="2898c-128">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="2898c-129">Používání atributu IntelliSense</span><span class="sxs-lookup"><span data-stu-id="2898c-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
