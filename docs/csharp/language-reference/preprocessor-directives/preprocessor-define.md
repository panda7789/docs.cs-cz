---
title: '#definovat – C# referenční informace'
ms.custom: seodec18
ms.date: 06/30/2018
f1_keywords:
- '#define'
helpviewer_keywords:
- '#define directive [C#]'
ms.assetid: 23638b8f-779c-450e-b600-d55682de7d01
ms.openlocfilehash: 5de8dc62e352d669c8008fa5ab8477799843375c
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2019
ms.locfileid: "69605789"
---
# <a name="define-c-reference"></a><span data-ttu-id="39867-102">#define (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="39867-102">#define (C# Reference)</span></span>
<span data-ttu-id="39867-103">Použijte `#define` k definování symbolu.</span><span class="sxs-lookup"><span data-stu-id="39867-103">You use `#define` to define a symbol.</span></span> <span data-ttu-id="39867-104">Použijete-li symbol jako výraz, který je předán direktivě [#if](./preprocessor-if.md) , výraz se vyhodnotí na `true`, jak ukazuje následující příklad:</span><span class="sxs-lookup"><span data-stu-id="39867-104">When you use the symbol as the expression that's passed to the [#if](./preprocessor-if.md) directive, the expression will evaluate to `true`, as the following example shows:</span></span>  
 
 ```csharp
 #define DEBUG
 ```
  
## <a name="remarks"></a><span data-ttu-id="39867-105">Poznámky</span><span class="sxs-lookup"><span data-stu-id="39867-105">Remarks</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="39867-106">Direktiva se nedá použít k deklaraci konstantních hodnot, jak se obvykle provádí v C a C++ `#define`</span><span class="sxs-lookup"><span data-stu-id="39867-106">The `#define` directive cannot be used to declare constant values as is typically done in C and C++.</span></span> <span data-ttu-id="39867-107">Konstanty C# v jsou nejlépe definovány jako statické členy třídy nebo struktury.</span><span class="sxs-lookup"><span data-stu-id="39867-107">Constants in C# are best defined as static members of a class or struct.</span></span> <span data-ttu-id="39867-108">Pokud máte několik takových konstant, zvažte vytvoření samostatné třídy "konstanty" pro jejich uložení.</span><span class="sxs-lookup"><span data-stu-id="39867-108">If you have several such constants, consider creating a separate "Constants" class to hold them.</span></span>  
  
 <span data-ttu-id="39867-109">Symboly lze použít k zadání podmínek pro kompilaci.</span><span class="sxs-lookup"><span data-stu-id="39867-109">Symbols can be used to specify conditions for compilation.</span></span> <span data-ttu-id="39867-110">Symbol můžete testovat buď pomocí [#if](./preprocessor-if.md) nebo [#elif](./preprocessor-elif.md).</span><span class="sxs-lookup"><span data-stu-id="39867-110">You can test for the symbol with either [#if](./preprocessor-if.md) or [#elif](./preprocessor-elif.md).</span></span> <span data-ttu-id="39867-111">Můžete také použít <xref:System.Diagnostics.ConditionalAttribute> k provedení podmíněné kompilace.</span><span class="sxs-lookup"><span data-stu-id="39867-111">You can also use the <xref:System.Diagnostics.ConditionalAttribute> to perform conditional compilation.</span></span>  
  
 <span data-ttu-id="39867-112">Můžete definovat symbol, ale nelze přiřadit hodnotu k symbolu.</span><span class="sxs-lookup"><span data-stu-id="39867-112">You can define a symbol, but you cannot assign a value to a symbol.</span></span> <span data-ttu-id="39867-113">`#define` Direktiva musí být uvedena v souboru předtím, než použijete pokyny, které nejsou také direktivami preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="39867-113">The `#define` directive must appear in the file before you use any instructions that aren't also preprocessor directives.</span></span>  
  
 <span data-ttu-id="39867-114">Můžete také definovat symbol pomocí možnosti kompilátoru [-define](../compiler-options/define-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="39867-114">You can also define a symbol with the [-define](../compiler-options/define-compiler-option.md) compiler option.</span></span> <span data-ttu-id="39867-115">Symbol můžete zrušit definováním [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="39867-115">You can undefine a symbol with [#undef](./preprocessor-undef.md).</span></span>  
  
 <span data-ttu-id="39867-116">Symbol, který definujete pomocí `-define` nebo s `#define` , není v konfliktu s proměnnou stejného názvu.</span><span class="sxs-lookup"><span data-stu-id="39867-116">A symbol that you define with `-define` or with `#define` does not conflict with a variable of the same name.</span></span> <span data-ttu-id="39867-117">To znamená, že název proměnné by neměl být předán direktivě preprocesoru a symbol lze vyhodnotit pouze pomocí direktivy preprocesoru.</span><span class="sxs-lookup"><span data-stu-id="39867-117">That is, a variable name should not be passed to a preprocessor directive and a symbol can only be evaluated by a preprocessor directive.</span></span>  
  
 <span data-ttu-id="39867-118">Rozsah symbolu, který byl vytvořen pomocí `#define` , je soubor, ve kterém byl symbol definován.</span><span class="sxs-lookup"><span data-stu-id="39867-118">The scope of a symbol that was created by using `#define` is the file in which the symbol was defined.</span></span>  
  
 <span data-ttu-id="39867-119">Jak ukazuje následující příklad, je nutné umístit `#define` direktivy v horní části souboru.</span><span class="sxs-lookup"><span data-stu-id="39867-119">As the following example shows, you must put `#define` directives at the top of the file.</span></span>  
  
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
  
 <span data-ttu-id="39867-120">Příklad, jak zrušit definování symbolu, naleznete v tématu [#undef](./preprocessor-undef.md).</span><span class="sxs-lookup"><span data-stu-id="39867-120">For an example of how to undefine a symbol, see [#undef](./preprocessor-undef.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="39867-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="39867-121">See also</span></span>

- [<span data-ttu-id="39867-122">C#Odkaz</span><span class="sxs-lookup"><span data-stu-id="39867-122">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="39867-123">Průvodce programováním v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="39867-123">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="39867-124">C# Direktivy preprocesoru</span><span class="sxs-lookup"><span data-stu-id="39867-124">C# Preprocessor Directives</span></span>](./index.md)
- [<span data-ttu-id="39867-125">const</span><span class="sxs-lookup"><span data-stu-id="39867-125">const</span></span>](../keywords/const.md)
- [<span data-ttu-id="39867-126">Postupy: Podmíněně kompilovat pomocí trasování a ladění</span><span class="sxs-lookup"><span data-stu-id="39867-126">How to: Compile Conditionally with Trace and Debug</span></span>](../../../framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md)
- [<span data-ttu-id="39867-127">#undef</span><span class="sxs-lookup"><span data-stu-id="39867-127">#undef</span></span>](./preprocessor-undef.md)
- [<span data-ttu-id="39867-128">#if</span><span class="sxs-lookup"><span data-stu-id="39867-128">#if</span></span>](./preprocessor-if.md)
