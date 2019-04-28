---
title: <authentication> z <serviceCertificate> – Element
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: b96d53312d672eebd67de82f69cd9a0a2b5bd22e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61704463"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="6b742-102">\<ověřování > z \<serviceCertificate > – Element</span><span class="sxs-lookup"><span data-stu-id="6b742-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="6b742-103">Určuje nastavení klientského serveru proxy k ověření certifikátů služby, které jsou získány pomocí vyjednávání protokolu SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="6b742-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
 <span data-ttu-id="6b742-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="6b742-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="6b742-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="6b742-105">\<behaviors></span></span>  
<span data-ttu-id="6b742-106">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="6b742-106">endpointBehaviors section</span></span>  
<span data-ttu-id="6b742-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="6b742-107">\<behavior></span></span>  
<span data-ttu-id="6b742-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="6b742-108">\<clientCredentials></span></span>  
<span data-ttu-id="6b742-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="6b742-109">\<serviceCertificate></span></span>  
<span data-ttu-id="6b742-110">\<ověřování ></span><span class="sxs-lookup"><span data-stu-id="6b742-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6b742-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="6b742-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6b742-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="6b742-112">Attributes and Elements</span></span>  
 <span data-ttu-id="6b742-113">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6b742-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6b742-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="6b742-114">Attributes</span></span>  
  
|<span data-ttu-id="6b742-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="6b742-115">Attribute</span></span>|<span data-ttu-id="6b742-116">Popis</span><span class="sxs-lookup"><span data-stu-id="6b742-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6b742-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="6b742-117">customCertificateValidatorType</span></span>|<span data-ttu-id="6b742-118">řetězec.</span><span class="sxs-lookup"><span data-stu-id="6b742-118">String.</span></span> <span data-ttu-id="6b742-119">Typ a sestavení používané pro ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="6b742-119">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="6b742-120">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="6b742-120">certificateValidationMode</span></span>|<span data-ttu-id="6b742-121">Určuje jeden ze tří režimů používaných pro ověření pověření.</span><span class="sxs-lookup"><span data-stu-id="6b742-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="6b742-122">Pokud hodnotu `Custom`, pak musí být rovněž dodán customCertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="6b742-122">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="6b742-123">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="6b742-123">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="6b742-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="6b742-124">revocationMode</span></span>|<span data-ttu-id="6b742-125">Jeden z režimů pro kontrolu seznamu odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="6b742-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="6b742-126">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="6b742-126">The default is `Online`.</span></span>|  
|<span data-ttu-id="6b742-127">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="6b742-127">trustedStoreLocation</span></span>|<span data-ttu-id="6b742-128">Jeden z umístění dvou systémových úložišť: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="6b742-128">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="6b742-129">Tato hodnota se používá při certifikát služby se vyjedná do klienta.</span><span class="sxs-lookup"><span data-stu-id="6b742-129">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="6b742-130">Ověření se provádí proti **důvěryhodné osoby** uložit do umístění určeného úložiště.</span><span class="sxs-lookup"><span data-stu-id="6b742-130">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="6b742-131">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="6b742-131">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="6b742-132">customCertificateValidator atribut</span><span class="sxs-lookup"><span data-stu-id="6b742-132">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="6b742-133">Value</span><span class="sxs-lookup"><span data-stu-id="6b742-133">Value</span></span>|<span data-ttu-id="6b742-134">Popis</span><span class="sxs-lookup"><span data-stu-id="6b742-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b742-135">String</span><span class="sxs-lookup"><span data-stu-id="6b742-135">String</span></span>|<span data-ttu-id="6b742-136">Určuje název typu a sestavení a další data použít k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="6b742-136">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="6b742-137">certificateValidationMode atribut</span><span class="sxs-lookup"><span data-stu-id="6b742-137">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="6b742-138">Value</span><span class="sxs-lookup"><span data-stu-id="6b742-138">Value</span></span>|<span data-ttu-id="6b742-139">Popis</span><span class="sxs-lookup"><span data-stu-id="6b742-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b742-140">Výčet</span><span class="sxs-lookup"><span data-stu-id="6b742-140">Enumeration</span></span>|<span data-ttu-id="6b742-141">Jeden z následujících hodnot: NONE, PeerTrust, ChainTrust, PeerOrChainTrust, vlastní.</span><span class="sxs-lookup"><span data-stu-id="6b742-141">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="6b742-142">Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6b742-142">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="6b742-143">revocationMode atribut</span><span class="sxs-lookup"><span data-stu-id="6b742-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="6b742-144">Value</span><span class="sxs-lookup"><span data-stu-id="6b742-144">Value</span></span>|<span data-ttu-id="6b742-145">Popis</span><span class="sxs-lookup"><span data-stu-id="6b742-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b742-146">Výčet</span><span class="sxs-lookup"><span data-stu-id="6b742-146">Enumeration</span></span>|<span data-ttu-id="6b742-147">Jeden z následujících hodnot: NoCheck, Online, Offline.</span><span class="sxs-lookup"><span data-stu-id="6b742-147">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="6b742-148">Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6b742-148">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="6b742-149">trustedStoreLocation atribut</span><span class="sxs-lookup"><span data-stu-id="6b742-149">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="6b742-150">Value</span><span class="sxs-lookup"><span data-stu-id="6b742-150">Value</span></span>|<span data-ttu-id="6b742-151">Popis</span><span class="sxs-lookup"><span data-stu-id="6b742-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="6b742-152">Výčet</span><span class="sxs-lookup"><span data-stu-id="6b742-152">Enumeration</span></span>|<span data-ttu-id="6b742-153">Jeden z následujících hodnot: LocalMachine nebo CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="6b742-153">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="6b742-154">Výchozí hodnota je CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="6b742-154">The default is CurrentUser.</span></span> <span data-ttu-id="6b742-155">Pokud klientská aplikace běží pod účtem systému, certifikátu je obvykle v rámci LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="6b742-155">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="6b742-156">Pokud klientská aplikace běží pod účtem uživatele, certifikát je obvykle v CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="6b742-156">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6b742-157">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="6b742-157">Child Elements</span></span>  
 <span data-ttu-id="6b742-158">Žádné</span><span class="sxs-lookup"><span data-stu-id="6b742-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6b742-159">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="6b742-159">Parent Elements</span></span>  
  
