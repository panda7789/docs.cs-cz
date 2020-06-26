---
title: bindingFailure – pomocník spravovaného ladění (MDA)
description: Přečtěte si o Pomocníkovi spravovaném ladění bindingFailure – (MDA), který se aktivuje, když se nepovede načíst sestavení v .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- binding failure
- binding, failures
- MDAs (managed debugging assistants), binding failures
- assemblies [.NET Framework], binding failures
- managed debugging assistants (MDAs), binding failures
- BindingFailure MDA
ms.assetid: 26ada5af-175c-4576-931a-9f07fa1723e9
ms.openlocfilehash: 98c7947c7e5d2a1f0af8c26744d3b292ed8cb4c4
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415625"
---
# <a name="bindingfailure-mda"></a><span data-ttu-id="50ef9-103">bindingFailure – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="50ef9-103">bindingFailure MDA</span></span>

<span data-ttu-id="50ef9-104">`bindingFailure`Pokud se sestavení nepovede načíst, aktivuje se pomocník spravovaného ladění (MDA).</span><span class="sxs-lookup"><span data-stu-id="50ef9-104">The `bindingFailure` managed debugging assistant (MDA) is activated when an assembly fails to load.</span></span>

## <a name="symptoms"></a><span data-ttu-id="50ef9-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="50ef9-105">Symptoms</span></span>

<span data-ttu-id="50ef9-106">Kód se pokusil načíst sestavení pomocí statického odkazu nebo jedné z metod zavaděče, například <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> nebo <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="50ef9-106">Code has attempted to load an assembly using a static reference or one of the loader methods, such as <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="50ef9-107">Sestavení není načteno a <xref:System.IO.FileNotFoundException> <xref:System.IO.FileLoadException> je vyvolána výjimka nebo.</span><span class="sxs-lookup"><span data-stu-id="50ef9-107">The assembly is not loaded and a <xref:System.IO.FileNotFoundException> or <xref:System.IO.FileLoadException> exception is thrown.</span></span>

## <a name="cause"></a><span data-ttu-id="50ef9-108">Příčina</span><span class="sxs-lookup"><span data-stu-id="50ef9-108">Cause</span></span>

<span data-ttu-id="50ef9-109">K selhání vazby dojde v případě, že modul runtime nemůže načíst sestavení.</span><span class="sxs-lookup"><span data-stu-id="50ef9-109">A binding failure occurs when the runtime is unable to load an assembly.</span></span> <span data-ttu-id="50ef9-110">Selhání vazby může být výsledkem jedné z následujících situací:</span><span class="sxs-lookup"><span data-stu-id="50ef9-110">A binding failure might be the result of one of the following situations:</span></span>

- <span data-ttu-id="50ef9-111">Modul CLR (Common Language Runtime) nemůže najít požadované sestavení.</span><span class="sxs-lookup"><span data-stu-id="50ef9-111">The common language runtime (CLR) cannot find the requested assembly.</span></span> <span data-ttu-id="50ef9-112">K tomu může dojít z mnoha důvodů, jako je například sestavení, které není nainstalováno nebo aplikace není správně nakonfigurována pro vyhledání sestavení.</span><span class="sxs-lookup"><span data-stu-id="50ef9-112">There are many reasons this can occur, such as the assembly not being installed or the application not being correctly configured to find the assembly.</span></span>

- <span data-ttu-id="50ef9-113">Běžný scénář problému předává typ jiné doméně aplikace, která vyžaduje, aby CLR načetl sestavení obsahující tento typ do druhé domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="50ef9-113">A common problem scenario is passing a type to another application domain, which requires the CLR to load the assembly containing that type in the other application domain.</span></span> <span data-ttu-id="50ef9-114">Může být možné, že modul runtime nebude moci načíst sestavení, pokud je jiná doména aplikace konfigurována odlišně od původní domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="50ef9-114">It may not be possible for the runtime to load the assembly if the other application domain is configured differently from the original application domain.</span></span> <span data-ttu-id="50ef9-115">Například dvě domény aplikace mohou mít různé <xref:System.AppDomain.BaseDirectory%2A> hodnoty vlastností.</span><span class="sxs-lookup"><span data-stu-id="50ef9-115">For example, the two application domains might have different <xref:System.AppDomain.BaseDirectory%2A> property values.</span></span>

