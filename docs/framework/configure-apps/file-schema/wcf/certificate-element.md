---
title: Element <certificate>
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: 0594f04ab17a9561e895efcc92e97c16e77c0a4d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926195"
---
# <a name="certificate-element"></a><span data-ttu-id="92f7e-102">\<> certifikátu – element</span><span class="sxs-lookup"><span data-stu-id="92f7e-102">\<certificate> Element</span></span>
<span data-ttu-id="92f7e-103">Určuje certifikát X. 509, který se použije pro podepisování a šifrování zpráv pro klienty peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="92f7e-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
 <span data-ttu-id="92f7e-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="92f7e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="92f7e-105">\<> chování</span><span class="sxs-lookup"><span data-stu-id="92f7e-105">\<behaviors></span></span>  
<span data-ttu-id="92f7e-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="92f7e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="92f7e-107">\<> chování</span><span class="sxs-lookup"><span data-stu-id="92f7e-107">\<behavior></span></span>  
<span data-ttu-id="92f7e-108">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="92f7e-108">\<clientCredentials></span></span>  
<span data-ttu-id="92f7e-109">\<peer></span><span class="sxs-lookup"><span data-stu-id="92f7e-109">\<peer></span></span>  
<span data-ttu-id="92f7e-110">\<> certifikátu</span><span class="sxs-lookup"><span data-stu-id="92f7e-110">\<certificate></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92f7e-111">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="92f7e-111">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="92f7e-112">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="92f7e-112">Attributes and Elements</span></span>  
 <span data-ttu-id="92f7e-113">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="92f7e-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="92f7e-114">Atributy</span><span class="sxs-lookup"><span data-stu-id="92f7e-114">Attributes</span></span>  
  
