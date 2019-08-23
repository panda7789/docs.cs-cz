---
title: <routing> z <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 73a610056f94efe144705968eaf97c8314c1ae0d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934188"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="6ce78-102">\<> směrování > \<ServiceBehavior</span><span class="sxs-lookup"><span data-stu-id="6ce78-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="6ce78-103">Poskytuje přístup ke směrovací službě za běhu, aby umožňoval dynamickou úpravu konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="6ce78-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
 <span data-ttu-id="6ce78-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6ce78-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6ce78-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="6ce78-105">\<behaviors></span></span>  
<span data-ttu-id="6ce78-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="6ce78-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="6ce78-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="6ce78-107">\<behavior></span></span>  
<span data-ttu-id="6ce78-108">\<> směrování</span><span class="sxs-lookup"><span data-stu-id="6ce78-108">\<routing></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ce78-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6ce78-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6ce78-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6ce78-110">Attributes and Elements</span></span>  
 <span data-ttu-id="6ce78-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="6ce78-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6ce78-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="6ce78-112">Attributes</span></span>  
  
|<span data-ttu-id="6ce78-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="6ce78-113">Attribute</span></span>|<span data-ttu-id="6ce78-114">Popis</span><span class="sxs-lookup"><span data-stu-id="6ce78-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6ce78-115">filterTable</span><span class="sxs-lookup"><span data-stu-id="6ce78-115">filterTable</span></span>|<span data-ttu-id="6ce78-116">Řetězec, který určuje název směrovací tabulky obsahující filtry, které mají být vyhodnoceny směrovací službou.</span><span class="sxs-lookup"><span data-stu-id="6ce78-116">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="6ce78-117">Tato hodnota musí odpovídat `name` atributu [ \<> elementu](filtertable.md) [ \<](filtertables.md) Filter v oddílu > filterTables.</span><span class="sxs-lookup"><span data-stu-id="6ce78-117">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="6ce78-118">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="6ce78-118">routeOnHeaderOnly</span></span>|<span data-ttu-id="6ce78-119">Logická hodnota určující, zda filtr prohlíží text zprávy i záhlaví, nebo pouze záhlaví.</span><span class="sxs-lookup"><span data-stu-id="6ce78-119">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="6ce78-120">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="6ce78-120">The default is `true`.</span></span>|  
|<span data-ttu-id="6ce78-121">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="6ce78-121">soapProcessingEnabled</span></span>|<span data-ttu-id="6ce78-122">Logická hodnota, která určuje, zda by mělo dojít ke zpracování protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="6ce78-122">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6ce78-123">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6ce78-123">Child Elements</span></span>  
 <span data-ttu-id="6ce78-124">Žádné</span><span class="sxs-lookup"><span data-stu-id="6ce78-124">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6ce78-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6ce78-125">Parent Elements</span></span>  
  
|<span data-ttu-id="6ce78-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="6ce78-126">Element</span></span>|<span data-ttu-id="6ce78-127">Popis</span><span class="sxs-lookup"><span data-stu-id="6ce78-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6ce78-128">\<> chování</span><span class="sxs-lookup"><span data-stu-id="6ce78-128">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="6ce78-129">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="6ce78-129">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6ce78-130">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ce78-130">Remarks</span></span>  
 <span data-ttu-id="6ce78-131">Po přidání do konfigurace chování služby tento prvek konfigurace povolí směrování pro službu.</span><span class="sxs-lookup"><span data-stu-id="6ce78-131">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="6ce78-132">Můžete zadat vlastní směrovací tabulku, kterou bude služba používat v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="6ce78-132">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="6ce78-133">Pomocí této části konfigurace můžete při změně vzoru nasazení změnit nastavení směrování průběžně.</span><span class="sxs-lookup"><span data-stu-id="6ce78-133">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="6ce78-134">Za běhu můžete zaregistrovat vlastní směrovací rozšíření s novým nastavením směrování a služba Směrování začne používat aktualizované informace o konfiguraci pro nové zprávy a relace a zároveň může ponechává zprávy a relace v letadlech pomocí jakýchkoli pravidel. umístit při spuštění.</span><span class="sxs-lookup"><span data-stu-id="6ce78-134">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="6ce78-135">Díky tomu je možné v době běhu provádět v rámci služby směrování v relaci, recyklicky méně opakovanou konfiguraci směrovací služby.</span><span class="sxs-lookup"><span data-stu-id="6ce78-135">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
