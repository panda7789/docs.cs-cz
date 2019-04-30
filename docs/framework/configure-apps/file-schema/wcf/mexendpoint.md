---
title: <mexEndpoint>
ms.date: 03/30/2017
ms.assetid: c9823060-0a5d-4f9d-99d4-4d113b758247
ms.openlocfilehash: 8fffcc05d5f53f719efce182083fbf103b1230ff
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61772473"
---
# <a name="mexendpoint"></a><span data-ttu-id="cac0c-101">\<mexEndpoint></span><span class="sxs-lookup"><span data-stu-id="cac0c-101">\<mexEndpoint></span></span>
<span data-ttu-id="cac0c-102">Tento prvek konfigurace definuje standardní koncový bod s pevným kontraktem IMetadataExchange.</span><span class="sxs-lookup"><span data-stu-id="cac0c-102">This configuration element defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="cac0c-103">Protože všechny koncové body metadat exchange určit jako jejich kontraktu IMetadataExchange, můžete použít tento standardní bod místo definování sami.</span><span class="sxs-lookup"><span data-stu-id="cac0c-103">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>  
  
 <span data-ttu-id="cac0c-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="cac0c-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="cac0c-105">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="cac0c-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cac0c-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cac0c-106">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <mexEndpoint>
      <standardEndpoint name="String" />
    </mexEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cac0c-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cac0c-107">Attributes and Elements</span></span>  
 <span data-ttu-id="cac0c-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cac0c-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cac0c-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="cac0c-109">Attributes</span></span>  
  
|<span data-ttu-id="cac0c-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="cac0c-110">Attribute</span></span>|<span data-ttu-id="cac0c-111">Popis</span><span class="sxs-lookup"><span data-stu-id="cac0c-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cac0c-112">name</span><span class="sxs-lookup"><span data-stu-id="cac0c-112">name</span></span>|<span data-ttu-id="cac0c-113">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="cac0c-113">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="cac0c-114">Název se používá v `endpointConfiguration` atribut koncového bodu služby propojit s jeho konfigurace je standardní koncový bod.</span><span class="sxs-lookup"><span data-stu-id="cac0c-114">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cac0c-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cac0c-115">Child Elements</span></span>  
 <span data-ttu-id="cac0c-116">Žádné</span><span class="sxs-lookup"><span data-stu-id="cac0c-116">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cac0c-117">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cac0c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="cac0c-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="cac0c-118">Element</span></span>|<span data-ttu-id="cac0c-119">Popis</span><span class="sxs-lookup"><span data-stu-id="cac0c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cac0c-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="cac0c-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="cac0c-121">Kolekce standardních koncových bodů, které jsou předem definované koncové body s jedním nebo více z jejich vlastností (adresu, vazbu, kontrakt) pevné.</span><span class="sxs-lookup"><span data-stu-id="cac0c-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|
