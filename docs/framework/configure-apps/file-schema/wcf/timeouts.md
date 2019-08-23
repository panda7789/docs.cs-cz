---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b159488efa2a80a9dea625e4c6dfe2f215dfc457
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69939190"
---
# <a name="timeouts"></a><span data-ttu-id="13b83-101">\<Časové limity ></span><span class="sxs-lookup"><span data-stu-id="13b83-101">\<timeOuts></span></span>
<span data-ttu-id="13b83-102">Představuje prvek konfigurace, který určuje časový interval, po který může hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="13b83-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="13b83-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="13b83-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="13b83-104">\<> klienta</span><span class="sxs-lookup"><span data-stu-id="13b83-104">\<client></span></span>  
<span data-ttu-id="13b83-105">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="13b83-105">\<endpoint></span></span>  
<span data-ttu-id="13b83-106">\<host></span><span class="sxs-lookup"><span data-stu-id="13b83-106">\<host></span></span>  
<span data-ttu-id="13b83-107">\<Časové limity ></span><span class="sxs-lookup"><span data-stu-id="13b83-107">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13b83-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="13b83-108">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="13b83-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="13b83-109">Attributes and Elements</span></span>  
 <span data-ttu-id="13b83-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="13b83-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="13b83-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="13b83-111">Attributes</span></span>  
  
|<span data-ttu-id="13b83-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="13b83-112">Attribute</span></span>|<span data-ttu-id="13b83-113">Popis</span><span class="sxs-lookup"><span data-stu-id="13b83-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="13b83-114"><xref:System.TimeSpan> Hodnota, která určuje časový interval, po který může hostitel služby zavřít.</span><span class="sxs-lookup"><span data-stu-id="13b83-114">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="13b83-115"><xref:System.TimeSpan> Hodnota, která určuje časový interval, po který může hostitel služby otevřít.</span><span class="sxs-lookup"><span data-stu-id="13b83-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="13b83-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="13b83-116">Child Elements</span></span>  
 <span data-ttu-id="13b83-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="13b83-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="13b83-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="13b83-118">Parent Elements</span></span>  
  
|<span data-ttu-id="13b83-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="13b83-119">Element</span></span>|<span data-ttu-id="13b83-120">Popis</span><span class="sxs-lookup"><span data-stu-id="13b83-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="13b83-121">\<host></span><span class="sxs-lookup"><span data-stu-id="13b83-121">\<host></span></span>](host.md)|<span data-ttu-id="13b83-122">Prvek konfigurace, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="13b83-122">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="13b83-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="13b83-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="13b83-124">Hostování</span><span class="sxs-lookup"><span data-stu-id="13b83-124">Hosting</span></span>](../../../wcf/feature-details/hosting.md)
