---
title: <authentication> z <clientCertificate> – Element
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 2cbc850331dc6bf76c352f975fda834a309564c6
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423241"
---
# <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="80ec0-102">\<ověřování > z \<clientCertificate > – Element</span><span class="sxs-lookup"><span data-stu-id="80ec0-102">\<authentication> of \<clientCertificate> Element</span></span>
<span data-ttu-id="80ec0-103">Určuje chování ověřování pro klientské certifikáty používané službou.</span><span class="sxs-lookup"><span data-stu-id="80ec0-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
 <span data-ttu-id="80ec0-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="80ec0-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="80ec0-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="80ec0-105">\<behaviors></span></span>  
<span data-ttu-id="80ec0-106">\<serviceBehaviors></span><span class="sxs-lookup"><span data-stu-id="80ec0-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="80ec0-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="80ec0-107">\<behavior></span></span>  
<span data-ttu-id="80ec0-108">\<serviceCredentials></span><span class="sxs-lookup"><span data-stu-id="80ec0-108">\<serviceCredentials></span></span>  
<span data-ttu-id="80ec0-109">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="80ec0-109">\<clientCertificate></span></span>  
<span data-ttu-id="80ec0-110">\<ověřování ></span><span class="sxs-lookup"><span data-stu-id="80ec0-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="80ec0-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="80ec0-111">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="80ec0-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="80ec0-112">Attributes and Elements</span></span>  
 <span data-ttu-id="80ec0-113">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="80ec0-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="80ec0-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="80ec0-114">Attributes</span></span>  
  
