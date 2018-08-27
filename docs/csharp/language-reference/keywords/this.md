---
title: this (Referenční dokumentace jazyka C#)
description: Toto klíčové slovo (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: df1bf6a3e6d24b231bf5e3c7a960f49084c4e53a
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42930188"
---
# <a name="this-c-reference"></a><span data-ttu-id="b0578-103">this (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="b0578-103">this (C# Reference)</span></span>
<span data-ttu-id="b0578-104">`this` – Klíčové slovo odkazuje na aktuální instanci třídy a slouží také jako modifikátor první parametr metody rozšíření.</span><span class="sxs-lookup"><span data-stu-id="b0578-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b0578-105">Tento článek popisuje způsob používání `this` instancemi třídy.</span><span class="sxs-lookup"><span data-stu-id="b0578-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="b0578-106">Další informace o jeho použití v metodách rozšíření naleznete v tématu [rozšiřující metody](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="b0578-106">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="b0578-107">Tady jsou běžné způsoby použití `this`:</span><span class="sxs-lookup"><span data-stu-id="b0578-107">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="b0578-108">K získání způsobilosti členy skryta podobnými názvy, například:</span><span class="sxs-lookup"><span data-stu-id="b0578-108">To qualify members hidden by similar names, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   <span data-ttu-id="b0578-109">K předání objektu jako parametr do jiné metody, například:</span><span class="sxs-lookup"><span data-stu-id="b0578-109">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```csharp  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="b0578-110">Chcete-li deklarovat indexery, například:</span><span class="sxs-lookup"><span data-stu-id="b0578-110">To declare indexers, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 <span data-ttu-id="b0578-111">Statické členské funkce, protože existují na úrovni třídy, nikoli jako součást objektu, není nutné `this` ukazatele.</span><span class="sxs-lookup"><span data-stu-id="b0578-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="b0578-112">Jedná se o chybu k odkazování na `this` uvnitř statické metody.</span><span class="sxs-lookup"><span data-stu-id="b0578-112">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b0578-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="b0578-113">Example</span></span>  
 <span data-ttu-id="b0578-114">V tomto příkladu `this` se použijí pro kvalifikaci `Employee` členy, třídy `name` a `alias`, které jsou skryté, podobně jako názvy.</span><span class="sxs-lookup"><span data-stu-id="b0578-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="b0578-115">Používá se také k objektu předat metodě `CalcTax`, který patří do jiné třídy.</span><span class="sxs-lookup"><span data-stu-id="b0578-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="b0578-116">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b0578-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b0578-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="b0578-117">See Also</span></span>

- [<span data-ttu-id="b0578-118">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b0578-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="b0578-119">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="b0578-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="b0578-120">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="b0578-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="b0578-121">base</span><span class="sxs-lookup"><span data-stu-id="b0578-121">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
- [<span data-ttu-id="b0578-122">Metody</span><span class="sxs-lookup"><span data-stu-id="b0578-122">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
