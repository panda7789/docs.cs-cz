---
title: implicit (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- implicit
- implicit_CSharpKeyword
helpviewer_keywords:
- implicit keyword [C#]
ms.assetid: 34db590e-eb3a-4f11-88d0-ffb3cd753dab
ms.openlocfilehash: 160d9f7c0d58abd685bf1d799b53cc96a26aebe8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215014"
---
# <a name="implicit-c-reference"></a><span data-ttu-id="6166b-102">implicit (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6166b-102">implicit (C# Reference)</span></span>
<span data-ttu-id="6166b-103">`implicit` – Klíčové slovo se používá k deklaraci operátor implicitní uživatelsky definovaný typ. převod.</span><span class="sxs-lookup"><span data-stu-id="6166b-103">The `implicit` keyword is used to declare an implicit user-defined type conversion operator.</span></span> <span data-ttu-id="6166b-104">Můžete povolit implicitní převody mezi uživatelem definovaný typ a jiného typu, pokud převod záruku, že nechcete mít za následek ztrátu dat.</span><span class="sxs-lookup"><span data-stu-id="6166b-104">Use it to enable implicit conversions between a user-defined type and another type, if the conversion is guaranteed not to cause a loss of data.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6166b-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="6166b-105">Example</span></span>  
 [!code-csharp[csrefKeywordsConversion#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/implicit_1.cs)]  
  
 <span data-ttu-id="6166b-106">Odstraněním nepotřebných přetypování implicitní převody zlepšit čitelnost zdrojového kódu.</span><span class="sxs-lookup"><span data-stu-id="6166b-106">By eliminating unnecessary casts, implicit conversions can improve source code readability.</span></span> <span data-ttu-id="6166b-107">Ale protože implicitní převody nevyžadují programátorům explicitně přetypování z jednoho typu na druhý, musí dát pozor na zabránit neočekávané výsledky.</span><span class="sxs-lookup"><span data-stu-id="6166b-107">However, because implicit conversions do not require programmers to explicitly cast from one type to the other, care must be taken to prevent unexpected results.</span></span> <span data-ttu-id="6166b-108">Operátory implicitního převodu obecně by nikdy generování výjimek a nikdy dojít ke ztrátě informací, tak, aby bylo možné bezpečně bez vědomí pro programátory.</span><span class="sxs-lookup"><span data-stu-id="6166b-108">In general, implicit conversion operators should never throw exceptions and never lose information so that they can be used safely without the programmer's awareness.</span></span> <span data-ttu-id="6166b-109">Pokud operátor převodu nelze splňují tato kritéria, by měl být označen `explicit`.</span><span class="sxs-lookup"><span data-stu-id="6166b-109">If a conversion operator cannot meet those criteria, it should be marked `explicit`.</span></span> <span data-ttu-id="6166b-110">Další informace najdete v tématu [použití operátorů převodu](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span><span class="sxs-lookup"><span data-stu-id="6166b-110">For more information, see [Using Conversion Operators](../../../csharp/programming-guide/statements-expressions-operators/using-conversion-operators.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="6166b-111">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6166b-111">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6166b-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="6166b-112">See Also</span></span>  
 [<span data-ttu-id="6166b-113">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6166b-113">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="6166b-114">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="6166b-114">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6166b-115">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="6166b-115">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="6166b-116">explicit</span><span class="sxs-lookup"><span data-stu-id="6166b-116">explicit</span></span>](../../../csharp/language-reference/keywords/explicit.md)  
 [<span data-ttu-id="6166b-117">Operátor (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="6166b-117">operator (C# Reference)</span></span>](../../../csharp/language-reference/keywords/operator.md)  
 [<span data-ttu-id="6166b-118">Postupy: Implementace uživatelem definovaných převodů mezi strukturami</span><span class="sxs-lookup"><span data-stu-id="6166b-118">How to: Implement User-Defined Conversions Between Structs</span></span>](../../../csharp/programming-guide/statements-expressions-operators/how-to-implement-user-defined-conversions-between-structs.md)
