---
title: Element <certificate>
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: f0cec2ad0e7747ddbc0ef566b4e8cbc7f8795b02
ms.sourcegitcommit: b8ace47d839f943f785b89e2fff8092b0bf8f565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/03/2019
ms.locfileid: "55675384"
---
# <a name="certificate-element"></a><span data-ttu-id="69815-102">\<certifikát > – Element</span><span class="sxs-lookup"><span data-stu-id="69815-102">\<certificate> Element</span></span>
<span data-ttu-id="69815-103">Určuje certifikát X.509, který chcete použít pro podepisování a šifrování zpráv klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="69815-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="69815-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="69815-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="69815-105">\<chování ></span><span class="sxs-lookup"><span data-stu-id="69815-105">\<behaviors></span></span>  
<span data-ttu-id="69815-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="69815-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="69815-107">\<chování ></span><span class="sxs-lookup"><span data-stu-id="69815-107">\<behavior></span></span>  
<span data-ttu-id="69815-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="69815-108">\<clientCredentials></span></span>  
<span data-ttu-id="69815-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="69815-109">\<peer></span></span>  
<span data-ttu-id="69815-110">\<certifikát ></span><span class="sxs-lookup"><span data-stu-id="69815-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="69815-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="69815-111">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="69815-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="69815-112">Attributes and Elements</span></span>  
 <span data-ttu-id="69815-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="69815-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="69815-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="69815-114">Attributes</span></span>  
  
|<span data-ttu-id="69815-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="69815-115">Attribute</span></span>|<span data-ttu-id="69815-116">Popis</span><span class="sxs-lookup"><span data-stu-id="69815-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="69815-117">Řetězec, který obsahuje hodnotu vyhledávání v úložišti certifikátů X.509.</span><span class="sxs-lookup"><span data-stu-id="69815-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="69815-118">Typ obsažené v atributu musí splňovat požadavky na zadané `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="69815-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="69815-119">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="69815-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="69815-120">Určuje umístění úložiště certifikátů X.509, který klient používá k ověření certifikátu druhé strany.</span><span class="sxs-lookup"><span data-stu-id="69815-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="69815-121">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="69815-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="69815-122">-LocalMachine: úložiště certifikátů přiřazené do místního počítače.</span><span class="sxs-lookup"><span data-stu-id="69815-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="69815-123">-CurrentUser: úložiště certifikátů přiřazené aktuálnímu uživateli.</span><span class="sxs-lookup"><span data-stu-id="69815-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="69815-124">Výchozí hodnota je v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="69815-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="69815-125">Určuje název úložiště certifikátu X.509 otevřete.</span><span class="sxs-lookup"><span data-stu-id="69815-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="69815-126">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="69815-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="69815-127">-Adresáře: Úložiště certifikátů pro ostatní uživatele.</span><span class="sxs-lookup"><span data-stu-id="69815-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="69815-128">-AuthRoot: Úložiště certifikátů pro třetí strany certifikačními autoritami (CA).</span><span class="sxs-lookup"><span data-stu-id="69815-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="69815-129">-CertificateAuthority: Úložiště certifikátů zprostředkující certifikační autority (CA).</span><span class="sxs-lookup"><span data-stu-id="69815-129">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="69815-130">– Zakázáno: Úložiště certifikátů pro odvolaných certifikátů.</span><span class="sxs-lookup"><span data-stu-id="69815-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="69815-131">-Můj: Úložiště certifikátů pro osobní certifikáty.</span><span class="sxs-lookup"><span data-stu-id="69815-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="69815-132">-Root: Úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CA).</span><span class="sxs-lookup"><span data-stu-id="69815-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="69815-133">-TrustedPeople: Úložiště certifikátů přímo důvěryhodných osob a prostředky.</span><span class="sxs-lookup"><span data-stu-id="69815-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="69815-134">-TrustedPublisher: Úložiště certifikátů přímo důvěryhodných vydavatelů.</span><span class="sxs-lookup"><span data-stu-id="69815-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="69815-135">Výchozí hodnota je My.</span><span class="sxs-lookup"><span data-stu-id="69815-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="69815-136">Definuje typ hledání X.509, který se spustí.</span><span class="sxs-lookup"><span data-stu-id="69815-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="69815-137">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="69815-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="69815-138">-FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="69815-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="69815-139">-FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="69815-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="69815-140">-FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="69815-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="69815-141">-   FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="69815-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="69815-142">-   FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="69815-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="69815-143">-   FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="69815-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="69815-144">-FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="69815-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="69815-145">-FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="69815-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="69815-146">-FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="69815-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="69815-147">-FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="69815-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="69815-148">-FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="69815-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="69815-149">-FindByExtension</span><span class="sxs-lookup"><span data-stu-id="69815-149">-   FindByExtension</span></span><br /><span data-ttu-id="69815-150">-FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="69815-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="69815-151">-   FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="69815-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="69815-152">Typ součástí `findValue` atribut musí splňovat požadavky na zadané `X509FindType`.</span><span class="sxs-lookup"><span data-stu-id="69815-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="69815-153">Výchozí hodnota je FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="69815-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="69815-154">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="69815-154">Child Elements</span></span>  
 <span data-ttu-id="69815-155">Žádné</span><span class="sxs-lookup"><span data-stu-id="69815-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="69815-156">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="69815-156">Parent Elements</span></span>  
  
|<span data-ttu-id="69815-157">Prvek</span><span class="sxs-lookup"><span data-stu-id="69815-157">Element</span></span>|<span data-ttu-id="69815-158">Popis</span><span class="sxs-lookup"><span data-stu-id="69815-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="69815-159">\<peer></span><span class="sxs-lookup"><span data-stu-id="69815-159">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="69815-160">Určuje pověření používaný při ověřování klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="69815-160">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="69815-161">Poznámky</span><span class="sxs-lookup"><span data-stu-id="69815-161">Remarks</span></span>  
 <span data-ttu-id="69815-162">Tento prvek konfigurace obsahuje instanci X509Certificate2 používaný při ověřování okolí ve sdílené síti.</span><span class="sxs-lookup"><span data-stu-id="69815-162">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="69815-163">Další informace o programování peer-to-peer, naleznete v tématu [sítě Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="69815-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="69815-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="69815-164">Example</span></span>  
 <span data-ttu-id="69815-165">Následující kód určuje, jak najít certifikát použít ve scénáři peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="69815-165">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="69815-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="69815-166">See also</span></span>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="69815-167">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="69815-167">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="69815-168">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="69815-168">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="69815-169">[Ověřování zpráv protokolu peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="69815-169">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="69815-170">[Vlastní ověřování protokolu peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="69815-170">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="69815-171">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="69815-171">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
