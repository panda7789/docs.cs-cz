---
title: Element &lt;messageSenderAuthentication&gt;
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: cb727df7b8d7605cbe984a8f6737c89bf1bfb2be
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43891622"
---
# <a name="ltmessagesenderauthenticationgt-element"></a><span data-ttu-id="2c567-102">Element &lt;messageSenderAuthentication&gt;</span><span class="sxs-lookup"><span data-stu-id="2c567-102">&lt;messageSenderAuthentication&gt; element</span></span>
<span data-ttu-id="2c567-103">Určuje možnosti ověřování pro odesílatele zpráv peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="2c567-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="2c567-104">Další informace o programování peer-to-peer, naleznete v tématu [sítě Peer-to-Peer](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="2c567-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
 <span data-ttu-id="2c567-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2c567-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="2c567-106">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2c567-106">\<behaviors></span></span>  
<span data-ttu-id="2c567-107">\<názvy endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="2c567-107">\<endpointBehaviors></span></span>  
<span data-ttu-id="2c567-108">\<chování ></span><span class="sxs-lookup"><span data-stu-id="2c567-108">\<behavior></span></span>  
<span data-ttu-id="2c567-109">\<třídu clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="2c567-109">\<clientCredentials></span></span>  
<span data-ttu-id="2c567-110">\<sdílená ></span><span class="sxs-lookup"><span data-stu-id="2c567-110">\<peer></span></span>  
<span data-ttu-id="2c567-111">\<messageSenderAuthentication ></span><span class="sxs-lookup"><span data-stu-id="2c567-111">\<messageSenderAuthentication></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2c567-112">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="2c567-112">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication  
customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"  
certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"  
revocationMode="NoCheck/Online/Offline"  
trustedStoreLocation="CurrentUser/LocalMachine"   
/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2c567-113">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="2c567-113">Attributes and Elements</span></span>  
 <span data-ttu-id="2c567-114">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2c567-114">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2c567-115">Atributy</span><span class="sxs-lookup"><span data-stu-id="2c567-115">Attributes</span></span>  
  
