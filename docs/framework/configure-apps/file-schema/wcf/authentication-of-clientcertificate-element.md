---
title: '&lt;authentication&gt; elementu &lt;clientCertificate&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4a55eea2-1826-4026-b911-b7cc9e9c8bfe
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0bebbc8b5cc315e92645cbbf0321de53122c7b1c
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="ltauthenticationgt-of-ltclientcertificategt-element"></a><span data-ttu-id="2da09-102">&lt;authentication&gt; elementu &lt;clientCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="2da09-102">&lt;authentication&gt; of &lt;clientCertificate&gt; Element</span></span>
<span data-ttu-id="2da09-103">Určuje chování ověřování pro klientské certifikáty používané služby.</span><span class="sxs-lookup"><span data-stu-id="2da09-103">Specifies authentication behaviors for client certificates used by a service.</span></span>  
  
 <span data-ttu-id="2da09-104">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="2da09-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="2da09-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2da09-105">\<behaviors></span></span>  
<span data-ttu-id="2da09-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2da09-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="2da09-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2da09-107">\<behavior></span></span>  
<span data-ttu-id="2da09-108">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="2da09-108">\<serviceCredentials></span></span>  
<span data-ttu-id="2da09-109">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="2da09-109">\<clientCertificate></span></span>  
<span data-ttu-id="2da09-110">\<ověřování ></span><span class="sxs-lookup"><span data-stu-id="2da09-110">\<authentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2da09-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2da09-111">Syntax</span></span>  
  
