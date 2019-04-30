---
title: <serviceTokenResolver>
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: 1143717882652fc8a03947327b5f1ea89dde7373
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61793806"
---
# <a name="servicetokenresolver"></a><span data-ttu-id="cab0d-101">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="cab0d-101">\<serviceTokenResolver></span></span>
<span data-ttu-id="cab0d-102">Zaregistruje překladač tokenů služby, který se používá obslužné rutiny v kolekci obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="cab0d-102">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="cab0d-103">Překladač tokenů služby se používá k překladu šifrování tokenu na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="cab0d-103">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="cab0d-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="cab0d-104">\<system.identityModel></span></span>  
<span data-ttu-id="cab0d-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="cab0d-105">\<identityConfiguration></span></span>  
<span data-ttu-id="cab0d-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="cab0d-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="cab0d-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="cab0d-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="cab0d-108">\<serviceTokenResolver></span><span class="sxs-lookup"><span data-stu-id="cab0d-108">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cab0d-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="cab0d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cab0d-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="cab0d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="cab0d-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="cab0d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cab0d-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="cab0d-112">Attributes</span></span>  
  
|<span data-ttu-id="cab0d-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="cab0d-113">Attribute</span></span>|<span data-ttu-id="cab0d-114">Popis</span><span class="sxs-lookup"><span data-stu-id="cab0d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="cab0d-115"> – typ</span><span class="sxs-lookup"><span data-stu-id="cab0d-115">type</span></span>|<span data-ttu-id="cab0d-116">Určuje typ služby překladač tokenů.</span><span class="sxs-lookup"><span data-stu-id="cab0d-116">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="cab0d-117">Buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typ nebo typ, který je odvozen od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="cab0d-117">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="cab0d-118">Další informace o tom, jak zadat `type` atributu naleznete v tématu [vlastní typ reference].</span><span class="sxs-lookup"><span data-stu-id="cab0d-118">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="cab0d-119">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="cab0d-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cab0d-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="cab0d-120">Child Elements</span></span>  
 <span data-ttu-id="cab0d-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="cab0d-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cab0d-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="cab0d-122">Parent Elements</span></span>  
  
|<span data-ttu-id="cab0d-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="cab0d-123">Element</span></span>|<span data-ttu-id="cab0d-124">Popis</span><span class="sxs-lookup"><span data-stu-id="cab0d-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cab0d-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="cab0d-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="cab0d-126">Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="cab0d-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cab0d-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="cab0d-127">Remarks</span></span>  
 <span data-ttu-id="cab0d-128">Překladač tokenů služby lze použít k vyřešení šifrování tokenu na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="cab0d-128">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="cab0d-129">Používá se k načtení klíče, který se má použít k dešifrování příchozí tokeny.</span><span class="sxs-lookup"><span data-stu-id="cab0d-129">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="cab0d-130">Je nutné zadat `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="cab0d-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="cab0d-131">Zadaný typ může být buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> nebo vlastní typ, který je odvozen od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="cab0d-131">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="cab0d-132">Některé obslužné rutiny tokenů vám umožňují určit nastavení překladač tokenů služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="cab0d-132">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="cab0d-133">Nastavení na jednotlivých obslužné rutiny tokenů přepsání zadaná v kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="cab0d-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cab0d-134">Zadání `<serviceTokenResolver>` prvek jako podřízený prvek [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) prvek se už nepoužívá, ale je z důvodu zpětné kompatibility stále podporována.</span><span class="sxs-lookup"><span data-stu-id="cab0d-134">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="cab0d-135">Nastavení `<securityTokenHandlerConfiguration>` element mají přednost před akcemi na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="cab0d-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cab0d-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="cab0d-136">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
