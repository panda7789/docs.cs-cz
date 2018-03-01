---
title: "implicit (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c893c7a9afbdc6f715010d537e9ccaf66c5785c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="implicit-c-reference"></a><span data-ttu-id="0c44d-102">implicit (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0c44d-102">implicit (C# Reference)</span></span>
<span data-ttu-id="0c44d-103">`implicit` – Klíčové slovo se používá k deklaraci operátor implicitní uživatelsky definovaný typ. převod.</span><span class="sxs-lookup"><span data-stu-id="0c44d-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="0c44d-104">Můžete povolit implicitní převody mezi uživatelem definovaný typ a jiného typu, pokud převod záruku, že nechcete mít za následek ztrátu dat.</span><span class="sxs-lookup"><span data-stu-id="0c44d-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0c44d-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="0c44d-105">Example</span></span>  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 <span data-ttu-id="0c44d-106">Odstraněním nepotřebných přetypování implicitní převody zlepšit čitelnost zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="0c44d-106">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="0c44d-107">Ale protože implicitní převody nevyžadují programátorům explicitně přetypování z jednoho typu na druhý, musí dát pozor na zabránit neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="0c44d-107">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="0c44d-108">Operátory implicitního převodu obecně by nikdy generování výjimek a nikdy dojít ke ztrátě informací, tak, aby bylo možné bezpečně bez vědomí pro programátory.</span><span class="sxs-lookup"><span data-stu-id="0c44d-108">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="0c44d-109">Pokud operátor převodu nelze splňují tato kritéria, by měl být označen `explicit`.</span><span class="sxs-lookup"><span data-stu-id="0c44d-109">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="0c44d-110">Další informace najdete v tématu [použití operátorů převodu](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="0c44d-110">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="0c44d-111">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0c44d-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0c44d-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="0c44d-112">See Also</span></span>  
 [<span data-ttu-id="0c44d-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0c44d-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0c44d-114">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="0c44d-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0c44d-115">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="0c44d-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="0c44d-116">explicitní</span><span class="sxs-lookup"><span data-stu-id="0c44d-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="0c44d-117">operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="0c44d-117">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="0c44d-118">Postupy: implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="0c44d-118">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