```xml  
<authentication  
customCertificateValidatorType="namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode="ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
includeWindowsGroups="Boolean"  
mapClientCertificateToWindowsAccount="Boolean"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2da09-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2da09-112">Attributes and Elements</span></span>  
 <span data-ttu-id="2da09-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2da09-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2da09-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="2da09-114">Attributes</span></span>  
  
|<span data-ttu-id="2da09-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="2da09-115">Attribute</span></span>|<span data-ttu-id="2da09-116">Popis</span><span class="sxs-lookup"><span data-stu-id="2da09-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2da09-117">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="2da09-117">customCertificateValidatorType</span></span>|<span data-ttu-id="2da09-118">Volitelný řetězec.</span><span class="sxs-lookup"><span data-stu-id="2da09-118">Optional string.</span></span> <span data-ttu-id="2da09-119">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="2da09-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="2da09-120">Tento atribut musí být nastaven při `certificateValidationMode` je nastaven na `Custom`.</span><span class="sxs-lookup"><span data-stu-id="2da09-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="2da09-121">certificateValidationMode</span><span class="sxs-lookup"><span data-stu-id="2da09-121">certificateValidationMode</span></span>|<span data-ttu-id="2da09-122">Volitelné výčtu.</span><span class="sxs-lookup"><span data-stu-id="2da09-122">Optional enumeration.</span></span> <span data-ttu-id="2da09-123">Určuje jeden z režimů slouží k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="2da09-123">Specifies one of the modes used to validate credentials.</span></span> <span data-ttu-id="2da09-124">Tento atribut je <xref:System.ServiceModel.Security.X509CertificateValidationMode> typu.</span><span class="sxs-lookup"><span data-stu-id="2da09-124">This attribute is of the <xref:System.ServiceModel.Security.X509CertificateValidationMode> type.</span></span> <span data-ttu-id="2da09-125">Pokud nastavena na <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, pak `customCertificateValidator` musí být uveden také.</span><span class="sxs-lookup"><span data-stu-id="2da09-125">If set to <xref:System.ServiceModel.Security.X509CertificateValidationMode.Custom?displayProperty=nameWithType>, then a `customCertificateValidator` must also be supplied.</span></span> <span data-ttu-id="2da09-126">Výchozí hodnota je <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="2da09-126">The default is <xref:System.ServiceModel.Security.X509CertificateValidationMode.ChainTrust?displayProperty=nameWithType>.</span></span>|  
|<span data-ttu-id="2da09-127">includeWindowsGroups</span><span class="sxs-lookup"><span data-stu-id="2da09-127">includeWindowsGroups</span></span>|<span data-ttu-id="2da09-128">Volitelné logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="2da09-128">Optional Boolean.</span></span> <span data-ttu-id="2da09-129">Určuje, pokud skupiny systému Windows jsou zahrnuty v kontextu zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="2da09-129">Specifies if Windows groups are included in the security context.</span></span> <span data-ttu-id="2da09-130">Nastavení tohoto atributu na `true` má dopad na výkon, jako je výsledkem rozšíření úplné skupiny.</span><span class="sxs-lookup"><span data-stu-id="2da09-130">Setting this attribute to `true` has a performance impact, as it results in a full group expansion.</span></span> <span data-ttu-id="2da09-131">Nastavte tento atribut `false` Pokud není potřeba vytvořit seznam skupin uživatel patří do.</span><span class="sxs-lookup"><span data-stu-id="2da09-131">Set this attribute to `false` if you do not need to establish the list of groups a user belongs to.</span></span>|  
|<span data-ttu-id="2da09-132">mapClientCertificateToWindowsAcccount</span><span class="sxs-lookup"><span data-stu-id="2da09-132">mapClientCertificateToWindowsAcccount</span></span>|<span data-ttu-id="2da09-133">Logická hodnota.</span><span class="sxs-lookup"><span data-stu-id="2da09-133">Boolean.</span></span> <span data-ttu-id="2da09-134">Určuje, zda klient lze mapovat na identitu systému Windows pomocí certifikátu.</span><span class="sxs-lookup"><span data-stu-id="2da09-134">Specifies whether the client can be mapped to a Windows identity using the certificate.</span></span> <span data-ttu-id="2da09-135">K tomu musí být povolena služby Active Directory.</span><span class="sxs-lookup"><span data-stu-id="2da09-135">Active Directory must be enabled to do this.</span></span>|  
|<span data-ttu-id="2da09-136">revocationMode</span><span class="sxs-lookup"><span data-stu-id="2da09-136">revocationMode</span></span>|<span data-ttu-id="2da09-137">Volitelné výčtu.</span><span class="sxs-lookup"><span data-stu-id="2da09-137">Optional enumeration.</span></span> <span data-ttu-id="2da09-138">Jeden z režimů používá k ověření pro seznamy odvolaných certifikátů (RCL).</span><span class="sxs-lookup"><span data-stu-id="2da09-138">One of the modes used to check for a revoked certificate lists (RCL).</span></span> <span data-ttu-id="2da09-139">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="2da09-139">The default is `Online`.</span></span> <span data-ttu-id="2da09-140">Tato hodnota se ignoruje, pokud pomocí zabezpečení přenosu HTTP.</span><span class="sxs-lookup"><span data-stu-id="2da09-140">This value is ignored when using HTTP transport security.</span></span>|  
|<span data-ttu-id="2da09-141">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="2da09-141">trustedStoreLocation</span></span>|<span data-ttu-id="2da09-142">Volitelné výčtu.</span><span class="sxs-lookup"><span data-stu-id="2da09-142">Optional enumeration.</span></span> <span data-ttu-id="2da09-143">Jedno z umístění úložiště dvě systému: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2da09-143">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="2da09-144">Tato hodnota se používá, když je klientovi vyjednal certifikát služby.</span><span class="sxs-lookup"><span data-stu-id="2da09-144">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="2da09-145">Ověření se provádí před **důvěryhodné osoby** uložit do umístění zadaného úložiště.</span><span class="sxs-lookup"><span data-stu-id="2da09-145">Validation is performed against the **Trusted People** store in the specified store location.</span></span> <span data-ttu-id="2da09-146">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2da09-146">The default is `CurrentUser`.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="2da09-147">customCertificateValidatorType atribut</span><span class="sxs-lookup"><span data-stu-id="2da09-147">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="2da09-148">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2da09-148">Value</span></span>|<span data-ttu-id="2da09-149">Popis</span><span class="sxs-lookup"><span data-stu-id="2da09-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2da09-150">String</span><span class="sxs-lookup"><span data-stu-id="2da09-150">String</span></span>|<span data-ttu-id="2da09-151">Určuje název typu a sestavení a další data použít k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="2da09-151">Specifies the type name and assembly and other data used to find the type.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="2da09-152">certificateValidationMode atribut</span><span class="sxs-lookup"><span data-stu-id="2da09-152">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="2da09-153">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2da09-153">Value</span></span>|<span data-ttu-id="2da09-154">Popis</span><span class="sxs-lookup"><span data-stu-id="2da09-154">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2da09-155">Výčet</span><span class="sxs-lookup"><span data-stu-id="2da09-155">Enumeration</span></span>|<span data-ttu-id="2da09-156">Jeden z následujících hodnot: None, PeerTrust, ChainTrust, PeerOrChainTrust, vlastní.</span><span class="sxs-lookup"><span data-stu-id="2da09-156">One of the following values: None, PeerTrust, ChainTrust, PeerOrChainTrust, Custom.</span></span><br /><br /> <span data-ttu-id="2da09-157">Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2da09-157">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="2da09-158">revocationMode atribut</span><span class="sxs-lookup"><span data-stu-id="2da09-158">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="2da09-159">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2da09-159">Value</span></span>|<span data-ttu-id="2da09-160">Popis</span><span class="sxs-lookup"><span data-stu-id="2da09-160">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2da09-161">Výčet</span><span class="sxs-lookup"><span data-stu-id="2da09-161">Enumeration</span></span>|<span data-ttu-id="2da09-162">Jeden z následujících hodnot: NoCheck, Online, do režimu Offline.</span><span class="sxs-lookup"><span data-stu-id="2da09-162">One of the following values: NoCheck, Online, Offline.</span></span> <span data-ttu-id="2da09-163">Další informace najdete v tématu [práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2da09-163">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="2da09-164">trustedStoreLocation atribut</span><span class="sxs-lookup"><span data-stu-id="2da09-164">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="2da09-165">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2da09-165">Value</span></span>|<span data-ttu-id="2da09-166">Popis</span><span class="sxs-lookup"><span data-stu-id="2da09-166">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2da09-167">Výčet</span><span class="sxs-lookup"><span data-stu-id="2da09-167">Enumeration</span></span>|<span data-ttu-id="2da09-168">Jeden z následujících hodnot: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2da09-168">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="2da09-169">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2da09-169">The default is `CurrentUser`.</span></span> <span data-ttu-id="2da09-170">Pokud klientská aplikace běží pod účtem systému pak certifikát je obvykle v části `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="2da09-170">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="2da09-171">Pokud klientská aplikace běží pod účtem uživatele, pak tento certifikát je obvykle v `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2da09-171">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2da09-172">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2da09-172">Child Elements</span></span>  
 <span data-ttu-id="2da09-173">Žádné</span><span class="sxs-lookup"><span data-stu-id="2da09-173">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2da09-174">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2da09-174">Parent Elements</span></span>  
  
|<span data-ttu-id="2da09-175">Prvek</span><span class="sxs-lookup"><span data-stu-id="2da09-175">Element</span></span>|<span data-ttu-id="2da09-176">Popis</span><span class="sxs-lookup"><span data-stu-id="2da09-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2da09-177">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="2da09-177">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)|<span data-ttu-id="2da09-178">Definuje certifikátu X.509. certifikát použitý k ověření klienta ke službě.</span><span class="sxs-lookup"><span data-stu-id="2da09-178">Defines an X.509 certificate used to authenticate a client to a service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2da09-179">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2da09-179">Remarks</span></span>  
 <span data-ttu-id="2da09-180">`<authentication>` Element odpovídá <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> třídy.</span><span class="sxs-lookup"><span data-stu-id="2da09-180">The `<authentication>` element corresponds to the <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication> class.</span></span> <span data-ttu-id="2da09-181">Umožňuje přizpůsobit, jak klienti se ověřují.</span><span class="sxs-lookup"><span data-stu-id="2da09-181">It enables you to customize how clients are authenticated.</span></span> <span data-ttu-id="2da09-182">Můžete nastavit `certificateValidationMode` atribut `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, nebo `Custom`.</span><span class="sxs-lookup"><span data-stu-id="2da09-182">You can set the `certificateValidationMode` attribute to `None`, `ChainTrust`, `PeerOrChainTrust`, `PeerTrust`, or `Custom`.</span></span> <span data-ttu-id="2da09-183">Ve výchozím nastavení je úroveň nastavena na `ChainTrust`, která určuje, že každý certifikát, je nutné nalézt v hierarchii certifikátů končí na *kořenová autorita* v horní části řetězu.</span><span class="sxs-lookup"><span data-stu-id="2da09-183">By default, the level is set to `ChainTrust`, which specifies that each certificate must be found in a hierarchy of certificates ending in a *root authority* at the top of the chain.</span></span> <span data-ttu-id="2da09-184">Toto je nejbezpečnější režim.</span><span class="sxs-lookup"><span data-stu-id="2da09-184">This is the most secure mode.</span></span> <span data-ttu-id="2da09-185">Můžete také nastavit hodnotu `PeerOrChainTrust`, která určuje, že samoobslužné vydaných certifikátů (peer vztahu důvěryhodnosti) jsou přijaty a také certifikáty, které jsou v důvěryhodné řetězu.</span><span class="sxs-lookup"><span data-stu-id="2da09-185">You can also set the value to `PeerOrChainTrust`, which specifies that self-issued certificates (peer trust) are accepted as well as certificates that are in a trusted chain.</span></span> <span data-ttu-id="2da09-186">Tato hodnota se používá při vývoji a ladění klientů a služeb, protože samoobslužné vydaných certifikátů nemusí zakoupenému od důvěryhodné autority.</span><span class="sxs-lookup"><span data-stu-id="2da09-186">This value is used when developing and debugging clients and services because self-issued certificates need not be purchased from a trusted authority.</span></span> <span data-ttu-id="2da09-187">Při nasazování klienta, použijte `ChainTrust` místo hodnoty.</span><span class="sxs-lookup"><span data-stu-id="2da09-187">When deploying a client, use the `ChainTrust` value instead.</span></span>  
  
 <span data-ttu-id="2da09-188">Můžete také nastavit hodnotu `Custom`.</span><span class="sxs-lookup"><span data-stu-id="2da09-188">You can also set the value to `Custom`.</span></span> <span data-ttu-id="2da09-189">Pokud nastavíte `Custom` hodnotu, je nutné také nastavit `customCertificateValidatorType` atribut sestavení a typ použitý k ověření certifikátu.</span><span class="sxs-lookup"><span data-stu-id="2da09-189">When set to the `Custom` value, you must also set the `customCertificateValidatorType` attribute to an assembly and type used to validate the certificate.</span></span> <span data-ttu-id="2da09-190">Pokud chcete vytvořit vlastní vlastní validátor, musí dědit z abstraktní <xref:System.IdentityModel.Selectors.X509CertificateValidator> třídy.</span><span class="sxs-lookup"><span data-stu-id="2da09-190">To create your own custom validator, you must inherit from the abstract <xref:System.IdentityModel.Selectors.X509CertificateValidator> class.</span></span> <span data-ttu-id="2da09-191">Další informace najdete v tématu [postupy: vytvoření služby, který využívá validátor certifikátu vlastní](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span><span class="sxs-lookup"><span data-stu-id="2da09-191">For more information, see [How to: Create a Service that Employs a Custom Certificate Validator](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2da09-192">Příklad</span><span class="sxs-lookup"><span data-stu-id="2da09-192">Example</span></span>  
 <span data-ttu-id="2da09-193">Následující kód určuje certifikátu X.509. certifikát a typ vlastní ověření v `<authentication>` elementu.</span><span class="sxs-lookup"><span data-stu-id="2da09-193">The following code specifies an X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
```xml  
<serviceBehaviors>  
 <behavior name="myServiceBehavior">  
  <clientCertificate>  
   <certificate   
         findValue="www.cohowinery.com"   
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
  
## <a name="see-also"></a><span data-ttu-id="2da09-194">Viz také</span><span class="sxs-lookup"><span data-stu-id="2da09-194">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509ClientCertificateAuthentication>  
 <xref:System.ServiceModel.Security.X509CertificateValidationMode>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Authentication%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateAuthenticationElement>  
 [<span data-ttu-id="2da09-195">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="2da09-195">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="2da09-196">Postupy: vytvoření služby, který využívá validátor vlastní certifikát</span><span class="sxs-lookup"><span data-stu-id="2da09-196">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="2da09-197">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="2da09-197">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
