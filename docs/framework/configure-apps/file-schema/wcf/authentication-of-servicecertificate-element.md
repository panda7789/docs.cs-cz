---
title: <authentication><serviceCertificate>elementu
ms.date: 03/30/2017
ms.assetid: 733b67b4-08a1-4d25-9741-10046f9357ef
ms.openlocfilehash: 29170f032469b4d55b50f57ca06ce403a5aeaf2c
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398227"
---
# <a name="authentication-of-servicecertificate-element"></a><span data-ttu-id="339d5-102">\<authentication>\<serviceCertificate>elementu</span><span class="sxs-lookup"><span data-stu-id="339d5-102">\<authentication> of \<serviceCertificate> Element</span></span>
<span data-ttu-id="339d5-103">Určuje nastavení používané klientským proxy serverem k ověřování certifikátů služby, které jsou získány pomocí vyjednávání protokolu SSL/TLS.</span><span class="sxs-lookup"><span data-stu-id="339d5-103">Specifies the settings used by the client proxy to authenticate service certificates that are obtained using SSL/TLS negotiation.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCertificate>**](servicecertificate-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="339d5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="339d5-104">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="String"
                certificateValidationMode="None/PeerTrust/ChainTrust/PeerOrChainTrust/Custom"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="LocalMachine/CurrentUser" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="339d5-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="339d5-105">Attributes and Elements</span></span>  
 <span data-ttu-id="339d5-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="339d5-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="339d5-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="339d5-107">Attributes</span></span>  
  
|<span data-ttu-id="339d5-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="339d5-108">Attribute</span></span>|<span data-ttu-id="339d5-109">Popis</span><span class="sxs-lookup"><span data-stu-id="339d5-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="339d5-110">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="339d5-110">customCertificateValidatorType</span></span>|<span data-ttu-id="339d5-111">Řetězec.</span><span class="sxs-lookup"><span data-stu-id="339d5-111">String.</span></span> <span data-ttu-id="339d5-112">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="339d5-112">A type and assembly used to validate a custom type.</span></span>|  
|<span data-ttu-id="339d5-113">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="339d5-113">certificateValidationMode</span></span>|<span data-ttu-id="339d5-114">Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="339d5-114">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="339d5-115">Pokud je nastaveno na `Custom` , je nutné zadat také CustomCertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="339d5-115">If set to `Custom`, then a customCertificateValidator must also be supplied.</span></span> <span data-ttu-id="339d5-116">Výchozí formát je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="339d5-116">The default is `ChainTrust`.</span></span>|  
|<span data-ttu-id="339d5-117">revocationMode</span><span class="sxs-lookup"><span data-stu-id="339d5-117">revocationMode</span></span>|<span data-ttu-id="339d5-118">Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="339d5-118">One of the modes used to check for a revoked certificate lists (CRL).</span></span> <span data-ttu-id="339d5-119">Výchozí formát je `Online`.</span><span class="sxs-lookup"><span data-stu-id="339d5-119">The default is `Online`.</span></span>|  
|<span data-ttu-id="339d5-120">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="339d5-120">trustedStoreLocation</span></span>|<span data-ttu-id="339d5-121">Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="339d5-121">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="339d5-122">Tato hodnota se používá, když je certifikát služby vyjednán klientovi.</span><span class="sxs-lookup"><span data-stu-id="339d5-122">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="339d5-123">Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="339d5-123">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="339d5-124">Výchozí formát je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="339d5-124">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidator-attribute"></a><span data-ttu-id="339d5-125">customCertificateValidator – atribut</span><span class="sxs-lookup"><span data-stu-id="339d5-125">customCertificateValidator Attribute</span></span>  
  
|<span data-ttu-id="339d5-126">Hodnota</span><span class="sxs-lookup"><span data-stu-id="339d5-126">Value</span></span>|<span data-ttu-id="339d5-127">Description</span><span class="sxs-lookup"><span data-stu-id="339d5-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="339d5-128">Řetězec</span><span class="sxs-lookup"><span data-stu-id="339d5-128">String</span></span>|<span data-ttu-id="339d5-129">Určuje název typu a sestavení a další data, která se používají k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="339d5-129">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="339d5-130">certificateValidationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="339d5-130">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="339d5-131">Hodnota</span><span class="sxs-lookup"><span data-stu-id="339d5-131">Value</span></span>|<span data-ttu-id="339d5-132">Description</span><span class="sxs-lookup"><span data-stu-id="339d5-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="339d5-133">Výčet</span><span class="sxs-lookup"><span data-stu-id="339d5-133">Enumeration</span></span>|<span data-ttu-id="339d5-134">Jedna z následujících hodnot: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="339d5-134">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="339d5-135">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="339d5-135">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="339d5-136">revocationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="339d5-136">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="339d5-137">Hodnota</span><span class="sxs-lookup"><span data-stu-id="339d5-137">Value</span></span>|<span data-ttu-id="339d5-138">Description</span><span class="sxs-lookup"><span data-stu-id="339d5-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="339d5-139">Výčet</span><span class="sxs-lookup"><span data-stu-id="339d5-139">Enumeration</span></span>|<span data-ttu-id="339d5-140">Jedna z následujících hodnot: nekontrolujte, online, offline.</span><span class="sxs-lookup"><span data-stu-id="339d5-140">One of the following values: NoCheck, Online, Offline.</span></span><br /><br /> <span data-ttu-id="339d5-141">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="339d5-141">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="339d5-142">trustedStoreLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="339d5-142">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="339d5-143">Hodnota</span><span class="sxs-lookup"><span data-stu-id="339d5-143">Value</span></span>|<span data-ttu-id="339d5-144">Description</span><span class="sxs-lookup"><span data-stu-id="339d5-144">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="339d5-145">Výčet</span><span class="sxs-lookup"><span data-stu-id="339d5-145">Enumeration</span></span>|<span data-ttu-id="339d5-146">Jedna z následujících hodnot: LocalMachine nebo CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="339d5-146">One of the following values: LocalMachine or CurrentUser.</span></span> <span data-ttu-id="339d5-147">Výchozí hodnota je CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="339d5-147">The default is CurrentUser.</span></span> <span data-ttu-id="339d5-148">Pokud klientská aplikace běží pod účtem systému, pak je certifikát obvykle pod LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="339d5-148">If the client application is running under a system account, then the certificate is typically under LocalMachine.</span></span> <span data-ttu-id="339d5-149">Pokud klientská aplikace běží pod uživatelským účtem, je certifikát většinou v CurrentUser.</span><span class="sxs-lookup"><span data-stu-id="339d5-149">If the client application is running under a user account, then the certificate is typically in CurrentUser.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="339d5-150">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="339d5-150">Child Elements</span></span>  
 <span data-ttu-id="339d5-151">Žádné</span><span class="sxs-lookup"><span data-stu-id="339d5-151">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="339d5-152">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="339d5-152">Parent Elements</span></span>  
  
|<span data-ttu-id="339d5-153">Prvek</span><span class="sxs-lookup"><span data-stu-id="339d5-153">Element</span></span>|<span data-ttu-id="339d5-154">Description</span><span class="sxs-lookup"><span data-stu-id="339d5-154">Description</span></span>|  
|-------------|-----------------|  
|[\<serviceCertificate>](servicecertificate-of-clientcredentials-element.md)|<span data-ttu-id="339d5-155">Určuje certifikát, který se má použít při ověřování služby pro klienta.</span><span class="sxs-lookup"><span data-stu-id="339d5-155">Specifies a certificate to use when authenticating a service to the client.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="339d5-156">Poznámky</span><span class="sxs-lookup"><span data-stu-id="339d5-156">Remarks</span></span>  
 <span data-ttu-id="339d5-157">`certificateValidationMode`Atribut tohoto elementu konfigurace určuje úroveň důvěryhodnosti použitou k ověřování certifikátů.</span><span class="sxs-lookup"><span data-stu-id="339d5-157">The `certificateValidationMode` attribute of this configuration element specifies the level of trust used to authenticate certificates.</span></span> <span data-ttu-id="339d5-158">Ve výchozím nastavení je úroveň nastavena na hodnotu `ChainTrust` , která určuje, že každý certifikát musí být nalezen v hierarchii certifikátů končících důvěryhodnou certifikační autoritou v horní části řetězce.</span><span class="sxs-lookup"><span data-stu-id="339d5-158">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a trusted certification authority at the top of the chain.</span></span> <span data-ttu-id="339d5-159">Toto je nejbezpečnější režim.</span><span class="sxs-lookup"><span data-stu-id="339d5-159">This is the most secure mode.</span></span> <span data-ttu-id="339d5-160">Můžete také nastavit hodnotu na `PeerOrChainTrust` , což znamená, že jsou přijímány certifikáty vystavené svým držitelem (vztah důvěryhodnosti peering) i certifikáty, které jsou v důvěryhodném řetězci.</span><span class="sxs-lookup"><span data-stu-id="339d5-160">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="339d5-161">Tato hodnota se používá při vývoji a ladění klientů a služeb vzhledem k tomu, že certifikáty vystavené svým držitelem nemusejí být zakoupeny důvěryhodnou autoritou.</span><span class="sxs-lookup"><span data-stu-id="339d5-161">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="339d5-162">Při nasazování klienta použijte `ChainTrust` místo něj hodnotu.</span><span class="sxs-lookup"><span data-stu-id="339d5-162">When deploying a client, use the `ChainTrust` value instead.</span></span> <span data-ttu-id="339d5-163">Můžete také nastavit hodnotu na `Custom` nebo `None` .</span><span class="sxs-lookup"><span data-stu-id="339d5-163">You can also set the value to `Custom` or `None`.</span></span> <span data-ttu-id="339d5-164">Chcete-li použít `Custom` hodnotu, je nutné také nastavit `customCertificateValidator` atribut na sestavení a typ použitý k ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="339d5-164">To use the `Custom` value, you must also set the `customCertificateValidator` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="339d5-165">Chcete-li vytvořit vlastní validátor, je nutné dědit z abstraktní třídy X509CertificateValidator.</span><span class="sxs-lookup"><span data-stu-id="339d5-165">To create your own custom validator, you must inherit from the abstract X509CertificateValidator class.</span></span> <span data-ttu-id="339d5-166">Další informace najdete v tématu [Postup: vytvoření služby, která využívá vlastní validátor certifikátů](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="339d5-166">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
 <span data-ttu-id="339d5-167">`revocationMode`Atribut určuje, jak se kontrolují certifikáty pro odvolání.</span><span class="sxs-lookup"><span data-stu-id="339d5-167">The `revocationMode` attribute specifies how certificates are checked for revocation.</span></span> <span data-ttu-id="339d5-168">Ve výchozím nastavení `online` to znamená, že se certifikáty budou kontrolovat automaticky pro odvolání.</span><span class="sxs-lookup"><span data-stu-id="339d5-168">The default is `online` which indicates that certificates will be checked automatically for revocation.</span></span> <span data-ttu-id="339d5-169">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="339d5-169">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="339d5-170">Příklad</span><span class="sxs-lookup"><span data-stu-id="339d5-170">Example</span></span>  
 <span data-ttu-id="339d5-171">Následující příklad provádí dvě úlohy.</span><span class="sxs-lookup"><span data-stu-id="339d5-171">The following example does two tasks.</span></span> <span data-ttu-id="339d5-172">Nejprve Určuje certifikát služby, který má klient použít při komunikaci s koncovými body, jejichž název domény je `www.contoso.com` přes protokol HTTP.</span><span class="sxs-lookup"><span data-stu-id="339d5-172">It first specifies a service certificate for the client to use when communicating with endpoints whose domain name is `www.contoso.com` over the HTTP protocol.</span></span> <span data-ttu-id="339d5-173">Za druhé určuje režim odvolání a umístění úložiště použité při ověřování.</span><span class="sxs-lookup"><span data-stu-id="339d5-173">Second, it specifies the revocation mode and store location used during authentication.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="339d5-174">Viz také</span><span class="sxs-lookup"><span data-stu-id="339d5-174">See also</span></span>

- <xref:System.ServiceModel.Configuration.X509RecipientCertificateClientElement>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>
- <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential.Authentication%2A>
- <xref:System.ServiceModel.Security.X509ServiceCertificateAuthentication>
- [<span data-ttu-id="339d5-175">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="339d5-175">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="339d5-176">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="339d5-176">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="339d5-177">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="339d5-177">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [\<authentication>](authentication-of-clientcertificate-element.md)
- [<span data-ttu-id="339d5-178">Zabezpečení klientů</span><span class="sxs-lookup"><span data-stu-id="339d5-178">Securing Clients</span></span>](../../../wcf/securing-clients.md)
- [<span data-ttu-id="339d5-179">Zabezpečení služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="339d5-179">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
