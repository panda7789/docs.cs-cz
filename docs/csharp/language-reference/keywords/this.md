---
title: this (Referenční dokumentace jazyka C#)
description: This – klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 04496079114be45388926993b67e8f1d3f2e9f15
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172032"
---
# <a name="this-c-reference"></a><span data-ttu-id="33681-103">this (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="33681-103">this (C# Reference)</span></span>
<span data-ttu-id="33681-104">`this` – Klíčové slovo odkazuje na aktuální instanci třídy a také slouží jako modifikátor první parametr metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="33681-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33681-105">Tento článek popisuje použití `this` s instancí třídy.</span><span class="sxs-lookup"><span data-stu-id="33681-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="33681-106">Další informace o jeho použití v metody rozšíření najdete v tématu [rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="33681-106">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="33681-107">Toto jsou běžná použití služby `this`:</span><span class="sxs-lookup"><span data-stu-id="33681-107">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="33681-108">Aby se dosáhlo nároku členy skryt podobné názvy, například:</span><span class="sxs-lookup"><span data-stu-id="33681-108">To qualify members hidden by similar names, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   <span data-ttu-id="33681-109">Chcete-li předat objekt jako parametr jinými metodami, například:</span><span class="sxs-lookup"><span data-stu-id="33681-109">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```csharp  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="33681-110">Chcete-li deklarovat indexery, například:</span><span class="sxs-lookup"><span data-stu-id="33681-110">To declare indexers, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 <span data-ttu-id="33681-111">Statické členské funkce, protože existují na úrovni třídy a nikoli jako součást objekt, nemají `this` ukazatel.</span><span class="sxs-lookup"><span data-stu-id="33681-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="33681-112">Jedná se o chybu, který bude odkazovat na `this` v statickou metodu.</span><span class="sxs-lookup"><span data-stu-id="33681-112">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33681-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="33681-113">Example</span></span>  
 <span data-ttu-id="33681-114">V tomto příkladu `this` se použijí pro kvalifikaci `Employee` třídy členy, `name` a `alias`, které jsou podobné názvy skryté.</span><span class="sxs-lookup"><span data-stu-id="33681-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="33681-115">Používá se také předat objekt metodu `CalcTax`, který patří do jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="33681-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="33681-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="33681-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="33681-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="33681-117">See Also</span></span>  
 [<span data-ttu-id="33681-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="33681-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="33681-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="33681-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="33681-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="33681-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="33681-121">base</span><span class="sxs-lookup"><span data-stu-id="33681-121">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="33681-122">Metody</span><span class="sxs-lookup"><span data-stu-id="33681-122">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
