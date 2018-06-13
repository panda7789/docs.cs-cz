---
title: '#definování (referenční dokumentace jazyka C#)'
ms.date: 07/20/2015
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 1903b96de5f9dfa4efc252897a4a4bd18ed64924
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33286731"
---
# <a name="define-c-reference"></a><span data-ttu-id="190b5-102">#define (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="190b5-102">#define (C# Reference)</span></span>
<span data-ttu-id="190b5-103">Používáte `#define` k definování symbol.</span><span class="sxs-lookup"><span data-stu-id="190b5-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="190b5-104">Při použití symbol jako výraz, který je předán [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) direktivy, výraz vyhodnotí jako `true`, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="190b5-104">When you use the symbol as the expression that's passed to the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="190b5-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="190b5-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="190b5-106">`#define` – Direktiva nelze použít k deklarace konstantní hodnoty, což se většinou děje jazyka C a C++.</span><span class="sxs-lookup"><span data-stu-id="190b5-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="190b5-107">Konstanty v jazyku C# jsou nejlépe definované jako statické členy třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="190b5-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="190b5-108">Pokud máte několik takové konstanty, zvažte vytvoření samostatné třídy "Konstanty" k jejich umístění.</span><span class="sxs-lookup"><span data-stu-id="190b5-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="190b5-109">Symboly můžete použít k určení podmínek pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="190b5-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="190b5-110">Můžete otestovat pro symbol s buď [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nebo [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="190b5-110">You can test for the symbol with either [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span></span> <span data-ttu-id="190b5-111">Můžete také `conditional` atribut provést Podmíněná kompilace.</span><span class="sxs-lookup"><span data-stu-id="190b5-111">You can also use the `conditional` attribute to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="190b5-112">Můžete definovat symbol, ale nelze přiřadit hodnotu symbol.</span><span class="sxs-lookup"><span data-stu-id="190b5-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="190b5-113">`#define` – Direktiva musí být v souboru dříve, než použijete žádné pokyny, které nejsou také preprocesor – direktivy.</span><span class="sxs-lookup"><span data-stu-id="190b5-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="190b5-114">Můžete také definovat symbol s [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="190b5-114">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="190b5-115">Můžete nedefinované symbol s [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="190b5-115">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="190b5-116">Symbol, který definujete s `/define` nebo s `#define` není v konfliktu s proměnné se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="190b5-116">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="190b5-117">To znamená název proměnné nesmí být předaný direktivy preprocesoru a symbol lze vyhodnotit pouze direktivy preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="190b5-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="190b5-118">Rozsah symbol, který byl vytvořen pomocí `#define` je soubor, ve které byla definována symbolu.</span><span class="sxs-lookup"><span data-stu-id="190b5-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="190b5-119">Jak ukazuje následující příklad, musíte umístit `#define` direktivy v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="190b5-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="190b5-120">Příklad toho, jak nedefinované symbol, naleznete v části [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="190b5-120">For an example of how to undefine a symbol, see [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="190b5-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="190b5-121">See Also</span></span>  
 [<span data-ttu-id="190b5-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="190b5-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="190b5-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="190b5-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="190b5-124">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="190b5-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="190b5-125">const</span><span class="sxs-lookup"><span data-stu-id="190b5-125">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
 [<span data-ttu-id="190b5-126">Postupy: Podmíněná kompilace pomocí atributu Trace a Debug</span><span class="sxs-lookup"><span data-stu-id="190b5-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [<span data-ttu-id="190b5-127">#undef</span><span class="sxs-lookup"><span data-stu-id="190b5-127">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
 [<span data-ttu-id="190b5-128">#if</span><span class="sxs-lookup"><span data-stu-id="190b5-128">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
