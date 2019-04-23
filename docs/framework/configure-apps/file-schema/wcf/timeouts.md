---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: b6ae5faa2dd2ffef9669a0245a75227b0f669cf7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59118063"
---
# <a name="timeouts"></a><span data-ttu-id="1d688-101">\<vypršení časových limitů ></span><span class="sxs-lookup"><span data-stu-id="1d688-101">\<timeOuts></span></span>
<span data-ttu-id="1d688-102">Představuje prvek konfigurace, který určuje dobu hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="1d688-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="1d688-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="1d688-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="1d688-104">\<client></span><span class="sxs-lookup"><span data-stu-id="1d688-104">\<client></span></span>  
<span data-ttu-id="1d688-105">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="1d688-105">\<endpoint></span></span>  
<span data-ttu-id="1d688-106">\<host></span><span class="sxs-lookup"><span data-stu-id="1d688-106">\<host></span></span>  
<span data-ttu-id="1d688-107">\<vypršení časových limitů ></span><span class="sxs-lookup"><span data-stu-id="1d688-107">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d688-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d688-108">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d688-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1d688-109">Attributes and Elements</span></span>  
 <span data-ttu-id="1d688-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1d688-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d688-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="1d688-111">Attributes</span></span>  
  
|<span data-ttu-id="1d688-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="1d688-112">Attribute</span></span>|<span data-ttu-id="1d688-113">Popis</span><span class="sxs-lookup"><span data-stu-id="1d688-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="1d688-114">A <xref:System.TimeSpan> hodnota, která určuje časový interval povolený pro hostitel služby zavřít.</span><span class="sxs-lookup"><span data-stu-id="1d688-114">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="1d688-115">A <xref:System.TimeSpan> hodnota, která určuje časový interval povolený pro hostitel služby otevřít.</span><span class="sxs-lookup"><span data-stu-id="1d688-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1d688-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1d688-116">Child Elements</span></span>  
 <span data-ttu-id="1d688-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="1d688-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1d688-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1d688-118">Parent Elements</span></span>  
  
|<span data-ttu-id="1d688-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="1d688-119">Element</span></span>|<span data-ttu-id="1d688-120">Popis</span><span class="sxs-lookup"><span data-stu-id="1d688-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d688-121">\<host></span><span class="sxs-lookup"><span data-stu-id="1d688-121">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="1d688-122">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="1d688-122">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1d688-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d688-123">See also</span></span>

- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="1d688-124">Hostování</span><span class="sxs-lookup"><span data-stu-id="1d688-124">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