|<span data-ttu-id="6b742-160">Prvek</span><span class="sxs-lookup"><span data-stu-id="6b742-160">Element</span></span>|<span data-ttu-id="6b742-161">Popis</span><span class="sxs-lookup"><span data-stu-id="6b742-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6b742-162">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="6b742-162">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="6b742-163">Určuje certifikát používaný při ověřování služby ke klientovi.</span><span class="sxs-lookup"><span data-stu-id="6b742-163">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6b742-164">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6b742-164">Remarks</span></span>  
 <span data-ttu-id="6b742-165">`certificateValidationMode` Atribut tento prvek konfigurace určuje úroveň vztahu důvěryhodnosti používá k ověřování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="6b742-165">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="6b742-166">Ve výchozím nastavení, úroveň je nastavena `ChainTrust`, která určuje, že každý certifikát musí být nalezena v hierarchii certifikátů důvěryhodné certifikační autority v horní části řetězce s koncovkou.</span><span class="sxs-lookup"><span data-stu-id="6b742-166">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="6b742-167">Toto je nejbezpečnější režim.</span><span class="sxs-lookup"><span data-stu-id="6b742-167">This is the most secure mode.</span></span> <span data-ttu-id="6b742-168">Můžete také nastavit hodnotu `PeerOrChainTrust`, která určuje, že jsou přijímány samostatně vydané certifikáty (peer vztahu důvěryhodnosti) a také certifikáty, které jsou v důvěryhodným řetězem.</span><span class="sxs-lookup"><span data-stu-id="6b742-168">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="6b742-169">Tato hodnota se používá při vývoji a ladění klientů a služeb, protože samostatně vydané certifikáty nemusí být zakoupenému od důvěryhodné autority.</span><span class="sxs-lookup"><span data-stu-id="6b742-169">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="6b742-170">Při nasazování klienta, použijte `ChainTrust` místo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="6b742-170">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="6b742-171">Můžete také nastavit hodnotu `Custom` nebo `None`.</span><span class="sxs-lookup"><span data-stu-id="6b742-171">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="6b742-172">Použít `Custom` hodnotu, je nutné nastavit také `customCertificateValidator` atribut na sestavení a typ použitý k ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="6b742-172">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="6b742-173">Pokud chcete vytvořit vlastní vlastní validátor, musí dědit z abstraktní třídy X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="6b742-173">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="6b742-174">Další informace najdete v tématu [jak: Vytvoření služby, která používá vlastní validátor certifikátů](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="6b742-174">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="6b742-175">`revocationMode` Atribut určuje, jak kontroluje odvolání certifikátů.</span><span class="sxs-lookup"><span data-stu-id="6b742-175">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="6b742-176">Výchozí hodnota je `online` což znamená, že certifikáty se automaticky vráceny na zrušení.</span><span class="sxs-lookup"><span data-stu-id="6b742-176">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="6b742-177">Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="6b742-177">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b742-178">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b742-178">Example</span></span>  
 <span data-ttu-id="6b742-179">Následující příklad provádí dvě úlohy.</span><span class="sxs-lookup"><span data-stu-id="6b742-179">The following example does two tasks.</span></span> <span data-ttu-id="6b742-180">Určuje první certifikát služby pro klienty při komunikaci s koncovými body, jejichž název domény je `www.contoso.com` přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="6b742-180">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="6b742-181">Za druhé Určuje odvolání režimu a úložiště umístění použité během ověřování.</span><span class="sxs-lookup"><span data-stu-id="6b742-181">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
```xml  
<serviceCertificate>
  <defaultCertificate findValue="www.contoso.com"
                      storeLocation="LocalMachine"
                      storeName="TrustedPeople"
                      x509FindType="FindByIssuerDistinguishedName" />
  <scopedCertificates>
     <add targetUri="http://www.contoso.com"
          findValue="www.contoso.com"
          storeLocation="LocalMachine"
          storeName="Root"
          x509FindType="FindByIssuerName" />
  </scopedCertificates>
  <authentication revocationMode="Online"
                  trustedStoreLocation="LocalMachine" />
</serviceCertificate>
```  
  
## <a name="see-also"></a><span data-ttu-id="6b742-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6b742-182">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="6b742-183">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="6b742-183">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="6b742-184">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="6b742-184">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="6b742-185">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="6b742-185">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="6b742-186">\<authentication></span><span class="sxs-lookup"><span data-stu-id="6b742-186">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="6b742-187">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="6b742-187">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)
- [<span data-ttu-id="6b742-188">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="6b742-188">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
