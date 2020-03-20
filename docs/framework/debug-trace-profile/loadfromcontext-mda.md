---
title: loadFromContext – pomocník spravovaného ladění (MDA)
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), LoadFrom context
- managed debugging assistants (MDAs), LoadFrom context
- LoadFrom context
- LoadFromContext MDA
ms.assetid: a9b14db1-d3a9-4150-a767-dcf3aea0071a
ms.openlocfilehash: d0090a0272d1c3b6175b351175689df1e1e4fdbd
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79181799"
---
# <a name="loadfromcontext-mda"></a><span data-ttu-id="0d203-102">loadFromContext – pomocník spravovaného ladění (MDA)</span><span class="sxs-lookup"><span data-stu-id="0d203-102">loadFromContext MDA</span></span>
<span data-ttu-id="0d203-103">Spravovaný `loadFromContext` pomocník pro ladění (MDA) je aktivován, `LoadFrom` pokud je sestavení načteno do kontextu.</span><span class="sxs-lookup"><span data-stu-id="0d203-103">The `loadFromContext` managed debugging assistant (MDA) is activated if an assembly is loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="0d203-104">Tato situace může nastat <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> v důsledku volání nebo jiné podobné metody.</span><span class="sxs-lookup"><span data-stu-id="0d203-104">This situation can occur as a result of calling <xref:System.Reflection.Assembly.LoadFrom%2A?displayProperty=nameWithType> or other similar methods.</span></span>  
  
## <a name="symptoms"></a><span data-ttu-id="0d203-105">Příznaky</span><span class="sxs-lookup"><span data-stu-id="0d203-105">Symptoms</span></span>  
 <span data-ttu-id="0d203-106">Použití některých metod zavaděče může mít `LoadFrom` za následek sestavení načtenv kontextu.</span><span class="sxs-lookup"><span data-stu-id="0d203-106">The use of some loader methods can result in assemblies being loaded in the `LoadFrom` context.</span></span> <span data-ttu-id="0d203-107">Použití tohoto kontextu může mít za následek neočekávané chování pro serializaci, přetypování a řešení závislostí.</span><span class="sxs-lookup"><span data-stu-id="0d203-107">The use of this context can result in unexpected behavior for serialization, casting, and dependency resolution.</span></span> <span data-ttu-id="0d203-108">Obecně se doporučuje, aby sestavení být `Load` načteny do kontextu, aby se zabránilo těmto problémům.</span><span class="sxs-lookup"><span data-stu-id="0d203-108">In general, it is recommended that assemblies be loaded into the `Load` context to avoid these problems.</span></span> <span data-ttu-id="0d203-109">Je obtížné určit, do kterého kontextu bylo sestavení načteno bez tohoto MDA.</span><span class="sxs-lookup"><span data-stu-id="0d203-109">It is difficult to determine which context an assembly has been loaded into without this MDA.</span></span>  
  
## <a name="cause"></a><span data-ttu-id="0d203-110">Příčina</span><span class="sxs-lookup"><span data-stu-id="0d203-110">Cause</span></span>  
 <span data-ttu-id="0d203-111">Obecně platí, že sestavení `LoadFrom` bylo načteno do kontextu, `Load` pokud bylo načteno z <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> cesty mimo kontext, jako je například globální mezipaměť sestavení nebo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="0d203-111">Generally, an assembly was loaded into the `LoadFrom` context if it was loaded from a path outside the `Load` context, such as the global assembly cache or the <xref:System.AppDomainSetup.ApplicationBase%2A?displayProperty=nameWithType> property.</span></span>  
  
## <a name="resolution"></a><span data-ttu-id="0d203-112">Řešení</span><span class="sxs-lookup"><span data-stu-id="0d203-112">Resolution</span></span>  
 <span data-ttu-id="0d203-113">Nakonfigurujte aplikace tak, aby <xref:System.Reflection.Assembly.LoadFrom%2A> volání již není potřeba.</span><span class="sxs-lookup"><span data-stu-id="0d203-113">Configure applications such that <xref:System.Reflection.Assembly.LoadFrom%2A> calls are no longer needed.</span></span> <span data-ttu-id="0d203-114">K tomu můžete použít následující techniky:</span><span class="sxs-lookup"><span data-stu-id="0d203-114">You can use the following techniques for doing so:</span></span>  
  
- <span data-ttu-id="0d203-115">Nainstalujte sestavení do globální mezipaměti sestavení.</span><span class="sxs-lookup"><span data-stu-id="0d203-115">Install assemblies in the global assembly cache.</span></span>  
  
