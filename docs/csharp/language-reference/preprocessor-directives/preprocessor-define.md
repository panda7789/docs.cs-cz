---
title: '#definovat – C# referenční informace'
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 7457b05ae827675969398792bcb02f025f3028fb
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712582"
---
# <a name="define-c-reference"></a><span data-ttu-id="5fccf-102">#define (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="5fccf-102">#define (C# Reference)</span></span>
<span data-ttu-id="5fccf-103">Použijete `#define` k definování symbolu.</span><span class="sxs-lookup"><span data-stu-id="5fccf-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="5fccf-104">Použijete-li symbol jako výraz, který je předán direktivě [#if](./preprocessor-if.md) , bude výraz vyhodnocen jako `true`, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="5fccf-104">When you use the symbol as the expression that's passed to the [#if](./preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="5fccf-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5fccf-105">Remarks</span></span>  
  
> [!NOTE]
> <span data-ttu-id="5fccf-106">Direktiva `#define` nemůže být použita k deklaraci konstantních hodnot, jak je obvykle prováděna v jazyce C a C++.</span><span class="sxs-lookup"><span data-stu-id="5fccf-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="5fccf-107">Konstanty C# v jsou nejlépe definovány jako statické členy třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="5fccf-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="5fccf-108">Pokud máte několik takových konstant, zvažte vytvoření samostatné třídy "konstanty" pro jejich uložení.</span><span class="sxs-lookup"><span data-stu-id="5fccf-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="5fccf-109">Symboly lze použít k zadání podmínek pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="5fccf-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="5fccf-110">Symbol můžete testovat buď pomocí [#if](./preprocessor-if.md) nebo [#elif](./preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="5fccf-110">You can test for the symbol with either [#if](./preprocessor-if.md) or [#elif](./preprocessor-elif.md).</span></span> <span data-ttu-id="5fccf-111">Můžete také použít <xref:System.Diagnostics.ConditionalAttribute> k provedení podmíněné kompilace.</span><span class="sxs-lookup"><span data-stu-id="5fccf-111">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="5fccf-112">Můžete definovat symbol, ale nelze přiřadit hodnotu k symbolu.</span><span class="sxs-lookup"><span data-stu-id="5fccf-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="5fccf-113">Direktiva `#define` musí být uvedená v souboru předtím, než použijete pokyny, které nejsou také direktivami preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="5fccf-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="5fccf-114">Můžete také definovat symbol pomocí možnosti kompilátoru [-define](../compiler-options/define-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="5fccf-114">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="5fccf-115">Symbol můžete zrušit definováním [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="5fccf-115">You can undefine a symbol with [#undef](./preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="5fccf-116">Symbol definovaný pomocí `-define` nebo with `#define` není v konfliktu s proměnnou stejného názvu.</span><span class="sxs-lookup"><span data-stu-id="5fccf-116">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="5fccf-117">To znamená, že název proměnné by neměl být předán direktivě preprocesoru a symbol lze vyhodnotit pouze pomocí direktivy preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="5fccf-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="5fccf-118">Rozsah symbolu, který byl vytvořen pomocí `#define` je soubor, ve kterém byl symbol definován.</span><span class="sxs-lookup"><span data-stu-id="5fccf-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="5fccf-119">Jak ukazuje následující příklad, je nutné umístit direktivy `#define` v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="5fccf-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="5fccf-120">Příklad, jak zrušit definování symbolu, naleznete v tématu [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="5fccf-120">For an example of how to undefine a symbol, see [#undef](./preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fccf-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5fccf-121">See also</span></span>

- [<span data-ttu-id="5fccf-122">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="5fccf-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="5fccf-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="5fccf-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="5fccf-124">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="5fccf-124">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="5fccf-125">const</span><span class="sxs-lookup"><span data-stu-id="5fccf-125">const</span></span>](../keywords/const.md)
- [<span data-ttu-id="5fccf-126">Postupy: Podmíněná kompilace pomocí atributu Trace a Debug</span><span class="sxs-lookup"><span data-stu-id="5fccf-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [<span data-ttu-id="5fccf-127">#undef</span><span class="sxs-lookup"><span data-stu-id="5fccf-127">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="5fccf-128">#if</span><span class="sxs-lookup"><span data-stu-id="5fccf-128">#if</span></span>](./preprocessor-if.md)
