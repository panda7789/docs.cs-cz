---
title: Nezabezpečený kód a ukazatele – Průvodce programováním v C#
Description: Seznamte se s nebezpečným kódem a ukazateli. Jazyk C# nepodporuje ukazatele, ale můžete definovat nezabezpečený kontext, ve kterém mohou být ukazatele použity s klíčovým slovem unsafe.
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
ms.openlocfilehash: 5684a97ed6f7b6632d8fe3d52747d9187c4b8cbc
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381772"
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="03949-104">Nezabezpečený kód a ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="03949-104">Unsafe code and pointers (C# Programming Guide)</span></span>

<span data-ttu-id="03949-105">Aby bylo možné zachovat bezpečnost typů a zabezpečení, C# ve výchozím nastavení nepodporuje aritmetické operace s ukazatelem.</span><span class="sxs-lookup"><span data-stu-id="03949-105">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="03949-106">Pomocí klíčového slova [unsafe](../../language-reference/keywords/unsafe.md) můžete však definovat nezabezpečený kontext, ve kterém mohou být ukazatele použity.</span><span class="sxs-lookup"><span data-stu-id="03949-106">However, by using the [unsafe](../../language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="03949-107">Další informace o ukazatelích naleznete v tématu [typy ukazatelů](pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="03949-107">For more information about pointers, see [Pointer types](pointer-types.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="03949-108">V modulu CLR (Common Language Runtime) se nezabezpečený kód označuje jako neověřitelný kód.</span><span class="sxs-lookup"><span data-stu-id="03949-108">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="03949-109">Nezabezpečený kód v jazyce C# není nutně nebezpečný; je to pouze kód, jehož bezpečnost nemůže být ověřena modulem CLR.</span><span class="sxs-lookup"><span data-stu-id="03949-109">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="03949-110">Modul CLR proto spustí pouze nezabezpečený kód, pokud je v plně důvěryhodném sestavení.</span><span class="sxs-lookup"><span data-stu-id="03949-110">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="03949-111">Pokud používáte nezabezpečený kód, je vaše zodpovědnost za to, že váš kód nezavádí bezpečnostní rizika nebo chyby ukazatelů.</span><span class="sxs-lookup"><span data-stu-id="03949-111">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="03949-112">Přehled nebezpečného kódu</span><span class="sxs-lookup"><span data-stu-id="03949-112">Unsafe code overview</span></span>

<span data-ttu-id="03949-113">Nezabezpečený kód má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="03949-113">Unsafe code has the following properties:</span></span>

- <span data-ttu-id="03949-114">Metody, typy a bloky kódu lze definovat jako nebezpečné.</span><span class="sxs-lookup"><span data-stu-id="03949-114">Methods, types, and code blocks can be defined as unsafe.</span></span>

- <span data-ttu-id="03949-115">V některých případech může nezabezpečený kód zvýšit výkon aplikace odebráním kontrol hranic pole.</span><span class="sxs-lookup"><span data-stu-id="03949-115">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>

- <span data-ttu-id="03949-116">Nezabezpečený kód je vyžadován při volání nativních funkcí, které vyžadují ukazatele.</span><span class="sxs-lookup"><span data-stu-id="03949-116">Unsafe code is required when you call native functions that require pointers.</span></span>

- <span data-ttu-id="03949-117">Použití nebezpečného kódu zavádí rizika zabezpečení a stability.</span><span class="sxs-lookup"><span data-stu-id="03949-117">Using unsafe code introduces security and stability risks.</span></span>

- <span data-ttu-id="03949-118">Kód, který obsahuje nebezpečné bloky, musí být zkompilován s možností [– nezabezpečený](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilátor.</span><span class="sxs-lookup"><span data-stu-id="03949-118">The code that contains unsafe blocks must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>
  
## <a name="related-sections"></a><span data-ttu-id="03949-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="03949-119">Related sections</span></span>

<span data-ttu-id="03949-120">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="03949-120">For more information, see:</span></span>

- [<span data-ttu-id="03949-121">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="03949-121">Pointer types</span></span>](pointer-types.md)

- [<span data-ttu-id="03949-122">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="03949-122">Fixed size buffers</span></span>](fixed-size-buffers.md)

## <a name="c-language-specification"></a><span data-ttu-id="03949-123">specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="03949-123">C# language specification</span></span>

<span data-ttu-id="03949-124">Další informace naleznete v tématu [nezabezpečeného kódu](~/_csharplang/spec/unsafe-code.md) [specifikace jazyka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="03949-124">For more information, see the [Unsafe code](~/_csharplang/spec/unsafe-code.md) topic of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>
  
## <a name="see-also"></a><span data-ttu-id="03949-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03949-125">See also</span></span>

- [<span data-ttu-id="03949-126">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="03949-126">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="03949-127">UNSAFE</span><span class="sxs-lookup"><span data-stu-id="03949-127">unsafe</span></span>](../../language-reference/keywords/unsafe.md)
