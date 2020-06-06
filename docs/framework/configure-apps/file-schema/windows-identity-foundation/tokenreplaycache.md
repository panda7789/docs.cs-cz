---
title: <tokenReplayCache>
ms.date: 03/30/2017
ms.assetid: 1572ab23-6933-41b5-bfb4-0c4548145500
author: BrucePerlerMS
ms.openlocfilehash: 9f3a95fd0a39f199eaf13c7509aff22caa0e3b66
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251788"
---
# \<tokenReplayCache>
<span data-ttu-id="aeb1c-101">Zaregistruje mezipaměť opětovného přehrání tokenu pomocí kolekce obslužné rutiny tokenu zabezpečení nebo služby.</span><span class="sxs-lookup"><span data-stu-id="aeb1c-101">Registers a token replay cache with a service or a security token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<caches>**](caches.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayCache>**  
  
## <a name="syntax"></a><span data-ttu-id="aeb1c-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aeb1c-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="aeb1c-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="aeb1c-103">Attributes and Elements</span></span>  
 <span data-ttu-id="aeb1c-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="aeb1c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="aeb1c-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="aeb1c-105">Attributes</span></span>  
  
|<span data-ttu-id="aeb1c-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="aeb1c-106">Attribute</span></span>|<span data-ttu-id="aeb1c-107">Popis</span><span class="sxs-lookup"><span data-stu-id="aeb1c-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="aeb1c-108">typ</span><span class="sxs-lookup"><span data-stu-id="aeb1c-108">type</span></span>|<span data-ttu-id="aeb1c-109">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.TokenReplayCache> třídy.</span><span class="sxs-lookup"><span data-stu-id="aeb1c-109">A type that derives from the <xref:System.IdentityModel.Tokens.TokenReplayCache> class.</span></span> <span data-ttu-id="aeb1c-110">Další informace o tom, jak zadat vlastní `type` , naleznete v tématu [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="aeb1c-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>
  
### <a name="child-elements"></a><span data-ttu-id="aeb1c-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="aeb1c-111">Child Elements</span></span>  
 <span data-ttu-id="aeb1c-112">Žádné</span><span class="sxs-lookup"><span data-stu-id="aeb1c-112">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="aeb1c-113">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="aeb1c-113">Parent Elements</span></span>  
  
|<span data-ttu-id="aeb1c-114">Prvek</span><span class="sxs-lookup"><span data-stu-id="aeb1c-114">Element</span></span>|<span data-ttu-id="aeb1c-115">Description</span><span class="sxs-lookup"><span data-stu-id="aeb1c-115">Description</span></span>|  
|-------------|-----------------|  
|[\<caches>](caches.md)|<span data-ttu-id="aeb1c-116">Zaregistruje mezipaměti používané službou nebo kolekcí obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="aeb1c-116">Registers the caches used by a service or a security token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aeb1c-117">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aeb1c-117">Remarks</span></span>  
 <span data-ttu-id="aeb1c-118">Mezipaměť pro opětovné přehrání tokenu se používá ke zjišťování předaných tokenů.</span><span class="sxs-lookup"><span data-stu-id="aeb1c-118">The token replay cache is used to detect replayed tokens.</span></span> <span data-ttu-id="aeb1c-119">Detekce opětovného přehrání tokenu je povolena [\<tokenReplayDetection>](tokenreplaydetection.md) prvkem, který také určuje maximální dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="aeb1c-119">Token replay detection is enabled by the [\<tokenReplayDetection>](tokenreplaydetection.md) element, which also specifies the maximum expiration time for tokens.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aeb1c-120">Příklad</span><span class="sxs-lookup"><span data-stu-id="aeb1c-120">Example</span></span>  
 <span data-ttu-id="aeb1c-121">Následující kód XML ukazuje konfiguraci vlastní mezipaměti pro detekci přehráných tokenů.</span><span class="sxs-lookup"><span data-stu-id="aeb1c-121">The following XML shows the configuration of a custom cache for detecting replayed tokens.</span></span>  
  
```xml  
<caches>  
  <tokenReplayCache type="MyCacheLibrary.MyTokenReplayCache, MyCacheLibrary">  
  </tokenReplayCache>  
</caches>  
```  
  
## <a name="see-also"></a><span data-ttu-id="aeb1c-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="aeb1c-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.TokenReplayCache>
- [\<tokenReplayDetection>](tokenreplaydetection.md)
