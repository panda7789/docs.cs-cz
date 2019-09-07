---
title: Element <certificate>
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: e28e7d16073a56f3b6126439644bfff86c9af18b
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400557"
---
# <a name="certificate-element"></a><span data-ttu-id="2baaf-102">\<> certifikátu – element</span><span class="sxs-lookup"><span data-stu-id="2baaf-102">\<certificate> Element</span></span>
<span data-ttu-id="2baaf-103">Určuje certifikát X. 509, který se použije pro podepisování a šifrování zpráv pro klienty peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="2baaf-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
<span data-ttu-id="2baaf-104">[ **\<> Konfigurace**](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="2baaf-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="2baaf-105">&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="2baaf-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="2baaf-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2baaf-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="2baaf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2baaf-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="2baaf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="2baaf-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="2baaf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)</span><span class="sxs-lookup"><span data-stu-id="2baaf-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)</span></span>\
<span data-ttu-id="2baaf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<Partnerský >** ](peer-of-clientcredentials-element.md)</span><span class="sxs-lookup"><span data-stu-id="2baaf-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)</span></span>\
<span data-ttu-id="2baaf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> certifikátu**</span><span class="sxs-lookup"><span data-stu-id="2baaf-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2baaf-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2baaf-112">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2baaf-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2baaf-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2baaf-114">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="2baaf-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2baaf-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="2baaf-115">Attributes</span></span>  
  
|<span data-ttu-id="2baaf-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="2baaf-116">Attribute</span></span>|<span data-ttu-id="2baaf-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2baaf-117">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="2baaf-118">Řetězec, který obsahuje hodnotu, která se má vyhledat v úložišti certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="2baaf-118">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="2baaf-119">Typ obsažený v atributu musí splňovat požadavky zadané `x509FindType`.</span><span class="sxs-lookup"><span data-stu-id="2baaf-119">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="2baaf-120">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="2baaf-120">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="2baaf-121">Určuje umístění úložiště certifikátů X. 509, které klient používá k ověření certifikátu druhé strany.</span><span class="sxs-lookup"><span data-stu-id="2baaf-121">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="2baaf-122">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="2baaf-122">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2baaf-123">-LocalMachine: úložiště certifikátů přiřazené k místnímu počítači.</span><span class="sxs-lookup"><span data-stu-id="2baaf-123">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="2baaf-124">-CurrentUser: úložiště certifikátů přiřazené k aktuálnímu uživateli.</span><span class="sxs-lookup"><span data-stu-id="2baaf-124">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="2baaf-125">Výchozí hodnota je LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="2baaf-125">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="2baaf-126">Určuje název úložiště certifikátů X. 509, které se má otevřít.</span><span class="sxs-lookup"><span data-stu-id="2baaf-126">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="2baaf-127">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="2baaf-127">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2baaf-128">- AddressBook: Úložiště certifikátů pro ostatní uživatele.</span><span class="sxs-lookup"><span data-stu-id="2baaf-128">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="2baaf-129">- AuthRoot: Úložiště certifikátů pro certifikační autority třetích stran (CAs).</span><span class="sxs-lookup"><span data-stu-id="2baaf-129">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="2baaf-130">CertificateAuthority Úložiště certifikátů pro zprostředkující certifikační autority (CAs).</span><span class="sxs-lookup"><span data-stu-id="2baaf-130">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="2baaf-131">Zakázané Úložiště certifikátů pro odvolané certifikáty.</span><span class="sxs-lookup"><span data-stu-id="2baaf-131">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="2baaf-132">Složkách Úložiště certifikátů pro osobní certifikáty.</span><span class="sxs-lookup"><span data-stu-id="2baaf-132">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="2baaf-133">Zobrazuje Úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CAs).</span><span class="sxs-lookup"><span data-stu-id="2baaf-133">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="2baaf-134">TrustedPeople Úložiště certifikátů pro přímo důvěryhodné osoby a prostředky.</span><span class="sxs-lookup"><span data-stu-id="2baaf-134">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="2baaf-135">- TrustedPublisher: Úložiště certifikátů pro přímo důvěryhodné vydavatele.</span><span class="sxs-lookup"><span data-stu-id="2baaf-135">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="2baaf-136">Výchozí hodnota je my.</span><span class="sxs-lookup"><span data-stu-id="2baaf-136">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="2baaf-137">Definuje typ hledání X. 509, které se má provést.</span><span class="sxs-lookup"><span data-stu-id="2baaf-137">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="2baaf-138">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="2baaf-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="2baaf-139">- FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="2baaf-139">-   FindByThumbPrint</span></span><br /><span data-ttu-id="2baaf-140">- FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="2baaf-140">-   FindBySubjectName</span></span><br /><span data-ttu-id="2baaf-141">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="2baaf-141">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="2baaf-142">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="2baaf-142">-   FindByIssuerName</span></span><br /><span data-ttu-id="2baaf-143">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="2baaf-143">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="2baaf-144">- FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="2baaf-144">-   FindBySerialNumber</span></span><br /><span data-ttu-id="2baaf-145">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="2baaf-145">-   FindByTimeValid</span></span><br /><span data-ttu-id="2baaf-146">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="2baaf-146">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="2baaf-147">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="2baaf-147">-   FindByTemplateName</span></span><br /><span data-ttu-id="2baaf-148">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="2baaf-148">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="2baaf-149">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="2baaf-149">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="2baaf-150">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="2baaf-150">-   FindByExtension</span></span><br /><span data-ttu-id="2baaf-151">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="2baaf-151">-   FindByKeyUsage</span></span><br /><span data-ttu-id="2baaf-152">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="2baaf-152">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="2baaf-153">Typ obsažený v `findValue` atributu musí splňovat požadavky zadané `X509FindType`.</span><span class="sxs-lookup"><span data-stu-id="2baaf-153">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="2baaf-154">Výchozí hodnota je FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="2baaf-154">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2baaf-155">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2baaf-155">Child Elements</span></span>  
 <span data-ttu-id="2baaf-156">Žádné</span><span class="sxs-lookup"><span data-stu-id="2baaf-156">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2baaf-157">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2baaf-157">Parent Elements</span></span>  
  
