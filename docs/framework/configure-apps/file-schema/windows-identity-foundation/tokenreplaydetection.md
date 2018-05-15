---
title: '&lt;tokenReplayDetection&gt;'
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 7f0cef2590bb301e6897aa4922454942ecdd0957
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="4c19f-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="4c19f-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="4c19f-103">Umožňuje rozpoznání opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="4c19f-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="4c19f-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4c19f-104">\<system.identityModel></span></span>  
<span data-ttu-id="4c19f-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4c19f-105">\<identityConfiguration></span></span>  
<span data-ttu-id="4c19f-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="4c19f-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4c19f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4c19f-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="4c19f-108">Typ</span><span class="sxs-lookup"><span data-stu-id="4c19f-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c19f-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4c19f-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4c19f-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="4c19f-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c19f-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4c19f-111">Attributes</span></span>  
  
|<span data-ttu-id="4c19f-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="4c19f-112">Attribute</span></span>|<span data-ttu-id="4c19f-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4c19f-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c19f-114">povoleno</span><span class="sxs-lookup"><span data-stu-id="4c19f-114">enabled</span></span>|<span data-ttu-id="4c19f-115">Hodnota, která určuje, zda je povoleno rozpoznání opětovného přehrání tokenu; zjišťování opakování "true" Povolit token.</span><span class="sxs-lookup"><span data-stu-id="4c19f-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="4c19f-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="4c19f-116">expirationPeriod</span></span>|<span data-ttu-id="4c19f-117">A <xref:System.TimeSpan> který určuje maximální množství času položku považuje za platnost a odebrány z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4c19f-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="4c19f-118">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v části [časový interval hodnoty](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="4c19f-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c19f-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4c19f-119">Child Elements</span></span>  
 <span data-ttu-id="4c19f-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="4c19f-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4c19f-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4c19f-121">Parent Elements</span></span>  
  
|<span data-ttu-id="4c19f-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="4c19f-122">Element</span></span>|<span data-ttu-id="4c19f-123">Popis</span><span class="sxs-lookup"><span data-stu-id="4c19f-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4c19f-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4c19f-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="4c19f-125">Určuje nastavení identity úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="4c19f-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="4c19f-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="4c19f-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="4c19f-127">Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="4c19f-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4c19f-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4c19f-128">Remarks</span></span>  
 <span data-ttu-id="4c19f-129">A `<tokenReplayDetection>` element lze na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužná rutina tokenu zabezpečení v části `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="4c19f-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="4c19f-130">Nastavení na kolekci obslužná rutina tokenu přepíšou nastavení zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="4c19f-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="4c19f-131">Typ mezipaměti opětovného přehrání tokenu je zadána [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span><span class="sxs-lookup"><span data-stu-id="4c19f-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
