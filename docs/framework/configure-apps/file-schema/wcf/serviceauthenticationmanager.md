---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: cc5ebcf36a10e88d48ed14f1f10dac6396d7b242
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399712"
---
# <a name="serviceauthenticationmanager"></a><span data-ttu-id="f9752-101">\<serviceAuthenticationManager></span><span class="sxs-lookup"><span data-stu-id="f9752-101">\<serviceAuthenticationManager></span></span>
<span data-ttu-id="f9752-102">Poskytuje prvek konfigurace pracovního postupu, který na úrovni služby stanovuje platnost přenosu, zprávy nebo původce.</span><span class="sxs-lookup"><span data-stu-id="f9752-102">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
<span data-ttu-id="f9752-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f9752-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f9752-104">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f9752-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f9752-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f9752-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="f9752-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceBehaviors >** ](servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f9752-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)</span></span>\
<span data-ttu-id="f9752-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-servicebehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="f9752-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)</span></span>\
<span data-ttu-id="f9752-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<serviceAuthenticationManager >**</span><span class="sxs-lookup"><span data-stu-id="f9752-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9752-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f9752-109">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f9752-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f9752-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f9752-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f9752-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f9752-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="f9752-112">Attributes</span></span>  
  
|<span data-ttu-id="f9752-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="f9752-113">Attribute</span></span>|<span data-ttu-id="f9752-114">Popis</span><span class="sxs-lookup"><span data-stu-id="f9752-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f9752-115">serviceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="f9752-115">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="f9752-116">Řetězec, který určuje typ zásad ověřování pro aktuální chování.</span><span class="sxs-lookup"><span data-stu-id="f9752-116">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f9752-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f9752-117">Child Elements</span></span>  
 <span data-ttu-id="f9752-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="f9752-118">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f9752-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f9752-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f9752-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="f9752-120">Element</span></span>|<span data-ttu-id="f9752-121">Popis</span><span class="sxs-lookup"><span data-stu-id="f9752-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f9752-122">\<> chování</span><span class="sxs-lookup"><span data-stu-id="f9752-122">\<behavior></span></span>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="f9752-123">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="f9752-123">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f9752-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f9752-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
