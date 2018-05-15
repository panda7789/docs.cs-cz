---
title: '&lt;wsFederationHttpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- wsFederationBinding element
ms.assetid: 9c3312b4-2137-4e71-bf3f-de1cf8e9be79
ms.openlocfilehash: d89d0aeb68aed91b28ca7358a6140e171d3b36b2
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltwsfederationhttpbindinggt"></a><span data-ttu-id="62195-102">&lt;wsFederationHttpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="62195-102">&lt;wsFederationHttpBinding&gt;</span></span>
<span data-ttu-id="62195-103">Definuje vazbu, která podporuje WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="62195-103">Defines a binding that supports WS-Federation.</span></span>  
  
 <span data-ttu-id="62195-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="62195-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="62195-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="62195-105">\<bindings></span></span>  
<span data-ttu-id="62195-106">wsFederationBinding – element</span><span class="sxs-lookup"><span data-stu-id="62195-106">wsFederationBinding element</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62195-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62195-107">Syntax</span></span>  
  
```xml  
<wsFederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="Boolean"  
        closeTimeout="TimeSpan"   
        hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
        maxBufferPoolSize="integer"  
        maxReceivedMessageSize="integer"  
        messageEncoding="Text/Mtom"   
                name="string"  
        openTimeout="TimeSpan"   
        privacyNoticeAt="Uri"  
        privacyNoticeVersion="Integer"  
        proxyAddress="Uri"   
        receiveTimeout="TimeSpan"  
        sendTimeout="TimeSpan"  
        textEncoding="UnicodeFffeTextEncoding/Utf16TextEncoding/ Utf8TextEncoding"  
        transactionFlow="Boolean"  
        useDefaultWebProxy="Boolean">  
        <security mode="None/Message/TransportWithMessageCredential">  
         <message   
            algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
            issuedTokenType="string"   
            issuedKeyType="SymmetricKey/PublicKey"  
            negotiateServiceCredential="Boolean" >  
            <claimTypeRequirements>  
               <add claimType="URI"  
                    isOptional="Boolean" />  
            </claimTypeRequirements>  
                        <issuer address="Uri" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
                          </headers>  
                              <identity>  
                                 <certificate encodedValue="String"/>  
                                <certificateReference findValue="String"   
                                 isChainIncluded="Boolean"  
                            storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                                  storeLocation="LocalMachine/CurrentUser"  
                                   X509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                                   <dns value="String"/>  
                                <rsa value="String"/>  
                                <servicePrincipalName value="String"/>  
                                <usePrincipalName value="String"/>  
                              </identity>  
                        </issuer>  
                        <issuerMetadata address=String" >  
               <headers>  
                  <add name="String"  
                       namespace="String" />  
               </headers>  
               <identity>  
                  <certificate encodedValue="String"/>  
                  <certificateReference findValue="String"   
                     isChainIncluded="Boolean"  
                     storeName="AddressBook/AuthRoot/CertificateAuthority/Disallowed/My/Root/TrustedPeople/TrustedPublisher"  
                     storeLocation="LocalMachine/CurrentUser"  
                     x509FindType=System.Security.Cryptography.X509certificates.X509findtype/>  
                  <dns value="String"/>  
                  <rsa value="String"/>  
                  <servicePrincipalName value="String"/>  
                  <usePrincipalName value="String"/>  
               </identity>  
                        </issuerMetadata>  
            <tokenRequestParameters>  
               <xmlElement>  
               </xmlElement>  
            </tokenRequestParameters>  
           </message>  
        </security>  
        <reliableSession ordered="Boolean"  
           inactivityTimeout="TimeSpan"  
           enabled="Boolean" />  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />    </binding>  
</wsFederationBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62195-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="62195-108">Attributes and Elements</span></span>  
 <span data-ttu-id="62195-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="62195-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62195-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="62195-110">Attributes</span></span>  
  
|<span data-ttu-id="62195-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="62195-111">Attribute</span></span>|<span data-ttu-id="62195-112">Popis</span><span class="sxs-lookup"><span data-stu-id="62195-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62195-113">bypassProxyOnLocal</span><span class="sxs-lookup"><span data-stu-id="62195-113">bypassProxyOnLocal</span></span>|<span data-ttu-id="62195-114">Logická hodnota, která označuje, zda Nepoužívat proxy server pro místní adresy.</span><span class="sxs-lookup"><span data-stu-id="62195-114">A Boolean value that indicates whether to bypass the proxy server for local addresses.</span></span> <span data-ttu-id="62195-115">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="62195-115">The default is `false`.</span></span>|  
|<span data-ttu-id="62195-116">Intervalu</span><span class="sxs-lookup"><span data-stu-id="62195-116">closeTimeout</span></span>|<span data-ttu-id="62195-117">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="62195-117">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="62195-118">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="62195-118">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="62195-119">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="62195-119">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="62195-120">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="62195-120">hostnameComparisonMode</span></span>|<span data-ttu-id="62195-121">Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="62195-121">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="62195-122">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="62195-122">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="62195-123">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, který ignoruje název hostitele se shodují.</span><span class="sxs-lookup"><span data-stu-id="62195-123">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="62195-124">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="62195-124">maxBufferPoolSize</span></span>|<span data-ttu-id="62195-125">Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="62195-125">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="62195-126">Výchozí hodnota je 524,288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="62195-126">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="62195-127">Mnoho části služby Windows Communication Foundation (WCF) pomocí vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="62195-127">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="62195-128">Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="62195-128">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="62195-129">S fondy vyrovnávací paměti můžete provést vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu.</span><span class="sxs-lookup"><span data-stu-id="62195-129">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="62195-130">Proto je předejde režijní náklady v vytváření a zničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="62195-130">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="62195-131">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="62195-131">maxReceivedMessageSize</span></span>|<span data-ttu-id="62195-132">Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně hlavičky, které můžou přijímat na kanál nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="62195-132">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="62195-133">Odesílatel zprávy překročení tohoto limitu obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="62195-133">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="62195-134">Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="62195-134">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="62195-135">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="62195-135">The default is 65536.</span></span>|  
|<span data-ttu-id="62195-136">messageEncoding</span><span class="sxs-lookup"><span data-stu-id="62195-136">messageEncoding</span></span>|<span data-ttu-id="62195-137">Definuje kodér použitá ke kódování zprávy.</span><span class="sxs-lookup"><span data-stu-id="62195-137">Defines the encoder used to encode the message.</span></span> <span data-ttu-id="62195-138">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="62195-138">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="62195-139">-Text: Pomocí kodéru text zprávy.</span><span class="sxs-lookup"><span data-stu-id="62195-139">-   Text: Use a text message encoder.</span></span><br /><span data-ttu-id="62195-140">-Mtom: Pomocí kodéru zpráv přenosu organizace mechanismus 1.0 (MTOM).</span><span class="sxs-lookup"><span data-stu-id="62195-140">-   Mtom: Use a Message Transmission Organization Mechanism 1.0 (MTOM) encoder.</span></span><br /><br /> <span data-ttu-id="62195-141">Výchozí hodnota je Text.</span><span class="sxs-lookup"><span data-stu-id="62195-141">The default is Text.</span></span><br /><br /> <span data-ttu-id="62195-142">Tento atribut je typu <xref:System.ServiceModel.WSMessageEncoding>.</span><span class="sxs-lookup"><span data-stu-id="62195-142">This attribute is of type <xref:System.ServiceModel.WSMessageEncoding>.</span></span>|  
|<span data-ttu-id="62195-143">name</span><span class="sxs-lookup"><span data-stu-id="62195-143">name</span></span>|<span data-ttu-id="62195-144">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="62195-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="62195-145">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="62195-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="62195-146">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="62195-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="62195-147">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="62195-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="62195-148">openTimeout</span><span class="sxs-lookup"><span data-stu-id="62195-148">openTimeout</span></span>|<span data-ttu-id="62195-149">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="62195-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="62195-150">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="62195-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="62195-151">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="62195-151">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="62195-152">privactyNoticeAt</span><span class="sxs-lookup"><span data-stu-id="62195-152">privactyNoticeAt</span></span>|<span data-ttu-id="62195-153">Řetězec, který určuje identifikátor URI, ve kterém se nachází v oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="62195-153">A String that specifies a URI at which the privacy notice is located.</span></span>|  
|<span data-ttu-id="62195-154">privactyNoticeVersion</span><span class="sxs-lookup"><span data-stu-id="62195-154">privactyNoticeVersion</span></span>|<span data-ttu-id="62195-155">Celé číslo, které určuje verzi aktuální informace o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="62195-155">An integer that specifies the version of the current privacy notice.</span></span>|  
|<span data-ttu-id="62195-156">proxyAddress</span><span class="sxs-lookup"><span data-stu-id="62195-156">proxyAddress</span></span>|<span data-ttu-id="62195-157">Identifikátor URI, který určuje adresu proxy serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="62195-157">A URI that specifies the address of the HTTP proxy.</span></span> <span data-ttu-id="62195-158">Pokud `useDefaultWebProxy` je `true`, toto nastavení musí být `null`.</span><span class="sxs-lookup"><span data-stu-id="62195-158">If `useDefaultWebProxy` is `true`, this setting must be `null`.</span></span> <span data-ttu-id="62195-159">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="62195-159">The default is `null`.</span></span>|  
|<span data-ttu-id="62195-160">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="62195-160">receiveTimeout</span></span>|<span data-ttu-id="62195-161">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="62195-161">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="62195-162">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="62195-162">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="62195-163">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="62195-163">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="62195-164">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="62195-164">sendTimeout</span></span>|<span data-ttu-id="62195-165">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="62195-165">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="62195-166">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="62195-166">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="62195-167">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="62195-167">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="62195-168">textEncoding</span><span class="sxs-lookup"><span data-stu-id="62195-168">textEncoding</span></span>|<span data-ttu-id="62195-169">Nastaví znak, nastavení kódování, který se má použít pro vysílání zpráv v vazby.</span><span class="sxs-lookup"><span data-stu-id="62195-169">Sets the character set encoding to be used for emitting messages on the binding.</span></span> <span data-ttu-id="62195-170">Platné hodnoty patří:</span><span class="sxs-lookup"><span data-stu-id="62195-170">Valid values include the following:</span></span><br /><br /> <span data-ttu-id="62195-171">-BigEndianUnicode: Unicode BigEndian kódování.</span><span class="sxs-lookup"><span data-stu-id="62195-171">-   BigEndianUnicode: Unicode BigEndian encoding.</span></span><br /><span data-ttu-id="62195-172">-Unicode: 16bitové kódování.</span><span class="sxs-lookup"><span data-stu-id="62195-172">-   Unicode: 16-bit encoding.</span></span><br /><span data-ttu-id="62195-173">-UTF8: kódování 8bitové</span><span class="sxs-lookup"><span data-stu-id="62195-173">-   UTF8: 8-bit encoding</span></span><br /><br /> <span data-ttu-id="62195-174">Výchozí hodnota je UTF8.</span><span class="sxs-lookup"><span data-stu-id="62195-174">The default is UTF8.</span></span> <span data-ttu-id="62195-175">Tento atribut je typu <xref:System.Text.Encoding>...</span><span class="sxs-lookup"><span data-stu-id="62195-175">This attribute is of type <xref:System.Text.Encoding>..</span></span>|  
|<span data-ttu-id="62195-176">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="62195-176">transactionFlow</span></span>|<span data-ttu-id="62195-177">Logická hodnota, která určuje, zda vazby podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="62195-177">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="62195-178">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="62195-178">The default is `false`.</span></span>|  
|<span data-ttu-id="62195-179">useDefaultWebProxy</span><span class="sxs-lookup"><span data-stu-id="62195-179">useDefaultWebProxy</span></span>|<span data-ttu-id="62195-180">Logická hodnota, která určuje, zda je použít server proxy protokolu HTTP pro automatickou konfiguraci systému.</span><span class="sxs-lookup"><span data-stu-id="62195-180">A Boolean value that indicates whether the system’s auto-configured HTTP proxy is used.</span></span> <span data-ttu-id="62195-181">Adresa proxy serveru musí být `null` (to znamená, že není nastavena) Pokud tento atribut je `true`.</span><span class="sxs-lookup"><span data-stu-id="62195-181">The proxy address must be `null` (that is, not set) if this attribute is `true`.</span></span> <span data-ttu-id="62195-182">Výchozí hodnota je `true`.</span><span class="sxs-lookup"><span data-stu-id="62195-182">The default is `true`.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62195-183">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="62195-183">Child Elements</span></span>  
  
|<span data-ttu-id="62195-184">Prvek</span><span class="sxs-lookup"><span data-stu-id="62195-184">Element</span></span>|<span data-ttu-id="62195-185">Popis</span><span class="sxs-lookup"><span data-stu-id="62195-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62195-186">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="62195-186">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md)|<span data-ttu-id="62195-187">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="62195-187">Defines the security settings for the message.</span></span> <span data-ttu-id="62195-188">Tento element je typu <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="62195-188">This element is of type <xref:System.ServiceModel.Configuration.WSFederationHttpSecurityElement>.</span></span>|  
|[<span data-ttu-id="62195-189">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="62195-189">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="62195-190">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="62195-190">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="62195-191">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="62195-191">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="62195-192">reliableSession</span><span class="sxs-lookup"><span data-stu-id="62195-192">reliableSession</span></span>](http://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="62195-193">Určuje, pokud jsou určeny spolehlivé relace mezi koncovými body kanálu.</span><span class="sxs-lookup"><span data-stu-id="62195-193">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62195-194">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="62195-194">Parent Elements</span></span>  
  
|<span data-ttu-id="62195-195">Prvek</span><span class="sxs-lookup"><span data-stu-id="62195-195">Element</span></span>|<span data-ttu-id="62195-196">Popis</span><span class="sxs-lookup"><span data-stu-id="62195-196">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62195-197">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="62195-197">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="62195-198">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="62195-198">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62195-199">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62195-199">Remarks</span></span>  
 <span data-ttu-id="62195-200">Federace se nachází možnost identity sdílet mezi několika systémy pro ověřování a autorizaci.</span><span class="sxs-lookup"><span data-stu-id="62195-200">Federation is the ability to share identities across multiple systems for authentication and authorization.</span></span> <span data-ttu-id="62195-201">Tyto identity může označovat pro uživatele nebo počítače.</span><span class="sxs-lookup"><span data-stu-id="62195-201">These identities can refer to users or to machines.</span></span> <span data-ttu-id="62195-202">Federované HTTP podporuje zabezpečení protokolu SOAP, jakož i ve smíšeném režimu zabezpečení, ale nepodporuje výhradně pomocí zabezpečení přenosu.</span><span class="sxs-lookup"><span data-stu-id="62195-202">Federated HTTP supports SOAP security as well as mixed-mode security, but it does not support exclusively using transport security.</span></span> <span data-ttu-id="62195-203">Tato vazba poskytuje podporu Windows Communication Foundation (WCF) pro protokol WS-Federation.</span><span class="sxs-lookup"><span data-stu-id="62195-203">This binding provides Windows Communication Foundation (WCF) support for the WS-Federation protocol.</span></span> <span data-ttu-id="62195-204">Nakonfigurované s touto vazbou služby musíte použít přenos HTTP.</span><span class="sxs-lookup"><span data-stu-id="62195-204">Services configured with this binding must use the HTTP transport.</span></span>  
  
 <span data-ttu-id="62195-205">Vazby obsahovat zásobník elementů vazby.</span><span class="sxs-lookup"><span data-stu-id="62195-205">Bindings consist of a stack of binding elements.</span></span> <span data-ttu-id="62195-206">Zásobník elementů v vazby</span><span class="sxs-lookup"><span data-stu-id="62195-206">The stack of binding elements in</span></span>  
  
 <span data-ttu-id="62195-207">`wsFederationHttpBinding` je stejný jako příkaz, který je součástí `wsHttpBinding`</span><span class="sxs-lookup"><span data-stu-id="62195-207">`wsFederationHttpBinding` is the same as that contained in `wsHttpBinding`</span></span>  
  
 <span data-ttu-id="62195-208">Když [ \<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) nastavena na výchozí hodnotu <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span><span class="sxs-lookup"><span data-stu-id="62195-208">when [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) is set to the default value of <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message>.</span></span>  
  
 <span data-ttu-id="62195-209">`wsFederationHttpBinding` Řídí podrobnosti o nastavení zabezpečení zpráv v [ \<zpráva >](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="62195-209">The `wsFederationHttpBinding` controls the details of the message security settings in [\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-wsfederationhttpbinding.md).</span></span> <span data-ttu-id="62195-210">Všimněte si, že [ \<zabezpečení >](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element poskytuje získal přístup pouze jako zabezpečení používané vazby nelze změnit po vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="62195-210">Note that the [\<security>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-wsfederationhttpbinding.md) element provides get access only as the security used by the binding cannot be changed once the binding is created.</span></span>  
  
 <span data-ttu-id="62195-211">`wsFederationHttpBinding` Také poskytuje atribut privactyNoticeAt nastavit a načíst identifikátor URI, ve kterém se nachází v oznámení o ochraně osobních údajů.</span><span class="sxs-lookup"><span data-stu-id="62195-211">The `wsFederationHttpBinding` also provides a privactyNoticeAt attribute to set and retrieve the URI at which the privacy notice is located.</span></span>  
  
 <span data-ttu-id="62195-212">Udržování zásad zabezpečení je obzvláště důležité ve scénářích federace.</span><span class="sxs-lookup"><span data-stu-id="62195-212">Keeping policy secure is especially important in federation scenarios.</span></span> <span data-ttu-id="62195-213">Doporučuje se použít nějaký způsob zabezpečení, jako je například HTTPS, zásady ochrany před uživateli se zlými úmysly.</span><span class="sxs-lookup"><span data-stu-id="62195-213">The recommendation is to use some form of security, such as HTTPS, to protect the policy from malicious users.</span></span>  
  
 <span data-ttu-id="62195-214">Ve scénářích federační používá tuto vazbu má zásady služby potenciálně důležité informace, jako například klíč použít k zašifrování vydaných tokenu (SAML), typ deklarace identity put v tokenu a tak dále.</span><span class="sxs-lookup"><span data-stu-id="62195-214">In federation scenarios using this binding, the service policy potentially has important information such as the key to use to encrypt the issued (SAML) token, the type of claims to put in the token, and so forth.</span></span> <span data-ttu-id="62195-215">Pokud tato zásada se manipulovalo, může útočník zjistit klíč vystavený token vedoucí k další manipulaci s obsahem, zpřístupnění informací a další škodlivé chování.</span><span class="sxs-lookup"><span data-stu-id="62195-215">If this policy is tampered with, an attacker could discover the key of the issued token leading to further tampering, info disclosure and other malicious behavior.</span></span> <span data-ttu-id="62195-216">Chcete-li tomu zabránit, musí být získána zásady bezpečně (např. pomocí protokolu HTTPS) ze služby.</span><span class="sxs-lookup"><span data-stu-id="62195-216">To help prevent this, the policy must be obtained securely (for example using HTTPS) from the service.</span></span>  
  
 <span data-ttu-id="62195-217">Další informace o této vazbě najdete v tématu [postupy: vytvoření třídy WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span><span class="sxs-lookup"><span data-stu-id="62195-217">For more information on this binding, see [How to: Create a WSFederationHttpBinding](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="62195-218">Příklad</span><span class="sxs-lookup"><span data-stu-id="62195-218">Example</span></span>  
  
```xml  
<configuration>  
<system.ServiceModel>  
<bindings>  
<wsFederationHttpBinding>  
    <binding   
        bypassProxyOnLocal="false"  
        transactionFlow="false"  
        hostNameComparisonMode="WeakWildcard"  
        maxReceivedMessageSize="1000"  
        messageEncoding="Mtom"   
        proxyAddress="http://foo/bar"   
        textEncoding="Utf16TextEncoding"  
        useDefaultWebProxy="false">  
        <reliableSession ordered="false"  
            inactivityTimeout="00:02:00" enabled="true" />  
        <security mode="None">  
           <message negotiateServiceCredential="false"  
                algorithmSuite="Aes128"  
                issuedTokenType="saml"   
                issuedKeyType="PublicKey">  
               <issuer address="http://localhost/Sts" />  
           </message>  
        </security>  
    </binding>  
</wsFederationBinding>  
</bindings>  
</system.ServiceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="62195-219">Viz také</span><span class="sxs-lookup"><span data-stu-id="62195-219">See Also</span></span>  
 <xref:System.ServiceModel.WSFederationHttpBinding>  
 <xref:System.ServiceModel.Configuration.WSFederationHttpBindingElement>  
 [<span data-ttu-id="62195-220">Postupy: Vytvoření WSFederationHttpBinding</span><span class="sxs-lookup"><span data-stu-id="62195-220">How to: Create a WSFederationHttpBinding</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)  
 [<span data-ttu-id="62195-221">Vazby</span><span class="sxs-lookup"><span data-stu-id="62195-221">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="62195-222">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="62195-222">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="62195-223">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="62195-223">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="62195-224">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="62195-224">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
