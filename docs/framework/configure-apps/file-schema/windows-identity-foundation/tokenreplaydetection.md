---
title: '&lt;tokenReplayDetection&gt;'
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: bd2272cb83dc0183d5008cfa178e11783f51ca2d
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/26/2018
ms.locfileid: "47205925"
---
# <a name="lttokenreplaydetectiongt"></a><span data-ttu-id="68ea4-102">&lt;tokenReplayDetection&gt;</span><span class="sxs-lookup"><span data-stu-id="68ea4-102">&lt;tokenReplayDetection&gt;</span></span>
<span data-ttu-id="68ea4-103">Umožňuje rozpoznání opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="68ea4-103">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="68ea4-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="68ea4-104">\<system.identityModel></span></span>  
<span data-ttu-id="68ea4-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="68ea4-105">\<identityConfiguration></span></span>  
<span data-ttu-id="68ea4-106">\<tokenReplayDetection ></span><span class="sxs-lookup"><span data-stu-id="68ea4-106">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="68ea4-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="68ea4-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="68ea4-108">Typ</span><span class="sxs-lookup"><span data-stu-id="68ea4-108">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="68ea4-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="68ea4-109">Attributes and Elements</span></span>  
 <span data-ttu-id="68ea4-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="68ea4-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="68ea4-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="68ea4-111">Attributes</span></span>  
  
|<span data-ttu-id="68ea4-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="68ea4-112">Attribute</span></span>|<span data-ttu-id="68ea4-113">Popis</span><span class="sxs-lookup"><span data-stu-id="68ea4-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="68ea4-114">Povoleno</span><span class="sxs-lookup"><span data-stu-id="68ea4-114">enabled</span></span>|<span data-ttu-id="68ea4-115">Hodnota, která určuje, zda je povoleno rozpoznání opětovného přehrání tokenu; zjišťování opakování povolit token "true".</span><span class="sxs-lookup"><span data-stu-id="68ea4-115">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="68ea4-116">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="68ea4-116">expirationPeriod</span></span>|<span data-ttu-id="68ea4-117">A <xref:System.TimeSpan> , která určuje maximální množství času, než položka je považována za vypršela platnost a odebrány z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="68ea4-117">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="68ea4-118">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v článku [hodnoty prvku Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="68ea4-118">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="68ea4-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="68ea4-119">Child Elements</span></span>  
 <span data-ttu-id="68ea4-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="68ea4-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="68ea4-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="68ea4-121">Parent Elements</span></span>  
  
|<span data-ttu-id="68ea4-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="68ea4-122">Element</span></span>|<span data-ttu-id="68ea4-123">Popis</span><span class="sxs-lookup"><span data-stu-id="68ea4-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="68ea4-124">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="68ea4-124">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="68ea4-125">Určuje nastavení identit na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="68ea4-125">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="68ea4-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="68ea4-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="68ea4-127">Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="68ea4-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="68ea4-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="68ea4-128">Remarks</span></span>  
 <span data-ttu-id="68ea4-129">A `<tokenReplayDetection>` element se dá nastavit na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužné rutiny tokenů zabezpečení v rámci `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="68ea4-129">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="68ea4-130">Nastavení kolekce obslužné rutiny tokenů přepíšou nastavení zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="68ea4-130">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="68ea4-131">Typ mezipaměti opětovného přehrání tokenu je určená [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="68ea4-131">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