|<span data-ttu-id="80ec0-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="80ec0-115">Attribute</span></span>|<span data-ttu-id="80ec0-116">Popis</span><span class="sxs-lookup"><span data-stu-id="80ec0-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="80ec0-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="80ec0-117">customCertificateValidatorType</span></span>|<span data-ttu-id="80ec0-118">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="80ec0-118">Optional string.</span></span> <span data-ttu-id="80ec0-119">Typ a sestavení používané pro ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="80ec0-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="80ec0-120">Tento atribut musí být nastaven při `certificateValidationMode` je nastavena na `Custom`.</span><span class="sxs-lookup"><span data-stu-id="80ec0-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="80ec0-121">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="80ec0-121">certificateValidationMode</span></span>|<span data-ttu-id="80ec0-122">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="80ec0-122">Optional enumeration.</span></span> <span data-ttu-id="80ec0-123">Určuje jeden z režimů pro ověření pověření.</span><span class="sxs-lookup"><span data-stu-id="80ec0-123">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="80ec0-124">Tento atribut je <xref:System.ServiceModel.Security.X509CertificateValidationMode> typu.</span><span class="sxs-lookup"><span data-stu-id="80ec0-124">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="80ec0-125">Pokud hodnotu <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, o `customCertificateValidator` musí být rovněž dodán.</span><span class="sxs-lookup"><span data-stu-id="80ec0-125">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="80ec0-126">Výchozí hodnota je <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="80ec0-126">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="80ec0-127">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="80ec0-127">includeWindowsGroups</span></span>|<span data-ttu-id="80ec0-128">Nepovinný datový typ Boolean.</span><span class="sxs-lookup"><span data-stu-id="80ec0-128">Optional Boolean.</span></span> <span data-ttu-id="80ec0-129">Určuje, pokud jsou skupiny Windows zahrnuty v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="80ec0-129">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="80ec0-130">Nastavení tohoto atributu na `true` má dopad na výkon, protože výsledkem rozšíření celé skupiny.</span><span class="sxs-lookup"><span data-stu-id="80ec0-130">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="80ec0-131">Tento atribut nastavte na `false` Pokud není potřeba vytvořit seznam skupin uživatel patří.</span><span class="sxs-lookup"><span data-stu-id="80ec0-131">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="80ec0-132">mapClientCertificateToWindowsAccount</span><span class="sxs-lookup"><span data-stu-id="80ec0-132">mapClientCertificateToWindowsAccount</span></span>|<span data-ttu-id="80ec0-133">Datový typ Boolean.</span><span class="sxs-lookup"><span data-stu-id="80ec0-133">Boolean.</span></span> <span data-ttu-id="80ec0-134">Určuje, zda klient je možné mapovat na Windows identity pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="80ec0-134">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="80ec0-135">K tomu musí být povolené služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="80ec0-135">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="80ec0-136">revocationMode</span><span class="sxs-lookup"><span data-stu-id="80ec0-136">revocationMode</span></span>|<span data-ttu-id="80ec0-137">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="80ec0-137">Optional enumeration.</span></span> <span data-ttu-id="80ec0-138">Jeden z režimů pro kontrolu seznamu odvolaných certifikátů (RCL).</span><span class="sxs-lookup"><span data-stu-id="80ec0-138">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="80ec0-139">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="80ec0-139">The default is `Online`.</span></span> <span data-ttu-id="80ec0-140">Tato hodnota se ignoruje při použití zabezpečení přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="80ec0-140">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="80ec0-141">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="80ec0-141">trustedStoreLocation</span></span>|<span data-ttu-id="80ec0-142">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="80ec0-142">Optional enumeration.</span></span> <span data-ttu-id="80ec0-143">Jeden z umístění dvou systémových úložišť: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="80ec0-143">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="80ec0-144">Tato hodnota se používá při certifikát služby se vyjedná do klienta.</span><span class="sxs-lookup"><span data-stu-id="80ec0-144">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="80ec0-145">Ověření se provádí proti **důvěryhodné osoby** uložit do umístění určeného úložiště.</span><span class="sxs-lookup"><span data-stu-id="80ec0-145">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="80ec0-146">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="80ec0-146">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="80ec0-147">customCertificateValidatorType Attribute</span><span class="sxs-lookup"><span data-stu-id="80ec0-147">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="80ec0-148">Value</span><span class="sxs-lookup"><span data-stu-id="80ec0-148">Value</span></span>|<span data-ttu-id="80ec0-149">Popis</span><span class="sxs-lookup"><span data-stu-id="80ec0-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="80ec0-150">String</span><span class="sxs-lookup"><span data-stu-id="80ec0-150">String</span></span>|<span data-ttu-id="80ec0-151">Určuje název typu a sestavení a další data použít k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="80ec0-151">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="80ec0-152">certificateValidationMode atribut</span><span class="sxs-lookup"><span data-stu-id="80ec0-152">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="80ec0-153">Hodnota</span><span class="sxs-lookup"><span data-stu-id="80ec0-153">Value</span></span>|<span data-ttu-id="80ec0-154">Popis</span><span class="sxs-lookup"><span data-stu-id="80ec0-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="80ec0-155">Výčet</span><span class="sxs-lookup"><span data-stu-id="80ec0-155">Enumeration</span></span>|<span data-ttu-id="80ec0-156">Jeden z následujících hodnot: NONE, PeerTrust, ChainTrust, PeerOrChainTrust, vlastní.</span><span class="sxs-lookup"><span data-stu-id="80ec0-156">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="80ec0-157">Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="80ec0-157">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="80ec0-158">revocationMode atribut</span><span class="sxs-lookup"><span data-stu-id="80ec0-158">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="80ec0-159">Value</span><span class="sxs-lookup"><span data-stu-id="80ec0-159">Value</span></span>|<span data-ttu-id="80ec0-160">Popis</span><span class="sxs-lookup"><span data-stu-id="80ec0-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="80ec0-161">Výčet</span><span class="sxs-lookup"><span data-stu-id="80ec0-161">Enumeration</span></span>|<span data-ttu-id="80ec0-162">Jeden z následujících hodnot: NoCheck, Online, Offline.</span><span class="sxs-lookup"><span data-stu-id="80ec0-162">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="80ec0-163">Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="80ec0-163">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="80ec0-164">trustedStoreLocation atribut</span><span class="sxs-lookup"><span data-stu-id="80ec0-164">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="80ec0-165">Hodnota</span><span class="sxs-lookup"><span data-stu-id="80ec0-165">Value</span></span>|<span data-ttu-id="80ec0-166">Popis</span><span class="sxs-lookup"><span data-stu-id="80ec0-166">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="80ec0-167">Výčet</span><span class="sxs-lookup"><span data-stu-id="80ec0-167">Enumeration</span></span>|<span data-ttu-id="80ec0-168">Jeden z následujících hodnot: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="80ec0-168">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="80ec0-169">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="80ec0-169">The default is `CurrentUser`.</span></span> <span data-ttu-id="80ec0-170">Pokud klientská aplikace běží pod účtem systému, certifikátu je obvykle pod `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="80ec0-170">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="80ec0-171">Pokud klientská aplikace běží pod účtem uživatele, že certifikát je obvykle v `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="80ec0-171">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="80ec0-172">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="80ec0-172">Child Elements</span></span>  
 <span data-ttu-id="80ec0-173">Žádné</span><span class="sxs-lookup"><span data-stu-id="80ec0-173">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="80ec0-174">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="80ec0-174">Parent Elements</span></span>  
  
