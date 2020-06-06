---
title: <issuerNameRegistry>
ms.date: 03/30/2017
ms.assetid: 58b39d12-c953-40c4-88af-d7eb3343ca28
author: BrucePerlerMS
ms.openlocfilehash: 209e702da80f2569f2b6c068f50f1af4489157f6
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251970"
---
# \<issuerNameRegistry>
<span data-ttu-id="fe082-101">Konfiguruje registr názvu vystavitele, který jsou používány obslužnými rutinami v kolekci obslužných rutin tokenů.</span><span class="sxs-lookup"><span data-stu-id="fe082-101">Configures the issuer name registry that is used by handlers in the token handler collection.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<issuerNameRegistry>**  
  
## <a name="syntax"></a><span data-ttu-id="fe082-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="fe082-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry type=xs:string>  
          <optionalCustomConfigurationElements />  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fe082-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="fe082-103">Attributes and Elements</span></span>  
 <span data-ttu-id="fe082-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="fe082-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fe082-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="fe082-105">Attributes</span></span>  
  
|<span data-ttu-id="fe082-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="fe082-106">Attribute</span></span>|<span data-ttu-id="fe082-107">Popis</span><span class="sxs-lookup"><span data-stu-id="fe082-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fe082-108">typ</span><span class="sxs-lookup"><span data-stu-id="fe082-108">type</span></span>|<span data-ttu-id="fe082-109">Typ, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="fe082-109">A type that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="fe082-110">Další informace o tom, jak zadat vlastní `type` , naleznete v tématu [odkazy na vlastní typ].</span><span class="sxs-lookup"><span data-stu-id="fe082-110">For more information about how to specify a custom `type`, see [Custom Type References].</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fe082-111">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="fe082-111">Child Elements</span></span>  
  
|<span data-ttu-id="fe082-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe082-112">Element</span></span>|<span data-ttu-id="fe082-113">Description</span><span class="sxs-lookup"><span data-stu-id="fe082-113">Description</span></span>|  
|-------------|-----------------|  
|[\<trustedIssuers>](trustedissuers.md)|<span data-ttu-id="fe082-114">Pokud `type` atribut určuje registr názvu vystavitele založený na konfiguraci ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třída), [\<trustedIssuers>](trustedissuers.md) musí být zadaný element.</span><span class="sxs-lookup"><span data-stu-id="fe082-114">When the `type` attribute specifies the configuration-based issuer name registry (the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class), the [\<trustedIssuers>](trustedissuers.md) element must be specified.</span></span> <span data-ttu-id="fe082-115">[\<trustedIssuers>](trustedissuers.md)Element může převzít `<add>` prvky, `<clear>` nebo `<remove>` jako podřízené prvky.</span><span class="sxs-lookup"><span data-stu-id="fe082-115">The [\<trustedIssuers>](trustedissuers.md) element can take `<add>`, `<clear>`, or `<remove>` elements as child elements.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fe082-116">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="fe082-116">Parent Elements</span></span>  
  
