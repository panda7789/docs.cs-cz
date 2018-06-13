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
ms.openlocfilehash: e1ba65194c49f76bb5c29ed28b1b038c02cf1a59
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393078"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="a5d73-102">loadFromContext – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="a5d73-102">loadFromContext MDA</span></span>
<span data-ttu-id="a5d73-103">`loadFromContext` Pomocník spravovaného ladění (MDA) se aktivuje, pokud je načtena do sestavení `LoadFrom` kontextu.</span><span class="sxs-lookup"><span data-stu-id="a5d73-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="a5d73-104">Tato situace může nastat v důsledku volání <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> nebo jiné podobné metody.</span><span class="sxs-lookup"><span data-stu-id="a5d73-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="a5d73-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="a5d73-105">Symptoms</span></span>  
 <span data-ttu-id="a5d73-106">Použití některé metody zavaděč může mít za následek načítá v sestavení `LoadFrom` kontextu.</span><span class="sxs-lookup"><span data-stu-id="a5d73-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="a5d73-107">Použití tohoto kontextu může způsobit neočekávané chování pro serializaci, přetypování a zjištění závislosti.</span><span class="sxs-lookup"><span data-stu-id="a5d73-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="a5d73-108">Obecně se doporučuje, aby sestavení být načtena do `Load` kontext, který má se těmto problémům vyhnuli.</span><span class="sxs-lookup"><span data-stu-id="a5d73-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="a5d73-109">Je obtížné určit, které kontext sestavení bylo načteno do bez této (mda).</span><span class="sxs-lookup"><span data-stu-id="a5d73-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="a5d73-110">příčina</span><span class="sxs-lookup"><span data-stu-id="a5d73-110">Cause</span></span>  
 <span data-ttu-id="a5d73-111">Obecně platí, sestavení bylo načteno do `LoadFrom` kontextu, pokud byla načtena z cesty mimo `Load` kontextu, jako je například globální mezipaměti sestavení nebo <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a5d73-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="a5d73-112">Rozlišení</span><span class="sxs-lookup"><span data-stu-id="a5d73-112">Resolution</span></span>  
 <span data-ttu-id="a5d73-113">Konfigurace aplikací tak, aby <xref:System.Reflection.Assembly.LoadFrom%2A> volání už nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="a5d73-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="a5d73-114">Jak to udělat, můžete použít následující postupy:</span><span class="sxs-lookup"><span data-stu-id="a5d73-114">You can use the following techniques for doing so:</span></span>  
  
-   <span data-ttu-id="a5d73-115">Instalace sestavení v globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="a5d73-115">Install assemblies in the global assembly cache.</span></span>  
  
-   <span data-ttu-id="a5d73-116">Sestavení v umístit <xref:System.AppDomainSetup.ApplicationBase%2A> adresář pro <xref:System.AppDomain>.</span><span class="sxs-lookup"><span data-stu-id="a5d73-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="a5d73-117">V případě výchozí doménu <xref:System.AppDomainSetup.ApplicationBase%2A> adresář je ta, která obsahuje spustitelný soubor, který spustil proces.</span><span class="sxs-lookup"><span data-stu-id="a5d73-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="a5d73-118">To může také vyžadovat vytvoření nové <xref:System.AppDomain> Pokud není vhodné pro přesun sestavení.</span><span class="sxs-lookup"><span data-stu-id="a5d73-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
-   <span data-ttu-id="a5d73-119">Přidejte cestu k testování konfiguračním (config) souboru aplikace nebo sekundární aplikační domény, pokud jsou závislé sestavení v podřízených adresářích relativně ke spustitelnému souboru.</span><span class="sxs-lookup"><span data-stu-id="a5d73-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="a5d73-120">V každém případě může změnit kód tak, aby použít <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metoda.</span><span class="sxs-lookup"><span data-stu-id="a5d73-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="a5d73-121">Vliv na modulu Runtime</span><span class="sxs-lookup"><span data-stu-id="a5d73-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="a5d73-122">MDA nemá žádný vliv na modulu CLR.</span><span class="sxs-lookup"><span data-stu-id="a5d73-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="a5d73-123">Oznámí kontext, který byl použit jako výsledek požadavku na zatížení.</span><span class="sxs-lookup"><span data-stu-id="a5d73-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="a5d73-124">Výstup</span><span class="sxs-lookup"><span data-stu-id="a5d73-124">Output</span></span>  
 <span data-ttu-id="a5d73-125">MDA hlásí, že sestavení bylo načteno do `LoadFrom` kontextu.</span><span class="sxs-lookup"><span data-stu-id="a5d73-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="a5d73-126">Určuje jednoduchý název sestavení a cestu.</span><span class="sxs-lookup"><span data-stu-id="a5d73-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="a5d73-127">Rovněž nabízí jejich zmírnění pro nepoužívejte `LoadFrom` kontextu.</span><span class="sxs-lookup"><span data-stu-id="a5d73-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="a5d73-128">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="a5d73-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="a5d73-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="a5d73-129">Example</span></span>  
 <span data-ttu-id="a5d73-130">Následující příklad kódu ukazuje situace, které můžou aktivovat tuto (mda):</span><span class="sxs-lookup"><span data-stu-id="a5d73-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="a5d73-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="a5d73-131">See Also</span></span>  
 [<span data-ttu-id="a5d73-132">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="a5d73-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
