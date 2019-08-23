---
title: <authentication><clientCertificate> elementu
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 4a7fee3bd8441a9612e954160397cc56aca163d1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926512"
---
# <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="19881-102">\<ověřování > \<elementu ClientCertificate ></span><span class="sxs-lookup"><span data-stu-id="19881-102">\<authentication> of \<clientCertificate> Element</span></span>
<span data-ttu-id="19881-103">Určuje chování ověřování pro klientské certifikáty používané službou.</span><span class="sxs-lookup"><span data-stu-id="19881-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
 <span data-ttu-id="19881-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="19881-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="19881-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="19881-105">\<behaviors></span></span>  
<span data-ttu-id="19881-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="19881-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="19881-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="19881-107">\<behavior></span></span>  
<span data-ttu-id="19881-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="19881-108">\<serviceCredentials></span></span>  
<span data-ttu-id="19881-109">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="19881-109">\<clientCertificate></span></span>  
<span data-ttu-id="19881-110">\<> ověřování</span><span class="sxs-lookup"><span data-stu-id="19881-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="19881-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="19881-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="19881-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="19881-112">Attributes and Elements</span></span>  
 <span data-ttu-id="19881-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="19881-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="19881-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="19881-114">Attributes</span></span>  
  
|<span data-ttu-id="19881-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="19881-115">Attribute</span></span>|<span data-ttu-id="19881-116">Popis</span><span class="sxs-lookup"><span data-stu-id="19881-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="19881-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="19881-117">customCertificateValidatorType</span></span>|<span data-ttu-id="19881-118">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="19881-118">Optional string.</span></span> <span data-ttu-id="19881-119">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="19881-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="19881-120">Tento atribut musí být nastaven, `certificateValidationMode` je-li `Custom`nastavena na hodnotu.</span><span class="sxs-lookup"><span data-stu-id="19881-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="19881-121">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="19881-121">certificateValidationMode</span></span>|<span data-ttu-id="19881-122">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="19881-122">Optional enumeration.</span></span> <span data-ttu-id="19881-123">Určuje jeden z režimů používaných k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="19881-123">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="19881-124">Tento atribut je <xref:System.ServiceModel.Security.X509CertificateValidationMode> typu.</span><span class="sxs-lookup"><span data-stu-id="19881-124">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="19881-125">Je-li <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>nastaveno na hodnotu, musí být zadána také. `customCertificateValidator`</span><span class="sxs-lookup"><span data-stu-id="19881-125">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="19881-126">Výchozí hodnota je <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="19881-126">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="19881-127">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="19881-127">includeWindowsGroups</span></span>|<span data-ttu-id="19881-128">Volitelná logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="19881-128">Optional Boolean.</span></span> <span data-ttu-id="19881-129">Určuje, zda jsou skupiny systému Windows zahrnuty v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="19881-129">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="19881-130">Nastavení tohoto atributu na `true` má vliv na výkon, protože má za následek rozšíření celé skupiny.</span><span class="sxs-lookup"><span data-stu-id="19881-130">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="19881-131">Nastavte tento atribut na `false` , pokud nepotřebujete vytvořit seznam skupin, do kterých uživatel patří.</span><span class="sxs-lookup"><span data-stu-id="19881-131">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="19881-132">mapClientCertificateToWindowsAccount</span><span class="sxs-lookup"><span data-stu-id="19881-132">mapClientCertificateToWindowsAccount</span></span>|<span data-ttu-id="19881-133">Datového.</span><span class="sxs-lookup"><span data-stu-id="19881-133">Boolean.</span></span> <span data-ttu-id="19881-134">Určuje, jestli je možné klienta namapovat na identitu Windows pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="19881-134">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="19881-135">K tomu musí být povolená služba Active Directory.</span><span class="sxs-lookup"><span data-stu-id="19881-135">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="19881-136">revocationMode</span><span class="sxs-lookup"><span data-stu-id="19881-136">revocationMode</span></span>|<span data-ttu-id="19881-137">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="19881-137">Optional enumeration.</span></span> <span data-ttu-id="19881-138">Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (RCL).</span><span class="sxs-lookup"><span data-stu-id="19881-138">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="19881-139">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="19881-139">The default is `Online`.</span></span> <span data-ttu-id="19881-140">Tato hodnota se při použití zabezpečení přenosu HTTP ignoruje.</span><span class="sxs-lookup"><span data-stu-id="19881-140">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="19881-141">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="19881-141">trustedStoreLocation</span></span>|<span data-ttu-id="19881-142">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="19881-142">Optional enumeration.</span></span> <span data-ttu-id="19881-143">Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="19881-143">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="19881-144">Tato hodnota se používá, když je certifikát služby vyjednán klientovi.</span><span class="sxs-lookup"><span data-stu-id="19881-144">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="19881-145">Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="19881-145">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="19881-146">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="19881-146">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="19881-147">customCertificateValidatorType – atribut</span><span class="sxs-lookup"><span data-stu-id="19881-147">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="19881-148">Value</span><span class="sxs-lookup"><span data-stu-id="19881-148">Value</span></span>|<span data-ttu-id="19881-149">Popis</span><span class="sxs-lookup"><span data-stu-id="19881-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="19881-150">String</span><span class="sxs-lookup"><span data-stu-id="19881-150">String</span></span>|<span data-ttu-id="19881-151">Určuje název typu a sestavení a další data, která se používají k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="19881-151">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="19881-152">certificateValidationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="19881-152">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="19881-153">Value</span><span class="sxs-lookup"><span data-stu-id="19881-153">Value</span></span>|<span data-ttu-id="19881-154">Popis</span><span class="sxs-lookup"><span data-stu-id="19881-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="19881-155">Výčet</span><span class="sxs-lookup"><span data-stu-id="19881-155">Enumeration</span></span>|<span data-ttu-id="19881-156">Jedna z následujících hodnot: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="19881-156">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="19881-157">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="19881-157">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="19881-158">revocationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="19881-158">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="19881-159">Value</span><span class="sxs-lookup"><span data-stu-id="19881-159">Value</span></span>|<span data-ttu-id="19881-160">Popis</span><span class="sxs-lookup"><span data-stu-id="19881-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="19881-161">Výčet</span><span class="sxs-lookup"><span data-stu-id="19881-161">Enumeration</span></span>|<span data-ttu-id="19881-162">Jedna z následujících hodnot: Nekontrolujte, online, offline.</span><span class="sxs-lookup"><span data-stu-id="19881-162">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="19881-163">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="19881-163">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="19881-164">trustedStoreLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="19881-164">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="19881-165">Value</span><span class="sxs-lookup"><span data-stu-id="19881-165">Value</span></span>|<span data-ttu-id="19881-166">Popis</span><span class="sxs-lookup"><span data-stu-id="19881-166">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="19881-167">Výčet</span><span class="sxs-lookup"><span data-stu-id="19881-167">Enumeration</span></span>|<span data-ttu-id="19881-168">Jedna z následujících hodnot: `LocalMachine` nebo. `CurrentUser`</span><span class="sxs-lookup"><span data-stu-id="19881-168">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="19881-169">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="19881-169">The default is `CurrentUser`.</span></span> <span data-ttu-id="19881-170">Pokud klientská aplikace běží pod účtem systému, certifikát se obvykle nachází v části `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="19881-170">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="19881-171">Pokud klientská aplikace běží pod uživatelským účtem, bude certifikát typicky v `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="19881-171">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="19881-172">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="19881-172">Child Elements</span></span>  
 <span data-ttu-id="19881-173">Žádné</span><span class="sxs-lookup"><span data-stu-id="19881-173">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="19881-174">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="19881-174">Parent Elements</span></span>  
  
