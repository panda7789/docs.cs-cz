---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 8775e3044e58886cfa53a9fd9fc8b4b8ed2105b5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251954"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="c6039-101">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="c6039-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="c6039-102">Registruje překladač tokenů vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="c6039-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="c6039-103">Překladač tokenů vystavitele se používá k překladu podpisového tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="c6039-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
<span data-ttu-id="c6039-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c6039-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c6039-105">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="c6039-105">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="c6039-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c6039-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="c6039-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="c6039-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="c6039-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c6039-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="c6039-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<issuerTokenResolver >**</span><span class="sxs-lookup"><span data-stu-id="c6039-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6039-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c6039-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c6039-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c6039-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c6039-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c6039-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c6039-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="c6039-113">Attributes</span></span>  
  
|<span data-ttu-id="c6039-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="c6039-114">Attribute</span></span>|<span data-ttu-id="c6039-115">Popis</span><span class="sxs-lookup"><span data-stu-id="c6039-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c6039-116">– typ</span><span class="sxs-lookup"><span data-stu-id="c6039-116">type</span></span>|<span data-ttu-id="c6039-117">Určuje typ překladače tokenu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="c6039-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="c6039-118">Musí být buď <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třída, nebo typ, který je odvozen <xref:System.IdentityModel.Tokens.IssuerTokenResolver> od třídy.</span><span class="sxs-lookup"><span data-stu-id="c6039-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="c6039-119">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="c6039-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c6039-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c6039-120">Child Elements</span></span>  
 <span data-ttu-id="c6039-121">Žádné</span><span class="sxs-lookup"><span data-stu-id="c6039-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c6039-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c6039-122">Parent Elements</span></span>  
  
|<span data-ttu-id="c6039-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="c6039-123">Element</span></span>|<span data-ttu-id="c6039-124">Popis</span><span class="sxs-lookup"><span data-stu-id="c6039-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c6039-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="c6039-125">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="c6039-126">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c6039-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c6039-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c6039-127">Remarks</span></span>  
 <span data-ttu-id="c6039-128">Překladač tokenů vystavitele se používá k překladu podpisového tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="c6039-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="c6039-129">Slouží k načtení kryptografického materiálu, který se používá k ověření podpisu.</span><span class="sxs-lookup"><span data-stu-id="c6039-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="c6039-130">Je nutné zadat `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="c6039-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="c6039-131">Zadaný typ může být buď <xref:System.IdentityModel.Tokens.IssuerTokenResolver> nebo vlastní typ, který je odvozen <xref:System.IdentityModel.Tokens.IssuerTokenResolver> od třídy.</span><span class="sxs-lookup"><span data-stu-id="c6039-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="c6039-132">Některé obslužné rutiny tokenů umožňují zadat nastavení překladače tokenu vystavitele v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="c6039-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="c6039-133">Nastavení pro obslužné rutiny jednotlivých tokenů přepíší ty zadané v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="c6039-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="c6039-134">Určení prvku jako podřízeného prvku [ \<prvku IdentityConfiguration >](identityconfiguration.md) je zastaralé, ale stále se podporuje z důvodu zpětné kompatibility. `<issuerTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="c6039-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="c6039-135">Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky `<identityConfiguration>` na elementu.</span><span class="sxs-lookup"><span data-stu-id="c6039-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c6039-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6039-136">Example</span></span>  
 <span data-ttu-id="c6039-137">Následující kód XML ukazuje konfiguraci překladače tokenu vystavitele, který je založen na vlastní třídě, která <xref:System.IdentityModel.Tokens.IssuerTokenResolver>je odvozena z.</span><span class="sxs-lookup"><span data-stu-id="c6039-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="c6039-138">Překladač tokenů udržuje slovník dvojic klíčů cílové skupiny, které jsou inicializovány z vlastního elementu konfigurace (`<AddAudienceKeyPair>`) definovaného pro třídu.</span><span class="sxs-lookup"><span data-stu-id="c6039-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="c6039-139">Třída Přepisuje <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metodu pro zpracování tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="c6039-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="c6039-140">Přepsání je uvedeno v následujícím příkladu. Nicméně metody, které volá, nejsou zobrazeny pro zkrácení.</span><span class="sxs-lookup"><span data-stu-id="c6039-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="c6039-141">Úplný příklad najdete `CustomToken` v ukázce.</span><span class="sxs-lookup"><span data-stu-id="c6039-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="c6039-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="c6039-142">Example</span></span>  
  
```  
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
  
## <a name="see-also"></a><span data-ttu-id="c6039-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c6039-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
