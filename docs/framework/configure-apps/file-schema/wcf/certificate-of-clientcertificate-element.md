---
title: <certificate><clientCertificate>elementu
ms.date: 03/30/2017
ms.assetid: 00297efb-a7f2-4e03-bc2b-943d545610fc
ms.openlocfilehash: d0c4ef9d3657d2dfa787feb3576beda09d1997a3
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400534"
---
# <a name="certificate-of-clientcertificate-element"></a><span data-ttu-id="3ce98-102">\<certificate>\<clientCertificate>elementu</span><span class="sxs-lookup"><span data-stu-id="3ce98-102">\<certificate> of \<clientCertificate> Element</span></span>
<span data-ttu-id="3ce98-103">Určuje certifikát X. 509, který se používá k podpisu a šifrování zpráv.</span><span class="sxs-lookup"><span data-stu-id="3ce98-103">Specifies an X.509 certificate used to sign and encrypt messages.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceBehaviors>**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<serviceCredentials>**](servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCertificate>**](clientcertificate-of-servicecredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="3ce98-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ce98-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation = "CurrentUser/LocalMachine"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ce98-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3ce98-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3ce98-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3ce98-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ce98-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3ce98-107">Attributes</span></span>  
  
|<span data-ttu-id="3ce98-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="3ce98-108">Attribute</span></span>|<span data-ttu-id="3ce98-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3ce98-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="3ce98-110">Řetězec, který obsahuje hodnotu, která se má vyhledat v úložišti certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="3ce98-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="3ce98-111">Typ obsažený v atributu musí splňovat požadavky zadaného X509FindType.</span><span class="sxs-lookup"><span data-stu-id="3ce98-111">The type contained in the attribute must satisfy the requirements of the specified X509FindType.</span></span> <span data-ttu-id="3ce98-112">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="3ce98-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="3ce98-113">Určuje umístění úložiště certifikátů X. 509, které klient používá k ověření certifikátu serveru proti.</span><span class="sxs-lookup"><span data-stu-id="3ce98-113">Specifies the location of the X.509 certificate store that the client uses to validate the server’s certificate against.</span></span> <span data-ttu-id="3ce98-114">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="3ce98-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3ce98-115">-LocalMachine: úložiště certifikátů přiřazené k místnímu počítači.</span><span class="sxs-lookup"><span data-stu-id="3ce98-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="3ce98-116">-CurrentUser: úložiště certifikátů přiřazené k aktuálnímu uživateli.</span><span class="sxs-lookup"><span data-stu-id="3ce98-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="3ce98-117">Výchozí hodnota je LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="3ce98-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="3ce98-118">Určuje název úložiště certifikátů X. 509, které se má otevřít.</span><span class="sxs-lookup"><span data-stu-id="3ce98-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="3ce98-119">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="3ce98-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3ce98-120">-AddressBook: úložiště certifikátů pro ostatní uživatele.</span><span class="sxs-lookup"><span data-stu-id="3ce98-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="3ce98-121">-AuthRoot: úložiště certifikátů pro certifikační autority třetích stran (CAs).</span><span class="sxs-lookup"><span data-stu-id="3ce98-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="3ce98-122">-Certifikační autorita: úložiště certifikátů pro zprostředkující certifikační autority (CAs).</span><span class="sxs-lookup"><span data-stu-id="3ce98-122">-   CertificationAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="3ce98-123">-Nepovoleno: úložiště certifikátů pro odvolané certifikáty.</span><span class="sxs-lookup"><span data-stu-id="3ce98-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="3ce98-124">– Moje: úložiště certifikátů pro osobní certifikáty.</span><span class="sxs-lookup"><span data-stu-id="3ce98-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="3ce98-125">-Root: úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CAs).</span><span class="sxs-lookup"><span data-stu-id="3ce98-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="3ce98-126">-TrustedPeople: úložiště certifikátů pro přímo důvěryhodné osoby a prostředky.</span><span class="sxs-lookup"><span data-stu-id="3ce98-126">-   TrustedPeople: Certificate store for directly trusted people and resources.</span></span><br /><span data-ttu-id="3ce98-127">-TrustedPublisher: úložiště certifikátů pro vydavatele přímo důvěryhodných vydavatelů.</span><span class="sxs-lookup"><span data-stu-id="3ce98-127">-   TrustedPublisher: Certificate store for directly trusted publishers.</span></span><br /><br /> <span data-ttu-id="3ce98-128">Výchozí hodnota je Moje.</span><span class="sxs-lookup"><span data-stu-id="3ce98-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="3ce98-129">Definuje typ hledání X. 509, které se má provést.</span><span class="sxs-lookup"><span data-stu-id="3ce98-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="3ce98-130">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="3ce98-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3ce98-131">- FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="3ce98-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="3ce98-132">- FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="3ce98-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="3ce98-133">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="3ce98-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="3ce98-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="3ce98-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="3ce98-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="3ce98-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="3ce98-136">- FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="3ce98-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="3ce98-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="3ce98-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="3ce98-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="3ce98-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="3ce98-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="3ce98-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="3ce98-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="3ce98-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="3ce98-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="3ce98-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="3ce98-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="3ce98-142">-   FindByExtension</span></span><br /><span data-ttu-id="3ce98-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="3ce98-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="3ce98-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="3ce98-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="3ce98-145">Typ obsažený v `findValue` atributu musí splňovat požadavky zadaného X509FindType.</span><span class="sxs-lookup"><span data-stu-id="3ce98-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified X509FindType.</span></span><br /><br /> <span data-ttu-id="3ce98-146">Výchozí hodnota je FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="3ce98-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ce98-147">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3ce98-147">Child Elements</span></span>  
 <span data-ttu-id="3ce98-148">Žádné</span><span class="sxs-lookup"><span data-stu-id="3ce98-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ce98-149">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3ce98-149">Parent Elements</span></span>  
  
