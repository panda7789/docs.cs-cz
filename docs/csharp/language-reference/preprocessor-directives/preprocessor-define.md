---
title: '#definování (referenční dokumentace jazyka C#)'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: f40c32a89641256e4f8fe30cd24f523b898139d5
ms.sourcegitcommit: dc02d7d95f1e3efcc7166eaf431b0ec0dc9d8dca
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2018
ms.locfileid: "37143476"
---
# <a name="define-c-reference"></a><span data-ttu-id="c2279-102">#define (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="c2279-102">#define (C# Reference)</span></span>
<span data-ttu-id="c2279-103">Použijete `#define` k definici symbolu.</span><span class="sxs-lookup"><span data-stu-id="c2279-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="c2279-104">Při použití symbolu jako výraz, který je předán [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) direktiv, bude výraz vyhodnocen na `true`, jak je vidět v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c2279-104">When you use the symbol as the expression that's passed to the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="c2279-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c2279-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c2279-106">`#define` – Direktiva nelze použít k deklarování konstantních hodnot, což se většinou děje v jazyce C a C++.</span><span class="sxs-lookup"><span data-stu-id="c2279-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="c2279-107">Konstanty v jazyce C# jsou nejlépe definovány jako statické členy třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="c2279-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="c2279-108">Pokud máte několik takových konstant, zvažte vytvoření samostatné třídy "Konstanty" pro jejich uložení.</span><span class="sxs-lookup"><span data-stu-id="c2279-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="c2279-109">Symboly lze použít k určení podmínek kompilace.</span><span class="sxs-lookup"><span data-stu-id="c2279-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="c2279-110">Můžete vyzkoušet symbol s [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nebo [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="c2279-110">You can test for the symbol with either [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span></span> <span data-ttu-id="c2279-111">Můžete také použít `conditional` atribut má provést Podmíněná kompilace.</span><span class="sxs-lookup"><span data-stu-id="c2279-111">You can also use the `conditional` attribute to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="c2279-112">Můžete definovat symbol, ale nelze přiřadit hodnotu symbolu.</span><span class="sxs-lookup"><span data-stu-id="c2279-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="c2279-113">`#define` Direktiva musí být uvedená v souboru, než použijete pokyny, které nejsou zároveň i direktivy preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="c2279-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="c2279-114">Můžete také definovat symbol s [-definovat](../../../csharp/language-reference/compiler-options/define-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="c2279-114">You can also define a symbol with the [-define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="c2279-115">Můžete nedefinovat symbol s [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="c2279-115">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="c2279-116">Symbol, který definujete pomocí `-define` nebo s `#define` není v rozporu s proměnnou se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="c2279-116">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="c2279-117">To znamená že název proměnné by neměl být předán direktivě preprocesoru a symbol lze vyhodnotit pouze pomocí direktivy preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="c2279-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="c2279-118">Rozsah symbolu, který byl vytvořen pomocí `#define` je soubor, ve kterém byl definován symbol.</span><span class="sxs-lookup"><span data-stu-id="c2279-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="c2279-119">Jak ukazuje následující příklad, je nutné umístit `#define` direktivy v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="c2279-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="c2279-120">Příklad zrušení definice symbolu naleznete v tématu [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="c2279-120">For an example of how to undefine a symbol, see [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2279-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2279-121">See Also</span></span>  
 [<span data-ttu-id="c2279-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="c2279-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="c2279-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="c2279-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c2279-124">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="c2279-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="c2279-125">const</span><span class="sxs-lookup"><span data-stu-id="c2279-125">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
 [<span data-ttu-id="c2279-126">Postupy: Podmíněná kompilace pomocí atributu Trace a Debug</span><span class="sxs-lookup"><span data-stu-id="c2279-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [<span data-ttu-id="c2279-127">#undef</span><span class="sxs-lookup"><span data-stu-id="c2279-127">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
 [<span data-ttu-id="c2279-128">#if</span><span class="sxs-lookup"><span data-stu-id="c2279-128">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
