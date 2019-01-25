---
title: '&lt;issuerTokenResolver&gt;'
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 9f88d3cec5e1cb95ce5e12b203e32b706d407a2e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54556623"
---
# <a name="ltissuertokenresolvergt"></a><span data-ttu-id="53ec3-102">&lt;issuerTokenResolver&gt;</span><span class="sxs-lookup"><span data-stu-id="53ec3-102">&lt;issuerTokenResolver&gt;</span></span>
<span data-ttu-id="53ec3-103">Zaregistruje překladač tokenů vystavitele, který se používá obslužné rutiny v kolekci obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="53ec3-103">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="53ec3-104">Překladač tokenů vystavitele se používá k překladu podpisový token na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="53ec3-104">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
 <span data-ttu-id="53ec3-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="53ec3-105">\<system.identityModel></span></span>  
<span data-ttu-id="53ec3-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="53ec3-106">\<identityConfiguration></span></span>  
<span data-ttu-id="53ec3-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="53ec3-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="53ec3-108">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="53ec3-108">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="53ec3-109">\<issuerTokenResolver></span><span class="sxs-lookup"><span data-stu-id="53ec3-109">\<issuerTokenResolver></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="53ec3-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="53ec3-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="53ec3-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="53ec3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="53ec3-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="53ec3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="53ec3-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="53ec3-113">Attributes</span></span>  
  
|<span data-ttu-id="53ec3-114">Atribut</span><span class="sxs-lookup"><span data-stu-id="53ec3-114">Attribute</span></span>|<span data-ttu-id="53ec3-115">Popis</span><span class="sxs-lookup"><span data-stu-id="53ec3-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="53ec3-116">– typ</span><span class="sxs-lookup"><span data-stu-id="53ec3-116">type</span></span>|<span data-ttu-id="53ec3-117">Určuje typ překladač tokenů vystavitele.</span><span class="sxs-lookup"><span data-stu-id="53ec3-117">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="53ec3-118">Musí být buď <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třídy nebo typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="53ec3-118">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="53ec3-119">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="53ec3-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="53ec3-120">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="53ec3-120">Child Elements</span></span>  
 <span data-ttu-id="53ec3-121">Žádná</span><span class="sxs-lookup"><span data-stu-id="53ec3-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="53ec3-122">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="53ec3-122">Parent Elements</span></span>  
  
|<span data-ttu-id="53ec3-123">Prvek</span><span class="sxs-lookup"><span data-stu-id="53ec3-123">Element</span></span>|<span data-ttu-id="53ec3-124">Popis</span><span class="sxs-lookup"><span data-stu-id="53ec3-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="53ec3-125">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="53ec3-125">\<securityTokenHandlerConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|<span data-ttu-id="53ec3-126">Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.</span><span class="sxs-lookup"><span data-stu-id="53ec3-126">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="53ec3-127">Poznámky</span><span class="sxs-lookup"><span data-stu-id="53ec3-127">Remarks</span></span>  
 <span data-ttu-id="53ec3-128">Překladač tokenů vystavitele se používá k překladu podpisový token na příchozí tokeny a zprávy.</span><span class="sxs-lookup"><span data-stu-id="53ec3-128">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="53ec3-129">Používá se k načtení kryptografický materiál, který se používá pro kontrolu podpisu.</span><span class="sxs-lookup"><span data-stu-id="53ec3-129">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="53ec3-130">Je nutné zadat `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="53ec3-130">You must specify the `type` attribute.</span></span> <span data-ttu-id="53ec3-131">Zadaný typ může být buď <xref:System.IdentityModel.Tokens.IssuerTokenResolver> nebo vlastní typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="53ec3-131">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="53ec3-132">Některé obslužné rutiny tokenů vám umožňují určit nastavení vystavitele překladač tokenů v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="53ec3-132">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="53ec3-133">Nastavení na jednotlivých obslužné rutiny tokenů přepsání zadaná v kolekci obslužné rutiny tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="53ec3-133">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="53ec3-134">Zadání `<issuerTokenResolver>` prvek jako podřízený prvek [ \<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) prvek se už nepoužívá, ale je z důvodu zpětné kompatibility stále podporována.</span><span class="sxs-lookup"><span data-stu-id="53ec3-134">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="53ec3-135">Nastavení `<securityTokenHandlerConfiguration>` element mají přednost před akcemi na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="53ec3-135">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="53ec3-136">Příklad</span><span class="sxs-lookup"><span data-stu-id="53ec3-136">Example</span></span>  
 <span data-ttu-id="53ec3-137">Následující kód XML ukazuje konfiguraci pro překladač tokenů vystavitele, který je založen na vlastní třídu, která je odvozena z <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span><span class="sxs-lookup"><span data-stu-id="53ec3-137">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="53ec3-138">Překladač tokenů udržuje slovník párů klíč cílové skupiny, který je inicializován z prvku vlastní konfigurace (`<AddAudienceKeyPair>`) definovaný pro třídu.</span><span class="sxs-lookup"><span data-stu-id="53ec3-138">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="53ec3-139">Třída přepsání <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metodu ke zpracování tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="53ec3-139">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="53ec3-140">Přepsání je znázorněno v následujícím příkladu; metody, které volá, ale nejsou zobrazeny pro zkrácení.</span><span class="sxs-lookup"><span data-stu-id="53ec3-140">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="53ec3-141">Kompletní příklad najdete v článku `CustomToken` vzorku.</span><span class="sxs-lookup"><span data-stu-id="53ec3-141">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="53ec3-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="53ec3-142">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="53ec3-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="53ec3-143">See also</span></span>
- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
