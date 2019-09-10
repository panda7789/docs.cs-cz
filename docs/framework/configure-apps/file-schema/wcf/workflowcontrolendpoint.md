---
title: <workflowControlEndpoint>
ms.date: 03/30/2017
ms.assetid: 6c89e76c-643b-4b6a-9b25-628f753d7027
ms.openlocfilehash: 670c1573fe4378a18c19d0a58fe58241745725bd
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854781"
---
# <a name="workflowcontrolendpoint"></a><span data-ttu-id="52d07-101">\<workflowControlEndpoint></span><span class="sxs-lookup"><span data-stu-id="52d07-101">\<workflowControlEndpoint></span></span>
<span data-ttu-id="52d07-102">Tento prvek konfigurace definuje standardní koncový bod pro řízení spouštění instancí pracovního postupu (vytvořit, spustit, pozastavit, ukončit atd.).</span><span class="sxs-lookup"><span data-stu-id="52d07-102">This configuration element defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>  
  
<span data-ttu-id="52d07-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="52d07-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="52d07-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="52d07-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="52d07-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="52d07-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="52d07-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<workflowControlEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="52d07-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<workflowControlEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52d07-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="52d07-107">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <workflowControlEndpoint>
      <standardEndpoint name="String" />
    </workflowControlEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="52d07-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="52d07-108">Attributes and Elements</span></span>  
 <span data-ttu-id="52d07-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="52d07-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="52d07-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="52d07-110">Attributes</span></span>  
  
|<span data-ttu-id="52d07-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="52d07-111">Attribute</span></span>|<span data-ttu-id="52d07-112">Popis</span><span class="sxs-lookup"><span data-stu-id="52d07-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="52d07-113">name</span><span class="sxs-lookup"><span data-stu-id="52d07-113">name</span></span>|<span data-ttu-id="52d07-114">Řetězec, který určuje název konfigurace standardního koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="52d07-114">A String that specifies the name of the configuration of the standard endpoint.</span></span> <span data-ttu-id="52d07-115">Název se používá v `endpointConfiguration` atributu koncového bodu služby k propojení standardního koncového bodu s jeho konfigurací.</span><span class="sxs-lookup"><span data-stu-id="52d07-115">The name is used in the `endpointConfiguration` attribute of the service endpoint to link a standard endpoint to its configuration.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="52d07-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="52d07-116">Child Elements</span></span>  
 <span data-ttu-id="52d07-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="52d07-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="52d07-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="52d07-118">Parent Elements</span></span>  
  
|<span data-ttu-id="52d07-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="52d07-119">Element</span></span>|<span data-ttu-id="52d07-120">Popis</span><span class="sxs-lookup"><span data-stu-id="52d07-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="52d07-121">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="52d07-121">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="52d07-122">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="52d07-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="52d07-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="52d07-123">See also</span></span>

- <xref:System.ServiceModel.Activities.WorkflowControlEndpoint>
