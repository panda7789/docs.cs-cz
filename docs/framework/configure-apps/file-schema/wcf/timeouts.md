---
title: <timeOuts>
ms.date: 03/30/2017
ms.assetid: 7fccd436-b326-48ec-8de1-c16817a09e0d
ms.openlocfilehash: 8a8a352380fe6eedb41ead089405e7b79fad29fe
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55272771"
---
# <a name="timeouts"></a><span data-ttu-id="e6673-101">\<vypršení časových limitů ></span><span class="sxs-lookup"><span data-stu-id="e6673-101">\<timeOuts></span></span>
<span data-ttu-id="e6673-102">Představuje prvek konfigurace, který určuje dobu hostitel služby otevřít nebo zavřít.</span><span class="sxs-lookup"><span data-stu-id="e6673-102">Represents a configuration element that specifies the interval of time allowed for the service host to open or close.</span></span>  
  
 <span data-ttu-id="e6673-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="e6673-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="e6673-104">\<client></span><span class="sxs-lookup"><span data-stu-id="e6673-104">\<client></span></span>  
<span data-ttu-id="e6673-105">\<endpoint></span><span class="sxs-lookup"><span data-stu-id="e6673-105">\<endpoint></span></span>  
<span data-ttu-id="e6673-106">\<host></span><span class="sxs-lookup"><span data-stu-id="e6673-106">\<host></span></span>  
<span data-ttu-id="e6673-107">\<vypršení časových limitů ></span><span class="sxs-lookup"><span data-stu-id="e6673-107">\<timeOuts></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6673-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e6673-108">Syntax</span></span>  
  
```xml  
<timeOuts closeTimeout="TimeSpan"
          openTimeout="TimeSpan" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e6673-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e6673-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e6673-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e6673-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e6673-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e6673-111">Attributes</span></span>  
  
|<span data-ttu-id="e6673-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="e6673-112">Attribute</span></span>|<span data-ttu-id="e6673-113">Popis</span><span class="sxs-lookup"><span data-stu-id="e6673-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="e6673-114">A <xref:System.TimeSpan> hodnota, která určuje časový interval povolený pro hostitel služby zavřít.</span><span class="sxs-lookup"><span data-stu-id="e6673-114">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to close.</span></span>|  
|`openTimeout`|<span data-ttu-id="e6673-115">A <xref:System.TimeSpan> hodnota, která určuje časový interval povolený pro hostitel služby otevřít.</span><span class="sxs-lookup"><span data-stu-id="e6673-115">A <xref:System.TimeSpan> value that specifies the interval of time allowed for the service host to open.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e6673-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e6673-116">Child Elements</span></span>  
 <span data-ttu-id="e6673-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="e6673-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e6673-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e6673-118">Parent Elements</span></span>  
  
|<span data-ttu-id="e6673-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="e6673-119">Element</span></span>|<span data-ttu-id="e6673-120">Popis</span><span class="sxs-lookup"><span data-stu-id="e6673-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e6673-121">\<host></span><span class="sxs-lookup"><span data-stu-id="e6673-121">\<host></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/host.md)|<span data-ttu-id="e6673-122">Konfigurace element, který určuje nastavení pro hostitele služby.</span><span class="sxs-lookup"><span data-stu-id="e6673-122">A configuration element that specifies settings for a service host.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e6673-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6673-123">See also</span></span>
- <xref:System.ServiceModel.Configuration.HostElement>
- <xref:System.ServiceModel.ServiceHost>
- [<span data-ttu-id="e6673-124">Hostování</span><span class="sxs-lookup"><span data-stu-id="e6673-124">Hosting</span></span>](../../../../../docs/framework/wcf/feature-details/hosting.md)
