---
title: <add> z <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: f5de2aa897a3bc37d08932451a2c7b94bc603b9e
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400640"
---
# <a name="add-of-defaultports"></a><span data-ttu-id="5daf5-102">\<Přidat > \<> defaultPorts</span><span class="sxs-lookup"><span data-stu-id="5daf5-102">\<add> of \<defaultPorts></span></span>
<span data-ttu-id="5daf5-103">Výchozí koncový bod komunikace, na kterém naslouchá klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="5daf5-103">A default communications endpoint that the client application listens to.</span></span>  
  
<span data-ttu-id="5daf5-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="5daf5-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="5daf5-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="5daf5-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="5daf5-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5daf5-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="5daf5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5daf5-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="5daf5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="5daf5-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="5daf5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<useRequestHeadersForMetadataAddress >** ](userequestheadersformetadataaddress.md)</span><span class="sxs-lookup"><span data-stu-id="5daf5-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<useRequestHeadersForMetadataAddress>**](userequestheadersformetadataaddress.md)</span></span>\
<span data-ttu-id="5daf5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<defaultPorts >** ](defaultports.md)</span><span class="sxs-lookup"><span data-stu-id="5daf5-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<defaultPorts>**](defaultports.md)</span></span>\
<span data-ttu-id="5daf5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Přidat >**</span><span class="sxs-lookup"><span data-stu-id="5daf5-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5daf5-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5daf5-112">Syntax</span></span>  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5daf5-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5daf5-113">Attributes and Elements</span></span>  
 <span data-ttu-id="5daf5-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5daf5-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5daf5-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="5daf5-115">Attributes</span></span>  
  
|<span data-ttu-id="5daf5-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="5daf5-116">Attribute</span></span>|<span data-ttu-id="5daf5-117">Popis</span><span class="sxs-lookup"><span data-stu-id="5daf5-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5daf5-118">port</span><span class="sxs-lookup"><span data-stu-id="5daf5-118">port</span></span>|<span data-ttu-id="5daf5-119">Celé číslo, které určuje výchozí číslo komunikačního portu</span><span class="sxs-lookup"><span data-stu-id="5daf5-119">An integer that specifies the default communications port number</span></span>|  
|<span data-ttu-id="5daf5-120">scheme</span><span class="sxs-lookup"><span data-stu-id="5daf5-120">scheme</span></span>|<span data-ttu-id="5daf5-121">Řetězec, který určuje skupinu nastavení protokolu, která je přidružena k komunikačnímu portu.</span><span class="sxs-lookup"><span data-stu-id="5daf5-121">A string that specifies the group of protocol settings associated with a communications port.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5daf5-122">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5daf5-122">Child Elements</span></span>  
 <span data-ttu-id="5daf5-123">Žádné</span><span class="sxs-lookup"><span data-stu-id="5daf5-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5daf5-124">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5daf5-124">Parent Elements</span></span>  
  
|<span data-ttu-id="5daf5-125">Prvek</span><span class="sxs-lookup"><span data-stu-id="5daf5-125">Element</span></span>|<span data-ttu-id="5daf5-126">Popis</span><span class="sxs-lookup"><span data-stu-id="5daf5-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5daf5-127">\<defaultPorts></span><span class="sxs-lookup"><span data-stu-id="5daf5-127">\<defaultPorts></span></span>](defaultports.md)|<span data-ttu-id="5daf5-128">Kolekce výchozích portů, které jsou uvedeny v seznamu výchozích koncových bodů komunikace, na které klientská aplikace naslouchá.</span><span class="sxs-lookup"><span data-stu-id="5daf5-128">A collection of default ports listing the default communications endpoints that the client application listens to.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5daf5-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5daf5-129">See also</span></span>

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
