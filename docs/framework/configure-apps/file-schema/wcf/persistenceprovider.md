---
title: <persistenceProvider>
ms.date: 03/30/2017
ms.assetid: a37049c5-a7ea-4519-94f2-912eeb010380
ms.openlocfilehash: 7c4d9ae29ca1e543217d444e05a661b48e2cbb62
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400067"
---
# \<persistenceProvider>
<span data-ttu-id="81bef-101">Určuje typ používané implementace poskytovatele trvalosti a také časový limit pro operace trvalého uložení.</span><span class="sxs-lookup"><span data-stu-id="81bef-101">Specifies the type of the persistence provider implementation to use, as well as the time-out to use for persistence operations.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<persistenceProvider>**  
  
## <a name="syntax"></a><span data-ttu-id="81bef-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="81bef-102">Syntax</span></span>  
  
```xml  
<persistenceProvider persistenceOperationTimeout="TimeSpan"
                     type="String" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="81bef-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="81bef-103">Attributes and Elements</span></span>  
 <span data-ttu-id="81bef-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="81bef-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="81bef-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="81bef-105">Attributes</span></span>  
  
|<span data-ttu-id="81bef-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="81bef-106">Attribute</span></span>|<span data-ttu-id="81bef-107">Popis</span><span class="sxs-lookup"><span data-stu-id="81bef-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="81bef-108">persistenceOperationTimeout</span><span class="sxs-lookup"><span data-stu-id="81bef-108">persistenceOperationTimeout</span></span>|<span data-ttu-id="81bef-109"><xref:System.TimeSpan>Hodnota, která určuje časový limit, který se používá pro operace trvalosti.</span><span class="sxs-lookup"><span data-stu-id="81bef-109">A <xref:System.TimeSpan> value that specifies the time-out used for persistence operations.</span></span> <span data-ttu-id="81bef-110">Výchozí hodnota je "00:00:30".</span><span class="sxs-lookup"><span data-stu-id="81bef-110">The default is "00:00:30".</span></span>|  
|<span data-ttu-id="81bef-111">typ</span><span class="sxs-lookup"><span data-stu-id="81bef-111">type</span></span>|<span data-ttu-id="81bef-112">Řetězec, který určuje typ továrny poskytovatele trvalosti, který se má použít.</span><span class="sxs-lookup"><span data-stu-id="81bef-112">A string that specifies the type of the persistence provider factory to use.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="81bef-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="81bef-113">Child Elements</span></span>  
 <span data-ttu-id="81bef-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="81bef-114">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="81bef-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="81bef-115">Parent Elements</span></span>  
  
|<span data-ttu-id="81bef-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="81bef-116">Element</span></span>|<span data-ttu-id="81bef-117">Description</span><span class="sxs-lookup"><span data-stu-id="81bef-117">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="81bef-118">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="81bef-118">Specifies a behavior element.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="81bef-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81bef-119">Remarks</span></span>  
 <span data-ttu-id="81bef-120">Tento prvek určuje poskytovatele trvalosti, který se použije k serializaci stavu služby WCF.</span><span class="sxs-lookup"><span data-stu-id="81bef-120">This element specifies the persistence provider to be used to serialize the state of a WCF service.</span></span> <span data-ttu-id="81bef-121">Měl by se používat společně s tím, `wsHttpContextBinding` který předává informace o stavu v hlavičkách protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="81bef-121">It should be used together with the `wsHttpContextBinding` which passes state information in HTTP headers.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81bef-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="81bef-122">See also</span></span>

- <xref:System.ServiceModel.Configuration.PersistenceProviderElement>
- <xref:System.ServiceModel.Persistence.PersistenceProvider>
