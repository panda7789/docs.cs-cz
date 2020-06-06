---
title: <add> z <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: f5de2aa897a3bc37d08932451a2c7b94bc603b9e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400640"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="dd016-102">\<add> z \<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="dd016-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="dd016-103">Výchozí koncový bod komunikace, na kterém naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="dd016-103">A default communications endpoint that the client application listens to.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="dd016-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd016-104">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd016-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dd016-105">Attributes and Elements</span></span>  
 <span data-ttu-id="dd016-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dd016-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd016-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="dd016-107">Attributes</span></span>  
  
|<span data-ttu-id="dd016-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="dd016-108">Attribute</span></span>|<span data-ttu-id="dd016-109">Popis</span><span class="sxs-lookup"><span data-stu-id="dd016-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd016-110">port</span><span class="sxs-lookup"><span data-stu-id="dd016-110">port</span></span>|<span data-ttu-id="dd016-111">Celé číslo, které určuje výchozí číslo komunikačního portu</span><span class="sxs-lookup"><span data-stu-id="dd016-111">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="dd016-112">scheme</span><span class="sxs-lookup"><span data-stu-id="dd016-112">scheme</span></span>|<span data-ttu-id="dd016-113">Řetězec, který určuje skupinu nastavení protokolu, která je přidružena k komunikačnímu portu.</span><span class="sxs-lookup"><span data-stu-id="dd016-113">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd016-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dd016-114">Child Elements</span></span>  
 <span data-ttu-id="dd016-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="dd016-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dd016-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dd016-116">Parent Elements</span></span>  
  
|<span data-ttu-id="dd016-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="dd016-117">Element</span></span>|<span data-ttu-id="dd016-118">Description</span><span class="sxs-lookup"><span data-stu-id="dd016-118">Description</span></span>|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|<span data-ttu-id="dd016-119">Kolekce výchozích portů, které jsou uvedeny v seznamu výchozích koncových bodů komunikace, na které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="dd016-119">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="dd016-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="dd016-120">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
