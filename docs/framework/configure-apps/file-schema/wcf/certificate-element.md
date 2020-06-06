---
title: Element <certificate>
ms.date: 03/30/2017
ms.assetid: 9b3d9233-ef35-477a-bf5d-efd1e80a52f4
ms.openlocfilehash: e28e7d16073a56f3b6126439644bfff86c9af18b
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400557"
---
# <a name="certificate-element"></a><span data-ttu-id="3ec85-102">Element \<certificate></span><span class="sxs-lookup"><span data-stu-id="3ec85-102">\<certificate> Element</span></span>
<span data-ttu-id="3ec85-103">Určuje certifikát X. 509, který se použije pro podepisování a šifrování zpráv pro klienty peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="3ec85-103">Specifies an X.509 certificate to use for signing and encrypting messages for peer-to-peer clients.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificate>**  
  
## <a name="syntax"></a><span data-ttu-id="3ec85-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3ec85-104">Syntax</span></span>  
  
```xml  
<certificate findValue="String"
             storeLocation="LocalMachine/CurrentUser"
             storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"
             X509FindType="FindByThumbPrint/FindBySubjectName/FindBySubjectDistinguishedName/FindByIssuerName/FindByIssuerDistinguishedName/FindBySerialNumber/FindByTimeValid/FindByTimeNotYetValid/FindByTemplateName/FindByApplicationPolicy/FindByCertificatePolicy/FindByExtension/FindByKeyUsage/FindBySubjectKeyIdentifier" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3ec85-105">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3ec85-105">Attributes and Elements</span></span>  
 <span data-ttu-id="3ec85-106">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3ec85-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3ec85-107">Atributy</span><span class="sxs-lookup"><span data-stu-id="3ec85-107">Attributes</span></span>  
  
|<span data-ttu-id="3ec85-108">Atribut</span><span class="sxs-lookup"><span data-stu-id="3ec85-108">Attribute</span></span>|<span data-ttu-id="3ec85-109">Popis</span><span class="sxs-lookup"><span data-stu-id="3ec85-109">Description</span></span>|  
|---------------|-----------------|  
|`findValue`|<span data-ttu-id="3ec85-110">Řetězec, který obsahuje hodnotu, která se má vyhledat v úložišti certifikátů X. 509.</span><span class="sxs-lookup"><span data-stu-id="3ec85-110">A string that contains the value to search for in the X.509 certificate store.</span></span> <span data-ttu-id="3ec85-111">Typ obsažený v atributu musí splňovat požadavky zadané `x509FindType` .</span><span class="sxs-lookup"><span data-stu-id="3ec85-111">The type contained in the attribute must satisfy the requirements of the specified `x509FindType`.</span></span> <span data-ttu-id="3ec85-112">Výchozí hodnota je prázdný řetězec.</span><span class="sxs-lookup"><span data-stu-id="3ec85-112">The default is an empty string.</span></span>|  
|`storeLocation`|<span data-ttu-id="3ec85-113">Určuje umístění úložiště certifikátů X. 509, které klient používá k ověření certifikátu druhé strany.</span><span class="sxs-lookup"><span data-stu-id="3ec85-113">Specifies the location of the X.509 certificate store that the client uses to validate the peer's certificate against.</span></span> <span data-ttu-id="3ec85-114">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="3ec85-114">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3ec85-115">-LocalMachine: úložiště certifikátů přiřazené k místnímu počítači.</span><span class="sxs-lookup"><span data-stu-id="3ec85-115">-   LocalMachine: the certificate store assigned to the local machine.</span></span><br /><span data-ttu-id="3ec85-116">-CurrentUser: úložiště certifikátů přiřazené k aktuálnímu uživateli.</span><span class="sxs-lookup"><span data-stu-id="3ec85-116">-   CurrentUser: the certificate store assigned to the current user.</span></span><br /><br /> <span data-ttu-id="3ec85-117">Výchozí hodnota je LocalMachine.</span><span class="sxs-lookup"><span data-stu-id="3ec85-117">The default is LocalMachine.</span></span>|  
|`storeName`|<span data-ttu-id="3ec85-118">Určuje název úložiště certifikátů X. 509, které se má otevřít.</span><span class="sxs-lookup"><span data-stu-id="3ec85-118">Specifies the name of the X.509 certificate store to open.</span></span> <span data-ttu-id="3ec85-119">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="3ec85-119">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3ec85-120">-AddressBook: úložiště certifikátů pro ostatní uživatele.</span><span class="sxs-lookup"><span data-stu-id="3ec85-120">-   AddressBook: Certificate store for other users.</span></span><br /><span data-ttu-id="3ec85-121">-AuthRoot: úložiště certifikátů pro certifikační autority třetích stran (CAs).</span><span class="sxs-lookup"><span data-stu-id="3ec85-121">-   AuthRoot: Certificate store for third-party certification authorities (CAs).</span></span><br /><span data-ttu-id="3ec85-122">-CertificateAuthority: úložiště certifikátů pro zprostředkující certifikační autority (CAs).</span><span class="sxs-lookup"><span data-stu-id="3ec85-122">-   CertificateAuthority: Certificate store for intermediate certification authorities (CAs).</span></span><br /><span data-ttu-id="3ec85-123">-Nepovoleno: úložiště certifikátů pro odvolané certifikáty.</span><span class="sxs-lookup"><span data-stu-id="3ec85-123">-   Disallowed: Certificate store for revoked certificates.</span></span><br /><span data-ttu-id="3ec85-124">– Moje: úložiště certifikátů pro osobní certifikáty.</span><span class="sxs-lookup"><span data-stu-id="3ec85-124">-   My: Certificate store for personal certificates.</span></span><br /><span data-ttu-id="3ec85-125">-Root: úložiště certifikátů pro důvěryhodné kořenové certifikační autority (CAs).</span><span class="sxs-lookup"><span data-stu-id="3ec85-125">-   Root: Certificate store for trusted root certification authorities (CAs).</span></span><br /><span data-ttu-id="3ec85-126">-TrustedPeople: úložiště certifikátů pro přímo důvěryhodné osoby a prostředky.</span><span class="sxs-lookup"><span data-stu-id="3ec85-126">-   TrustedPeople: Certificate store for directly-trusted people and resources.</span></span><br /><span data-ttu-id="3ec85-127">-TrustedPublisher: úložiště certifikátů pro přímo důvěryhodné vydavatele.</span><span class="sxs-lookup"><span data-stu-id="3ec85-127">-   TrustedPublisher: Certificate store for directly-trusted publishers.</span></span><br /><br /> <span data-ttu-id="3ec85-128">Výchozí hodnota je Moje.</span><span class="sxs-lookup"><span data-stu-id="3ec85-128">The default is My.</span></span>|  
|`X509FindType`|<span data-ttu-id="3ec85-129">Definuje typ hledání X. 509, které se má provést.</span><span class="sxs-lookup"><span data-stu-id="3ec85-129">Defines the type of X.509 search to be executed.</span></span> <span data-ttu-id="3ec85-130">Platné hodnoty jsou následující:</span><span class="sxs-lookup"><span data-stu-id="3ec85-130">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="3ec85-131">- FindByThumbPrint</span><span class="sxs-lookup"><span data-stu-id="3ec85-131">-   FindByThumbPrint</span></span><br /><span data-ttu-id="3ec85-132">- FindBySubjectName</span><span class="sxs-lookup"><span data-stu-id="3ec85-132">-   FindBySubjectName</span></span><br /><span data-ttu-id="3ec85-133">- FindBySubjectDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="3ec85-133">-   FindBySubjectDistinguishedName</span></span><br /><span data-ttu-id="3ec85-134">- FindByIssuerName</span><span class="sxs-lookup"><span data-stu-id="3ec85-134">-   FindByIssuerName</span></span><br /><span data-ttu-id="3ec85-135">- FindByIssuerDistinguishedName</span><span class="sxs-lookup"><span data-stu-id="3ec85-135">-   FindByIssuerDistinguishedName</span></span><br /><span data-ttu-id="3ec85-136">- FindBySerialNumber</span><span class="sxs-lookup"><span data-stu-id="3ec85-136">-   FindBySerialNumber</span></span><br /><span data-ttu-id="3ec85-137">- FindByTimeValid</span><span class="sxs-lookup"><span data-stu-id="3ec85-137">-   FindByTimeValid</span></span><br /><span data-ttu-id="3ec85-138">- FindByTimeNotYetValid</span><span class="sxs-lookup"><span data-stu-id="3ec85-138">-   FindByTimeNotYetValid</span></span><br /><span data-ttu-id="3ec85-139">- FindByTemplateName</span><span class="sxs-lookup"><span data-stu-id="3ec85-139">-   FindByTemplateName</span></span><br /><span data-ttu-id="3ec85-140">- FindByApplicationPolicy</span><span class="sxs-lookup"><span data-stu-id="3ec85-140">-   FindByApplicationPolicy</span></span><br /><span data-ttu-id="3ec85-141">- FindByCertificatePolicy</span><span class="sxs-lookup"><span data-stu-id="3ec85-141">-   FindByCertificatePolicy</span></span><br /><span data-ttu-id="3ec85-142">- FindByExtension</span><span class="sxs-lookup"><span data-stu-id="3ec85-142">-   FindByExtension</span></span><br /><span data-ttu-id="3ec85-143">- FindByKeyUsage</span><span class="sxs-lookup"><span data-stu-id="3ec85-143">-   FindByKeyUsage</span></span><br /><span data-ttu-id="3ec85-144">- FindBySubjectKeyIdentifier</span><span class="sxs-lookup"><span data-stu-id="3ec85-144">-   FindBySubjectKeyIdentifier</span></span><br /><br /> <span data-ttu-id="3ec85-145">Typ obsažený v `findValue` atributu musí splňovat požadavky zadané `X509FindType` .</span><span class="sxs-lookup"><span data-stu-id="3ec85-145">The type contained in the `findValue` attribute must satisfy the requirements of the specified `X509FindType`.</span></span><br /><br /> <span data-ttu-id="3ec85-146">Výchozí hodnota je FindBySubjectDistinguishedName.</span><span class="sxs-lookup"><span data-stu-id="3ec85-146">The default value is FindBySubjectDistinguishedName.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3ec85-147">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="3ec85-147">Child Elements</span></span>  
 <span data-ttu-id="3ec85-148">Žádné</span><span class="sxs-lookup"><span data-stu-id="3ec85-148">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3ec85-149">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="3ec85-149">Parent Elements</span></span>  
  
|<span data-ttu-id="3ec85-150">Prvek</span><span class="sxs-lookup"><span data-stu-id="3ec85-150">Element</span></span>|<span data-ttu-id="3ec85-151">Description</span><span class="sxs-lookup"><span data-stu-id="3ec85-151">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="3ec85-152">Určuje přihlašovací údaje, které se používají při ověřování klientů peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="3ec85-152">Specifies credentials used when authenticating peer-to-peer clients.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3ec85-153">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3ec85-153">Remarks</span></span>  
 <span data-ttu-id="3ec85-154">Tento prvek konfigurace obsahuje instanci X509Certificate2, která se používá při ověřování sousedních sítí v partnerské síti.</span><span class="sxs-lookup"><span data-stu-id="3ec85-154">This configuration element contains a X509Certificate2 instance used when authenticating neighbors in the peer mesh.</span></span>  
  
 <span data-ttu-id="3ec85-155">Další informace o programování peer-to-peer najdete v tématu [sítě peer-to-peer](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="3ec85-155">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="3ec85-156">Příklad</span><span class="sxs-lookup"><span data-stu-id="3ec85-156">Example</span></span>  
 <span data-ttu-id="3ec85-157">Následující kód určuje, jak najít certifikát používaný ve scénáři peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="3ec85-157">The following code specifies how to find the certificate used in a peer-to-peer scenario.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3ec85-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="3ec85-158">See also</span></span>

- <xref:System.ServiceModel.Configuration.PeerCredentialElement>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.Certificate%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateElement>
- <xref:System.ServiceModel.Security.PeerCredential.Certificate%2A>
- [<span data-ttu-id="3ec85-159">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="3ec85-159">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="3ec85-160">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="3ec85-160">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="3ec85-161">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3ec85-161">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="3ec85-162">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="3ec85-162">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="3ec85-163">Zabezpečení aplikací rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="3ec85-163">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
