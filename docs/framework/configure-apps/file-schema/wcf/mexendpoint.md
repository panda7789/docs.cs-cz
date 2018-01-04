---
title: '&lt;mexEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 713c1c260f36d6d980903cce1ebcc9c5648116c2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="49812-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="49812-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="49812-103">Tento element konfigurace definuje standardní koncový bod s pevnou IMetadataExchange kontrakt.</span><span class="sxs-lookup"><span data-stu-id="49812-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="49812-104">Vzhledem k tomu, že všechny koncové body metadat serveru exchange zadejte IMetadataExchange jako jejich kontrakt, můžete použít tento standardní bod místo definování jeden pro sami.</span><span class="sxs-lookup"><span data-stu-id="49812-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="49812-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="49812-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="49812-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="49812-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49812-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="49812-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="49812-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="49812-108">Attributes and Elements</span></span>  
 <span data-ttu-id="49812-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="49812-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="49812-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="49812-110">Attributes</span></span>  
  
|<span data-ttu-id="49812-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="49812-111">Attribute</span></span>|<span data-ttu-id="49812-112">Popis</span><span class="sxs-lookup"><span data-stu-id="49812-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="49812-113">name</span><span class="sxs-lookup"><span data-stu-id="49812-113">name</span></span>|<span data-ttu-id="49812-114">Řetězec, který určuje název konfigurace standardní koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="49812-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="49812-115">Název je používán `endpointConfiguration` atribut propojení koncový bod standardní konfiguraci koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="49812-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="49812-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="49812-116">Child Elements</span></span>  
 <span data-ttu-id="49812-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="49812-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="49812-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="49812-118">Parent Elements</span></span>  
  
|<span data-ttu-id="49812-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="49812-119">Element</span></span>|<span data-ttu-id="49812-120">Popis</span><span class="sxs-lookup"><span data-stu-id="49812-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="49812-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="49812-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="49812-122">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="49812-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
