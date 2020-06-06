---
title: <routing> z <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0998f4fc61de7099879ba6e122eed1e64588baec
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397736"
---
# <a name="routing-of-servicebehavior"></a><span data-ttu-id="2c9f3-102">\<routing> z \<serviceBehavior></span><span class="sxs-lookup"><span data-stu-id="2c9f3-102">\<routing> of \<serviceBehavior></span></span>
<span data-ttu-id="2c9f3-103">Poskytuje přístup ke směrovací službě za běhu, aby umožňoval dynamickou úpravu konfigurace směrování.</span><span class="sxs-lookup"><span data-stu-id="2c9f3-103">Provides run-time access to the routing service to allow dynamic modification of the routing configuration.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<routing>**  
  
## <a name="syntax"></a><span data-ttu-id="2c9f3-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c9f3-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c9f3-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2c9f3-105">Attributes and Elements</span></span>  
 <span data-ttu-id="2c9f3-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2c9f3-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c9f3-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="2c9f3-107">Attributes</span></span>  
  
|<span data-ttu-id="2c9f3-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="2c9f3-108">Attribute</span></span>|<span data-ttu-id="2c9f3-109">Popis</span><span class="sxs-lookup"><span data-stu-id="2c9f3-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c9f3-110">filterTable</span><span class="sxs-lookup"><span data-stu-id="2c9f3-110">filterTable</span></span>|<span data-ttu-id="2c9f3-111">Řetězec, který určuje název směrovací tabulky obsahující filtry, které mají být vyhodnoceny směrovací službou.</span><span class="sxs-lookup"><span data-stu-id="2c9f3-111">A string that specifies the name of the routing table that contains filters to be evaluated by the routing service.</span></span> <span data-ttu-id="2c9f3-112">Tato hodnota musí odpovídat `name` atributu [\<filterTable>](filtertable.md) elementu v [\<filterTables>](filtertables.md) oddílu.</span><span class="sxs-lookup"><span data-stu-id="2c9f3-112">This value must match the `name` attribute of a [\<filterTable>](filtertable.md) element in the [\<filterTables>](filtertables.md) section.</span></span>|  
|<span data-ttu-id="2c9f3-113">routeOnHeaderOnly</span><span class="sxs-lookup"><span data-stu-id="2c9f3-113">routeOnHeaderOnly</span></span>|<span data-ttu-id="2c9f3-114">Logická hodnota určující, zda filtr prohlíží text zprávy i záhlaví, nebo pouze záhlaví.</span><span class="sxs-lookup"><span data-stu-id="2c9f3-114">A Boolean value that specifies whether the filter will examine both the message body and the header, or the header only.</span></span> <span data-ttu-id="2c9f3-115">Výchozí formát je `true`.</span><span class="sxs-lookup"><span data-stu-id="2c9f3-115">The default is `true`.</span></span>|  
|<span data-ttu-id="2c9f3-116">soapProcessingEnabled</span><span class="sxs-lookup"><span data-stu-id="2c9f3-116">soapProcessingEnabled</span></span>|<span data-ttu-id="2c9f3-117">Logická hodnota, která určuje, zda by mělo dojít ke zpracování protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="2c9f3-117">A Boolean value that specifies whether SOAP processing should occur.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c9f3-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2c9f3-118">Child Elements</span></span>  
 <span data-ttu-id="2c9f3-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="2c9f3-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c9f3-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2c9f3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2c9f3-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="2c9f3-121">Element</span></span>|<span data-ttu-id="2c9f3-122">Description</span><span class="sxs-lookup"><span data-stu-id="2c9f3-122">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="2c9f3-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="2c9f3-123">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c9f3-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c9f3-124">Remarks</span></span>  
 <span data-ttu-id="2c9f3-125">Po přidání do konfigurace chování služby tento prvek konfigurace povolí směrování pro službu.</span><span class="sxs-lookup"><span data-stu-id="2c9f3-125">When added to the service’s behavior configuration, this configuration element enables routing for the service.</span></span> <span data-ttu-id="2c9f3-126">Můžete zadat vlastní směrovací tabulku, kterou bude služba používat v tomto elementu.</span><span class="sxs-lookup"><span data-stu-id="2c9f3-126">You can specify the actual routing table to be used by the service in this element.</span></span>  
  
 <span data-ttu-id="2c9f3-127">Pomocí této části konfigurace můžete při změně vzoru nasazení změnit nastavení směrování průběžně.</span><span class="sxs-lookup"><span data-stu-id="2c9f3-127">Using this configuration section, you can change your routing settings on the fly when your deployment pattern changes.</span></span> <span data-ttu-id="2c9f3-128">Za běhu můžete zaregistrovat vlastní směrovací rozšíření s novým nastavením směrování a služba Směrování začne používat aktualizované informace o konfiguraci pro nové zprávy a relace a zároveň zanechává zprávy a relace v letadle pomocí pravidel, která byla zahájena.</span><span class="sxs-lookup"><span data-stu-id="2c9f3-128">At runtime, you can register your own routing extension with new routing settings and the routing service will begin using the updated configuration information for new messages and sessions, while leaving in-flight messages/sessions using whatever rules were in place when they started.</span></span>  <span data-ttu-id="2c9f3-129">Díky tomu je možné v době běhu provádět v rámci služby směrování v relaci, recyklicky méně opakovanou konfiguraci směrovací služby.</span><span class="sxs-lookup"><span data-stu-id="2c9f3-129">This gives you the ability to do session-safe, recycle-less reconfiguration of the Routing Service during runtime.</span></span>  
