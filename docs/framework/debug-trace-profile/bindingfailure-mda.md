---
title: bindingFailure – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1a75efaf6703858fdb48a3f09635da1be4463d34
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364695"
---
# <a name="bindingfailure-mda"></a><span data-ttu-id="6e8f5-102">bindingFailure – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="6e8f5-102">bindingFailure MDA</span></span>
<span data-ttu-id="6e8f5-103">`bindingFailure` Pomocník spravovaného ladění (MDA) se aktivuje, když se nepodaří načíst sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-103">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="6e8f5-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="6e8f5-104">Symptoms</span></span>  
 <span data-ttu-id="6e8f5-105">Kód se pokusil o načtení sestavení pomocí statické odkaz nebo jednu z metod zavaděč, jako třeba <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-105">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="6e8f5-106">Sestavení není načíst a <xref:System.IO.FileNotFoundException> nebo <xref:System.IO.FileLoadException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-106">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="6e8f5-107">příčina</span><span class="sxs-lookup"><span data-stu-id="6e8f5-107">Cause</span></span>  
 <span data-ttu-id="6e8f5-108">Selhání vazby nastane, když se nepodařilo načíst sestavení modulu runtime.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-108">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="6e8f5-109">Selhání vazby může být výsledkem jednoho z následujících situací:</span><span class="sxs-lookup"><span data-stu-id="6e8f5-109">A binding failure might be the result of one of the following situations:</span></span>  
  
-   <span data-ttu-id="6e8f5-110">Modul CLR (CLR) nelze najít požadovaný sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-110">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="6e8f5-111">Existuje mnoho důvodů této situaci může dojít, jako je například sestavení, není nainstalována nebo není správně nakonfigurován k vyhledání sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-111">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>  
  
-   <span data-ttu-id="6e8f5-112">Běžný scénář problému dojde k předání typu do jiné domény aplikace, které vyžaduje CLR se načíst sestavení obsahující daný typ v jiné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-112">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="6e8f5-113">Nemusí být možné pro modul runtime k načtení sestavení, pokud jiné doméně aplikace je nakonfigurována jinak než původní domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-113">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="6e8f5-114">Například může mít dva aplikační domény různých <xref:System.AppDomain.BaseDirectory%2A> hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-114">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>  
  
-   <span data-ttu-id="6e8f5-115">Požadovaný sestavení je poškozený nebo není sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-115">The requested assembly is corrupted or is not an assembly.</span></span>  
  
-   <span data-ttu-id="6e8f5-116">Kód pokusu o načtení sestavení nemá správný kód přístupová oprávnění zabezpečení k načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-116">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>  
  
-   <span data-ttu-id="6e8f5-117">Přihlašovací údaje uživatele nemají potřebná oprávnění pro čtení tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-117">The user credentials do not provide the required permissions to read the file.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="6e8f5-118">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="6e8f5-118">Resolution</span></span>  
 <span data-ttu-id="6e8f5-119">Prvním krokem je určit, proč modulu CLR nelze vytvořit vazbu na požadovaný sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-119">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="6e8f5-120">Existuje mnoho důvodů, proč nemusí mít modulu runtime nalezeno nebo bylo možné zatížení požadovaný sestavení, např. scénáře uvedené v části Příčina.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-120">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="6e8f5-121">K vyloučení příčinou selhání vazby doporučujeme následující akce:</span><span class="sxs-lookup"><span data-stu-id="6e8f5-121">The following actions are recommended to eliminate the cause of the binding failure:</span></span>  
  
