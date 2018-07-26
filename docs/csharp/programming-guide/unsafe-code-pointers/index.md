---
title: Nezabezpečený kód a ukazatele (Průvodce programováním v C#)
ms.date: 07/20/2015
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
ms.openlocfilehash: b57a6f607dbdbc84c60889a5ce2b1e3c33d7f435
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245169"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="780cf-102">Nezabezpečený kód a ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="780cf-102">Unsafe Code and Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="780cf-103">Pokud chcete zachovat bezpečnost typů a zabezpečení, C# nepodporuje aritmetiku ukazatele ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="780cf-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="780cf-104">Nicméně pomocí [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo, můžete definovat nezabezpečený kontext, ve které je možné ukazatele.</span><span class="sxs-lookup"><span data-stu-id="780cf-104">However, by using the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="780cf-105">Další informace o ukazatelích naleznete v tématu [typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="780cf-105">For more information about pointers, see the topic [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="780cf-106">V modulu common language runtime (CLR) nebezpečný kód se označuje jako neověřitelný kód.</span><span class="sxs-lookup"><span data-stu-id="780cf-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="780cf-107">Nezabezpečený kód v jazyce C# není nutně nebezpečné; je jenom kód, jejichž zabezpečení nelze ověřit pomocí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="780cf-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="780cf-108">Modul CLR proto pouze spustí nezabezpečený kód by byl v plně důvěryhodná sestavení.</span><span class="sxs-lookup"><span data-stu-id="780cf-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="780cf-109">Pokud používáte nebezpečný kód, je vaší povinností ujistit, že váš kód nezavádí rizika zabezpečení nebo ukazatel chyby.</span><span class="sxs-lookup"><span data-stu-id="780cf-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="780cf-110">Přehled nebezpečného kódu</span><span class="sxs-lookup"><span data-stu-id="780cf-110">Unsafe Code Overview</span></span>  
 <span data-ttu-id="780cf-111">Nezabezpečený kód má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="780cf-111">Unsafe code has the following properties:</span></span>  
  
-   <span data-ttu-id="780cf-112">Metody, typy a bloků kódu může být definován jako bezpečné.</span><span class="sxs-lookup"><span data-stu-id="780cf-112">Methods, types, and code blocks can be defined as unsafe.</span></span>  
  
-   <span data-ttu-id="780cf-113">V některých případech může nezabezpečený kód zvýšit výkon vaší aplikace tak, že odeberete kontroly hranice pole.</span><span class="sxs-lookup"><span data-stu-id="780cf-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>  
  
-   <span data-ttu-id="780cf-114">Nezabezpečený kód je potřeba při volání nativních funkcí, které vyžadují ukazatele.</span><span class="sxs-lookup"><span data-stu-id="780cf-114">Unsafe code is required when you call native functions that require pointers.</span></span>  
  
-   <span data-ttu-id="780cf-115">Použití nezabezpečeného kódu představuje rizika zabezpečení a stabilitu.</span><span class="sxs-lookup"><span data-stu-id="780cf-115">Using unsafe code introduces security and stability risks.</span></span>  
  
-   <span data-ttu-id="780cf-116">V pořadí pro jazyk C# ke kompilaci nezabezpečený kód aplikace musí být kompilována s [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="780cf-116">In order for C# to compile unsafe code, the application must be compiled with [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="780cf-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="780cf-117">Related Sections</span></span>  
 <span data-ttu-id="780cf-118">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="780cf-118">For more information, see:</span></span>  
  
-   [<span data-ttu-id="780cf-119">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="780cf-119">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [<span data-ttu-id="780cf-120">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="780cf-120">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [<span data-ttu-id="780cf-121">Postupy: použití ukazatelů ke kopírování pole bajtů</span><span class="sxs-lookup"><span data-stu-id="780cf-121">How to: Use Pointers to Copy an Array of Bytes</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [<span data-ttu-id="780cf-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="780cf-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="780cf-123">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="780cf-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="780cf-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="780cf-124">See Also</span></span>  
 [<span data-ttu-id="780cf-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="780cf-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
