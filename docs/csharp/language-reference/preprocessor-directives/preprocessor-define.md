---
title: '#definovat - C# Reference'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: c08d6f42c11184a4d14aa6712f9f0f8706a72cab
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173429"
---
# <a name="define-c-reference"></a><span data-ttu-id="d0f65-102">#define (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d0f65-102">#define (C# Reference)</span></span>
<span data-ttu-id="d0f65-103">Slouží `#define` k definování symbolu.</span><span class="sxs-lookup"><span data-stu-id="d0f65-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="d0f65-104">Použijete-li symbol jako výraz, který je předán direktivě [#if,](./preprocessor-if.md) výraz se vyhodnotí na `true`, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="d0f65-104">When you use the symbol as the expression that's passed to the [#if](./preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  

 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="d0f65-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d0f65-105">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d0f65-106">Direktivu `#define` nelze použít k deklarování konstantních hodnot, jak se obvykle provádí v jazycích C a C++.</span><span class="sxs-lookup"><span data-stu-id="d0f65-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="d0f65-107">Konstanty v C# jsou nejlépe definovány jako statické členy třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="d0f65-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="d0f65-108">Pokud máte několik takových konstant, zvažte vytvoření samostatné třídy "Konstanty", která je bude držet.</span><span class="sxs-lookup"><span data-stu-id="d0f65-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="d0f65-109">Symboly lze použít k určení podmínek pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="d0f65-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="d0f65-110">Symbol můžete testovat buď [#if,](./preprocessor-if.md) nebo [#elif](./preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="d0f65-110">You can test for the symbol with either [#if](./preprocessor-if.md) or [#elif](./preprocessor-elif.md).</span></span> <span data-ttu-id="d0f65-111">Můžete také použít <xref:System.Diagnostics.ConditionalAttribute> k provedení podmíněné kompilace.</span><span class="sxs-lookup"><span data-stu-id="d0f65-111">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="d0f65-112">Symbol můžete definovat, ale nelze mu přiřadit hodnotu.</span><span class="sxs-lookup"><span data-stu-id="d0f65-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="d0f65-113">Směrnice `#define` se musí objevit v souboru před použitím pokynů, které nejsou také direktivy preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="d0f65-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="d0f65-114">Můžete také definovat symbol s volbou [-define](../compiler-options/define-compiler-option.md) kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="d0f65-114">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="d0f65-115">Symbol můžete zrušit pomocí [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="d0f65-115">You can undefine a symbol with [#undef](./preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="d0f65-116">Symbol, který definujete `-define` `#define` s nebo s není v konfliktu s proměnnou se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="d0f65-116">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="d0f65-117">To znamená, že název proměnné by neměl být předán direktivě preprocesoru a symbol může být vyhodnocen pouze direktivou preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="d0f65-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="d0f65-118">Rozsah symbolu, který byl `#define` vytvořen pomocí, je soubor, ve kterém byl definován symbol.</span><span class="sxs-lookup"><span data-stu-id="d0f65-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="d0f65-119">Jak ukazuje následující příklad, `#define` je nutné umístit direktivy v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="d0f65-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
```csharp  
#define DEBUG  
//#define TRACE  
#undef TRACE  
  
using System;  
  
public class TestDefine  
{  
    static void Main()  
    {  
#if (DEBUG)  
        Console.WriteLine("Debugging is enabled.");  
#endif  
  
#if (TRACE)  
     Console.WriteLine("Tracing is enabled.");  
#endif  
    }  
}  
// Output:  
// Debugging is enabled.  
```  
  
 <span data-ttu-id="d0f65-120">Příklad zrušení definice symbolu naleznete v [tématu #undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="d0f65-120">For an example of how to undefine a symbol, see [#undef](./preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d0f65-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="d0f65-121">See also</span></span>

- [<span data-ttu-id="d0f65-122">Odkaz jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d0f65-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="d0f65-123">Programovací příručka jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d0f65-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="d0f65-124">Direktivy preprocesoru jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d0f65-124">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="d0f65-125">const</span><span class="sxs-lookup"><span data-stu-id="d0f65-125">const</span></span>](../keywords/const.md)
- [<span data-ttu-id="d0f65-126">Postupy: Podmíněná kompilace pomocí atributu Trace a Debug</span><span class="sxs-lookup"><span data-stu-id="d0f65-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [<span data-ttu-id="d0f65-127">#undef</span><span class="sxs-lookup"><span data-stu-id="d0f65-127">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="d0f65-128">#if</span><span class="sxs-lookup"><span data-stu-id="d0f65-128">#if</span></span>](./preprocessor-if.md)
