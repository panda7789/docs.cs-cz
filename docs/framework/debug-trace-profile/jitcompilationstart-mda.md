---
title: jitCompilationStart – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9643a2d2ea0967b8cf6d8e18ce2e9073ae583f71
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33387033"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="96698-102">jitCompilationStart – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="96698-102">jitCompilationStart MDA</span></span>
<span data-ttu-id="96698-103">`jitCompilationStart` Pomocník spravovaného ladění (MDA) se při spuštění v běhu (JIT) kompilátor zkompilovat funkci aktivuje do sestavy.</span><span class="sxs-lookup"><span data-stu-id="96698-103">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="96698-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="96698-104">Symptoms</span></span>  
 <span data-ttu-id="96698-105">Pracovní sada větší velikostí pro program, který je již ve formátu nativních bitových kopií, protože mscorjit.dll je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="96698-105">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="96698-106">příčina</span><span class="sxs-lookup"><span data-stu-id="96698-106">Cause</span></span>  
 <span data-ttu-id="96698-107">Ne všechny sestavení, které program závisí na byly vygenerovány do nativní formát nebo ty, které mají nejsou správně zaregistrovány.</span><span class="sxs-lookup"><span data-stu-id="96698-107">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="96698-108">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="96698-108">Resolution</span></span>  
 <span data-ttu-id="96698-109">Povolení této MDA umožňuje určit, které funkce, která má být kompilována.</span><span class="sxs-lookup"><span data-stu-id="96698-109">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="96698-110">Určete, jestli je sestavení obsahující funkce je generována do nativní formát a řádně zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="96698-110">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="96698-111">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="96698-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="96698-112">Tato MDA zaznamená zprávu těsně před metodu je kompilována, takže povolení této MDA má významný dopad na výkon.</span><span class="sxs-lookup"><span data-stu-id="96698-112">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="96698-113">Všimněte si, že pokud vložené je metoda, nevygeneruje tento MDA samostatnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="96698-113">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="96698-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="96698-114">Output</span></span>  
 <span data-ttu-id="96698-115">Následující příklad kódu ukazuje ukázkový výstup.</span><span class="sxs-lookup"><span data-stu-id="96698-115">The following code sample shows sample output.</span></span> <span data-ttu-id="96698-116">Výstup ukazuje, které se v sestavení Test metody "m" na třídu "ns2.CO" v tomto případě se kompilována.</span><span class="sxs-lookup"><span data-stu-id="96698-116">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="96698-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="96698-117">Configuration</span></span>  
 <span data-ttu-id="96698-118">Následujícího konfiguračního souboru ukazuje různé filtry, které mohou být použity pro odfiltrování které metody jsou hlášené, když jsou nejprve kompilována.</span><span class="sxs-lookup"><span data-stu-id="96698-118">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="96698-119">Můžete určit, že všechny metody hlášené nastavením hodnoty atributu název tak, aby \*.</span><span class="sxs-lookup"><span data-stu-id="96698-119">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <jitCompilationStart>  
      <methods>  
        <match name="C0::m" />  
        <match name="MyMethod" />  
        <match name="C2::*" />  
        <match name="ns0::*" />  
        <match name="ns1.C0::*" />  
        <match name="ns2.C0::m" />  
        <match name="ns2.C0+N0::m" />  
      </methods>  
    </jitCompilationStart >  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="96698-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="96698-120">Example</span></span>  
 <span data-ttu-id="96698-121">Následující ukázka kódu je určena pro použití s předchozím konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="96698-121">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
```  
using System;  
using System.Reflection;  
using System.Runtime.CompilerServices;  
using System.Runtime.InteropServices;  
  
public class Entry  
{  
    public static void Main(string[] args)  
    {  
        C0.m();  
        C1.MyMethod();  
        C2.m();  
  
        ns0.C0.m();  
        ns0.C0.N0.m();  
        ns0.C1.m();  
  
        ns1.C0.m();  
        ns1.C0.N0.m();  
  
        ns2.C0.m();  
        ns2.C0.N0.m();  
    }  
}  
  
public class C0  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
public class C1  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void MyMethod() { }  
}  
  
public class C2  
{  
    [MethodImpl(MethodImplOptions.NoInlining)]  
    public static void m() { }  
}  
  
namespace ns0  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
  
    public class C1  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
    }  
}  
  
namespace ns1  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
  
namespace ns2  
{  
    public class C0  
    {  
        [MethodImpl(MethodImplOptions.NoInlining)]  
        public static void m() { }  
  
        public class N0  
        {  
            [MethodImpl(MethodImplOptions.NoInlining)]  
            public static void m() { }  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="96698-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="96698-122">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="96698-123">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="96698-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="96698-124">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="96698-124">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
