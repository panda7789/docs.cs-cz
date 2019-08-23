---
title: <authentication><serviceCertificate> elementu
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: d770ba1f9a0a18c927b3a4bf6d4141286e3a380c
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919985"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="7cb1d-102">\<ověřování > \<elementu serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="7cb1d-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="7cb1d-103">Určuje nastavení používané klientským proxy serverem k ověřování certifikátů služby, které jsou získány pomocí vyjednávání protokolu SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
 <span data-ttu-id="7cb1d-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7cb1d-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="7cb1d-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="7cb1d-105">\<behaviors></span></span>  
<span data-ttu-id="7cb1d-106">oddíl endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="7cb1d-106">endpointBehaviors section</span></span>  
<span data-ttu-id="7cb1d-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="7cb1d-107">\<behavior></span></span>  
<span data-ttu-id="7cb1d-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="7cb1d-108">\<clientCredentials></span></span>  
<span data-ttu-id="7cb1d-109">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="7cb1d-109">\<serviceCertificate></span></span>  
<span data-ttu-id="7cb1d-110">\<> ověřování</span><span class="sxs-lookup"><span data-stu-id="7cb1d-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cb1d-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7cb1d-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7cb1d-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7cb1d-112">Attributes and Elements</span></span>  
 <span data-ttu-id="7cb1d-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7cb1d-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="7cb1d-114">Attributes</span></span>  
  
|<span data-ttu-id="7cb1d-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="7cb1d-115">Attribute</span></span>|<span data-ttu-id="7cb1d-116">Popis</span><span class="sxs-lookup"><span data-stu-id="7cb1d-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7cb1d-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="7cb1d-117">customCertificateValidatorType</span></span>|<span data-ttu-id="7cb1d-118">Řetezce.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-118">String.</span></span> <span data-ttu-id="7cb1d-119">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-119">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="7cb1d-120">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="7cb1d-120">certificateValidationMode</span></span>|<span data-ttu-id="7cb1d-121">Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="7cb1d-122">Pokud je nastaveno `Custom`na, je nutné zadat také CustomCertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-122">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="7cb1d-123">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-123">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="7cb1d-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="7cb1d-124">revocationMode</span></span>|<span data-ttu-id="7cb1d-125">Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="7cb1d-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="7cb1d-126">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-126">The default is `Online`.</span></span>|  
|<span data-ttu-id="7cb1d-127">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="7cb1d-127">trustedStoreLocation</span></span>|<span data-ttu-id="7cb1d-128">Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="7cb1d-128">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="7cb1d-129">Tato hodnota se používá, když je certifikát služby vyjednán klientovi.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-129">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="7cb1d-130">Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-130">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="7cb1d-131">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-131">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="7cb1d-132">customCertificateValidator – atribut</span><span class="sxs-lookup"><span data-stu-id="7cb1d-132">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="7cb1d-133">Value</span><span class="sxs-lookup"><span data-stu-id="7cb1d-133">Value</span></span>|<span data-ttu-id="7cb1d-134">Popis</span><span class="sxs-lookup"><span data-stu-id="7cb1d-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7cb1d-135">String</span><span class="sxs-lookup"><span data-stu-id="7cb1d-135">String</span></span>|<span data-ttu-id="7cb1d-136">Určuje název typu a sestavení a další data, která se používají k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-136">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="7cb1d-137">certificateValidationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="7cb1d-137">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="7cb1d-138">Value</span><span class="sxs-lookup"><span data-stu-id="7cb1d-138">Value</span></span>|<span data-ttu-id="7cb1d-139">Popis</span><span class="sxs-lookup"><span data-stu-id="7cb1d-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7cb1d-140">Výčet</span><span class="sxs-lookup"><span data-stu-id="7cb1d-140">Enumeration</span></span>|<span data-ttu-id="7cb1d-141">Jedna z následujících hodnot: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-141">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="7cb1d-142">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7cb1d-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="7cb1d-143">revocationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="7cb1d-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="7cb1d-144">Value</span><span class="sxs-lookup"><span data-stu-id="7cb1d-144">Value</span></span>|<span data-ttu-id="7cb1d-145">Popis</span><span class="sxs-lookup"><span data-stu-id="7cb1d-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7cb1d-146">Výčet</span><span class="sxs-lookup"><span data-stu-id="7cb1d-146">Enumeration</span></span>|<span data-ttu-id="7cb1d-147">Jedna z následujících hodnot: Nekontrolujte, online, offline.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-147">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="7cb1d-148">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7cb1d-148">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="7cb1d-149">trustedStoreLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="7cb1d-149">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="7cb1d-150">Value</span><span class="sxs-lookup"><span data-stu-id="7cb1d-150">Value</span></span>|<span data-ttu-id="7cb1d-151">Popis</span><span class="sxs-lookup"><span data-stu-id="7cb1d-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="7cb1d-152">Výčet</span><span class="sxs-lookup"><span data-stu-id="7cb1d-152">Enumeration</span></span>|<span data-ttu-id="7cb1d-153">Jedna z následujících hodnot: LocalMachine nebo CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-153">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="7cb1d-154">Výchozí hodnota je CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-154">The default is CurrentUser.</span></span> <span data-ttu-id="7cb1d-155">Pokud klientská aplikace běží pod účtem systému, pak je certifikát obvykle pod LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-155">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="7cb1d-156">Pokud klientská aplikace běží pod uživatelským účtem, je certifikát většinou v CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-156">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7cb1d-157">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7cb1d-157">Child Elements</span></span>  
 <span data-ttu-id="7cb1d-158">Žádné</span><span class="sxs-lookup"><span data-stu-id="7cb1d-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="7cb1d-159">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7cb1d-159">Parent Elements</span></span>  
  
