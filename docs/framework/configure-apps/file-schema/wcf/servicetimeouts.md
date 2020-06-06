---
title: <serviceTimeouts>
ms.date: 03/30/2017
ms.assetid: ada536cf-97dc-4cd7-89ec-ed1466c1c557
ms.openlocfilehash: 801a7aaf1f0d0fa267fa8cca3d2e7fd02919c475
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399551"
---
# \<serviceTimeouts>
<span data-ttu-id="7e65e-101">Určuje časový limit služby.</span><span class="sxs-lookup"><span data-stu-id="7e65e-101">Specifies the timeout for a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceTimeouts>**  
  
## <a name="syntax"></a><span data-ttu-id="7e65e-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e65e-102">Syntax</span></span>  
  
```xml  
<serviceTimeouts transactionTimeout="TimeSpan" />
```  
  
## <a name="type"></a><span data-ttu-id="7e65e-103">Typ</span><span class="sxs-lookup"><span data-stu-id="7e65e-103">Type</span></span>  
 `Type`  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e65e-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7e65e-104">Attributes and Elements</span></span>  
 <span data-ttu-id="7e65e-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7e65e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e65e-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="7e65e-106">Attributes</span></span>  
  
|<span data-ttu-id="7e65e-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="7e65e-107">Attribute</span></span>|<span data-ttu-id="7e65e-108">Popis</span><span class="sxs-lookup"><span data-stu-id="7e65e-108">Description</span></span>|  
|---------------|-----------------|  
|`transactionTimeout`|<span data-ttu-id="7e65e-109"><xref:System.TimeSpan>Hodnota, která určuje časový interval, po který musí transakce z klienta na server přesměrovat.</span><span class="sxs-lookup"><span data-stu-id="7e65e-109">A <xref:System.TimeSpan> value that specifies the interval of time a transaction must flow from client to server.</span></span> <span data-ttu-id="7e65e-110">Výchozí hodnota je "00:00:00".</span><span class="sxs-lookup"><span data-stu-id="7e65e-110">The default is "00:00:00".</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e65e-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7e65e-111">Child Elements</span></span>  
 <span data-ttu-id="7e65e-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="7e65e-112">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7e65e-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7e65e-113">Parent Elements</span></span>  
  
|<span data-ttu-id="7e65e-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="7e65e-114">Element</span></span>|<span data-ttu-id="7e65e-115">Description</span><span class="sxs-lookup"><span data-stu-id="7e65e-115">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="7e65e-116">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="7e65e-116">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7e65e-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e65e-117">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