|<span data-ttu-id="2c567-116">Atribut</span><span class="sxs-lookup"><span data-stu-id="2c567-116">Attribute</span></span>|<span data-ttu-id="2c567-117">Popis</span><span class="sxs-lookup"><span data-stu-id="2c567-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2c567-118">customCertificateValidatorType</span><span class="sxs-lookup"><span data-stu-id="2c567-118">customCertificateValidatorType</span></span>|<span data-ttu-id="2c567-119">Typ a sestavení používané pro ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="2c567-119">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="2c567-120">Tento atribut musí být nastaven při `certificateValidationMode` je nastavena na `Custom`.</span><span class="sxs-lookup"><span data-stu-id="2c567-120">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|<span data-ttu-id="2c567-121">certifcateValidationMode</span><span class="sxs-lookup"><span data-stu-id="2c567-121">certifcateValidationMode</span></span>|<span data-ttu-id="2c567-122">Určuje jeden ze tří režimů používaných pro ověření pověření.</span><span class="sxs-lookup"><span data-stu-id="2c567-122">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="2c567-123">Pokud hodnotu `Custom`, o `customCertificateValidator` musí být rovněž dodán.</span><span class="sxs-lookup"><span data-stu-id="2c567-123">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|<span data-ttu-id="2c567-124">revocationMode</span><span class="sxs-lookup"><span data-stu-id="2c567-124">revocationMode</span></span>|<span data-ttu-id="2c567-125">Jeden z režimů pro kontrolu seznamu odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="2c567-125">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|<span data-ttu-id="2c567-126">trustedStoreLocation</span><span class="sxs-lookup"><span data-stu-id="2c567-126">trustedStoreLocation</span></span>|<span data-ttu-id="2c567-127">Jeden z umístění dvou systémových úložišť: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2c567-127">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="2c567-128">Tato hodnota se používá při certifikát služby se vyjedná do klienta.</span><span class="sxs-lookup"><span data-stu-id="2c567-128">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="2c567-129">Ověření se provádí proti **důvěryhodné osoby** uložit do umístění určeného úložiště.</span><span class="sxs-lookup"><span data-stu-id="2c567-129">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="2c567-130">customCertificateValidatorType atribut</span><span class="sxs-lookup"><span data-stu-id="2c567-130">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="2c567-131">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2c567-131">Value</span></span>|<span data-ttu-id="2c567-132">Popis</span><span class="sxs-lookup"><span data-stu-id="2c567-132">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2c567-133">String</span><span class="sxs-lookup"><span data-stu-id="2c567-133">String</span></span>|<span data-ttu-id="2c567-134">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2c567-134">Optional.</span></span> <span data-ttu-id="2c567-135">Určuje název typu a sestavení a další data použít k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="2c567-135">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="2c567-136">Minimálně název oboru názvů a typ jsou požadovány.</span><span class="sxs-lookup"><span data-stu-id="2c567-136">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="2c567-137">Volitelné informace zahrnují: název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="2c567-137">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="2c567-138">certificateValidationMode atribut</span><span class="sxs-lookup"><span data-stu-id="2c567-138">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="2c567-139">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2c567-139">Value</span></span>|<span data-ttu-id="2c567-140">Popis</span><span class="sxs-lookup"><span data-stu-id="2c567-140">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2c567-141">Výčet</span><span class="sxs-lookup"><span data-stu-id="2c567-141">Enumeration</span></span>|<span data-ttu-id="2c567-142">Volitelné.</span><span class="sxs-lookup"><span data-stu-id="2c567-142">Optional.</span></span> <span data-ttu-id="2c567-143">Jeden z následujících hodnot: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span><span class="sxs-lookup"><span data-stu-id="2c567-143">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="2c567-144">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="2c567-144">The default is `ChainTrust`.</span></span> <span data-ttu-id="2c567-145">Výchozí hodnota je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="2c567-145">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="2c567-146">Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2c567-146">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="2c567-147">revocationMode atribut</span><span class="sxs-lookup"><span data-stu-id="2c567-147">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="2c567-148">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2c567-148">Value</span></span>|<span data-ttu-id="2c567-149">Popis</span><span class="sxs-lookup"><span data-stu-id="2c567-149">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2c567-150">Výčet</span><span class="sxs-lookup"><span data-stu-id="2c567-150">Enumeration</span></span>|<span data-ttu-id="2c567-151">Jeden z následujících hodnot: `NoCheck`, `Online`, `Offline`.</span><span class="sxs-lookup"><span data-stu-id="2c567-151">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="2c567-152">Výchozí hodnota je `Online`.</span><span class="sxs-lookup"><span data-stu-id="2c567-152">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="2c567-153">Další informace najdete v tématu [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="2c567-153">For more information, see [Working with Certificates](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="2c567-154">trustedStoreLocation atribut</span><span class="sxs-lookup"><span data-stu-id="2c567-154">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="2c567-155">Hodnota</span><span class="sxs-lookup"><span data-stu-id="2c567-155">Value</span></span>|<span data-ttu-id="2c567-156">Popis</span><span class="sxs-lookup"><span data-stu-id="2c567-156">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="2c567-157">Výčet</span><span class="sxs-lookup"><span data-stu-id="2c567-157">Enumeration</span></span>|<span data-ttu-id="2c567-158">Jeden z následujících hodnot: `LocalMachine` nebo `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2c567-158">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="2c567-159">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2c567-159">The default is `CurrentUser`.</span></span> <span data-ttu-id="2c567-160">Pokud klientská aplikace běží pod účtem systému, certifikátu je obvykle pod `LocalMachine`.</span><span class="sxs-lookup"><span data-stu-id="2c567-160">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="2c567-161">Pokud klientská aplikace běží pod účtem uživatele, že certifikát je obvykle v `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2c567-161">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="2c567-162">Výchozí hodnota je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="2c567-162">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2c567-163">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="2c567-163">Child Elements</span></span>  
 <span data-ttu-id="2c567-164">Žádné</span><span class="sxs-lookup"><span data-stu-id="2c567-164">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2c567-165">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="2c567-165">Parent Elements</span></span>  
  
