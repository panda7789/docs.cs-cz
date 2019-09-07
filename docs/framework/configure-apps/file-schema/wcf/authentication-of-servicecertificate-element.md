---
title: <authentication><serviceCertificate> elementu
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 29170f032469b4d55b50f57ca06ce403a5aeaf2c
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398227"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="9f182-102">\<ověřování > \<elementu serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="9f182-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="9f182-103">Určuje nastavení používané klientským proxy serverem k ověřování certifikátů služby, které jsou získány pomocí vyjednávání protokolu SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="9f182-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
<span data-ttu-id="9f182-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9f182-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9f182-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9f182-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9f182-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9f182-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="9f182-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9f182-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="9f182-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="9f182-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="9f182-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="9f182-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="9f182-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<serviceCertificate >** ](servicecertificate-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="9f182-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="9f182-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> ověřování**</span><span class="sxs-lookup"><span data-stu-id="9f182-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f182-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9f182-112">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9f182-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="9f182-113">Attributes and Elements</span></span>  
 <span data-ttu-id="9f182-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="9f182-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9f182-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="9f182-115">Attributes</span></span>  
  
|<span data-ttu-id="9f182-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="9f182-116">Attribute</span></span>|<span data-ttu-id="9f182-117">Popis</span><span class="sxs-lookup"><span data-stu-id="9f182-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9f182-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="9f182-118">customCertificateValidatorType</span></span>|<span data-ttu-id="9f182-119">Řetezce.</span><span class="sxs-lookup"><span data-stu-id="9f182-119">String.</span></span> <span data-ttu-id="9f182-120">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="9f182-120">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="9f182-121">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="9f182-121">certificateValidationMode</span></span>|<span data-ttu-id="9f182-122">Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="9f182-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="9f182-123">Pokud je nastaveno `Custom`na, je nutné zadat také CustomCertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="9f182-123">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="9f182-124">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="9f182-124">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="9f182-125">revocationMode</span><span class="sxs-lookup"><span data-stu-id="9f182-125">revocationMode</span></span>|<span data-ttu-id="9f182-126">Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="9f182-126">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="9f182-127">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="9f182-127">The default is `Online`.</span></span>|  
|<span data-ttu-id="9f182-128">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="9f182-128">trustedStoreLocation</span></span>|<span data-ttu-id="9f182-129">Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="9f182-129">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="9f182-130">Tato hodnota se používá, když je certifikát služby vyjednán klientovi.</span><span class="sxs-lookup"><span data-stu-id="9f182-130">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="9f182-131">Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="9f182-131">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="9f182-132">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="9f182-132">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="9f182-133">customCertificateValidator – atribut</span><span class="sxs-lookup"><span data-stu-id="9f182-133">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="9f182-134">Value</span><span class="sxs-lookup"><span data-stu-id="9f182-134">Value</span></span>|<span data-ttu-id="9f182-135">Popis</span><span class="sxs-lookup"><span data-stu-id="9f182-135">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f182-136">String</span><span class="sxs-lookup"><span data-stu-id="9f182-136">String</span></span>|<span data-ttu-id="9f182-137">Určuje název typu a sestavení a další data, která se používají k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="9f182-137">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="9f182-138">certificateValidationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="9f182-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="9f182-139">Value</span><span class="sxs-lookup"><span data-stu-id="9f182-139">Value</span></span>|<span data-ttu-id="9f182-140">Popis</span><span class="sxs-lookup"><span data-stu-id="9f182-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f182-141">Výčet</span><span class="sxs-lookup"><span data-stu-id="9f182-141">Enumeration</span></span>|<span data-ttu-id="9f182-142">Jedna z následujících hodnot: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="9f182-142">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="9f182-143">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="9f182-143">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="9f182-144">revocationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="9f182-144">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="9f182-145">Value</span><span class="sxs-lookup"><span data-stu-id="9f182-145">Value</span></span>|<span data-ttu-id="9f182-146">Popis</span><span class="sxs-lookup"><span data-stu-id="9f182-146">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f182-147">Výčet</span><span class="sxs-lookup"><span data-stu-id="9f182-147">Enumeration</span></span>|<span data-ttu-id="9f182-148">Jedna z následujících hodnot: Nekontrolujte, online, offline.</span><span class="sxs-lookup"><span data-stu-id="9f182-148">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="9f182-149">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="9f182-149">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="9f182-150">trustedStoreLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="9f182-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="9f182-151">Value</span><span class="sxs-lookup"><span data-stu-id="9f182-151">Value</span></span>|<span data-ttu-id="9f182-152">Popis</span><span class="sxs-lookup"><span data-stu-id="9f182-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="9f182-153">Výčet</span><span class="sxs-lookup"><span data-stu-id="9f182-153">Enumeration</span></span>|<span data-ttu-id="9f182-154">Jedna z následujících hodnot: LocalMachine nebo CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="9f182-154">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="9f182-155">Výchozí hodnota je CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="9f182-155">The default is CurrentUser.</span></span> <span data-ttu-id="9f182-156">Pokud klientská aplikace běží pod účtem systému, pak je certifikát obvykle pod LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="9f182-156">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="9f182-157">Pokud klientská aplikace běží pod uživatelským účtem, je certifikát většinou v CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="9f182-157">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9f182-158">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="9f182-158">Child Elements</span></span>  
 <span data-ttu-id="9f182-159">Žádné</span><span class="sxs-lookup"><span data-stu-id="9f182-159">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9f182-160">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="9f182-160">Parent Elements</span></span>  
  
