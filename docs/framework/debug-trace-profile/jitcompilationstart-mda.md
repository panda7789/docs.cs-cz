---
title: Pomocník spravovaného ladění jitCompilationStart – (MDA)
description: Sestavy pomocníka spravovaného ladění (MDA) jitCompilationStart –, když kompilátor JIT (just-in-time) začne kompilovat funkci .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: 13e20c1a940b7bfa777245ba35f3cc1b003d15b2
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325535"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="f28a8-103">jitCompilationStart – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="f28a8-103">jitCompilationStart MDA</span></span>

<span data-ttu-id="f28a8-104">`jitCompilationStart`Je aktivován pomocník spravovaného ladění (MDA), který bude hlásit, že kompilátor JIT (just-in-time) začne kompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="f28a8-104">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f28a8-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="f28a8-105">Symptoms</span></span>  
 <span data-ttu-id="f28a8-106">Velikost pracovní sady roste pro program, který je již v nativním formátu bitové kopie, protože mscorjit.dll je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="f28a8-106">The working set size increases for a program that's already in native image format, because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f28a8-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="f28a8-107">Cause</span></span>  
<span data-ttu-id="f28a8-108">Ne všechna sestavení, na kterých je program závislý, byla vygenerována v nativním formátu nebo sestavení není správně registrováno.</span><span class="sxs-lookup"><span data-stu-id="f28a8-108">Not all the assemblies the program depends on have been generated into native format, or an assembly is not registered correctly.</span></span>  

## <a name="resolution"></a><span data-ttu-id="f28a8-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="f28a8-109">Resolution</span></span>  
 <span data-ttu-id="f28a8-110">Povolení tohoto MDA vám umožní určit, která funkce je kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="f28a8-110">Enabling this MDA allows you to identify which function is being JIT-compiled.</span></span> <span data-ttu-id="f28a8-111">Ujistěte se, že sestavení, které obsahuje funkci, je vygenerováno do nativního formátu a správně zaregistrováno.</span><span class="sxs-lookup"><span data-stu-id="f28a8-111">Make sure that the assembly that contains the function is generated to native format and properly registered.</span></span>
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f28a8-112">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="f28a8-112">Effect on the runtime</span></span>  
 <span data-ttu-id="f28a8-113">Tento MDA zaznamená zprávu těsně před tím, než je metoda kompilována JIT, takže povolení tohoto MDA má významný dopad na výkon.</span><span class="sxs-lookup"><span data-stu-id="f28a8-113">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="f28a8-114">Pokud je metoda vložená, negeneruje tato MDA samostatnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="f28a8-114">If a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f28a8-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="f28a8-115">Output</span></span>  
 <span data-ttu-id="f28a8-116">Následující ukázka kódu ukazuje vzorový výstup.</span><span class="sxs-lookup"><span data-stu-id="f28a8-116">The following code sample shows sample output.</span></span> <span data-ttu-id="f28a8-117">V tomto případě výstup ukazuje, že v testu sestavení byla metoda "m" ve třídě "ns2.CO" zkompilována kompilátorem JIT.</span><span class="sxs-lookup"><span data-stu-id="f28a8-117">In this case, the output shows that, in assembly Test, the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="f28a8-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f28a8-118">Configuration</span></span>  
 <span data-ttu-id="f28a8-119">Následující konfigurační soubor znázorňuje různé filtry, které mohou být použity k vyfiltrování, které metody jsou hlášeny při prvním kompilování JIT.</span><span class="sxs-lookup"><span data-stu-id="f28a8-119">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="f28a8-120">Můžete určit, že budou všechny metody hlášeny nastavením hodnoty atributu name na \* .</span><span class="sxs-lookup"><span data-stu-id="f28a8-120">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="f28a8-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="f28a8-121">Example</span></span>  
 <span data-ttu-id="f28a8-122">Následující ukázka kódu je určena pro použití s předchozím konfiguračním souborem.</span><span class="sxs-lookup"><span data-stu-id="f28a8-122">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="f28a8-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f28a8-123">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f28a8-124">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="f28a8-124">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f28a8-125">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="f28a8-125">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
