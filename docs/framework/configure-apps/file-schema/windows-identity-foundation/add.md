---
title: '&lt;add&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: d863a0fc2b575aceef12370a57f7f7807261cb5a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="ltaddgt"></a><span data-ttu-id="dcb04-102">&lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="dcb04-102">&lt;add&gt;</span></span>
<span data-ttu-id="dcb04-103">Obslužná rutina tokenu zabezpečení zadaný přidá do kolekce obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="dcb04-103">Adds the specified security token handler to the token handler collection.</span></span>  
  
 <span data-ttu-id="dcb04-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="dcb04-104">\<system.identityModel></span></span>  
<span data-ttu-id="dcb04-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="dcb04-105">\<identityConfiguration></span></span>  
<span data-ttu-id="dcb04-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="dcb04-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="dcb04-107">\<add></span><span class="sxs-lookup"><span data-stu-id="dcb04-107">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dcb04-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dcb04-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dcb04-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dcb04-109">Attributes and Elements</span></span>  
 <span data-ttu-id="dcb04-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dcb04-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dcb04-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="dcb04-111">Attributes</span></span>  
  
|<span data-ttu-id="dcb04-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="dcb04-112">Attribute</span></span>|<span data-ttu-id="dcb04-113">Popis</span><span class="sxs-lookup"><span data-stu-id="dcb04-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dcb04-114">– typ</span><span class="sxs-lookup"><span data-stu-id="dcb04-114">type</span></span>|<span data-ttu-id="dcb04-115">Název typu CLR obslužná rutina tokenu má být přidán.</span><span class="sxs-lookup"><span data-stu-id="dcb04-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="dcb04-116">Další informace o tom, jak zadat `type` atributů najdete v tématu [odkazy na typ vlastní](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span><span class="sxs-lookup"><span data-stu-id="dcb04-116">For more information about how to specify the `type` attribute, see [Custom Type References](http://msdn.microsoft.com/library/7286d2e3-c63d-49fd-abdc-ce2705f22c24).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dcb04-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dcb04-117">Child Elements</span></span>  
  
|<span data-ttu-id="dcb04-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="dcb04-118">Element</span></span>|<span data-ttu-id="dcb04-119">Popis</span><span class="sxs-lookup"><span data-stu-id="dcb04-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcb04-120">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="dcb04-120">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="dcb04-121">Poskytuje konfigurace <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídy, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , nebo odvozená třída buď z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="dcb04-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="dcb04-122">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="dcb04-122">\<sessionTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessiontokenrequirement.md)|<span data-ttu-id="dcb04-123">Obsahuje konfiguraci <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="dcb04-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="dcb04-124">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="dcb04-124">\<userNameSecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="dcb04-125">Obsahuje konfiguraci <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="dcb04-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="dcb04-126">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="dcb04-126">\<x509SecurityTokenHandlerRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/x509securitytokenhandlerrequirement.md)|<span data-ttu-id="dcb04-127">Poskytuje volitelné konfigurace pro <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="dcb04-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dcb04-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dcb04-128">Parent Elements</span></span>  
  
|<span data-ttu-id="dcb04-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="dcb04-129">Element</span></span>|<span data-ttu-id="dcb04-130">Popis</span><span class="sxs-lookup"><span data-stu-id="dcb04-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dcb04-131">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="dcb04-131">\<securityTokenHandlers></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|<span data-ttu-id="dcb04-132">Určuje kolekci zabezpečení tokenu rutin, které jsou registrovány koncový bod.</span><span class="sxs-lookup"><span data-stu-id="dcb04-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dcb04-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dcb04-133">Remarks</span></span>  
 <span data-ttu-id="dcb04-134">`<add>` Element může trvat jeden podřízený element, který určuje konfiguraci, aby obslužná rutina tokenu.</span><span class="sxs-lookup"><span data-stu-id="dcb04-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="dcb04-135">Toto je závislá na tom, jestli třídu obslužné rutiny odkazuje prostřednictvím `type` atribut `<add>` element poskytuje podporu pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="dcb04-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="dcb04-136">Obslužná rutina tokenu třídy, které poskytují tuto funkci musí vystavit konstruktor, který přebírá <xref:System.Xml.XmlElement> objektu.</span><span class="sxs-lookup"><span data-stu-id="dcb04-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="dcb04-137">Několik tříd obslužná rutina tokenu integrované zabezpečení zadejte tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="dcb04-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="dcb04-138">Tyto třídy jsou <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, a <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="dcb04-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="dcb04-139">Obslužná rutina tokenu kolekce může obsahovat jenom jeden obslužné rutině daného typu.</span><span class="sxs-lookup"><span data-stu-id="dcb04-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="dcb04-140">To znamená, například, pokud chcete přidat obslužnou rutinu, která je odvozená od <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> – třída do kolekce, je nutné nejprve odebrat <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, což je existuje ve výchozím nastavení, z kolekce.</span><span class="sxs-lookup"><span data-stu-id="dcb04-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="dcb04-141">Můžete použít [ \<odebrat >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) elementu, který chcete odebrat z kolekce nebo použijte jeden obslužné rutině [ \<clear >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) elementu, který chcete odebrat všechny rutiny z kolekce.</span><span class="sxs-lookup"><span data-stu-id="dcb04-141">You can use the [\<remove>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/remove.md) element to remove a single handler from the collection or use the [\<clear>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="dcb04-142">Bylo nastaveno na obslužnou rutinu přepsat ekvivalentní nastavení zadané v kolekci obslužná rutina tokenu v [ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) elementu a uvedenými na úrovni služby, v části [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span><span class="sxs-lookup"><span data-stu-id="dcb04-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dcb04-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="dcb04-143">Example</span></span>  
 <span data-ttu-id="dcb04-144">Následující kód XML ukazuje použití `<add>` a `<remove>` elementy nahradit výchozí obslužnou rutinu tokenu relace obslužnou rutinu tokenu vlastní relaci.</span><span class="sxs-lookup"><span data-stu-id="dcb04-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="dcb04-145">Soubor XML je převzat ze `ClaimsAwareWebFarm` ukázka.</span><span class="sxs-lookup"><span data-stu-id="dcb04-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
