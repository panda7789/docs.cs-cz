---
title: Doplňky a rozšíření
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb2485f2ecf0426360dba80d443500a92b5a7af6
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43482220"
---
# <a name="add-ins-and-extensibility"></a><span data-ttu-id="e9b92-102">Doplňky a rozšíření</span><span class="sxs-lookup"><span data-stu-id="e9b92-102">Add-ins and Extensibility</span></span>
<a name="top"></a> <span data-ttu-id="e9b92-103">Doplňky poskytují rozšířené funkce nebo služby pro hostitelskou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e9b92-103">Add-ins provide extended features or services for a host application.</span></span> <span data-ttu-id="e9b92-104">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Poskytuje programovací model, který mohou vývojáři k vývoji doplňky a aktivovat ve své hostitelské aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e9b92-104">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] provides a programming model that developers can use to develop add-ins and activate them in their host application.</span></span> <span data-ttu-id="e9b92-105">Model toho dosahuje tak, že vytváří komunikační kanál mezi hostitelem a doplňku.</span><span class="sxs-lookup"><span data-stu-id="e9b92-105">The model achieves this by constructing a communication pipeline between the host and the add-in.</span></span> <span data-ttu-id="e9b92-106">Model je implementovaný s využitím typy v <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, a <xref:System.AddIn.Contract> obory názvů.</span><span class="sxs-lookup"><span data-stu-id="e9b92-106">The model is implemented by using the types in the <xref:System.AddIn>, <xref:System.AddIn.Hosting>, <xref:System.AddIn.Pipeline>, and <xref:System.AddIn.Contract> namespaces.</span></span>  
  
 <span data-ttu-id="e9b92-107">Tento přehled obsahuje následující části:</span><span class="sxs-lookup"><span data-stu-id="e9b92-107">This overview contains the following sections:</span></span>  
  
