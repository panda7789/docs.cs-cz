---
title: "Nezabezpečený kód a ukazatele (Průvodce programováním v C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- security [C#], type safety
- C# language, unsafe code
- type safety [C#]
- unsafe keyword [C#]
- unsafe code [C#]
- C# language, pointers
- pointers [C#], about pointers
ms.assetid: b0fcca10-a92d-4f2a-835b-b0ccae6739ee
caps.latest.revision: "24"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 32856461fbc6513509342a3567240de723f1fe8f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="unsafe-code-and-pointers-c-programming-guide"></a><span data-ttu-id="5b3b0-102">Nezabezpečený kód a ukazatele (Průvodce programováním v C#)</span><span class="sxs-lookup"><span data-stu-id="5b3b0-102">Unsafe Code and Pointers (C# Programming Guide)</span></span>
<span data-ttu-id="5b3b0-103">Pokud chcete zachovat bezpečnost typů a zabezpečení, C# nepodporuje aritmetika ukazatele ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="5b3b0-103">To maintain type safety and security, C# does not support pointer arithmetic, by default.</span></span> <span data-ttu-id="5b3b0-104">Avšak pomocí [unsafe](../../../csharp/language-reference/keywords/unsafe.md) – klíčové slovo, můžete definovat kontextu unsafe, ve které je možné ukazatele.</span><span class="sxs-lookup"><span data-stu-id="5b3b0-104">However, by using the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, you can define an unsafe context in which pointers can be used.</span></span> <span data-ttu-id="5b3b0-105">Další informace o ukazatele, naleznete v tématu [typy ukazatelů](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span><span class="sxs-lookup"><span data-stu-id="5b3b0-105">For more information about pointers, see the topic [Pointer types](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5b3b0-106">V common language runtime (CLR) nezabezpečený kód se označuje jako neověřitelný kód.</span><span class="sxs-lookup"><span data-stu-id="5b3b0-106">In the common language runtime (CLR), unsafe code is referred to as unverifiable code.</span></span> <span data-ttu-id="5b3b0-107">Nezabezpečený kód v jazyce C# není nutně nebezpečné; je pouze kód, jejichž zabezpečení nelze ověřit pomocí modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="5b3b0-107">Unsafe code in C# is not necessarily dangerous; it is just code whose safety cannot be verified by the CLR.</span></span> <span data-ttu-id="5b3b0-108">Modul CLR bude proto pouze spouštění nezabezpečený kód Pokud je ve plně důvěryhodné sestavení.</span><span class="sxs-lookup"><span data-stu-id="5b3b0-108">The CLR will therefore only execute unsafe code if it is in a fully trusted assembly.</span></span> <span data-ttu-id="5b3b0-109">Pokud používáte nezabezpečený kód, je vaší povinností ujistit, že váš kód nezavádí rizika zabezpečení nebo chyby ukazatele.</span><span class="sxs-lookup"><span data-stu-id="5b3b0-109">If you use unsafe code, it is your responsibility to ensure that your code does not introduce security risks or pointer errors.</span></span>  
  
## <a name="unsafe-code-overview"></a><span data-ttu-id="5b3b0-110">Přehled nebezpečného kódu</span><span class="sxs-lookup"><span data-stu-id="5b3b0-110">Unsafe Code Overview</span></span>  
 <span data-ttu-id="5b3b0-111">Nezabezpečený kód má následující vlastnosti:</span><span class="sxs-lookup"><span data-stu-id="5b3b0-111">Unsafe code has the following properties:</span></span>  
  
-   <span data-ttu-id="5b3b0-112">Metody, typy a bloky kódu je možné definovat jako bezpečné.</span><span class="sxs-lookup"><span data-stu-id="5b3b0-112">Methods, types, and code blocks can be defined as unsafe.</span></span>  
  
-   <span data-ttu-id="5b3b0-113">V některých případech může nezabezpečený kód zvýšit výkon aplikace odebráním kontroly meze pole.</span><span class="sxs-lookup"><span data-stu-id="5b3b0-113">In some cases, unsafe code may increase an application's performance by removing array bounds checks.</span></span>  
  
-   <span data-ttu-id="5b3b0-114">Nezabezpečený kód je potřeba při volání nativních funkcí, které vyžadují ukazatele.</span><span class="sxs-lookup"><span data-stu-id="5b3b0-114">Unsafe code is required when you call native functions that require pointers.</span></span>  
  
-   <span data-ttu-id="5b3b0-115">Nezabezpečený kód představuje riziko zabezpečení a stability.</span><span class="sxs-lookup"><span data-stu-id="5b3b0-115">Using unsafe code introduces security and stability risks.</span></span>  
  
-   <span data-ttu-id="5b3b0-116">V pořadí pro jazyk C# zkompilovat nezabezpečený kód, aplikace musí být zkompilovány s [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span><span class="sxs-lookup"><span data-stu-id="5b3b0-116">In order for C# to compile unsafe code, the application must be compiled with [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md).</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="5b3b0-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="5b3b0-117">Related Sections</span></span>  
 <span data-ttu-id="5b3b0-118">Další informace naleznete v tématu:</span><span class="sxs-lookup"><span data-stu-id="5b3b0-118">For more information, see:</span></span>  
  
-   [<span data-ttu-id="5b3b0-119">Typy ukazatelů</span><span class="sxs-lookup"><span data-stu-id="5b3b0-119">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
  
-   [<span data-ttu-id="5b3b0-120">Vyrovnávací paměti pevné velikosti</span><span class="sxs-lookup"><span data-stu-id="5b3b0-120">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)  
  
-   [<span data-ttu-id="5b3b0-121">Postupy: použití ukazatelů ke kopírování pole bajtů</span><span class="sxs-lookup"><span data-stu-id="5b3b0-121">How to: Use Pointers to Copy an Array of Bytes</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/how-to-use-pointers-to-copy-an-array-of-bytes.md)  
  
-   [<span data-ttu-id="5b3b0-122">nezabezpečený</span><span class="sxs-lookup"><span data-stu-id="5b3b0-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="5b3b0-123">Specifikace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="5b3b0-123">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5b3b0-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="5b3b0-124">See Also</span></span>  
 [<span data-ttu-id="5b3b0-125">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="5b3b0-125">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
