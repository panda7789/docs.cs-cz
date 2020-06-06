---
title: <messageSenderAuthentication> – element
ms.date: 03/30/2017
ms.assetid: 8d979dfc-a6f9-42ec-96d5-7fbc13a48118
ms.openlocfilehash: bab0e50d7feba3ea55d505be07cfa41427a5cbbc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70397779"
---
# <a name="messagesenderauthentication-element"></a><span data-ttu-id="d3e36-102">\<messageSenderAuthentication> – element</span><span class="sxs-lookup"><span data-stu-id="d3e36-102">\<messageSenderAuthentication> element</span></span>
<span data-ttu-id="d3e36-103">Určuje možnosti ověřování pro odesílatele zpráv peer-to-peer.</span><span class="sxs-lookup"><span data-stu-id="d3e36-103">Specifies authentication options for peer-to-peer message senders.</span></span>  
  
 <span data-ttu-id="d3e36-104">Další informace o programování peer-to-peer najdete v tématu [sítě peer-to-peer](../../../wcf/feature-details/peer-to-peer-networking.md).</span><span class="sxs-lookup"><span data-stu-id="d3e36-104">For more information about peer-to-peer programming, see [Peer-to-Peer Networking](../../../wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<clientCredentials>**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<peer>**](peer-of-clientcredentials-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<messageSenderAuthentication>**  
  
## <a name="syntax"></a><span data-ttu-id="d3e36-105">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d3e36-105">Syntax</span></span>  
  
```xml  
<messageSenderAuthentication customCertificateValidatorType= "namespace.typeName, [,AssemblyName] [,Version=version number] [,Culture=culture] [,PublicKeyToken=token]"
                             certificateValidationMode = "ChainTrust/None/PeerTrust/PeerOrChainTrust/Custom"
                             revocationMode="NoCheck/Online/Offline"
                             trustedStoreLocation="CurrentUser/LocalMachine" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d3e36-106">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="d3e36-106">Attributes and Elements</span></span>  
 <span data-ttu-id="d3e36-107">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="d3e36-107">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d3e36-108">Atributy</span><span class="sxs-lookup"><span data-stu-id="d3e36-108">Attributes</span></span>  
  
|<span data-ttu-id="d3e36-109">Atribut</span><span class="sxs-lookup"><span data-stu-id="d3e36-109">Attribute</span></span>|<span data-ttu-id="d3e36-110">Popis</span><span class="sxs-lookup"><span data-stu-id="d3e36-110">Description</span></span>|  
|---------------|-----------------|  
|`customCertificateValidatorType`|<span data-ttu-id="d3e36-111">Typ a sestavení, které slouží k ověření vlastního typu.</span><span class="sxs-lookup"><span data-stu-id="d3e36-111">A type and assembly used to validate a custom type.</span></span> <span data-ttu-id="d3e36-112">Tento atribut musí být nastaven `certificateValidationMode` , je-li nastavena na hodnotu `Custom` .</span><span class="sxs-lookup"><span data-stu-id="d3e36-112">This attribute must be set when `certificateValidationMode` is set to `Custom`.</span></span>|  
|`certificateValidationMode`|<span data-ttu-id="d3e36-113">Určuje jeden ze tří režimů, který se používá k ověření přihlašovacích údajů.</span><span class="sxs-lookup"><span data-stu-id="d3e36-113">Specifies one of three modes used to validate credentials.</span></span> <span data-ttu-id="d3e36-114">Je-li nastaveno na hodnotu `Custom` , `customCertificateValidator` musí být zadána také.</span><span class="sxs-lookup"><span data-stu-id="d3e36-114">If set to `Custom`, then a `customCertificateValidator` must also be supplied.</span></span>|  
|`revocationMode`|<span data-ttu-id="d3e36-115">Jeden z režimů, který slouží ke kontrole seznamů odvolaných certifikátů (CRL).</span><span class="sxs-lookup"><span data-stu-id="d3e36-115">One of the modes used to check for a revoked certificate lists (CRL).</span></span>|  
|`trustedStoreLocation`|<span data-ttu-id="d3e36-116">Jedno ze dvou umístění úložiště systému: `LocalMachine` nebo `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="d3e36-116">One of the two system store locations: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="d3e36-117">Tato hodnota se používá, když je certifikát služby vyjednán klientovi.</span><span class="sxs-lookup"><span data-stu-id="d3e36-117">This value is used when a service certificate is negotiated to the client.</span></span> <span data-ttu-id="d3e36-118">Ověřování se provádí pro úložiště **důvěryhodných osob** v zadaném umístění úložiště.</span><span class="sxs-lookup"><span data-stu-id="d3e36-118">Validation is performed against the **Trusted People** store in the specified store location.</span></span>|  
  
## <a name="customcertificatevalidatortype-attribute"></a><span data-ttu-id="d3e36-119">customCertificateValidatorType – atribut</span><span class="sxs-lookup"><span data-stu-id="d3e36-119">customCertificateValidatorType Attribute</span></span>  
  
|<span data-ttu-id="d3e36-120">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d3e36-120">Value</span></span>|<span data-ttu-id="d3e36-121">Description</span><span class="sxs-lookup"><span data-stu-id="d3e36-121">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d3e36-122">Řetězec</span><span class="sxs-lookup"><span data-stu-id="d3e36-122">String</span></span>|<span data-ttu-id="d3e36-123">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="d3e36-123">Optional.</span></span> <span data-ttu-id="d3e36-124">Určuje název typu a sestavení a další data, která se používají k vyhledání typu.</span><span class="sxs-lookup"><span data-stu-id="d3e36-124">Specifies the type name and assembly and other data used to find the type.</span></span> <span data-ttu-id="d3e36-125">Je vyžadován minimální obor názvů a název typu.</span><span class="sxs-lookup"><span data-stu-id="d3e36-125">At minimum, a namespace and type name are required.</span></span> <span data-ttu-id="d3e36-126">Volitelné informace zahrnují: název sestavení, číslo verze, jazykovou verzi a token veřejného klíče.</span><span class="sxs-lookup"><span data-stu-id="d3e36-126">Optional information includes: assembly name, version number, culture, and public key token.</span></span>|  
  
## <a name="certificatevalidationmode-attribute"></a><span data-ttu-id="d3e36-127">certificateValidationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="d3e36-127">certificateValidationMode Attribute</span></span>  
  
|<span data-ttu-id="d3e36-128">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d3e36-128">Value</span></span>|<span data-ttu-id="d3e36-129">Description</span><span class="sxs-lookup"><span data-stu-id="d3e36-129">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d3e36-130">Výčet</span><span class="sxs-lookup"><span data-stu-id="d3e36-130">Enumeration</span></span>|<span data-ttu-id="d3e36-131">Nepovinný parametr.</span><span class="sxs-lookup"><span data-stu-id="d3e36-131">Optional.</span></span> <span data-ttu-id="d3e36-132">Jedna z následujících hodnot: `None` , `PeerTrust` , `ChainTrust` , `PeerOrChainTrust` , `Custom` .</span><span class="sxs-lookup"><span data-stu-id="d3e36-132">One of the following values: `None`, `PeerTrust`, `ChainTrust`, `PeerOrChainTrust`, `Custom`.</span></span> <span data-ttu-id="d3e36-133">Výchozí formát je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="d3e36-133">The default is `ChainTrust`.</span></span> <span data-ttu-id="d3e36-134">Výchozí formát je `ChainTrust`.</span><span class="sxs-lookup"><span data-stu-id="d3e36-134">The default is `ChainTrust`.</span></span><br /><br /> <span data-ttu-id="d3e36-135">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="d3e36-135">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="revocationmode-attribute"></a><span data-ttu-id="d3e36-136">revocationMode – atribut</span><span class="sxs-lookup"><span data-stu-id="d3e36-136">revocationMode Attribute</span></span>  
  
|<span data-ttu-id="d3e36-137">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d3e36-137">Value</span></span>|<span data-ttu-id="d3e36-138">Description</span><span class="sxs-lookup"><span data-stu-id="d3e36-138">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d3e36-139">Výčet</span><span class="sxs-lookup"><span data-stu-id="d3e36-139">Enumeration</span></span>|<span data-ttu-id="d3e36-140">Jedna z následujících hodnot: `NoCheck` , `Online` , `Offline` .</span><span class="sxs-lookup"><span data-stu-id="d3e36-140">One of the following values: `NoCheck`, `Online`, `Offline`.</span></span> <span data-ttu-id="d3e36-141">Výchozí formát je `Online`.</span><span class="sxs-lookup"><span data-stu-id="d3e36-141">The default is `Online`.</span></span><br /><br /> <span data-ttu-id="d3e36-142">Další informace najdete v tématu [práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md).</span><span class="sxs-lookup"><span data-stu-id="d3e36-142">For more information, see [Working with Certificates](../../../wcf/feature-details/working-with-certificates.md).</span></span>|  
  
## <a name="trustedstorelocation-attribute"></a><span data-ttu-id="d3e36-143">trustedStoreLocation – atribut</span><span class="sxs-lookup"><span data-stu-id="d3e36-143">trustedStoreLocation Attribute</span></span>  
  
|<span data-ttu-id="d3e36-144">Hodnota</span><span class="sxs-lookup"><span data-stu-id="d3e36-144">Value</span></span>|<span data-ttu-id="d3e36-145">Description</span><span class="sxs-lookup"><span data-stu-id="d3e36-145">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d3e36-146">Výčet</span><span class="sxs-lookup"><span data-stu-id="d3e36-146">Enumeration</span></span>|<span data-ttu-id="d3e36-147">Jedna z následujících hodnot: `LocalMachine` nebo `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="d3e36-147">One of the following values: `LocalMachine` or `CurrentUser`.</span></span> <span data-ttu-id="d3e36-148">Výchozí formát je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="d3e36-148">The default is `CurrentUser`.</span></span> <span data-ttu-id="d3e36-149">Pokud klientská aplikace běží pod účtem systému, certifikát se obvykle nachází v části `LocalMachine` .</span><span class="sxs-lookup"><span data-stu-id="d3e36-149">If the client application is running under a system account then the certificate is typically under `LocalMachine`.</span></span> <span data-ttu-id="d3e36-150">Pokud klientská aplikace běží pod uživatelským účtem, bude certifikát typicky v `CurrentUser` .</span><span class="sxs-lookup"><span data-stu-id="d3e36-150">If the client application is running under a user account then the certificate is typically in `CurrentUser`.</span></span> <span data-ttu-id="d3e36-151">Výchozí formát je `CurrentUser`.</span><span class="sxs-lookup"><span data-stu-id="d3e36-151">The default is `CurrentUser`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d3e36-152">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="d3e36-152">Child Elements</span></span>  
 <span data-ttu-id="d3e36-153">Žádné</span><span class="sxs-lookup"><span data-stu-id="d3e36-153">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d3e36-154">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="d3e36-154">Parent Elements</span></span>  
  
|<span data-ttu-id="d3e36-155">Prvek</span><span class="sxs-lookup"><span data-stu-id="d3e36-155">Element</span></span>|<span data-ttu-id="d3e36-156">Description</span><span class="sxs-lookup"><span data-stu-id="d3e36-156">Description</span></span>|  
|-------------|-----------------|  
|[\<peer>](peer-of-clientcredentials-element.md)|<span data-ttu-id="d3e36-157">Určuje přihlašovací údaje, které se používají k ověřování klienta pro partnerských služeb.</span><span class="sxs-lookup"><span data-stu-id="d3e36-157">Specifies a credential used for authenticating the client to a peer service.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3e36-158">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d3e36-158">Remarks</span></span>  
 <span data-ttu-id="d3e36-159">Tento prvek musí být nakonfigurován, pokud je zvoleno ověřování zpráv.</span><span class="sxs-lookup"><span data-stu-id="d3e36-159">This element must be configured if message authentication is chosen.</span></span> <span data-ttu-id="d3e36-160">U výstupních kanálů se každá zpráva podepisuje pomocí certifikátu, který poskytuje [\<certificate>](certificate-element.md) .</span><span class="sxs-lookup"><span data-stu-id="d3e36-160">For output channels, each message is signed using the certificate provided by [\<certificate>](certificate-element.md).</span></span> <span data-ttu-id="d3e36-161">Všechny zprávy před doručením do aplikace jsou zkontrolovány proti pověření zprávy pomocí validátoru určeného `customCertificateValidatorType` atributem tohoto prvku.</span><span class="sxs-lookup"><span data-stu-id="d3e36-161">All messages, before delivered to the application, are checked against the message credential using the validator specified by the `customCertificateValidatorType` attribute of this element.</span></span> <span data-ttu-id="d3e36-162">Validátor může buď přijmout nebo odmítnout přihlašovací údaje.</span><span class="sxs-lookup"><span data-stu-id="d3e36-162">The validator can either accept or reject the credential.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d3e36-163">Příklad</span><span class="sxs-lookup"><span data-stu-id="d3e36-163">Example</span></span>  
 <span data-ttu-id="d3e36-164">Následující kód nastaví režim ověřování odesílatele zprávy na `PeerOrChainTrust` .</span><span class="sxs-lookup"><span data-stu-id="d3e36-164">The following code sets the message sender validation mode to `PeerOrChainTrust`.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="d3e36-165">Viz také</span><span class="sxs-lookup"><span data-stu-id="d3e36-165">See also</span></span>

- <xref:System.ServiceModel.Security.X509PeerCertificateAuthentication>
- <xref:System.ServiceModel.Security.PeerCredential.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.PeerCredentialElement.MessageSenderAuthentication%2A>
- <xref:System.ServiceModel.Configuration.X509PeerCertificateAuthenticationElement>
- [<span data-ttu-id="d3e36-166">Práce s certifikáty</span><span class="sxs-lookup"><span data-stu-id="d3e36-166">Working with Certificates</span></span>](../../../wcf/feature-details/working-with-certificates.md)
- [<span data-ttu-id="d3e36-167">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="d3e36-167">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
- <span data-ttu-id="d3e36-168">[Ověřování zpráv rovnocenného kanálu](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d3e36-168">[Peer Channel Message Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/aa967730(v=vs.90))</span></span>
- <span data-ttu-id="d3e36-169">[Vlastní ověřování rovnocenných kanálů](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d3e36-169">[Peer Channel Custom Authentication](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751447(v=vs.90))</span></span>
- [<span data-ttu-id="d3e36-170">Zabezpečení aplikací rovnocenného kanálu</span><span class="sxs-lookup"><span data-stu-id="d3e36-170">Securing Peer Channel Applications</span></span>](../../../wcf/feature-details/securing-peer-channel-applications.md)
