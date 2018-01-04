---
title: "Doplňky a rozšíření"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- extensibility [.NET Framework], add-ins
- add-ins [.NET Framework]
- add-ins [.NET Framework], about
- hosts [.NET Framework], compared to add-ins
- .NET Framework, add-ins
- add-in pipeline [.NET Framework], about
- add-ins [.NET Framework], compared to hosts
- .NET Framework, extensibility
- versioning [.NET Framework], add-ins
ms.assetid: 8dd45b02-7218-40f9-857d-40d7b98b850b
caps.latest.revision: "42"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7e4d336992be216178b1237c9f43bffb3de61fba
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="add-ins-and-extensibility"></a><span data-ttu-id="11fb1-102">Doplňky a rozšíření</span><span class="sxs-lookup"><span data-stu-id="11fb1-102">Add-ins and Extensibility</span></span>
<a name="top"></a><span data-ttu-id="11fb1-103">Doplňky poskytují rozšířené funkce nebo služby pro hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="11fb1-103">Add-ins provide extended features or services for a host application.</span></span> <span data-ttu-id="11fb1-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Poskytuje programovací model, který mohou vývojáři k vývoji doplňky a jejich aktivaci ve svých aplikacích hostitele.</span><span class="sxs-lookup"><span data-stu-id="11fb1-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides a programming model that developers can use to develop add-ins and activate them in their host application.</span></span> <span data-ttu-id="11fb1-105">Model se dosahuje pomocí vytváření komunikační kanál mezi hostitelem a doplněk.</span><span class="sxs-lookup"><span data-stu-id="11fb1-105">The model achieves this by constructing a communication pipeline between the host and the add-in.</span></span> <span data-ttu-id="11fb1-106">Model je implementována pomocí typy v <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, a <xref:System.AddIn.Contract> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="11fb1-106">The model is implemented by using the types in the <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, and <xref:System.AddIn.Contract> namespaces.</span></span>  
  
 <span data-ttu-id="11fb1-107">Tento přehled obsahuje následující části:</span><span class="sxs-lookup"><span data-stu-id="11fb1-107">This overview contains the following sections:</span></span>  
  
