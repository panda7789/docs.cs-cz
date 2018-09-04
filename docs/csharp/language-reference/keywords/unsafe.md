---
title: unsafe (Referenční dokumentace jazyka C#)
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: b4615021a4fc3391ac0ae703b6c97301b44aa60e
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541430"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="1db4b-102">unsafe (Referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="1db4b-102">unsafe (C# Reference)</span></span>
<span data-ttu-id="1db4b-103">`unsafe` – Klíčové slovo označuje nezabezpečený kontext, který se vyžaduje pro libovolnou operaci s ukazateli.</span><span class="sxs-lookup"><span data-stu-id="1db4b-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="1db4b-104">Další informace najdete v tématu [nezabezpečený kód a ukazatele](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="1db4b-104">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="1db4b-105">Můžete použít `unsafe` modifikátor v deklaraci typu nebo člena.</span><span class="sxs-lookup"><span data-stu-id="1db4b-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="1db4b-106">Textové celý rozsah tento typ nebo člen je proto považován za nezabezpečený kontext.</span><span class="sxs-lookup"><span data-stu-id="1db4b-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="1db4b-107">Například tady je metody deklarované s `unsafe` modifikátor:</span><span class="sxs-lookup"><span data-stu-id="1db4b-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>  
  
```csharp  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="1db4b-108">Obor nezabezpečeném kontextu rozšiřuje ze seznamu parametrů na konec metody, takže ukazatele lze také v seznamu parametrů:</span><span class="sxs-lookup"><span data-stu-id="1db4b-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>  
  
```csharp  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 <span data-ttu-id="1db4b-109">Můžete také použít blok unsafe umožní použít nezabezpečený kód v tomto bloku.</span><span class="sxs-lookup"><span data-stu-id="1db4b-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="1db4b-110">Příklad:</span><span class="sxs-lookup"><span data-stu-id="1db4b-110">For example:</span></span>  
  
```csharp  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="1db4b-111">Chcete-li zkompilovat nebezpečný kód, je nutné zadat [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="1db4b-111">To compile unsafe code, you must specify the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="1db4b-112">Nezabezpečený kód není možné ověřit modulem common language runtime.</span><span class="sxs-lookup"><span data-stu-id="1db4b-112">Unsafe code is not verifiable by the common language runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1db4b-113">Příklad</span><span class="sxs-lookup"><span data-stu-id="1db4b-113">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="1db4b-114">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1db4b-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1db4b-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="1db4b-115">See Also</span></span>

- [<span data-ttu-id="1db4b-116">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1db4b-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="1db4b-117">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="1db4b-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="1db4b-118">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="1db4b-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="1db4b-119">fixed – příkaz</span><span class="sxs-lookup"><span data-stu-id="1db4b-119">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="1db4b-120">Nebezpečný kód a ukazatele</span><span class="sxs-lookup"><span data-stu-id="1db4b-120">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [<span data-ttu-id="1db4b-121">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="1db4b-121">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
