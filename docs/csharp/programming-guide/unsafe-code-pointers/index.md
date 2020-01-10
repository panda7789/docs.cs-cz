---
title: Nezabezpečený kód a ukazatele C# – Průvodce programováním
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
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711828"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="a98e9-102">Nezabezpečený kód a ukazateleC# (Průvodce programováním)</span><span class="sxs-lookup"><span data-stu-id="a98e9-102">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="a98e9-103">Aby se zachovala bezpečnost typů a C# zabezpečení, ve výchozím nastavení nepodporuje aritmetický ukazatel.</span><span class="sxs-lookup"><span data-stu-id="a98e9-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="a98e9-104">Pomocí klíčového slova [unsafe](../../language-reference/keywords/unsafe.md) můžete však definovat nezabezpečený kontext, ve kterém mohou být ukazatele použity.</span><span class="sxs-lookup"><span data-stu-id="a98e9-104">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="a98e9-105">Další informace o ukazatelích naleznete v tématu [typy ukazatelů](pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="a98e9-105">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a98e9-106">V modulu CLR (Common Language Runtime) se nezabezpečený kód označuje jako neověřitelný kód.</span><span class="sxs-lookup"><span data-stu-id="a98e9-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="a98e9-107">Nezabezpečený C# kód v nástroji není nutně nebezpečný; je to pouze kód, jehož bezpečnost nemůže být ověřena modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="a98e9-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="a98e9-108">Modul CLR proto spustí pouze nezabezpečený kód, pokud je v plně důvěryhodném sestavení.</span><span class="sxs-lookup"><span data-stu-id="a98e9-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="a98e9-109">Pokud používáte nezabezpečený kód, je vaše zodpovědnost za to, že váš kód nezavádí bezpečnostní rizika nebo chyby ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="a98e9-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="a98e9-110">Přehled nebezpečného kódu</span><span class="sxs-lookup"><span data-stu-id="a98e9-110">Unsafe code overview</span></span>

<span data-ttu-id="a98e9-111">Nezabezpečený kód má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="a98e9-111">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="a98e9-112">Metody, typy a bloky kódu lze definovat jako nebezpečné.</span><span class="sxs-lookup"><span data-stu-id="a98e9-112">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="a98e9-113">V některých případech může nezabezpečený kód zvýšit výkon aplikace odebráním kontrol hranic pole.</span><span class="sxs-lookup"><span data-stu-id="a98e9-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="a98e9-114">Nezabezpečený kód je vyžadován při volání nativních funkcí, které vyžadují ukazatele.</span><span class="sxs-lookup"><span data-stu-id="a98e9-114">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="a98e9-115">Použití nebezpečného kódu zavádí rizika zabezpečení a stability.</span><span class="sxs-lookup"><span data-stu-id="a98e9-115">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="a98e9-116">Kód, který obsahuje nebezpečné bloky, musí být zkompilován s možností [– nezabezpečený](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilátor.</span><span class="sxs-lookup"><span data-stu-id="a98e9-116">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="a98e9-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a98e9-117">Related sections</span></span>

<span data-ttu-id="a98e9-118">Další informace najdete v části .</span><span class="sxs-lookup"><span data-stu-id="a98e9-118">For more information, see:</span></span>

- [<span data-ttu-id="a98e9-119">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="a98e9-119">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="a98e9-120">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="a98e9-120">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="a98e9-121">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="a98e9-121">C# language specification</span></span>

<span data-ttu-id="a98e9-122">Další informace naleznete v tématu věnovaném [nebezpečnému kódu](~/_csharplang/spec/unsafe-code.md) [ C# specifikace jazyka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="a98e9-122">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a98e9-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a98e9-123">See also</span></span>

- [<span data-ttu-id="a98e9-124">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="a98e9-124">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a98e9-125">unsafe</span><span class="sxs-lookup"><span data-stu-id="a98e9-125">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
