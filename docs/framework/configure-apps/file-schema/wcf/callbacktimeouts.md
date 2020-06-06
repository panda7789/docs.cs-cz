---
title: <callbackTimeouts>
ms.date: 03/30/2017
ms.assetid: d7fcfc5f-6d35-491e-8fa6-2f964c1e792f
ms.openlocfilehash: e1b40718638ded54e59743730159ea6e65a51a57
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398188"
---
# \<callbackTimeouts>
<span data-ttu-id="8f0f3-101">Určuje hodnotu časového limitu při toku transakcí ze serveru tak, aby client.in scénář kontraktu pro oboustranný zpětný pokus.</span><span class="sxs-lookup"><span data-stu-id="8f0f3-101">Specifies the timeout value when flowing transactions from server to client.in a duplex callback contract scenario.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<callbackTimeOuts>**  
  
## <a name="syntax"></a><span data-ttu-id="8f0f3-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8f0f3-102">Syntax</span></span>  
  
```xml  
<callbackTimeOuts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="8f0f3-103">Typ</span><span class="sxs-lookup"><span data-stu-id="8f0f3-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8f0f3-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8f0f3-104">Attributes and Elements</span></span>  
 <span data-ttu-id="8f0f3-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8f0f3-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8f0f3-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="8f0f3-106">Attributes</span></span>  
  
|<span data-ttu-id="8f0f3-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="8f0f3-107">Attribute</span></span>|<span data-ttu-id="8f0f3-108">Popis</span><span class="sxs-lookup"><span data-stu-id="8f0f3-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="8f0f3-109"><xref:System.TimeSpan>Hodnota, která určuje časový interval, ve kterém musí být transakce dokončeny nebo automaticky ukončeny.</span><span class="sxs-lookup"><span data-stu-id="8f0f3-109">A <xref:System.TimeSpan> value that specifies the interval of time within which transactions must complete or be automatically terminated.</span></span> <span data-ttu-id="8f0f3-110">Výchozí hodnota je "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="8f0f3-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8f0f3-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8f0f3-111">Child Elements</span></span>  
 <span data-ttu-id="8f0f3-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="8f0f3-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8f0f3-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8f0f3-113">Parent Elements</span></span>  
  
|<span data-ttu-id="8f0f3-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="8f0f3-114">Element</span></span>|<span data-ttu-id="8f0f3-115">Description</span><span class="sxs-lookup"><span data-stu-id="8f0f3-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="8f0f3-116">Určuje chování koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="8f0f3-116">Specifies an endpoint behavior.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8f0f3-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="8f0f3-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.CallbackTimeoutsElement>
