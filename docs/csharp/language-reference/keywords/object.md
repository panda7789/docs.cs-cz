---
title: "object (Referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0fcced75d3a86fd700e642e48b7e325e554cae53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="object-c-reference"></a><span data-ttu-id="27075-102">object (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="27075-102">object (C# Reference)</span></span>
<span data-ttu-id="27075-103">`object` Typ je alias <xref:System.Object> v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27075-103">The `object` type is an alias for <xref:System.Object> in the .NET Framework.</span></span> <span data-ttu-id="27075-104">V systému jednotná typu jazyka C#, všechny typy, odkaz na předdefinované a uživatelem definované typy a typy hodnot, dědí přímo nebo nepřímo <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="27075-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="27075-105">Můžete přiřadit hodnoty libovolného typu proměnné typu `object`.</span><span class="sxs-lookup"><span data-stu-id="27075-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="27075-106">Když je proměnná typu hodnoty převést na objekt, je označováno jako *do pole*.</span><span class="sxs-lookup"><span data-stu-id="27075-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="27075-107">Pokud proměnná typu objektu je převést na typ hodnoty, je označováno jako *nezabalený*.</span><span class="sxs-lookup"><span data-stu-id="27075-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="27075-108">Další informace najdete v tématu [zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="27075-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="27075-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="27075-109">Example</span></span>  
 <span data-ttu-id="27075-110">Následující ukázkové ukazuje, jak proměnné typu `object` může přijmout hodnoty libovolného typu data a jak proměnné typu `object` můžete použít metody na <xref:System.Object> z rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="27075-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="27075-111">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="27075-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="27075-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="27075-112">See Also</span></span>  
 [<span data-ttu-id="27075-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="27075-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="27075-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="27075-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="27075-115">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="27075-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="27075-116">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="27075-116">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="27075-117">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="27075-117">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
