---
title: '&lt;serviceTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: 6e9001e1-e064-4f47-84b2-46225c177746
author: BrucePerlerMS
ms.openlocfilehash: d4b64e2c88e153834b7cf5a83bd6258b6dfd471f
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/29/2018
ms.locfileid: "47454286"
---
# <a name="ltservicetokenresolvergt"></a><span data-ttu-id="1c4c0-102">&lt;serviceTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="1c4c0-102">&lt;serviceTokenResolver&gt;</span></span>
<span data-ttu-id="1c4c0-103">Zaregistruje překladač tokenů služby, který se používá obslužné rutiny v kolekci obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-103">Registers the service token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="1c4c0-104">Překladač tokenů služby se používá k překladu šifrování tokenu na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-104">The service token resolver is used to resolve the encryption token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="1c4c0-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1c4c0-105">\<system.identityModel></span></span>  
<span data-ttu-id="1c4c0-106">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1c4c0-106">\<identityConfiguration></span></span>  
<span data-ttu-id="1c4c0-107">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="1c4c0-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="1c4c0-108">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1c4c0-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="1c4c0-109">\<serviceTokenResolver ></span><span class="sxs-lookup"><span data-stu-id="1c4c0-109">\<serviceTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1c4c0-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1c4c0-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1c4c0-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1c4c0-111">Attributes and Elements</span></span>  
 <span data-ttu-id="1c4c0-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1c4c0-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="1c4c0-113">Attributes</span></span>  
  
|<span data-ttu-id="1c4c0-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="1c4c0-114">Attribute</span></span>|<span data-ttu-id="1c4c0-115">Popis</span><span class="sxs-lookup"><span data-stu-id="1c4c0-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1c4c0-116">– typ</span><span class="sxs-lookup"><span data-stu-id="1c4c0-116">type</span></span>|<span data-ttu-id="1c4c0-117">Určuje typ služby překladač tokenů.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-117">Specifies the type of the service token resolver.</span></span> <span data-ttu-id="1c4c0-118">Buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> typ nebo typ, který je odvozen od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-118">Either the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> type or a type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span> <span data-ttu-id="1c4c0-119">Další informace o tom, jak zadat `type` atributu naleznete v tématu [vlastní typ reference].</span><span class="sxs-lookup"><span data-stu-id="1c4c0-119">For more information about how to specify the `type` attribute, see [Custom Type References].</span></span> <span data-ttu-id="1c4c0-120">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1c4c0-121">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1c4c0-121">Child Elements</span></span>  
 <span data-ttu-id="1c4c0-122">Žádná</span><span class="sxs-lookup"><span data-stu-id="1c4c0-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1c4c0-123">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1c4c0-123">Parent Elements</span></span>  
  
|<span data-ttu-id="1c4c0-124">Prvek</span><span class="sxs-lookup"><span data-stu-id="1c4c0-124">Element</span></span>|<span data-ttu-id="1c4c0-125">Popis</span><span class="sxs-lookup"><span data-stu-id="1c4c0-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1c4c0-126">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1c4c0-126">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="1c4c0-127">Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-127">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1c4c0-128">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1c4c0-128">Remarks</span></span>  
 <span data-ttu-id="1c4c0-129">Překladač tokenů služby lze použít k vyřešení šifrování tokenu na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-129">The service token resolver can be used to resolve the encryption token on incoming tokens and messages.</span></span> <span data-ttu-id="1c4c0-130">Používá se k načtení klíče, který se má použít k dešifrování příchozí tokeny.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-130">It is used to retrieve the key that should be used to decrypt incoming tokens.</span></span> <span data-ttu-id="1c4c0-131">Je nutné zadat `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-131">You must specify the `type` attribute.</span></span> <span data-ttu-id="1c4c0-132">Zadaný typ může být buď <xref:System.IdentityModel.Selectors.SecurityTokenResolver> nebo vlastní typ, který je odvozen od <xref:System.IdentityModel.Selectors.SecurityTokenResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-132">The type specified can be either <xref:System.IdentityModel.Selectors.SecurityTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Selectors.SecurityTokenResolver> class.</span></span>  
  
 <span data-ttu-id="1c4c0-133">Některé obslužné rutiny tokenů vám umožňují určit nastavení překladač tokenů služby v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-133">Some token handlers allow you to specify service token resolver settings in configuration.</span></span> <span data-ttu-id="1c4c0-134">Nastavení na jednotlivých obslužné rutiny tokenů přepsání zadaná v kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-134">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1c4c0-135">Zadání `<serviceTokenResolver>` prvek jako podřízený prvek [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) prvek se už nepoužívá, ale je z důvodu zpětné kompatibility stále podporována.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-135">Specifying the `<serviceTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="1c4c0-136">Nastavení `<securityTokenHandlerConfiguration>` element mají přednost před akcemi na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="1c4c0-136">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1c4c0-137">Příklad</span><span class="sxs-lookup"><span data-stu-id="1c4c0-137">Example</span></span>  
  
```xml  
<serviceTokenResolver type="MyNamespace.CustomTokenResolver, MyAssembly" />  
```