|<span data-ttu-id="9f182-161">Prvek</span><span class="sxs-lookup"><span data-stu-id="9f182-161">Element</span></span>|<span data-ttu-id="9f182-162">Popis</span><span class="sxs-lookup"><span data-stu-id="9f182-162">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9f182-163">\<serviceCertificate></span><span class="sxs-lookup"><span data-stu-id="9f182-163">\<serviceCertificate></span></span>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="9f182-164">Určuje certifikát, který se má použít při ověřování služby pro klienta.</span><span class="sxs-lookup"><span data-stu-id="9f182-164">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9f182-165">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9f182-165">Remarks</span></span>  
 <span data-ttu-id="9f182-166">`certificateValidationMode` Atribut tohoto elementu konfigurace určuje úroveň důvěryhodnosti použitou k ověřování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="9f182-166">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="9f182-167">Ve výchozím nastavení je úroveň nastavena na `ChainTrust`hodnotu, která určuje, že každý certifikát musí být nalezen v hierarchii certifikátů končících důvěryhodnou certifikační autoritou v horní části řetězce.</span><span class="sxs-lookup"><span data-stu-id="9f182-167">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="9f182-168">Toto je nejbezpečnější režim.</span><span class="sxs-lookup"><span data-stu-id="9f182-168">This is the most secure mode.</span></span> <span data-ttu-id="9f182-169">Můžete také nastavit hodnotu na `PeerOrChainTrust`, což znamená, že jsou přijímány certifikáty vystavené svým držitelem (vztah důvěryhodnosti peering) i certifikáty, které jsou v důvěryhodném řetězci.</span><span class="sxs-lookup"><span data-stu-id="9f182-169">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="9f182-170">Tato hodnota se používá při vývoji a ladění klientů a služeb vzhledem k tomu, že certifikáty vystavené svým držitelem nemusejí být zakoupeny důvěryhodnou autoritou.</span><span class="sxs-lookup"><span data-stu-id="9f182-170">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="9f182-171">Při nasazování klienta použijte `ChainTrust` místo něj hodnotu.</span><span class="sxs-lookup"><span data-stu-id="9f182-171">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="9f182-172">Můžete také nastavit hodnotu na `Custom` nebo. `None`</span><span class="sxs-lookup"><span data-stu-id="9f182-172">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="9f182-173">Chcete-li `Custom` použít hodnotu, je nutné také `customCertificateValidator` nastavit atribut na sestavení a typ použitý k ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="9f182-173">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="9f182-174">Chcete-li vytvořit vlastní validátor, je nutné dědit z abstraktní třídy X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="9f182-174">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="9f182-175">Další informace najdete v tématu [jak: Vytvořte službu, která využívá vlastní validátor](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)certifikátů.</span><span class="sxs-lookup"><span data-stu-id="9f182-175">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="9f182-176">`revocationMode` Atribut určuje, jak se kontrolují certifikáty pro odvolání.</span><span class="sxs-lookup"><span data-stu-id="9f182-176">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="9f182-177">Ve výchozím nastavení `online` to znamená, že se certifikáty budou kontrolovat automaticky pro odvolání.</span><span class="sxs-lookup"><span data-stu-id="9f182-177">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="9f182-178">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="9f182-178">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9f182-179">Příklad</span><span class="sxs-lookup"><span data-stu-id="9f182-179">Example</span></span>  
 <span data-ttu-id="9f182-180">Následující příklad provádí dvě úlohy.</span><span class="sxs-lookup"><span data-stu-id="9f182-180">The following example does two tasks.</span></span> <span data-ttu-id="9f182-181">Nejprve Určuje certifikát služby, který má klient použít při komunikaci s koncovými body, jejichž název domény `www.contoso.com` je přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="9f182-181">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="9f182-182">Za druhé určuje režim odvolání a umístění úložiště použité při ověřování.</span><span class="sxs-lookup"><span data-stu-id="9f182-182">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f182-183">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f182-183">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="9f182-184">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="9f182-184">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="9f182-185">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="9f182-185">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="9f182-186">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="9f182-186">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="9f182-187">\<> ověřování</span><span class="sxs-lookup"><span data-stu-id="9f182-187">\<authentication></span></span>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="9f182-188">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="9f182-188">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="9f182-189">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="9f182-189">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
