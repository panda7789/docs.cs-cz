---
title: '&lt;trustedIssuers&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d818c917-07b4-40db-9801-8676561859fd
caps.latest.revision: "7"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 33ef3ca88462595d81d269a92a643b43c9aea025
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lttrustedissuersgt"></a><span data-ttu-id="265d6-102">&lt;trustedIssuers&gt;</span><span class="sxs-lookup"><span data-stu-id="265d6-102">&lt;trustedIssuers&gt;</span></span>
<span data-ttu-id="265d6-103">Nakonfiguruje seznam důvěryhodných vystavitelů certifikátů používaných registru název vystavitele založené na konfiguraci (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span><span class="sxs-lookup"><span data-stu-id="265d6-103">Configures the list of trusted issuer certificates used by the configuration-based issuer name registry (<xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>).</span></span>  
  
 <span data-ttu-id="265d6-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="265d6-104">\<system.identityModel></span></span>  
<span data-ttu-id="265d6-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="265d6-105">\<identityConfiguration></span></span>  
<span data-ttu-id="265d6-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="265d6-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="265d6-107">\<securityTokenHandlerConfiguration ></span><span class="sxs-lookup"><span data-stu-id="265d6-107">\<securityTokenHandlerConfiguration></span></span>  
<span data-ttu-id="265d6-108">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="265d6-108">\<issuerNameRegistry></span></span>  
<span data-ttu-id="265d6-109">\<trustedIssuers ></span><span class="sxs-lookup"><span data-stu-id="265d6-109">\<trustedIssuers></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="265d6-110">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="265d6-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="265d6-111">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="265d6-111">Attributes and Elements</span></span>  
 <span data-ttu-id="265d6-112">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="265d6-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="265d6-113">Atributy</span><span class="sxs-lookup"><span data-stu-id="265d6-113">Attributes</span></span>  
 <span data-ttu-id="265d6-114">Žádné</span><span class="sxs-lookup"><span data-stu-id="265d6-114">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="265d6-115">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="265d6-115">Child Elements</span></span>  
  
|<span data-ttu-id="265d6-116">Prvek</span><span class="sxs-lookup"><span data-stu-id="265d6-116">Element</span></span>|<span data-ttu-id="265d6-117">Popis</span><span class="sxs-lookup"><span data-stu-id="265d6-117">Description</span></span>|  
|-------------|-----------------|  
|`<add thumbprint=xs:string name=xs:string>`|<span data-ttu-id="265d6-118">Přidá certifikát do kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="265d6-118">Adds a certificate to the collection of trusted issuers.</span></span> <span data-ttu-id="265d6-119">Certifikát zadaný `thumbprint` atribut.</span><span class="sxs-lookup"><span data-stu-id="265d6-119">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="265d6-120">Tento atribut je povinný a musí obsahovat kódovaný ASN.1 formu kryptografický otisk certifikátu.</span><span class="sxs-lookup"><span data-stu-id="265d6-120">This attribute is required and should contain the ASN.1 encoded form of the certificate thumbprint.</span></span> <span data-ttu-id="265d6-121">`name` Atribut je volitelné a lze zadat popisný název certifikátu.</span><span class="sxs-lookup"><span data-stu-id="265d6-121">The `name` attribute is optional and can be used to specify a friendly name for the certificate.</span></span>|  
|`<clear>`|<span data-ttu-id="265d6-122">Vymaže všechny certifikáty z kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="265d6-122">Clears all certificates from the collection of trusted issuers.</span></span>|  
|`<remove thumbprint=xs:string>`|<span data-ttu-id="265d6-123">Odebere certifikát z kolekce důvěryhodných vystavitelů.</span><span class="sxs-lookup"><span data-stu-id="265d6-123">Removes a certificate from the collection of trusted issuers.</span></span> <span data-ttu-id="265d6-124">Certifikát zadaný `thumbprint` atribut.</span><span class="sxs-lookup"><span data-stu-id="265d6-124">The certificate is specified with the `thumbprint` attribute.</span></span> <span data-ttu-id="265d6-125">Tento atribut je vyžadován.</span><span class="sxs-lookup"><span data-stu-id="265d6-125">This attribute is required.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="265d6-126">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="265d6-126">Parent Elements</span></span>  
  
|<span data-ttu-id="265d6-127">Prvek</span><span class="sxs-lookup"><span data-stu-id="265d6-127">Element</span></span>|<span data-ttu-id="265d6-128">Popis</span><span class="sxs-lookup"><span data-stu-id="265d6-128">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="265d6-129">\<issuerNameRegistry ></span><span class="sxs-lookup"><span data-stu-id="265d6-129">\<issuerNameRegistry></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)|<span data-ttu-id="265d6-130">Nakonfiguruje registru název vystavitele.</span><span class="sxs-lookup"><span data-stu-id="265d6-130">Configures the issuer name registry.</span></span> <span data-ttu-id="265d6-131">**Důležité:** `type` atribut `<issuerNameRegistry>` element musí odkazovat <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy pro `<trustedIssuers>` elementu platný.</span><span class="sxs-lookup"><span data-stu-id="265d6-131">**Important:**  The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="265d6-132">Poznámky</span><span class="sxs-lookup"><span data-stu-id="265d6-132">Remarks</span></span>  
 <span data-ttu-id="265d6-133">Windows Identity Foundation (WIF) poskytuje jedna implementace položky <xref:System.IdentityModel.Tokens.IssuerNameRegistry> třída předinstalované, <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy.</span><span class="sxs-lookup"><span data-stu-id="265d6-133">Windows Identity Foundation (WIF) provides a single implementation of the <xref:System.IdentityModel.Tokens.IssuerNameRegistry> class out of the box, the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class.</span></span> <span data-ttu-id="265d6-134">Konfigurace registru název vystavitele udržuje seznam důvěryhodných vystavitelů, který je načten z konfigurace.</span><span class="sxs-lookup"><span data-stu-id="265d6-134">The configuration issuer name registry maintains a list of trusted issuers that is loaded from configuration.</span></span> <span data-ttu-id="265d6-135">V seznamu přidruží každý název vystavitele certifikátu X.509, který je třeba ověřit podpis tokeny vyprodukované vystavitele.</span><span class="sxs-lookup"><span data-stu-id="265d6-135">The list associates each issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by the issuer.</span></span> <span data-ttu-id="265d6-136">Seznam důvěryhodných vystavitelů certifikátů je zadaný v `<trustedIssuers>` elementu.</span><span class="sxs-lookup"><span data-stu-id="265d6-136">The list of trusted issuer certificates is specified under the `<trustedIssuers>` element.</span></span> <span data-ttu-id="265d6-137">Každý prvek v seznamu přidruží název klávesovými vystavitele certifikátu X.509, který je třeba ověřit podpis tokeny vyprodukované této vystavitele.</span><span class="sxs-lookup"><span data-stu-id="265d6-137">Each element in the list associates a mnemonic issuer name with the X.509 certificate that is needed to verify the signature of tokens produced by that issuer.</span></span> <span data-ttu-id="265d6-138">Důvěryhodné certifikáty jsou zadány pomocí ASN.1 kódovaný formu kryptografický otisk certifikátu a kolekce se přidají pomocí `<add>` elementu.</span><span class="sxs-lookup"><span data-stu-id="265d6-138">Trusted certificates are specified using the ASN.1 encoded form of the certificate thumbprint and are added the collection by using `<add>` element.</span></span> <span data-ttu-id="265d6-139">Můžete vyčistit nebo můžete odebrat ze seznamu vystavitelů (certifikáty) pomocí `<clear>` a `<remove>` elementy.</span><span class="sxs-lookup"><span data-stu-id="265d6-139">You can clear or remove issuers (certificates) from the list by using the `<clear>` and `<remove>` elements.</span></span>  
  
 <span data-ttu-id="265d6-140">`type` Atribut `<issuerNameRegistry>` element musí odkazovat <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> třídy pro `<trustedIssuers>` elementu platný.</span><span class="sxs-lookup"><span data-stu-id="265d6-140">The `type` attribute of the `<issuerNameRegistry>` element must reference the <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry> class for the `<trustedIssuers>` element to be valid.</span></span>  
  
## <a name="example"></a><span data-ttu-id="265d6-141">Příklad</span><span class="sxs-lookup"><span data-stu-id="265d6-141">Example</span></span>  
 <span data-ttu-id="265d6-142">Následující kód XML ukazuje, jak zadat konfiguraci na základě vystavitele název registru.</span><span class="sxs-lookup"><span data-stu-id="265d6-142">The following XML shows how to specify the configuration based issuer name registry.</span></span>  
  
```xml  
<issuerNameRegistry type="System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry, System.IdentityModel, Version=4.0.0.0, Culture=neutral, PublicKeyToken=b77a5c561934e089">  
  <trustedIssuers>  
    <add thumbprint="9B74CB2F32 … B1DC01EF40D0" name="LocalSTS" />  
  </trustedIssuers>  
</issuerNameRegistry>  
```  
  
## <a name="see-also"></a><span data-ttu-id="265d6-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="265d6-143">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.ConfigurationBasedIssuerNameRegistry>  
 <xref:System.IdentityModel.Tokens.IssuerNameRegistry>
