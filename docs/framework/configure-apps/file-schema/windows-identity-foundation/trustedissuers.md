---
title: <trustedIssuers>
ms.date: 03/30/2017
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
author: BrucePerlerMS
ms.openlocfilehash: cebfc2f3598f32f233db6039dfe82076d2ffce46
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59221701"
---
# <a name="trustedissuers"></a><span data-ttu-id="1d022-101">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="1d022-101">\<trustedIssuers></span></span>
<span data-ttu-id="1d022-102">Nakonfiguruje seznam důvěryhodných vystavitelů certifikátů používané registru názvu vystavitele založená na konfiguraci (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span><span class="sxs-lookup"><span data-stu-id="1d022-102">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="1d022-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1d022-103">\<system.identityModel></span></span>  
<span data-ttu-id="1d022-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="1d022-104">\<identityConfiguration></span></span>  
<span data-ttu-id="1d022-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="1d022-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="1d022-106">\<securityTokenHandlerConfiguration></span><span class="sxs-lookup"><span data-stu-id="1d022-106">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="1d022-107">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="1d022-107">\<issuerNameRegistry></span></span>  
<span data-ttu-id="1d022-108">\<trustedIssuers></span><span class="sxs-lookup"><span data-stu-id="1d022-108">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1d022-109">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="1d022-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1d022-110">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="1d022-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1d022-111">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="1d022-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1d022-112">Atributy</span><span class="sxs-lookup"><span data-stu-id="1d022-112">Attributes</span></span>  
 <span data-ttu-id="1d022-113">Žádný</span><span class="sxs-lookup"><span data-stu-id="1d022-113">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1d022-114">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="1d022-114">Child Elements</span></span>  
  
|<span data-ttu-id="1d022-115">Prvek</span><span class="sxs-lookup"><span data-stu-id="1d022-115">Element</span></span>|<span data-ttu-id="1d022-116">Popis</span><span class="sxs-lookup"><span data-stu-id="1d022-116">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="1d022-117">Přidá certifikát do kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="1d022-117">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="1d022-118">Certifikát se zadaným `thumbprint` atribut.</span><span class="sxs-lookup"><span data-stu-id="1d022-118">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="1d022-119">Tento atribut je vyžadován a musí obsahovat ASN.1 kódované podobě kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="1d022-119">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="1d022-120">`name` Atribut je volitelný a je možné zadat popisný název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="1d022-120">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="1d022-121">Vymaže všechny certifikáty z kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="1d022-121">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="1d022-122">Certifikát se odebere z kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="1d022-122">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="1d022-123">Certifikát se zadaným `thumbprint` atribut.</span><span class="sxs-lookup"><span data-stu-id="1d022-123">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="1d022-124">Tento atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="1d022-124">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1d022-125">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="1d022-125">Parent Elements</span></span>  
  
|<span data-ttu-id="1d022-126">Prvek</span><span class="sxs-lookup"><span data-stu-id="1d022-126">Element</span></span>|<span data-ttu-id="1d022-127">Popis</span><span class="sxs-lookup"><span data-stu-id="1d022-127">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1d022-128">\<issuerNameRegistry></span><span class="sxs-lookup"><span data-stu-id="1d022-128">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="1d022-129">Nakonfiguruje registru názvu vystavitele.</span><span class="sxs-lookup"><span data-stu-id="1d022-129">Configures the issuer name registry.</span></span> <span data-ttu-id="1d022-130">**Důležité:**  `type` Atribut `<issuerNameRegistry>` prvek musí odkazovat <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy pro `<trustedIssuers>` element platný.</span><span class="sxs-lookup"><span data-stu-id="1d022-130">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1d022-131">Poznámky</span><span class="sxs-lookup"><span data-stu-id="1d022-131">Remarks</span></span>  
 <span data-ttu-id="1d022-132">Technologie Windows Identity Foundation (WIF) poskytuje jedna implementace položky <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třídy hned po spuštění <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="1d022-132">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="1d022-133">Konfigurace registru názvu vystavitele udržuje seznam důvěryhodných vystavitelů, který je načten z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="1d022-133">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="1d022-134">V seznamu přidruží každý název vystavitele, která je potřeba ověřit podpis tokeny vytvářených vystavitele certifikátu X.509.</span><span class="sxs-lookup"><span data-stu-id="1d022-134">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="1d022-135">Seznam důvěryhodných vystavitelů certifikátů se zadává v části `<trustedIssuers>` elementu.</span><span class="sxs-lookup"><span data-stu-id="1d022-135">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="1d022-136">Každý prvek v seznamu přidruží mnemonická vystavitele certifikátu X.509, který je potřeba k ověření podpisu tokeny vytvářených tohoto vydavatele.</span><span class="sxs-lookup"><span data-stu-id="1d022-136">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="1d022-137">Důvěryhodné certifikáty jsou zadány pomocí ASN.1 kódovaný formu kryptografický otisk certifikátu a jsou přidány do kolekce pomocí `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="1d022-137">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="1d022-138">Můžete vymazat nebo odebrání vystavitele (certifikáty) ze seznamu pomocí `<clear>` a `<remove>` elementy.</span><span class="sxs-lookup"><span data-stu-id="1d022-138">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="1d022-139">`type` Atribut `<issuerNameRegistry>` prvek musí odkazovat <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy pro `<trustedIssuers>` element platný.</span><span class="sxs-lookup"><span data-stu-id="1d022-139">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d022-140">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d022-140">Example</span></span>  
 <span data-ttu-id="1d022-141">Následující kód XML ukazuje, jak zadat vystavitele konfigurace na základě názvu registru.</span><span class="sxs-lookup"><span data-stu-id="1d022-141">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1d022-142">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1d022-142">See also</span></span>

- <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>
- <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