|<span data-ttu-id="19881-175">Prvek</span><span class="sxs-lookup"><span data-stu-id="19881-175">Element</span></span>|<span data-ttu-id="19881-176">Popis</span><span class="sxs-lookup"><span data-stu-id="19881-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="19881-177">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="19881-177">\<clientCertificate></span></span>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="19881-178">Definuje certifikát X. 509, který se používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="19881-178">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="19881-179">Poznámky</span><span class="sxs-lookup"><span data-stu-id="19881-179">Remarks</span></span>  
 <span data-ttu-id="19881-180">`<authentication>` Prvek odpovídá<xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídě.</span><span class="sxs-lookup"><span data-stu-id="19881-180">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="19881-181">Umožňuje vám přizpůsobit způsob ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="19881-181">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="19881-182">Můžete nastavit `certificateValidationMode` atribut na `None`, `ChainTrust` `PeerOrChainTrust` ,,`Custom`nebo. `PeerTrust`</span><span class="sxs-lookup"><span data-stu-id="19881-182">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="19881-183">Ve výchozím nastavení je úroveň nastavena na `ChainTrust`hodnotu, která určuje, že každý certifikát musí být nalezen v hierarchii certifikátů končících kořenovou *autoritou* v horní části řetězce.</span><span class="sxs-lookup"><span data-stu-id="19881-183">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="19881-184">Toto je nejbezpečnější režim.</span><span class="sxs-lookup"><span data-stu-id="19881-184">This is the most secure mode.</span></span> <span data-ttu-id="19881-185">Můžete také nastavit hodnotu na `PeerOrChainTrust`, což znamená, že jsou přijímány certifikáty vystavené svým držitelem (vztah důvěryhodnosti peering) i certifikáty, které jsou v důvěryhodném řetězci.</span><span class="sxs-lookup"><span data-stu-id="19881-185">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="19881-186">Tato hodnota se používá při vývoji a ladění klientů a služeb vzhledem k tomu, že certifikáty vystavené svým držitelem nemusejí být zakoupeny důvěryhodnou autoritou.</span><span class="sxs-lookup"><span data-stu-id="19881-186">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="19881-187">Při nasazování klienta použijte `ChainTrust` místo něj hodnotu.</span><span class="sxs-lookup"><span data-stu-id="19881-187">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="19881-188">Můžete také nastavit hodnotu na `Custom`.</span><span class="sxs-lookup"><span data-stu-id="19881-188">You can also set the value to `Custom`.</span></span> <span data-ttu-id="19881-189">Pokud je nastaveno na `Custom` hodnotu, je nutné také `customCertificateValidatorType` nastavit atribut na sestavení a typ použitý k ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="19881-189">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="19881-190">Chcete-li vytvořit vlastní validátor, je nutné dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="19881-190">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="19881-191">Další informace najdete v tématu [jak: Vytvořte službu, která využívá vlastní validátor](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)certifikátů.</span><span class="sxs-lookup"><span data-stu-id="19881-191">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="19881-192">Příklad</span><span class="sxs-lookup"><span data-stu-id="19881-192">Example</span></span>  
 <span data-ttu-id="19881-193">Následující kód Určuje certifikát X. 509 a typ vlastního ověřování v `<authentication>` elementu.</span><span class="sxs-lookup"><span data-stu-id="19881-193">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>
  <behavior name="myServiceBehavior">
    <clientCertificate>
      <certificate findValue="www.cohowinery.com"
                   storeLocation="CurrentUser"
                   storeName="TrustedPeople"
                   x509FindType="FindByIssuerName" />
      <authentication customCertificateValidatorType="MyTypes.Coho"
                      certificateValidationMode="Custom"
                      revocationMode="Offline"
                      includeWindowsGroups="false"
                      mapClientCertificateToWindowsAccount="true" />
    </clientCertificate>
  </behavior>
</serviceBehaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="19881-194">Viz také:</span><span class="sxs-lookup"><span data-stu-id="19881-194">See also</span></span>

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [<span data-ttu-id="19881-195">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="19881-195">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="19881-196">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="19881-196">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="19881-197">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="19881-197">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
