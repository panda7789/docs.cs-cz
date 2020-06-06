---
title: <authentication><clientCertificate>elementu
ms.date: 03/30/2017
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
ms.openlocfilehash: 99084f6b7afbdd8586ee706cd6ec44b349d81ff2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398269"
---
# <a name="authentication-of-clientcertificate-element"></a><span data-ttu-id="01d3a-102">\<authentication>\<clientCertificate>elementu</span><span class="sxs-lookup"><span data-stu-id="01d3a-102">\<authentication> of \<clientCertificate> Element</span></span>
<span data-ttu-id="01d3a-103">Určuje chování ověřování pro klientské certifikáty používané službou.</span><span class="sxs-lookup"><span data-stu-id="01d3a-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<authentication>**  
  
## <a name="syntax"></a><span data-ttu-id="01d3a-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="01d3a-104">Syntax</span></span>  
  
```xml  
<authentication customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                includeWindowsGroups="Boolean"
                mapClientCertificateToWindowsAccount="Boolean"
                revocationMode="NoCheck/Online/Offline"
                trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01d3a-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="01d3a-105">Attributes and Elements</span></span>  
 <span data-ttu-id="01d3a-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="01d3a-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01d3a-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="01d3a-107">Attributes</span></span>  
  
|<span data-ttu-id="01d3a-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="01d3a-108">Attribute</span></span>|<span data-ttu-id="01d3a-109">Popis</span><span class="sxs-lookup"><span data-stu-id="01d3a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01d3a-110">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="01d3a-110">customCertificateValidatorType</span></span>|<span data-ttu-id="01d3a-111">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="01d3a-111">Optional string.</span></span> <span data-ttu-id="01d3a-112">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="01d3a-112">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="01d3a-113">Tento atribut musí být nastaven `certificateValidationMode` , je-li nastavena na hodnotu `Custom` .</span><span class="sxs-lookup"><span data-stu-id="01d3a-113">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="01d3a-114">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="01d3a-114">certificateValidationMode</span></span>|<span data-ttu-id="01d3a-115">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="01d3a-115">Optional enumeration.</span></span> <span data-ttu-id="01d3a-116">Určuje jeden z režimů používaných k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="01d3a-116">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="01d3a-117">Tento atribut je <xref:System.ServiceModel.Security.X509CertificateValidationMode> typu.</span><span class="sxs-lookup"><span data-stu-id="01d3a-117">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="01d3a-118">Je-li nastaveno na hodnotu <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType> , `customCertificateValidator` musí být zadána také.</span><span class="sxs-lookup"><span data-stu-id="01d3a-118">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="01d3a-119">Výchozí formát je <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="01d3a-119">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="01d3a-120">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="01d3a-120">includeWindowsGroups</span></span>|<span data-ttu-id="01d3a-121">Volitelná logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="01d3a-121">Optional Boolean.</span></span> <span data-ttu-id="01d3a-122">Určuje, zda jsou skupiny systému Windows zahrnuty v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="01d3a-122">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="01d3a-123">Nastavení tohoto atributu na `true` má vliv na výkon, protože má za následek rozšíření celé skupiny.</span><span class="sxs-lookup"><span data-stu-id="01d3a-123">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="01d3a-124">Nastavte tento atribut na, `false` Pokud nepotřebujete vytvořit seznam skupin, do kterých uživatel patří.</span><span class="sxs-lookup"><span data-stu-id="01d3a-124">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="01d3a-125">mapClientCertificateToWindowsAccount</span><span class="sxs-lookup"><span data-stu-id="01d3a-125">mapClientCertificateToWindowsAccount</span></span>|<span data-ttu-id="01d3a-126">Datového.</span><span class="sxs-lookup"><span data-stu-id="01d3a-126">Boolean.</span></span> <span data-ttu-id="01d3a-127">Určuje, jestli je možné klienta namapovat na identitu Windows pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="01d3a-127">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="01d3a-128">K tomu musí být povolená služba Active Directory.</span><span class="sxs-lookup"><span data-stu-id="01d3a-128">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="01d3a-129">revocationMode</span><span class="sxs-lookup"><span data-stu-id="01d3a-129">revocationMode</span></span>|<span data-ttu-id="01d3a-130">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="01d3a-130">Optional enumeration.</span></span> <span data-ttu-id="01d3a-131">Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (RCL).</span><span class="sxs-lookup"><span data-stu-id="01d3a-131">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="01d3a-132">Výchozí formát je `Online`.</span><span class="sxs-lookup"><span data-stu-id="01d3a-132">The default is `Online`.</span></span> <span data-ttu-id="01d3a-133">Tato hodnota se při použití zabezpečení přenosu HTTP ignoruje.</span><span class="sxs-lookup"><span data-stu-id="01d3a-133">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="01d3a-134">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="01d3a-134">trustedStoreLocation</span></span>|<span data-ttu-id="01d3a-135">Volitelný výčet.</span><span class="sxs-lookup"><span data-stu-id="01d3a-135">Optional enumeration.</span></span> <span data-ttu-id="01d3a-136">Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="01d3a-136">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="01d3a-137">Tato hodnota se používá, když je certifikát služby vyjednán klientovi.</span><span class="sxs-lookup"><span data-stu-id="01d3a-137">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="01d3a-138">Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="01d3a-138">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="01d3a-139">Výchozí formát je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="01d3a-139">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="01d3a-140">customCertificateValidatorType – atribut</span><span class="sxs-lookup"><span data-stu-id="01d3a-140">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="01d3a-141">Hodnota</span><span class="sxs-lookup"><span data-stu-id="01d3a-141">Value</span></span>|<span data-ttu-id="01d3a-142">Description</span><span class="sxs-lookup"><span data-stu-id="01d3a-142">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="01d3a-143">Řetězec</span><span class="sxs-lookup"><span data-stu-id="01d3a-143">String</span></span>|<span data-ttu-id="01d3a-144">Určuje název typu a sestavení a další data, která se používají k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="01d3a-144">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="01d3a-145">certificateValidationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="01d3a-145">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="01d3a-146">Hodnota</span><span class="sxs-lookup"><span data-stu-id="01d3a-146">Value</span></span>|<span data-ttu-id="01d3a-147">Description</span><span class="sxs-lookup"><span data-stu-id="01d3a-147">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="01d3a-148">Výčet</span><span class="sxs-lookup"><span data-stu-id="01d3a-148">Enumeration</span></span>|<span data-ttu-id="01d3a-149">Jedna z následujících hodnot: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span><span class="sxs-lookup"><span data-stu-id="01d3a-149">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="01d3a-150">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="01d3a-150">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="01d3a-151">revocationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="01d3a-151">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="01d3a-152">Hodnota</span><span class="sxs-lookup"><span data-stu-id="01d3a-152">Value</span></span>|<span data-ttu-id="01d3a-153">Description</span><span class="sxs-lookup"><span data-stu-id="01d3a-153">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="01d3a-154">Výčet</span><span class="sxs-lookup"><span data-stu-id="01d3a-154">Enumeration</span></span>|<span data-ttu-id="01d3a-155">Jedna z následujících hodnot: nekontrolujte, online, offline.</span><span class="sxs-lookup"><span data-stu-id="01d3a-155">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="01d3a-156">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="01d3a-156">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="01d3a-157">trustedStoreLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="01d3a-157">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="01d3a-158">Hodnota</span><span class="sxs-lookup"><span data-stu-id="01d3a-158">Value</span></span>|<span data-ttu-id="01d3a-159">Description</span><span class="sxs-lookup"><span data-stu-id="01d3a-159">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="01d3a-160">Výčet</span><span class="sxs-lookup"><span data-stu-id="01d3a-160">Enumeration</span></span>|<span data-ttu-id="01d3a-161">Jedna z následujících hodnot: `LocalMachine` nebo `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="01d3a-161">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="01d3a-162">Výchozí formát je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="01d3a-162">The default is `CurrentUser`.</span></span> <span data-ttu-id="01d3a-163">Pokud klientská aplikace běží pod účtem systému, certifikát se obvykle nachází v části `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="01d3a-163">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="01d3a-164">Pokud klientská aplikace běží pod uživatelským účtem, bude certifikát typicky v `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="01d3a-164">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01d3a-165">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="01d3a-165">Child Elements</span></span>  
 <span data-ttu-id="01d3a-166">Žádné</span><span class="sxs-lookup"><span data-stu-id="01d3a-166">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01d3a-167">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="01d3a-167">Parent Elements</span></span>  
  
