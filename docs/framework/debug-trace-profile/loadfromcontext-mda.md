---
title: loadFromContext – pomocník spravovaného ladění (MDA)
description: Pochopení pomocníka spravovaného ladění Loadfromcontext – (MDA) v rozhraní .NET, který se aktivuje, pokud je sestavení načteno do kontextu LoadFrom.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 8d55268f2b2106dde4e488a6f0271fd3b17349da
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051646"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="99bc9-103">loadFromContext – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="99bc9-103">loadFromContext MDA</span></span>
<span data-ttu-id="99bc9-104">`loadFromContext`Pokud je sestavení načteno do kontextu, je aktivován pomocník spravovaného ladění (MDA) `LoadFrom` .</span><span class="sxs-lookup"><span data-stu-id="99bc9-104">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="99bc9-105">Tato situace může nastat v důsledku volání <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> nebo podobných metod.</span><span class="sxs-lookup"><span data-stu-id="99bc9-105">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="99bc9-106">Příznaky</span><span class="sxs-lookup"><span data-stu-id="99bc9-106">Symptoms</span></span>  
 <span data-ttu-id="99bc9-107">Použití některých metod zavaděče může vést k tomu, že sestavení jsou načtena v `LoadFrom` kontextu.</span><span class="sxs-lookup"><span data-stu-id="99bc9-107">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="99bc9-108">Použití tohoto kontextu může vést k neočekávanému chování při serializaci, přetypování a rozlišení závislostí.</span><span class="sxs-lookup"><span data-stu-id="99bc9-108">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="99bc9-109">Obecně se doporučuje, aby byla sestavení načtena do kontextu, `Load` aby se tyto problémy předešly.</span><span class="sxs-lookup"><span data-stu-id="99bc9-109">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="99bc9-110">Je obtížné určit, který kontext bylo sestavení načteno bez tohoto MDA.</span><span class="sxs-lookup"><span data-stu-id="99bc9-110">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="99bc9-111">Příčina</span><span class="sxs-lookup"><span data-stu-id="99bc9-111">Cause</span></span>  
 <span data-ttu-id="99bc9-112">Obecně platí, že sestavení bylo načteno do `LoadFrom` kontextu, pokud bylo načteno z cesty mimo `Load` kontext, jako je například globální mezipaměť sestavení (GAC) nebo <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="99bc9-112">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="99bc9-113">Řešení</span><span class="sxs-lookup"><span data-stu-id="99bc9-113">Resolution</span></span>  
 <span data-ttu-id="99bc9-114">Nakonfigurujte aplikace tak, aby <xref:System.Reflection.Assembly.LoadFrom%2A> již nevyžadovaly volání.</span><span class="sxs-lookup"><span data-stu-id="99bc9-114">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="99bc9-115">K tomu můžete použít následující postupy:</span><span class="sxs-lookup"><span data-stu-id="99bc9-115">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="99bc9-116">Nainstalujte sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="99bc9-116">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="99bc9-117">Umístěte sestavení do <xref:System.AppDomainSetup.ApplicationBase%2A> adresáře pro <xref:System.AppDomain> .</span><span class="sxs-lookup"><span data-stu-id="99bc9-117">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="99bc9-118">V případě výchozí domény <xref:System.AppDomainSetup.ApplicationBase%2A> je adresář souborem, který obsahuje spustitelný soubor, který proces zahájil.</span><span class="sxs-lookup"><span data-stu-id="99bc9-118">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="99bc9-119">To může také vyžadovat vytvoření nového, <xref:System.AppDomain> Pokud není vhodné přesunout sestavení.</span><span class="sxs-lookup"><span data-stu-id="99bc9-119">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="99bc9-120">Přidejte cestu pro zjišťování do konfiguračního souboru aplikace (. config) nebo do domén sekundární aplikace, pokud jsou závislá sestavení v podřízených adresářích vzhledem ke spustitelnému souboru.</span><span class="sxs-lookup"><span data-stu-id="99bc9-120">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="99bc9-121">V každém případě může být kód změněn tak, aby používal <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metodu.</span><span class="sxs-lookup"><span data-stu-id="99bc9-121">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="99bc9-122">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="99bc9-122">Effect on the Runtime</span></span>  
 <span data-ttu-id="99bc9-123">Modul MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="99bc9-123">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="99bc9-124">Oznamuje kontext, který byl použit jako výsledek žádosti o načtení.</span><span class="sxs-lookup"><span data-stu-id="99bc9-124">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="99bc9-125">Výstup</span><span class="sxs-lookup"><span data-stu-id="99bc9-125">Output</span></span>  
 <span data-ttu-id="99bc9-126">MDA hlásí, že sestavení bylo načteno do `LoadFrom` kontextu.</span><span class="sxs-lookup"><span data-stu-id="99bc9-126">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="99bc9-127">Určuje jednoduchý název sestavení a cesty.</span><span class="sxs-lookup"><span data-stu-id="99bc9-127">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="99bc9-128">Navrhuje také zmírnění rizik, aby nedocházelo k používání `LoadFrom` kontextu.</span><span class="sxs-lookup"><span data-stu-id="99bc9-128">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="99bc9-129">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="99bc9-129">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="99bc9-130">Příklad</span><span class="sxs-lookup"><span data-stu-id="99bc9-130">Example</span></span>  
 <span data-ttu-id="99bc9-131">Následující příklad kódu ukazuje situaci, která může aktivovat Tento MDA:</span><span class="sxs-lookup"><span data-stu-id="99bc9-131">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="99bc9-132">Viz také</span><span class="sxs-lookup"><span data-stu-id="99bc9-132">See also</span></span>

- [<span data-ttu-id="99bc9-133">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="99bc9-133">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
