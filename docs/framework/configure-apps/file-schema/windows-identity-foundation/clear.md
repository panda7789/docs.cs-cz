---
title: <clear>
ms.date: 03/30/2017
ms.assetid: 54dcd1d1-038f-4fc8-a3a4-56ba7a1ca0fd
author: BrucePerlerMS
ms.openlocfilehash: e96349c72fc4a952e3dc7efeea5f69ebaa1fd0ad
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252048"
---
# \<clear>
<span data-ttu-id="1b7a7-101">Vymaže všechny obslužné rutiny tokenů zabezpečení z aktuální kolekce obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="1b7a7-101">Clears all security token handlers from the current token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**  
  
## <a name="syntax"></a><span data-ttu-id="1b7a7-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1b7a7-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <clear>  
      </clear>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1b7a7-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1b7a7-103">Attributes and Elements</span></span>  
 <span data-ttu-id="1b7a7-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1b7a7-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1b7a7-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="1b7a7-105">Attributes</span></span>  
 <span data-ttu-id="1b7a7-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="1b7a7-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1b7a7-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1b7a7-107">Child Elements</span></span>  
 <span data-ttu-id="1b7a7-108">Žádné</span><span class="sxs-lookup"><span data-stu-id="1b7a7-108">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1b7a7-109">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1b7a7-109">Parent Elements</span></span>  
  
|<span data-ttu-id="1b7a7-110">Prvek</span><span class="sxs-lookup"><span data-stu-id="1b7a7-110">Element</span></span>|<span data-ttu-id="1b7a7-111">Description</span><span class="sxs-lookup"><span data-stu-id="1b7a7-111">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="1b7a7-112">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="1b7a7-112">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|
