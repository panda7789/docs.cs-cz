---
title: '&lt;routing&gt; – &lt;serviceBehavior&gt;'
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0a007eb33063f8f44098a8c63708255b884b5fdc
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146846"
---
# <a name="ltroutinggt-of-ltservicebehaviorgt"></a><span data-ttu-id="bd8e4-102">&lt;routing&gt; – &lt;serviceBehavior&gt;</span><span class="sxs-lookup"><span data-stu-id="bd8e4-102">&lt;routing&gt; of &lt;serviceBehavior&gt;</span></span>
<span data-ttu-id="bd8e4-103">Poskytuje přístup ke službě Směrování a povolit dynamickou změnu konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="bd8e4-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
 <span data-ttu-id="bd8e4-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="bd8e4-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="bd8e4-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="bd8e4-105">\<behaviors></span></span>  
<span data-ttu-id="bd8e4-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="bd8e4-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="bd8e4-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="bd8e4-107">\<behavior></span></span>  
<span data-ttu-id="bd8e4-108">\<směrování ></span><span class="sxs-lookup"><span data-stu-id="bd8e4-108">\<routing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bd8e4-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bd8e4-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String"
               routeOnHeadersOnly="Boolean"
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bd8e4-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bd8e4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="bd8e4-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bd8e4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bd8e4-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="bd8e4-112">Attributes</span></span>  
  
|<span data-ttu-id="bd8e4-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="bd8e4-113">Attribute</span></span>|<span data-ttu-id="bd8e4-114">Popis</span><span class="sxs-lookup"><span data-stu-id="bd8e4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bd8e4-115">filterTable</span><span class="sxs-lookup"><span data-stu-id="bd8e4-115">filterTable</span></span>|<span data-ttu-id="bd8e4-116">Řetězec určující název směrovací tabulku, která obsahuje filtry, který se má vyhodnotit ve službě Směrování.</span><span class="sxs-lookup"><span data-stu-id="bd8e4-116">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="bd8e4-117">Tato hodnota musí odpovídat `name` atribut [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) prvek [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) části.</span><span class="sxs-lookup"><span data-stu-id="bd8e4-117">This value must match the `name` attribute of a [\<filterTable>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) element in the [\<filterTables>](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) section.</span></span>|  
|<span data-ttu-id="bd8e4-118">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="bd8e4-118">routeOnHeaderOnly</span></span>|<span data-ttu-id="bd8e4-119">Logická hodnota, která určuje, zda bude text zprávy a záhlaví nebo pouze záhlaví prozkoumat filtr.</span><span class="sxs-lookup"><span data-stu-id="bd8e4-119">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="bd8e4-120">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="bd8e4-120">The default is `true`.</span></span>|  
|<span data-ttu-id="bd8e4-121">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="bd8e4-121">soapProcessingEnabled</span></span>|<span data-ttu-id="bd8e4-122">Logická hodnota určující, zda by měla probíhat zpracování SOAP.</span><span class="sxs-lookup"><span data-stu-id="bd8e4-122">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bd8e4-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bd8e4-123">Child Elements</span></span>  
 <span data-ttu-id="bd8e4-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="bd8e4-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bd8e4-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bd8e4-125">Parent Elements</span></span>  
  
|<span data-ttu-id="bd8e4-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="bd8e4-126">Element</span></span>|<span data-ttu-id="bd8e4-127">Popis</span><span class="sxs-lookup"><span data-stu-id="bd8e4-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bd8e4-128">\<chování ></span><span class="sxs-lookup"><span data-stu-id="bd8e4-128">\<behavior></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|<span data-ttu-id="bd8e4-129">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="bd8e4-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bd8e4-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bd8e4-130">Remarks</span></span>  
 <span data-ttu-id="bd8e4-131">Když se přidá do konfigurace chování služby, umožňuje tento prvek konfigurace, směrování pro službu.</span><span class="sxs-lookup"><span data-stu-id="bd8e4-131">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="bd8e4-132">Můžete určit skutečný směrovací tabulky používané služby v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="bd8e4-132">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="bd8e4-133">Používá tento konfigurační oddíl, můžete změnit nastavení směrování v reálném čase při změně vzorek vašeho nasazení.</span><span class="sxs-lookup"><span data-stu-id="bd8e4-133">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="bd8e4-134">Za běhu zaregistrujete vlastní rozšíření směrování s novými nastaveními směrování a služba Směrování se začít používat informace o aktualizovanou konfiguraci pro nové zprávy a relací, ale zároveň je nechává vydávaných za pochodu zpráv/relací pomocí určit jakákoli pravidla byly v místo při jejich spuštění.</span><span class="sxs-lookup"><span data-stu-id="bd8e4-134">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="bd8e4-135">Získáte možnost provádět relace typově bezpečný, recyklace bez změny konfigurace směrování služby za běhu.</span><span class="sxs-lookup"><span data-stu-id="bd8e4-135">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
  