|<span data-ttu-id="80ec0-175">Prvek</span><span class="sxs-lookup"><span data-stu-id="80ec0-175">Element</span></span>|<span data-ttu-id="80ec0-176">Popis</span><span class="sxs-lookup"><span data-stu-id="80ec0-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="80ec0-177">\<clientCertificate></span><span class="sxs-lookup"><span data-stu-id="80ec0-177">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="80ec0-178">Určuje certifikát X.509 použitý k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="80ec0-178">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="80ec0-179">Poznámky</span><span class="sxs-lookup"><span data-stu-id="80ec0-179">Remarks</span></span>  
 <span data-ttu-id="80ec0-180">`<authentication>` Odpovídá elementu <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy.</span><span class="sxs-lookup"><span data-stu-id="80ec0-180">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="80ec0-181">Umožňuje přizpůsobit, jak se budou ověřovat klienti.</span><span class="sxs-lookup"><span data-stu-id="80ec0-181">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="80ec0-182">Můžete nastavit `certificateValidationMode` atribut `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, nebo `Custom`.</span><span class="sxs-lookup"><span data-stu-id="80ec0-182">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="80ec0-183">Ve výchozím nastavení, úroveň je nastavena `ChainTrust`, která určuje, že každý certifikát musí být nalezena v hierarchii certifikátů končí na *kořenová autorita* na začátku řetězce.</span><span class="sxs-lookup"><span data-stu-id="80ec0-183">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="80ec0-184">Toto je nejbezpečnější režim.</span><span class="sxs-lookup"><span data-stu-id="80ec0-184">This is the most secure mode.</span></span> <span data-ttu-id="80ec0-185">Můžete také nastavit hodnotu `PeerOrChainTrust`, která určuje, že jsou přijímány samostatně vydané certifikáty (peer vztahu důvěryhodnosti) a také certifikáty, které jsou v důvěryhodným řetězem.</span><span class="sxs-lookup"><span data-stu-id="80ec0-185">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="80ec0-186">Tato hodnota se používá při vývoji a ladění klientů a služeb, protože samostatně vydané certifikáty nemusí být zakoupenému od důvěryhodné autority.</span><span class="sxs-lookup"><span data-stu-id="80ec0-186">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="80ec0-187">Při nasazování klienta, použijte `ChainTrust` místo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="80ec0-187">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="80ec0-188">Můžete také nastavit hodnotu `Custom`.</span><span class="sxs-lookup"><span data-stu-id="80ec0-188">You can also set the value to `Custom`.</span></span> <span data-ttu-id="80ec0-189">Pokud je nastavena na `Custom` hodnotu, je nutné nastavit také `customCertificateValidatorType` atribut na sestavení a typ použitý k ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="80ec0-189">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="80ec0-190">Pokud chcete vytvořit vlastní vlastní validátor, musí dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="80ec0-190">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="80ec0-191">Další informace najdete v tématu [jak: Vytvoření služby, která používá vlastní validátor certifikátů](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="80ec0-191">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="80ec0-192">Příklad</span><span class="sxs-lookup"><span data-stu-id="80ec0-192">Example</span></span>  
 <span data-ttu-id="80ec0-193">Následující kód Určuje certifikát X.509 a zadejte vlastní ověření v `<authentication>` elementu.</span><span class="sxs-lookup"><span data-stu-id="80ec0-193">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="80ec0-194">Viz také:</span><span class="sxs-lookup"><span data-stu-id="80ec0-194">See also</span></span>

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [<span data-ttu-id="80ec0-195">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="80ec0-195">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="80ec0-196">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="80ec0-196">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="80ec0-197">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="80ec0-197">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
