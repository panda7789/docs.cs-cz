---
title: "#<a name=\"define-c-reference\"></a>definování (referenční dokumentace jazyka C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '#define'
helpviewer_keywords: '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
caps.latest.revision: "22"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ae72a1b6c19421c51348a0d93691ba3fe29a191c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="define-c-reference"></a><span data-ttu-id="322c7-102">#define (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="322c7-102">#define (C# Reference)</span></span>
<span data-ttu-id="322c7-103">Používáte `#define` k definování symbol.</span><span class="sxs-lookup"><span data-stu-id="322c7-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="322c7-104">Při použití symbol jako výraz, který je předán [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) direktivy, výraz vyhodnotí jako `true`, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="322c7-104">When you use the symbol as the expression that's passed to the [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="322c7-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="322c7-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="322c7-106">`#define` – Direktiva nelze použít k deklarace konstantní hodnoty, což se většinou děje jazyka C a C++.</span><span class="sxs-lookup"><span data-stu-id="322c7-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="322c7-107">Konstanty v jazyku C# jsou nejlépe definované jako statické členy třídě nebo struktuře.</span><span class="sxs-lookup"><span data-stu-id="322c7-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="322c7-108">Pokud máte několik takové konstanty, zvažte vytvoření samostatné třídy "Konstanty" k jejich umístění.</span><span class="sxs-lookup"><span data-stu-id="322c7-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="322c7-109">Symboly můžete použít k určení podmínek pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="322c7-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="322c7-110">Můžete otestovat pro symbol s buď [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) nebo [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="322c7-110">You can test for the symbol with either [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md) or [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md).</span></span> <span data-ttu-id="322c7-111">Můžete také `conditional` atribut provést Podmíněná kompilace.</span><span class="sxs-lookup"><span data-stu-id="322c7-111">You can also use the `conditional` attribute to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="322c7-112">Můžete definovat symbol, ale nelze přiřadit hodnotu symbol.</span><span class="sxs-lookup"><span data-stu-id="322c7-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="322c7-113">`#define` – Direktiva musí být v souboru dříve, než použijete žádné pokyny, které nejsou také preprocesor – direktivy.</span><span class="sxs-lookup"><span data-stu-id="322c7-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="322c7-114">Můžete také definovat symbol s [/ define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) – možnost kompilátoru.</span><span class="sxs-lookup"><span data-stu-id="322c7-114">You can also define a symbol with the [/define](../../../csharp/language-reference/compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="322c7-115">Můžete nedefinované symbol s [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="322c7-115">You can undefine a symbol with [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="322c7-116">Symbol, který definujete s `/define` nebo s `#define` není v konfliktu s proměnné se stejným názvem.</span><span class="sxs-lookup"><span data-stu-id="322c7-116">A symbol that you define with `/define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="322c7-117">To znamená název proměnné nesmí být předaný direktivy preprocesoru a symbol lze vyhodnotit pouze direktivy preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="322c7-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="322c7-118">Rozsah symbol, který byl vytvořen pomocí `#define` je soubor, ve které byla definována symbolu.</span><span class="sxs-lookup"><span data-stu-id="322c7-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="322c7-119">Jak ukazuje následující příklad, musíte umístit `#define` direktivy v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="322c7-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="322c7-120">Příklad toho, jak nedefinované symbol, naleznete v části [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="322c7-120">For an example of how to undefine a symbol, see [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="322c7-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="322c7-121">See Also</span></span>  
 [<span data-ttu-id="322c7-122">Referenční dokumentace jazyka C#</span><span class="sxs-lookup"><span data-stu-id="322c7-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="322c7-123">Průvodce programováním v C#</span><span class="sxs-lookup"><span data-stu-id="322c7-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="322c7-124">C# direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="322c7-124">C# Preprocessor Directives</span></span>](../../../csharp/language-reference/preprocessor-directives/index.md)  
 [<span data-ttu-id="322c7-125">Const</span><span class="sxs-lookup"><span data-stu-id="322c7-125">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
 [<span data-ttu-id="322c7-126">Postupy: Podmíněná kompilace pomocí trasování a ladění</span><span class="sxs-lookup"><span data-stu-id="322c7-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)  
 [<span data-ttu-id="322c7-127">#undef</span><span class="sxs-lookup"><span data-stu-id="322c7-127">#undef</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md)  
 [<span data-ttu-id="322c7-128">#if</span><span class="sxs-lookup"><span data-stu-id="322c7-128">#if</span></span>](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md)
