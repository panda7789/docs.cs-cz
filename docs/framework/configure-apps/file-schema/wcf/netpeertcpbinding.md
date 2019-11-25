---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 921da4d0b010672585a045d58d03182e480a255a
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140728"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="47529-101">\<netPeerTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="47529-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="47529-102">Definuje vazbu pro zasílání zpráv TCP pro rovnocenné kanály.</span><span class="sxs-lookup"><span data-stu-id="47529-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
<span data-ttu-id="47529-103">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="47529-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="47529-104">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="47529-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="47529-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="47529-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="47529-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netPeerTcpBinding >**</span><span class="sxs-lookup"><span data-stu-id="47529-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47529-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="47529-107">Syntax</span></span>  
  
```xml  
<netPeerBinding>
  <binding name="string"
           closeTimeout="TimeSpan"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           listenIPAddress="String"
           maxBufferPoolSize="integer"
           maxReceiveMessageSize="Integer"
           port="Integer">
    <security mode="None/Transport/Message/TransportWithMessageCredential">
      <transport credentialType="Certificate/Password" />
    </security>
  </binding>
</netPeerBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="47529-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="47529-108">Attributes and Elements</span></span>  
 <span data-ttu-id="47529-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="47529-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="47529-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="47529-110">Attributes</span></span>  
  
|<span data-ttu-id="47529-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="47529-111">Attribute</span></span>|<span data-ttu-id="47529-112">Popis</span><span class="sxs-lookup"><span data-stu-id="47529-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="47529-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="47529-113">closeTimeout</span></span>|<span data-ttu-id="47529-114">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení.</span><span class="sxs-lookup"><span data-stu-id="47529-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="47529-115">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="47529-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="47529-116">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="47529-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="47529-117">Třída ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="47529-117">listenIPAddress</span></span>|<span data-ttu-id="47529-118">Řetězec, který určuje IP adresu, na které bude partnerský uzel naslouchat zprávám TCP.</span><span class="sxs-lookup"><span data-stu-id="47529-118">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="47529-119">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="47529-119">The default is `null`.</span></span>|  
|<span data-ttu-id="47529-120">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="47529-120">maxBufferPoolSize</span></span>|<span data-ttu-id="47529-121">Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="47529-121">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="47529-122">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="47529-122">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="47529-123">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="47529-123">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="47529-124">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="47529-124">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="47529-125">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="47529-125">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="47529-126">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="47529-126">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="47529-127">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="47529-127">maxReceivedMessageSize</span></span>|<span data-ttu-id="47529-128">Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="47529-128">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="47529-129">Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="47529-129">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="47529-130">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="47529-130">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="47529-131">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="47529-131">The default is 65536.</span></span>|  
|<span data-ttu-id="47529-132">name</span><span class="sxs-lookup"><span data-stu-id="47529-132">name</span></span>|<span data-ttu-id="47529-133">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="47529-133">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="47529-134">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="47529-134">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="47529-135">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="47529-135">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="47529-136">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="47529-136">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="47529-137">openTimeout</span><span class="sxs-lookup"><span data-stu-id="47529-137">openTimeout</span></span>|<span data-ttu-id="47529-138">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="47529-138">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="47529-139">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="47529-139">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="47529-140">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="47529-140">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="47529-141">port</span><span class="sxs-lookup"><span data-stu-id="47529-141">port</span></span>|<span data-ttu-id="47529-142">Celé číslo určující, na kterém portu síťového rozhraní bude tato vazba zpracovávat zprávy TCP rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="47529-142">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="47529-143">Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="47529-143">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="47529-144">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="47529-144">The default is 0.</span></span>|  
|<span data-ttu-id="47529-145">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="47529-145">receiveTimeout</span></span>|<span data-ttu-id="47529-146">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="47529-146">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="47529-147">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="47529-147">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="47529-148">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="47529-148">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="47529-149">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="47529-149">sendTimeout</span></span>|<span data-ttu-id="47529-150">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="47529-150">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="47529-151">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="47529-151">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="47529-152">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="47529-152">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="47529-153">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="47529-153">Child Elements</span></span>  
  
|<span data-ttu-id="47529-154">Prvek</span><span class="sxs-lookup"><span data-stu-id="47529-154">Element</span></span>|<span data-ttu-id="47529-155">Popis</span><span class="sxs-lookup"><span data-stu-id="47529-155">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="47529-156">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="47529-156">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="47529-157">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="47529-157">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="47529-158">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="47529-158">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="47529-159">\<překladač ></span><span class="sxs-lookup"><span data-stu-id="47529-159">\<resolver></span></span>](resolver.md)|<span data-ttu-id="47529-160">Určuje rovnocenný překladač, který tato vazba používá k překladu ID partnerské sítě na IP adresy koncových uzlů v rámci partnerské sítě.</span><span class="sxs-lookup"><span data-stu-id="47529-160">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="47529-161">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="47529-161">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="47529-162">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="47529-162">Defines the security settings for the message.</span></span> <span data-ttu-id="47529-163">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="47529-163">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="47529-164">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="47529-164">Parent Elements</span></span>  
  
|<span data-ttu-id="47529-165">Prvek</span><span class="sxs-lookup"><span data-stu-id="47529-165">Element</span></span>|<span data-ttu-id="47529-166">Popis</span><span class="sxs-lookup"><span data-stu-id="47529-166">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="47529-167">vazby\<</span><span class="sxs-lookup"><span data-stu-id="47529-167">\<bindings></span></span>](bindings.md)|<span data-ttu-id="47529-168">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="47529-168">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47529-169">Poznámky</span><span class="sxs-lookup"><span data-stu-id="47529-169">Remarks</span></span>  
 <span data-ttu-id="47529-170">Tato vazba poskytuje podporu pro vytváření aplikací typu peer-to-peer nebo s více částmi využívajících partnerský přenos přes protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="47529-170">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="47529-171">Každý uzel rovnocenného uzlu může hostovat několik partnerských kanálů definovaných s tímto typem vazby.</span><span class="sxs-lookup"><span data-stu-id="47529-171">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47529-172">Příklad</span><span class="sxs-lookup"><span data-stu-id="47529-172">Example</span></span>  
 <span data-ttu-id="47529-173">Následující příklad ukazuje použití vazby NetPeerTcpBinding, která poskytuje komunikaci s více částmi pomocí rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="47529-173">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="47529-174">Podrobný scénář použití této vazby najdete v tématu [net peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="47529-174">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
```xml  
<configuration>
  <system.ServiceModel>
    <bindings>
      <netPeerBinding>
        <binding closeTimeout="00:00:10"
                 openTimeout="00:00:20"
                 receiveTimeout="00:00:30"
                 sendTimeout="00:00:40"
                 maxBufferSize="1001"
                 maxConnections="123"
                 maxReceiveMessageSize="1000">
          <reliableSession ordered="false"
                           inactivityTimeout="00:02:00"
                           enabled="true" />
          <security mode="TransportWithMessageCredential">
            <message clientCredentialType="CardSpace" />
          </security>
        </binding>
      </netPeerBinding>
    </bindings>
  </system.ServiceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="47529-175">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47529-175">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="47529-176">Vazby</span><span class="sxs-lookup"><span data-stu-id="47529-176">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="47529-177">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="47529-177">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="47529-178">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="47529-178">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="47529-179">vazba \<</span><span class="sxs-lookup"><span data-stu-id="47529-179">\<binding></span></span>](bindings.md)
- <span data-ttu-id="47529-180">[Síťový partner TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="47529-180">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="47529-181">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="47529-181">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
