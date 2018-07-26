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
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39199248"
---
# <a name="object-c-reference"></a><span data-ttu-id="6b9ce-102">object (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6b9ce-102">object (C# Reference)</span></span>
<span data-ttu-id="6b9ce-103">`object` Typ je alias pro <xref:System.Object> v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-103">The `object` type is an alias for <xref:System.Object> in the .NET Framework.</span></span> <span data-ttu-id="6b9ce-104">V systému unified typů jazyka C#, všechny typy, typy odkazů předdefinovaných a definovaný uživatelem, a typů hodnot, dědí přímo nebo nepřímo <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="6b9ce-105">Můžete přiřadit proměnné typu hodnoty libovolného typu `object`.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="6b9ce-106">Když je proměnné typu hodnoty převeden na objekt, je označen jako *boxed*.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="6b9ce-107">Pokud proměnnou typu objektu je převeden na typ hodnoty, je označen jako *nezabalené*.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="6b9ce-108">Další informace najdete v tématu [zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="6b9ce-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b9ce-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b9ce-109">Example</span></span>  
 <span data-ttu-id="6b9ce-110">Následující ukázkový ukazuje, jak proměnné typu `object` může přijmout hodnoty libovolného typu dat a jak proměnné typu `object` můžete použít metody na <xref:System.Object> z rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6b9ce-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>  
  
 [!code-csharp[csrefKeywordsTypes#16](../../../csharp/language-reference/keywords/codesnippet/CSharp/object_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="6b9ce-111">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6b9ce-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6b9ce-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b9ce-112">See Also</span></span>  
 [<span data-ttu-id="6b9ce-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6b9ce-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6b9ce-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6b9ce-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6b9ce-115">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6b9ce-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6b9ce-116">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="6b9ce-116">Reference Types</span></span>](../../../csharp/language-reference/keywords/reference-types.md)  
 [<span data-ttu-id="6b9ce-117">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="6b9ce-117">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)
