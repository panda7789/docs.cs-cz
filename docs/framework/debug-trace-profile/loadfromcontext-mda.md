---
title: loadFromContext – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: 28ef6e12c82cf5ca56962756b9ea964d0ae9baaa
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216163"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="86ce2-102">loadFromContext – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="86ce2-102">loadFromContext MDA</span></span>
<span data-ttu-id="86ce2-103">Pokud je sestavení načteno do kontextu `LoadFrom`, je aktivována aplikace `loadFromContext` Managed Debugging Assistant (MDA).</span><span class="sxs-lookup"><span data-stu-id="86ce2-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="86ce2-104">Tato situace může nastat v důsledku volání <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> nebo jiných podobných metod.</span><span class="sxs-lookup"><span data-stu-id="86ce2-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="86ce2-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="86ce2-105">Symptoms</span></span>  
 <span data-ttu-id="86ce2-106">Použití některých metod zavaděče může mít za následek načítání sestavení v kontextu `LoadFrom`.</span><span class="sxs-lookup"><span data-stu-id="86ce2-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="86ce2-107">Použití tohoto kontextu může vést k neočekávanému chování při serializaci, přetypování a rozlišení závislostí.</span><span class="sxs-lookup"><span data-stu-id="86ce2-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="86ce2-108">Obecně se doporučuje, aby byla sestavení načtena do `Load`ho kontextu, aby se předešlo těmto problémům.</span><span class="sxs-lookup"><span data-stu-id="86ce2-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="86ce2-109">Je obtížné určit, který kontext bylo sestavení načteno bez tohoto MDA.</span><span class="sxs-lookup"><span data-stu-id="86ce2-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="86ce2-110">Příčina</span><span class="sxs-lookup"><span data-stu-id="86ce2-110">Cause</span></span>  
 <span data-ttu-id="86ce2-111">Obecně platí, že sestavení bylo načteno do kontextu `LoadFrom`, pokud bylo načteno z cesty mimo `Load` kontext, jako je například globální mezipaměť sestavení (GAC) nebo vlastnost <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="86ce2-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="86ce2-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="86ce2-112">Resolution</span></span>  
 <span data-ttu-id="86ce2-113">Konfigurace aplikací, například <xref:System.Reflection.Assembly.LoadFrom%2A> volání již nejsou potřeba.</span><span class="sxs-lookup"><span data-stu-id="86ce2-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="86ce2-114">K tomu můžete použít následující postupy:</span><span class="sxs-lookup"><span data-stu-id="86ce2-114">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="86ce2-115">Nainstalujte sestavení do globální mezipaměti sestavení (GAC).</span><span class="sxs-lookup"><span data-stu-id="86ce2-115">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="86ce2-116">Pro <xref:System.AppDomain>umístěte sestavení do adresáře <xref:System.AppDomainSetup.ApplicationBase%2A>.</span><span class="sxs-lookup"><span data-stu-id="86ce2-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="86ce2-117">V případě výchozí domény je <xref:System.AppDomainSetup.ApplicationBase%2A> adresářem, který obsahuje spustitelný soubor, který proces zahájil.</span><span class="sxs-lookup"><span data-stu-id="86ce2-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="86ce2-118">To může také vyžadovat vytvoření nového <xref:System.AppDomain>, pokud není vhodné přesunout sestavení.</span><span class="sxs-lookup"><span data-stu-id="86ce2-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="86ce2-119">Přidejte cestu pro zjišťování do konfiguračního souboru aplikace (. config) nebo do domén sekundární aplikace, pokud jsou závislá sestavení v podřízených adresářích vzhledem ke spustitelnému souboru.</span><span class="sxs-lookup"><span data-stu-id="86ce2-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="86ce2-120">V každém případě může být kód změněn tak, aby používal metodu <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="86ce2-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="86ce2-121">Vliv na modul runtime</span><span class="sxs-lookup"><span data-stu-id="86ce2-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="86ce2-122">Modul MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="86ce2-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="86ce2-123">Oznamuje kontext, který byl použit jako výsledek žádosti o načtení.</span><span class="sxs-lookup"><span data-stu-id="86ce2-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="86ce2-124">Výstup</span><span class="sxs-lookup"><span data-stu-id="86ce2-124">Output</span></span>  
 <span data-ttu-id="86ce2-125">MDA hlásí, že bylo sestavení načteno do kontextu `LoadFrom`.</span><span class="sxs-lookup"><span data-stu-id="86ce2-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="86ce2-126">Určuje jednoduchý název sestavení a cesty.</span><span class="sxs-lookup"><span data-stu-id="86ce2-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="86ce2-127">Navrhuje také zmírnění rizik, aby se předešlo použití `LoadFrom`ho kontextu.</span><span class="sxs-lookup"><span data-stu-id="86ce2-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="86ce2-128">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="86ce2-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="86ce2-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="86ce2-129">Example</span></span>  
 <span data-ttu-id="86ce2-130">Následující příklad kódu ukazuje situaci, která může aktivovat Tento MDA:</span><span class="sxs-lookup"><span data-stu-id="86ce2-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="86ce2-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="86ce2-131">See also</span></span>

- [<span data-ttu-id="86ce2-132">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="86ce2-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
