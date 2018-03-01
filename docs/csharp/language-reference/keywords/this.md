---
title: "this (Referenční dokumentace jazyka C#)"
description: "This – klíčové slovo (referenční dokumentace jazyka C#)"
keywords: "Tato (C#), toto klíčové slovo (C#), toto klíčové slovo (C# odkaz), toto klíčové slovo (C# referenční dokumentace jazyka)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f159967707061481a34e72a97ec8cc8316d982ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="this-c-reference"></a><span data-ttu-id="65ef7-104">this (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="65ef7-104">this (C# Reference)</span></span>
<span data-ttu-id="65ef7-105">`this` – Klíčové slovo odkazuje na aktuální instanci třídy a také slouží jako modifikátor první parametr metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="65ef7-105">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="65ef7-106">Tento článek popisuje použití `this` s instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="65ef7-106">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="65ef7-107">Další informace o jeho použití v metody rozšíření najdete v tématu [rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="65ef7-107">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="65ef7-108">Toto jsou běžná použití služby `this`:</span><span class="sxs-lookup"><span data-stu-id="65ef7-108">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="65ef7-109">Aby se dosáhlo nároku členy skryt podobné názvy, například:</span><span class="sxs-lookup"><span data-stu-id="65ef7-109">To qualify members hidden by similar names, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   <span data-ttu-id="65ef7-110">Chcete-li předat objekt jako parametr jinými metodami, například:</span><span class="sxs-lookup"><span data-stu-id="65ef7-110">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="65ef7-111">Chcete-li deklarovat indexery, například:</span><span class="sxs-lookup"><span data-stu-id="65ef7-111">To declare indexers, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 <span data-ttu-id="65ef7-112">Statické členské funkce, protože existují na úrovni třídy a nikoli jako součást objekt, nemají `this` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="65ef7-112">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="65ef7-113">Jedná se o chybu, který bude odkazovat na `this` v statickou metodu.</span><span class="sxs-lookup"><span data-stu-id="65ef7-113">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65ef7-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="65ef7-114">Example</span></span>  
 <span data-ttu-id="65ef7-115">V tomto příkladu `this` se použijí pro kvalifikaci `Employee` třídy členy, `name` a `alias`, které jsou podobné názvy skryté.</span><span class="sxs-lookup"><span data-stu-id="65ef7-115">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="65ef7-116">Používá se také předat objekt metodu `CalcTax`, který patří do jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="65ef7-116">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="65ef7-117">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="65ef7-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="65ef7-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="65ef7-118">See Also</span></span>  
 [<span data-ttu-id="65ef7-119">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="65ef7-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="65ef7-120">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="65ef7-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="65ef7-121">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="65ef7-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="65ef7-122">základní</span><span class="sxs-lookup"><span data-stu-id="65ef7-122">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="65ef7-123">Metody</span><span class="sxs-lookup"><span data-stu-id="65ef7-123">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