|<span data-ttu-id="fe082-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="fe082-117">Element</span></span>|<span data-ttu-id="fe082-118">Description</span><span class="sxs-lookup"><span data-stu-id="fe082-118">Description</span></span>|  
|-------------|-----------------|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|<span data-ttu-id="fe082-119">Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="fe082-119">Provides configuration for a collection of security token handlers.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fe082-120">Poznámky</span><span class="sxs-lookup"><span data-stu-id="fe082-120">Remarks</span></span>  
 <span data-ttu-id="fe082-121">Všechny tokeny vystavitele se ověřují pomocí registru názvu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="fe082-121">All issuer tokens are validated using an issuer name registry.</span></span> <span data-ttu-id="fe082-122">Toto je objekt, který je odvozen od <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="fe082-122">This is an object that derives from the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class.</span></span> <span data-ttu-id="fe082-123">Registr názvu vystavitele se používá k přidružení symbolického názvu k kryptografickému materiálu, který je nutný k ověření podpisů tokenů vyprodukovaných odpovídajícím vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="fe082-123">The issuer name registry is used to associate a mnemonic name to the cryptographic material that is needed to verify the signatures of tokens produced by the corresponding issuer.</span></span> <span data-ttu-id="fe082-124">Registr názvů vystavitele uchovává seznam vystavitelů, které jsou důvěryhodné pro aplikaci předávající strany (RP).</span><span class="sxs-lookup"><span data-stu-id="fe082-124">The issuer name registry maintains a list of issuers that are trusted by the relying party (RP) application.</span></span> <span data-ttu-id="fe082-125">Typ registru názvu vystavitele je zadaný pomocí `type` atributu.</span><span class="sxs-lookup"><span data-stu-id="fe082-125">The type of the issuer name registry is specified using the `type` attribute.</span></span> <span data-ttu-id="fe082-126">`<issuerNameRegistry>`Element může mít jeden nebo více podřízených elementů, které poskytují konfiguraci pro zadaný typ.</span><span class="sxs-lookup"><span data-stu-id="fe082-126">The `<issuerNameRegistry>` element can have one or more child elements that provide configuration for the specified type.</span></span> <span data-ttu-id="fe082-127">Zadáte logiku, která zpracovává tyto podřízené prvky přepsáním <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="fe082-127">You provide the logic that processes these child elements by overriding the <xref:System.IdentityModel.Tokens.IssuerNameRegistry.LoadCustomConfiguration%2A> method.</span></span>  
  
 <span data-ttu-id="fe082-128">WIF poskytuje jeden název vystavitele jako typ registru v poli, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> Třída.</span><span class="sxs-lookup"><span data-stu-id="fe082-128">WIF provides a single issuer name registry type out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="fe082-129">Tato třída používá sadu certifikátů důvěryhodných vystavitelů, které jsou zadány v konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="fe082-129">This class uses a set of trusted issuer certificates that are specified in configuration.</span></span> <span data-ttu-id="fe082-130">Vyžaduje podřízený element konfigurace, `<trustedIssuers>` pod kterým je nakonfigurované shromažďování certifikátů důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="fe082-130">It requires a child configuration element, `<trustedIssuers>`, under which the collection of trusted issuer certificates is configured.</span></span> <span data-ttu-id="fe082-131">Důvěryhodné certifikáty jsou určeny pomocí formátu ASN. 1 kódovaného otisku certifikátu a jsou přidány nebo odebrány z kolekce pomocí `<add>` `<clear>` prvků, nebo `<remove>` .</span><span class="sxs-lookup"><span data-stu-id="fe082-131">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added or removed from the collection by using `<add>`, `<clear>`, or `<remove>` elements.</span></span>  
  
 <span data-ttu-id="fe082-132">`<issuerNameRegistry>`Element je reprezentován <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> třídou.</span><span class="sxs-lookup"><span data-stu-id="fe082-132">The `<issuerNameRegistry>` element is represented by the <xref:System.IdentityModel.Configuration.IssuerNameRegistryElement> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="fe082-133">Určení `<issuerNameRegistry>` prvku jako podřízený element [\<identityConfiguration>](identityconfiguration.md) elementu je zastaralé, ale je stále podporováno z důvodu zpětné kompatibility.</span><span class="sxs-lookup"><span data-stu-id="fe082-133">Specifying the `<issuerNameRegistry>` element as a child element of the [\<identityConfiguration>](identityconfiguration.md) element has been deprecated, but is still supported for backward compatibility.</span></span> <span data-ttu-id="fe082-134">Nastavení na `<securityTokenHandlerConfiguration>` elementu přepíší tyto prvky na `<identityConfiguration>` elementu.</span><span class="sxs-lookup"><span data-stu-id="fe082-134">Settings on the `<securityTokenHandlerConfiguration>` element override those on the `<identityConfiguration>` element.</span></span>  
  
## <a name="example"></a><span data-ttu-id="fe082-135">Příklad</span><span class="sxs-lookup"><span data-stu-id="fe082-135">Example</span></span>  
 <span data-ttu-id="fe082-136">Následující kód XML ukazuje, jak zadat registr názvů vystavitelů na základě konfigurace.</span><span class="sxs-lookup"><span data-stu-id="fe082-136">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB … 1EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fe082-137">Viz také</span><span class="sxs-lookup"><span data-stu-id="fe082-137">See also</span></span>

- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
