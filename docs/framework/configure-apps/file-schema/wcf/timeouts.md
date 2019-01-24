---
title: '&lt;vypršení časových limitů&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 42f4db1d954834cbfa3c526328cca45443751506
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54629654"
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="7b891-102">&lt;vypršení časových limitů&gt;</span><span class="sxs-lookup"><span data-stu-id="7b891-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="7b891-103">Představuje prvek konfigurace, který určuje dobu hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="7b891-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="7b891-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7b891-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b891-105">\<client></span><span class="sxs-lookup"><span data-stu-id="7b891-105">\<client></span></span>  
<span data-ttu-id="7b891-106">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="7b891-106">\<endpoint></span></span>  
<span data-ttu-id="7b891-107">\<host></span><span class="sxs-lookup"><span data-stu-id="7b891-107">\<host></span></span>  
<span data-ttu-id="7b891-108">\<vypršení časových limitů ></span><span class="sxs-lookup"><span data-stu-id="7b891-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b891-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b891-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b891-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7b891-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7b891-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7b891-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b891-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="7b891-112">Attributes</span></span>  
  
|<span data-ttu-id="7b891-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="7b891-113">Attribute</span></span>|<span data-ttu-id="7b891-114">Popis</span><span class="sxs-lookup"><span data-stu-id="7b891-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="7b891-115">A <xref:System.TimeSpan> hodnota, která určuje časový interval povolený pro hostitel služby zavřít.</span><span class="sxs-lookup"><span data-stu-id="7b891-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="7b891-116">A <xref:System.TimeSpan> hodnota, která určuje časový interval povolený pro hostitel služby otevřít.</span><span class="sxs-lookup"><span data-stu-id="7b891-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b891-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7b891-117">Child Elements</span></span>  
 <span data-ttu-id="7b891-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="7b891-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b891-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7b891-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7b891-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="7b891-120">Element</span></span>|<span data-ttu-id="7b891-121">Popis</span><span class="sxs-lookup"><span data-stu-id="7b891-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b891-122">\<host></span><span class="sxs-lookup"><span data-stu-id="7b891-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="7b891-123">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="7b891-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b891-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7b891-124">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="7b891-125">Hostování</span><span class="sxs-lookup"><span data-stu-id="7b891-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
