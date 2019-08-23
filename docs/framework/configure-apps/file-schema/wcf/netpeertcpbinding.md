---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: fc1930889235805d68d88aa8080f8f9fb3235612
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933031"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="46d2d-101">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="46d2d-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="46d2d-102">Definuje vazbu pro zasílání zpráv TCP pro rovnocenné kanály.</span><span class="sxs-lookup"><span data-stu-id="46d2d-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="46d2d-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="46d2d-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="46d2d-104">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="46d2d-104">\<bindings></span></span>  
<span data-ttu-id="46d2d-105">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="46d2d-105">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46d2d-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="46d2d-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="46d2d-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="46d2d-107">Attributes and Elements</span></span>  
 <span data-ttu-id="46d2d-108">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="46d2d-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="46d2d-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="46d2d-109">Attributes</span></span>  
  
|<span data-ttu-id="46d2d-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="46d2d-110">Attribute</span></span>|<span data-ttu-id="46d2d-111">Popis</span><span class="sxs-lookup"><span data-stu-id="46d2d-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="46d2d-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="46d2d-112">closeTimeout</span></span>|<span data-ttu-id="46d2d-113"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="46d2d-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="46d2d-114">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="46d2d-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="46d2d-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="46d2d-115">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="46d2d-116">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="46d2d-116">listenIPAddress</span></span>|<span data-ttu-id="46d2d-117">Řetězec, který určuje IP adresu, na které bude partnerský uzel naslouchat zprávám TCP.</span><span class="sxs-lookup"><span data-stu-id="46d2d-117">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="46d2d-118">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="46d2d-118">The default is `null`.</span></span>|  
|<span data-ttu-id="46d2d-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="46d2d-119">maxBufferPoolSize</span></span>|<span data-ttu-id="46d2d-120">Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="46d2d-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="46d2d-121">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="46d2d-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="46d2d-122">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="46d2d-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="46d2d-123">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="46d2d-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="46d2d-124">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="46d2d-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="46d2d-125">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="46d2d-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="46d2d-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="46d2d-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="46d2d-127">Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="46d2d-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="46d2d-128">Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="46d2d-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="46d2d-129">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="46d2d-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="46d2d-130">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="46d2d-130">The default is 65536.</span></span>|  
|<span data-ttu-id="46d2d-131">name</span><span class="sxs-lookup"><span data-stu-id="46d2d-131">name</span></span>|<span data-ttu-id="46d2d-132">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="46d2d-132">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="46d2d-133">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="46d2d-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="46d2d-134">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="46d2d-134">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="46d2d-135">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="46d2d-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="46d2d-136">openTimeout</span><span class="sxs-lookup"><span data-stu-id="46d2d-136">openTimeout</span></span>|<span data-ttu-id="46d2d-137"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="46d2d-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="46d2d-138">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="46d2d-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="46d2d-139">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="46d2d-139">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="46d2d-140">port</span><span class="sxs-lookup"><span data-stu-id="46d2d-140">port</span></span>|<span data-ttu-id="46d2d-141">Celé číslo určující, na kterém portu síťového rozhraní bude tato vazba zpracovávat zprávy TCP rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="46d2d-141">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="46d2d-142">Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="46d2d-142">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="46d2d-143">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="46d2d-143">The default is 0.</span></span>|  
|<span data-ttu-id="46d2d-144">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="46d2d-144">receiveTimeout</span></span>|<span data-ttu-id="46d2d-145"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="46d2d-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="46d2d-146">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="46d2d-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="46d2d-147">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="46d2d-147">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="46d2d-148">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="46d2d-148">sendTimeout</span></span>|<span data-ttu-id="46d2d-149"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="46d2d-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="46d2d-150">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="46d2d-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="46d2d-151">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="46d2d-151">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="46d2d-152">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="46d2d-152">Child Elements</span></span>  
  
|<span data-ttu-id="46d2d-153">Prvek</span><span class="sxs-lookup"><span data-stu-id="46d2d-153">Element</span></span>|<span data-ttu-id="46d2d-154">Popis</span><span class="sxs-lookup"><span data-stu-id="46d2d-154">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="46d2d-155">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="46d2d-155">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="46d2d-156">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="46d2d-156">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="46d2d-157">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="46d2d-157">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="46d2d-158">\<resolver></span><span class="sxs-lookup"><span data-stu-id="46d2d-158">\<resolver></span></span>](resolver.md)|<span data-ttu-id="46d2d-159">Určuje rovnocenný překladač, který tato vazba používá k překladu ID partnerské sítě na IP adresy koncových uzlů v rámci partnerské sítě.</span><span class="sxs-lookup"><span data-stu-id="46d2d-159">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="46d2d-160">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="46d2d-160">\<security></span></span>](security-of-netpeerbinding.md)|<span data-ttu-id="46d2d-161">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="46d2d-161">Defines the security settings for the message.</span></span> <span data-ttu-id="46d2d-162">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="46d2d-162">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="46d2d-163">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="46d2d-163">Parent Elements</span></span>  
  
|<span data-ttu-id="46d2d-164">Prvek</span><span class="sxs-lookup"><span data-stu-id="46d2d-164">Element</span></span>|<span data-ttu-id="46d2d-165">Popis</span><span class="sxs-lookup"><span data-stu-id="46d2d-165">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="46d2d-166">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="46d2d-166">\<bindings></span></span>](bindings.md)|<span data-ttu-id="46d2d-167">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="46d2d-167">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="46d2d-168">Poznámky</span><span class="sxs-lookup"><span data-stu-id="46d2d-168">Remarks</span></span>  
 <span data-ttu-id="46d2d-169">Tato vazba poskytuje podporu pro vytváření aplikací typu peer-to-peer nebo s více částmi využívajících partnerský přenos přes protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="46d2d-169">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="46d2d-170">Každý uzel rovnocenného uzlu může hostovat několik partnerských kanálů definovaných s tímto typem vazby.</span><span class="sxs-lookup"><span data-stu-id="46d2d-170">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="46d2d-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="46d2d-171">Example</span></span>  
 <span data-ttu-id="46d2d-172">Následující příklad ukazuje použití vazby NetPeerTcpBinding, která poskytuje komunikaci s více částmi pomocí rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="46d2d-172">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="46d2d-173">Podrobný scénář použití této vazby najdete v tématu [net peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="46d2d-173">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="46d2d-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="46d2d-174">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="46d2d-175">Vazby</span><span class="sxs-lookup"><span data-stu-id="46d2d-175">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="46d2d-176">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="46d2d-176">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="46d2d-177">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="46d2d-177">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="46d2d-178">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="46d2d-178">\<binding></span></span>](../../../misc/binding.md)
- <span data-ttu-id="46d2d-179">[Síťový partner TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="46d2d-179">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="46d2d-180">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="46d2d-180">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