|<span data-ttu-id="7cb1d-160">Prvek</span><span class="sxs-lookup"><span data-stu-id="7cb1d-160">Element</span></span>|<span data-ttu-id="7cb1d-161">Popis</span><span class="sxs-lookup"><span data-stu-id="7cb1d-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7cb1d-162">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="7cb1d-162">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="7cb1d-163">Určuje certifikát, který se má použít při ověřování služby pro klienta.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-163">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7cb1d-164">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7cb1d-164">Remarks</span></span>  
 <span data-ttu-id="7cb1d-165">`certificateValidationMode` Atribut tohoto elementu konfigurace určuje úroveň důvěryhodnosti použitou k ověřování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-165">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="7cb1d-166">Ve výchozím nastavení je úroveň nastavena na `ChainTrust`hodnotu, která určuje, že každý certifikát musí být nalezen v hierarchii certifikátů končících důvěryhodnou certifikační autoritou v horní části řetězce.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-166">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="7cb1d-167">Toto je nejbezpečnější režim.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-167">This is the most secure mode.</span></span> <span data-ttu-id="7cb1d-168">Můžete také nastavit hodnotu na `PeerOrChainTrust`, což znamená, že jsou přijímány certifikáty vystavené svým držitelem (vztah důvěryhodnosti peering) i certifikáty, které jsou v důvěryhodném řetězci.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-168">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="7cb1d-169">Tato hodnota se používá při vývoji a ladění klientů a služeb vzhledem k tomu, že certifikáty vystavené svým držitelem nemusejí být zakoupeny důvěryhodnou autoritou.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-169">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="7cb1d-170">Při nasazování klienta použijte `ChainTrust` místo něj hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-170">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="7cb1d-171">Můžete také nastavit hodnotu na `Custom` nebo. `None`</span><span class="sxs-lookup"><span data-stu-id="7cb1d-171">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="7cb1d-172">Chcete-li `Custom` použít hodnotu, je nutné také `customCertificateValidator` nastavit atribut na sestavení a typ použitý k ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-172">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="7cb1d-173">Chcete-li vytvořit vlastní validátor, je nutné dědit z abstraktní třídy X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-173">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="7cb1d-174">Další informace najdete v tématu [jak: Vytvořte službu, která využívá vlastní validátor](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)certifikátů.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-174">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="7cb1d-175">`revocationMode` Atribut určuje, jak se kontrolují certifikáty pro odvolání.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-175">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="7cb1d-176">Ve výchozím nastavení `online` to znamená, že se certifikáty budou kontrolovat automaticky pro odvolání.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-176">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="7cb1d-177">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="7cb1d-177">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7cb1d-178">Příklad</span><span class="sxs-lookup"><span data-stu-id="7cb1d-178">Example</span></span>  
 <span data-ttu-id="7cb1d-179">Následující příklad provádí dvě úlohy.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-179">The following example does two tasks.</span></span> <span data-ttu-id="7cb1d-180">Nejprve Určuje certifikát služby, který má klient použít při komunikaci s koncovými body, jejichž název domény `www.contoso.com` je přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-180">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="7cb1d-181">Za druhé určuje režim odvolání a umístění úložiště použité při ověřování.</span><span class="sxs-lookup"><span data-stu-id="7cb1d-181">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7cb1d-182">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7cb1d-182">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="7cb1d-183">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="7cb1d-183">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="7cb1d-184">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="7cb1d-184">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="7cb1d-185">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="7cb1d-185">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="7cb1d-186">\<> ověřování</span><span class="sxs-lookup"><span data-stu-id="7cb1d-186">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="7cb1d-187">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="7cb1d-187">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="7cb1d-188">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7cb1d-188">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
