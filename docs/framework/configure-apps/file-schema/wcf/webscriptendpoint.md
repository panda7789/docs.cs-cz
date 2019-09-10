---
title: <webScriptEndpoint>
ms.date: 03/30/2017
ms.assetid: 85cb5ecf-351b-45f3-aa29-aa2e4b64bcdd
ms.openlocfilehash: b4bc33cf8ff4e703973efe7df49e9f1d2189302e
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70854811"
---
# <a name="webscriptendpoint"></a><span data-ttu-id="d1921-101">\<webScriptEndpoint></span><span class="sxs-lookup"><span data-stu-id="d1921-101">\<webScriptEndpoint></span></span>
<span data-ttu-id="d1921-102">Tento prvek konfigurace definuje standardní koncový bod s pevnou [ \<vazbou WebHttpBinding >](webhttpbinding.md) [ \<](enablewebscript.md) , která automaticky přidá chování enableWebScript >.</span><span class="sxs-lookup"><span data-stu-id="d1921-102">This configuration element defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="d1921-103">Tento koncový bod použijte při psaní služby, která se volá z aplikace ASP.NET AJAX.</span><span class="sxs-lookup"><span data-stu-id="d1921-103">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>  
  
<span data-ttu-id="d1921-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d1921-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d1921-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="d1921-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="d1921-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Oddílu StandardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="d1921-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="d1921-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<webScriptEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="d1921-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<webScriptEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1921-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d1921-108">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <webScriptEndpoint>
      <standardEndpoint webEndpointType="String" />
    </webScriptEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1921-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d1921-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d1921-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d1921-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1921-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="d1921-111">Attributes</span></span>  
  
|<span data-ttu-id="d1921-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="d1921-112">Attribute</span></span>|<span data-ttu-id="d1921-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d1921-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d1921-114">webEndpointType</span><span class="sxs-lookup"><span data-stu-id="d1921-114">webEndpointType</span></span>|<span data-ttu-id="d1921-115">Řetězec, který určuje typ koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d1921-115">A string that specifies the type of the endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d1921-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d1921-116">Child Elements</span></span>  
 <span data-ttu-id="d1921-117">Žádné</span><span class="sxs-lookup"><span data-stu-id="d1921-117">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d1921-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d1921-118">Parent Elements</span></span>  
  
|<span data-ttu-id="d1921-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="d1921-119">Element</span></span>|<span data-ttu-id="d1921-120">Popis</span><span class="sxs-lookup"><span data-stu-id="d1921-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1921-121">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="d1921-121">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="d1921-122">Kolekce standardních koncových bodů, které jsou předem definovanými koncovými body s jednou nebo více vlastnostmi (adresa, vazba, smlouva) opraveny.</span><span class="sxs-lookup"><span data-stu-id="d1921-122">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d1921-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d1921-123">See also</span></span>

- <xref:System.ServiceModel.Description.WebScriptEndpoint>
- <xref:System.ServiceModel.Configuration.WebScriptEndpointElement>
