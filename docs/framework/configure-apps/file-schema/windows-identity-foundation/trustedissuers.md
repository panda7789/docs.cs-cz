---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 32aad3529ded6d0234b1bcb388ecbbc3b0a11c87
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944263"
---
# <a name="trustedissuers"></a><span data-ttu-id="c7b07-101">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="c7b07-101">\<trustedIssuers></span></span>
<span data-ttu-id="c7b07-102">Nakonfiguruje seznam certifikátů důvěryhodných vystavitelů, které používá registr názvů vystavitelů na<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>základě konfigurace ().</span><span class="sxs-lookup"><span data-stu-id="c7b07-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="c7b07-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="c7b07-103">\<system.identityModel></span></span>  
<span data-ttu-id="c7b07-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c7b07-104">\<identityConfiguration></span></span>  
<span data-ttu-id="c7b07-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="c7b07-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="c7b07-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="c7b07-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="c7b07-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="c7b07-107">\<issuerNameRegistry></span></span>  
<span data-ttu-id="c7b07-108">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="c7b07-108">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c7b07-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c7b07-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c7b07-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c7b07-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c7b07-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="c7b07-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c7b07-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="c7b07-112">Attributes</span></span>  
 <span data-ttu-id="c7b07-113">Žádné</span><span class="sxs-lookup"><span data-stu-id="c7b07-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c7b07-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c7b07-114">Child Elements</span></span>  
  
|<span data-ttu-id="c7b07-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="c7b07-115">Element</span></span>|<span data-ttu-id="c7b07-116">Popis</span><span class="sxs-lookup"><span data-stu-id="c7b07-116">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="c7b07-117">Přidá certifikát do kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="c7b07-117">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="c7b07-118">Certifikát je zadán s `thumbprint` atributem.</span><span class="sxs-lookup"><span data-stu-id="c7b07-118">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="c7b07-119">Tento atribut je povinný a měl by obsahovat formát ASN. 1 kódovaný v rámci kryptografického otisku certifikátu.</span><span class="sxs-lookup"><span data-stu-id="c7b07-119">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="c7b07-120">`name` Atribut je nepovinný a dá se použít k zadání popisného názvu pro certifikát.</span><span class="sxs-lookup"><span data-stu-id="c7b07-120">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="c7b07-121">Vymaže všechny certifikáty z kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="c7b07-121">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="c7b07-122">Odebere certifikát z kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="c7b07-122">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="c7b07-123">Certifikát je zadán s `thumbprint` atributem.</span><span class="sxs-lookup"><span data-stu-id="c7b07-123">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="c7b07-124">Tento atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="c7b07-124">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c7b07-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c7b07-125">Parent Elements</span></span>  
  
|<span data-ttu-id="c7b07-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="c7b07-126">Element</span></span>|<span data-ttu-id="c7b07-127">Popis</span><span class="sxs-lookup"><span data-stu-id="c7b07-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c7b07-128">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="c7b07-128">\<issuerNameRegistry></span></span>](issuernameregistry.md)|<span data-ttu-id="c7b07-129">Nakonfiguruje registr názvu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="c7b07-129">Configures the issuer name registry.</span></span> <span data-ttu-id="c7b07-130">**Důležité:**  Atribut elementu musí odkazovat na <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídu, aby byl elementplatný.`<trustedIssuers>` `<issuerNameRegistry>` `type`</span><span class="sxs-lookup"><span data-stu-id="c7b07-130">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c7b07-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c7b07-131">Remarks</span></span>  
 <span data-ttu-id="c7b07-132">Windows Identity Foundation (WIF) poskytuje jednu implementaci <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy mimo pole <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> , třídu.</span><span class="sxs-lookup"><span data-stu-id="c7b07-132">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="c7b07-133">Registr názvů vystavitele konfigurace uchovává seznam důvěryhodných vystavitelů načtených z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c7b07-133">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="c7b07-134">Seznam přidruží jednotlivé názvy vystavitelů k certifikátu X. 509, který je nezbytný k ověření podpisu tokenů vyprodukovaných vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="c7b07-134">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="c7b07-135">Seznam certifikátů důvěryhodných vystavitelů je určen pod `<trustedIssuers>` prvkem.</span><span class="sxs-lookup"><span data-stu-id="c7b07-135">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="c7b07-136">Každý prvek v seznamu přidruží název vystavitele pomocí certifikátu X. 509, který je nezbytný k ověření podpisu tokenů vyprodukovaných tímto vystavitelem.</span><span class="sxs-lookup"><span data-stu-id="c7b07-136">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="c7b07-137">Důvěryhodné certifikáty jsou zadány pomocí formátu ASN. 1 kódovaného otisku certifikátu a jsou přidány do kolekce pomocí `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="c7b07-137">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="c7b07-138">Můžete vymazat nebo odebrat vystavitele (certifikáty) ze seznamu pomocí `<clear>` prvků a. `<remove>`</span><span class="sxs-lookup"><span data-stu-id="c7b07-138">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="c7b07-139">Atribut elementu musí odkazovat na <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídu, aby byl elementplatný.`<trustedIssuers>` `<issuerNameRegistry>` `type`</span><span class="sxs-lookup"><span data-stu-id="c7b07-139">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c7b07-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="c7b07-140">Example</span></span>  
 <span data-ttu-id="c7b07-141">Následující kód XML ukazuje, jak zadat registr názvů vystavitelů na základě konfigurace.</span><span class="sxs-lookup"><span data-stu-id="c7b07-141">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="c7b07-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c7b07-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
