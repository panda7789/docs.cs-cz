---
title: '&lt;authentication&gt; elementu &lt;serviceCertificate&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 163a035c667c25be4f780daf85c50d96816bd0f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltauthenticationgt-of-ltservicecertificategt-element"></a><span data-ttu-id="36287-102">&lt;authentication&gt; elementu &lt;serviceCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="36287-102">&lt;authentication&gt; of &lt;serviceCertificate&gt; Element</span></span>
<span data-ttu-id="36287-103">Určuje nastavení proxy serveru klienta používaná k ověřování certifikáty služby, které jsou získány pomocí vyjednávání SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="36287-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
 <span data-ttu-id="36287-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="36287-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="36287-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="36287-105">\<behaviors></span></span>  
<span data-ttu-id="36287-106">část endpointBehaviors</span><span class="sxs-lookup"><span data-stu-id="36287-106">endpointBehaviors section</span></span>  
<span data-ttu-id="36287-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="36287-107">\<behavior></span></span>  
<span data-ttu-id="36287-108">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="36287-108">\<clientCredentials></span></span>  
<span data-ttu-id="36287-109">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="36287-109">\<serviceCertificate></span></span>  
<span data-ttu-id="36287-110">\<ověřování ></span><span class="sxs-lookup"><span data-stu-id="36287-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="36287-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="36287-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String" certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"   
trustedStoreLocation="LocalMachine/CurrentUser" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="36287-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="36287-112">Attributes and Elements</span></span>  
 <span data-ttu-id="36287-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="36287-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="36287-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="36287-114">Attributes</span></span>  
  
|<span data-ttu-id="36287-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="36287-115">Attribute</span></span>|<span data-ttu-id="36287-116">Popis</span><span class="sxs-lookup"><span data-stu-id="36287-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="36287-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="36287-117">customCertificateValidatorType</span></span>|<span data-ttu-id="36287-118">Řetězec.</span><span class="sxs-lookup"><span data-stu-id="36287-118">String.</span></span> <span data-ttu-id="36287-119">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="36287-119">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="36287-120">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="36287-120">certificateValidationMode</span></span>|<span data-ttu-id="36287-121">Určuje jeden ze tří režimů slouží k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="36287-121">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="36287-122">Pokud nastavena na `Custom`, pak musí být uveden také customCertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="36287-122">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="36287-123">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="36287-123">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="36287-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="36287-124">revocationMode</span></span>|<span data-ttu-id="36287-125">Jeden z režimů používá k ověření pro seznamy odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="36287-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="36287-126">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="36287-126">The default is `Online`.</span></span>|  
|<span data-ttu-id="36287-127">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="36287-127">trustedStoreLocation</span></span>|<span data-ttu-id="36287-128">Jedno z umístění úložiště dvě systému: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="36287-128">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="36287-129">Tato hodnota se používá, když je klientovi vyjednal certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="36287-129">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="36287-130">Ověření se provádí před **důvěryhodné osoby** uložit do umístění zadaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="36287-130">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="36287-131">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="36287-131">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="36287-132">customCertificateValidator atribut</span><span class="sxs-lookup"><span data-stu-id="36287-132">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="36287-133">Hodnota</span><span class="sxs-lookup"><span data-stu-id="36287-133">Value</span></span>|<span data-ttu-id="36287-134">Popis</span><span class="sxs-lookup"><span data-stu-id="36287-134">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="36287-135">String</span><span class="sxs-lookup"><span data-stu-id="36287-135">String</span></span>|<span data-ttu-id="36287-136">Určuje název typu a sestavení a další data použít k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="36287-136">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="36287-137">certificateValidationMode atribut</span><span class="sxs-lookup"><span data-stu-id="36287-137">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="36287-138">Hodnota</span><span class="sxs-lookup"><span data-stu-id="36287-138">Value</span></span>|<span data-ttu-id="36287-139">Popis</span><span class="sxs-lookup"><span data-stu-id="36287-139">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="36287-140">Výčet</span><span class="sxs-lookup"><span data-stu-id="36287-140">Enumeration</span></span>|<span data-ttu-id="36287-141">Jeden z následujících hodnot: None, PeerTrust, ChainTrust, PeerOrChainTrust, vlastní.</span><span class="sxs-lookup"><span data-stu-id="36287-141">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="36287-142">Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="36287-142">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="36287-143">revocationMode atribut</span><span class="sxs-lookup"><span data-stu-id="36287-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="36287-144">Hodnota</span><span class="sxs-lookup"><span data-stu-id="36287-144">Value</span></span>|<span data-ttu-id="36287-145">Popis</span><span class="sxs-lookup"><span data-stu-id="36287-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="36287-146">Výčet</span><span class="sxs-lookup"><span data-stu-id="36287-146">Enumeration</span></span>|<span data-ttu-id="36287-147">Jeden z následujících hodnot: NoCheck, Online, do režimu Offline.</span><span class="sxs-lookup"><span data-stu-id="36287-147">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="36287-148">Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="36287-148">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="36287-149">trustedStoreLocation atribut</span><span class="sxs-lookup"><span data-stu-id="36287-149">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="36287-150">Hodnota</span><span class="sxs-lookup"><span data-stu-id="36287-150">Value</span></span>|<span data-ttu-id="36287-151">Popis</span><span class="sxs-lookup"><span data-stu-id="36287-151">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="36287-152">Výčet</span><span class="sxs-lookup"><span data-stu-id="36287-152">Enumeration</span></span>|<span data-ttu-id="36287-153">Jeden z následujících hodnot: LocalMachine nebo CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="36287-153">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="36287-154">Výchozí hodnota je CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="36287-154">The default is CurrentUser.</span></span> <span data-ttu-id="36287-155">Pokud klientská aplikace běží pod účtem system, certifikát je obvykle v rámci LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="36287-155">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="36287-156">Pokud klientská aplikace běží pod účtem uživatele, pak certifikát je obvykle v CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="36287-156">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="36287-157">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="36287-157">Child Elements</span></span>  
 <span data-ttu-id="36287-158">Žádné</span><span class="sxs-lookup"><span data-stu-id="36287-158">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="36287-159">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="36287-159">Parent Elements</span></span>  
  
