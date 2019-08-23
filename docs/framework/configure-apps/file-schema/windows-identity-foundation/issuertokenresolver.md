---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: da591940910b16d42ef8ab1a05c4b244dbe543f4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942632"
---
# <a name="issuertokenresolver"></a><span data-ttu-id="8955b-101">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="8955b-101">\<issuerTokenResolver></span></span>
<span data-ttu-id="8955b-102">Registruje překladač tokenů vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="8955b-102">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="8955b-103">Překladač tokenů vystavitele se používá k překladu podpisového tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="8955b-103">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="8955b-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8955b-104">\<system.identityModel></span></span>  
<span data-ttu-id="8955b-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8955b-105">\<identityConfiguration></span></span>  
<span data-ttu-id="8955b-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="8955b-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="8955b-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="8955b-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="8955b-108">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="8955b-108">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8955b-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="8955b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8955b-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="8955b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8955b-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="8955b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8955b-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="8955b-112">Attributes</span></span>  
  
|<span data-ttu-id="8955b-113">Atribut</span><span class="sxs-lookup"><span data-stu-id="8955b-113">Attribute</span></span>|<span data-ttu-id="8955b-114">Popis</span><span class="sxs-lookup"><span data-stu-id="8955b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8955b-115">– typ</span><span class="sxs-lookup"><span data-stu-id="8955b-115">type</span></span>|<span data-ttu-id="8955b-116">Určuje typ překladače tokenu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="8955b-116">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="8955b-117">Musí být buď <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třída, nebo typ, který je odvozen <xref:System.IdentityModel.Tokens.IssuerTokenResolver> od třídy.</span><span class="sxs-lookup"><span data-stu-id="8955b-117">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="8955b-118">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="8955b-118">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8955b-119">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="8955b-119">Child Elements</span></span>  
 <span data-ttu-id="8955b-120">Žádné</span><span class="sxs-lookup"><span data-stu-id="8955b-120">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8955b-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="8955b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="8955b-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="8955b-122">Element</span></span>|<span data-ttu-id="8955b-123">Popis</span><span class="sxs-lookup"><span data-stu-id="8955b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8955b-124">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="8955b-124">\<securityTokenHandlerConfiguration></span></span>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="8955b-125">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8955b-125">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8955b-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="8955b-126">Remarks</span></span>  
 <span data-ttu-id="8955b-127">Překladač tokenů vystavitele se používá k překladu podpisového tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="8955b-127">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="8955b-128">Slouží k načtení kryptografického materiálu, který se používá k ověření podpisu.</span><span class="sxs-lookup"><span data-stu-id="8955b-128">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="8955b-129">Je nutné zadat `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="8955b-129">You must specify the `type` attribute.</span></span> <span data-ttu-id="8955b-130">Zadaný typ může být buď <xref:System.IdentityModel.Tokens.IssuerTokenResolver> nebo vlastní typ, který je odvozen <xref:System.IdentityModel.Tokens.IssuerTokenResolver> od třídy.</span><span class="sxs-lookup"><span data-stu-id="8955b-130">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="8955b-131">Některé obslužné rutiny tokenů umožňují zadat nastavení překladače tokenu vystavitele v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="8955b-131">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="8955b-132">Nastavení pro obslužné rutiny jednotlivých tokenů přepíší ty zadané v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="8955b-132">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="8955b-133">Určení prvku jako podřízeného prvku [ \<prvku IdentityConfiguration >](identityconfiguration.md) je zastaralé, ale stále se podporuje z důvodu zpětné kompatibility. `<issuerTokenResolver>`</span><span class="sxs-lookup"><span data-stu-id="8955b-133">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="8955b-134">Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky `<identityConfiguration>` na elementu.</span><span class="sxs-lookup"><span data-stu-id="8955b-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8955b-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="8955b-135">Example</span></span>  
 <span data-ttu-id="8955b-136">Následující kód XML ukazuje konfiguraci překladače tokenu vystavitele, který je založen na vlastní třídě, která <xref:System.IdentityModel.Tokens.IssuerTokenResolver>je odvozena z.</span><span class="sxs-lookup"><span data-stu-id="8955b-136">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="8955b-137">Překladač tokenů udržuje slovník dvojic klíčů cílové skupiny, které jsou inicializovány z vlastního elementu konfigurace (`<AddAudienceKeyPair>`) definovaného pro třídu.</span><span class="sxs-lookup"><span data-stu-id="8955b-137">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="8955b-138">Třída Přepisuje <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metodu pro zpracování tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="8955b-138">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="8955b-139">Přepsání je uvedeno v následujícím příkladu. Nicméně metody, které volá, nejsou zobrazeny pro zkrácení.</span><span class="sxs-lookup"><span data-stu-id="8955b-139">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="8955b-140">Úplný příklad najdete `CustomToken` v ukázce.</span><span class="sxs-lookup"><span data-stu-id="8955b-140">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="8955b-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="8955b-141">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="8955b-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8955b-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
