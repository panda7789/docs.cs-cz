---
title: Nebezpečný kód a ukazatele – průvodce programováním jazyka C#
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
ms.openlocfilehash: 013af4e55c8fc396bbc92058d7fb454484f3263e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "75711828"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="2049a-102">Nebezpečný kód a ukazatele (Průvodce programováním jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="2049a-102">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="2049a-103">Chcete-li zachovat zabezpečení typu, C# nepodporuje aritmetické ukazatele, ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="2049a-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="2049a-104">Pomocí [nebezpečného](../../language-reference/keywords/unsafe.md) klíčového slova však můžete definovat nebezpečný kontext, ve kterém lze použít ukazatele.</span><span class="sxs-lookup"><span data-stu-id="2049a-104">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="2049a-105">Další informace o ukazatelích naleznete v tématu [Pointer types](pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="2049a-105">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="2049a-106">V clr (common language runtime) se nebezpečný kód označuje jako neověřitelný kód.</span><span class="sxs-lookup"><span data-stu-id="2049a-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="2049a-107">Nebezpečný kód v c# není nutně nebezpečné; je to jen kód, jehož bezpečnost nelze ověřit CLR.</span><span class="sxs-lookup"><span data-stu-id="2049a-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="2049a-108">CLR proto spustí pouze nebezpečný kód, pokud je v plně důvěryhodném sestavení.</span><span class="sxs-lookup"><span data-stu-id="2049a-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="2049a-109">Pokud používáte nebezpečný kód, je vaší odpovědností zajistit, aby váš kód nezaváděl bezpečnostní rizika nebo chyby ukazatele.</span><span class="sxs-lookup"><span data-stu-id="2049a-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="2049a-110">Přehled nebezpečných kódů</span><span class="sxs-lookup"><span data-stu-id="2049a-110">Unsafe code overview</span></span>

<span data-ttu-id="2049a-111">Nebezpečný kód má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="2049a-111">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="2049a-112">Metody, typy a bloky kódu lze definovat jako nebezpečné.</span><span class="sxs-lookup"><span data-stu-id="2049a-112">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="2049a-113">V některých případech může nebezpečný kód zvýšit výkon aplikace odebráním kontroly hranice pole.</span><span class="sxs-lookup"><span data-stu-id="2049a-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="2049a-114">Nebezpečný kód je vyžadován při volání nativních funkcí, které vyžadují ukazatele.</span><span class="sxs-lookup"><span data-stu-id="2049a-114">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="2049a-115">Použití nebezpečného kódu představuje bezpečnostní a stabilizační rizika.</span><span class="sxs-lookup"><span data-stu-id="2049a-115">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="2049a-116">Kód, který obsahuje nebezpečné bloky, musí být zkompilován s možností [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="2049a-116">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="2049a-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="2049a-117">Related sections</span></span>

<span data-ttu-id="2049a-118">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="2049a-118">For more information, see:</span></span>

- [<span data-ttu-id="2049a-119">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="2049a-119">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="2049a-120">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="2049a-120">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="2049a-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2049a-121">C# language specification</span></span>

<span data-ttu-id="2049a-122">Další informace naleznete v tématu [nebezpečný kód](~/_csharplang/spec/unsafe-code.md) specifikace [jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="2049a-122">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="2049a-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="2049a-123">See also</span></span>

- [<span data-ttu-id="2049a-124">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="2049a-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="2049a-125">unsafe</span><span class="sxs-lookup"><span data-stu-id="2049a-125">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
