---
title: <serviceAuthenticationManager>
ms.date: 03/30/2017
ms.assetid: 5d69e64f-f325-4d55-8e2d-0fb30f222dda
ms.openlocfilehash: cc5ebcf36a10e88d48ed14f1f10dac6396d7b242
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399712"
---
# \<serviceAuthenticationManager>
<span data-ttu-id="cf776-101">Poskytuje prvek konfigurace pracovního postupu, který na úrovni služby stanovuje platnost přenosu, zprávy nebo původce.</span><span class="sxs-lookup"><span data-stu-id="cf776-101">Provides a workflow configuration element that establishes at the service level the validity of a transmission, message, or originator.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<serviceAuthenticationManager>**  
  
## <a name="syntax"></a><span data-ttu-id="cf776-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cf776-102">Syntax</span></span>  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <serviceAuthenticationManager serviceAuthenticationManagerType="String" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf776-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cf776-103">Attributes and Elements</span></span>  
 <span data-ttu-id="cf776-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cf776-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf776-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="cf776-105">Attributes</span></span>  
  
|<span data-ttu-id="cf776-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="cf776-106">Attribute</span></span>|<span data-ttu-id="cf776-107">Popis</span><span class="sxs-lookup"><span data-stu-id="cf776-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cf776-108">Typ ServiceAuthenticationManagerType</span><span class="sxs-lookup"><span data-stu-id="cf776-108">serviceAuthenticationManagerType</span></span>|<span data-ttu-id="cf776-109">Řetězec, který určuje typ zásad ověřování pro aktuální chování.</span><span class="sxs-lookup"><span data-stu-id="cf776-109">A string that specifies the type of the authentication policy for the current behavior.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cf776-110">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cf776-110">Child Elements</span></span>  
 <span data-ttu-id="cf776-111">Žádné</span><span class="sxs-lookup"><span data-stu-id="cf776-111">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cf776-112">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cf776-112">Parent Elements</span></span>  
  
|<span data-ttu-id="cf776-113">Prvek</span><span class="sxs-lookup"><span data-stu-id="cf776-113">Element</span></span>|<span data-ttu-id="cf776-114">Description</span><span class="sxs-lookup"><span data-stu-id="cf776-114">Description</span></span>|  
|-------------|-----------------|  
|[\<behavior>](behavior-of-endpointbehaviors.md)|<span data-ttu-id="cf776-115">Určuje chování element.</span><span class="sxs-lookup"><span data-stu-id="cf776-115">Specifies a behavior element.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf776-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="cf776-116">See also</span></span>

- <xref:System.ServiceModel.Configuration.ServiceAuthenticationElement>
