---
title: získat C# odkaz
ms.date: 03/10/2017
f1_keywords:
- get_CSharpKeyword
- get
helpviewer_keywords:
- get keyword [C#]
ms.assetid: a52de048-fbe0-41b0-82ec-8e4ac04d3a71
ms.openlocfilehash: d6c0452a7890a6ade480054115c1383199a3f91c
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713496"
---
# <a name="get-c-reference"></a><span data-ttu-id="c492a-102">get (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c492a-102">get (C# Reference)</span></span>

<span data-ttu-id="c492a-103">Klíčové slovo `get` definuje metodu *přistupujícího objektu* ve vlastnosti nebo indexeru, která vrací hodnotu vlastnosti nebo prvek indexeru.</span><span class="sxs-lookup"><span data-stu-id="c492a-103">The `get` keyword defines an *accessor* method in a property or indexer that returns the property value or the indexer element.</span></span> <span data-ttu-id="c492a-104">Další informace najdete v tématu [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md) a [indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="c492a-104">For more information, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md) and [Indexers](../../programming-guide/indexers/index.md).</span></span>  
  
<span data-ttu-id="c492a-105">Následující příklad definuje `get` a přístupový objekt `set` pro vlastnost s názvem `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="c492a-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="c492a-106">Pro zálohu hodnoty vlastnosti používá soukromé pole s názvem `_seconds`.</span><span class="sxs-lookup"><span data-stu-id="c492a-106">It uses a private field named `_seconds` to back the property value.</span></span>  
 
 [!code-csharp[get#1](../../../../samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]  
  
<span data-ttu-id="c492a-107">Přístupový objekt `get` se často skládá z jediného příkazu, který vrací hodnotu, stejně jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="c492a-107">Often, the `get` accessor consists of a single statement that returns a value, as it did in the previous example.</span></span> <span data-ttu-id="c492a-108">Počínaje C# 7,0 můžete implementovat přistupující objekt `get` jako člena Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="c492a-108">Starting with C# 7.0, you can implement the `get` accessor as an expression-bodied member.</span></span> <span data-ttu-id="c492a-109">Následující příklad implementuje `get` a přístupový objekt `set` jako členy Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="c492a-109">The following example implements both the `get` and the `set` accessor as expression-bodied members.</span></span>

 [!code-csharp[get#3](../../../../samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]   
 
<span data-ttu-id="c492a-110">Pro jednoduché případy, kdy `get` a přistupující objekty `set` neprovádí žádnou jinou operaci než nastavení nebo načtení hodnoty v soukromém poli pro zálohování, můžete využít podporu C# kompilátoru pro automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="c492a-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="c492a-111">Následující příklad implementuje `Hours` jako automaticky implementovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="c492a-111">The following example implements `Hours` as an auto-implemented property.</span></span> 
  
 [!code-csharp[get#2](../../../../samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c492a-112">C# – jazyková specifikace</span><span class="sxs-lookup"><span data-stu-id="c492a-112">C# Language Specification</span></span>

 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c492a-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c492a-113">See also</span></span>

- [<span data-ttu-id="c492a-114">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="c492a-114">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="c492a-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c492a-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="c492a-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c492a-116">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="c492a-117">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="c492a-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
