---
title: "Návratové hodnoty REF (Visual Basic)"
ms.custom: 
ms.date: 04/28/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- variables [Visual Basic]
- ref return values [Visual Basic]
- ref returns [Visual Basic]
ms.assetid: 5ef0cc69-eb3a-4a67-92a2-78585f223cb5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 560607f7aa304b25314daabeef3952e6bbef7426
ms.sourcegitcommit: 7e99f66ef09d2903e22c789c67ff5a10aa953b2f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/18/2017
---
# <a name="support-for-reference-return-values-visual-basic"></a><span data-ttu-id="4d12c-102">Podpora pro odkaz návratové hodnoty (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="4d12c-102">Support for reference return values (Visual Basic)</span></span>

<span data-ttu-id="4d12c-103">Od verze jazyka C# 7, podporuje jazyka C# *odkazovat návratové hodnoty*.</span><span class="sxs-lookup"><span data-stu-id="4d12c-103">Starting with C# 7, the C# language supports *reference return values*.</span></span> <span data-ttu-id="4d12c-104">Jeden způsob, jak pochopit návratové hodnoty odkazu je, že jsou opak argumenty, které se předávají pomocí odkazu na třídu metodě.</span><span class="sxs-lookup"><span data-stu-id="4d12c-104">One way to understand reference return values is that they are the opposite of arguments that are passed by reference to a method.</span></span> <span data-ttu-id="4d12c-105">Při úpravě argument předaný odkazem změny se projeví v hodnotu proměnné na volajícího.</span><span class="sxs-lookup"><span data-stu-id="4d12c-105">When an argument passed by reference is modified, the changes are reflected in value of the variable on the caller.</span></span> <span data-ttu-id="4d12c-106">Při metodu návratovou hodnotu odkazu poskytne volající, změny provedené návratovou hodnotu odkazu volající projeví v datech zavolat metodu.</span><span class="sxs-lookup"><span data-stu-id="4d12c-106">When an method provides a reference return value to a caller, modifications made to the reference return value by the caller are reflected in the called method's data.</span></span>

<span data-ttu-id="4d12c-107">Vám autor metody s odkazem na návratové hodnoty, ale neumožňuje můžete využívat návratové hodnoty referenční dokumentace jazyka Visual Basic není povoleno.</span><span class="sxs-lookup"><span data-stu-id="4d12c-107">Visual Basic does not allow you to author methods with reference return values, but it does allow you to consume reference return values.</span></span> <span data-ttu-id="4d12c-108">Jinými slovy můžete volat metodu s návratovou hodnotou odkaz a upravit že návratová hodnota a změny návratovou hodnotu odkazu se projeví v datech zavolat metodu.</span><span class="sxs-lookup"><span data-stu-id="4d12c-108">In other words, you can call a method with a reference return value and modify that return value, and changes to the reference return value are reflected in the called method's data.</span></span>

## <a name="modifying-the-ref-return-value-directly"></a><span data-ttu-id="4d12c-109">Návratové hodnoty ref přímém upravování</span><span class="sxs-lookup"><span data-stu-id="4d12c-109">Modifying the ref return value directly</span></span>

<span data-ttu-id="4d12c-110">Pro metody, které vždy úspěšné a mají ne `ByRef` parametry, můžete upravit přímo návratovou hodnotu odkazu.</span><span class="sxs-lookup"><span data-stu-id="4d12c-110">For methods that always succeed and have no `ByRef` parameters, you can modify the reference return value directly.</span></span> <span data-ttu-id="4d12c-111">To provedete přiřazením nová hodnota výrazů, které vrátí odkaz na návratovou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4d12c-111">You do this by assigning the new value to the expressions that returns the reference return value.</span></span> 

<span data-ttu-id="4d12c-112">Definuje následující příklad jazyka C# `NumericValue.IncrementValue` metodu, která zvýší interní hodnotu a vrátí ji jako odkaz vrátit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4d12c-112">The following C# example defines a `NumericValue.IncrementValue` method that increments an internal value and returns it as a reference return value.</span></span> 

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/ref-returns1.cs)]

<span data-ttu-id="4d12c-113">Odkaz na návratové hodnoty je pak upraveném volající v následujícím příkladu jazyka Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="4d12c-113">The reference return value is then modified by the caller in the following Visual Basic example.</span></span> <span data-ttu-id="4d12c-114">Všimněte si, že souladu se zásadami `NumericValue.IncrementValue` volání metody nepřiřazuje hodnotu do metody.</span><span class="sxs-lookup"><span data-stu-id="4d12c-114">Note that the line with the `NumericValue.IncrementValue` method call does not assign a value to the method.</span></span> <span data-ttu-id="4d12c-115">Místo toho přiřadí hodnotu vrácenou hodnotu odkazu vrácený metodou.</span><span class="sxs-lookup"><span data-stu-id="4d12c-115">Instead, it assigns a value to the reference return value returned by the method.</span></span>

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/programming-guide/language-features/procedures/use-ref-returns1.vb)]

## <a name="using-a-helper-method"></a><span data-ttu-id="4d12c-116">Pomocí Pomocná metoda</span><span class="sxs-lookup"><span data-stu-id="4d12c-116">Using a helper method</span></span>

<span data-ttu-id="4d12c-117">V ostatních případech přímém upravování odkaz návratovou hodnotu volání metody nemusí být vždy žádoucí.</span><span class="sxs-lookup"><span data-stu-id="4d12c-117">In other cases, modifying the reference return value of a method call directly may not always be desirable.</span></span> <span data-ttu-id="4d12c-118">Například metoda vyhledávání, která vrací řetězec nemusí vždy najít shodu.</span><span class="sxs-lookup"><span data-stu-id="4d12c-118">For example, a search method that returns a string may not always find a match.</span></span> <span data-ttu-id="4d12c-119">V takovém případě budete chtít upravit návratovou hodnotu odkazu pouze v případě, že je hledání úspěšné.</span><span class="sxs-lookup"><span data-stu-id="4d12c-119">In that case, you want to modify the reference return value only if the search is successful.</span></span>

