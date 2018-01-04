---
title: "jitCompilationStart – pomocník spravovaného ladění (MDA)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0fd520392ca7f6bb97ac11d868db7a0df9a32d5f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="60e9a-102">jitCompilationStart – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="60e9a-102">jitCompilationStart MDA</span></span>
<span data-ttu-id="60e9a-103">`jitCompilationStart` Pomocník spravovaného ladění (MDA) se při spuštění v běhu (JIT) kompilátor zkompilovat funkci aktivuje do sestavy.</span><span class="sxs-lookup"><span data-stu-id="60e9a-103">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="60e9a-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="60e9a-104">Symptoms</span></span>  
 <span data-ttu-id="60e9a-105">Pracovní sada větší velikostí pro program, který je již ve formátu nativních bitových kopií, protože mscorjit.dll je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="60e9a-105">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="60e9a-106">příčina</span><span class="sxs-lookup"><span data-stu-id="60e9a-106">Cause</span></span>  
 <span data-ttu-id="60e9a-107">Ne všechny sestavení, které program závisí na byly vygenerovány do nativní formát nebo ty, které mají nejsou správně zaregistrovány.</span><span class="sxs-lookup"><span data-stu-id="60e9a-107">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="60e9a-108">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="60e9a-108">Resolution</span></span>  
 <span data-ttu-id="60e9a-109">Povolení této MDA umožňuje určit, které funkce, která má být kompilována.</span><span class="sxs-lookup"><span data-stu-id="60e9a-109">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="60e9a-110">Určete, jestli je sestavení obsahující funkce je generována do nativní formát a řádně zaregistrován.</span><span class="sxs-lookup"><span data-stu-id="60e9a-110">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="60e9a-111">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="60e9a-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="60e9a-112">Tato MDA zaznamená zprávu těsně před metodu je kompilována, takže povolení této MDA má významný dopad na výkon.</span><span class="sxs-lookup"><span data-stu-id="60e9a-112">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="60e9a-113">Všimněte si, že pokud vložené je metoda, nevygeneruje tento MDA samostatnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="60e9a-113">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="60e9a-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="60e9a-114">Output</span></span>  
 <span data-ttu-id="60e9a-115">Následující příklad kódu ukazuje ukázkový výstup.</span><span class="sxs-lookup"><span data-stu-id="60e9a-115">The following code sample shows sample output.</span></span> <span data-ttu-id="60e9a-116">Výstup ukazuje, které se v sestavení Test metody "m" na třídu "ns2.CO" v tomto případě se kompilována.</span><span class="sxs-lookup"><span data-stu-id="60e9a-116">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="60e9a-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="60e9a-117">Configuration</span></span>  
 <span data-ttu-id="60e9a-118">Následujícího konfiguračního souboru ukazuje různé filtry, které mohou být použity pro odfiltrování které metody jsou hlášené, když jsou nejprve kompilována.</span><span class="sxs-lookup"><span data-stu-id="60e9a-118">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="60e9a-119">Můžete určit, že všechny metody hlášené nastavením hodnoty atributu název tak, aby *.</span><span class="sxs-lookup"><span data-stu-id="60e9a-119">You can specify that all methods be reported by setting the value of the name attribute to *.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="60e9a-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="60e9a-120">Example</span></span>  
 <span data-ttu-id="60e9a-121">Následující ukázka kódu je určena pro použití s předchozím konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="60e9a-121">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="60e9a-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="60e9a-122">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="60e9a-123">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="60e9a-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="60e9a-124">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="60e9a-124">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
