---
description: '#define – reference jazyka C#'
title: '#define – reference jazyka C#'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: a37f883a249ec74b66769ee40b84b20e8568c451
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/30/2020
ms.locfileid: "89132336"
---
# <a name="define-c-reference"></a><span data-ttu-id="9c1e7-103">#define (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9c1e7-103">#define (C# Reference)</span></span>
<span data-ttu-id="9c1e7-104">Použijte `#define` k definování symbolu.</span><span class="sxs-lookup"><span data-stu-id="9c1e7-104">You use `#define` to define a symbol.</span></span> <span data-ttu-id="9c1e7-105">Použijete-li symbol jako výraz, který je předán direktivě [#if](./preprocessor-if.md) , výraz se vyhodnotí na `true` , jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="9c1e7-105">When you use the symbol as the expression that's passed to the [#if](./preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  

 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="9c1e7-106">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9c1e7-106">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9c1e7-107">`#define`Direktiva nemůže být použita k deklaraci konstantních hodnot, jak je obvykle prováděna v jazyce C a C++.</span><span class="sxs-lookup"><span data-stu-id="9c1e7-107">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="9c1e7-108">Konstanty v jazyce C# jsou nejlépe definovány jako statické členy třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="9c1e7-108">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="9c1e7-109">Pokud máte několik takových konstant, zvažte vytvoření samostatné třídy "konstanty" pro jejich uložení.</span><span class="sxs-lookup"><span data-stu-id="9c1e7-109">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="9c1e7-110">Symboly lze použít k zadání podmínek pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="9c1e7-110">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="9c1e7-111">Symbol můžete testovat buď pomocí [#if](./preprocessor-if.md) nebo [#elif](./preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="9c1e7-111">You can test for the symbol with either [#if](./preprocessor-if.md) or [#elif](./preprocessor-elif.md).</span></span> <span data-ttu-id="9c1e7-112">Můžete také použít <xref:System.Diagnostics.ConditionalAttribute> k provedení podmíněné kompilace.</span><span class="sxs-lookup"><span data-stu-id="9c1e7-112">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="9c1e7-113">Můžete definovat symbol, ale nelze přiřadit hodnotu k symbolu.</span><span class="sxs-lookup"><span data-stu-id="9c1e7-113">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="9c1e7-114">`#define`Direktiva musí být uvedena v souboru předtím, než použijete pokyny, které nejsou také direktivami preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="9c1e7-114">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="9c1e7-115">Můžete také definovat symbol pomocí možnosti kompilátoru [-define](../compiler-options/define-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="9c1e7-115">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="9c1e7-116">Symbol můžete zrušit definováním [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="9c1e7-116">You can undefine a symbol with [#undef](./preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="9c1e7-117">Symbol, který definujete pomocí `-define` nebo s, `#define` není v konfliktu s proměnnou stejného názvu.</span><span class="sxs-lookup"><span data-stu-id="9c1e7-117">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="9c1e7-118">To znamená, že název proměnné by neměl být předán direktivě preprocesoru a symbol lze vyhodnotit pouze pomocí direktivy preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="9c1e7-118">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="9c1e7-119">Rozsah symbolu, který byl vytvořen pomocí, `#define` je soubor, ve kterém byl symbol definován.</span><span class="sxs-lookup"><span data-stu-id="9c1e7-119">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="9c1e7-120">Jak ukazuje následující příklad, je nutné umístit `#define` direktivy v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="9c1e7-120">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="9c1e7-121">Příklad, jak zrušit definování symbolu, naleznete v tématu [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="9c1e7-121">For an example of how to undefine a symbol, see [#undef](./preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9c1e7-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="9c1e7-122">See also</span></span>

- [<span data-ttu-id="9c1e7-123">Reference jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9c1e7-123">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="9c1e7-124">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="9c1e7-124">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="9c1e7-125">C# – direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="9c1e7-125">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="9c1e7-126">const</span><span class="sxs-lookup"><span data-stu-id="9c1e7-126">const</span></span>](../keywords/const.md)
- [<span data-ttu-id="9c1e7-127">Postupy: Podmíněná kompilace pomocí atributu Trace a Debug</span><span class="sxs-lookup"><span data-stu-id="9c1e7-127">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [<span data-ttu-id="9c1e7-128">#undef</span><span class="sxs-lookup"><span data-stu-id="9c1e7-128">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="9c1e7-129">#if</span><span class="sxs-lookup"><span data-stu-id="9c1e7-129">#if</span></span>](./preprocessor-if.md)
