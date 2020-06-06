---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251757"
---
# \<trustedIssuers>
<span data-ttu-id="02105-101">Nakonfiguruje seznam certifikátů důvěryhodných vystavitelů, které používá registr názvů vystavitelů na základě konfigurace ( <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> ).</span><span class="sxs-lookup"><span data-stu-id="02105-101">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**  
  
## <a name="syntax"></a><span data-ttu-id="02105-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="02105-102">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <securityTokenHandlerConfiguration>  
        <issuerNameRegistry>  
          <trustedIssuers>  
            <add thumbprint=xs:string name=xs:string>  
            <clear>  
            <remove thumbprint=xs:string>  
          </trustedIssuers>  
        </issuerNameRegistry>  
      </securityTokenHandlerConfiguration>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="02105-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="02105-103">Attributes and Elements</span></span>  
 <span data-ttu-id="02105-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="02105-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="02105-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="02105-105">Attributes</span></span>  
 <span data-ttu-id="02105-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="02105-106">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="02105-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="02105-107">Child Elements</span></span>  
  
|<span data-ttu-id="02105-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="02105-108">Element</span></span>|<span data-ttu-id="02105-109">Description</span><span class="sxs-lookup"><span data-stu-id="02105-109">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="02105-110">Přidá certifikát do kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="02105-110">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="02105-111">Certifikát je zadán s `thumbprint` atributem.</span><span class="sxs-lookup"><span data-stu-id="02105-111">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="02105-112">Tento atribut je povinný a měl by obsahovat formát ASN. 1 kódovaný v rámci kryptografického otisku certifikátu.</span><span class="sxs-lookup"><span data-stu-id="02105-112">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="02105-113">`name`Atribut je nepovinný a dá se použít k zadání popisného názvu pro certifikát.</span><span class="sxs-lookup"><span data-stu-id="02105-113">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="02105-114">Vymaže všechny certifikáty z kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="02105-114">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="02105-115">Odebere certifikát z kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="02105-115">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="02105-116">Certifikát je zadán s `thumbprint` atributem.</span><span class="sxs-lookup"><span data-stu-id="02105-116">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="02105-117">Tento atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="02105-117">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="02105-118">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="02105-118">Parent Elements</span></span>  
  
|<span data-ttu-id="02105-119">Prvek</span><span class="sxs-lookup"><span data-stu-id="02105-119">Element</span></span>|<span data-ttu-id="02105-120">Description</span><span class="sxs-lookup"><span data-stu-id="02105-120">Description</span></span>|  
|-------------|-----------------|  
|[\<issuerNameRegistry>](issuernameregistry.md)|<span data-ttu-id="02105-121">Nakonfiguruje registr názvu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="02105-121">Configures the issuer name registry.</span></span> <span data-ttu-id="02105-122">**Důležité informace:**  `type`Atribut `<issuerNameRegistry>` elementu musí odkazovat na <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídu, aby byl `<trustedIssuers>` element platný.</span><span class="sxs-lookup"><span data-stu-id="02105-122">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="02105-123">Poznámky</span><span class="sxs-lookup"><span data-stu-id="02105-123">Remarks</span></span>  
 <span data-ttu-id="02105-124">Windows Identity Foundation (WIF) poskytuje jednu implementaci <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy mimo pole, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídu.</span><span class="sxs-lookup"><span data-stu-id="02105-124">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="02105-125">Registr názvů vystavitele konfigurace uchovává seznam důvěryhodných vystavitelů načtených z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="02105-125">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="02105-126">Seznam přidruží jednotlivé názvy vystavitelů k certifikátu X. 509, který je nezbytný k ověření podpisu tokenů vyprodukovaných vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="02105-126">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="02105-127">Seznam certifikátů důvěryhodných vystavitelů je určen pod `<trustedIssuers>` prvkem.</span><span class="sxs-lookup"><span data-stu-id="02105-127">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="02105-128">Každý prvek v seznamu přidruží název vystavitele pomocí certifikátu X. 509, který je nezbytný k ověření podpisu tokenů vyprodukovaných tímto vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="02105-128">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="02105-129">Důvěryhodné certifikáty jsou zadány pomocí formátu ASN. 1 kódovaného otisku certifikátu a jsou přidány do kolekce pomocí `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="02105-129">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="02105-130">Můžete vymazat nebo odebrat vystavitele (certifikáty) ze seznamu pomocí `<clear>` `<remove>` prvků a.</span><span class="sxs-lookup"><span data-stu-id="02105-130">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="02105-131">`type`Atribut `<issuerNameRegistry>` elementu musí odkazovat na <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídu, aby byl `<trustedIssuers>` element platný.</span><span class="sxs-lookup"><span data-stu-id="02105-131">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="02105-132">Příklad</span><span class="sxs-lookup"><span data-stu-id="02105-132">Example</span></span>  
 <span data-ttu-id="02105-133">Následující kód XML ukazuje, jak zadat registr názvů vystavitelů na základě konfigurace.</span><span class="sxs-lookup"><span data-stu-id="02105-133">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="02105-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="02105-134">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
