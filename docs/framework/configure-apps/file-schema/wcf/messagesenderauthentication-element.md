---
title: <messageSenderAuthentication> – element
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: 804c280bcdb0fecc87f71121b7d95b5fd0268de9
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/28/2019
ms.locfileid: "67423126"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="c1b40-102">\<messageSenderAuthentication > – element</span><span class="sxs-lookup"><span data-stu-id="c1b40-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="c1b40-103">Určuje možnosti ověřování pro odesílatele zpráv peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="c1b40-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="c1b40-104">Další informace o programování peer-to-peer, naleznete v tématu [sítě Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="c1b40-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="c1b40-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c1b40-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="c1b40-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c1b40-106">\<behaviors></span></span>  
<span data-ttu-id="c1b40-107">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="c1b40-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="c1b40-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="c1b40-108">\<behavior></span></span>  
<span data-ttu-id="c1b40-109">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="c1b40-109">\<clientCredentials></span></span>  
<span data-ttu-id="c1b40-110">\<peer></span><span class="sxs-lookup"><span data-stu-id="c1b40-110">\<peer></span></span>  
<span data-ttu-id="c1b40-111">\<messageSenderAuthentication></span><span class="sxs-lookup"><span data-stu-id="c1b40-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1b40-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c1b40-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1b40-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="c1b40-113">Attributes and Elements</span></span>  
 <span data-ttu-id="c1b40-114">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c1b40-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1b40-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="c1b40-115">Attributes</span></span>  
  
|<span data-ttu-id="c1b40-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="c1b40-116">Attribute</span></span>|<span data-ttu-id="c1b40-117">Popis</span><span class="sxs-lookup"><span data-stu-id="c1b40-117">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="c1b40-118">Typ a sestavení používané pro ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="c1b40-118">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="c1b40-119">Tento atribut musí být nastaven při `certificateValidationMode` je nastavena na `Custom`.</span><span class="sxs-lookup"><span data-stu-id="c1b40-119">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="c1b40-120">Určuje jeden ze tří režimů používaných pro ověření pověření.</span><span class="sxs-lookup"><span data-stu-id="c1b40-120">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="c1b40-121">Pokud hodnotu `Custom`, o `customCertificateValidator` musí být rovněž dodán.</span><span class="sxs-lookup"><span data-stu-id="c1b40-121">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="c1b40-122">Jeden z režimů pro kontrolu seznamu odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="c1b40-122">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="c1b40-123">Jeden z umístění dvou systémových úložišť: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="c1b40-123">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="c1b40-124">Tato hodnota se používá při certifikát služby se vyjedná do klienta.</span><span class="sxs-lookup"><span data-stu-id="c1b40-124">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="c1b40-125">Ověření se provádí proti **důvěryhodné osoby** uložit do umístění určeného úložiště.</span><span class="sxs-lookup"><span data-stu-id="c1b40-125">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="c1b40-126">customCertificateValidatorType Attribute</span><span class="sxs-lookup"><span data-stu-id="c1b40-126">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="c1b40-127">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c1b40-127">Value</span></span>|<span data-ttu-id="c1b40-128">Popis</span><span class="sxs-lookup"><span data-stu-id="c1b40-128">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c1b40-129">String</span><span class="sxs-lookup"><span data-stu-id="c1b40-129">String</span></span>|<span data-ttu-id="c1b40-130">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c1b40-130">Optional.</span></span> <span data-ttu-id="c1b40-131">Určuje název typu a sestavení a další data použít k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="c1b40-131">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="c1b40-132">Minimálně název oboru názvů a typ jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="c1b40-132">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="c1b40-133">Volitelné informace zahrnují: název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="c1b40-133">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="c1b40-134">certificateValidationMode atribut</span><span class="sxs-lookup"><span data-stu-id="c1b40-134">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="c1b40-135">Hodnota</span><span class="sxs-lookup"><span data-stu-id="c1b40-135">Value</span></span>|<span data-ttu-id="c1b40-136">Popis</span><span class="sxs-lookup"><span data-stu-id="c1b40-136">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c1b40-137">Výčet</span><span class="sxs-lookup"><span data-stu-id="c1b40-137">Enumeration</span></span>|<span data-ttu-id="c1b40-138">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="c1b40-138">Optional.</span></span> <span data-ttu-id="c1b40-139">Jeden z následujících hodnot: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="c1b40-139">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="c1b40-140">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="c1b40-140">The default is `ChainTrust`.</span></span> <span data-ttu-id="c1b40-141">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="c1b40-141">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="c1b40-142">Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="c1b40-142">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="c1b40-143">revocationMode atribut</span><span class="sxs-lookup"><span data-stu-id="c1b40-143">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="c1b40-144">Value</span><span class="sxs-lookup"><span data-stu-id="c1b40-144">Value</span></span>|<span data-ttu-id="c1b40-145">Popis</span><span class="sxs-lookup"><span data-stu-id="c1b40-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c1b40-146">Výčet</span><span class="sxs-lookup"><span data-stu-id="c1b40-146">Enumeration</span></span>|<span data-ttu-id="c1b40-147">Jeden z následujících hodnot: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="c1b40-147">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="c1b40-148">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="c1b40-148">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="c1b40-149">Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="c1b40-149">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="c1b40-150">trustedStoreLocation atribut</span><span class="sxs-lookup"><span data-stu-id="c1b40-150">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="c1b40-151">Value</span><span class="sxs-lookup"><span data-stu-id="c1b40-151">Value</span></span>|<span data-ttu-id="c1b40-152">Popis</span><span class="sxs-lookup"><span data-stu-id="c1b40-152">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="c1b40-153">Výčet</span><span class="sxs-lookup"><span data-stu-id="c1b40-153">Enumeration</span></span>|<span data-ttu-id="c1b40-154">Jeden z následujících hodnot: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="c1b40-154">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="c1b40-155">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="c1b40-155">The default is `CurrentUser`.</span></span> <span data-ttu-id="c1b40-156">Pokud klientská aplikace běží pod účtem systému, certifikátu je obvykle pod `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="c1b40-156">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="c1b40-157">Pokud klientská aplikace běží pod účtem uživatele, že certifikát je obvykle v `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="c1b40-157">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="c1b40-158">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="c1b40-158">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c1b40-159">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="c1b40-159">Child Elements</span></span>  
 <span data-ttu-id="c1b40-160">Žádné</span><span class="sxs-lookup"><span data-stu-id="c1b40-160">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c1b40-161">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="c1b40-161">Parent Elements</span></span>  
  
|<span data-ttu-id="c1b40-162">Prvek</span><span class="sxs-lookup"><span data-stu-id="c1b40-162">Element</span></span>|<span data-ttu-id="c1b40-163">Popis</span><span class="sxs-lookup"><span data-stu-id="c1b40-163">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1b40-164">\<peer></span><span class="sxs-lookup"><span data-stu-id="c1b40-164">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="c1b40-165">Určuje pověření pro ověření klienta ke službě partnera.</span><span class="sxs-lookup"><span data-stu-id="c1b40-165">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c1b40-166">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c1b40-166">Remarks</span></span>  
 <span data-ttu-id="c1b40-167">Tento element musí být nakonfigurované, pokud je zvoleno ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="c1b40-167">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="c1b40-168">Pro výstup kanály, každá zpráva je podepsaná pomocí certifikátu poskytnutého [ \<certifikátu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="c1b40-168">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="c1b40-169">Všechny zprávy, předtím, než se doručí do aplikace, jsou porovnávána s přihlašovacími údaji zprávy pomocí validátor určené `customCertificateValidatorType` atribut tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="c1b40-169">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="c1b40-170">Validátor můžete přijmout nebo odmítnout přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="c1b40-170">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c1b40-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="c1b40-171">Example</span></span>  
 <span data-ttu-id="c1b40-172">Následující kód nastaví režim ověřování zpráv odesílatele `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="c1b40-172">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="MyEndpointBehavior">
      <clientCredentials>
        <peer>
          <certificate findValue="www.contoso.com"
                       storeLocation="LocalMachine"
                       x509FindType="FindByIssuerName" />
          <messageSenderAuthentication certificateValidationMode="PeerOrChainTrust" />
          <messageSenderAuthentication certificateValidationMode="None" />
        </peer>
      </clientCredentials>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="see-also"></a><span data-ttu-id="c1b40-173">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c1b40-173">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="c1b40-174">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="c1b40-174">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="c1b40-175">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="c1b40-175">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="c1b40-176">[Ověřování zpráv protokolu peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c1b40-176">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="c1b40-177">[Vlastní ověřování protokolu peer Channel](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="c1b40-177">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="c1b40-178">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="c1b40-178">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
