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
ms.openlocfilehash: 6eefecb696c88d160e56c7f12a1b03ea67e531b6
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltmexendpointgt"></a><span data-ttu-id="713ca-102">&lt;mexEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="713ca-102">&lt;mexEndpoint&gt;</span></span>
<span data-ttu-id="713ca-103">Tento element konfigurace definuje standardní koncový bod s pevnou IMetadataExchange kontrakt.</span><span class="sxs-lookup"><span data-stu-id="713ca-103">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="713ca-104">Vzhledem k tomu, že všechny koncové body metadat serveru exchange zadejte IMetadataExchange jako jejich kontrakt, můžete použít tento standardní bod místo definování jeden pro sami.</span><span class="sxs-lookup"><span data-stu-id="713ca-104">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="713ca-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="713ca-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="713ca-106">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="713ca-106">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="713ca-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="713ca-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>  
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="713ca-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="713ca-108">Attributes and Elements</span></span>  
 <span data-ttu-id="713ca-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="713ca-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="713ca-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="713ca-110">Attributes</span></span>  
  
|<span data-ttu-id="713ca-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="713ca-111">Attribute</span></span>|<span data-ttu-id="713ca-112">Popis</span><span class="sxs-lookup"><span data-stu-id="713ca-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="713ca-113">name</span><span class="sxs-lookup"><span data-stu-id="713ca-113">name</span></span>|<span data-ttu-id="713ca-114">Řetězec, který určuje název konfigurace standardní koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="713ca-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="713ca-115">Název je používán `endpointConfiguration` atribut propojení koncový bod standardní konfiguraci koncového bodu služby.</span><span class="sxs-lookup"><span data-stu-id="713ca-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="713ca-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="713ca-116">Child Elements</span></span>  
 <span data-ttu-id="713ca-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="713ca-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="713ca-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="713ca-118">Parent Elements</span></span>  
  
|<span data-ttu-id="713ca-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="713ca-119">Element</span></span>|<span data-ttu-id="713ca-120">Popis</span><span class="sxs-lookup"><span data-stu-id="713ca-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="713ca-121">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="713ca-121">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="713ca-122">Kolekce standardních koncových bodů, které jsou předem definované koncových bodů s jedním nebo více jejich vlastnosti (adresy, vazby, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="713ca-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
