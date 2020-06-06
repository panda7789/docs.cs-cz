---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: a4454042e1d97fb3cc2d6f2735104dadda6e7b5a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251775"
---
# \<tokenReplayDetection>
<span data-ttu-id="7b64d-101">Umožňuje detekci opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="7b64d-101">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<tokenReplayDetection>**  
  
## <a name="syntax"></a><span data-ttu-id="7b64d-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7b64d-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="7b64d-103">Typ</span><span class="sxs-lookup"><span data-stu-id="7b64d-103">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b64d-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7b64d-104">Attributes and Elements</span></span>  
 <span data-ttu-id="7b64d-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7b64d-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b64d-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="7b64d-106">Attributes</span></span>  
  
|<span data-ttu-id="7b64d-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="7b64d-107">Attribute</span></span>|<span data-ttu-id="7b64d-108">Popis</span><span class="sxs-lookup"><span data-stu-id="7b64d-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7b64d-109">enabled</span><span class="sxs-lookup"><span data-stu-id="7b64d-109">enabled</span></span>|<span data-ttu-id="7b64d-110">Hodnota, která určuje, zda je povoleno zjišťování opětovného přehrání tokenu; "true" pro povolení detekce opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="7b64d-110">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="7b64d-111">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="7b64d-111">expirationPeriod</span></span>|<span data-ttu-id="7b64d-112">A <xref:System.TimeSpan> Určuje maximální dobu před tím, než vyprší platnost položky a její odebrání z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="7b64d-112">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="7b64d-113">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v tématu [hodnoty TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="7b64d-113">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7b64d-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7b64d-114">Child Elements</span></span>  
 <span data-ttu-id="7b64d-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="7b64d-115">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7b64d-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7b64d-116">Parent Elements</span></span>  
  
|<span data-ttu-id="7b64d-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="7b64d-117">Element</span></span>|<span data-ttu-id="7b64d-118">Description</span><span class="sxs-lookup"><span data-stu-id="7b64d-118">Description</span></span>|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|<span data-ttu-id="7b64d-119">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="7b64d-119">Specifies service-level identity settings.</span></span>|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="7b64d-120">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7b64d-120">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b64d-121">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7b64d-121">Remarks</span></span>  
 <span data-ttu-id="7b64d-122">`<tokenReplayDetection>`Element lze zadat na úrovni služby pod `<identityConfiguration>` prvkem nebo na úrovni kolekce obslužné rutiny tokenu zabezpečení pod `<securityTokenHandlerConfiguration>` prvkem.</span><span class="sxs-lookup"><span data-stu-id="7b64d-122">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="7b64d-123">Nastavení v kolekci obslužných rutin tokenu přepíší hodnoty zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="7b64d-123">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="7b64d-124">Typ mezipaměti pro opětovné přehrání tokenu je určen [\<tokenReplayCache>](tokenreplaycache.md) elementem.</span><span class="sxs-lookup"><span data-stu-id="7b64d-124">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
