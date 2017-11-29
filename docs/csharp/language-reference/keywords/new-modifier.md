---
title: "new – modifikátor (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: new modifier keyword [C#]
ms.assetid: a2e20856-33b9-4620-b535-a60dbce8349b
caps.latest.revision: "28"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 28124c2f3ecef01fd4bc43fe7cfc975dd6466506
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="new-modifier-c-reference"></a><span data-ttu-id="6158f-102">new – modifikátor (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6158f-102">new Modifier (C# Reference)</span></span>
<span data-ttu-id="6158f-103">Když se použije jako modifikátor deklarace, `new` – klíčové slovo explicitně skryje člena, který je zděděn ze základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6158f-103">When used as a declaration modifier, the `new` keyword explicitly hides a member that is inherited from a base class.</span></span> <span data-ttu-id="6158f-104">Skrytí zděděného členu odvozenou verzí člena nahradí verzi základní třídy.</span><span class="sxs-lookup"><span data-stu-id="6158f-104">When you hide an inherited member, the derived version of the member replaces the base class version.</span></span> <span data-ttu-id="6158f-105">I když můžete skrýt členy, bez použití `new` modifikátor, zobrazí se upozornění kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="6158f-105">Although you can hide members without using the `new` modifier, you get a compiler warning.</span></span> <span data-ttu-id="6158f-106">Pokud používáte `new` explicitně skrýt členem, potlačí toto upozornění.</span><span class="sxs-lookup"><span data-stu-id="6158f-106">If you use `new` to explicitly hide a member, it suppresses this warning.</span></span>  
  
 <span data-ttu-id="6158f-107">Skrýt zděděného členu, deklarovat v odvozené třídě za použití stejného názvu člen a upravit ho pomocí `new` – klíčové slovo.</span><span class="sxs-lookup"><span data-stu-id="6158f-107">To hide an inherited member, declare it in the derived class by using the same member name, and modify it with the `new` keyword.</span></span> <span data-ttu-id="6158f-108">Příklad:</span><span class="sxs-lookup"><span data-stu-id="6158f-108">For example:</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#8](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_1.cs)]  
  
 <span data-ttu-id="6158f-109">V tomto příkladu `BaseC.Invoke` je skrytý na základě `DerivedC.Invoke`.</span><span class="sxs-lookup"><span data-stu-id="6158f-109">In this example, `BaseC.Invoke` is hidden by `DerivedC.Invoke`.</span></span> <span data-ttu-id="6158f-110">Pole `x` nemá vliv, protože není skryt podobným jménem.</span><span class="sxs-lookup"><span data-stu-id="6158f-110">The field `x` is not affected because it is not hidden by a similar name.</span></span>  
  
 <span data-ttu-id="6158f-111">Název skrytí prostřednictvím dědičnosti má jednu z následujících podob:</span><span class="sxs-lookup"><span data-stu-id="6158f-111">Name hiding through inheritance takes one of the following forms:</span></span>  
  
-   <span data-ttu-id="6158f-112">Obecně platí konstanta, pole, vlastnost nebo typ, který byl představen v třídě nebo struktuře skryje všechny členy základní třídy, které jeho název sdílené složky.</span><span class="sxs-lookup"><span data-stu-id="6158f-112">Generally, a constant, field, property, or type that is introduced in a class or struct hides all base class members that share its name.</span></span>  <span data-ttu-id="6158f-113">Existují zvláštní případy.</span><span class="sxs-lookup"><span data-stu-id="6158f-113">There are special cases.</span></span>  <span data-ttu-id="6158f-114">Například, pokud je deklarovat nové pole s názvem `N` mít typ, který není invocable a základní typ deklaruje `N` jako metodu nové pole není skrýt základní deklaraci v syntaxi volání.</span><span class="sxs-lookup"><span data-stu-id="6158f-114">For example, if you declare a new field with name `N` to have a type that is not invocable, and a base type declares `N` to be a method, the new field does not hide the base declaration in invocation syntax.</span></span>  <span data-ttu-id="6158f-115">Najdete v článku [specifikace jazyka C# 5.0](http://go.microsoft.com/fwlink/?LinkId=199552) podrobnosti (viz část "Člen vyhledávání" v části "Výrazy").</span><span class="sxs-lookup"><span data-stu-id="6158f-115">See the [C# 5.0 language specification](http://go.microsoft.com/fwlink/?LinkId=199552) for details (see section "Member Lookup" in section "Expressions").</span></span>  
  
-   <span data-ttu-id="6158f-116">Metoda byla zavedená v třídě nebo struktuře skryje vlastnosti, pole a typy, které sdílejí tento název v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="6158f-116">A method introduced in a class or struct hides properties, fields, and types that share that name in the base class.</span></span> <span data-ttu-id="6158f-117">Skryje také všechny metody třídy base, které mají stejným podpisem.</span><span class="sxs-lookup"><span data-stu-id="6158f-117">It also hides all base class methods that have the same signature.</span></span>  
  
-   <span data-ttu-id="6158f-118">Indexer byla zavedená v třídě nebo struktuře skryje všechny základní třídy indexery, které mají stejným podpisem.</span><span class="sxs-lookup"><span data-stu-id="6158f-118">An indexer introduced in a class or struct hides all base class indexers that have the same signature.</span></span>  
  
 <span data-ttu-id="6158f-119">Jedná se o chybu použití `new` a [přepsat](../../../csharp/language-reference/keywords/override.md) na stejného člena, protože mají dva modifikátory vzájemně se vylučuje významy.</span><span class="sxs-lookup"><span data-stu-id="6158f-119">It is an error to use both `new` and [override](../../../csharp/language-reference/keywords/override.md) on the same member, because the two modifiers have mutually exclusive meanings.</span></span> <span data-ttu-id="6158f-120">`new` Modifikátor vytvoří nový člen se stejným názvem a způsobí, že původní člen stát skryté.</span><span class="sxs-lookup"><span data-stu-id="6158f-120">The `new` modifier creates a new member with the same name and causes the original member to become hidden.</span></span> <span data-ttu-id="6158f-121">`override` Modifikátor rozšiřuje implementaci pro zděděného členu.</span><span class="sxs-lookup"><span data-stu-id="6158f-121">The `override` modifier extends the implementation for an inherited member.</span></span>  
  
 <span data-ttu-id="6158f-122">Pomocí `new` modifikátor v deklaraci, která není skrýt zděděného členu vygeneruje upozornění.</span><span class="sxs-lookup"><span data-stu-id="6158f-122">Using the `new` modifier in a declaration that does not hide an inherited member generates a warning.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6158f-123">Příklad</span><span class="sxs-lookup"><span data-stu-id="6158f-123">Example</span></span>  
 <span data-ttu-id="6158f-124">V tomto příkladu základní třídu, `BaseC`a odvozené třídy `DerivedC`, použijte stejný název pole `x`, která skryje hodnotu zděděné pole.</span><span class="sxs-lookup"><span data-stu-id="6158f-124">In this example, a base class, `BaseC`, and a derived class, `DerivedC`, use the same field name `x`, which hides the value of the inherited field.</span></span> <span data-ttu-id="6158f-125">Příklad ukazuje použití `new` modifikátor.</span><span class="sxs-lookup"><span data-stu-id="6158f-125">The example demonstrates the use of the `new` modifier.</span></span> <span data-ttu-id="6158f-126">Také ukazuje, jak skrytý členy základní třídy přistupovat pomocí jejich plně kvalifikované názvy.</span><span class="sxs-lookup"><span data-stu-id="6158f-126">It also demonstrates how to access the hidden members of the base class by using their fully qualified names.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#9](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_2.cs)]  
  
## <a name="example"></a><span data-ttu-id="6158f-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="6158f-127">Example</span></span>  
 <span data-ttu-id="6158f-128">V tomto příkladu vnořené třídy skryje třídu, která má stejný název v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="6158f-128">In this example, a nested class hides a class that has the same name in the base class.</span></span> <span data-ttu-id="6158f-129">Příklad ukazuje, jak používat `new` modifikátor eliminovat upozornění a přístupu k členům skrytá třídy pomocí jejich plně kvalifikované názvy.</span><span class="sxs-lookup"><span data-stu-id="6158f-129">The example demonstrates how to use the `new` modifier to eliminate the warning message and how to access the hidden class members by using their fully qualified names.</span></span>  
  
 [!code-csharp[csrefKeywordsOperator#10](../../../csharp/language-reference/keywords/codesnippet/CSharp/new-modifier_3.cs)]  
  
 <span data-ttu-id="6158f-130">Pokud odeberete `new` modifikátor, program stále zkompilování a spuštění, ale zobrazí se následující upozornění:</span><span class="sxs-lookup"><span data-stu-id="6158f-130">If you remove the `new` modifier, the program will still compile and run, but you will get the following warning:</span></span>  
  
```  
The keyword new is required on 'MyDerivedC.x' because it hides inherited member 'MyBaseC.x'.  
```  
  
## <a name="c-language-specification"></a><span data-ttu-id="6158f-131">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6158f-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6158f-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="6158f-132">See Also</span></span>  
 [<span data-ttu-id="6158f-133">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6158f-133">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6158f-134">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="6158f-134">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6158f-135">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6158f-135">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6158f-136">Klíčová slova operátorů</span><span class="sxs-lookup"><span data-stu-id="6158f-136">Operator Keywords</span></span>](../../../csharp/language-reference/keywords/operator-keywords.md)  
 [<span data-ttu-id="6158f-137">Modifikátory</span><span class="sxs-lookup"><span data-stu-id="6158f-137">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="6158f-138">Správa verzí pomocí nové klíčových slov Override a</span><span class="sxs-lookup"><span data-stu-id="6158f-138">Versioning with the Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords.md)  
 [<span data-ttu-id="6158f-139">Znalost, kdy použít nové klíčových slov Override a</span><span class="sxs-lookup"><span data-stu-id="6158f-139">Knowing When to Use Override and New Keywords</span></span>](../../../csharp/programming-guide/classes-and-structs/knowing-when-to-use-override-and-new-keywords.md)