- <span data-ttu-id="50ef9-116">Požadované sestavení je poškozeno nebo se nejedná o sestavení.</span><span class="sxs-lookup"><span data-stu-id="50ef9-116">The requested assembly is corrupted or is not an assembly.</span></span>

- <span data-ttu-id="50ef9-117">Kód, který se pokouší načíst sestavení, nemá správná oprávnění zabezpečení přístupu kódu k načtení sestavení.</span><span class="sxs-lookup"><span data-stu-id="50ef9-117">The code attempting to load the assembly does not have the correct code access security permissions to load assemblies.</span></span>

- <span data-ttu-id="50ef9-118">Přihlašovací údaje uživatele neposkytují požadovaná oprávnění ke čtení tohoto souboru.</span><span class="sxs-lookup"><span data-stu-id="50ef9-118">The user credentials do not provide the required permissions to read the file.</span></span>

## <a name="resolution"></a><span data-ttu-id="50ef9-119">Řešení</span><span class="sxs-lookup"><span data-stu-id="50ef9-119">Resolution</span></span>

<span data-ttu-id="50ef9-120">Prvním krokem je určit, proč se modul CLR nemůže přivážet k požadovanému sestavení.</span><span class="sxs-lookup"><span data-stu-id="50ef9-120">The first step is to determine why the CLR could not bind to the requested assembly.</span></span> <span data-ttu-id="50ef9-121">Existuje mnoho důvodů, proč modul runtime pravděpodobně nenajde nebo nedokázal načíst požadované sestavení, například scénáře uvedené v části Příčina.</span><span class="sxs-lookup"><span data-stu-id="50ef9-121">There are many reasons why the runtime might not have found or been able load the requested assembly, such as the scenarios listed in the Cause section.</span></span> <span data-ttu-id="50ef9-122">K odstranění příčiny selhání vazby doporučujeme následující akce:</span><span class="sxs-lookup"><span data-stu-id="50ef9-122">The following actions are recommended to eliminate the cause of the binding failure:</span></span>

- <span data-ttu-id="50ef9-123">Určete příčinu pomocí dat poskytovaných v rámci aplikace `bindingFailure` MDA:</span><span class="sxs-lookup"><span data-stu-id="50ef9-123">Determine the cause by using the data provided by the `bindingFailure` MDA:</span></span>

  - <span data-ttu-id="50ef9-124">Spusťte [Fuslogvw.exe (Prohlížeč protokolů vazby sestavení)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) a přečtěte si protokoly chyb vytvořené pořadačem sestavení.</span><span class="sxs-lookup"><span data-stu-id="50ef9-124">Run the [Fuslogvw.exe (Assembly Binding Log Viewer)](../tools/fuslogvw-exe-assembly-binding-log-viewer.md) to read the error logs produced by the assembly binder.</span></span>

  - <span data-ttu-id="50ef9-125">Určete, zda je sestavení v požadovaném umístění.</span><span class="sxs-lookup"><span data-stu-id="50ef9-125">Determine if the assembly is at the location requested.</span></span> <span data-ttu-id="50ef9-126">V případě <xref:System.Reflection.Assembly.LoadFrom%2A> <xref:System.Reflection.Assembly.LoadFile%2A> metod a lze požadované umístění snadno určit.</span><span class="sxs-lookup"><span data-stu-id="50ef9-126">In the case of the <xref:System.Reflection.Assembly.LoadFrom%2A> and <xref:System.Reflection.Assembly.LoadFile%2A> methods, the requested location can be easily determined.</span></span> <span data-ttu-id="50ef9-127">V případě <xref:System.Reflection.Assembly.Load%2A> metody, která se váže pomocí identity sestavení, je nutné vyhledat sestavení, která odpovídají této identitě v <xref:System.AppDomain.BaseDirectory%2A> cestě k vlastnostem vlastnosti domény aplikace a globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="50ef9-127">In the case of the <xref:System.Reflection.Assembly.Load%2A> method, which binds using the assembly identity, you must look for assemblies that match that identity in the application domain's <xref:System.AppDomain.BaseDirectory%2A> property probe path and the global assembly cache.</span></span>

