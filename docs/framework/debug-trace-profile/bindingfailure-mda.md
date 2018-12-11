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
ms.openlocfilehash: d6cf0c944fc904a50a5b652f666f50c457a60204
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130830"
---
# <a name="bindingfailure-mda"></a><span data-ttu-id="86e8a-102">bindingFailure – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="86e8a-102">bindingFailure MDA</span></span>
<span data-ttu-id="86e8a-103">`bindingFailure` Pomocníka spravovaného ladění (MDA) se aktivuje, když sestavení se nepodaří načíst.</span><span class="sxs-lookup"><span data-stu-id="86e8a-103">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="86e8a-104">Příznaky</span><span class="sxs-lookup"><span data-stu-id="86e8a-104">Symptoms</span></span>  
 <span data-ttu-id="86e8a-105">Kód se pokusil o načtení sestavení pomocí statický odkaz nebo jednu z metod zavaděč, jako například <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="86e8a-105">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="86e8a-106">Sestavení není načteno a <xref:System.IO.FileNotFoundException> nebo <xref:System.IO.FileLoadException> je vyvolána výjimka.</span><span class="sxs-lookup"><span data-stu-id="86e8a-106">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="86e8a-107">příčina</span><span class="sxs-lookup"><span data-stu-id="86e8a-107">Cause</span></span>  
 <span data-ttu-id="86e8a-108">Když nelze načíst sestavení modulu runtime dojde k selhání vazby.</span><span class="sxs-lookup"><span data-stu-id="86e8a-108">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="86e8a-109">Selhání vazby může být výsledkem jednoho z následujících situací:</span><span class="sxs-lookup"><span data-stu-id="86e8a-109">A binding failure might be the result of one of the following situations:</span></span>  
  
-   <span data-ttu-id="86e8a-110">Modul CLR (CLR) nejde najít požadované sestavení.</span><span class="sxs-lookup"><span data-stu-id="86e8a-110">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="86e8a-111">Existuje mnoho důvodů, že tato situace může nastat, jako je například sestavení není nainstalován nebo není správně nakonfigurován k vyhledání sestavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="86e8a-111">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>  
  
-   <span data-ttu-id="86e8a-112">Běžný scénář, kdy problém předává typ k jiné doméně aplikace, která vyžaduje CLR pro načtení sestavení obsahující daný typ v jiné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="86e8a-112">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="86e8a-113">Nemusí být možné pro modul runtime k načtení sestavení, pokud jiné doméně aplikace je nakonfigurována jinak než původní domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="86e8a-113">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="86e8a-114">Například může mít dvě domény aplikace různé <xref:System.AppDomain.BaseDirectory%2A> hodnot vlastností.</span><span class="sxs-lookup"><span data-stu-id="86e8a-114">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>  
  
-   <span data-ttu-id="86e8a-115">Požadované sestavení je poškozený nebo se nejedná o sestavení.</span><span class="sxs-lookup"><span data-stu-id="86e8a-115">The requested assembly is corrupted or is not an assembly.</span></span>  
  
-   <span data-ttu-id="86e8a-116">Kód pokusu o načtení sestavení nemá oprávnění zabezpečení přístupu ke správný kód pro načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="86e8a-116">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>  
  
-   <span data-ttu-id="86e8a-117">Přihlašovací údaje uživatele nemají potřebná oprávnění ke čtení souboru.</span><span class="sxs-lookup"><span data-stu-id="86e8a-117">The user credentials do not provide the required permissions to read the file.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="86e8a-118">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="86e8a-118">Resolution</span></span>  
 <span data-ttu-id="86e8a-119">Prvním krokem je určit, proč nebylo možné vytvořit vazbu CLR na požadovaná sestavení.</span><span class="sxs-lookup"><span data-stu-id="86e8a-119">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="86e8a-120">Existuje mnoho důvodů, proč nemusí mít modul runtime nalezen nebo je možné načíst požadovaná sestavení, jako je například scénáře uvedené v části Příčina.</span><span class="sxs-lookup"><span data-stu-id="86e8a-120">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="86e8a-121">Tyto akce se doporučuje, aby eliminovat příčinou selhání vazby:</span><span class="sxs-lookup"><span data-stu-id="86e8a-121">The following actions are recommended to eliminate the cause of the binding failure:</span></span>  
  
