---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 83ba51cbbd5100bf7412f9914a270cac88f7faa1
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73973806"
---
# <a name="add"></a><span data-ttu-id="d3605-101">\<přidat ></span><span class="sxs-lookup"><span data-stu-id="d3605-101">\<add></span></span>
<span data-ttu-id="d3605-102">Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d3605-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
<span data-ttu-id="d3605-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="d3605-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d3605-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="d3605-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="d3605-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d3605-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="d3605-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="d3605-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="d3605-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<přidat >**</span><span class="sxs-lookup"><span data-stu-id="d3605-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3605-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3605-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3605-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d3605-109">Attributes and Elements</span></span>  
 <span data-ttu-id="d3605-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d3605-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3605-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="d3605-111">Attributes</span></span>  
  
|<span data-ttu-id="d3605-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="d3605-112">Attribute</span></span>|<span data-ttu-id="d3605-113">Popis</span><span class="sxs-lookup"><span data-stu-id="d3605-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d3605-114">– typ</span><span class="sxs-lookup"><span data-stu-id="d3605-114">type</span></span>|<span data-ttu-id="d3605-115">Název typu CLR obslužné rutiny tokenu, která má být přidána.</span><span class="sxs-lookup"><span data-stu-id="d3605-115">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="d3605-116">Další informace o tom, jak zadat atribut `type`, naleznete v tématu [odkazy na vlastní typ](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="d3605-116">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3605-117">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d3605-117">Child Elements</span></span>  
  
|<span data-ttu-id="d3605-118">Prvek</span><span class="sxs-lookup"><span data-stu-id="d3605-118">Element</span></span>|<span data-ttu-id="d3605-119">Popis</span><span class="sxs-lookup"><span data-stu-id="d3605-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3605-120">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="d3605-120">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="d3605-121">Poskytuje konfiguraci pro třídu <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo odvozenou třídu některé z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="d3605-121">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="d3605-122">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="d3605-122">\<sessionTokenRequirement></span></span>](sessiontokenrequirement.md)|<span data-ttu-id="d3605-123">Poskytuje konfiguraci pro třídu <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="d3605-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="d3605-124">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="d3605-124">\<userNameSecurityTokenHandlerRequirement></span></span>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="d3605-125">Poskytuje konfiguraci pro třídu <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="d3605-125">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="d3605-126">\<x509SecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="d3605-126">\<x509SecurityTokenHandlerRequirement></span></span>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="d3605-127">Poskytuje volitelnou konfiguraci pro třídu <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="d3605-127">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3605-128">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d3605-128">Parent Elements</span></span>  
  
|<span data-ttu-id="d3605-129">Prvek</span><span class="sxs-lookup"><span data-stu-id="d3605-129">Element</span></span>|<span data-ttu-id="d3605-130">Popis</span><span class="sxs-lookup"><span data-stu-id="d3605-130">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3605-131">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="d3605-131">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="d3605-132">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="d3605-132">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3605-133">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3605-133">Remarks</span></span>  
 <span data-ttu-id="d3605-134">Element `<add>` může převzít jeden podřízený prvek, který určuje konfiguraci pro obslužnou rutinu tokenu.</span><span class="sxs-lookup"><span data-stu-id="d3605-134">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="d3605-135">To závisí na tom, zda třída obslužné rutiny, na kterou odkazuje atribut `type` elementu `<add>`, poskytuje podporu pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="d3605-135">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="d3605-136">Třídy obslužné rutiny tokenu, které poskytují tuto funkci, musí vystavit konstruktor, který přebírá objekt <xref:System.Xml.XmlElement>.</span><span class="sxs-lookup"><span data-stu-id="d3605-136">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="d3605-137">Tuto funkci poskytují některé z vestavěných tříd obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="d3605-137">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="d3605-138">Tyto třídy jsou <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>a <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span><span class="sxs-lookup"><span data-stu-id="d3605-138">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="d3605-139">Kolekce obslužných rutin tokenů může obsahovat pouze jednu obslužnou rutinu pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="d3605-139">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="d3605-140">To znamená, že pokud chcete přidat obslužnou rutinu, která je odvozena od třídy <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> do kolekce, je nutné nejprve odebrat <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, která je ve výchozím nastavení přítomna, z kolekce.</span><span class="sxs-lookup"><span data-stu-id="d3605-140">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="d3605-141">Pomocí elementu [\<remove >](remove.md) můžete z kolekce odebrat jednu obslužnou rutinu nebo pomocí elementu [\<vymazat >](clear.md) odstranit všechny obslužné rutiny z kolekce.</span><span class="sxs-lookup"><span data-stu-id="d3605-141">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="d3605-142">Nastavení zadané u obslužné rutiny přepište ekvivalentní nastavení zadaná v kolekci obslužných rutin tokenu v rámci [\<securityTokenHandlerConfiguration >](securitytokenhandlerconfiguration.md) elementu a na úrovni služby v rámci elementu [\<IdentityConfiguration >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="d3605-142">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3605-143">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3605-143">Example</span></span>  
 <span data-ttu-id="d3605-144">Následující kód XML ukazuje použití prvků `<add>` a `<remove>` k nahrazení výchozí obslužné rutiny tokenu relace s vlastní obslužnou rutinou tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="d3605-144">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="d3605-145">KÓD XML je pořízen z ukázky `ClaimsAwareWebFarm`.</span><span class="sxs-lookup"><span data-stu-id="d3605-145">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
