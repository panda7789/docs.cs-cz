---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: 2e2159a73ca79fc362a8138eea95dbd173dafb11
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944301"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="8b1d4-101">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="8b1d4-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="8b1d4-102">Umožňuje detekci opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="8b1d4-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="8b1d4-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8b1d4-103">\<system.identityModel></span></span>  
<span data-ttu-id="8b1d4-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8b1d4-104">\<identityConfiguration></span></span>  
<span data-ttu-id="8b1d4-105">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="8b1d4-105">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b1d4-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8b1d4-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="8b1d4-107">type</span><span class="sxs-lookup"><span data-stu-id="8b1d4-107">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8b1d4-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8b1d4-108">Attributes and Elements</span></span>  
 <span data-ttu-id="8b1d4-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8b1d4-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8b1d4-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="8b1d4-110">Attributes</span></span>  
  
|<span data-ttu-id="8b1d4-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="8b1d4-111">Attribute</span></span>|<span data-ttu-id="8b1d4-112">Popis</span><span class="sxs-lookup"><span data-stu-id="8b1d4-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8b1d4-113">enabled</span><span class="sxs-lookup"><span data-stu-id="8b1d4-113">enabled</span></span>|<span data-ttu-id="8b1d4-114">Hodnota, která určuje, zda je povoleno zjišťování opětovného přehrání tokenu; "true" pro povolení detekce opětovného přehrání tokenu.</span><span class="sxs-lookup"><span data-stu-id="8b1d4-114">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="8b1d4-115">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="8b1d4-115">expirationPeriod</span></span>|<span data-ttu-id="8b1d4-116">A <xref:System.TimeSpan> určuje maximální dobu před tím, než vyprší platnost položky a její odebrání z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="8b1d4-116">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="8b1d4-117">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v tématu [hodnoty TimeSpan](../windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="8b1d4-117">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8b1d4-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8b1d4-118">Child Elements</span></span>  
 <span data-ttu-id="8b1d4-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="8b1d4-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8b1d4-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8b1d4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="8b1d4-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="8b1d4-121">Element</span></span>|<span data-ttu-id="8b1d4-122">Popis</span><span class="sxs-lookup"><span data-stu-id="8b1d4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8b1d4-123">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8b1d4-123">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="8b1d4-124">Určuje nastavení identity na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="8b1d4-124">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="8b1d4-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="8b1d4-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="8b1d4-126">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8b1d4-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b1d4-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8b1d4-127">Remarks</span></span>  
 <span data-ttu-id="8b1d4-128">Element lze zadat na úrovni služby `<identityConfiguration>` pod prvkem nebo na úrovni kolekce `<securityTokenHandlerConfiguration>` obslužné rutiny tokenu zabezpečení pod prvkem. `<tokenReplayDetection>`</span><span class="sxs-lookup"><span data-stu-id="8b1d4-128">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="8b1d4-129">Nastavení v kolekci obslužných rutin tokenu přepíší hodnoty zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="8b1d4-129">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="8b1d4-130">Typ mezipaměti pro opětovné přehrání tokenu je určen [ \<elementem > tokenReplayCache](tokenreplaycache.md) .</span><span class="sxs-lookup"><span data-stu-id="8b1d4-130">The type of the token replay cache is specified by the [\<tokenReplayCache>](tokenreplaycache.md) element.</span></span>
