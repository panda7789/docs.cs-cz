---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152668"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="b09aa-101">\<> překladače tokenu</span><span class="sxs-lookup"><span data-stu-id="b09aa-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="b09aa-102">Registruje překladač tokenů vystavitelů, který používají obslužné rutiny v kolekci obslužné rutiny tokenu.</span><span class="sxs-lookup"><span data-stu-id="b09aa-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="b09aa-103">Překladač tokenů vystavithonu se používá k vyřešení podpisového tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="b09aa-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="b09aa-104">[**\<>konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b09aa-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b09aa-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="b09aa-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="b09aa-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="b09aa-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="b09aa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="b09aa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="b09aa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="b09aa-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="b09aa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>překladače tokenu**</span><span class="sxs-lookup"><span data-stu-id="b09aa-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b09aa-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b09aa-110">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerTokenResolver type=xs:string>  
        </issuerTokenResolver>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b09aa-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b09aa-111">Attributes and Elements</span></span>  
 <span data-ttu-id="b09aa-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="b09aa-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b09aa-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="b09aa-113">Attributes</span></span>  
  
|<span data-ttu-id="b09aa-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="b09aa-114">Attribute</span></span>|<span data-ttu-id="b09aa-115">Popis</span><span class="sxs-lookup"><span data-stu-id="b09aa-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b09aa-116">type</span><span class="sxs-lookup"><span data-stu-id="b09aa-116">type</span></span>|<span data-ttu-id="b09aa-117">Určuje typ překládání tokenů vystavitenu.</span><span class="sxs-lookup"><span data-stu-id="b09aa-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="b09aa-118">Musí být <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třída nebo typ, který <xref:System.IdentityModel.Tokens.IssuerTokenResolver> je odvozen z třídy.</span><span class="sxs-lookup"><span data-stu-id="b09aa-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="b09aa-119">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="b09aa-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b09aa-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b09aa-120">Child Elements</span></span>  
 <span data-ttu-id="b09aa-121">Žádný</span><span class="sxs-lookup"><span data-stu-id="b09aa-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b09aa-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b09aa-122">Parent Elements</span></span>  
  
|<span data-ttu-id="b09aa-123">Element</span><span class="sxs-lookup"><span data-stu-id="b09aa-123">Element</span></span>|<span data-ttu-id="b09aa-124">Popis</span><span class="sxs-lookup"><span data-stu-id="b09aa-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b09aa-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="b09aa-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="b09aa-126">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b09aa-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b09aa-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b09aa-127">Remarks</span></span>  
 <span data-ttu-id="b09aa-128">Překladač tokenů vystavithonu se používá k vyřešení podpisového tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="b09aa-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="b09aa-129">Používá se k načtení kryptografického materiálu, který se používá ke kontrole podpisu.</span><span class="sxs-lookup"><span data-stu-id="b09aa-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="b09aa-130">Je nutné `type` zadat atribut.</span><span class="sxs-lookup"><span data-stu-id="b09aa-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="b09aa-131">Zadaný typ může <xref:System.IdentityModel.Tokens.IssuerTokenResolver> být buď nebo vlastní <xref:System.IdentityModel.Tokens.IssuerTokenResolver> typ, který je odvozen z třídy.</span><span class="sxs-lookup"><span data-stu-id="b09aa-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="b09aa-132">Některé obslužné rutiny tokenů umožňují určit nastavení překladače tokenů vystavithonu v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="b09aa-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="b09aa-133">Nastavení na obslužné rutiny jednotlivých tokenů přepsat ty zadané v kolekci obslužné rutiny tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="b09aa-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="b09aa-134">Určení `<issuerTokenResolver>` prvku jako podřízeného prvku [ \<identityKonfigurace>](identityconfiguration.md) element ubírala, ale je stále podporována z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="b09aa-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="b09aa-135">Nastavení na `<securityTokenHandlerConfiguration>` prvek přepsat ty `<identityConfiguration>` na prvek.</span><span class="sxs-lookup"><span data-stu-id="b09aa-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b09aa-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="b09aa-136">Example</span></span>  
 <span data-ttu-id="b09aa-137">Následující jazyk XML zobrazuje konfiguraci pro překladače tokenů vystavithonu, který je založen na vlastní třídě, která je odvozena od <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="b09aa-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="b09aa-138">Překladač tokenů udržuje slovník párů publika a klíčů, který je inicializován z vlastního konfiguračního prvku (`<AddAudienceKeyPair>`) definovaného pro třídu.</span><span class="sxs-lookup"><span data-stu-id="b09aa-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="b09aa-139">Třída přepíše <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metodu ke zpracování tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="b09aa-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="b09aa-140">Přepsání je znázorněno v následujícím příkladu; metody, které volá však nejsou zobrazeny pro stručnost.</span><span class="sxs-lookup"><span data-stu-id="b09aa-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="b09aa-141">Úplný příklad naleznete v `CustomToken` ukázce.</span><span class="sxs-lookup"><span data-stu-id="b09aa-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="b09aa-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="b09aa-142">Example</span></span>
  
```csharp
public override void LoadCustomConfiguration(System.Xml.XmlNodeList nodelist)  
{  
    foreach (XmlNode node in nodelist)  
    {  
        XmlDictionaryReader rdr = XmlDictionaryReader.CreateDictionaryReader(new XmlTextReader(new StringReader(node.OuterXml)));  
        rdr.MoveToContent();  
  
        string symmetricKey = rdr.GetAttribute("symmetricKey");  
        string audience = rdr.GetAttribute("audience");  
  
        this.AddAudienceKeyPair(audience, symmetricKey);  
    }  
}  
```
  
## <a name="see-also"></a><span data-ttu-id="b09aa-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="b09aa-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
