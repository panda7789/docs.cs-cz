---
title: object (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: 67eaf7f1fd2f01e433395ed21701c3b7fad7c7b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33267919"
---
# <a name="object-c-reference"></a><span data-ttu-id="8e2a9-102">object (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="8e2a9-102">object (C# Reference)</span></span>
<span data-ttu-id="8e2a9-103">`object` Typ je alias <xref:System.Object> v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e2a9-103">The `object` type is an alias for <xref:System.Object> in the .NET Framework.</span></span> <span data-ttu-id="8e2a9-104">V systému jednotná typu jazyka C#, všechny typy, odkaz na předdefinované a uživatelem definované typy a typy hodnot, dědí přímo nebo nepřímo <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="8e2a9-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="8e2a9-105">Můžete přiřadit hodnoty libovolného typu proměnné typu `object`.</span><span class="sxs-lookup"><span data-stu-id="8e2a9-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="8e2a9-106">Když je proměnná typu hodnoty převést na objekt, je označováno jako *do pole*.</span><span class="sxs-lookup"><span data-stu-id="8e2a9-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="8e2a9-107">Pokud proměnná typu objektu je převést na typ hodnoty, je označováno jako *nezabalený*.</span><span class="sxs-lookup"><span data-stu-id="8e2a9-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="8e2a9-108">Další informace najdete v tématu [zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="8e2a9-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e2a9-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="8e2a9-109">Example</span></span>  
 <span data-ttu-id="8e2a9-110">Následující ukázkové ukazuje, jak proměnné typu `object` může přijmout hodnoty libovolného typu data a jak proměnné typu `object` můžete použít metody na <xref:System.Object> z rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="8e2a9-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="8e2a9-111">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e2a9-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="8e2a9-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e2a9-112">See Also</span></span>  
 [<span data-ttu-id="8e2a9-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e2a9-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="8e2a9-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="8e2a9-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="8e2a9-115">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="8e2a9-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="8e2a9-116">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="8e2a9-116">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="8e2a9-117">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="8e2a9-117">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
