---
title: "Účinné používání datových typů (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 0e13a1d61aacb06eb336c39aab969847127dfc67
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="efficient-use-of-data-types-visual-basic"></a><span data-ttu-id="e5259-102">Účinné používání datových typů (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e5259-102">Efficient Use of Data Types (Visual Basic)</span></span>
<span data-ttu-id="e5259-103">Nedeklarovaný proměnných a proměnných deklarovaných bez datový typ přiřazené `Object` datového typu.</span><span class="sxs-lookup"><span data-stu-id="e5259-103">Undeclared variables and variables declared without a data type are assigned the `Object` data type.</span></span> <span data-ttu-id="e5259-104">To umožňuje snadno vytvářet programy rychle, ale může to způsobit je provést pomaleji.</span><span class="sxs-lookup"><span data-stu-id="e5259-104">This makes it easy to write programs quickly, but it can cause them to execute more slowly.</span></span>  
  
## <a name="strong-typing"></a><span data-ttu-id="e5259-105">Silné typování</span><span class="sxs-lookup"><span data-stu-id="e5259-105">Strong Typing</span></span>  
 <span data-ttu-id="e5259-106">Určení typů dat pro všechny proměnné se označuje jako *silného typování*.</span><span class="sxs-lookup"><span data-stu-id="e5259-106">Specifying data types for all your variables is known as *strong typing*.</span></span> <span data-ttu-id="e5259-107">Používání silného typování má několik výhod:</span><span class="sxs-lookup"><span data-stu-id="e5259-107">Using strong typing has several advantages:</span></span>  
  
-   <span data-ttu-id="e5259-108">Umožňuje podporu technologie IntelliSense pro proměnných.</span><span class="sxs-lookup"><span data-stu-id="e5259-108">It enables IntelliSense support for your variables.</span></span> <span data-ttu-id="e5259-109">To umožňuje zobrazit jejich vlastnosti a ostatní členové jako typ v kódu.</span><span class="sxs-lookup"><span data-stu-id="e5259-109">This allows you to see their properties and other members as you type in the code.</span></span>  
  
-   <span data-ttu-id="e5259-110">Provádí se kontrola typu kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="e5259-110">It takes advantage of compiler type checking.</span></span> <span data-ttu-id="e5259-111">To zachytí příkazy, které může selhat v době běhu z důvodu chyby jako např. přetečení.</span><span class="sxs-lookup"><span data-stu-id="e5259-111">This catches statements that can fail at run time due to errors such as overflow.</span></span> <span data-ttu-id="e5259-112">Volání metody také zachytávalo na objekty, které je nepodporují.</span><span class="sxs-lookup"><span data-stu-id="e5259-112">It also catches calls to methods on objects that do not support them.</span></span>  
  
-   <span data-ttu-id="e5259-113">Výsledkem rychlejší provádění kódu.</span><span class="sxs-lookup"><span data-stu-id="e5259-113">It results in faster execution of your code.</span></span>  
  
## <a name="most-efficient-data-types"></a><span data-ttu-id="e5259-114">Nejúčinnější datové typy</span><span class="sxs-lookup"><span data-stu-id="e5259-114">Most Efficient Data Types</span></span>  
 <span data-ttu-id="e5259-115">Pro proměnné, které nikdy nesmí obsahovat zlomků jsou efektivnější než nonintegral typy integrální datové typy.</span><span class="sxs-lookup"><span data-stu-id="e5259-115">For variables that never contain fractions, the integral data types are more efficient than the nonintegral types.</span></span> <span data-ttu-id="e5259-116">V [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], `Integer` a `UInteger` jsou nejúčinnější číselnými typy.</span><span class="sxs-lookup"><span data-stu-id="e5259-116">In [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)], `Integer` and `UInteger` are the most efficient numeric types.</span></span>  
  
 <span data-ttu-id="e5259-117">Pro desetinná čísla `Double` je nejúčinnější datového typu, protože procesory na aktuální platformy provádět operace s plovoucí desetinnou čárkou v dvojitou přesností.</span><span class="sxs-lookup"><span data-stu-id="e5259-117">For fractional numbers, `Double` is the most efficient data type, because the processors on current platforms perform floating-point operations in double precision.</span></span> <span data-ttu-id="e5259-118">Ale operací s `Double` nejsou tak rychlý jako u celočíselných typů jako `Integer`.</span><span class="sxs-lookup"><span data-stu-id="e5259-118">However, operations with `Double` are not as fast as with the integral types such as `Integer`.</span></span>  
  