|<span data-ttu-id="01d3a-168">Prvek</span><span class="sxs-lookup"><span data-stu-id="01d3a-168">Element</span></span>|<span data-ttu-id="01d3a-169">Description</span><span class="sxs-lookup"><span data-stu-id="01d3a-169">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)|<span data-ttu-id="01d3a-170">Definuje certifikát X. 509, který se používá k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="01d3a-170">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="01d3a-171">Poznámky</span><span class="sxs-lookup"><span data-stu-id="01d3a-171">Remarks</span></span>  
 <span data-ttu-id="01d3a-172">`<authentication>`Prvek odpovídá <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídě.</span><span class="sxs-lookup"><span data-stu-id="01d3a-172">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="01d3a-173">Umožňuje vám přizpůsobit způsob ověřování klientů.</span><span class="sxs-lookup"><span data-stu-id="01d3a-173">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="01d3a-174">Můžete nastavit `certificateValidationMode` atribut na,, `None` , `ChainTrust` `PeerOrChainTrust` `PeerTrust` nebo `Custom` .</span><span class="sxs-lookup"><span data-stu-id="01d3a-174">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="01d3a-175">Ve výchozím nastavení je úroveň nastavena na hodnotu `ChainTrust` , která určuje, že každý certifikát musí být nalezen v hierarchii certifikátů končících *kořenovou autoritou* v horní části řetězce.</span><span class="sxs-lookup"><span data-stu-id="01d3a-175">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="01d3a-176">Toto je nejbezpečnější režim.</span><span class="sxs-lookup"><span data-stu-id="01d3a-176">This is the most secure mode.</span></span> <span data-ttu-id="01d3a-177">Můžete také nastavit hodnotu na `PeerOrChainTrust` , což znamená, že jsou přijímány certifikáty vystavené svým držitelem (vztah důvěryhodnosti peering) i certifikáty, které jsou v důvěryhodném řetězci.</span><span class="sxs-lookup"><span data-stu-id="01d3a-177">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="01d3a-178">Tato hodnota se používá při vývoji a ladění klientů a služeb vzhledem k tomu, že certifikáty vystavené svým držitelem nemusejí být zakoupeny důvěryhodnou autoritou.</span><span class="sxs-lookup"><span data-stu-id="01d3a-178">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="01d3a-179">Při nasazování klienta použijte `ChainTrust` místo něj hodnotu.</span><span class="sxs-lookup"><span data-stu-id="01d3a-179">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="01d3a-180">Můžete také nastavit hodnotu na `Custom` .</span><span class="sxs-lookup"><span data-stu-id="01d3a-180">You can also set the value to `Custom`.</span></span> <span data-ttu-id="01d3a-181">Pokud je nastaveno na `Custom` hodnotu, je nutné také nastavit `customCertificateValidatorType` atribut na sestavení a typ použitý k ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="01d3a-181">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="01d3a-182">Chcete-li vytvořit vlastní validátor, je nutné dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="01d3a-182">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="01d3a-183">Další informace najdete v tématu [Postup: vytvoření služby, která využívá vlastní validátor certifikátů](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="01d3a-183">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="01d3a-184">Příklad</span><span class="sxs-lookup"><span data-stu-id="01d3a-184">Example</span></span>  
 <span data-ttu-id="01d3a-185">Následující kód Určuje certifikát X. 509 a typ vlastního ověřování v `<authentication>` elementu.</span><span class="sxs-lookup"><span data-stu-id="01d3a-185">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="01d3a-186">Viz také</span><span class="sxs-lookup"><span data-stu-id="01d3a-186">See also</span></span>

- <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>
- <xref:System.ServiceModel.Security.X509CertificateValidationMode>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>
- [<span data-ttu-id="01d3a-187">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="01d3a-187">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="01d3a-188">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="01d3a-188">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="01d3a-189">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="01d3a-189">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
