---
title: '&lt;trustedIssuers&gt;'
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: 1459027ae22344d5b1abc917c490b8e98fa0f2c3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633996"
---
# <a name="lttrustedissuersgt"></a><span data-ttu-id="d6f07-102">&lt;trustedIssuers&gt;</span><span class="sxs-lookup"><span data-stu-id="d6f07-102">&lt;trustedIssuers&gt;</span></span>
<span data-ttu-id="d6f07-103">Nakonfiguruje seznam důvěryhodných vystavitelů certifikátů používané registru názvu vystavitele založená na konfiguraci (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span><span class="sxs-lookup"><span data-stu-id="d6f07-103">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="d6f07-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d6f07-104">\<system.identityModel></span></span>  
<span data-ttu-id="d6f07-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d6f07-105">\<identityConfiguration></span></span>  
<span data-ttu-id="d6f07-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="d6f07-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d6f07-107">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="d6f07-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="d6f07-108">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="d6f07-108">\<issuerNameRegistry></span></span>  
<span data-ttu-id="d6f07-109">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="d6f07-109">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6f07-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6f07-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d6f07-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d6f07-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d6f07-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d6f07-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d6f07-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="d6f07-113">Attributes</span></span>  
 <span data-ttu-id="d6f07-114">Žádná</span><span class="sxs-lookup"><span data-stu-id="d6f07-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d6f07-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d6f07-115">Child Elements</span></span>  
  
|<span data-ttu-id="d6f07-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6f07-116">Element</span></span>|<span data-ttu-id="d6f07-117">Popis</span><span class="sxs-lookup"><span data-stu-id="d6f07-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="d6f07-118">Přidá certifikát do kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="d6f07-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="d6f07-119">Certifikát se zadaným `thumbprint` atribut.</span><span class="sxs-lookup"><span data-stu-id="d6f07-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="d6f07-120">Tento atribut je vyžadován a musí obsahovat ASN.1 kódované podobě kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d6f07-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="d6f07-121">`name` Atribut je volitelný a je možné zadat popisný název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="d6f07-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="d6f07-122">Vymaže všechny certifikáty z kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="d6f07-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="d6f07-123">Certifikát se odebere z kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="d6f07-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="d6f07-124">Certifikát se zadaným `thumbprint` atribut.</span><span class="sxs-lookup"><span data-stu-id="d6f07-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="d6f07-125">Tento atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="d6f07-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d6f07-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d6f07-126">Parent Elements</span></span>  
  
|<span data-ttu-id="d6f07-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="d6f07-127">Element</span></span>|<span data-ttu-id="d6f07-128">Popis</span><span class="sxs-lookup"><span data-stu-id="d6f07-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d6f07-129">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="d6f07-129">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="d6f07-130">Nakonfiguruje registru názvu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="d6f07-130">Configures the issuer name registry.</span></span> <span data-ttu-id="d6f07-131">**Důležité:**  `type` Atribut `<issuerNameRegistry>` prvek musí odkazovat <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy pro `<trustedIssuers>` element platný.</span><span class="sxs-lookup"><span data-stu-id="d6f07-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6f07-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6f07-132">Remarks</span></span>  
 <span data-ttu-id="d6f07-133">Technologie Windows Identity Foundation (WIF) poskytuje jedna implementace položky <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy hned po spuštění <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="d6f07-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="d6f07-134">Konfigurace registru názvu vystavitele udržuje seznam důvěryhodných vystavitelů, který je načten z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="d6f07-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="d6f07-135">V seznamu přidruží každý název vystavitele, která je potřeba ověřit podpis tokeny vytvářených vystavitele certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="d6f07-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="d6f07-136">Seznam důvěryhodných vystavitelů certifikátů se zadává v části `<trustedIssuers>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d6f07-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="d6f07-137">Každý prvek v seznamu přidruží mnemonická vystavitele certifikátu X.509, který je potřeba k ověření podpisu tokeny vytvářených tohoto vydavatele.</span><span class="sxs-lookup"><span data-stu-id="d6f07-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="d6f07-138">Důvěryhodné certifikáty jsou zadány pomocí ASN.1 kódovaný formu kryptografický otisk certifikátu a jsou přidány do kolekce pomocí `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="d6f07-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="d6f07-139">Můžete vymazat nebo odebrání vystavitele (certifikáty) ze seznamu pomocí `<clear>` a `<remove>` elementy.</span><span class="sxs-lookup"><span data-stu-id="d6f07-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="d6f07-140">`type` Atribut `<issuerNameRegistry>` prvek musí odkazovat <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy pro `<trustedIssuers>` element platný.</span><span class="sxs-lookup"><span data-stu-id="d6f07-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6f07-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6f07-141">Example</span></span>  
 <span data-ttu-id="d6f07-142">Následující kód XML ukazuje, jak zadat vystavitele konfigurace na základě názvu registru.</span><span class="sxs-lookup"><span data-stu-id="d6f07-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d6f07-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6f07-143">See also</span></span>
- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
