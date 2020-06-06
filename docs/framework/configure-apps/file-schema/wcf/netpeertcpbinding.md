---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: 921da4d0b010672585a045d58d03182e480a255a
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140728"
---
# \<netPeerTcpBinding>
<span data-ttu-id="7d66a-101">Definuje vazbu pro zasílání zpráv TCP pro rovnocenné kanály.</span><span class="sxs-lookup"><span data-stu-id="7d66a-101">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netPeerTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="7d66a-102">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7d66a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7d66a-103">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7d66a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="7d66a-104">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7d66a-104">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7d66a-105">Atributy</span><span class="sxs-lookup"><span data-stu-id="7d66a-105">Attributes</span></span>  
  
|<span data-ttu-id="7d66a-106">Atribut</span><span class="sxs-lookup"><span data-stu-id="7d66a-106">Attribute</span></span>|<span data-ttu-id="7d66a-107">Popis</span><span class="sxs-lookup"><span data-stu-id="7d66a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="7d66a-108">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="7d66a-108">closeTimeout</span></span>|<span data-ttu-id="7d66a-109"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="7d66a-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7d66a-110">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="7d66a-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7d66a-111">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7d66a-111">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="7d66a-112">Třída ListenIPAddress</span><span class="sxs-lookup"><span data-stu-id="7d66a-112">listenIPAddress</span></span>|<span data-ttu-id="7d66a-113">Řetězec, který určuje IP adresu, na které bude partnerský uzel naslouchat zprávám TCP.</span><span class="sxs-lookup"><span data-stu-id="7d66a-113">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="7d66a-114">Výchozí formát je `null`.</span><span class="sxs-lookup"><span data-stu-id="7d66a-114">The default is `null`.</span></span>|  
|<span data-ttu-id="7d66a-115">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="7d66a-115">maxBufferPoolSize</span></span>|<span data-ttu-id="7d66a-116">Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="7d66a-116">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="7d66a-117">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="7d66a-117">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="7d66a-118">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7d66a-118">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="7d66a-119">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="7d66a-119">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="7d66a-120">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="7d66a-120">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="7d66a-121">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="7d66a-121">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="7d66a-122">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="7d66a-122">maxReceivedMessageSize</span></span>|<span data-ttu-id="7d66a-123">Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="7d66a-123">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="7d66a-124">Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="7d66a-124">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="7d66a-125">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="7d66a-125">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="7d66a-126">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="7d66a-126">The default is 65536.</span></span>|  
|<span data-ttu-id="7d66a-127">name</span><span class="sxs-lookup"><span data-stu-id="7d66a-127">name</span></span>|<span data-ttu-id="7d66a-128">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="7d66a-128">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7d66a-129">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="7d66a-129">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7d66a-130">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="7d66a-130">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7d66a-131">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7d66a-131">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="7d66a-132">openTimeout</span><span class="sxs-lookup"><span data-stu-id="7d66a-132">openTimeout</span></span>|<span data-ttu-id="7d66a-133"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="7d66a-133">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7d66a-134">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="7d66a-134">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7d66a-135">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7d66a-135">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="7d66a-136">port</span><span class="sxs-lookup"><span data-stu-id="7d66a-136">port</span></span>|<span data-ttu-id="7d66a-137">Celé číslo určující, na kterém portu síťového rozhraní bude tato vazba zpracovávat zprávy TCP rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="7d66a-137">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="7d66a-138">Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort> .</span><span class="sxs-lookup"><span data-stu-id="7d66a-138">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="7d66a-139">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="7d66a-139">The default is 0.</span></span>|  
|<span data-ttu-id="7d66a-140">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="7d66a-140">receiveTimeout</span></span>|<span data-ttu-id="7d66a-141"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="7d66a-141">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7d66a-142">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="7d66a-142">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7d66a-143">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="7d66a-143">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="7d66a-144">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="7d66a-144">sendTimeout</span></span>|<span data-ttu-id="7d66a-145"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="7d66a-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7d66a-146">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="7d66a-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7d66a-147">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7d66a-147">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7d66a-148">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="7d66a-148">Child Elements</span></span>  
  
|<span data-ttu-id="7d66a-149">Prvek</span><span class="sxs-lookup"><span data-stu-id="7d66a-149">Element</span></span>|<span data-ttu-id="7d66a-150">Description</span><span class="sxs-lookup"><span data-stu-id="7d66a-150">Description</span></span>|  
|-------------|-----------------|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="7d66a-151">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="7d66a-151">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="7d66a-152">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="7d66a-152">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<resolver>](resolver.md)|<span data-ttu-id="7d66a-153">Určuje rovnocenný překladač, který tato vazba používá k překladu ID partnerské sítě na IP adresy koncových uzlů v rámci partnerské sítě.</span><span class="sxs-lookup"><span data-stu-id="7d66a-153">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[\<security>](security-of-netpeerbinding.md)|<span data-ttu-id="7d66a-154">Definuje nastavení zabezpečení zprávy.</span><span class="sxs-lookup"><span data-stu-id="7d66a-154">Defines the security settings for the message.</span></span> <span data-ttu-id="7d66a-155">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="7d66a-155">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7d66a-156">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="7d66a-156">Parent Elements</span></span>  
  
|<span data-ttu-id="7d66a-157">Prvek</span><span class="sxs-lookup"><span data-stu-id="7d66a-157">Element</span></span>|<span data-ttu-id="7d66a-158">Description</span><span class="sxs-lookup"><span data-stu-id="7d66a-158">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="7d66a-159">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="7d66a-159">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d66a-160">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7d66a-160">Remarks</span></span>  
 <span data-ttu-id="7d66a-161">Tato vazba poskytuje podporu pro vytváření aplikací typu peer-to-peer nebo s více částmi využívajících partnerský přenos přes protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="7d66a-161">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="7d66a-162">Každý uzel rovnocenného uzlu může hostovat několik partnerských kanálů definovaných s tímto typem vazby.</span><span class="sxs-lookup"><span data-stu-id="7d66a-162">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d66a-163">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d66a-163">Example</span></span>  
 <span data-ttu-id="7d66a-164">Následující příklad ukazuje použití vazby NetPeerTcpBinding, která poskytuje komunikaci s více částmi pomocí rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="7d66a-164">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="7d66a-165">Podrobný scénář použití této vazby najdete v tématu [net peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="7d66a-165">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7d66a-166">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d66a-166">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="7d66a-167">Vazby</span><span class="sxs-lookup"><span data-stu-id="7d66a-167">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="7d66a-168">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="7d66a-168">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="7d66a-169">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7d66a-169">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
- <span data-ttu-id="7d66a-170">[Síťový partner TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="7d66a-170">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="7d66a-171">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="7d66a-171">Peer-to-Peer Networking</span></span>](../../../wcf/feature-details/peer-to-peer-networking.md)
