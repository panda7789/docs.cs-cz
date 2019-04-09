---
title: loadFromContext – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 01b2cf06a5ab921f5ae89da4856e8164b6f57db5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59098602"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="62c8e-102">loadFromContext – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="62c8e-102">loadFromContext MDA</span></span>
<span data-ttu-id="62c8e-103">`loadFromContext` Pomocníka spravovaného ladění (MDA) se aktivuje, pokud je sestavení načteno do `LoadFrom` kontextu.</span><span class="sxs-lookup"><span data-stu-id="62c8e-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="62c8e-104">Tato situace může nastat v důsledku volání <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> nebo další podobné metody.</span><span class="sxs-lookup"><span data-stu-id="62c8e-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="62c8e-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="62c8e-105">Symptoms</span></span>  
 <span data-ttu-id="62c8e-106">Pomocí některé metody zavaděč může vést k načítání v sestavení `LoadFrom` kontextu.</span><span class="sxs-lookup"><span data-stu-id="62c8e-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="62c8e-107">Použití tohoto kontextu může způsobit neočekávané chování pro serializaci, přetypování a řešení závislostí.</span><span class="sxs-lookup"><span data-stu-id="62c8e-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="62c8e-108">Obecně je vhodné, že sestavení načtena do `Load` kontext k těmto problémům vyhnout.</span><span class="sxs-lookup"><span data-stu-id="62c8e-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="62c8e-109">Je obtížné určit kontext sestavení bylo načteno do bez toto MDA.</span><span class="sxs-lookup"><span data-stu-id="62c8e-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="62c8e-110">Příčina</span><span class="sxs-lookup"><span data-stu-id="62c8e-110">Cause</span></span>  
 <span data-ttu-id="62c8e-111">Obecně platí, bylo načteno do sestavení `LoadFrom` kontextu, pokud byl načten z cesty `Load` kontextu, jako je například globální mezipaměti sestavení nebo <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="62c8e-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="62c8e-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="62c8e-112">Resolution</span></span>  
 <span data-ttu-id="62c8e-113">Konfigurace aplikací tak, aby <xref:System.Reflection.Assembly.LoadFrom%2A> volání už nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="62c8e-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="62c8e-114">Následující postupy můžete to udělat:</span><span class="sxs-lookup"><span data-stu-id="62c8e-114">You can use the following techniques for doing so:</span></span>  
  
-   <span data-ttu-id="62c8e-115">Nainstalujte sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="62c8e-115">Install assemblies in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="62c8e-116">Sestavení v umístit <xref:System.AppDomainSetup.ApplicationBase%2A> adresář <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="62c8e-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="62c8e-117">V případě výchozí doménu <xref:System.AppDomainSetup.ApplicationBase%2A> adresář je ten, který obsahuje spustitelný soubor, který spustil proces.</span><span class="sxs-lookup"><span data-stu-id="62c8e-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="62c8e-118">To může také vyžadovat vytvoření nového <xref:System.AppDomain> Pokud není vhodné přesunout sestavení.</span><span class="sxs-lookup"><span data-stu-id="62c8e-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
-   <span data-ttu-id="62c8e-119">Přidáte cesta zjišťování (.config) konfigurační soubor aplikace nebo sekundární aplikačních doménách, pokud jsou závislé sestavení v adresářích podřízené vzhledem ke spustitelnému souboru.</span><span class="sxs-lookup"><span data-stu-id="62c8e-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="62c8e-120">V obou případech lze změnit kód určený <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="62c8e-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="62c8e-121">Vliv na modul Runtime</span><span class="sxs-lookup"><span data-stu-id="62c8e-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="62c8e-122">MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="62c8e-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="62c8e-123">Oznámí kontext, který se použil jako výsledek požadavku na zatížení.</span><span class="sxs-lookup"><span data-stu-id="62c8e-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="62c8e-124">Výstup</span><span class="sxs-lookup"><span data-stu-id="62c8e-124">Output</span></span>  
 <span data-ttu-id="62c8e-125">MDA hlásí, že sestavení bylo načteno do `LoadFrom` kontextu.</span><span class="sxs-lookup"><span data-stu-id="62c8e-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="62c8e-126">Určuje jednoduchý název sestavení a cestu.</span><span class="sxs-lookup"><span data-stu-id="62c8e-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="62c8e-127">Rovněž navrhuje způsoby zmírnění rizik, abyste se vyhnuli použití `LoadFrom` kontextu.</span><span class="sxs-lookup"><span data-stu-id="62c8e-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="62c8e-128">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="62c8e-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="62c8e-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="62c8e-129">Example</span></span>  
 <span data-ttu-id="62c8e-130">Následující příklad kódu ukazuje situaci, která může aktivovat toto MDA:</span><span class="sxs-lookup"><span data-stu-id="62c8e-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```csharp
using System.Reflection;  
namespace ConsoleApplication1  
{  
    class Program  
    {  
        static void Main(string[] args)  
        {  
            // The following call caused the LoadFrom context to be used  
            // because the assembly is loaded using LoadFrom and the path is   
            // located outside of the Load context probing path.   
            Assembly.LoadFrom(@"C:\Text\Test.dll");  
        }  
    }  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="62c8e-131">Viz také:</span><span class="sxs-lookup"><span data-stu-id="62c8e-131">See also</span></span>

- [<span data-ttu-id="62c8e-132">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="62c8e-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
