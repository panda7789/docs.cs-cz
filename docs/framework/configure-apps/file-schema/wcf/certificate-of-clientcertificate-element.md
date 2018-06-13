---
title: '&lt;certificate&gt; elementu &lt;clientCertificate&gt;'
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: 07885f8f1a575ef5b6ccb8d5f91f38a561261183
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753388"
---
# <a name="ltcertificategt-of-ltclientcertificategt-element"></a><span data-ttu-id="f0216-102">&lt;certificate&gt; elementu &lt;clientCertificate&gt;</span><span class="sxs-lookup"><span data-stu-id="f0216-102">&lt;certificate&gt; of &lt;clientCertificate&gt; Element</span></span>
<span data-ttu-id="f0216-103">Určuje X.509 certifikát používaný k podepisování a šifrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="f0216-103">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
 <span data-ttu-id="f0216-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f0216-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f0216-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f0216-105">\<behaviors></span></span>  
<span data-ttu-id="f0216-106">\<serviceBehaviors ></span><span class="sxs-lookup"><span data-stu-id="f0216-106">\<serviceBehaviors></span></span>  
<span data-ttu-id="f0216-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="f0216-107">\<behavior></span></span>  
<span data-ttu-id="f0216-108">\<– serviceCredentials ></span><span class="sxs-lookup"><span data-stu-id="f0216-108">\<serviceCredentials></span></span>  
<span data-ttu-id="f0216-109">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="f0216-109">\<clientCertificate></span></span>  
<span data-ttu-id="f0216-110">\<certifikátu ></span><span class="sxs-lookup"><span data-stu-id="f0216-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f0216-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f0216-111">Syntax</span></span>  
  
