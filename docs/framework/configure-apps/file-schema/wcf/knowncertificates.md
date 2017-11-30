---
title: '&lt;knownCertificates&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
caps.latest.revision: "17"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e1ce8be4dfa71685933512c1c0db36000ce93c12
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltknowncertificatesgt"></a><span data-ttu-id="7ede9-102">&lt;knownCertificates&gt;</span><span class="sxs-lookup"><span data-stu-id="7ede9-102">&lt;knownCertificates&gt;</span></span>
<span data-ttu-id="7ede9-103">Představuje kolekci certifikáty X.509, které jsou k dispozici k ověření pověření zabezpečení vydané z zabezpečení tokenu služby (STS).</span><span class="sxs-lookup"><span data-stu-id="7ede9-103">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
 <span data-ttu-id="7ede9-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="7ede9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7ede9-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7ede9-105">\<behaviors></span></span>  
<span data-ttu-id="7ede9-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="7ede9-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="7ede9-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="7ede9-107">\<behavior></span></span>  
<span data-ttu-id="7ede9-108">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="7ede9-108">\<serviceCredentials></span></span>  
<span data-ttu-id="7ede9-109">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="7ede9-109">\<issuedTokenAuthentication></span></span>  
<span data-ttu-id="7ede9-110">\<knownCertificates ></span><span class="sxs-lookup"><span data-stu-id="7ede9-110">\<knownCertificates></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7ede9-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7ede9-111">Syntax</span></span>  
  
```xml  
<knownCertificates>   
      <add findValue="String"  
         storeLocation="CurrentUser/LocalMachine"  
          storeName=" CurrentUser/LocalMachine"  
           x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"/>  
</knownCertificates>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7ede9-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7ede9-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7ede9-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7ede9-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7ede9-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="7ede9-114">Attributes</span></span>  
 <span data-ttu-id="7ede9-115">Žádné</span><span class="sxs-lookup"><span data-stu-id="7ede9-115">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7ede9-116">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7ede9-116">Child Elements</span></span>  
  
|<span data-ttu-id="7ede9-117">Prvek</span><span class="sxs-lookup"><span data-stu-id="7ede9-117">Element</span></span>|<span data-ttu-id="7ede9-118">Popis</span><span class="sxs-lookup"><span data-stu-id="7ede9-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ede9-119">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="7ede9-119">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)|<span data-ttu-id="7ede9-120">Certifikát X.509 přidá do kolekce.</span><span class="sxs-lookup"><span data-stu-id="7ede9-120">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7ede9-121">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7ede9-121">Parent Elements</span></span>  
  
|<span data-ttu-id="7ede9-122">Prvek</span><span class="sxs-lookup"><span data-stu-id="7ede9-122">Element</span></span>|<span data-ttu-id="7ede9-123">Popis</span><span class="sxs-lookup"><span data-stu-id="7ede9-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7ede9-124">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="7ede9-124">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="7ede9-125">Určuje tokenem vydaným jako přihlašovací údaje služby.</span><span class="sxs-lookup"><span data-stu-id="7ede9-125">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7ede9-126">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ede9-126">Remarks</span></span>  
 <span data-ttu-id="7ede9-127">Vystavený token scénář má tři fáze.</span><span class="sxs-lookup"><span data-stu-id="7ede9-127">The issued token scenario has three stages.</span></span> <span data-ttu-id="7ede9-128">V první fázi se klient pokouší o přístup ke službě označuje *služby tokenů zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="7ede9-128">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="7ede9-129">Službu tokenů zabezpečení pak ověřuje klienta a následně vydá klienta token, obvykle token zabezpečení kontrolní výrazy Markup Language (SAML).</span><span class="sxs-lookup"><span data-stu-id="7ede9-129">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="7ede9-130">Klient pak vrátí ke službě pomocí tokenu.</span><span class="sxs-lookup"><span data-stu-id="7ede9-130">The client then returns to the service with the token.</span></span> <span data-ttu-id="7ede9-131">Služba prověří token pro data, která umožňuje službě ověření tokenu a proto klienta.</span><span class="sxs-lookup"><span data-stu-id="7ede9-131">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="7ede9-132">K ověření tokenu, certifikátu používá zabezpečené tokenu služby musí být známo ke službě.</span><span class="sxs-lookup"><span data-stu-id="7ede9-132">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="7ede9-133">[ \<IssuedTokenAuthentication >](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element slouží jako úložiště pro všechny zabezpečené služby tokenů certifikáty.</span><span class="sxs-lookup"><span data-stu-id="7ede9-133">The [\<issuedTokenAuthentication>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="7ede9-134">Chcete-li přidat certifikáty, použijte [ \<knownCertificates > element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="7ede9-134">To add certificates, use the [\<knownCertificates> element](../../../../../docs/framework/configure-apps/file-schema/wcf/knowncertificates.md).</span></span> <span data-ttu-id="7ede9-135">Vložit [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) pro každý certifikát, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="7ede9-135">Insert an [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>  
   <knownCertificates>  
      <add findValue="www.contoso.com"   
           storeLocation="LocalMachine" storeName="My"   
           X509FindType="FindBySubjectName" />  
    </knownCertificates>  
</issuedTokenAuthentication>  
```  
  
 <span data-ttu-id="7ede9-136">Ve výchozím nastavení musí získat certifikáty ze služby tokenu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="7ede9-136">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="7ede9-137">Tyto "známé" certifikáty, ujistěte se, že který pouze oprávněné klientů můžete přístup ke službě.</span><span class="sxs-lookup"><span data-stu-id="7ede9-137">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="7ede9-138">Podmínky pro klienta k ověření pomocí federované služby a také další informace o použití tohoto elementu konfigurace najdete v tématu [postupy: Konfigurace pověření ve službě Federation](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="7ede9-138">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="7ede9-139">Další informace o federovaných scénářích najdete v tématu [federace a vystavené tokeny](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="7ede9-139">For more information about federated scenarios, see [Federation and Issued Tokens](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="7ede9-140">Příklad, který ukazuje, jak k naplnění kolekce v konfiguraci, naleznete v části [ \<Přidat >](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="7ede9-140">For an example that shows how to populate the collection in configuration, see [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7ede9-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="7ede9-141">See Also</span></span>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>  
 <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>  
 <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>  
 <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>  
 <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>  
 [<span data-ttu-id="7ede9-142">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="7ede9-142">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [<span data-ttu-id="7ede9-143">\<issuedTokenAuthentication ></span><span class="sxs-lookup"><span data-stu-id="7ede9-143">\<issuedTokenAuthentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/issuedtokenauthentication-of-servicecredentials.md)  
 [<span data-ttu-id="7ede9-144">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7ede9-144">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="7ede9-145">Postupy: Konfigurace pověření ve službě Federation</span><span class="sxs-lookup"><span data-stu-id="7ede9-145">How to: Configure Credentials on a Federation Service</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [<span data-ttu-id="7ede9-146">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="7ede9-146">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="7ede9-147">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="7ede9-147">Federation and Issued Tokens</span></span>](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)  
 [<span data-ttu-id="7ede9-148">\<Přidat ></span><span class="sxs-lookup"><span data-stu-id="7ede9-148">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-knowncertificates.md)  
 [<span data-ttu-id="7ede9-149">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7ede9-149">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