|<span data-ttu-id="3ce98-150">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ce98-150">Element</span></span>|<span data-ttu-id="3ce98-151">Description</span><span class="sxs-lookup"><span data-stu-id="3ce98-151">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCertificate>](clientcertificate-of-servicecredentials.md)||  
  
## <a name="remarks"></a><span data-ttu-id="3ce98-152">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ce98-152">Remarks</span></span>  
 <span data-ttu-id="3ce98-153">`<certificate>`Element se používá v případě, že služba musí mít certifikát klienta předem pro zabezpečenou komunikaci s klientem.</span><span class="sxs-lookup"><span data-stu-id="3ce98-153">The `<certificate>` element is used when the service must have the client's certificate in advance to communicate securely with the client.</span></span> <span data-ttu-id="3ce98-154">K tomu dochází při použití duplexního způsobu komunikace.</span><span class="sxs-lookup"><span data-stu-id="3ce98-154">This occurs when using the duplex communication pattern.</span></span> <span data-ttu-id="3ce98-155">V typickém vzoru požadavků a odpovědí klient zahrne svůj certifikát do žádosti, kterou služba používá k šifrování a podepsání své odpovědi zpět do klienta.</span><span class="sxs-lookup"><span data-stu-id="3ce98-155">In the more typical request/response pattern, the client includes its certificate in the request, which the service uses to encrypt and sign its response back to the client.</span></span> <span data-ttu-id="3ce98-156">Ve způsobu duplexního přenosu však služba nemá požadavek od klienta, a proto potřebuje certifikát klienta předem, aby bylo možné zprávu zabezpečit klientovi.</span><span class="sxs-lookup"><span data-stu-id="3ce98-156">In the duplex communication pattern, however, the service does not have a request from the client and therefore it needs the client's certificate in advance to secure the message to the client.</span></span> <span data-ttu-id="3ce98-157">Proto je nutné získat certifikát klienta při vzdáleném vyjednávání a zadat certifikát pomocí tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="3ce98-157">Therefore you must obtain the client's certificate in an out-of-band negotiation, and specify the certificate using this element.</span></span> <span data-ttu-id="3ce98-158">Další informace o duplexních službách najdete v tématu [Postupy: Vytvoření duplexního kontraktu](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span><span class="sxs-lookup"><span data-stu-id="3ce98-158">For more information about duplex services, see [How to: Create a Duplex Contract](../../../wcf/feature-details/how-to-create-a-duplex-contract.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ce98-159">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ce98-159">Example</span></span>  
 <span data-ttu-id="3ce98-160">Následující kód určuje, jak najít vhodný certifikát X. 509 a typ vlastního ověřování v `<authentication>` elementu.</span><span class="sxs-lookup"><span data-stu-id="3ce98-160">The following code specifies how to find an appropriate X.509 certificate and a custom validation type in the `<authentication>` element.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ce98-161">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ce98-161">See also</span></span>

- <xref:System.ServiceModel.Security.X509CertificateInitiatorServiceCredential.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509InitiatorCertificateServiceElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509ClientCertificateCredentialsElement>
- [<span data-ttu-id="3ce98-162">Chování zabezpečení</span><span class="sxs-lookup"><span data-stu-id="3ce98-162">Security Behaviors</span></span>](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [<span data-ttu-id="3ce98-163">Postupy: Vytvoření služby, která používá vlastní validátor certifikátů</span><span class="sxs-lookup"><span data-stu-id="3ce98-163">How to: Create a Service that Employs a Custom Certificate Validator</span></span>](../../../wcf/extending/how-to-create-a-service-that-employs-a-custom-certificate-validator.md)
- [<span data-ttu-id="3ce98-164">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="3ce98-164">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
