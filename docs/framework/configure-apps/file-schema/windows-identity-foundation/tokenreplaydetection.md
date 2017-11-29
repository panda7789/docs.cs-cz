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
ms.openlocfilehash: f95d200f74621a40d2987acf68bc554df8d17ab6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="9fd78-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="9fd78-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="9fd78-103">Umožňuje rozpoznání opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="9fd78-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="9fd78-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="9fd78-104">\<system.identityModel></span></span>  
<span data-ttu-id="9fd78-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9fd78-105">\<identityConfiguration></span></span>  
<span data-ttu-id="9fd78-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="9fd78-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9fd78-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9fd78-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="9fd78-108">Typ</span><span class="sxs-lookup"><span data-stu-id="9fd78-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9fd78-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9fd78-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9fd78-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9fd78-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9fd78-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="9fd78-111">Attributes</span></span>  
  
|<span data-ttu-id="9fd78-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="9fd78-112">Attribute</span></span>|<span data-ttu-id="9fd78-113">Popis</span><span class="sxs-lookup"><span data-stu-id="9fd78-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9fd78-114">povoleno</span><span class="sxs-lookup"><span data-stu-id="9fd78-114">enabled</span></span>|<span data-ttu-id="9fd78-115">Hodnota, která určuje, zda je povoleno rozpoznání opětovného přehrání tokenu; zjišťování opakování "true" Povolit token.</span><span class="sxs-lookup"><span data-stu-id="9fd78-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="9fd78-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="9fd78-116">expirationPeriod</span></span>|<span data-ttu-id="9fd78-117">A <xref:System.TimeSpan> který určuje maximální množství času položku považuje za platnost a odebrány z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="9fd78-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="9fd78-118">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v části [časový interval hodnoty](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="9fd78-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9fd78-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9fd78-119">Child Elements</span></span>  
 <span data-ttu-id="9fd78-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="9fd78-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9fd78-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9fd78-121">Parent Elements</span></span>  
  
|<span data-ttu-id="9fd78-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="9fd78-122">Element</span></span>|<span data-ttu-id="9fd78-123">Popis</span><span class="sxs-lookup"><span data-stu-id="9fd78-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9fd78-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9fd78-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="9fd78-125">Určuje nastavení identity úrovně služeb.</span><span class="sxs-lookup"><span data-stu-id="9fd78-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="9fd78-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="9fd78-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="9fd78-127">Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="9fd78-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9fd78-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9fd78-128">Remarks</span></span>  
 <span data-ttu-id="9fd78-129">A `<tokenReplayDetection>` element lze na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužná rutina tokenu zabezpečení v části `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="9fd78-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="9fd78-130">Nastavení na kolekci obslužná rutina tokenu přepíšou nastavení zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="9fd78-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="9fd78-131">Typ mezipaměti opětovného přehrání tokenu je zadána [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span><span class="sxs-lookup"><span data-stu-id="9fd78-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