|<span data-ttu-id="2baaf-158">Prvek</span><span class="sxs-lookup"><span data-stu-id="2baaf-158">Element</span></span>|<span data-ttu-id="2baaf-159">Popis</span><span class="sxs-lookup"><span data-stu-id="2baaf-159">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2baaf-160">\<peer></span><span class="sxs-lookup"><span data-stu-id="2baaf-160">\<peer></span></span>](peer-of-clientcredentials-element.md)|<span data-ttu-id="2baaf-161">Určuje přihlašovací údaje, které se používají při ověřování klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="2baaf-161">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2baaf-162">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2baaf-162">Remarks</span></span>  
 <span data-ttu-id="2baaf-163">Tento prvek konfigurace obsahuje instanci X509Certificate2, která se používá při ověřování sousedních sítí v partnerské síti.</span><span class="sxs-lookup"><span data-stu-id="2baaf-163">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="2baaf-164">Další informace o programování peer-to-peer najdete v tématu [sítě peer-to-peer](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="2baaf-164">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="2baaf-165">Příklad</span><span class="sxs-lookup"><span data-stu-id="2baaf-165">Example</span></span>  
 <span data-ttu-id="2baaf-166">Následující kód určuje, jak najít certifikát používaný ve scénáři peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="2baaf-166">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="2baaf-167">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2baaf-167">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="2baaf-168">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="2baaf-168">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="2baaf-169">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="2baaf-169">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="2baaf-170">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2baaf-170">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="2baaf-171">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="2baaf-171">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="2baaf-172">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="2baaf-172">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
