---
title: <knownCertificates>
ms.date: 03/30/2017
ms.assetid: 678e21b4-6493-47c3-8359-fcf0d37e2138
ms.openlocfilehash: 23fe19258e09e9e8a5e05a94ccef0e40ee1cb5fd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400326"
---
# \<knownCertificates>
<span data-ttu-id="03bfa-101">Představuje kolekci certifikátů X. 509, které jsou k dispozici pro ověřování bezpečnostních přihlašovacích údajů vydaných službou tokenu zabezpečení (STS).</span><span class="sxs-lookup"><span data-stu-id="03bfa-101">Represents a collection of X.509 certificates that are provided to authenticate security credentials issued from a Security Token Service (STS).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<issuedTokenAuthentication>**](issuedtokenauthentication-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<knownCertificates>**  
  
## <a name="syntax"></a><span data-ttu-id="03bfa-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03bfa-102">Syntax</span></span>  
  
```xml  
<knownCertificates>
  <add findValue="String"
       storeLocation="CurrentUser/LocalMachine"
       storeName=" CurrentUser/LocalMachine"
       x509FindType="FindByThumbprint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindBySerialNumber/FindByTimeExpired/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
</knownCertificates>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="03bfa-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="03bfa-103">Attributes and Elements</span></span>  
 <span data-ttu-id="03bfa-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="03bfa-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="03bfa-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="03bfa-105">Attributes</span></span>  
 <span data-ttu-id="03bfa-106">Žádné</span><span class="sxs-lookup"><span data-stu-id="03bfa-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="03bfa-107">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="03bfa-107">Child Elements</span></span>  
  
|<span data-ttu-id="03bfa-108">Prvek</span><span class="sxs-lookup"><span data-stu-id="03bfa-108">Element</span></span>|<span data-ttu-id="03bfa-109">Description</span><span class="sxs-lookup"><span data-stu-id="03bfa-109">Description</span></span>|  
|-------------|-----------------|  
|[\<add>](add-of-knowncertificates.md)|<span data-ttu-id="03bfa-110">Přidá do kolekce certifikát X. 509.</span><span class="sxs-lookup"><span data-stu-id="03bfa-110">Adds an X.509 certificate to the collection.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="03bfa-111">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="03bfa-111">Parent Elements</span></span>  
  
|<span data-ttu-id="03bfa-112">Prvek</span><span class="sxs-lookup"><span data-stu-id="03bfa-112">Element</span></span>|<span data-ttu-id="03bfa-113">Description</span><span class="sxs-lookup"><span data-stu-id="03bfa-113">Description</span></span>|  
|-------------|-----------------|  
|[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)|<span data-ttu-id="03bfa-114">Určuje token vydaný jako pověření služby.</span><span class="sxs-lookup"><span data-stu-id="03bfa-114">Specifies a token issued as a service credential.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03bfa-115">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03bfa-115">Remarks</span></span>  
 <span data-ttu-id="03bfa-116">Scénář vydaného tokenu má tři fáze.</span><span class="sxs-lookup"><span data-stu-id="03bfa-116">The issued token scenario has three stages.</span></span> <span data-ttu-id="03bfa-117">V první fázi se klientovi, který se pokouší o přístup ke službě, říká *služba tokenů zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="03bfa-117">In the first stage, a client trying to access a service is referred to a *secure token service*.</span></span> <span data-ttu-id="03bfa-118">Služba tokenů zabezpečení potom ověří klienta a následně vydá token klienta, obvykle token SAML (Security Assert Markup Language).</span><span class="sxs-lookup"><span data-stu-id="03bfa-118">The secure token service then authenticates the client and subsequently issues the client a token, typically a Security Assertions Markup Language (SAML) token.</span></span> <span data-ttu-id="03bfa-119">Klient se pak vrátí ke službě s tokenem.</span><span class="sxs-lookup"><span data-stu-id="03bfa-119">The client then returns to the service with the token.</span></span> <span data-ttu-id="03bfa-120">Služba prověřuje token pro data, která umožňují službě ověřit token, a tedy klienta.</span><span class="sxs-lookup"><span data-stu-id="03bfa-120">The service examines the token for data that allows the service to authenticate the token and therefore the client.</span></span> <span data-ttu-id="03bfa-121">Chcete-li ověřit token, je nutné, aby služba používala certifikát, který používá služba tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="03bfa-121">To authenticate the token, the certificate the secure token service uses must be known to the service.</span></span>  
  
 <span data-ttu-id="03bfa-122">[\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)Element je úložištěm těchto certifikátů služby tokenů zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="03bfa-122">The [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md) element is the repository for any such secure token service certificates.</span></span> <span data-ttu-id="03bfa-123">Chcete-li přidat certifikáty, použijte [ \<knownCertificates> element](knowncertificates.md).</span><span class="sxs-lookup"><span data-stu-id="03bfa-123">To add certificates, use the [\<knownCertificates> element](knowncertificates.md).</span></span> <span data-ttu-id="03bfa-124">Vložte [\<add>](add-of-knowncertificates.md) pro každý certifikát, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="03bfa-124">Insert an [\<add>](add-of-knowncertificates.md) for each certificate, as shown in the following example.</span></span>  
  
```xml  
<issuedTokenAuthentication>
  <knownCertificates>
    <add findValue="www.contoso.com"
         storeLocation="LocalMachine"
         storeName="My"
         X509FindType="FindBySubjectName" />
  </knownCertificates>
</issuedTokenAuthentication>
```  
  
 <span data-ttu-id="03bfa-125">Ve výchozím nastavení se certifikáty musí získat ze služby zabezpečeného tokenu.</span><span class="sxs-lookup"><span data-stu-id="03bfa-125">By default, the certificates must be obtained from a secure token service.</span></span> <span data-ttu-id="03bfa-126">Tyto "známé" certifikáty zajistí, že ke službě budou mít přístup jenom legitimní klienti.</span><span class="sxs-lookup"><span data-stu-id="03bfa-126">These "known" certificates ensure that only legitimate clients can access a service.</span></span>  
  
 <span data-ttu-id="03bfa-127">Chcete-li zkontrolovat podmínky požadované pro ověření klienta federované službou a další informace o použití tohoto prvku konfigurace, přečtěte si téma [How to: Configure a Credentials on a služba FS (Federation Service)](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span><span class="sxs-lookup"><span data-stu-id="03bfa-127">To review conditions required for a client to be authenticated by a federated service, as well as more information on using this configuration element, see [How to: Configure Credentials on a Federation Service](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md).</span></span> <span data-ttu-id="03bfa-128">Další informace o federovaných scénářích najdete v tématu [federace a vystavené tokeny](../../../wcf/feature-details/federation-and-issued-tokens.md).</span><span class="sxs-lookup"><span data-stu-id="03bfa-128">For more information about federated scenarios, see [Federation and Issued Tokens](../../../wcf/feature-details/federation-and-issued-tokens.md).</span></span>  
  
 <span data-ttu-id="03bfa-129">Příklad, který ukazuje, jak naplnit kolekci v konfiguraci, najdete v tématu [\<add>](add-of-knowncertificates.md) .</span><span class="sxs-lookup"><span data-stu-id="03bfa-129">For an example that shows how to populate the collection in configuration, see [\<add>](add-of-knowncertificates.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="03bfa-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="03bfa-130">See also</span></span>

- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AllowedAudienceUris%2A>
- <xref:System.IdentityModel.Selectors.SamlSecurityTokenAuthenticator.AudienceUriMode%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenServiceElement.KnownCertificates%2A>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElementCollection>
- <xref:System.ServiceModel.Configuration.X509CertificateTrustedIssuerElement>
- <xref:System.ServiceModel.Security.IssuedTokenServiceCredential.KnownCertificates%2A>
- [\<add>](add-of-knowncertificates.md)
- [\<issuedTokenAuthentication>](issuedtokenauthentication-of-servicecredentials.md)
- [<span data-ttu-id="03bfa-131">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="03bfa-131">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="03bfa-132">Postupy: Konfigurace pověření ve službě Federation Service</span><span class="sxs-lookup"><span data-stu-id="03bfa-132">How to: Configure Credentials on a Federation Service</span></span>](../../../wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [<span data-ttu-id="03bfa-133">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="03bfa-133">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="03bfa-134">Federace a vystavené tokeny</span><span class="sxs-lookup"><span data-stu-id="03bfa-134">Federation and Issued Tokens</span></span>](../../../wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](add-of-knowncertificates.md)
- [<span data-ttu-id="03bfa-135">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="03bfa-135">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
