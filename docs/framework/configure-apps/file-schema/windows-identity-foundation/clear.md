---
title: <clear>
ms.date: 03/30/2017
ms.assetid: 54dcd1d1-038f-4fc8-a3a4-56ba7a1ca0fd
author: BrucePerlerMS
ms.openlocfilehash: e96349c72fc4a952e3dc7efeea5f69ebaa1fd0ad
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252048"
---
# <a name="clear"></a><span data-ttu-id="e2801-101">\<Vymazat ></span><span class="sxs-lookup"><span data-stu-id="e2801-101">\<clear></span></span>
<span data-ttu-id="e2801-102">Vymaže všechny obslužné rutiny tokenů zabezpečení z aktuální kolekce obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="e2801-102">Clears all security token handlers from the current token handler collection.</span></span>  
  
<span data-ttu-id="e2801-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e2801-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e2801-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="e2801-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="e2801-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="e2801-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="e2801-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="e2801-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="e2801-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<Vymazat >**</span><span class="sxs-lookup"><span data-stu-id="e2801-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<clear>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2801-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e2801-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2801-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e2801-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e2801-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e2801-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2801-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="e2801-111">Attributes</span></span>  
 <span data-ttu-id="e2801-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="e2801-112">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e2801-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e2801-113">Child Elements</span></span>  
 <span data-ttu-id="e2801-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="e2801-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e2801-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e2801-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e2801-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="e2801-116">Element</span></span>|<span data-ttu-id="e2801-117">Popis</span><span class="sxs-lookup"><span data-stu-id="e2801-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2801-118">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e2801-118">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="e2801-119">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="e2801-119">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|
