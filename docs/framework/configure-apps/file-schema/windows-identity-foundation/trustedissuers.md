---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 50fc7194823fb0c5c426fb54ffd50b17c3714ed9
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251757"
---
# <a name="trustedissuers"></a><span data-ttu-id="d3c78-101">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="d3c78-101">\<trustedIssuers></span></span>
<span data-ttu-id="d3c78-102">Nakonfiguruje seznam certifikátů důvěryhodných vystavitelů, které používá registr názvů vystavitelů na<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>základě konfigurace ().</span><span class="sxs-lookup"><span data-stu-id="d3c78-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
<span data-ttu-id="d3c78-103">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="d3c78-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="d3c78-104">&nbsp;&nbsp;[ **\<System. identityModel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="d3c78-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="d3c78-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d3c78-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="d3c78-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="d3c78-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="d3c78-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlerConfiguration >** ](securitytokenhandlerconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="d3c78-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlerConfiguration>**](securitytokenhandlerconfiguration.md)</span></span>\
<span data-ttu-id="d3c78-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<issuerNameRegistry >** ](issuernameregistry.md)</span><span class="sxs-lookup"><span data-stu-id="d3c78-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuerNameRegistry>**](issuernameregistry.md)</span></span>\
<span data-ttu-id="d3c78-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<trustedIssuers >**</span><span class="sxs-lookup"><span data-stu-id="d3c78-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<trustedIssuers>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3c78-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3c78-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3c78-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d3c78-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d3c78-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d3c78-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3c78-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d3c78-113">Attributes</span></span>  
 <span data-ttu-id="d3c78-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="d3c78-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d3c78-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d3c78-115">Child Elements</span></span>  
  
|<span data-ttu-id="d3c78-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="d3c78-116">Element</span></span>|<span data-ttu-id="d3c78-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d3c78-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="d3c78-118">Přidá certifikát do kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="d3c78-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="d3c78-119">Certifikát je zadán s `thumbprint` atributem.</span><span class="sxs-lookup"><span data-stu-id="d3c78-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="d3c78-120">Tento atribut je povinný a měl by obsahovat formát ASN. 1 kódovaný v rámci kryptografického otisku certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d3c78-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="d3c78-121">`name` Atribut je nepovinný a dá se použít k zadání popisného názvu pro certifikát.</span><span class="sxs-lookup"><span data-stu-id="d3c78-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="d3c78-122">Vymaže všechny certifikáty z kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="d3c78-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="d3c78-123">Odebere certifikát z kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="d3c78-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="d3c78-124">Certifikát je zadán s `thumbprint` atributem.</span><span class="sxs-lookup"><span data-stu-id="d3c78-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="d3c78-125">Tento atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="d3c78-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d3c78-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d3c78-126">Parent Elements</span></span>  
  
|<span data-ttu-id="d3c78-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="d3c78-127">Element</span></span>|<span data-ttu-id="d3c78-128">Popis</span><span class="sxs-lookup"><span data-stu-id="d3c78-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d3c78-129">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="d3c78-129">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="d3c78-130">Nakonfiguruje registr názvu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="d3c78-130">Configures the issuer name registry.</span></span> <span data-ttu-id="d3c78-131">**Důležité:**  Atribut elementu musí odkazovat na <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídu, aby byl elementplatný.`<trustedIssuers>` `<issuerNameRegistry>` `type`</span><span class="sxs-lookup"><span data-stu-id="d3c78-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3c78-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3c78-132">Remarks</span></span>  
 <span data-ttu-id="d3c78-133">Windows Identity Foundation (WIF) poskytuje jednu implementaci <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy mimo pole <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> , třídu.</span><span class="sxs-lookup"><span data-stu-id="d3c78-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="d3c78-134">Registr názvů vystavitele konfigurace uchovává seznam důvěryhodných vystavitelů načtených z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d3c78-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="d3c78-135">Seznam přidruží jednotlivé názvy vystavitelů k certifikátu X. 509, který je nezbytný k ověření podpisu tokenů vyprodukovaných vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="d3c78-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="d3c78-136">Seznam certifikátů důvěryhodných vystavitelů je určen pod `<trustedIssuers>` prvkem.</span><span class="sxs-lookup"><span data-stu-id="d3c78-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="d3c78-137">Každý prvek v seznamu přidruží název vystavitele pomocí certifikátu X. 509, který je nezbytný k ověření podpisu tokenů vyprodukovaných tímto vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="d3c78-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="d3c78-138">Důvěryhodné certifikáty jsou zadány pomocí formátu ASN. 1 kódovaného otisku certifikátu a jsou přidány do kolekce pomocí `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d3c78-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="d3c78-139">Můžete vymazat nebo odebrat vystavitele (certifikáty) ze seznamu pomocí `<clear>` prvků a. `<remove>`</span><span class="sxs-lookup"><span data-stu-id="d3c78-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="d3c78-140">Atribut elementu musí odkazovat na <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídu, aby byl elementplatný.`<trustedIssuers>` `<issuerNameRegistry>` `type`</span><span class="sxs-lookup"><span data-stu-id="d3c78-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3c78-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3c78-141">Example</span></span>  
 <span data-ttu-id="d3c78-142">Následující kód XML ukazuje, jak zadat registr názvů vystavitelů na základě konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d3c78-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d3c78-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3c78-143">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
