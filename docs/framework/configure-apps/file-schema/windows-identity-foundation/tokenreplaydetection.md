---
title: <tokenReplayDetection>
ms.date: 03/30/2017
ms.assetid: ac3f588e-5f75-4275-b969-2d492ecc3b47
author: BrucePerlerMS
ms.openlocfilehash: 4deeb1d84f2621adb7ff1b649a505138b6856ec1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61790491"
---
# <a name="tokenreplaydetection"></a><span data-ttu-id="904e9-101">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="904e9-101">\<tokenReplayDetection></span></span>
<span data-ttu-id="904e9-102">Umožňuje rozpoznání opětovného přehrání tokenu a určuje dobu vypršení platnosti tokenů.</span><span class="sxs-lookup"><span data-stu-id="904e9-102">Enables token replay detection and specifies the expiration time for tokens.</span></span>  
  
 <span data-ttu-id="904e9-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="904e9-103">\<system.identityModel></span></span>  
<span data-ttu-id="904e9-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="904e9-104">\<identityConfiguration></span></span>  
<span data-ttu-id="904e9-105">\<tokenReplayDetection></span><span class="sxs-lookup"><span data-stu-id="904e9-105">\<tokenReplayDetection></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="904e9-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="904e9-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <tokenReplayDetection enabled=xs:boolean expirationPeriod=TimeSpan>  
    </tokenReplayDetection>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="type"></a><span data-ttu-id="904e9-107">Type</span><span class="sxs-lookup"><span data-stu-id="904e9-107">Type</span></span>  
 <xref:System.IdentityModel.Configuration.TokenReplayDetectionElement>  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="904e9-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="904e9-108">Attributes and Elements</span></span>  
 <span data-ttu-id="904e9-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="904e9-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="904e9-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="904e9-110">Attributes</span></span>  
  
|<span data-ttu-id="904e9-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="904e9-111">Attribute</span></span>|<span data-ttu-id="904e9-112">Popis</span><span class="sxs-lookup"><span data-stu-id="904e9-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="904e9-113">enabled</span><span class="sxs-lookup"><span data-stu-id="904e9-113">enabled</span></span>|<span data-ttu-id="904e9-114">Hodnota, která určuje, zda je povoleno rozpoznání opětovného přehrání tokenu; zjišťování opakování povolit token "true".</span><span class="sxs-lookup"><span data-stu-id="904e9-114">A value that specifies whether token replay detection is enabled; "true" to enable token replay detection.</span></span>|  
|<span data-ttu-id="904e9-115">expirationPeriod</span><span class="sxs-lookup"><span data-stu-id="904e9-115">expirationPeriod</span></span>|<span data-ttu-id="904e9-116">A <xref:System.TimeSpan> , která určuje maximální množství času, než položka je považována za vypršela platnost a odebrány z mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="904e9-116">A <xref:System.TimeSpan> that specifies the maximum amount of time before an item is considered expired and removed from the cache.</span></span>  <span data-ttu-id="904e9-117">Další informace o tom, jak zadat <xref:System.TimeSpan> hodnoty, najdete v článku [hodnoty prvku Timespan](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span><span class="sxs-lookup"><span data-stu-id="904e9-117">For more information about how to specify <xref:System.TimeSpan> values, see [Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="904e9-118">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="904e9-118">Child Elements</span></span>  
 <span data-ttu-id="904e9-119">Žádné</span><span class="sxs-lookup"><span data-stu-id="904e9-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="904e9-120">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="904e9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="904e9-121">Prvek</span><span class="sxs-lookup"><span data-stu-id="904e9-121">Element</span></span>|<span data-ttu-id="904e9-122">Popis</span><span class="sxs-lookup"><span data-stu-id="904e9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="904e9-123">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="904e9-123">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="904e9-124">Určuje nastavení identit na úrovni služby.</span><span class="sxs-lookup"><span data-stu-id="904e9-124">Specifies service-level identity settings.</span></span>|  
|[<span data-ttu-id="904e9-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="904e9-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="904e9-126">Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="904e9-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="904e9-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="904e9-127">Remarks</span></span>  
 <span data-ttu-id="904e9-128">A `<tokenReplayDetection>` element se dá nastavit na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužné rutiny tokenů zabezpečení v rámci `<securityTokenHandlerConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="904e9-128">A `<tokenReplayDetection>` element can be specified at the service level under the `<identityConfiguration>` element or on the security token handler collection level under the `<securityTokenHandlerConfiguration>` element.</span></span> <span data-ttu-id="904e9-129">Nastavení kolekce obslužné rutiny tokenů přepíšou nastavení zadané ve službě.</span><span class="sxs-lookup"><span data-stu-id="904e9-129">Settings on a token handler collection override those specified on the service.</span></span>  
  
 <span data-ttu-id="904e9-130">Typ mezipaměti opětovného přehrání tokenu je určená [ \<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="904e9-130">The type of the token replay cache is specified by the [\<tokenReplayCache>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md) element.</span></span>