|<span data-ttu-id="92f7e-115">Atribut</span><span class="sxs-lookup"><span data-stu-id="92f7e-115">Attribute</span></span>|<span data-ttu-id="92f7e-116">Popis</span><span class="sxs-lookup"><span data-stu-id="92f7e-116">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="92f7e-117">Řetězec, který obsahuje hodnotu, která se má vyhledat v úložišti certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="92f7e-117">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="92f7e-118">Typ obsažený v atributu musí splňovat požadavky zadané `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="92f7e-118">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="92f7e-119">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="92f7e-119">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="92f7e-120">Určuje umístění úložiště certifikátů X. 509, které klient používá k ověření certifikátu druhé strany.</span><span class="sxs-lookup"><span data-stu-id="92f7e-120">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="92f7e-121">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="92f7e-121">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="92f7e-122">-LocalMachine: úložiště certifikátů přiřazené k místnímu počítači.</span><span class="sxs-lookup"><span data-stu-id="92f7e-122">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="92f7e-123">-CurrentUser: úložiště certifikátů přiřazené k aktuálnímu uživateli.</span><span class="sxs-lookup"><span data-stu-id="92f7e-123">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="92f7e-124">Výchozí hodnota je LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="92f7e-124">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="92f7e-125">Určuje název úložiště certifikátů X. 509, které se má otevřít.</span><span class="sxs-lookup"><span data-stu-id="92f7e-125">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="92f7e-126">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="92f7e-126">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="92f7e-127">- AddressBook: Úložiště certifikátů pro ostatní uživatele.</span><span class="sxs-lookup"><span data-stu-id="92f7e-127">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="92f7e-128">- AuthRoot: Úložiště certifikátů pro certifikační autority třetích stran (CAs).</span><span class="sxs-lookup"><span data-stu-id="92f7e-128">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="92f7e-129">CertificateAuthority Úložiště certifikátů pro zprostředkující certifikační autority (CAs).</span><span class="sxs-lookup"><span data-stu-id="92f7e-129">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="92f7e-130">Zakázané Úložiště certifikátů pro odvolané certifikáty.</span><span class="sxs-lookup"><span data-stu-id="92f7e-130">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="92f7e-131">Složkách Úložiště certifikátů pro osobní certifikáty.</span><span class="sxs-lookup"><span data-stu-id="92f7e-131">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="92f7e-132">Zobrazuje Úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CAs).</span><span class="sxs-lookup"><span data-stu-id="92f7e-132">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="92f7e-133">TrustedPeople Úložiště certifikátů pro přímo důvěryhodné osoby a prostředky.</span><span class="sxs-lookup"><span data-stu-id="92f7e-133">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="92f7e-134">- TrustedPublisher: Úložiště certifikátů pro přímo důvěryhodné vydavatele.</span><span class="sxs-lookup"><span data-stu-id="92f7e-134">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="92f7e-135">Výchozí hodnota je my.</span><span class="sxs-lookup"><span data-stu-id="92f7e-135">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="92f7e-136">Definuje typ hledání X. 509, které se má provést.</span><span class="sxs-lookup"><span data-stu-id="92f7e-136">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="92f7e-137">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="92f7e-137">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="92f7e-138">- FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="92f7e-138">-   FindByThumbPrint</span></span><br /><span data-ttu-id="92f7e-139">- FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="92f7e-139">-   FindBySubjectName</span></span><br /><span data-ttu-id="92f7e-140">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="92f7e-140">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="92f7e-141">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="92f7e-141">-   FindByIssuerName</span></span><br /><span data-ttu-id="92f7e-142">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="92f7e-142">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="92f7e-143">- FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="92f7e-143">-   FindBySerialNumber</span></span><br /><span data-ttu-id="92f7e-144">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="92f7e-144">-   FindByTimeValid</span></span><br /><span data-ttu-id="92f7e-145">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="92f7e-145">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="92f7e-146">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="92f7e-146">-   FindByTemplateName</span></span><br /><span data-ttu-id="92f7e-147">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="92f7e-147">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="92f7e-148">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="92f7e-148">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="92f7e-149">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="92f7e-149">-   FindByExtension</span></span><br /><span data-ttu-id="92f7e-150">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="92f7e-150">-   FindByKeyUsage</span></span><br /><span data-ttu-id="92f7e-151">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="92f7e-151">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="92f7e-152">Typ obsažený v `findValue` atributu musí splňovat požadavky zadané `X509FindType`.</span><span class="sxs-lookup"><span data-stu-id="92f7e-152">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="92f7e-153">Výchozí hodnota je FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="92f7e-153">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="92f7e-154">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="92f7e-154">Child Elements</span></span>  
 <span data-ttu-id="92f7e-155">Žádné</span><span class="sxs-lookup"><span data-stu-id="92f7e-155">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="92f7e-156">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="92f7e-156">Parent Elements</span></span>  
  
|<span data-ttu-id="92f7e-157">Prvek</span><span class="sxs-lookup"><span data-stu-id="92f7e-157">Element</span></span>|<span data-ttu-id="92f7e-158">Popis</span><span class="sxs-lookup"><span data-stu-id="92f7e-158">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="92f7e-159">\<peer></span><span class="sxs-lookup"><span data-stu-id="92f7e-159">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="92f7e-160">Určuje přihlašovací údaje, které se používají při ověřování klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="92f7e-160">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92f7e-161">Poznámky</span><span class="sxs-lookup"><span data-stu-id="92f7e-161">Remarks</span></span>  
 <span data-ttu-id="92f7e-162">Tento prvek konfigurace obsahuje instanci X509Certificate2, která se používá při ověřování sousedních sítí v partnerské síti.</span><span class="sxs-lookup"><span data-stu-id="92f7e-162">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="92f7e-163">Další informace o programování peer-to-peer najdete v tématu [sítě peer-to-peer](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="92f7e-163">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="92f7e-164">Příklad</span><span class="sxs-lookup"><span data-stu-id="92f7e-164">Example</span></span>  
 <span data-ttu-id="92f7e-165">Následující kód určuje, jak najít certifikát používaný ve scénáři peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="92f7e-165">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="92f7e-166">Viz také:</span><span class="sxs-lookup"><span data-stu-id="92f7e-166">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="92f7e-167">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="92f7e-167">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="92f7e-168">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="92f7e-168">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="92f7e-169">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="92f7e-169">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="92f7e-170">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="92f7e-170">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="92f7e-171">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="92f7e-171">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
