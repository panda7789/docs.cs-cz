---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e1b40718638ded54e59743730159ea6e65a51a57
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398188"
---
# <a name="callbacktimeouts"></a><span data-ttu-id="980a1-101">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="980a1-101">\<callbackTimeouts></span></span>
<span data-ttu-id="980a1-102">Určuje hodnotu časového limitu při toku transakcí ze serveru tak, aby client.in scénář kontraktu pro oboustranný zpětný pokus.</span><span class="sxs-lookup"><span data-stu-id="980a1-102">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
<span data-ttu-id="980a1-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="980a1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="980a1-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="980a1-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="980a1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="980a1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="980a1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="980a1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="980a1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="980a1-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="980a1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<callbackTimeOuts >**</span><span class="sxs-lookup"><span data-stu-id="980a1-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="980a1-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="980a1-109">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="980a1-110">type</span><span class="sxs-lookup"><span data-stu-id="980a1-110">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="980a1-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="980a1-111">Attributes and Elements</span></span>  
 <span data-ttu-id="980a1-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="980a1-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="980a1-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="980a1-113">Attributes</span></span>  
  
|<span data-ttu-id="980a1-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="980a1-114">Attribute</span></span>|<span data-ttu-id="980a1-115">Popis</span><span class="sxs-lookup"><span data-stu-id="980a1-115">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="980a1-116"><xref:System.TimeSpan> Hodnota, která určuje časový interval, ve kterém musí být transakce dokončeny nebo automaticky ukončeny.</span><span class="sxs-lookup"><span data-stu-id="980a1-116">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="980a1-117">Výchozí hodnota je "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="980a1-117">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="980a1-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="980a1-118">Child Elements</span></span>  
 <span data-ttu-id="980a1-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="980a1-119">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="980a1-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="980a1-120">Parent Elements</span></span>  
  
|<span data-ttu-id="980a1-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="980a1-121">Element</span></span>|<span data-ttu-id="980a1-122">Popis</span><span class="sxs-lookup"><span data-stu-id="980a1-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="980a1-123">\<> chování</span><span class="sxs-lookup"><span data-stu-id="980a1-123">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="980a1-124">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="980a1-124">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="980a1-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="980a1-125">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
