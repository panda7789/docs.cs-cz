---
title: nastavit odkaz na C# klíčové slovo
ms.date: 03/10/2017
f1_keywords:
- set
- set_CSharpKeyword
helpviewer_keywords:
- set keyword [C#]
ms.assetid: 30d7e4e5-cc2e-4635-a597-14a724879619
ms.openlocfilehash: 97b0dbf8716edc4cd465eb5ac693efa0ecaa498b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713076"
---
# <a name="set-c-reference"></a><span data-ttu-id="98ec1-102">set (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="98ec1-102">set (C# Reference)</span></span>

<span data-ttu-id="98ec1-103">Klíčové slovo `set` definuje metodu *přistupujícího objektu* ve vlastnosti nebo indexeru, která přiřadí hodnotu vlastnosti nebo prvku indexeru.</span><span class="sxs-lookup"><span data-stu-id="98ec1-103">The `set` keyword defines an *accessor* method in a property or indexer that assigns a value to the property or the indexer element.</span></span> <span data-ttu-id="98ec1-104">Další informace a příklady najdete v tématech [vlastnosti](../../programming-guide/classes-and-structs/properties.md), [automaticky implementované vlastnosti](../../programming-guide/classes-and-structs/auto-implemented-properties.md)a [indexery](../../programming-guide/indexers/index.md).</span><span class="sxs-lookup"><span data-stu-id="98ec1-104">For more information and examples, see [Properties](../../programming-guide/classes-and-structs/properties.md), [Auto-Implemented Properties](../../programming-guide/classes-and-structs/auto-implemented-properties.md), and [Indexers](../../programming-guide/indexers/index.md).</span></span>

<span data-ttu-id="98ec1-105">Následující příklad definuje `get` a přístupový objekt `set` pro vlastnost s názvem `Seconds`.</span><span class="sxs-lookup"><span data-stu-id="98ec1-105">The following example defines both a `get` and a `set` accessor for a property named `Seconds`.</span></span> <span data-ttu-id="98ec1-106">Pro zálohu hodnoty vlastnosti používá soukromé pole s názvem `_seconds`.</span><span class="sxs-lookup"><span data-stu-id="98ec1-106">It uses a private field named `_seconds` to back the property value.</span></span>

[!code-csharp[set#1](~/samples/snippets/csharp/language-reference/keywords/get/get-1.cs)]

<span data-ttu-id="98ec1-107">Přístupový objekt `set` se často skládá z jediného příkazu, který přiřadí hodnotu, stejně jako v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="98ec1-107">Often, the `set` accessor consists of a single statement that assigns a value, as it did in the previous example.</span></span> <span data-ttu-id="98ec1-108">Počínaje C# 7,0 můžete implementovat přistupující objekt `set` jako člena Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="98ec1-108">Starting with C# 7.0, you can implement the `set` accessor as an expression-bodied member.</span></span> <span data-ttu-id="98ec1-109">Následující příklad implementuje `get` a přístupové objekty `set` jako členy Expression-těle.</span><span class="sxs-lookup"><span data-stu-id="98ec1-109">The following example implements both the `get` and the `set` accessors as expression-bodied members.</span></span>

[!code-csharp[set#3](~/samples/snippets/csharp/language-reference/keywords/get/get-3.cs)]
  
<span data-ttu-id="98ec1-110">Pro jednoduché případy, kdy `get` a přistupující objekty `set` neprovádí žádnou jinou operaci než nastavení nebo načtení hodnoty v soukromém poli pro zálohování, můžete využít podporu C# kompilátoru pro automaticky implementované vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="98ec1-110">For simple cases in which a property's `get` and `set` accessors perform no other operation than setting or retrieving a value in a private backing field, you can take advantage of the C# compiler's support for auto-implemented properties.</span></span> <span data-ttu-id="98ec1-111">Následující příklad implementuje `Hours` jako automaticky implementovanou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="98ec1-111">The following example implements `Hours` as an auto-implemented property.</span></span> 

[!code-csharp[set#2](~/samples/snippets/csharp/language-reference/keywords/get/get-2.cs)]
  
## <a name="c-language-specification"></a><span data-ttu-id="98ec1-112">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="98ec1-112">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="98ec1-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="98ec1-113">See also</span></span>

- [<span data-ttu-id="98ec1-114">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="98ec1-114">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="98ec1-115">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="98ec1-115">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="98ec1-116">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="98ec1-116">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="98ec1-117">Vlastnosti</span><span class="sxs-lookup"><span data-stu-id="98ec1-117">Properties</span></span>](../../programming-guide/classes-and-structs/properties.md)
