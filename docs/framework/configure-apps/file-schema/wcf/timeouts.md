---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b6ae5faa2dd2ffef9669a0245a75227b0f669cf7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61758220"
---
# <a name="timeouts"></a><span data-ttu-id="2e8dc-101">\<vypršení časových limitů ></span><span class="sxs-lookup"><span data-stu-id="2e8dc-101">\<timeOuts></span></span>
<span data-ttu-id="2e8dc-102">Představuje prvek konfigurace, který určuje dobu hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="2e8dc-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="2e8dc-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2e8dc-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2e8dc-104">\<client></span><span class="sxs-lookup"><span data-stu-id="2e8dc-104">\<client></span></span>  
<span data-ttu-id="2e8dc-105">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="2e8dc-105">\<endpoint></span></span>  
<span data-ttu-id="2e8dc-106">\<host></span><span class="sxs-lookup"><span data-stu-id="2e8dc-106">\<host></span></span>  
<span data-ttu-id="2e8dc-107">\<vypršení časových limitů ></span><span class="sxs-lookup"><span data-stu-id="2e8dc-107">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2e8dc-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2e8dc-108">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2e8dc-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2e8dc-109">Attributes and Elements</span></span>  
 <span data-ttu-id="2e8dc-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2e8dc-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2e8dc-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="2e8dc-111">Attributes</span></span>  
  
|<span data-ttu-id="2e8dc-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="2e8dc-112">Attribute</span></span>|<span data-ttu-id="2e8dc-113">Popis</span><span class="sxs-lookup"><span data-stu-id="2e8dc-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="2e8dc-114">A <xref:System.TimeSpan> hodnota, která určuje časový interval povolený pro hostitel služby zavřít.</span><span class="sxs-lookup"><span data-stu-id="2e8dc-114">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="2e8dc-115">A <xref:System.TimeSpan> hodnota, která určuje časový interval povolený pro hostitel služby otevřít.</span><span class="sxs-lookup"><span data-stu-id="2e8dc-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2e8dc-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2e8dc-116">Child Elements</span></span>  
 <span data-ttu-id="2e8dc-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="2e8dc-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2e8dc-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2e8dc-118">Parent Elements</span></span>  
  
|<span data-ttu-id="2e8dc-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="2e8dc-119">Element</span></span>|<span data-ttu-id="2e8dc-120">Popis</span><span class="sxs-lookup"><span data-stu-id="2e8dc-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2e8dc-121">\<host></span><span class="sxs-lookup"><span data-stu-id="2e8dc-121">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="2e8dc-122">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="2e8dc-122">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2e8dc-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2e8dc-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="2e8dc-124">Hostování</span><span class="sxs-lookup"><span data-stu-id="2e8dc-124">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
