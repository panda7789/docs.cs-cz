---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 9f3a95fd0a39f199eaf13c7509aff22caa0e3b66
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251788"
---
# <a name="tokenreplaycache"></a><span data-ttu-id="bc57d-101">\<tokenReplayCache></span><span class="sxs-lookup"><span data-stu-id="bc57d-101">\<tokenReplayCache></span></span>
<span data-ttu-id="bc57d-102">Zaregistruje mezipaměť opětovného přehrání tokenu pomocí kolekce obslužné rutiny tokenu zabezpečení nebo služby.</span><span class="sxs-lookup"><span data-stu-id="bc57d-102">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
<span data-ttu-id="bc57d-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="bc57d-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="bc57d-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="bc57d-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="bc57d-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="bc57d-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="bc57d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<ukládá do mezipaměti >** ](caches.md)</span><span class="sxs-lookup"><span data-stu-id="bc57d-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)</span></span>\
<span data-ttu-id="bc57d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tokenReplayCache >**</span><span class="sxs-lookup"><span data-stu-id="bc57d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bc57d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="bc57d-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <tokenReplayCache type=xs:string>  
      </tokenReplayCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bc57d-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="bc57d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="bc57d-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="bc57d-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bc57d-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="bc57d-111">Attributes</span></span>  
  
|<span data-ttu-id="bc57d-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="bc57d-112">Attribute</span></span>|<span data-ttu-id="bc57d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="bc57d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bc57d-114">– typ</span><span class="sxs-lookup"><span data-stu-id="bc57d-114">type</span></span>|<span data-ttu-id="bc57d-115">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.TokenReplayCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="bc57d-115">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="bc57d-116">Další informace o tom, jak zadat vlastní `type`, naleznete v tématu [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="bc57d-116">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="bc57d-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="bc57d-117">Child Elements</span></span>  
 <span data-ttu-id="bc57d-118">Žádné</span><span class="sxs-lookup"><span data-stu-id="bc57d-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bc57d-119">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="bc57d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="bc57d-120">Prvek</span><span class="sxs-lookup"><span data-stu-id="bc57d-120">Element</span></span>|<span data-ttu-id="bc57d-121">Popis</span><span class="sxs-lookup"><span data-stu-id="bc57d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="bc57d-122">\<caches></span><span class="sxs-lookup"><span data-stu-id="bc57d-122">\<caches></span></span>](caches.md)|<span data-ttu-id="bc57d-123">Zaregistruje mezipaměti používané službou nebo kolekcí obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="bc57d-123">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bc57d-124">Poznámky</span><span class="sxs-lookup"><span data-stu-id="bc57d-124">Remarks</span></span>  
 <span data-ttu-id="bc57d-125">Mezipaměť pro opětovné přehrání tokenu se používá ke zjišťování předaných tokenů.</span><span class="sxs-lookup"><span data-stu-id="bc57d-125">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="bc57d-126">Detekce opětovného přehrání tokenu je povolena [ \<prvkem tokenReplayDetection >](tokenreplaydetection.md) , který také určuje maximální dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="bc57d-126">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bc57d-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc57d-127">Example</span></span>  
 <span data-ttu-id="bc57d-128">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro detekci přehráných tokenů.</span><span class="sxs-lookup"><span data-stu-id="bc57d-128">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="bc57d-129">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bc57d-129">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [<span data-ttu-id="bc57d-130">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="bc57d-130">\<tokenReplayDetection></span></span>](tokenreplaydetection.md)