|<span data-ttu-id="36287-160">Prvek</span><span class="sxs-lookup"><span data-stu-id="36287-160">Element</span></span>|<span data-ttu-id="36287-161">Popis</span><span class="sxs-lookup"><span data-stu-id="36287-161">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="36287-162">\<serviceCertificate ></span><span class="sxs-lookup"><span data-stu-id="36287-162">\<serviceCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="36287-163">Určuje certifikát pro použití při ověřování služby klienta.</span><span class="sxs-lookup"><span data-stu-id="36287-163">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="36287-164">Poznámky</span><span class="sxs-lookup"><span data-stu-id="36287-164">Remarks</span></span>  
 <span data-ttu-id="36287-165">`certificateValidationMode` Atribut tohoto elementu konfigurace určuje úroveň důvěryhodnosti používá k ověření certifikátů.</span><span class="sxs-lookup"><span data-stu-id="36287-165">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="36287-166">Ve výchozím nastavení je úroveň nastavena na `ChainTrust`, která určuje, že každý certifikát, je nutné nalézt v hierarchii certifikátů končí na důvěryhodné certifikační autority v horní části řetězu.</span><span class="sxs-lookup"><span data-stu-id="36287-166">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="36287-167">Toto je nejbezpečnější režim.</span><span class="sxs-lookup"><span data-stu-id="36287-167">This is the most secure mode.</span></span> <span data-ttu-id="36287-168">Můžete také nastavit hodnotu `PeerOrChainTrust`, která určuje, že samoobslužné vydaných certifikátů (peer vztahu důvěryhodnosti) jsou přijaty a také certifikáty, které jsou v důvěryhodné řetězu.</span><span class="sxs-lookup"><span data-stu-id="36287-168">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="36287-169">Tato hodnota se používá při vývoji a ladění klientů a služeb, protože samoobslužné vydaných certifikátů nemusí zakoupenému od důvěryhodné autority.</span><span class="sxs-lookup"><span data-stu-id="36287-169">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="36287-170">Při nasazování klienta, použijte `ChainTrust` místo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="36287-170">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="36287-171">Můžete také nastavit hodnotu `Custom` nebo `None`.</span><span class="sxs-lookup"><span data-stu-id="36287-171">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="36287-172">Použít `Custom` hodnotu, je nutné také nastavit `customCertificateValidator` atribut sestavení a typ použitý k ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="36287-172">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="36287-173">Pokud chcete vytvořit vlastní vlastní validátor, musí dědit z abstraktní třídy X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="36287-173">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="36287-174">Další informace najdete v tématu [postupy: vytvoření služby, který využívá validátor certifikátu vlastní](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="36287-174">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="36287-175">`revocationMode` Atribut určuje, jak certifikáty jsou zaškrtnutá políčka pro odvolání.</span><span class="sxs-lookup"><span data-stu-id="36287-175">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="36287-176">Výchozí hodnota je `online` což naznačuje, že certifikáty budou automaticky odvolání zkontrolovat.</span><span class="sxs-lookup"><span data-stu-id="36287-176">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="36287-177">Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="36287-177">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="36287-178">Příklad</span><span class="sxs-lookup"><span data-stu-id="36287-178">Example</span></span>  
 <span data-ttu-id="36287-179">V následujícím příkladu se dvě úlohy.</span><span class="sxs-lookup"><span data-stu-id="36287-179">The following example does two tasks.</span></span> <span data-ttu-id="36287-180">Určuje první certifikát služby pro klienta pro použití při komunikaci s koncovými body, jejichž název domény je www.contoso.com přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="36287-180">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is www.contoso.com over the HTTP protocol.</span></span> <span data-ttu-id="36287-181">Druhý Určuje odvolání režimu a úložiště umístění, která používají při ověřování.</span><span class="sxs-lookup"><span data-stu-id="36287-181">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
```xml  
<serviceCertificate>  
  <defaultCertificate findValue="www.contoso.com"   
                      storeLocation="LocalMachine"  
                      storeName="TrustedPeople"   
                      x509FindType="FindByIssuerDistinguishedName" />  
  <scopedCertificates>  
     <add targetUri="http://www.contoso.com"   
          findValue="www.contoso.com" storeLocation="LocalMachine"  
                  storeName="Root" x509FindType="FindByIssuerName" />  
  </scopedCertificates>  
  <authentication revocationMode="Online"   
   trustedStoreLocation="LocalMachine" />  
</serviceCertificate>  
```  
  
## <a name="see-also"></a><span data-ttu-id="36287-182">Viz také</span><span class="sxs-lookup"><span data-stu-id="36287-182">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>  
 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>  
 <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>  
 [<span data-ttu-id="36287-183">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="36287-183">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="36287-184">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="36287-184">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="36287-185">Postupy: vytvoření služby, který využívá validátor vlastní certifikát</span><span class="sxs-lookup"><span data-stu-id="36287-185">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="36287-186">\<ověřování ></span><span class="sxs-lookup"><span data-stu-id="36287-186">\<authentication></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/authentication-of-clientcertificate-element.md)  
 [<span data-ttu-id="36287-187">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="36287-187">Securing Clients</span></span>](../../../../../docs/framework/wcf/securing-clients.md)  
 [<span data-ttu-id="36287-188">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="36287-188">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
