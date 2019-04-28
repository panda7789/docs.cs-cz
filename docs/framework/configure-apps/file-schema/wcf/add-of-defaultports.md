---
title: <add> z <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: 5200c8893a89488b72c2c71d1a3703bf2aad1235
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704554"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="cdd16-102">\<Přidat > z \<defaultPorts ></span><span class="sxs-lookup"><span data-stu-id="cdd16-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="cdd16-103">Výchozí koncový bod komunikace, na kterém naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="cdd16-103">A default communications endpoint that the client application listens to.</span></span>  
  
 <span data-ttu-id="cdd16-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cdd16-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cdd16-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="cdd16-105">\<behaviors></span></span>  
<span data-ttu-id="cdd16-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="cdd16-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="cdd16-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="cdd16-107">\<behavior></span></span>  
<span data-ttu-id="cdd16-108">\<useRequestHeadersForMetadataAddress></span><span class="sxs-lookup"><span data-stu-id="cdd16-108">\<useRequestHeadersForMetadataAddress></span></span>  
<span data-ttu-id="cdd16-109">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="cdd16-109">\<defaultPorts></span></span>  
<span data-ttu-id="cdd16-110">\<add></span><span class="sxs-lookup"><span data-stu-id="cdd16-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cdd16-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cdd16-111">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cdd16-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cdd16-112">Attributes and Elements</span></span>  
 <span data-ttu-id="cdd16-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cdd16-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cdd16-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="cdd16-114">Attributes</span></span>  
  
|<span data-ttu-id="cdd16-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="cdd16-115">Attribute</span></span>|<span data-ttu-id="cdd16-116">Popis</span><span class="sxs-lookup"><span data-stu-id="cdd16-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cdd16-117">port</span><span class="sxs-lookup"><span data-stu-id="cdd16-117">port</span></span>|<span data-ttu-id="cdd16-118">Celé číslo, které určuje výchozí číslo komunikačního portu</span><span class="sxs-lookup"><span data-stu-id="cdd16-118">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="cdd16-119">scheme</span><span class="sxs-lookup"><span data-stu-id="cdd16-119">scheme</span></span>|<span data-ttu-id="cdd16-120">Řetězec, který určuje skupinu nastavení protokolu přidružené komunikaci portu.</span><span class="sxs-lookup"><span data-stu-id="cdd16-120">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cdd16-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cdd16-121">Child Elements</span></span>  
 <span data-ttu-id="cdd16-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="cdd16-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cdd16-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cdd16-123">Parent Elements</span></span>  
  
|<span data-ttu-id="cdd16-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="cdd16-124">Element</span></span>|<span data-ttu-id="cdd16-125">Popis</span><span class="sxs-lookup"><span data-stu-id="cdd16-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cdd16-126">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="cdd16-126">\<defaultPorts></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/defaultports.md)|<span data-ttu-id="cdd16-127">Kolekce výchozích portů obsahující seznam výchozích komunikačních koncových bodů, které naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="cdd16-127">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cdd16-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdd16-128">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
