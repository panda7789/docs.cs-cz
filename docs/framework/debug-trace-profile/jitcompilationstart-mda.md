---
title: jitCompilationStart – pomocník spravovaného ladění (MDA)
description: Použijte pomocníka spravovaného ladění jitCompilationStart – (MDA), který je spuštěn k hlášení, když kompilátor JIT (just-in-time) začne kompilovat funkci .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: bf2d09f433f0b8e4056fecd1f4e82bf3b91dd2bc
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904127"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="f6da2-103">jitCompilationStart – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="f6da2-103">jitCompilationStart MDA</span></span>
<span data-ttu-id="f6da2-104">`jitCompilationStart`Je aktivován pomocník spravovaného ladění (MDA), který bude hlásit, že kompilátor JIT (just-in-time) začne kompilovat funkci.</span><span class="sxs-lookup"><span data-stu-id="f6da2-104">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="f6da2-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="f6da2-105">Symptoms</span></span>  
 <span data-ttu-id="f6da2-106">Velikost pracovní sady se zvyšuje pro program, který je již v nativním formátu obrázku, protože mscorjit.dll je načten do procesu.</span><span class="sxs-lookup"><span data-stu-id="f6da2-106">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="f6da2-107">Příčina</span><span class="sxs-lookup"><span data-stu-id="f6da2-107">Cause</span></span>  
 <span data-ttu-id="f6da2-108">Ne všechna sestavení, na kterých je program závislý, byla vygenerována v nativním formátu nebo ty, které nejsou správně registrovány.</span><span class="sxs-lookup"><span data-stu-id="f6da2-108">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="f6da2-109">Řešení</span><span class="sxs-lookup"><span data-stu-id="f6da2-109">Resolution</span></span>  
 <span data-ttu-id="f6da2-110">Povolením tohoto MDA můžete určit, která funkce je kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="f6da2-110">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="f6da2-111">Určete, zda sestavení, které obsahuje funkci, je vygenerováno do nativního formátu a správně zaregistrováno.</span><span class="sxs-lookup"><span data-stu-id="f6da2-111">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="f6da2-112">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="f6da2-112">Effect on the Runtime</span></span>  
 <span data-ttu-id="f6da2-113">Tento MDA zaznamená zprávu těsně před tím, než je metoda kompilována JIT, takže povolení tohoto MDA má významný dopad na výkon.</span><span class="sxs-lookup"><span data-stu-id="f6da2-113">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="f6da2-114">Všimněte si, že pokud je metoda vložená, negeneruje tato MDA samostatnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="f6da2-114">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="f6da2-115">Výstup</span><span class="sxs-lookup"><span data-stu-id="f6da2-115">Output</span></span>  
 <span data-ttu-id="f6da2-116">Následující ukázka kódu ukazuje vzorový výstup.</span><span class="sxs-lookup"><span data-stu-id="f6da2-116">The following code sample shows sample output.</span></span> <span data-ttu-id="f6da2-117">V tomto případě výstup ukazuje, že v sestavení test metoda "m" ve třídě "ns2.CO" byla kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="f6da2-117">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="f6da2-118">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="f6da2-118">Configuration</span></span>  
 <span data-ttu-id="f6da2-119">Následující konfigurační soubor znázorňuje různé filtry, které mohou být použity k vyfiltrování, které metody jsou hlášeny při prvním kompilování JIT.</span><span class="sxs-lookup"><span data-stu-id="f6da2-119">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="f6da2-120">Můžete určit, že budou všechny metody hlášeny nastavením hodnoty atributu name na \* .</span><span class="sxs-lookup"><span data-stu-id="f6da2-120">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="f6da2-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="f6da2-121">Example</span></span>  
 <span data-ttu-id="f6da2-122">Následující ukázka kódu je určena pro použití s předchozím konfiguračním souborem.</span><span class="sxs-lookup"><span data-stu-id="f6da2-122">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f6da2-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="f6da2-123">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="f6da2-124">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="f6da2-124">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="f6da2-125">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="f6da2-125">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
