---
title: Nezabezpečený kód a ukazatele – C# Průvodce programováním
ms.custom: seodec18
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
ms.openlocfilehash: 7d7371fb29f12a766ef6b78544f82d021dd8dceb
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237906"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="3942d-102">Nezabezpečený kód a ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="3942d-102">Unsafe Code and Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="3942d-103">Pokud chcete zachovat bezpečnost typů a zabezpečení, C# nepodporuje aritmetiku ukazatele ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="3942d-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="3942d-104">Nicméně pomocí [nebezpečné](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo, můžete definovat nezabezpečený kontext, ve které je možné ukazatele.</span><span class="sxs-lookup"><span data-stu-id="3942d-104">However, by using the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="3942d-105">Další informace o ukazatelích naleznete v tématu [typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="3942d-105">For more information about pointers, see the topic [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3942d-106">V modulu common language runtime (CLR) nebezpečný kód se označuje jako neověřitelný kód.</span><span class="sxs-lookup"><span data-stu-id="3942d-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="3942d-107">Nezabezpečený kód v jazyce C# není nutně nebezpečné; je jenom kód, jejichž zabezpečení nelze ověřit pomocí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="3942d-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="3942d-108">Modul CLR proto pouze spustí nezabezpečený kód by byl v plně důvěryhodná sestavení.</span><span class="sxs-lookup"><span data-stu-id="3942d-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="3942d-109">Pokud používáte nebezpečný kód, je vaší povinností ujistit, že váš kód nezavádí rizika zabezpečení nebo ukazatel chyby.</span><span class="sxs-lookup"><span data-stu-id="3942d-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="3942d-110">Přehled nebezpečného kódu</span><span class="sxs-lookup"><span data-stu-id="3942d-110">Unsafe Code Overview</span></span>  
 <span data-ttu-id="3942d-111">Nezabezpečený kód má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="3942d-111">Unsafe code has the following properties:</span></span>  
  
-   <span data-ttu-id="3942d-112">Metody, typy a bloků kódu může být definován jako bezpečné.</span><span class="sxs-lookup"><span data-stu-id="3942d-112">Methods, types, and code blocks can be defined as unsafe.</span></span>  
  
-   <span data-ttu-id="3942d-113">V některých případech může nezabezpečený kód zvýšit výkon vaší aplikace tak, že odeberete kontroly hranice pole.</span><span class="sxs-lookup"><span data-stu-id="3942d-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>  
  
-   <span data-ttu-id="3942d-114">Nezabezpečený kód je potřeba při volání nativních funkcí, které vyžadují ukazatele.</span><span class="sxs-lookup"><span data-stu-id="3942d-114">Unsafe code is required when you call native functions that require pointers.</span></span>  
  
-   <span data-ttu-id="3942d-115">Použití nezabezpečeného kódu představuje rizika zabezpečení a stabilitu.</span><span class="sxs-lookup"><span data-stu-id="3942d-115">Using unsafe code introduces security and stability risks.</span></span>  
  
-   <span data-ttu-id="3942d-116">V pořadí pro jazyk C# ke kompilaci nezabezpečený kód aplikace musí být kompilována s [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="3942d-116">In order for C# to compile unsafe code, the application must be compiled with [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3942d-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3942d-117">Related Sections</span></span>  
 <span data-ttu-id="3942d-118">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="3942d-118">For more information, see:</span></span>  
  
-   [<span data-ttu-id="3942d-119">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="3942d-119">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [<span data-ttu-id="3942d-120">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="3942d-120">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [<span data-ttu-id="3942d-121">Postupy: Použití ukazatelů ke kopírování pole bajtů</span><span class="sxs-lookup"><span data-stu-id="3942d-121">How to: Use Pointers to Copy an Array of Bytes</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [<span data-ttu-id="3942d-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="3942d-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="3942d-123">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="3942d-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3942d-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="3942d-124">See Also</span></span>

- [<span data-ttu-id="3942d-125">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="3942d-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
