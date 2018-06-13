---
title: Anonymní metody (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- anonymous methods [C#]
- methods [C#], anonymous
- delegates [C#], anonymous methods
ms.assetid: a62441fa-f0a3-4acb-9aa6-93762a635275
ms.openlocfilehash: 7f6c596dcc73cdfb335071f57aab18e836ceaae8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33338419"
---
# <a name="anonymous-methods-c-programming-guide"></a><span data-ttu-id="be5d3-102">Anonymní metody (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="be5d3-102">Anonymous Methods (C# Programming Guide)</span></span>
<span data-ttu-id="be5d3-103">Ve verzi jazyka C# před 2.0, lze deklarovat pouze [delegovat](../../../csharp/language-reference/keywords/delegate.md) pomocí [s názvem metody](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span><span class="sxs-lookup"><span data-stu-id="be5d3-103">In versions of C# before 2.0, the only way to declare a [delegate](../../../csharp/language-reference/keywords/delegate.md) was to use [named methods](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md).</span></span> <span data-ttu-id="be5d3-104">C# 2.0 zavedená anonymní metody a v C# 3.0 nebo novější, výrazů lambda jako upřednostňovaný způsob, jak napsat kód vložený mají přednost před anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="be5d3-104">C# 2.0 introduced anonymous methods and in C# 3.0 and later, lambda expressions supersede anonymous methods as the preferred way to write inline code.</span></span> <span data-ttu-id="be5d3-105">Ale informace o anonymní metody v tomto tématu platí taky pro výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="be5d3-105">However, the information about anonymous methods in this topic also applies to lambda expressions.</span></span> <span data-ttu-id="be5d3-106">Neexistuje jeden případ, ve kterém anonymní metoda poskytuje funkce nebyla nalezena v výrazy lambda.</span><span class="sxs-lookup"><span data-stu-id="be5d3-106">There is one case in which an anonymous method provides functionality not found in lambda expressions.</span></span> <span data-ttu-id="be5d3-107">Anonymní metody umožňují vynechejte parametr seznamu.</span><span class="sxs-lookup"><span data-stu-id="be5d3-107">Anonymous methods enable you to omit the parameter list.</span></span> <span data-ttu-id="be5d3-108">To znamená, že anonymní metody lze převést na delegáty s různými podpisy.</span><span class="sxs-lookup"><span data-stu-id="be5d3-108">This means that an anonymous method can be converted to delegates with a variety of signatures.</span></span> <span data-ttu-id="be5d3-109">To není možné pomocí výrazů lambda.</span><span class="sxs-lookup"><span data-stu-id="be5d3-109">This is not possible with lambda expressions.</span></span> <span data-ttu-id="be5d3-110">Další informace o výrazy lambda konkrétně najdete v tématu [výrazy Lambda](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span><span class="sxs-lookup"><span data-stu-id="be5d3-110">For more information specifically about lambda expressions, see [Lambda Expressions](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md).</span></span>  
  
 <span data-ttu-id="be5d3-111">Vytvoření anonymní metody je v podstatě způsob, jak předat blok kódu jako parametr delegáta.</span><span class="sxs-lookup"><span data-stu-id="be5d3-111">Creating anonymous methods is essentially a way to pass a code block as a delegate parameter.</span></span> <span data-ttu-id="be5d3-112">Zde jsou dva příklady:</span><span class="sxs-lookup"><span data-stu-id="be5d3-112">Here are two examples:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#6](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_1.cs)]  
  
 [!code-csharp[csProgGuideDelegates#5](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_2.cs)]  
  
 <span data-ttu-id="be5d3-113">Pomocí anonymní metody se snižuje režie kódování v vytváření instancí delegáti, protože není nutné vytvořit samostatné metodě.</span><span class="sxs-lookup"><span data-stu-id="be5d3-113">By using anonymous methods, you reduce the coding overhead in instantiating delegates because you do not have to create a separate method.</span></span>  
  
 <span data-ttu-id="be5d3-114">Například uvádějící že blok kódu místo delegáta může být užitečná v situaci, když nutnosti vytvoření metody zdát nepotřebné režijní náklady.</span><span class="sxs-lookup"><span data-stu-id="be5d3-114">For example, specifying a code block instead of a delegate can be useful in a situation when having to create a method might seem an unnecessary overhead.</span></span> <span data-ttu-id="be5d3-115">Dobrým příkladem může být, kdy spustit nové vlákno.</span><span class="sxs-lookup"><span data-stu-id="be5d3-115">A good example would be when you start a new thread.</span></span> <span data-ttu-id="be5d3-116">Tato třída se vytvoří vlákno a také obsahuje kód, který provede vlákno bez vytvoření další metodu pro delegáta.</span><span class="sxs-lookup"><span data-stu-id="be5d3-116">This class creates a thread and also contains the code that the thread executes without creating an additional method for the delegate.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#7](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_3.cs)]  
  
## <a name="remarks"></a><span data-ttu-id="be5d3-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="be5d3-117">Remarks</span></span>  
 <span data-ttu-id="be5d3-118">Rozsah parametry anonymní metody je *anonymní blok metody*.</span><span class="sxs-lookup"><span data-stu-id="be5d3-118">The scope of the parameters of an anonymous method is the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="be5d3-119">Jedná se o chybu tak, aby měl výpis přechod, jako například [goto](../../../csharp/language-reference/keywords/goto.md), [zalomení](../../../csharp/language-reference/keywords/break.md), nebo [pokračovat](../../../csharp/language-reference/keywords/continue.md), uvnitř bloku anonymní metody, pokud je cílem mimo blok.</span><span class="sxs-lookup"><span data-stu-id="be5d3-119">It is an error to have a jump statement, such as [goto](../../../csharp/language-reference/keywords/goto.md), [break](../../../csharp/language-reference/keywords/break.md), or [continue](../../../csharp/language-reference/keywords/continue.md), inside the anonymous method block if the target is outside the block.</span></span> <span data-ttu-id="be5d3-120">Je také chybu tak, aby měl výpis přechod, jako například `goto`, `break`, nebo `continue`, mimo blok anonymní metody, pokud je cílem uvnitř bloku.</span><span class="sxs-lookup"><span data-stu-id="be5d3-120">It is also an error to have a jump statement, such as `goto`, `break`, or `continue`, outside the anonymous method block if the target is inside the block.</span></span>  
  
 <span data-ttu-id="be5d3-121">Místní proměnné a parametry, jehož obor obsahuje deklaraci anonymní metoda se nazývají *vnější* proměnné anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="be5d3-121">The local variables and parameters whose scope contains an anonymous method declaration are called *outer* variables of the anonymous method.</span></span> <span data-ttu-id="be5d3-122">Například v následujícím kódu segmentu `n` je proměnná vnější:</span><span class="sxs-lookup"><span data-stu-id="be5d3-122">For example, in the following code segment, `n` is an outer variable:</span></span>  
  
 [!code-csharp[csProgGuideDelegates#8](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_4.cs)]  
  
 <span data-ttu-id="be5d3-123">Odkaz na proměnnou vnější `n` se říká, že *zachytit* vytvoření delegát.</span><span class="sxs-lookup"><span data-stu-id="be5d3-123">A reference to the outer variable `n` is said to be *captured* when the delegate is created.</span></span> <span data-ttu-id="be5d3-124">Na rozdíl od místní proměnné doba platnosti zaznamenané proměnné rozšiřuje dokud delegáti, které odkazují na anonymní metody jsou způsobilé pro uvolňování paměti.</span><span class="sxs-lookup"><span data-stu-id="be5d3-124">Unlike local variables, the lifetime of a captured variable extends until the delegates that reference the anonymous methods are eligible for garbage collection.</span></span>  
  
 <span data-ttu-id="be5d3-125">Anonymní metody nemůže získat přístup k [v](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) nebo [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parametry vnějším oboru.</span><span class="sxs-lookup"><span data-stu-id="be5d3-125">An anonymous method cannot access the [in](../../../csharp/language-reference/keywords/in.md), [ref](../../../csharp/language-reference/keywords/ref.md) or [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) parameters of an outer scope.</span></span>  
  
 <span data-ttu-id="be5d3-126">Žádné nezabezpečený kód je přístupná v rámci *anonymní blok metody*.</span><span class="sxs-lookup"><span data-stu-id="be5d3-126">No unsafe code can be accessed within the *anonymous-method-block*.</span></span>  
  
 <span data-ttu-id="be5d3-127">Anonymní metody nejsou povoleny na levé straně [je](../../../csharp/language-reference/keywords/is.md) operátor.</span><span class="sxs-lookup"><span data-stu-id="be5d3-127">Anonymous methods are not allowed on the left side of the [is](../../../csharp/language-reference/keywords/is.md) operator.</span></span>  
  
## <a name="example"></a><span data-ttu-id="be5d3-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="be5d3-128">Example</span></span>  
 <span data-ttu-id="be5d3-129">Následující příklad ukazuje dva způsoby vytvoření instance delegáta:</span><span class="sxs-lookup"><span data-stu-id="be5d3-129">The following example demonstrates two ways of instantiating a delegate:</span></span>  
  
-   <span data-ttu-id="be5d3-130">Delegát přidružením anonymní metody.</span><span class="sxs-lookup"><span data-stu-id="be5d3-130">Associating the delegate with an anonymous method.</span></span>  
  
-   <span data-ttu-id="be5d3-131">Delegát přidružením metodu s názvem (`DoWork`).</span><span class="sxs-lookup"><span data-stu-id="be5d3-131">Associating the delegate with a named method (`DoWork`).</span></span>  
  
 <span data-ttu-id="be5d3-132">V každém případě se zobrazí zpráva při vyvolání delegáta.</span><span class="sxs-lookup"><span data-stu-id="be5d3-132">In each case, a message is displayed when the delegate is invoked.</span></span>  
  
 [!code-csharp[csProgGuideDelegates#4](../../../csharp/programming-guide/delegates/codesnippet/CSharp/anonymous-methods_5.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="be5d3-133">Viz také</span><span class="sxs-lookup"><span data-stu-id="be5d3-133">See Also</span></span>  
 [<span data-ttu-id="be5d3-134">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="be5d3-134">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="be5d3-135">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="be5d3-135">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="be5d3-136">Delegáti</span><span class="sxs-lookup"><span data-stu-id="be5d3-136">Delegates</span></span>](../../../csharp/programming-guide/delegates/index.md)  
 [<span data-ttu-id="be5d3-137">Výrazy lambda</span><span class="sxs-lookup"><span data-stu-id="be5d3-137">Lambda Expressions</span></span>](../../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md)  
 [<span data-ttu-id="be5d3-138">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="be5d3-138">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="be5d3-139">Metody</span><span class="sxs-lookup"><span data-stu-id="be5d3-139">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)  
 [<span data-ttu-id="be5d3-140">Delegáti s pojmenovanými vs. anonymními metodami</span><span class="sxs-lookup"><span data-stu-id="be5d3-140">Delegates with Named vs. Anonymous Methods</span></span>](../../../csharp/programming-guide/delegates/delegates-with-named-vs-anonymous-methods.md)
