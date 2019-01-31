---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: cb88d2a37740cf439f4fd2aa0f7fe4c098da1cf2
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55269754"
---
# <a name="add"></a><span data-ttu-id="f3941-101">\<add></span><span class="sxs-lookup"><span data-stu-id="f3941-101">\<add></span></span>
<span data-ttu-id="f3941-102">Přidá obslužnou rutinu tokenu zabezpečení do kolekce obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="f3941-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
 <span data-ttu-id="f3941-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f3941-103">\<system.identityModel></span></span>  
<span data-ttu-id="f3941-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f3941-104">\<identityConfiguration></span></span>  
<span data-ttu-id="f3941-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="f3941-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="f3941-106">\<add></span><span class="sxs-lookup"><span data-stu-id="f3941-106">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3941-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f3941-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type=xs:string>  
        <optionalConfigurationElement>  
        </optionalConfigurationElement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3941-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f3941-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f3941-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f3941-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3941-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="f3941-110">Attributes</span></span>  
  
|<span data-ttu-id="f3941-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="f3941-111">Attribute</span></span>|<span data-ttu-id="f3941-112">Popis</span><span class="sxs-lookup"><span data-stu-id="f3941-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3941-113">– typ</span><span class="sxs-lookup"><span data-stu-id="f3941-113">type</span></span>|<span data-ttu-id="f3941-114">Název typu CLR přidat obslužnou rutinu tokenu.</span><span class="sxs-lookup"><span data-stu-id="f3941-114">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="f3941-115">Další informace o tom, jak zadat `type` atributu naleznete v tématu [odkazů na vlastní typy](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="f3941-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3941-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f3941-116">Child Elements</span></span>  
  
|<span data-ttu-id="f3941-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3941-117">Element</span></span>|<span data-ttu-id="f3941-118">Popis</span><span class="sxs-lookup"><span data-stu-id="f3941-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3941-119">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="f3941-119">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="f3941-120">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo z odvozené třídy kterékoli z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="f3941-120">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="f3941-121">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="f3941-121">\<sessionTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|<span data-ttu-id="f3941-122">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídy nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="f3941-122">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="f3941-123">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="f3941-123">\<userNameSecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="f3941-124">Poskytuje konfiguraci pro <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> třídy nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="f3941-124">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="f3941-125">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="f3941-125">\<x509SecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|<span data-ttu-id="f3941-126">Poskytuje volitelné konfigurace pro <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> třídy nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="f3941-126">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f3941-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f3941-127">Parent Elements</span></span>  
  
|<span data-ttu-id="f3941-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="f3941-128">Element</span></span>|<span data-ttu-id="f3941-129">Popis</span><span class="sxs-lookup"><span data-stu-id="f3941-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3941-130">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="f3941-130">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="f3941-131">Určuje kolekci obslužné rutiny tokenů zabezpečení, které jsou registrované na koncový bod.</span><span class="sxs-lookup"><span data-stu-id="f3941-131">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3941-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f3941-132">Remarks</span></span>  
 <span data-ttu-id="f3941-133">`<add>` Element může trvat jeden podřízený prvek, který určuje konfiguraci pro obslužnou rutinu tokenu.</span><span class="sxs-lookup"><span data-stu-id="f3941-133">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="f3941-134">Toto je závislá na Určuje, zda třída obslužné rutiny odkazuje prostřednictvím `type` atribut `<add>` element poskytuje podporu pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="f3941-134">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="f3941-135">Třídy obslužné rutiny tokenů, které poskytují tuto funkci musí vystavit konstruktor, který přebírá <xref:System.Xml.XmlElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="f3941-135">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="f3941-136">Několik tříd obslužné rutiny tokenů integrované zabezpečení poskytují tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="f3941-136">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="f3941-137">Tyto třídy jsou <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, a <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="f3941-137">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="f3941-138">Obslužná rutina tokenů kolekce může obsahovat jenom jedna obslužná rutina daného typu.</span><span class="sxs-lookup"><span data-stu-id="f3941-138">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="f3941-139">To znamená, například, že pokud chcete přidat obslužnou rutinu, která je odvozena z <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídy do kolekce, musíte nejdřív odebrat <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, což je k dispozici ve výchozím nastavení, z kolekce.</span><span class="sxs-lookup"><span data-stu-id="f3941-139">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="f3941-140">Můžete použít [ \<odebrat >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) prvek, který chcete odebrat z kolekce nebo použití jedna obslužná rutina [ \<vymazat >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) prvek, který chcete odebrat všechny obslužné rutiny z kolekce.</span><span class="sxs-lookup"><span data-stu-id="f3941-140">You can use the [\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) element to remove a single handler from the collection or use the [\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="f3941-141">Bylo nastaveno na obslužnou rutinu přepsat ekvivalentní nastavení zadané v kolekci obslužné rutiny tokenů v části [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element a jsou uvedeny na úrovni služby v části [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="f3941-141">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f3941-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="f3941-142">Example</span></span>  
 <span data-ttu-id="f3941-143">Následující kód XML ukazuje použití `<add>` a `<remove>` prvků, které mají výchozí obslužnou rutinu tokenu relace nahraďte obslužnou rutinu tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="f3941-143">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="f3941-144">XML je převzata z `ClaimsAwareWebFarm` vzorku.</span><span class="sxs-lookup"><span data-stu-id="f3941-144">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
