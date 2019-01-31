---
title: <add> z <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 799715ef008274ead6b745e8ab97e769cb59e6b5
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55261592"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="9f41b-102">\<Přidat > z \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="9f41b-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="9f41b-103">Výchozí koncový bod komunikace, na kterém naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f41b-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="9f41b-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9f41b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="9f41b-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9f41b-105">\<behaviors></span></span>  
<span data-ttu-id="9f41b-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="9f41b-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="9f41b-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="9f41b-107">\<behavior></span></span>  
<span data-ttu-id="9f41b-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="9f41b-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="9f41b-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="9f41b-109">\<defaultPorts></span></span>  
<span data-ttu-id="9f41b-110">\<add></span><span class="sxs-lookup"><span data-stu-id="9f41b-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f41b-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f41b-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f41b-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9f41b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="9f41b-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9f41b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f41b-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="9f41b-114">Attributes</span></span>  
  
|<span data-ttu-id="9f41b-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="9f41b-115">Attribute</span></span>|<span data-ttu-id="9f41b-116">Popis</span><span class="sxs-lookup"><span data-stu-id="9f41b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f41b-117">port</span><span class="sxs-lookup"><span data-stu-id="9f41b-117">port</span></span>|<span data-ttu-id="9f41b-118">Celé číslo, které určuje výchozí číslo komunikačního portu</span><span class="sxs-lookup"><span data-stu-id="9f41b-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="9f41b-119">scheme</span><span class="sxs-lookup"><span data-stu-id="9f41b-119">scheme</span></span>|<span data-ttu-id="9f41b-120">Řetězec, který určuje skupinu nastavení protokolu přidružené komunikaci portu.</span><span class="sxs-lookup"><span data-stu-id="9f41b-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f41b-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9f41b-121">Child Elements</span></span>  
 <span data-ttu-id="9f41b-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="9f41b-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f41b-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9f41b-123">Parent Elements</span></span>  
  
|<span data-ttu-id="9f41b-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="9f41b-124">Element</span></span>|<span data-ttu-id="9f41b-125">Popis</span><span class="sxs-lookup"><span data-stu-id="9f41b-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f41b-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="9f41b-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="9f41b-127">Kolekce výchozích portů obsahující seznam výchozích komunikačních koncových bodů, které naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="9f41b-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9f41b-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f41b-128">See also</span></span>
- <xref:System.ServiceModel.Configuration.DefaultPortElement>