## <a name="specifying-data-type"></a><span data-ttu-id="e5259-119">Určení datový typ</span><span class="sxs-lookup"><span data-stu-id="e5259-119">Specifying Data Type</span></span>  
 <span data-ttu-id="e5259-120">Použití [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md) deklarovat proměnnou určitého typu.</span><span class="sxs-lookup"><span data-stu-id="e5259-120">Use the [Dim Statement](../../../../visual-basic/language-reference/statements/dim-statement.md) to declare a variable of a specific type.</span></span> <span data-ttu-id="e5259-121">Současně můžete zadat jeho úroveň přístupu pomocí [veřejné](../../../../visual-basic/language-reference/modifiers/public.md), [chráněné](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), nebo [privátní](../../../../visual-basic/language-reference/modifiers/private.md) – klíčové slovo, jako v Následující příklad.</span><span class="sxs-lookup"><span data-stu-id="e5259-121">You can simultaneously specify its access level by using the [Public](../../../../visual-basic/language-reference/modifiers/public.md), [Protected](../../../../visual-basic/language-reference/modifiers/protected.md), [Friend](../../../../visual-basic/language-reference/modifiers/friend.md), or [Private](../../../../visual-basic/language-reference/modifiers/private.md) keyword, as in the following example.</span></span>  
  
```  
Private x As Double  
Protected s As String  
```  
  
## <a name="character-conversion"></a><span data-ttu-id="e5259-122">Převod znaků</span><span class="sxs-lookup"><span data-stu-id="e5259-122">Character Conversion</span></span>  
 <span data-ttu-id="e5259-123">`AscW` a `ChrW` funkce pracovat v kódu Unicode.</span><span class="sxs-lookup"><span data-stu-id="e5259-123">The `AscW` and `ChrW` functions operate in Unicode.</span></span> <span data-ttu-id="e5259-124">Používejte je preference do `Asc` a `Chr`, které musí překládat do a z kódování Unicode.</span><span class="sxs-lookup"><span data-stu-id="e5259-124">You should use them in preference to `Asc` and `Chr`, which must translate into and out of Unicode.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e5259-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5259-125">See Also</span></span>  
 <xref:Microsoft.VisualBasic.Strings.Asc%2A>  
 <xref:Microsoft.VisualBasic.Strings.AscW%2A>  
 <xref:Microsoft.VisualBasic.Strings.Chr%2A>  
 <xref:Microsoft.VisualBasic.Strings.ChrW%2A>  
 [<span data-ttu-id="e5259-126">Datové typy</span><span class="sxs-lookup"><span data-stu-id="e5259-126">Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/index.md)  
 [<span data-ttu-id="e5259-127">Číselné datové typy</span><span class="sxs-lookup"><span data-stu-id="e5259-127">Numeric Data Types</span></span>](../../../../visual-basic/programming-guide/language-features/data-types/numeric-data-types.md)  
 [<span data-ttu-id="e5259-128">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="e5259-128">Variable Declaration</span></span>](../../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)  
 [<span data-ttu-id="e5259-129">Používání atributu IntelliSense</span><span class="sxs-lookup"><span data-stu-id="e5259-129">Using IntelliSense</span></span>](/visualstudio/ide/using-intellisense)
