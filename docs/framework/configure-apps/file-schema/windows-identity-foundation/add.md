---
title: <add>
ms.date: 03/30/2017
ms.assetid: 4712a888-f154-4395-8887-ef14a88a6497
author: BrucePerlerMS
ms.openlocfilehash: 9505970c1fd7fcdfe62d3c6ef58f5d653fab4106
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69941998"
---
# <a name="add"></a><span data-ttu-id="5384f-101">\<add></span><span class="sxs-lookup"><span data-stu-id="5384f-101">\<add></span></span>
<span data-ttu-id="5384f-102">Přidá do kolekce obslužných rutin tokenu zadanou obslužnou rutinu tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5384f-102">Adds the specified security token handler to the token handler collection.</span></span>  
  
 <span data-ttu-id="5384f-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="5384f-103">\<system.identityModel></span></span>  
<span data-ttu-id="5384f-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="5384f-104">\<identityConfiguration></span></span>  
<span data-ttu-id="5384f-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="5384f-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="5384f-106">\<add></span><span class="sxs-lookup"><span data-stu-id="5384f-106">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5384f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="5384f-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5384f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="5384f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="5384f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="5384f-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5384f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="5384f-110">Attributes</span></span>  
  
|<span data-ttu-id="5384f-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="5384f-111">Attribute</span></span>|<span data-ttu-id="5384f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="5384f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5384f-113">– typ</span><span class="sxs-lookup"><span data-stu-id="5384f-113">type</span></span>|<span data-ttu-id="5384f-114">Název typu CLR obslužné rutiny tokenu, která má být přidána.</span><span class="sxs-lookup"><span data-stu-id="5384f-114">The CLR type name of the token handler to be added.</span></span> <span data-ttu-id="5384f-115">Další informace o tom, jak zadat `type` atribut, naleznete v tématu odkazy na [vlastní typ](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span><span class="sxs-lookup"><span data-stu-id="5384f-115">For more information about how to specify the `type` attribute, see [Custom Type References](https://docs.microsoft.com/previous-versions/windows-identity-foundation/gg638728(v=msdn.10)#custom-type-references).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5384f-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="5384f-116">Child Elements</span></span>  
  
|<span data-ttu-id="5384f-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="5384f-117">Element</span></span>|<span data-ttu-id="5384f-118">Popis</span><span class="sxs-lookup"><span data-stu-id="5384f-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5384f-119">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="5384f-119">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="5384f-120">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> třídu <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> , třídu nebo odvozenou třídu některé z těchto tříd.</span><span class="sxs-lookup"><span data-stu-id="5384f-120">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
|[<span data-ttu-id="5384f-121">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="5384f-121">\<sessionTokenRequirement></span></span>](sessiontokenrequirement.md)|<span data-ttu-id="5384f-122">Poskytuje konfiguraci pro <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="5384f-122">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="5384f-123">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="5384f-123">\<userNameSecurityTokenHandlerRequirement></span></span>](usernamesecuritytokenhandlerrequirement.md)|<span data-ttu-id="5384f-124">Poskytuje konfiguraci pro <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="5384f-124">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>|  
|[<span data-ttu-id="5384f-125">\<x509SecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="5384f-125">\<x509SecurityTokenHandlerRequirement></span></span>](x509securitytokenhandlerrequirement.md)|<span data-ttu-id="5384f-126">Poskytuje volitelnou konfiguraci pro <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> třídu nebo odvozené třídy.</span><span class="sxs-lookup"><span data-stu-id="5384f-126">Provides optional configuration for the <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> class or derived classes.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="5384f-127">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="5384f-127">Parent Elements</span></span>  
  
|<span data-ttu-id="5384f-128">Prvek</span><span class="sxs-lookup"><span data-stu-id="5384f-128">Element</span></span>|<span data-ttu-id="5384f-129">Popis</span><span class="sxs-lookup"><span data-stu-id="5384f-129">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5384f-130">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="5384f-130">\<securityTokenHandlers></span></span>](securitytokenhandlers.md)|<span data-ttu-id="5384f-131">Určuje kolekci obslužných rutin tokenů zabezpečení, které jsou registrovány u koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="5384f-131">Specifies a collection of security token handlers that are registered with the endpoint.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="5384f-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5384f-132">Remarks</span></span>  
 <span data-ttu-id="5384f-133">`<add>` Element může převzít jeden podřízený prvek, který určuje konfiguraci pro obslužnou rutinu tokenu.</span><span class="sxs-lookup"><span data-stu-id="5384f-133">The `<add>` element can take a single child element that specifies the configuration for the token handler.</span></span> <span data-ttu-id="5384f-134">To závisí na tom, zda třída obslužné rutiny, `type` na kterou odkazuje `<add>` atribut elementu, poskytuje podporu pro tuto funkci.</span><span class="sxs-lookup"><span data-stu-id="5384f-134">This is dependent on whether the handler class referenced through the `type` attribute of the `<add>` element provides support for this feature.</span></span> <span data-ttu-id="5384f-135">Třídy obslužné rutiny tokenu, které poskytují tuto funkci, musí vystavit konstruktor, který přebírá <xref:System.Xml.XmlElement> objekt.</span><span class="sxs-lookup"><span data-stu-id="5384f-135">Token handler classes that provide this feature must expose a constructor that takes an <xref:System.Xml.XmlElement> object.</span></span>  
  
```  
public class CustomTokenHandler : Microsoft.IdentityModel.Tokens.SecurityTokenHandler  
{  
    public CustomTokenHandler( XmlElement customConfig )  
    {  
    }  
}  
```  
  
 <span data-ttu-id="5384f-136">Tuto funkci poskytují některé z vestavěných tříd obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="5384f-136">Several of the built-in security token handler classes do provide this functionality.</span></span> <span data-ttu-id="5384f-137">Tyto třídy jsou <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, a .<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler></span><span class="sxs-lookup"><span data-stu-id="5384f-137">These classes are <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>, <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler>, and <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>.</span></span>  
  
> [!IMPORTANT]
> <span data-ttu-id="5384f-138">Kolekce obslužných rutin tokenů může obsahovat pouze jednu obslužnou rutinu pro daný typ.</span><span class="sxs-lookup"><span data-stu-id="5384f-138">The token handler collection can only contain a single handler of any given type.</span></span> <span data-ttu-id="5384f-139">To znamená, že pokud chcete přidat obslužnou rutinu, která je odvozena od <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> třídy do kolekce, musíte nejprve z kolekce <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>odebrat, která je ve výchozím nastavení přítomna.</span><span class="sxs-lookup"><span data-stu-id="5384f-139">This means, for example, that if you want to add a handler that is derived from the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class to the collection, you must first remove the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>, which is present by default, from the collection.</span></span> <span data-ttu-id="5384f-140">[ Pomocí\<elementu Remove >](remove.md) můžete z [ \<](clear.md) kolekce odebrat jednu obslužnou rutinu nebo pomocí elementu Clear > odebrat všechny obslužné rutiny z kolekce.</span><span class="sxs-lookup"><span data-stu-id="5384f-140">You can use the [\<remove>](remove.md) element to remove a single handler from the collection or use the [\<clear>](clear.md) element to remove all handlers from the collection.</span></span>  
  
 <span data-ttu-id="5384f-141">Nastavení zadané u obslužné rutiny přepište ekvivalentní nastavení zadaná v kolekci obslužných rutin [ \<](securitytokenhandlerconfiguration.md) tokenu pod elementem > securityTokenHandlerConfiguration a na úrovni služby zadané v [ \< části identityConfiguration prvek >](identityconfiguration.md) .</span><span class="sxs-lookup"><span data-stu-id="5384f-141">Settings specified on a handler override equivalent settings specified on the token handler collection under the [\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md) element and those specified at the service-level under the [\<identityConfiguration>](identityconfiguration.md) element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5384f-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="5384f-142">Example</span></span>  
 <span data-ttu-id="5384f-143">Následující kód XML ukazuje použití `<add>` elementů a `<remove>` k nahrazení výchozí obslužné rutiny tokenu relace vlastní obslužnou rutinou tokenu relace.</span><span class="sxs-lookup"><span data-stu-id="5384f-143">The following XML shows the use of the `<add>` and `<remove>` elements to replace the default session token handler with a custom session token handler.</span></span> <span data-ttu-id="5384f-144">Kód XML je získán z `ClaimsAwareWebFarm` ukázky.</span><span class="sxs-lookup"><span data-stu-id="5384f-144">The XML is taken from the `ClaimsAwareWebFarm` sample.</span></span>  
  
```xml  
<securityTokenHandlers>  
  <remove type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
  <add type="System.IdentityModel.Services.Tokens.MachineKeySessionSecurityTokenHandler, System.IdentityModel.Services, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" />  
</securityTokenHandlers>  
```
