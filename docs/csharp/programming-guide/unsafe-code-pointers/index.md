---
title: Nezabezpečený kód a ukazatele – C# Průvodce programováním pro službu
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
ms.openlocfilehash: 99f0b925a37bff8b6ab1ff46e9ce2f0ea0a38aed
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/21/2019
ms.locfileid: "65959478"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="2d633-102">Nezabezpečený kód a ukazatele (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="2d633-102">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="2d633-103">Pokud chcete zachovat bezpečnost typů a zabezpečení, C# nepodporuje aritmetiku ukazatele ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="2d633-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="2d633-104">Nicméně pomocí [nebezpečné](../../language-reference/keywords/unsafe.md) – klíčové slovo, můžete definovat nezabezpečený kontext, ve které je možné ukazatele.</span><span class="sxs-lookup"><span data-stu-id="2d633-104">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="2d633-105">Další informace o ukazatelích naleznete v tématu [typy ukazatelů](pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="2d633-105">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2d633-106">V modulu common language runtime (CLR) nebezpečný kód se označuje jako neověřitelný kód.</span><span class="sxs-lookup"><span data-stu-id="2d633-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="2d633-107">Nezabezpečený kód v jazyce C# není nutně nebezpečné; je jenom kód, jejichž zabezpečení nelze ověřit pomocí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="2d633-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="2d633-108">Modul CLR proto pouze spustí nezabezpečený kód by byl v plně důvěryhodná sestavení.</span><span class="sxs-lookup"><span data-stu-id="2d633-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="2d633-109">Pokud používáte nebezpečný kód, je vaší povinností ujistit, že váš kód nezavádí rizika zabezpečení nebo ukazatel chyby.</span><span class="sxs-lookup"><span data-stu-id="2d633-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="2d633-110">Přehled nebezpečného kódu</span><span class="sxs-lookup"><span data-stu-id="2d633-110">Unsafe code overview</span></span>

<span data-ttu-id="2d633-111">Nezabezpečený kód má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2d633-111">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="2d633-112">Metody, typy a bloků kódu může být definován jako bezpečné.</span><span class="sxs-lookup"><span data-stu-id="2d633-112">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="2d633-113">V některých případech může nezabezpečený kód zvýšit výkon vaší aplikace tak, že odeberete kontroly hranice pole.</span><span class="sxs-lookup"><span data-stu-id="2d633-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="2d633-114">Nezabezpečený kód je potřeba při volání nativních funkcí, které vyžadují ukazatele.</span><span class="sxs-lookup"><span data-stu-id="2d633-114">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="2d633-115">Použití nezabezpečeného kódu představuje rizika zabezpečení a stabilitu.</span><span class="sxs-lookup"><span data-stu-id="2d633-115">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="2d633-116">Kód, který obsahuje nebezpečné bloky musí být kompilována s [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2d633-116">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="2d633-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2d633-117">Related sections</span></span>

<span data-ttu-id="2d633-118">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="2d633-118">For more information, see:</span></span>

- [<span data-ttu-id="2d633-119">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="2d633-119">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="2d633-120">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="2d633-120">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="2d633-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2d633-121">C# language specification</span></span>

<span data-ttu-id="2d633-122">Další informace najdete v tématu [nezabezpečený kód](~/_csharplang/spec/unsafe-code.md) téma [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2d633-122">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2d633-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2d633-123">See also</span></span>

- [<span data-ttu-id="2d633-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="2d633-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2d633-125">unsafe</span><span class="sxs-lookup"><span data-stu-id="2d633-125">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
