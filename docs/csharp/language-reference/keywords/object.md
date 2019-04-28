---
title: objekt – C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- object_CSharpKeyword
- object
helpviewer_keywords:
- object keyword [C#]
ms.assetid: 93f60c0b-e17a-40a9-9362-cca5fb77b0e7
ms.openlocfilehash: a1917a7925d4ed90ede40248fa394f9c45d09b4e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61661123"
---
# <a name="object-c-reference"></a><span data-ttu-id="47622-102">object (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="47622-102">object (C# Reference)</span></span>

<span data-ttu-id="47622-103">`object` Typ je alias pro <xref:System.Object> v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="47622-103">The `object` type is an alias for <xref:System.Object> in .NET.</span></span> <span data-ttu-id="47622-104">V systému unified typů jazyka C#, všechny typy, typy odkazů předdefinovaných a definovaný uživatelem, a typů hodnot, dědí přímo nebo nepřímo <xref:System.Object>.</span><span class="sxs-lookup"><span data-stu-id="47622-104">In the unified type system of C#, all types, predefined and user-defined, reference types and value types, inherit directly or indirectly from <xref:System.Object>.</span></span> <span data-ttu-id="47622-105">Můžete přiřadit proměnné typu hodnoty libovolného typu `object`.</span><span class="sxs-lookup"><span data-stu-id="47622-105">You can assign values of any type to variables of type `object`.</span></span> <span data-ttu-id="47622-106">Když je proměnné typu hodnoty převeden na objekt, je označen jako *boxed*.</span><span class="sxs-lookup"><span data-stu-id="47622-106">When a variable of a value type is converted to object, it is said to be *boxed*.</span></span> <span data-ttu-id="47622-107">Pokud proměnnou typu objektu je převeden na typ hodnoty, je označen jako *nezabalené*.</span><span class="sxs-lookup"><span data-stu-id="47622-107">When a variable of type object is converted to a value type, it is said to be *unboxed*.</span></span> <span data-ttu-id="47622-108">Další informace najdete v tématu [zabalení a rozbalení](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span><span class="sxs-lookup"><span data-stu-id="47622-108">For more information, see [Boxing and Unboxing](../../../csharp/programming-guide/types/boxing-and-unboxing.md).</span></span>

## <a name="example"></a><span data-ttu-id="47622-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="47622-109">Example</span></span>

<span data-ttu-id="47622-110">Následující ukázkový ukazuje, jak proměnné typu `object` může přijmout hodnoty libovolného typu dat a jak proměnné typu `object` můžete použít metody na <xref:System.Object> z rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="47622-110">The following sample shows how variables of type `object` can accept values of any data type and how variables of type `object` can use methods on <xref:System.Object> from the .NET Framework.</span></span>

[!code-csharp[csrefKeywordsTypes#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsTypes/CS/keywordsTypes.cs#16)]

## <a name="c-language-specification"></a><span data-ttu-id="47622-111">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="47622-111">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="47622-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47622-112">See also</span></span>

- [<span data-ttu-id="47622-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="47622-113">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="47622-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="47622-114">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="47622-115">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="47622-115">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="47622-116">Odkazové typy</span><span class="sxs-lookup"><span data-stu-id="47622-116">Reference Types</span></span>](reference-types.md)
- [<span data-ttu-id="47622-117">Typy hodnot</span><span class="sxs-lookup"><span data-stu-id="47622-117">Value Types</span></span>](value-types.md)