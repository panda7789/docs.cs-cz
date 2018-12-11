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
ms.openlocfilehash: d73c299231a588a5ae0b252dd2b5a0a834685f2d
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53150664"
---
# <a name="jitcompilationstart-mda"></a><span data-ttu-id="1fd83-102">jitCompilationStart – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="1fd83-102">jitCompilationStart MDA</span></span>
<span data-ttu-id="1fd83-103">`jitCompilationStart` Pomocníka spravovaného ladění (MDA) je aktivován do sestavy, když začne kompilátor just-in-time (JIT) kompilaci funkce.</span><span class="sxs-lookup"><span data-stu-id="1fd83-103">The `jitCompilationStart` managed debugging assistant (MDA) is activated to report when the just-in-time (JIT) compiler starts to compile a function.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="1fd83-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="1fd83-104">Symptoms</span></span>  
 <span data-ttu-id="1fd83-105">Pracovní sada pro program, který je již ve formátu nativní bitové kopie, protože mscorjit.dll je načten do procesu se zvětší.</span><span class="sxs-lookup"><span data-stu-id="1fd83-105">The working set size increases for a program that is already in native image format because mscorjit.dll is loaded into the process.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="1fd83-106">příčina</span><span class="sxs-lookup"><span data-stu-id="1fd83-106">Cause</span></span>  
 <span data-ttu-id="1fd83-107">Ne všechna sestavení, které program závisí na byly vytvořeny v nativním formátu, nebo ty, které mají nejsou správně registrovány.</span><span class="sxs-lookup"><span data-stu-id="1fd83-107">Not all the assemblies the program depends on have been generated into native format, or those that have are not registered correctly.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="1fd83-108">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="1fd83-108">Resolution</span></span>  
 <span data-ttu-id="1fd83-109">Povolení toto MDA umožňuje určit, které funkce, která má být zkompilovaný pomocí kompilátoru JIT.</span><span class="sxs-lookup"><span data-stu-id="1fd83-109">Enabling this MDA allows you to determine which function is being JIT-compiled.</span></span> <span data-ttu-id="1fd83-110">Určete, zda je sestavení, které obsahuje funkce generované nativním formátu a správně registrována.</span><span class="sxs-lookup"><span data-stu-id="1fd83-110">Determine whether the assembly that contains the function is generated to native format and properly registered.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="1fd83-111">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="1fd83-111">Effect on the Runtime</span></span>  
 <span data-ttu-id="1fd83-112">Toto MDA zaznamená zprávu těsně před plánovaným metodu zkompilovaný pomocí kompilátoru JIT, takže umožňuje toto MDA má významný dopad na výkon.</span><span class="sxs-lookup"><span data-stu-id="1fd83-112">This MDA logs a message just before a method is JIT-compiled, so enabling this MDA has significant impact on performance.</span></span> <span data-ttu-id="1fd83-113">Všimněte si, že pokud je metoda vložené, nevygeneruje toto MDA samostatnou zprávu.</span><span class="sxs-lookup"><span data-stu-id="1fd83-113">Note that if a method is inline, this MDA will not generate a separate message.</span></span>  
  
## <a name="output"></a><span data-ttu-id="1fd83-114">Výstup</span><span class="sxs-lookup"><span data-stu-id="1fd83-114">Output</span></span>  
 <span data-ttu-id="1fd83-115">Následující příklad kódu ukazuje příklad výstupu.</span><span class="sxs-lookup"><span data-stu-id="1fd83-115">The following code sample shows sample output.</span></span> <span data-ttu-id="1fd83-116">V tomto případě ukazuje výstup, které v sestavení testovací metoda "m" ve třídě "ns2.CO" byl zkompilován JIT Kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="1fd83-116">In this case the output shows that in assembly Test the method "m" on class "ns2.CO" was JIT-compiled.</span></span>  
  
```  
method name="Test!ns2.C0::m"  
```  
  
## <a name="configuration"></a><span data-ttu-id="1fd83-117">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="1fd83-117">Configuration</span></span>  
 <span data-ttu-id="1fd83-118">Následující konfigurační soubor ukazuje různé filtry, které mohou být použity pro filtrování, které metody jsou hlášeny, když jsou nejprve zkompilován JIT Kompilátorem.</span><span class="sxs-lookup"><span data-stu-id="1fd83-118">The following configuration file shows a variety of filters that can be employed to filter out which methods are reported when they are first JIT-compiled.</span></span> <span data-ttu-id="1fd83-119">Můžete určit, že všechny metody oznámený tak, že nastavíte hodnotu atributu název \*.</span><span class="sxs-lookup"><span data-stu-id="1fd83-119">You can specify that all methods be reported by setting the value of the name attribute to \*.</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="1fd83-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="1fd83-120">Example</span></span>  
 <span data-ttu-id="1fd83-121">Následující ukázka kódu je určena pro použití s předchozím konfigurační soubor.</span><span class="sxs-lookup"><span data-stu-id="1fd83-121">The following code sample is intended to be used with the preceding configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="1fd83-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="1fd83-122">See Also</span></span>  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [<span data-ttu-id="1fd83-123">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="1fd83-123">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [<span data-ttu-id="1fd83-124">Zařazování spolupráce</span><span class="sxs-lookup"><span data-stu-id="1fd83-124">Interop Marshaling</span></span>](../../../docs/framework/interop/interop-marshaling.md)
