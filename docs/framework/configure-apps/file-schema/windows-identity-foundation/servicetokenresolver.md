---
title: '&lt;serviceTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: c25ea1fc32c93e7eb57ef8ed06d6f786ae0a670e
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltservicetokenresolvergt"></a><span data-ttu-id="e0601-102">&lt;serviceTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="e0601-102">&lt;serviceTokenResolver&gt;</span></span>
<span data-ttu-id="e0601-103">Zaregistruje překladač tokenu služby, který je používán obslužné rutiny v kolekci obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="e0601-103">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="e0601-104">Překladač tokenu služby se používá k překladu šifrování tokenu na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="e0601-104">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="e0601-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e0601-105">\<system.identityModel></span></span>  
<span data-ttu-id="e0601-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e0601-106">\<identityConfiguration></span></span>  
<span data-ttu-id="e0601-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="e0601-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e0601-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e0601-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="e0601-109">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="e0601-109">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e0601-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="e0601-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <serviceTokenResolver type=xs:string>  
        </serviceTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e0601-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="e0601-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e0601-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="e0601-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e0601-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="e0601-113">Attributes</span></span>  
  
|<span data-ttu-id="e0601-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="e0601-114">Attribute</span></span>|<span data-ttu-id="e0601-115">Popis</span><span class="sxs-lookup"><span data-stu-id="e0601-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e0601-116">– typ</span><span class="sxs-lookup"><span data-stu-id="e0601-116">type</span></span>|<span data-ttu-id="e0601-117">Určuje typ tokenu překladače služby.</span><span class="sxs-lookup"><span data-stu-id="e0601-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="e0601-118">Buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typu nebo typu, která je odvozena z <xref:System.IdentityModel.Selectors.SecurityTokenResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="e0601-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="e0601-119">Další informace o tom, jak zadat `type` atributů najdete v tématu [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="e0601-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="e0601-120">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="e0601-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e0601-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="e0601-121">Child Elements</span></span>  
 <span data-ttu-id="e0601-122">Žádné</span><span class="sxs-lookup"><span data-stu-id="e0601-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e0601-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="e0601-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e0601-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="e0601-124">Element</span></span>|<span data-ttu-id="e0601-125">Popis</span><span class="sxs-lookup"><span data-stu-id="e0601-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e0601-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="e0601-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="e0601-127">Poskytuje konfigurace pro kolekci zabezpečení tokenu obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="e0601-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e0601-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="e0601-128">Remarks</span></span>  
 <span data-ttu-id="e0601-129">Překladač tokenu služby lze použít k vyřešení šifrování tokenu na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="e0601-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="e0601-130">Umožňuje načíst klíč, který se má použít k dešifrování tokenů, příchozí.</span><span class="sxs-lookup"><span data-stu-id="e0601-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="e0601-131">Je nutné zadat `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="e0601-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="e0601-132">Zadaný typ může být buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> nebo vlastního typu, který je odvozen od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="e0601-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="e0601-133">Některé tokenu obslužné rutiny umožňují určit nastavení tokenu překladače služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="e0601-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="e0601-134">Nastavení na jednotlivých tokenu obslužné rutiny potlačit platformám zadaným v kolekci obslužná rutina tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="e0601-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e0601-135">Určení `<serviceTokenResolver>` prvku jako podřízeného prvku [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu se už nepoužívá, ale je stále podporováno pro zpětnou kompatibilitu.</span><span class="sxs-lookup"><span data-stu-id="e0601-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="e0601-136">Nastavení na `<securityTokenHandlerConfiguration>` element přepíšou na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="e0601-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e0601-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="e0601-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