-   [<span data-ttu-id="11fb1-108">Model doplňku</span><span class="sxs-lookup"><span data-stu-id="11fb1-108">Add-in Model</span></span>](#addin_model)  
  
-   [<span data-ttu-id="11fb1-109">Rozlišit doplňky a hostitele</span><span class="sxs-lookup"><span data-stu-id="11fb1-109">Distinguishing Between Add-ins and Hosts</span></span>](#distinguishing_between_addins_and_hosts)  
  
-   [<span data-ttu-id="11fb1-110">Související témata</span><span class="sxs-lookup"><span data-stu-id="11fb1-110">Related Topics</span></span>](#related_topics)  
  
-   [<span data-ttu-id="11fb1-111">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="11fb1-111">Reference</span></span>](#reference)  
  
> [!NOTE]
>  <span data-ttu-id="11fb1-112">Další ukázkový kód a zákazník technologie náhledy nástrojů můžete najít pro sestavování doplňku kanály v [spravované rozšiřitelnosti a Framework Add-In lokality na webu CodePlex](http://go.microsoft.com/fwlink/?LinkId=121190).</span><span class="sxs-lookup"><span data-stu-id="11fb1-112">You can find additional sample code, and customer technology previews of tools for building add-in pipelines, at the [Managed Extensibility and Add-In Framework site on CodePlex](http://go.microsoft.com/fwlink/?LinkId=121190).</span></span>  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a><span data-ttu-id="11fb1-113">Model doplňku</span><span class="sxs-lookup"><span data-stu-id="11fb1-113">Add-in Model</span></span>  
 <span data-ttu-id="11fb1-114">Model add-in se skládá z řady segmentů, které tvoří doplněk kanálu (také označované jako kanálu komunikace), která je zodpovědná za veškerou komunikaci mezi doplněk a hostitelem.</span><span class="sxs-lookup"><span data-stu-id="11fb1-114">The add-in model consists of a series of segments that make up the add-in pipeline (also known as the communication pipeline), that is responsible for all communication between the add-in and the host.</span></span> <span data-ttu-id="11fb1-115">Zřetězení příkazů je symetrický komunikační model segmentů, které výměnu dat mezi-in a jeho hostitele.</span><span class="sxs-lookup"><span data-stu-id="11fb1-115">The pipeline is a symmetrical communication model of segments that exchange data between an add-in and its host.</span></span> <span data-ttu-id="11fb1-116">Vývoj tyto segmenty mezi hostitelem a doplněk poskytuje požadované vrstvy abstrakce, které podporují správu verzí a izolace add-in.</span><span class="sxs-lookup"><span data-stu-id="11fb1-116">Developing these segments between the host and the add-in provides the required layers of abstraction that support versioning and isolation of the add-in.</span></span>  
  
 <span data-ttu-id="11fb1-117">Následující obrázek znázorňuje kanálu.</span><span class="sxs-lookup"><span data-stu-id="11fb1-117">The following illustration shows the pipeline.</span></span>  
  
 <span data-ttu-id="11fb1-118">![Přidat & č. 45; ve model kanálu. ] (../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span><span class="sxs-lookup"><span data-stu-id="11fb1-118">![Add&#45;in pipeline model.](../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span></span>  
<span data-ttu-id="11fb1-119">Kanál doplňku</span><span class="sxs-lookup"><span data-stu-id="11fb1-119">Add-in pipeline</span></span>  
  
 <span data-ttu-id="11fb1-120">Sestavení pro tyto segmenty nejsou nemusí být ve stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="11fb1-120">The assemblies for these segments are not required to be in the same application domain.</span></span> <span data-ttu-id="11fb1-121">Doplněk můžete načíst do své vlastní nové aplikace domény, do existující domény aplikace nebo i do domény aplikace hostitele.</span><span class="sxs-lookup"><span data-stu-id="11fb1-121">You can load an add-in into its own new application domain, into an existing application domain, or even into the host's application domain.</span></span> <span data-ttu-id="11fb1-122">Více add in můžete načíst do stejné domény aplikace, která umožňuje doplňků sdílet prostředky a kontexty zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="11fb1-122">You can load multiple add-ins into the same application domain, which enables the add-ins to share resources and security contexts.</span></span>  
  
 <span data-ttu-id="11fb1-123">Model doplňku podporuje a doporučuje hranici volitelné mezi hostitelem a doplněk, který se označuje jako hranic izolace (také označované jako hranici vzdálené komunikace).</span><span class="sxs-lookup"><span data-stu-id="11fb1-123">The add-in model supports, and recommends, an optional boundary between the host and the add-in, which is called the isolation boundary (also known as a remoting boundary).</span></span> <span data-ttu-id="11fb1-124">Tuto hranici může být hranice aplikace domény nebo proces.</span><span class="sxs-lookup"><span data-stu-id="11fb1-124">This boundary can be an application domain or process boundary.</span></span>  
  
 <span data-ttu-id="11fb1-125">Segment kontrakt uprostřed kanálu je načten do domény aplikace hostitele i v doplňku na domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="11fb1-125">The contract segment in the middle of the pipeline is loaded into both the host's application domain and the add-in's application domain.</span></span> <span data-ttu-id="11fb1-126">Kontrakt definuje virtuální metody, které hostitele a používání doplňku pro výměnu typy mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="11fb1-126">The contract defines the virtual methods that the host and the add-in use to exchange types with each other.</span></span>  
  
 <span data-ttu-id="11fb1-127">Předávat hranici izolace, musí být typy smluv nebo Serializovatelné typy.</span><span class="sxs-lookup"><span data-stu-id="11fb1-127">To pass through the isolation boundary, types must be either contracts or serializable types.</span></span> <span data-ttu-id="11fb1-128">Typy, které nejsou kontrakty nebo Serializovatelné typy musí být převést na kontrakty adaptér segmentů v kanálu.</span><span class="sxs-lookup"><span data-stu-id="11fb1-128">Types that are not contracts or serializable types must be converted to contracts by the adapter segments in the pipeline.</span></span>  
  
 <span data-ttu-id="11fb1-129">Zobrazení segmentů kanálu je abstraktní základní třídy nebo rozhraní, které poskytují hostitele a doplněk zobrazení metody, které sdílejí, podle definice kontraktu.</span><span class="sxs-lookup"><span data-stu-id="11fb1-129">The view segments of the pipeline are abstract base classes or interfaces that provide the host and the add-in with a view of the methods that they share, as defined by the contract.</span></span>  
  
 <span data-ttu-id="11fb1-130">Další informace o vývoji kanálu segmenty najdete v tématu [vývoj kanálu](../../../docs/framework/add-ins/pipeline-development.md).</span><span class="sxs-lookup"><span data-stu-id="11fb1-130">For more information about developing pipeline segments, see [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md).</span></span>  
  
 <span data-ttu-id="11fb1-131">Následující části popisují funkce doplňku modelu.</span><span class="sxs-lookup"><span data-stu-id="11fb1-131">The sections that follow describe the features of the add-in model.</span></span>  
  
### <a name="independent-versioning"></a><span data-ttu-id="11fb1-132">Nezávislé Správa verzí</span><span class="sxs-lookup"><span data-stu-id="11fb1-132">Independent Versioning</span></span>  
 <span data-ttu-id="11fb1-133">Model add-in umožňuje hostitelů a doplňky verzi nezávisle.</span><span class="sxs-lookup"><span data-stu-id="11fb1-133">The add-in model allows hosts and add-ins to version independently.</span></span> <span data-ttu-id="11fb1-134">V důsledku toho model add-in umožňuje následující scénáře:</span><span class="sxs-lookup"><span data-stu-id="11fb1-134">As a result, the add-in model enables the following scenarios:</span></span>  
  
-   <span data-ttu-id="11fb1-135">Vytvoření adaptér, který umožňuje hostitele použít doplněk vytvořené pro předchozí verze hostitele.</span><span class="sxs-lookup"><span data-stu-id="11fb1-135">Creating an adapter that enables a host to use an add-in built for a previous version of the host.</span></span>  
  
-   <span data-ttu-id="11fb1-136">Vytvoření adaptér, který umožňuje hostitele použít doplněk vytvořené pro novější verze hostitele.</span><span class="sxs-lookup"><span data-stu-id="11fb1-136">Creating an adapter that enables a host to use an add-in built for a later version of the host.</span></span>  
  
-   <span data-ttu-id="11fb1-137">Vytváření adaptér, který umožňuje hostitel používat doplňky vytvořené pro jiného hostitele.</span><span class="sxs-lookup"><span data-stu-id="11fb1-137">Creating an adapter that enables a host to use add-ins built for a different host.</span></span>  
  
### <a name="discovery-and-activation"></a><span data-ttu-id="11fb1-138">Zjišťování a aktivace</span><span class="sxs-lookup"><span data-stu-id="11fb1-138">Discovery and Activation</span></span>  
 <span data-ttu-id="11fb1-139">Doplněk, můžete aktivovat pomocí tokenu z kolekce, která představuje doplňků nalezených v úložišti informace.</span><span class="sxs-lookup"><span data-stu-id="11fb1-139">You can activate an add-in by using a token from a collection that represents the add-ins found from an information store.</span></span> <span data-ttu-id="11fb1-140">Doplňky najdete vyhledáním typ, který definuje zobrazení hostitele add-in.</span><span class="sxs-lookup"><span data-stu-id="11fb1-140">Add-ins are found by searching for the type that defines the host's view of the add-in.</span></span> <span data-ttu-id="11fb1-141">Můžete také získat konkrétní doplněk podle typu, který definuje doplněk.</span><span class="sxs-lookup"><span data-stu-id="11fb1-141">You can also find a specific add-in by the type that defines the add-in.</span></span> <span data-ttu-id="11fb1-142">Úložiště informací se skládá ze dvou souborů z mezipaměti: kanálu store a Windows store.</span><span class="sxs-lookup"><span data-stu-id="11fb1-142">The information store consists of two cache files: the pipeline store and the add-in store.</span></span>  
  
 <span data-ttu-id="11fb1-143">Informace o aktualizaci a znovu sestavit úložiště informací najdete v tématu [Add-in zjišťování](http://msdn.microsoft.com/en-us/5d268dde-11df-4c4d-a022-f58d88bbc421).</span><span class="sxs-lookup"><span data-stu-id="11fb1-143">For information about updating and rebuilding the information store, see [Add-in Discovery](http://msdn.microsoft.com/en-us/5d268dde-11df-4c4d-a022-f58d88bbc421).</span></span> <span data-ttu-id="11fb1-144">Informace o aktivaci doplňků najdete v tématu [aktivace Add-in](http://msdn.microsoft.com/en-us/bedcbcdf-5964-4215-b5f3-3299798b2b3f) a [postupy: Aktivace doplňky s jinou izolace a zabezpečení](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="11fb1-144">For information about activating add-ins, see [Add-in Activation](http://msdn.microsoft.com/en-us/bedcbcdf-5964-4215-b5f3-3299798b2b3f) and [How to: Activate Add-ins with Different Isolation and Security](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="isolation-levels-and-external-processes"></a><span data-ttu-id="11fb1-145">Úrovně izolace a externí procesy</span><span class="sxs-lookup"><span data-stu-id="11fb1-145">Isolation Levels and External Processes</span></span>  
 <span data-ttu-id="11fb1-146">Model doplňku podporuje několik úrovní izolace mezi-in a jeho hostitel nebo mezi doplňků. Od nejméně izolované, tyto úrovně jsou následující:</span><span class="sxs-lookup"><span data-stu-id="11fb1-146">The add-in model supports several levels of isolation between an add-in and its host or between add-ins. Starting from the least isolated, these levels are as follows:</span></span>  
  
-   <span data-ttu-id="11fb1-147">Doplněk běží ve stejné doméně aplikace jako hostitel.</span><span class="sxs-lookup"><span data-stu-id="11fb1-147">The add-in runs in the same application domain as the host.</span></span> <span data-ttu-id="11fb1-148">Není doporučeno, protože ztratíte izolace a uvolnění možnosti, které jste získali při použití různých aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="11fb1-148">This is not recommended because you lose the isolation and unloading capabilities that you get when you use different application domains.</span></span>  
  
-   <span data-ttu-id="11fb1-149">Více doplňky jsou načteny do stejné domény aplikace, které se liší od domény aplikace používá hostitel.</span><span class="sxs-lookup"><span data-stu-id="11fb1-149">Multiple add-ins are loaded into the same application domain that is different from the application domain used by the host.</span></span>  
  
-   <span data-ttu-id="11fb1-150">Každý doplněk načíst výhradně do vlastní domény aplikace.</span><span class="sxs-lookup"><span data-stu-id="11fb1-150">Each add-in is loaded exclusively into its own application domain.</span></span> <span data-ttu-id="11fb1-151">Toto je nejběžnější úroveň izolace.</span><span class="sxs-lookup"><span data-stu-id="11fb1-151">This is the most common level of isolation.</span></span>  
  
-   <span data-ttu-id="11fb1-152">Více doplňky jsou načteny do stejné domény aplikace v externím procesu.</span><span class="sxs-lookup"><span data-stu-id="11fb1-152">Multiple add-ins are loaded into the same application domain in an external process.</span></span>  
  
-   <span data-ttu-id="11fb1-153">Každý doplněk načíst výhradně do vlastní domény aplikace v externím procesu.</span><span class="sxs-lookup"><span data-stu-id="11fb1-153">Each add-in is loaded exclusively into its own application domain in an external process.</span></span> <span data-ttu-id="11fb1-154">Toto je nejvíce izolované scénář.</span><span class="sxs-lookup"><span data-stu-id="11fb1-154">This is the most isolated scenario.</span></span>  
  
 <span data-ttu-id="11fb1-155">Další informace o použití externí procesů najdete v tématu [postupy: Aktivace doplňky s jinou izolace a zabezpečení](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="11fb1-155">For more information about using external processes, see [How to: Activate Add-ins with Different Isolation and Security](http://msdn.microsoft.com/en-us/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="lifetime-management"></a><span data-ttu-id="11fb1-156">Správa po dobu platnosti</span><span class="sxs-lookup"><span data-stu-id="11fb1-156">Lifetime Management</span></span>  
 <span data-ttu-id="11fb1-157">Vzhledem k tomu, že model doplňku zahrnuje aplikace domény a proces hranice, uvolňování paměti sám o sobě není dostatečná pro verzi a uvolnění objektů.</span><span class="sxs-lookup"><span data-stu-id="11fb1-157">Because the add-in model spans application domain and process boundaries, garbage collection by itself is not sufficient to release and reclaim objects.</span></span> <span data-ttu-id="11fb1-158">Model doplňku poskytuje mechanismus správy životního cyklu, který používá tokeny a počítání odkazů a obvykle nevyžaduje další programování.</span><span class="sxs-lookup"><span data-stu-id="11fb1-158">The add-in model provides a lifetime management mechanism that uses tokens and reference counting, and usually does not require additional programming.</span></span> <span data-ttu-id="11fb1-159">Další informace najdete v tématu [správu životního cyklu](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="11fb1-159">For more information, see [Lifetime Management](http://msdn.microsoft.com/en-us/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
 [<span data-ttu-id="11fb1-160">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="11fb1-160">Back to top</span></span>](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a><span data-ttu-id="11fb1-161">Rozlišit doplňky a hostitele</span><span class="sxs-lookup"><span data-stu-id="11fb1-161">Distinguishing Between Add-ins and Hosts</span></span>  
 <span data-ttu-id="11fb1-162">Rozdíl mezi-v a hostitele je jenom hostitel je ten, který aktivuje v doplňku.</span><span class="sxs-lookup"><span data-stu-id="11fb1-162">The difference between an add-in and a host is merely that the host is the one that activates the add-in.</span></span> <span data-ttu-id="11fb1-163">Hostiteli může být větší dvou, jako je například aplikace word zpracování a jeho programy pro kontrolu pravopisu; nebo hostitele může být menší ze dvou, jako je například klienta rychlého zasílání zpráv, který se vloží přehrávač médií.</span><span class="sxs-lookup"><span data-stu-id="11fb1-163">The host can be the larger of the two, such as a word processing application and its spell checkers; or the host can be the smaller of the two, such as an instant messaging client that embeds a media player.</span></span> <span data-ttu-id="11fb1-164">Model doplňku podporuje doplňky ve scénářích klient i server.</span><span class="sxs-lookup"><span data-stu-id="11fb1-164">The add-in model supports add-ins in both client and server scenarios.</span></span> <span data-ttu-id="11fb1-165">Příklady doplňky serveru zahrnují doplňky, které poskytují poštovních serverů s vyhledáváním virů, filtry nevyžádané pošty a ochranu IP.</span><span class="sxs-lookup"><span data-stu-id="11fb1-165">Examples of server add-ins include add-ins that provide mail servers with virus scanning, spam filters, and IP protection.</span></span> <span data-ttu-id="11fb1-166">Klient doplňku příklady zahrnují doplňky odkaz pro textové editory, specializované funkce grafických aplikací a her a viry pro místní e-mailových klientů.</span><span class="sxs-lookup"><span data-stu-id="11fb1-166">Client add-in examples include reference add-ins for word processors, specialized features for graphics programs and games, and virus scanning for local e-mail clients.</span></span>  
  
 [<span data-ttu-id="11fb1-167">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="11fb1-167">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="11fb1-168">Související témata</span><span class="sxs-lookup"><span data-stu-id="11fb1-168">Related Topics</span></span>  
  
|<span data-ttu-id="11fb1-169">Název</span><span class="sxs-lookup"><span data-stu-id="11fb1-169">Title</span></span>|<span data-ttu-id="11fb1-170">Popis</span><span class="sxs-lookup"><span data-stu-id="11fb1-170">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="11fb1-171">Vývoj kanálu</span><span class="sxs-lookup"><span data-stu-id="11fb1-171">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)|<span data-ttu-id="11fb1-172">Popisuje komunikační kanál segmentů z hostitelskou aplikaci pro doplněk.</span><span class="sxs-lookup"><span data-stu-id="11fb1-172">Describes the communication pipeline of segments from the host application to the add-in.</span></span> <span data-ttu-id="11fb1-173">Obsahuje příklady kódu v tématech návod, které popisují, jak k vytvoření kanálu a postup nasazení segmenty na kanál v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="11fb1-173">Provides code examples in walkthrough topics that describe how to construct the pipeline and how to deploy segments to the pipeline in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span>|  
|[<span data-ttu-id="11fb1-174">Domény a sestavení aplikací</span><span class="sxs-lookup"><span data-stu-id="11fb1-174">Application Domains and Assemblies</span></span>](http://msdn.microsoft.com/en-us/433b04ae-4ba8-4849-9dbd-79194f240346)|<span data-ttu-id="11fb1-175">Popisuje vztah mezi doménami aplikací, které poskytují hranici izolace zabezpečení, spolehlivosti a správa verzí a sestavení.</span><span class="sxs-lookup"><span data-stu-id="11fb1-175">Describes the relationship between application domains, which provide an isolation boundary for security, reliability, and versioning, and assemblies.</span></span>|  
  
 [<span data-ttu-id="11fb1-176">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="11fb1-176">Back to top</span></span>](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a><span data-ttu-id="11fb1-177">Odkaz</span><span class="sxs-lookup"><span data-stu-id="11fb1-177">Reference</span></span>  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [<span data-ttu-id="11fb1-178">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="11fb1-178">Back to top</span></span>](#top)