```xml  
<certificate findValue = "String"   
storeLocation = "CurrentUser/LocalMachine"  
storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier"  
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f0216-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f0216-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f0216-113">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f0216-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f0216-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="f0216-114">Attributes</span></span>  
  
|<span data-ttu-id="f0216-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="f0216-115">Attribute</span></span>|<span data-ttu-id="f0216-116">Popis</span><span class="sxs-lookup"><span data-stu-id="f0216-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="f0216-117">Řetězec, který obsahuje hodnotu k vyhledání v úložišti certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="f0216-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="f0216-118">Typ obsažený v atributu musí splňovat požadavky na zadaný X509FindType.</span><span class="sxs-lookup"><span data-stu-id="f0216-118">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="f0216-119">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="f0216-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="f0216-120">Určuje umístění úložiště certifikátů X.509, který klient používá k ověření certifikátu serveru proti.</span><span class="sxs-lookup"><span data-stu-id="f0216-120">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="f0216-121">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="f0216-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f0216-122">-LocalMachine: úložiště certifikátů přiřazené k místnímu počítači.</span><span class="sxs-lookup"><span data-stu-id="f0216-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="f0216-123">-CurrentUser: úložiště certifikátů přiřazená aktuálnímu uživateli.</span><span class="sxs-lookup"><span data-stu-id="f0216-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="f0216-124">Výchozí hodnota je v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="f0216-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="f0216-125">Určuje název úložiště certifikátu X.509 otevřete.</span><span class="sxs-lookup"><span data-stu-id="f0216-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="f0216-126">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="f0216-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f0216-127">-Adresáře: Úložiště certifikátů pro ostatní uživatele.</span><span class="sxs-lookup"><span data-stu-id="f0216-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="f0216-128">-AuthRoot: Certifikát úložiště pro třetí strany certifikační autority (CA).</span><span class="sxs-lookup"><span data-stu-id="f0216-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="f0216-129">-Certifikační autorita: Úložiště certifikátů pro zprostředkující certifikační autority (CA).</span><span class="sxs-lookup"><span data-stu-id="f0216-129">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="f0216-130">-Nepovolené: Certifikát úložiště pro odvolané certifikáty.</span><span class="sxs-lookup"><span data-stu-id="f0216-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="f0216-131">-: Úložiště certifikátů my Pro osobní certifikáty.</span><span class="sxs-lookup"><span data-stu-id="f0216-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="f0216-132">-Root: Úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CA).</span><span class="sxs-lookup"><span data-stu-id="f0216-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="f0216-133">-TrustedPeople: Úložiště certifikátů přímo důvěryhodných osob a prostředky.</span><span class="sxs-lookup"><span data-stu-id="f0216-133">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="f0216-134">-TrustedPublisher: Úložiště certifikátů pro přímo důvěryhodné vydavatele.</span><span class="sxs-lookup"><span data-stu-id="f0216-134">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="f0216-135">Výchozí hodnota je můj.</span><span class="sxs-lookup"><span data-stu-id="f0216-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="f0216-136">Definuje typ vyhledávání X.509 provést.</span><span class="sxs-lookup"><span data-stu-id="f0216-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="f0216-137">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="f0216-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="f0216-138">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="f0216-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="f0216-139">-FindBySubjectName.</span><span class="sxs-lookup"><span data-stu-id="f0216-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="f0216-140">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="f0216-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="f0216-141">-FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="f0216-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="f0216-142">-FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="f0216-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="f0216-143">-FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="f0216-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="f0216-144">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="f0216-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="f0216-145">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="f0216-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="f0216-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="f0216-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="f0216-147">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="f0216-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="f0216-148">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="f0216-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="f0216-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="f0216-149">-   FindByExtension</span></span><br /><span data-ttu-id="f0216-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="f0216-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="f0216-151">-FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="f0216-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="f0216-152">Typ obsažený v `findValue` atributu musí splňovat požadavky na zadaný X509FindType.</span><span class="sxs-lookup"><span data-stu-id="f0216-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="f0216-153">Výchozí hodnota je FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="f0216-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f0216-154">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f0216-154">Child Elements</span></span>  
 <span data-ttu-id="f0216-155">Žádné</span><span class="sxs-lookup"><span data-stu-id="f0216-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f0216-156">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f0216-156">Parent Elements</span></span>  
  
|<span data-ttu-id="f0216-157">Prvek</span><span class="sxs-lookup"><span data-stu-id="f0216-157">Element</span></span>|<span data-ttu-id="f0216-158">Popis</span><span class="sxs-lookup"><span data-stu-id="f0216-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f0216-159">\<clientCertificate ></span><span class="sxs-lookup"><span data-stu-id="f0216-159">\<clientCertificate></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="f0216-160">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f0216-160">Remarks</span></span>  
 <span data-ttu-id="f0216-161">`<certificate>` Element se používá, když služba musí mít certifikát klienta předem pro bezpečnou komunikaci s klientem.</span><span class="sxs-lookup"><span data-stu-id="f0216-161">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="f0216-162">K tomu dochází, když pomocí vzoru duplexní komunikace.</span><span class="sxs-lookup"><span data-stu-id="f0216-162">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="f0216-163">Ve vzoru typičtější požadavků a odpovědí klienta zahrnuje svůj certifikát v žádosti, které služba používá k šifrování a podepisování odpověď zpět klientovi.</span><span class="sxs-lookup"><span data-stu-id="f0216-163">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="f0216-164">Ve vzoru duplexní komunikace ale služba nemá požadavek od klienta a proto potřebuje certifikát klienta předem k zabezpečení zprávy do klienta.</span><span class="sxs-lookup"><span data-stu-id="f0216-164">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="f0216-165">Proto musíte získat certifikát klienta v vyjednávání out-of-band a zadat certifikát pomocí tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="f0216-165">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="f0216-166">Další informace o duplexní služby najdete v tématu [postupy: vytvoření duplexního kontraktu](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="f0216-166">For more information about duplex services, see [How to: Create a Duplex Contract](../../../../../docs/framework/wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0216-167">Příklad</span><span class="sxs-lookup"><span data-stu-id="f0216-167">Example</span></span>  
 <span data-ttu-id="f0216-168">Následující kód určuje, jak se najít odpovídající certifikátu X.509. certifikát a vlastní ověření zadejte `<authentication>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f0216-168">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f0216-169">Viz také</span><span class="sxs-lookup"><span data-stu-id="f0216-169">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>  
 <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>  
 [<span data-ttu-id="f0216-170">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="f0216-170">Security Behaviors</span></span>](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [<span data-ttu-id="f0216-171">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="f0216-171">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../../../docs/framework/wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)  
 [<span data-ttu-id="f0216-172">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="f0216-172">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