- <span data-ttu-id="50ef9-128">Vyřešte příčinu na základě výše uvedeného rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="50ef9-128">Resolve the cause based on the preceding determination.</span></span> <span data-ttu-id="50ef9-129">Možné možnosti řešení jsou následující:</span><span class="sxs-lookup"><span data-stu-id="50ef9-129">Possible resolution options are the following:</span></span>

  - <span data-ttu-id="50ef9-130">Nainstalujte požadované sestavení do globální mezipaměti sestavení (GAC) a zavolejte na.</span><span class="sxs-lookup"><span data-stu-id="50ef9-130">Install the requested assembly in the global assembly cache and call the.</span></span> <span data-ttu-id="50ef9-131"><xref:System.Reflection.Assembly.Load%2A>Metoda pro načtení sestavení podle identity</span><span class="sxs-lookup"><span data-stu-id="50ef9-131"><xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="50ef9-132">Zkopírujte požadované sestavení do adresáře aplikace a zavolejte <xref:System.Reflection.Assembly.Load%2A> metodu pro načtení sestavení podle identity.</span><span class="sxs-lookup"><span data-stu-id="50ef9-132">Copy the requested assembly into the application directory and call the <xref:System.Reflection.Assembly.Load%2A> method to load the assembly by identity.</span></span>

  - <span data-ttu-id="50ef9-133">Překonfigurujte doménu aplikace, ve které došlo k chybě vazby, aby zahrnovala cestu sestavení, a to buď změnou <xref:System.AppDomain.BaseDirectory%2A> vlastnosti, nebo přidáním privátních cest probingu.</span><span class="sxs-lookup"><span data-stu-id="50ef9-133">Reconfigure the application domain in which the binding failure occurred to include the assembly path by either changing the <xref:System.AppDomain.BaseDirectory%2A> property or adding private probing paths.</span></span>

  - <span data-ttu-id="50ef9-134">Změňte seznam řízení přístupu pro soubor, aby mohl přihlášený uživatel číst soubor.</span><span class="sxs-lookup"><span data-stu-id="50ef9-134">Change the access control list for the file to allow the logged-on user to read the file.</span></span>

## <a name="effect-on-the-runtime"></a><span data-ttu-id="50ef9-135">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="50ef9-135">Effect on the Runtime</span></span>

<span data-ttu-id="50ef9-136">Tento MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="50ef9-136">This MDA has no effect on the CLR.</span></span> <span data-ttu-id="50ef9-137">Oznamuje pouze data o chybách vazeb.</span><span class="sxs-lookup"><span data-stu-id="50ef9-137">It only reports data about binding failures.</span></span>

## <a name="output"></a><span data-ttu-id="50ef9-138">Výstup</span><span class="sxs-lookup"><span data-stu-id="50ef9-138">Output</span></span>

<span data-ttu-id="50ef9-139">MDA hlásí sestavení, které se nepodařilo načíst, včetně požadované cesty nebo zobrazovaného názvu, kontextu vazby, domény aplikace, v níž bylo zatížení vyžádáno, a důvodu chyby.</span><span class="sxs-lookup"><span data-stu-id="50ef9-139">The MDA reports the assembly that failed to load, including the requested path and/or display name, the binding context, the application domain in which the load was requested, and the reason for the failure.</span></span>

<span data-ttu-id="50ef9-140">Pokud nejsou data pro CLR k dispozici, může být zobrazované jméno nebo požadovaná cesta prázdná.</span><span class="sxs-lookup"><span data-stu-id="50ef9-140">The display name or requested path may be blank if that data was not available to the CLR.</span></span> <span data-ttu-id="50ef9-141">Pokud volání metody neproběhlo <xref:System.Reflection.Assembly.Load%2A> , je pravděpodobně modulem runtime určení zobrazovaného názvu pro sestavení.</span><span class="sxs-lookup"><span data-stu-id="50ef9-141">If the call that failed was to the <xref:System.Reflection.Assembly.Load%2A> method, it is likely the runtime could not determine the display name for the assembly.</span></span>

## <a name="configuration"></a><span data-ttu-id="50ef9-142">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="50ef9-142">Configuration</span></span>

```xml
<mdaConfig>
  <assistants>
    <bindingFailure />
  </assistants>
</mdaConfig>
```

## <a name="example"></a><span data-ttu-id="50ef9-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="50ef9-143">Example</span></span>

<span data-ttu-id="50ef9-144">Následující příklad kódu ukazuje situaci, která může aktivovat Tento MDA:</span><span class="sxs-lookup"><span data-stu-id="50ef9-144">The following code example demonstrates a situation that can activate this MDA:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="50ef9-145">Viz také</span><span class="sxs-lookup"><span data-stu-id="50ef9-145">See also</span></span>

- [<span data-ttu-id="50ef9-146">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="50ef9-146">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