<span data-ttu-id="4d12c-120">Následující příklad jazyka C# znázorňuje tento scénář.</span><span class="sxs-lookup"><span data-stu-id="4d12c-120">The following C# example illustrates this scenario.</span></span> <span data-ttu-id="4d12c-121">Definuje `Sentence` zahrnuje třídy, které jsou napsané v C# `FindNext` metoda, která vyhledá další aplikace word ve větě, která začíná je určený dílčí řetězec.</span><span class="sxs-lookup"><span data-stu-id="4d12c-121">It defines a `Sentence` class written in C# includes a `FindNext` method that finds the next word in a sentence that begins with a specified substring.</span></span> <span data-ttu-id="4d12c-122">Řetězec se vrátí jako odkaz vrátí hodnotu a `Boolean` předaná odkazu na metodu proměnná Určuje, zda byla hledání úspěšné.</span><span class="sxs-lookup"><span data-stu-id="4d12c-122">The string is returned as a reference return value, and a `Boolean` variable passed by reference to the method indicates whether the search was successful.</span></span> <span data-ttu-id="4d12c-123">Návratovou hodnotu odkazu označuje volající nelze číst jenom vrácená hodnota; potvrdí také ho upravit, a že změna se odrazí v data obsažená v interně `Sentence` třídy.</span><span class="sxs-lookup"><span data-stu-id="4d12c-123">The reference return value indicates that the caller can not only read the returned value; he or she can also modify it, and that modification is reflected in the data contained internally in the `Sentence` class.</span></span>

[!code-csharp[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-returns.cs)]

<span data-ttu-id="4d12c-124">Hodnota v tomto případě není spolehlivá, protože volání metody, které může selhat pro vyhledání shody a vrácení první slovo ve větě přímou úpravou odkaz na vrácení.</span><span class="sxs-lookup"><span data-stu-id="4d12c-124">Directly modifying the reference return value in this case is not reliable, since the method call may fail to find a match and return the first word in the sentence.</span></span> <span data-ttu-id="4d12c-125">V takovém případě volající upraví nechtěně první slovo věty.</span><span class="sxs-lookup"><span data-stu-id="4d12c-125">In that case, the caller will inadvertently modify the first word of the sentence.</span></span> <span data-ttu-id="4d12c-126">To může zabránit volající vrácení `null` (nebo `Nothing` v jazyce Visual Basic).</span><span class="sxs-lookup"><span data-stu-id="4d12c-126">This could be prevented by the caller returning a `null` (or `Nothing` in Visual Basic).</span></span> <span data-ttu-id="4d12c-127">Ale v takovém případě se pokouší změnit řetězec, jehož hodnota je `Nothing` vyvolá <xref:System.NullReferenceException>.</span><span class="sxs-lookup"><span data-stu-id="4d12c-127">But in that case, attempting to modify a string whose value is `Nothing` throws a <xref:System.NullReferenceException>.</span></span> <span data-ttu-id="4d12c-128">Pokud může také možné volající vrácení <xref:System.String.Empty?displayProperty=nameWithType>, ale to vyžaduje, aby volající definujte proměnnou řetězec, jehož hodnota je <xref:System.String.Empty?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="4d12c-128">If could also be prevented by the caller returning <xref:System.String.Empty?displayProperty=nameWithType>, but this requires that the caller define a string variable whose value is <xref:System.String.Empty?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4d12c-129">Při volající můžete upravit tento řetězec, úpravy samotné slouží žádný účel, protože upravené řetězec nemá žádný vztah k slova ve větě uložené `Sentence` třídy.</span><span class="sxs-lookup"><span data-stu-id="4d12c-129">While the caller can modify that string, the modification itself serves no purpose, since the modified string has no relationship to the words in the sentence stored by the `Sentence` class.</span></span>

<span data-ttu-id="4d12c-130">Nejlepší způsob, jak u tohoto scénáře je předat návratovou hodnotu odkazu s odkazem na metodu helper.</span><span class="sxs-lookup"><span data-stu-id="4d12c-130">The best way to handle this scenario is to pass the reference return value by reference to a helper method.</span></span> <span data-ttu-id="4d12c-131">Pomocná metoda poté obsahuje logiku pro určení, zda bylo úspěšné volání metody, a pokud neodpovídala, k úpravě vrátí odkaz na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="4d12c-131">The helper method then contains the logic to determine whether the method call succeeded and, if it did, to modify the reference return value.</span></span> <span data-ttu-id="4d12c-132">Následující příklad uvádí možné implementace.</span><span class="sxs-lookup"><span data-stu-id="4d12c-132">The following example provides a possible implementation.</span></span>

[!code-vb[Ref-Return](../../../../../samples/snippets/visualbasic/getting-started/ref-return-helper.vb#1)]

## <a name="see-also"></a><span data-ttu-id="4d12c-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="4d12c-133">See also</span></span>

<span data-ttu-id="4d12c-134">[Předávání argumentů podle hodnoty a podle reference](passing-arguments-by-value-and-by-reference.md) </span><span class="sxs-lookup"><span data-stu-id="4d12c-134">[Passing arguments by value and by reference](passing-arguments-by-value-and-by-reference.md) </span></span>  
[<span data-ttu-id="4d12c-135">Procedury v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="4d12c-135">Procedures in Visual Basic</span></span>](index.md)   