-   [<span data-ttu-id="e9b92-108">Přidání modelu</span><span class="sxs-lookup"><span data-stu-id="e9b92-108">Add-in Model</span></span>](#addin_model)  
  
-   [<span data-ttu-id="e9b92-109">Rozlišování mezi moduly a hostiteli</span><span class="sxs-lookup"><span data-stu-id="e9b92-109">Distinguishing Between Add-ins and Hosts</span></span>](#distinguishing_between_addins_and_hosts)  
  
-   [<span data-ttu-id="e9b92-110">Související témata</span><span class="sxs-lookup"><span data-stu-id="e9b92-110">Related Topics</span></span>](#related_topics)  
  
-   [<span data-ttu-id="e9b92-111">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="e9b92-111">Reference</span></span>](#reference)  
  
> [!NOTE]
>  <span data-ttu-id="e9b92-112">Další ukázky kódu a náhledy technologie zákazníka nástrojů můžete najít pro vytváření doplňku kanály na [Managed Extensibility a přidat v rámci webu na webu CodePlex](https://go.microsoft.com/fwlink/?LinkId=121190).</span><span class="sxs-lookup"><span data-stu-id="e9b92-112">You can find additional sample code, and customer technology previews of tools for building add-in pipelines, at the [Managed Extensibility and Add-In Framework site on CodePlex](https://go.microsoft.com/fwlink/?LinkId=121190).</span></span>  
  
<a name="addin_model"></a>   
## <a name="add-in-model"></a><span data-ttu-id="e9b92-113">Přidání modelu</span><span class="sxs-lookup"><span data-stu-id="e9b92-113">Add-in Model</span></span>  
 <span data-ttu-id="e9b92-114">Model doplňku se skládá z řady segmenty, které tvoří doplňku kanálu (označované také jako komunikační kanál), která zodpovídá za veškerou komunikaci mezi doplněk a hostitelem.</span><span class="sxs-lookup"><span data-stu-id="e9b92-114">The add-in model consists of a series of segments that make up the add-in pipeline (also known as the communication pipeline), that is responsible for all communication between the add-in and the host.</span></span> <span data-ttu-id="e9b92-115">Kanál je symetrické komunikační model segmentů, které výměnu dat mezi doplňkem a jeho hostitelem.</span><span class="sxs-lookup"><span data-stu-id="e9b92-115">The pipeline is a symmetrical communication model of segments that exchange data between an add-in and its host.</span></span> <span data-ttu-id="e9b92-116">Vývoj těchto segmentů mezi hostitelem a doplněk poskytuje požadovaných úrovní abstrakce, které podporují správu verzí a izolaci doplňku.</span><span class="sxs-lookup"><span data-stu-id="e9b92-116">Developing these segments between the host and the add-in provides the required layers of abstraction that support versioning and isolation of the add-in.</span></span>  
  
 <span data-ttu-id="e9b92-117">Následující obrázek ukazuje kanál.</span><span class="sxs-lookup"><span data-stu-id="e9b92-117">The following illustration shows the pipeline.</span></span>  
  
 <span data-ttu-id="e9b92-118">![Přidat&#45;v kanálu modelu. ](../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span><span class="sxs-lookup"><span data-stu-id="e9b92-118">![Add&#45;in pipeline model.](../../../docs/framework/add-ins/media/addin1.png "AddIn1")</span></span>  
<span data-ttu-id="e9b92-119">Kanál doplňku</span><span class="sxs-lookup"><span data-stu-id="e9b92-119">Add-in pipeline</span></span>  
  
 <span data-ttu-id="e9b92-120">Sestavení pro tyto segmenty nejsou musí být ve stejné doméně aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9b92-120">The assemblies for these segments are not required to be in the same application domain.</span></span> <span data-ttu-id="e9b92-121">Do své vlastní nové aplikační doméně, do existující domény aplikace nebo dokonce do domény aplikace hostitele můžete načíst doplněk.</span><span class="sxs-lookup"><span data-stu-id="e9b92-121">You can load an add-in into its own new application domain, into an existing application domain, or even into the host's application domain.</span></span> <span data-ttu-id="e9b92-122">Načtení více doplňků do stejné doméně aplikace, která umožňuje doplňky sdílet prostředky a kontext zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e9b92-122">You can load multiple add-ins into the same application domain, which enables the add-ins to share resources and security contexts.</span></span>  
  
 <span data-ttu-id="e9b92-123">V modelu doplňku podporuje a doporučuje, abyste, volitelné hranice mezi hostitelem a doplněk, který se nazývá oddělovací hranice (označované také jako hranice vzdálené komunikace).</span><span class="sxs-lookup"><span data-stu-id="e9b92-123">The add-in model supports, and recommends, an optional boundary between the host and the add-in, which is called the isolation boundary (also known as a remoting boundary).</span></span> <span data-ttu-id="e9b92-124">Toto rozhraní může být hranice domény nebo proces aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9b92-124">This boundary can be an application domain or process boundary.</span></span>  
  
 <span data-ttu-id="e9b92-125">Segment smlouvy uprostřed kanálu se načtou do domény aplikací hostitele a doplněk na aplikační domény.</span><span class="sxs-lookup"><span data-stu-id="e9b92-125">The contract segment in the middle of the pipeline is loaded into both the host's application domain and the add-in's application domain.</span></span> <span data-ttu-id="e9b92-126">Kontrakt definuje virtuální metody, které hostitele a používání doplňku pro výměnu typy mezi sebou.</span><span class="sxs-lookup"><span data-stu-id="e9b92-126">The contract defines the virtual methods that the host and the add-in use to exchange types with each other.</span></span>  
  
 <span data-ttu-id="e9b92-127">Předávání oddělovací hranice, musí být typy kontraktů nebo Serializovatelné typy.</span><span class="sxs-lookup"><span data-stu-id="e9b92-127">To pass through the isolation boundary, types must be either contracts or serializable types.</span></span> <span data-ttu-id="e9b92-128">Typy, které nejsou smluv nebo Serializovatelné typy musí být převeden na smlouvy adaptér segmenty v kanálu.</span><span class="sxs-lookup"><span data-stu-id="e9b92-128">Types that are not contracts or serializable types must be converted to contracts by the adapter segments in the pipeline.</span></span>  
  
 <span data-ttu-id="e9b92-129">Zobrazení segmentů kanálu jsou abstraktní základní třídy nebo rozhraní, které poskytují hostitele a doplňku zobrazení metody, které sdílejí, jak je definováno ve smlouvě.</span><span class="sxs-lookup"><span data-stu-id="e9b92-129">The view segments of the pipeline are abstract base classes or interfaces that provide the host and the add-in with a view of the methods that they share, as defined by the contract.</span></span>  
  
 <span data-ttu-id="e9b92-130">Další informace o vývoji segmenty kanálu najdete v tématu [vývoj kanálu](../../../docs/framework/add-ins/pipeline-development.md).</span><span class="sxs-lookup"><span data-stu-id="e9b92-130">For more information about developing pipeline segments, see [Pipeline Development](../../../docs/framework/add-ins/pipeline-development.md).</span></span>  
  
 <span data-ttu-id="e9b92-131">Následující části popisují funkce modelu doplňku.</span><span class="sxs-lookup"><span data-stu-id="e9b92-131">The sections that follow describe the features of the add-in model.</span></span>  
  
### <a name="independent-versioning"></a><span data-ttu-id="e9b92-132">Nezávislé správy verzí</span><span class="sxs-lookup"><span data-stu-id="e9b92-132">Independent Versioning</span></span>  
 <span data-ttu-id="e9b92-133">Model doplňku umožňuje hostiteli a doplňky na verzi nezávisle na sobě.</span><span class="sxs-lookup"><span data-stu-id="e9b92-133">The add-in model allows hosts and add-ins to version independently.</span></span> <span data-ttu-id="e9b92-134">V důsledku toho model doplňku umožňuje následující scénáře:</span><span class="sxs-lookup"><span data-stu-id="e9b92-134">As a result, the add-in model enables the following scenarios:</span></span>  
  
-   <span data-ttu-id="e9b92-135">Vytvoření adaptéru, který umožňuje hostitele doplňku vytvořené pro předchozí verzi hostitele.</span><span class="sxs-lookup"><span data-stu-id="e9b92-135">Creating an adapter that enables a host to use an add-in built for a previous version of the host.</span></span>  
  
-   <span data-ttu-id="e9b92-136">Vytvoření adaptéru, který umožňuje hostitele doplňku vytvořené pro novější verzi hostitele.</span><span class="sxs-lookup"><span data-stu-id="e9b92-136">Creating an adapter that enables a host to use an add-in built for a later version of the host.</span></span>  
  
-   <span data-ttu-id="e9b92-137">Vytvoření adaptéru, který umožňuje hostitele doplňky vytvořené pro jiného hostitele.</span><span class="sxs-lookup"><span data-stu-id="e9b92-137">Creating an adapter that enables a host to use add-ins built for a different host.</span></span>  
  
### <a name="discovery-and-activation"></a><span data-ttu-id="e9b92-138">Zjišťování a aktivace</span><span class="sxs-lookup"><span data-stu-id="e9b92-138">Discovery and Activation</span></span>  
 <span data-ttu-id="e9b92-139">Doplněk můžete aktivovat pomocí tokenu z kolekce, která představuje doplňky od úložiště informace.</span><span class="sxs-lookup"><span data-stu-id="e9b92-139">You can activate an add-in by using a token from a collection that represents the add-ins found from an information store.</span></span> <span data-ttu-id="e9b92-140">Doplňky se nacházejí tak, že typ, který definuje hostitelském zobrazení doplňku.</span><span class="sxs-lookup"><span data-stu-id="e9b92-140">Add-ins are found by searching for the type that defines the host's view of the add-in.</span></span> <span data-ttu-id="e9b92-141">Můžete také najít konkrétní doplňku podle typu, který definuje doplňku.</span><span class="sxs-lookup"><span data-stu-id="e9b92-141">You can also find a specific add-in by the type that defines the add-in.</span></span> <span data-ttu-id="e9b92-142">Informace o úložišti se skládá ze dvou souborů z mezipaměti: úložiště kanálu a ve storu.</span><span class="sxs-lookup"><span data-stu-id="e9b92-142">The information store consists of two cache files: the pipeline store and the add-in store.</span></span>  
  
 <span data-ttu-id="e9b92-143">Informace o aktualizace a opětovné vytvoření úložiště informací najdete v tématu [doplňky zjišťování](https://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421).</span><span class="sxs-lookup"><span data-stu-id="e9b92-143">For information about updating and rebuilding the information store, see [Add-in Discovery](https://msdn.microsoft.com/library/5d268dde-11df-4c4d-a022-f58d88bbc421).</span></span> <span data-ttu-id="e9b92-144">Informace o aktivaci doplňky, naleznete v tématu [Add-in aktivace](https://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f) a [postupy: Aktivace doplňků s různou úrovní izolace a zabezpečení](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="e9b92-144">For information about activating add-ins, see [Add-in Activation](https://msdn.microsoft.com/library/bedcbcdf-5964-4215-b5f3-3299798b2b3f) and [How to: Activate Add-ins with Different Isolation and Security](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="isolation-levels-and-external-processes"></a><span data-ttu-id="e9b92-145">Úrovně izolace a externí proces</span><span class="sxs-lookup"><span data-stu-id="e9b92-145">Isolation Levels and External Processes</span></span>  
 <span data-ttu-id="e9b92-146">Model doplňku podporuje několik úrovní izolace mezi doplňkem a jeho hostitelem nebo doplňky. Od nejméně izolované, tyto úrovně jsou následující:</span><span class="sxs-lookup"><span data-stu-id="e9b92-146">The add-in model supports several levels of isolation between an add-in and its host or between add-ins. Starting from the least isolated, these levels are as follows:</span></span>  
  
-   <span data-ttu-id="e9b92-147">Doplněk běží ve stejné doméně aplikace jako hostitele.</span><span class="sxs-lookup"><span data-stu-id="e9b92-147">The add-in runs in the same application domain as the host.</span></span> <span data-ttu-id="e9b92-148">To se nedoporučuje, protože ztratíte izolace a uvolnění možnosti, které získáte při použití různých aplikačních doménách.</span><span class="sxs-lookup"><span data-stu-id="e9b92-148">This is not recommended because you lose the isolation and unloading capabilities that you get when you use different application domains.</span></span>  
  
-   <span data-ttu-id="e9b92-149">Více moduly se načítají do stejné domény aplikace, které se liší od aplikační domény, používá hostitel.</span><span class="sxs-lookup"><span data-stu-id="e9b92-149">Multiple add-ins are loaded into the same application domain that is different from the application domain used by the host.</span></span>  
  
-   <span data-ttu-id="e9b92-150">Každý doplněk načten výhradně na vlastní doménu aplikace.</span><span class="sxs-lookup"><span data-stu-id="e9b92-150">Each add-in is loaded exclusively into its own application domain.</span></span> <span data-ttu-id="e9b92-151">Toto je nejběžnější úroveň izolace.</span><span class="sxs-lookup"><span data-stu-id="e9b92-151">This is the most common level of isolation.</span></span>  
  
-   <span data-ttu-id="e9b92-152">Více doplňky jsou načtena do stejné domény aplikace v externím procesu.</span><span class="sxs-lookup"><span data-stu-id="e9b92-152">Multiple add-ins are loaded into the same application domain in an external process.</span></span>  
  
-   <span data-ttu-id="e9b92-153">Každý doplněk načten výhradně na vlastní doméně aplikace v externím procesu.</span><span class="sxs-lookup"><span data-stu-id="e9b92-153">Each add-in is loaded exclusively into its own application domain in an external process.</span></span> <span data-ttu-id="e9b92-154">Toto je nejčastěji izolované scénář.</span><span class="sxs-lookup"><span data-stu-id="e9b92-154">This is the most isolated scenario.</span></span>  
  
 <span data-ttu-id="e9b92-155">Další informace o používání externí proces, naleznete v tématu [postupy: Aktivace doplňků s různou úrovní izolace a zabezpečení](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span><span class="sxs-lookup"><span data-stu-id="e9b92-155">For more information about using external processes, see [How to: Activate Add-ins with Different Isolation and Security](https://msdn.microsoft.com/library/7afe7ec8-5158-4350-9119-5df0ecab8aa5).</span></span>  
  
### <a name="lifetime-management"></a><span data-ttu-id="e9b92-156">Správa po dobu platnosti</span><span class="sxs-lookup"><span data-stu-id="e9b92-156">Lifetime Management</span></span>  
 <span data-ttu-id="e9b92-157">Protože model doplňku přesahuje hranice aplikační domény a proces, uvolňování paměti sám o sobě není dostatečná k vydání verze a uvolnění objektů.</span><span class="sxs-lookup"><span data-stu-id="e9b92-157">Because the add-in model spans application domain and process boundaries, garbage collection by itself is not sufficient to release and reclaim objects.</span></span> <span data-ttu-id="e9b92-158">Model doplňku poskytuje mechanismus správy životního cyklu, které používá tokeny a počítání odkazů a obvykle nevyžaduje další programování.</span><span class="sxs-lookup"><span data-stu-id="e9b92-158">The add-in model provides a lifetime management mechanism that uses tokens and reference counting, and usually does not require additional programming.</span></span> <span data-ttu-id="e9b92-159">Další informace najdete v tématu [Správa životního cyklu](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span><span class="sxs-lookup"><span data-stu-id="e9b92-159">For more information, see [Lifetime Management](https://msdn.microsoft.com/library/57a9c87e-394c-4fef-89f2-aa4223a2aeb5).</span></span>  
  
 [<span data-ttu-id="e9b92-160">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="e9b92-160">Back to top</span></span>](#top)  
  
<a name="distinguishing_between_addins_and_hosts"></a>   
## <a name="distinguishing-between-add-ins-and-hosts"></a><span data-ttu-id="e9b92-161">Rozlišování mezi moduly a hostiteli</span><span class="sxs-lookup"><span data-stu-id="e9b92-161">Distinguishing Between Add-ins and Hosts</span></span>  
 <span data-ttu-id="e9b92-162">Rozdíl mezi doplňkem a hostitelem je pouze, že hostitel je ten, který aktivuje doplněk.</span><span class="sxs-lookup"><span data-stu-id="e9b92-162">The difference between an add-in and a host is merely that the host is the one that activates the add-in.</span></span> <span data-ttu-id="e9b92-163">Hostitel může být větší z nich, jako je zpracování textu aplikace a její pravopisu; nebo může být menší z nich, jako je rychlé klienta zasílání zpráv, který vloží multimediální přehrávač hostitele.</span><span class="sxs-lookup"><span data-stu-id="e9b92-163">The host can be the larger of the two, such as a word processing application and its spell checkers; or the host can be the smaller of the two, such as an instant messaging client that embeds a media player.</span></span> <span data-ttu-id="e9b92-164">Model doplňku podporuje doplňků ve scénářích klienta i serveru.</span><span class="sxs-lookup"><span data-stu-id="e9b92-164">The add-in model supports add-ins in both client and server scenarios.</span></span> <span data-ttu-id="e9b92-165">Doplňky server příklady doplňků, které poskytují poštovních serverů s vyhledávání virů, filtry nevyžádané pošty a ochranu IP.</span><span class="sxs-lookup"><span data-stu-id="e9b92-165">Examples of server add-ins include add-ins that provide mail servers with virus scanning, spam filters, and IP protection.</span></span> <span data-ttu-id="e9b92-166">Klient doplněk mezi příklady patří referenční doplňky textových editorů, specializované funkce grafických aplikací a her a virů pro místní e-mailoví klienti.</span><span class="sxs-lookup"><span data-stu-id="e9b92-166">Client add-in examples include reference add-ins for word processors, specialized features for graphics programs and games, and virus scanning for local email clients.</span></span>  
  
 [<span data-ttu-id="e9b92-167">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="e9b92-167">Back to top</span></span>](#top)  
  
<a name="related_topics"></a>   
## <a name="related-topics"></a><span data-ttu-id="e9b92-168">Související témata</span><span class="sxs-lookup"><span data-stu-id="e9b92-168">Related Topics</span></span>  
  
|<span data-ttu-id="e9b92-169">Název</span><span class="sxs-lookup"><span data-stu-id="e9b92-169">Title</span></span>|<span data-ttu-id="e9b92-170">Popis</span><span class="sxs-lookup"><span data-stu-id="e9b92-170">Description</span></span>|  
|-----------|-----------------|  
|[<span data-ttu-id="e9b92-171">Vývoj kanálu</span><span class="sxs-lookup"><span data-stu-id="e9b92-171">Pipeline Development</span></span>](../../../docs/framework/add-ins/pipeline-development.md)|<span data-ttu-id="e9b92-172">Popisuje komunikační kanál segmenty z hostitelské aplikace doplňku.</span><span class="sxs-lookup"><span data-stu-id="e9b92-172">Describes the communication pipeline of segments from the host application to the add-in.</span></span> <span data-ttu-id="e9b92-173">Poskytuje příklady kódu v návody, které popisují, jak k vytvoření kanálu a jak nasadit segmentů kanálu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="e9b92-173">Provides code examples in walkthrough topics that describe how to construct the pipeline and how to deploy segments to the pipeline in Visual Studio.</span></span>|  
|[<span data-ttu-id="e9b92-174">Domény a sestavení aplikací</span><span class="sxs-lookup"><span data-stu-id="e9b92-174">Application Domains and Assemblies</span></span>](https://msdn.microsoft.com/library/433b04ae-4ba8-4849-9dbd-79194f240346)|<span data-ttu-id="e9b92-175">Popisuje relace mezi doménami aplikace, které poskytují izolační hranici pro zabezpečení, spolehlivosti a správy verzí a sestavení.</span><span class="sxs-lookup"><span data-stu-id="e9b92-175">Describes the relationship between application domains, which provide an isolation boundary for security, reliability, and versioning, and assemblies.</span></span>|  
  
 [<span data-ttu-id="e9b92-176">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="e9b92-176">Back to top</span></span>](#top)  
  
<a name="reference"></a>   
## <a name="reference"></a><span data-ttu-id="e9b92-177">Odkaz</span><span class="sxs-lookup"><span data-stu-id="e9b92-177">Reference</span></span>  
 <xref:System.AddIn?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Contract?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Hosting?displayProperty=nameWithType>  
  
 <xref:System.AddIn.Pipeline?displayProperty=nameWithType>  
  
 [<span data-ttu-id="e9b92-178">Zpět na začátek</span><span class="sxs-lookup"><span data-stu-id="e9b92-178">Back to top</span></span>](#top)