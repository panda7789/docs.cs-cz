---
title: jitCompilationStart – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- JIT compilation
- MDAs (managed debugging assistants), JIT compilation
- JitCompilationStart MDA
- managed debugging assistants (MDAs), JIT compilation
ms.assetid: 5ffd2857-d0ba-4342-9824-9ffe04ec135d
ms.openlocfilehash: 9cae942bc01e9263720dbfe9acfb21bbb70bc548
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216262"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="0985d-102">jitCompilationStart – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="0985d-102">jitCompilationStart MDA</span></span>
<span data-ttu-id="0985d-103">V případě, že kompilátor JIT (just-in-time) začne kompilovat funkci, je aktivována funkce Pomocník pro spravované ladění (MDA) `jitCompilationStart`.</span><span class="sxs-lookup"><span data-stu-id="0985d-103">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0985d-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="0985d-104">Symptoms</span></span>  
 <span data-ttu-id="0985d-105">Velikost pracovní sady roste pro program, který je již v nativním formátu bitové kopie, protože do procesu je načtena knihovna Mscorjit. dll.</span><span class="sxs-lookup"><span data-stu-id="0985d-105">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0985d-106">Příčina</span><span class="sxs-lookup"><span data-stu-id="0985d-106">Cause</span></span>  
 <span data-ttu-id="0985d-107">Ne všechna sestavení, na kterých je program závislý, byla vygenerována v nativním formátu nebo ty, které nejsou správně registrovány.</span><span class="sxs-lookup"><span data-stu-id="0985d-107">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0985d-108">Řešení</span><span class="sxs-lookup"><span data-stu-id="0985d-108">Resolution</span></span>  
 <span data-ttu-id="0985d-109">Povolením tohoto MDA můžete určit, která funkce je kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="0985d-109">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="0985d-110">Určete, zda sestavení, které obsahuje funkci, je vygenerováno do nativního formátu a správně zaregistrováno.</span><span class="sxs-lookup"><span data-stu-id="0985d-110">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0985d-111">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="0985d-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="0985d-112">Tento MDA zaznamená zprávu těsně před tím, než je metoda kompilována JIT, takže povolení tohoto MDA má významný dopad na výkon.</span><span class="sxs-lookup"><span data-stu-id="0985d-112">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="0985d-113">Všimněte si, že pokud je metoda vložená, negeneruje tato MDA samostatnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="0985d-113">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0985d-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="0985d-114">Output</span></span>  
 <span data-ttu-id="0985d-115">Následující ukázka kódu ukazuje vzorový výstup.</span><span class="sxs-lookup"><span data-stu-id="0985d-115">The following code sample shows sample output.</span></span> <span data-ttu-id="0985d-116">V tomto případě výstup ukazuje, že v sestavení test metoda "m" ve třídě "ns2.CO" byla kompilována JIT.</span><span class="sxs-lookup"><span data-stu-id="0985d-116">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```output
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="0985d-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="0985d-117">Configuration</span></span>  
 <span data-ttu-id="0985d-118">Následující konfigurační soubor znázorňuje různé filtry, které mohou být použity k vyfiltrování, které metody jsou hlášeny při prvním kompilování JIT.</span><span class="sxs-lookup"><span data-stu-id="0985d-118">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="0985d-119">Můžete určit, že budou všechny metody hlášeny nastavením hodnoty atributu name na \*.</span><span class="sxs-lookup"><span data-stu-id="0985d-119">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="0985d-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="0985d-120">Example</span></span>  
 <span data-ttu-id="0985d-121">Následující ukázka kódu je určena pro použití s předchozím konfiguračním souborem.</span><span class="sxs-lookup"><span data-stu-id="0985d-121">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0985d-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="0985d-122">See also</span></span>

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [<span data-ttu-id="0985d-123">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="0985d-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
- [<span data-ttu-id="0985d-124">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="0985d-124">Interop Marshaling</span></span>](../interop/interop-marshaling.md)