-   <span data-ttu-id="6e8f5-122">Zjistit příčinu na základě dat poskytované `bindingFailure` (mda):</span><span class="sxs-lookup"><span data-stu-id="6e8f5-122">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>  
  
    -   <span data-ttu-id="6e8f5-123">Spustit [Fuslogvw.exe (sestavení vazby Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) ke čtení v souborech protokolů chyb vyprodukované vazač sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-123">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>  
  
    -   <span data-ttu-id="6e8f5-124">Určí, zda je sestavení v umístění požadovaný.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-124">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="6e8f5-125">U <xref:System.Reflection.Assembly.LoadFrom%2A> a <xref:System.Reflection.Assembly.LoadFile%2A> metody, požadované umístění se dá snadno určit.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-125">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="6e8f5-126">U <xref:System.Reflection.Assembly.Load%2A> metodu, která sváže pomocí identity sestavení, které hledáte sestavení, které odpovídají této identity v doméně aplikace <xref:System.AppDomain.BaseDirectory%2A> cesta testu vlastnosti a globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-126">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>  
  
-   <span data-ttu-id="6e8f5-127">Vyřešte příčinu založena na předchozí určení.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-127">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="6e8f5-128">Možným řešením možnosti jsou následující:</span><span class="sxs-lookup"><span data-stu-id="6e8f5-128">Possible resolution options are the following:</span></span>  
  
    -   <span data-ttu-id="6e8f5-129">Nainstalujte požadovaný sestavení v globální mezipaměti sestavení a volání.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-129">Install the requested assembly in the global assembly cache and call the.</span></span> <span data-ttu-id="6e8f5-130"><xref:System.Reflection.Assembly.Load%2A> Metoda pro načtení sestavení identita.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-130"><xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>  
  
    -   <span data-ttu-id="6e8f5-131">Zkopírujte požadované sestavení do adresáře aplikace a volání <xref:System.Reflection.Assembly.Load%2A> metoda pro načtení sestavení identita.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-131">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>  
  
    -   <span data-ttu-id="6e8f5-132">Znovu nakonfigurujte doménu aplikace, v němž došlo k selhání vazby zahrnout cesta k sestavení můžete buď změnit <xref:System.AppDomain.BaseDirectory%2A> vlastnost nebo přidání privátní testování cesty.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-132">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>  
  
    -   <span data-ttu-id="6e8f5-133">Změna seznamu řízení přístupu pro soubor umožňující přihlášeného uživatele pro čtení tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-133">Change the access control list for the file to allow the logged-on user to read the file.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="6e8f5-134">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="6e8f5-134">Effect on the Runtime</span></span>  
 <span data-ttu-id="6e8f5-135">Tato MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-135">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="6e8f5-136">Pouze sestavy data o selhání vazby.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-136">It only reports data about binding failures.</span></span>  
  
## <a name="output"></a><span data-ttu-id="6e8f5-137">Výstup</span><span class="sxs-lookup"><span data-stu-id="6e8f5-137">Output</span></span>  
 <span data-ttu-id="6e8f5-138">MDA sestav sestavení, které se nepodařilo načíst, včetně požadovanou cestu nebo zobrazit název, kontext vazby, doménu aplikace, ve kterém byl požadován zatížení a příčinu selhání.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-138">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>  
  
 <span data-ttu-id="6e8f5-139">Zobrazovaný název nebo požadovaná cesta může být prázdná, pokud tato data nebyla k dispozici pro modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-139">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="6e8f5-140">Pokud bylo volání, který selhal <xref:System.Reflection.Assembly.Load%2A> metoda, je pravděpodobné, modul runtime nelze určit, zobrazovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="6e8f5-140">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="6e8f5-141">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="6e8f5-141">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="6e8f5-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="6e8f5-142">Example</span></span>  
 <span data-ttu-id="6e8f5-143">Následující příklad kódu ukazuje situace, které můžou aktivovat tuto (mda):</span><span class="sxs-lookup"><span data-stu-id="6e8f5-143">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```  
using System;  
using System.Collections.Generic;  
using System.Text;  
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // This call attempts to load a nonexistent assembly.  
            // The call will throw a System.IO.FileNotFound exception  
            // and cause the activation of the bindingFailure MDA   
            // if it is registered.  
            Assembly.Load("NonExistentAssembly");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="6e8f5-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="6e8f5-144">See Also</span></span>  
 [<span data-ttu-id="6e8f5-145">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="6e8f5-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
