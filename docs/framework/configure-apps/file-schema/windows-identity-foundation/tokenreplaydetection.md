---
title: '&lt;tokenReplayDetection&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
caps.latest.revision: "6"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 88622d4d30d40702425da8bbdbdaf2c4a6878f47
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="3b7d9-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="3b7d9-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="3b7d9-103">Umožňuje rozpoznání opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="3b7d9-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="3b7d9-104">\<system.identityModel></span></span>  
<span data-ttu-id="3b7d9-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3b7d9-105">\<identityConfiguration></span></span>  
<span data-ttu-id="3b7d9-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="3b7d9-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b7d9-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3b7d9-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="3b7d9-108">Typ</span><span class="sxs-lookup"><span data-stu-id="3b7d9-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3b7d9-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3b7d9-109">Attributes and Elements</span></span>  
 <span data-ttu-id="3b7d9-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3b7d9-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="3b7d9-111">Attributes</span></span>  
  
|<span data-ttu-id="3b7d9-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="3b7d9-112">Attribute</span></span>|<span data-ttu-id="3b7d9-113">Popis</span><span class="sxs-lookup"><span data-stu-id="3b7d9-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="3b7d9-114">povoleno</span><span class="sxs-lookup"><span data-stu-id="3b7d9-114">enabled</span></span>|<span data-ttu-id="3b7d9-115">Hodnota, která určuje, zda je povoleno rozpoznání opětovného přehrání tokenu; zjišťování opakování "true" Povolit token.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="3b7d9-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="3b7d9-116">expirationPeriod</span></span>|<span data-ttu-id="3b7d9-117">A <xref:System.TimeSpan> který určuje maximální množství času položku považuje za platnost a odebrány z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="3b7d9-118">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v části [časový interval hodnoty](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="3b7d9-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3b7d9-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3b7d9-119">Child Elements</span></span>  
 <span data-ttu-id="3b7d9-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="3b7d9-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3b7d9-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3b7d9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="3b7d9-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="3b7d9-122">Element</span></span>|<span data-ttu-id="3b7d9-123">Popis</span><span class="sxs-lookup"><span data-stu-id="3b7d9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3b7d9-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3b7d9-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="3b7d9-125">Určuje nastavení identity úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="3b7d9-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="3b7d9-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="3b7d9-127">Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b7d9-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3b7d9-128">Remarks</span></span>  
 <span data-ttu-id="3b7d9-129">A `<tokenReplayDetection>` element lze na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužná rutina tokenu zabezpečení v části `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="3b7d9-130">Nastavení na kolekci obslužná rutina tokenu přepíšou nastavení zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="3b7d9-131">Typ mezipaměti opětovného přehrání tokenu je zadána [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span><span class="sxs-lookup"><span data-stu-id="3b7d9-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
