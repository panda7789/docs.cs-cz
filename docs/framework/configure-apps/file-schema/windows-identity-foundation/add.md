---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 83ba51cbbd5100bf7412f9914a270cac88f7faa1
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "73973806"
---
# \<add>
<span data-ttu-id="810ac-101">Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="810ac-101">Adds the specified security token handler to the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="810ac-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="810ac-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="810ac-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="810ac-103">Attributes and Elements</span></span>  
 <span data-ttu-id="810ac-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="810ac-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="810ac-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="810ac-105">Attributes</span></span>  
  
|<span data-ttu-id="810ac-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="810ac-106">Attribute</span></span>|<span data-ttu-id="810ac-107">Popis</span><span class="sxs-lookup"><span data-stu-id="810ac-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="810ac-108">typ</span><span class="sxs-lookup"><span data-stu-id="810ac-108">type</span></span>|<span data-ttu-id="810ac-109">Název typu CLR obslužné rutiny tokenu, která má být přidána.</span><span class="sxs-lookup"><span data-stu-id="810ac-109">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="810ac-110">Další informace o tom, jak zadat `type` atribut, naleznete v tématu [odkazy na vlastní typ](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="810ac-110">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="810ac-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="810ac-111">Child Elements</span></span>  
  
|<span data-ttu-id="810ac-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="810ac-112">Element</span></span>|<span data-ttu-id="810ac-113">Description</span><span class="sxs-lookup"><span data-stu-id="810ac-113">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="810ac-114">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídu, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídu nebo odvozenou třídu některé z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="810ac-114">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[\<sessionTokenRequirement>](sessiontokenrequirement.md)|<span data-ttu-id="810ac-115">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="810ac-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<userNameSecurityTokenHandlerRequirement>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="810ac-116">Poskytuje konfiguraci pro <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="810ac-116">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[\<x509SecurityTokenHandlerRequirement>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="810ac-117">Poskytuje volitelnou konfiguraci pro <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="810ac-117">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="810ac-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="810ac-118">Parent Elements</span></span>  
  
|<span data-ttu-id="810ac-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="810ac-119">Element</span></span>|<span data-ttu-id="810ac-120">Description</span><span class="sxs-lookup"><span data-stu-id="810ac-120">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlers>](securitytokenhandlers.md)|<span data-ttu-id="810ac-121">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="810ac-121">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="810ac-122">Poznámky</span><span class="sxs-lookup"><span data-stu-id="810ac-122">Remarks</span></span>  
 <span data-ttu-id="810ac-123">`<add>`Element může převzít jeden podřízený prvek, který určuje konfiguraci pro obslužnou rutinu tokenu.</span><span class="sxs-lookup"><span data-stu-id="810ac-123">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="810ac-124">To závisí na tom, zda třída obslužné rutiny, na kterou odkazuje `type` atribut `<add>` elementu, poskytuje podporu pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="810ac-124">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="810ac-125">Třídy obslužné rutiny tokenu, které poskytují tuto funkci, musí vystavit konstruktor, který přebírá <xref:System.Xml.XmlElement> objekt.</span><span class="sxs-lookup"><span data-stu-id="810ac-125">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  

```csharp  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="810ac-126">Tuto funkci poskytují některé z vestavěných tříd obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="810ac-126">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="810ac-127">Tyto třídy jsou <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> , <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> ,, a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> .</span><span class="sxs-lookup"><span data-stu-id="810ac-127">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="810ac-128">Kolekce obslužných rutin tokenů může obsahovat pouze jednu obslužnou rutinu pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="810ac-128">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="810ac-129">To znamená, že pokud chcete přidat obslužnou rutinu, která je odvozena od <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídy do kolekce, musíte nejprve <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> z kolekce odebrat, která je ve výchozím nastavení přítomna.</span><span class="sxs-lookup"><span data-stu-id="810ac-129">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="810ac-130">Pomocí [\<remove>](remove.md) elementu můžete odebrat jednu obslužnou rutinu z kolekce nebo použít [\<clear>](clear.md) element k odebrání všech obslužných rutin z kolekce.</span><span class="sxs-lookup"><span data-stu-id="810ac-130">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="810ac-131">Nastavení zadané u obslužné rutiny přepište ekvivalentní nastavení zadaná v kolekci obslužných rutin tokenu v rámci [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) elementu a na úrovni služby určené v rámci [\<identityConfiguration>](identityconfiguration.md) elementu.</span><span class="sxs-lookup"><span data-stu-id="810ac-131">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="810ac-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="810ac-132">Example</span></span>  
 <span data-ttu-id="810ac-133">Následující kód XML ukazuje použití `<add>` `<remove>` elementů a k nahrazení výchozí obslužné rutiny tokenu relace vlastní obslužnou rutinou tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="810ac-133">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="810ac-134">KÓD XML je získán z `ClaimsAwareWebFarm` ukázky.</span><span class="sxs-lookup"><span data-stu-id="810ac-134">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