-   <span data-ttu-id="86e8a-122">Zjistit příčinu pomocí dat poskytované `bindingFailure` MDA:</span><span class="sxs-lookup"><span data-stu-id="86e8a-122">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>  
  
    -   <span data-ttu-id="86e8a-123">Spustit [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) číst protokoly chyb vytváří vázacím objektem sestavení.</span><span class="sxs-lookup"><span data-stu-id="86e8a-123">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../../../docs/framework/tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>  
  
    -   <span data-ttu-id="86e8a-124">Určení, zda je sestavení v požadované umístění.</span><span class="sxs-lookup"><span data-stu-id="86e8a-124">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="86e8a-125">V případě třídy <xref:System.Reflection.Assembly.LoadFrom%2A> a <xref:System.Reflection.Assembly.LoadFile%2A> metody, požadované umístění se dá snadno určit.</span><span class="sxs-lookup"><span data-stu-id="86e8a-125">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="86e8a-126">V případě třídy <xref:System.Reflection.Assembly.Load%2A> metodu, která vytvoří vazbu pomocí identity sestavení, musí vyhledat sestavení, která tuto identitu do domény aplikace odpovídají <xref:System.AppDomain.BaseDirectory%2A> cesta testu paměti pro vlastnost a globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="86e8a-126">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>  
  
-   <span data-ttu-id="86e8a-127">Vyřešte příčinu podle předchozího určení.</span><span class="sxs-lookup"><span data-stu-id="86e8a-127">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="86e8a-128">Možným řešením možnosti jsou následující:</span><span class="sxs-lookup"><span data-stu-id="86e8a-128">Possible resolution options are the following:</span></span>  
  
    -   <span data-ttu-id="86e8a-129">Nainstalujte požadované sestavení v globální mezipaměti sestavení a volání.</span><span class="sxs-lookup"><span data-stu-id="86e8a-129">Install the requested assembly in the global assembly cache and call the.</span></span> <span data-ttu-id="86e8a-130"><xref:System.Reflection.Assembly.Load%2A> Metoda pro načtení sestavení podle identity.</span><span class="sxs-lookup"><span data-stu-id="86e8a-130"><xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>  
  
    -   <span data-ttu-id="86e8a-131">Zkopírujte požadované sestavení do adresáře aplikace a volání <xref:System.Reflection.Assembly.Load%2A> metodu pro načtení sestavení podle identity.</span><span class="sxs-lookup"><span data-stu-id="86e8a-131">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>  
  
    -   <span data-ttu-id="86e8a-132">Změna konfigurace domény aplikace 00Z došlo k chybě vazby neobsahuje cestu k sestavení tak, že buď změníte <xref:System.AppDomain.BaseDirectory%2A> vlastnost nebo přidání privátní definovaných cest.</span><span class="sxs-lookup"><span data-stu-id="86e8a-132">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>  
  
    -   <span data-ttu-id="86e8a-133">Změna seznamu řízení přístupu k souboru uživatel přihlášený ke čtení souboru.</span><span class="sxs-lookup"><span data-stu-id="86e8a-133">Change the access control list for the file to allow the logged-on user to read the file.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="86e8a-134">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="86e8a-134">Effect on the Runtime</span></span>  
 <span data-ttu-id="86e8a-135">Toto MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="86e8a-135">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="86e8a-136">Sestavy pouze data o selhání vazby.</span><span class="sxs-lookup"><span data-stu-id="86e8a-136">It only reports data about binding failures.</span></span>  
  
## <a name="output"></a><span data-ttu-id="86e8a-137">Výstup</span><span class="sxs-lookup"><span data-stu-id="86e8a-137">Output</span></span>  
 <span data-ttu-id="86e8a-138">MDA sestavy sestavení, které se nepodařilo načíst, včetně požadovanou cestu a/nebo zobrazované jméno, kontext vazby, domény aplikace, ve kterém byl vyžádán zatížení a důvod selhání.</span><span class="sxs-lookup"><span data-stu-id="86e8a-138">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>  
  
 <span data-ttu-id="86e8a-139">Zobrazovaný název nebo požadovaná cesta může být prázdné, pokud tato data nebyla k dispozici pro modul CLR.</span><span class="sxs-lookup"><span data-stu-id="86e8a-139">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="86e8a-140">Pokud bylo volání, které se nepovedlo <xref:System.Reflection.Assembly.Load%2A> metoda, je pravděpodobné, modul runtime nelze určit, zobrazovaný název sestavení.</span><span class="sxs-lookup"><span data-stu-id="86e8a-140">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="86e8a-141">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="86e8a-141">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <bindingFailure />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="86e8a-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="86e8a-142">Example</span></span>  
 <span data-ttu-id="86e8a-143">Následující příklad kódu ukazuje situaci, která může aktivovat toto MDA:</span><span class="sxs-lookup"><span data-stu-id="86e8a-143">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```csharp
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
  
## <a name="see-also"></a><span data-ttu-id="86e8a-144">Viz také</span><span class="sxs-lookup"><span data-stu-id="86e8a-144">See Also</span></span>  
 [<span data-ttu-id="86e8a-145">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="86e8a-145">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