|<span data-ttu-id="2c567-166">Prvek</span><span class="sxs-lookup"><span data-stu-id="2c567-166">Element</span></span>|<span data-ttu-id="2c567-167">Popis</span><span class="sxs-lookup"><span data-stu-id="2c567-167">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2c567-168">\<peer></span><span class="sxs-lookup"><span data-stu-id="2c567-168">\<peer></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/peer-of-clientcredentials-element.md)|<span data-ttu-id="2c567-169">Určuje pověření pro ověření klienta ke službě partnera.</span><span class="sxs-lookup"><span data-stu-id="2c567-169">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2c567-170">Poznámky</span><span class="sxs-lookup"><span data-stu-id="2c567-170">Remarks</span></span>  
 <span data-ttu-id="2c567-171">Tento element musí být nakonfigurované, pokud je zvoleno ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="2c567-171">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="2c567-172">Pro výstup kanály, každá zpráva je podepsaná pomocí certifikátu poskytnutého [ \<certifikátu >](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span><span class="sxs-lookup"><span data-stu-id="2c567-172">For output channels, each message is signed using the certificate provided by [\<certificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/certificate-element.md).</span></span> <span data-ttu-id="2c567-173">Všechny zprávy, předtím, než se doručí do aplikace, jsou porovnávána s přihlašovacími údaji zprávy pomocí validátor určené `customCertificateValidatorType` atribut tohoto elementu.</span><span class="sxs-lookup"><span data-stu-id="2c567-173">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="2c567-174">Validátor můžete přijmout nebo odmítnout přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="2c567-174">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2c567-175">Příklad</span><span class="sxs-lookup"><span data-stu-id="2c567-175">Example</span></span>  
 <span data-ttu-id="2c567-176">Následující kód nastaví režim ověřování zpráv odesílatele `PeerOrChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="2c567-176">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
```xml  
<behaviors>  
 <endpointBehaviors>  
  <behavior name="MyEndpointBehavior">  
   <clientCredentials>  
    <peer>  
      <certificate findValue="www.contoso.com"   
                   storeLocation="LocalMachine"  
                   x509FindType="FindByIssuerName" />  
        <messageSenderAuthentication   
          certificateValidationMode="PeerOrChainTrust" />  
       <messageSenderAuthentication certificateValidationMode="None" />  
    </peer>  
   </clientCredentials>  
  </behavior>  
 </endpointBehaviors>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2c567-177">Viz také</span><span class="sxs-lookup"><span data-stu-id="2c567-177">See Also</span></span>  
 <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>  
 <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>  
 <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>  
 [<span data-ttu-id="2c567-178">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="2c567-178">Working with Certificates</span></span>](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [<span data-ttu-id="2c567-179">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="2c567-179">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)  
 [<span data-ttu-id="2c567-180">Ověřování zpráv protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="2c567-180">Peer Channel Message Authentication</span></span>](https://msdn.microsoft.com/library/80e73386-514e-4c30-9e4a-b9ca8c173a95)  
 [<span data-ttu-id="2c567-181">Vlastní ověřování protokolu peer Channel</span><span class="sxs-lookup"><span data-stu-id="2c567-181">Peer Channel Custom Authentication</span></span>](https://msdn.microsoft.com/library/4aa8a82e-41a8-48e2-8621-7e1cbabdca7c)  
 [<span data-ttu-id="2c567-182">Zabezpečení aplikací protokolu Peer Channel</span><span class="sxs-lookup"><span data-stu-id="2c567-182">Securing Peer Channel Applications</span></span>](../../../../../docs/framework/wcf/feature-details/securing-peer-channel-applications.md)
