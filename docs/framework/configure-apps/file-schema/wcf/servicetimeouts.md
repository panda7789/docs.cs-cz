---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 801a7aaf1f0d0fa267fa8cca3d2e7fd02919c475
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399551"
---
# <a name="servicetimeouts"></a><span data-ttu-id="bfcea-101">\<serviceTimeouts ></span><span class="sxs-lookup"><span data-stu-id="bfcea-101">\<serviceTimeouts></span></span>
<span data-ttu-id="bfcea-102">Určuje časový limit služby.</span><span class="sxs-lookup"><span data-stu-id="bfcea-102">Specifies the timeout for a service.</span></span>  
  
<span data-ttu-id="bfcea-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bfcea-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bfcea-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="bfcea-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="bfcea-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bfcea-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="bfcea-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bfcea-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="bfcea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="bfcea-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="bfcea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceTimeouts >**</span><span class="sxs-lookup"><span data-stu-id="bfcea-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bfcea-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bfcea-109">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="bfcea-110">type</span><span class="sxs-lookup"><span data-stu-id="bfcea-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bfcea-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bfcea-111">Attributes and Elements</span></span>  
 <span data-ttu-id="bfcea-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bfcea-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bfcea-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="bfcea-113">Attributes</span></span>  
  
|<span data-ttu-id="bfcea-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="bfcea-114">Attribute</span></span>|<span data-ttu-id="bfcea-115">Popis</span><span class="sxs-lookup"><span data-stu-id="bfcea-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="bfcea-116"><xref:System.TimeSpan> Hodnota, která určuje časový interval, po který musí transakce z klienta na server přesměrovat.</span><span class="sxs-lookup"><span data-stu-id="bfcea-116">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="bfcea-117">Výchozí hodnota je "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="bfcea-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bfcea-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bfcea-118">Child Elements</span></span>  
 <span data-ttu-id="bfcea-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="bfcea-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bfcea-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bfcea-120">Parent Elements</span></span>  
  
|<span data-ttu-id="bfcea-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="bfcea-121">Element</span></span>|<span data-ttu-id="bfcea-122">Popis</span><span class="sxs-lookup"><span data-stu-id="bfcea-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bfcea-123">\<> chování</span><span class="sxs-lookup"><span data-stu-id="bfcea-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="bfcea-124">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="bfcea-124">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bfcea-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bfcea-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