- <span data-ttu-id="0d203-116">Umístěte sestavení do <xref:System.AppDomainSetup.ApplicationBase%2A> adresáře <xref:System.AppDomain>pro rozhraní .</span><span class="sxs-lookup"><span data-stu-id="0d203-116">Place assemblies in the <xref:System.AppDomainSetup.ApplicationBase%2A> directory for the <xref:System.AppDomain>.</span></span> <span data-ttu-id="0d203-117">V případě výchozí domény je <xref:System.AppDomainSetup.ApplicationBase%2A> adresář ten, který obsahuje spustitelný soubor, který proces spustil.</span><span class="sxs-lookup"><span data-stu-id="0d203-117">In the case of the default domain, the <xref:System.AppDomainSetup.ApplicationBase%2A> directory is the one that contains the executable file that started the process.</span></span> <span data-ttu-id="0d203-118">To může také vyžadovat <xref:System.AppDomain> vytvoření nového, pokud není vhodné přesunout sestavení.</span><span class="sxs-lookup"><span data-stu-id="0d203-118">This might also require creating a new <xref:System.AppDomain> if it is not convenient to move the assembly.</span></span>  
  
- <span data-ttu-id="0d203-119">Přidejte cestu zjišťování do souboru konfigurace aplikace (.config) nebo do sekundárních aplikačních domén, pokud jsou závislá sestavení v podřízených adresářích vzhledem ke spustitelnému souboru.</span><span class="sxs-lookup"><span data-stu-id="0d203-119">Add a probing path to your application configuration (.config) file or to secondary  application domains if dependent assemblies are in child directories relative to the executable.</span></span>  
  
 <span data-ttu-id="0d203-120">V každém případě kód lze změnit <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> na použití metody.</span><span class="sxs-lookup"><span data-stu-id="0d203-120">In each case, the code can be changed to use the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
## <a name="effect-on-the-runtime"></a><span data-ttu-id="0d203-121">Vliv na běhový čas</span><span class="sxs-lookup"><span data-stu-id="0d203-121">Effect on the Runtime</span></span>  
 <span data-ttu-id="0d203-122">MDA nemá žádný vliv na CLR.</span><span class="sxs-lookup"><span data-stu-id="0d203-122">The MDA does not have any effect on the CLR.</span></span> <span data-ttu-id="0d203-123">Hlásí kontext, který byl použit v důsledku požadavku na zatížení.</span><span class="sxs-lookup"><span data-stu-id="0d203-123">It reports the context that was used as a result of a load request.</span></span>  
  
## <a name="output"></a><span data-ttu-id="0d203-124">Výstup</span><span class="sxs-lookup"><span data-stu-id="0d203-124">Output</span></span>  
 <span data-ttu-id="0d203-125">MDA hlásí, že sestavení bylo `LoadFrom` načteno do kontextu.</span><span class="sxs-lookup"><span data-stu-id="0d203-125">The MDA reports that the assembly was loaded into the `LoadFrom` context.</span></span> <span data-ttu-id="0d203-126">Určuje jednoduchý název sestavení a cesty.</span><span class="sxs-lookup"><span data-stu-id="0d203-126">It specifies the simple name of the assembly and the path.</span></span> <span data-ttu-id="0d203-127">Navrhuje také skutečnosti snižující závažnost `LoadFrom` rizika, aby se zabránilo použití kontextu.</span><span class="sxs-lookup"><span data-stu-id="0d203-127">It also suggests mitigations to avoid using the `LoadFrom` context.</span></span>  
  
## <a name="configuration"></a><span data-ttu-id="0d203-128">Konfigurace</span><span class="sxs-lookup"><span data-stu-id="0d203-128">Configuration</span></span>  
  
```xml  
<mdaConfig>  
  <assistants>  
    <loadFromContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="example"></a><span data-ttu-id="0d203-129">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d203-129">Example</span></span>  
 <span data-ttu-id="0d203-130">Následující příklad kódu ukazuje situaci, která může aktivovat tento MDA:</span><span class="sxs-lookup"><span data-stu-id="0d203-130">The following code example demonstrates a situation that can activate this MDA:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="0d203-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="0d203-131">See also</span></span>

- [<span data-ttu-id="0d203-132">Diagnostikování chyb pomocí asistentů spravovaného ladění</span><span class="sxs-lookup"><span data-stu-id="0d203-132">Diagnosing Errors with Managed Debugging Assistants</span></span>](diagnosing-errors-with-managed-debugging-assistants.md)
