---
title: <routing> z <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0998f4fc61de7099879ba6e122eed1e64588baec
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397736"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="4fe4b-102">\<> směrování > \<ServiceBehavior</span><span class="sxs-lookup"><span data-stu-id="4fe4b-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="4fe4b-103">Poskytuje přístup ke směrovací službě za běhu, aby umožňoval dynamickou úpravu konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="4fe4b-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
<span data-ttu-id="4fe4b-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="4fe4b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="4fe4b-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="4fe4b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="4fe4b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4fe4b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="4fe4b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4fe4b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="4fe4b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="4fe4b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="4fe4b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> směrování**</span><span class="sxs-lookup"><span data-stu-id="4fe4b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4fe4b-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4fe4b-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4fe4b-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4fe4b-111">Attributes and Elements</span></span>  
 <span data-ttu-id="4fe4b-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4fe4b-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4fe4b-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="4fe4b-113">Attributes</span></span>  
  
|<span data-ttu-id="4fe4b-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="4fe4b-114">Attribute</span></span>|<span data-ttu-id="4fe4b-115">Popis</span><span class="sxs-lookup"><span data-stu-id="4fe4b-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4fe4b-116">filterTable</span><span class="sxs-lookup"><span data-stu-id="4fe4b-116">filterTable</span></span>|<span data-ttu-id="4fe4b-117">Řetězec, který určuje název směrovací tabulky obsahující filtry, které mají být vyhodnoceny směrovací službou.</span><span class="sxs-lookup"><span data-stu-id="4fe4b-117">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="4fe4b-118">Tato hodnota musí odpovídat `name` atributu [ \<> elementu](filtertable.md) [ \<](filtertables.md) Filter v oddílu > filterTables.</span><span class="sxs-lookup"><span data-stu-id="4fe4b-118">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="4fe4b-119">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="4fe4b-119">routeOnHeaderOnly</span></span>|<span data-ttu-id="4fe4b-120">Logická hodnota určující, zda filtr prohlíží text zprávy i záhlaví, nebo pouze záhlaví.</span><span class="sxs-lookup"><span data-stu-id="4fe4b-120">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="4fe4b-121">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="4fe4b-121">The default is `true`.</span></span>|  
|<span data-ttu-id="4fe4b-122">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="4fe4b-122">soapProcessingEnabled</span></span>|<span data-ttu-id="4fe4b-123">Logická hodnota, která určuje, zda by mělo dojít ke zpracování protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4fe4b-123">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4fe4b-124">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4fe4b-124">Child Elements</span></span>  
 <span data-ttu-id="4fe4b-125">Žádné</span><span class="sxs-lookup"><span data-stu-id="4fe4b-125">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4fe4b-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4fe4b-126">Parent Elements</span></span>  
  
|<span data-ttu-id="4fe4b-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="4fe4b-127">Element</span></span>|<span data-ttu-id="4fe4b-128">Popis</span><span class="sxs-lookup"><span data-stu-id="4fe4b-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4fe4b-129">\<> chování</span><span class="sxs-lookup"><span data-stu-id="4fe4b-129">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="4fe4b-130">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="4fe4b-130">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4fe4b-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4fe4b-131">Remarks</span></span>  
 <span data-ttu-id="4fe4b-132">Po přidání do konfigurace chování služby tento prvek konfigurace povolí směrování pro službu.</span><span class="sxs-lookup"><span data-stu-id="4fe4b-132">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="4fe4b-133">Můžete zadat vlastní směrovací tabulku, kterou bude služba používat v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="4fe4b-133">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="4fe4b-134">Pomocí této části konfigurace můžete při změně vzoru nasazení změnit nastavení směrování průběžně.</span><span class="sxs-lookup"><span data-stu-id="4fe4b-134">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="4fe4b-135">Za běhu můžete zaregistrovat vlastní směrovací rozšíření s novým nastavením směrování a služba Směrování začne používat aktualizované informace o konfiguraci pro nové zprávy a relace a zároveň může ponechává zprávy a relace v letadlech pomocí jakýchkoli pravidel. umístit při spuštění.</span><span class="sxs-lookup"><span data-stu-id="4fe4b-135">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="4fe4b-136">Díky tomu je možné v době běhu provádět v rámci služby směrování v relaci, recyklicky méně opakovanou konfiguraci směrovací služby.</span><span class="sxs-lookup"><span data-stu-id="4fe4b-136">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
