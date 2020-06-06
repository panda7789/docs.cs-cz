---
title: <issuerTokenResolver>
ms.date: 03/30/2017
ms.assetid: f74392f6-3f5b-4880-bd8a-3a9130d31e65
author: BrucePerlerMS
ms.openlocfilehash: 67d7e0aa5b6b05bfe8b17a1b1efebb1fbddbb0eb
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79152668"
---
# \<issuerTokenResolver>
<span data-ttu-id="80715-101">Registruje překladač tokenů vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenu.</span><span class="sxs-lookup"><span data-stu-id="80715-101">Registers the issuer token resolver that is used by handlers in the token handler collection.</span></span> <span data-ttu-id="80715-102">Překladač tokenů vystavitele se používá k překladu podpisového tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="80715-102">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerTokenResolver>**  
  
## <a name="syntax"></a><span data-ttu-id="80715-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80715-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80715-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="80715-104">Attributes and Elements</span></span>  
 <span data-ttu-id="80715-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="80715-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80715-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="80715-106">Attributes</span></span>  
  
|<span data-ttu-id="80715-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="80715-107">Attribute</span></span>|<span data-ttu-id="80715-108">Popis</span><span class="sxs-lookup"><span data-stu-id="80715-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80715-109">typ</span><span class="sxs-lookup"><span data-stu-id="80715-109">type</span></span>|<span data-ttu-id="80715-110">Určuje typ překladače tokenu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="80715-110">Specifies the type of the issuer token resolver.</span></span> <span data-ttu-id="80715-111">Musí být buď <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třída, nebo typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="80715-111">Must be either the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class or a type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span> <span data-ttu-id="80715-112">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="80715-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80715-113">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="80715-113">Child Elements</span></span>  
 <span data-ttu-id="80715-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="80715-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80715-115">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="80715-115">Parent Elements</span></span>  
  
|<span data-ttu-id="80715-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="80715-116">Element</span></span>|<span data-ttu-id="80715-117">Description</span><span class="sxs-lookup"><span data-stu-id="80715-117">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="80715-118">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="80715-118">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80715-119">Poznámky</span><span class="sxs-lookup"><span data-stu-id="80715-119">Remarks</span></span>  
 <span data-ttu-id="80715-120">Překladač tokenů vystavitele se používá k překladu podpisového tokenu na příchozích tokenech a zprávách.</span><span class="sxs-lookup"><span data-stu-id="80715-120">The issuer token resolver is used to resolve the signing token on incoming tokens and messages.</span></span> <span data-ttu-id="80715-121">Slouží k načtení kryptografického materiálu, který se používá k ověření podpisu.</span><span class="sxs-lookup"><span data-stu-id="80715-121">It is used to retrieve the cryptographic material that is used for checking the signature.</span></span> <span data-ttu-id="80715-122">Je nutné zadat `type` atribut.</span><span class="sxs-lookup"><span data-stu-id="80715-122">You must specify the `type` attribute.</span></span> <span data-ttu-id="80715-123">Zadaný typ může být buď <xref:System.IdentityModel.Tokens.IssuerTokenResolver> nebo vlastní typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerTokenResolver> třídy.</span><span class="sxs-lookup"><span data-stu-id="80715-123">The type specified can be either <xref:System.IdentityModel.Tokens.IssuerTokenResolver> or a custom type that derives from the <xref:System.IdentityModel.Tokens.IssuerTokenResolver> class.</span></span>  
  
 <span data-ttu-id="80715-124">Některé obslužné rutiny tokenů umožňují zadat nastavení překladače tokenu vystavitele v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="80715-124">Some token handlers allow you to specify issuer token resolver settings in configuration.</span></span> <span data-ttu-id="80715-125">Nastavení pro obslužné rutiny jednotlivých tokenů přepíší ty zadané v kolekci obslužných rutin tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="80715-125">Settings on individual token handlers override those specified on the security token handler collection.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="80715-126">Určení `<issuerTokenResolver>` prvku jako podřízený element [\<identityConfiguration>](identityconfiguration.md) elementu je zastaralé, ale je stále podporováno z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="80715-126">Specifying the `<issuerTokenResolver>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="80715-127">Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="80715-127">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="80715-128">Příklad</span><span class="sxs-lookup"><span data-stu-id="80715-128">Example</span></span>  
 <span data-ttu-id="80715-129">Následující kód XML ukazuje konfiguraci překladače tokenu vystavitele, který je založen na vlastní třídě, která je odvozena z <xref:System.IdentityModel.Tokens.IssuerTokenResolver> .</span><span class="sxs-lookup"><span data-stu-id="80715-129">The following XML shows configuration for an issuer token resolver that is based on a custom class that derives from <xref:System.IdentityModel.Tokens.IssuerTokenResolver>.</span></span> <span data-ttu-id="80715-130">Překladač tokenů udržuje slovník dvojic klíčů cílové skupiny, které jsou inicializovány z vlastního elementu konfigurace ( `<AddAudienceKeyPair>` ) definovaného pro třídu.</span><span class="sxs-lookup"><span data-stu-id="80715-130">The token resolver maintains a dictionary of audience-key pairs that is initialized from a custom configuration element (`<AddAudienceKeyPair>`) defined for the class.</span></span> <span data-ttu-id="80715-131">Třída Přepisuje <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> metodu pro zpracování tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="80715-131">The class overrides the <xref:System.IdentityModel.Selectors.SecurityTokenResolver.LoadCustomConfiguration%2A> method to process this element.</span></span> <span data-ttu-id="80715-132">Přepsání je uvedeno v následujícím příkladu. Nicméně metody, které volá, nejsou zobrazeny pro zkrácení.</span><span class="sxs-lookup"><span data-stu-id="80715-132">The override is shown in the following example; however, the methods it calls are not shown for brevity.</span></span> <span data-ttu-id="80715-133">Úplný příklad najdete v `CustomToken` ukázce.</span><span class="sxs-lookup"><span data-stu-id="80715-133">For the complete example, see the `CustomToken` sample.</span></span>  
  
```xml  
<issuerTokenResolver type="SimpleWebToken.CustomIssuerTokenResolver, SimpleWebToken">  
  <AddAudienceKeyPair  symmetricKey="wAVkldQiFypTQ+kdNdGWCYCHRcee8XmXxOvgmak8vSY=" audience="http://localhost:19851/" />  
</issuerTokenResolver>  
```  
  
## <a name="example"></a><span data-ttu-id="80715-134">Příklad</span><span class="sxs-lookup"><span data-stu-id="80715-134">Example</span></span>
  
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
  
## <a name="see-also"></a><span data-ttu-id="80715-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="80715-135">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerTokenResolver>
