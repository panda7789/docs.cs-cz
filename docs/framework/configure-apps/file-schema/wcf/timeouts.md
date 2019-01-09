---
title: '&lt;vypršení časových limitů&gt;'
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: e39deeb251865b87eb7734e4447088ca2f221d1d
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148328"
---
# <a name="lttimeoutsgt"></a><span data-ttu-id="71b2f-102">&lt;vypršení časových limitů&gt;</span><span class="sxs-lookup"><span data-stu-id="71b2f-102">&lt;timeOuts&gt;</span></span>
<span data-ttu-id="71b2f-103">Představuje prvek konfigurace, který určuje dobu hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="71b2f-103">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="71b2f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="71b2f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="71b2f-105">\<klient ></span><span class="sxs-lookup"><span data-stu-id="71b2f-105">\<client></span></span>  
<span data-ttu-id="71b2f-106">\<koncový bod ></span><span class="sxs-lookup"><span data-stu-id="71b2f-106">\<endpoint></span></span>  
<span data-ttu-id="71b2f-107">\<Hostitel ></span><span class="sxs-lookup"><span data-stu-id="71b2f-107">\<host></span></span>  
<span data-ttu-id="71b2f-108">\<vypršení časových limitů ></span><span class="sxs-lookup"><span data-stu-id="71b2f-108">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="71b2f-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="71b2f-109">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="71b2f-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="71b2f-110">Attributes and Elements</span></span>  
 <span data-ttu-id="71b2f-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="71b2f-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="71b2f-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="71b2f-112">Attributes</span></span>  
  
|<span data-ttu-id="71b2f-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="71b2f-113">Attribute</span></span>|<span data-ttu-id="71b2f-114">Popis</span><span class="sxs-lookup"><span data-stu-id="71b2f-114">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="71b2f-115">A <xref:System.TimeSpan> hodnota, která určuje časový interval povolený pro hostitel služby zavřít.</span><span class="sxs-lookup"><span data-stu-id="71b2f-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="71b2f-116">A <xref:System.TimeSpan> hodnota, která určuje časový interval povolený pro hostitel služby otevřít.</span><span class="sxs-lookup"><span data-stu-id="71b2f-116">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="71b2f-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="71b2f-117">Child Elements</span></span>  
 <span data-ttu-id="71b2f-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="71b2f-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="71b2f-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="71b2f-119">Parent Elements</span></span>  
  
|<span data-ttu-id="71b2f-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="71b2f-120">Element</span></span>|<span data-ttu-id="71b2f-121">Popis</span><span class="sxs-lookup"><span data-stu-id="71b2f-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="71b2f-122">\<Hostitel ></span><span class="sxs-lookup"><span data-stu-id="71b2f-122">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="71b2f-123">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="71b2f-123">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="71b2f-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="71b2f-124">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.HostElement>  
 <xref:System.ServiceModel.ServiceHost>  
 [<span data-ttu-id="71b2f-125">Hostování</span><span class="sxs-lookup"><span data-stu-id="71b2f-125">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
