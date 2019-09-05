---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: a4454042e1d97fb3cc2d6f2735104dadda6e7b5a
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251775"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="c8dd5-101">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="c8dd5-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="c8dd5-102">Umožňuje detekci opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="c8dd5-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
<span data-ttu-id="c8dd5-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c8dd5-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c8dd5-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="c8dd5-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="c8dd5-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c8dd5-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="c8dd5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<tokenReplayDetection >**</span><span class="sxs-lookup"><span data-stu-id="c8dd5-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8dd5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c8dd5-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="c8dd5-108">type</span><span class="sxs-lookup"><span data-stu-id="c8dd5-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8dd5-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c8dd5-109">Attributes and Elements</span></span>  
 <span data-ttu-id="c8dd5-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c8dd5-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8dd5-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="c8dd5-111">Attributes</span></span>  
  
|<span data-ttu-id="c8dd5-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="c8dd5-112">Attribute</span></span>|<span data-ttu-id="c8dd5-113">Popis</span><span class="sxs-lookup"><span data-stu-id="c8dd5-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8dd5-114">enabled</span><span class="sxs-lookup"><span data-stu-id="c8dd5-114">enabled</span></span>|<span data-ttu-id="c8dd5-115">Hodnota, která určuje, zda je povoleno zjišťování opětovného přehrání tokenu; "true" pro povolení detekce opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="c8dd5-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="c8dd5-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="c8dd5-116">expirationPeriod</span></span>|<span data-ttu-id="c8dd5-117">A <xref:System.TimeSpan> určuje maximální dobu před tím, než vyprší platnost položky a její odebrání z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="c8dd5-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="c8dd5-118">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v tématu [hodnoty TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="c8dd5-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8dd5-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c8dd5-119">Child Elements</span></span>  
 <span data-ttu-id="c8dd5-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="c8dd5-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8dd5-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c8dd5-121">Parent Elements</span></span>  
  
|<span data-ttu-id="c8dd5-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="c8dd5-122">Element</span></span>|<span data-ttu-id="c8dd5-123">Popis</span><span class="sxs-lookup"><span data-stu-id="c8dd5-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8dd5-124">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c8dd5-124">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="c8dd5-125">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="c8dd5-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="c8dd5-126">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="c8dd5-126">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="c8dd5-127">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c8dd5-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8dd5-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c8dd5-128">Remarks</span></span>  
 <span data-ttu-id="c8dd5-129">Element lze zadat na úrovni služby `<identityConfiguration>` pod prvkem nebo na úrovni kolekce `<securityTokenHandlerConfiguration>` obslužné rutiny tokenu zabezpečení pod prvkem. `<tokenReplayDetection>`</span><span class="sxs-lookup"><span data-stu-id="c8dd5-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="c8dd5-130">Nastavení v kolekci obslužných rutin tokenu přepíší hodnoty zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="c8dd5-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="c8dd5-131">Typ mezipaměti pro opětovné přehrání tokenu je určen [ \<elementem > tokenReplayCache](tokenreplaycache.md) .</span><span class="sxs-lookup"><span data-stu-id="c8dd5-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
