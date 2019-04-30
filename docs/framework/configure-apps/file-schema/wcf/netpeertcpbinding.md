---
title: <netPeerTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netPeerBinding element
ms.assetid: 2dd77ada-a176-47c7-a740-900b279f1aad
ms.openlocfilehash: b35e2f365e82291d3f8b827850fdebfe8fa2237d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61780364"
---
# <a name="netpeertcpbinding"></a><span data-ttu-id="790ee-101">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="790ee-101">\<netPeerTcpBinding></span></span>
<span data-ttu-id="790ee-102">Definuje vazbu pro peer channel zprávy TCP.</span><span class="sxs-lookup"><span data-stu-id="790ee-102">Defines a binding for peer channel specific TCP messaging.</span></span>  
  
 <span data-ttu-id="790ee-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="790ee-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="790ee-104">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="790ee-104">\<bindings></span></span>  
<span data-ttu-id="790ee-105">\<netPeerTcpBinding></span><span class="sxs-lookup"><span data-stu-id="790ee-105">\<netPeerTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="790ee-106">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="790ee-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="790ee-107">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="790ee-107">Attributes and Elements</span></span>  
 <span data-ttu-id="790ee-108">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="790ee-108">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="790ee-109">Atributy</span><span class="sxs-lookup"><span data-stu-id="790ee-109">Attributes</span></span>  
  
|<span data-ttu-id="790ee-110">Atribut</span><span class="sxs-lookup"><span data-stu-id="790ee-110">Attribute</span></span>|<span data-ttu-id="790ee-111">Popis</span><span class="sxs-lookup"><span data-stu-id="790ee-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="790ee-112">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="790ee-112">closeTimeout</span></span>|<span data-ttu-id="790ee-113">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="790ee-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="790ee-114">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="790ee-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="790ee-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="790ee-115">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="790ee-116">listenIPAddress</span><span class="sxs-lookup"><span data-stu-id="790ee-116">listenIPAddress</span></span>|<span data-ttu-id="790ee-117">Řetězec, který určuje IP adresu, na které bude partnerský uzel přijímat zprávy TCP.</span><span class="sxs-lookup"><span data-stu-id="790ee-117">A string that specifies an IP address on which the peer node will listen for TCP messages.</span></span> <span data-ttu-id="790ee-118">Výchozí hodnota je `null`.</span><span class="sxs-lookup"><span data-stu-id="790ee-118">The default is `null`.</span></span>|  
|<span data-ttu-id="790ee-119">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="790ee-119">maxBufferPoolSize</span></span>|<span data-ttu-id="790ee-120">Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="790ee-120">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="790ee-121">Výchozí hodnota je 524,288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="790ee-121">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="790ee-122">Mnoho částí Windows Communication Foundation (WCF) použít vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="790ee-122">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="790ee-123">Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné.</span><span class="sxs-lookup"><span data-stu-id="790ee-123">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="790ee-124">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="790ee-124">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="790ee-125">Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="790ee-125">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="790ee-126">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="790ee-126">maxReceivedMessageSize</span></span>|<span data-ttu-id="790ee-127">Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně záhlaví, které může být přijata v kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="790ee-127">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="790ee-128">Odesílatel zprávy překračující tento limit se zobrazí chyba protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="790ee-128">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="790ee-129">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="790ee-129">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="790ee-130">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="790ee-130">The default is 65536.</span></span>|  
|<span data-ttu-id="790ee-131">name</span><span class="sxs-lookup"><span data-stu-id="790ee-131">name</span></span>|<span data-ttu-id="790ee-132">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="790ee-132">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="790ee-133">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="790ee-133">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="790ee-134">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="790ee-134">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="790ee-135">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="790ee-135">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="790ee-136">openTimeout</span><span class="sxs-lookup"><span data-stu-id="790ee-136">openTimeout</span></span>|<span data-ttu-id="790ee-137">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="790ee-137">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="790ee-138">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="790ee-138">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="790ee-139">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="790ee-139">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="790ee-140">port</span><span class="sxs-lookup"><span data-stu-id="790ee-140">port</span></span>|<span data-ttu-id="790ee-141">Celé číslo, které určuje portu síťového rozhraní, na které bude tato vazba zpracovávat zprávy TCP rovnocenného kanálu.</span><span class="sxs-lookup"><span data-stu-id="790ee-141">An integer that specifies the network interface port on which this binding will process peer channel TCP messages.</span></span> <span data-ttu-id="790ee-142">Tato hodnota musí být mezi <xref:System.Net.IPEndPoint.MinPort> a <xref:System.Net.IPEndPoint.MaxPort>.</span><span class="sxs-lookup"><span data-stu-id="790ee-142">This value must be between <xref:System.Net.IPEndPoint.MinPort> and <xref:System.Net.IPEndPoint.MaxPort>.</span></span> <span data-ttu-id="790ee-143">Výchozí hodnota je 0.</span><span class="sxs-lookup"><span data-stu-id="790ee-143">The default is 0.</span></span>|  
|<span data-ttu-id="790ee-144">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="790ee-144">receiveTimeout</span></span>|<span data-ttu-id="790ee-145">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="790ee-145">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="790ee-146">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="790ee-146">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="790ee-147">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="790ee-147">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="790ee-148">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="790ee-148">sendTimeout</span></span>|<span data-ttu-id="790ee-149">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="790ee-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="790ee-150">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="790ee-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="790ee-151">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="790ee-151">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="790ee-152">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="790ee-152">Child Elements</span></span>  
  
|<span data-ttu-id="790ee-153">Prvek</span><span class="sxs-lookup"><span data-stu-id="790ee-153">Element</span></span>|<span data-ttu-id="790ee-154">Popis</span><span class="sxs-lookup"><span data-stu-id="790ee-154">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="790ee-155">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="790ee-155">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="790ee-156">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="790ee-156">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="790ee-157">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="790ee-157">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="790ee-158">\<resolver></span><span class="sxs-lookup"><span data-stu-id="790ee-158">\<resolver></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/resolver.md)|<span data-ttu-id="790ee-159">Určuje mechanismus rozpoznávání partnera použité v této vazbě partnerské sítě ID na koncový bod IP adresy uzlů v rámci sdílené sítě.</span><span class="sxs-lookup"><span data-stu-id="790ee-159">Specifies a peer resolver used by this binding to resolve a peer mesh ID to the endpoint IP addresses of nodes within the peer mesh.</span></span>|  
|[<span data-ttu-id="790ee-160">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="790ee-160">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netpeerbinding.md)|<span data-ttu-id="790ee-161">Definuje nastavení zabezpečení pro zprávu.</span><span class="sxs-lookup"><span data-stu-id="790ee-161">Defines the security settings for the message.</span></span> <span data-ttu-id="790ee-162">Tento prvek je typu <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="790ee-162">This element is of type <xref:System.ServiceModel.Configuration.PeerSecurityElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="790ee-163">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="790ee-163">Parent Elements</span></span>  
  
|<span data-ttu-id="790ee-164">Prvek</span><span class="sxs-lookup"><span data-stu-id="790ee-164">Element</span></span>|<span data-ttu-id="790ee-165">Popis</span><span class="sxs-lookup"><span data-stu-id="790ee-165">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="790ee-166">\<bindings></span><span class="sxs-lookup"><span data-stu-id="790ee-166">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="790ee-167">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="790ee-167">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="790ee-168">Poznámky</span><span class="sxs-lookup"><span data-stu-id="790ee-168">Remarks</span></span>  
 <span data-ttu-id="790ee-169">Tato vazba poskytuje podporu pro vytváření aplikací peer-to-peer nebo více uživatelů pomocí rovnocenný přenos přes protokol TCP.</span><span class="sxs-lookup"><span data-stu-id="790ee-169">This binding provides support for the creation of peer-to-peer or multiparty applications using peer transport over TCP.</span></span> <span data-ttu-id="790ee-170">Každý partnerský uzel může hostovat více kanálů peer definované s tímto typem vazby.</span><span class="sxs-lookup"><span data-stu-id="790ee-170">Each peer node can host multiple peer channels defined with this binding type.</span></span>  
  
## <a name="example"></a><span data-ttu-id="790ee-171">Příklad</span><span class="sxs-lookup"><span data-stu-id="790ee-171">Example</span></span>  
 <span data-ttu-id="790ee-172">Následující příklad ukazuje použití NetPeerTcpBinding vazeb, které poskytuje éře komunikaci pomocí protokolu peer channel.</span><span class="sxs-lookup"><span data-stu-id="790ee-172">The following example demonstrates using the NetPeerTcpBinding binding, which provides multiparty communication using a peer channel.</span></span> <span data-ttu-id="790ee-173">Podrobné scénář použití tuto vazbu, najdete v článku [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span><span class="sxs-lookup"><span data-stu-id="790ee-173">For a detailed scenario of using this binding, see [Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90)).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="790ee-174">Viz také:</span><span class="sxs-lookup"><span data-stu-id="790ee-174">See also</span></span>

- <xref:System.ServiceModel.NetPeerTcpBinding>
- <xref:System.ServiceModel.Configuration.NetPeerTcpBindingElement>
- [<span data-ttu-id="790ee-175">Vazby</span><span class="sxs-lookup"><span data-stu-id="790ee-175">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="790ee-176">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="790ee-176">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="790ee-177">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="790ee-177">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="790ee-178">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="790ee-178">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- <span data-ttu-id="790ee-179">[NET Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="790ee-179">[Net Peer TCP](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751426(v=vs.90))</span></span>
- [<span data-ttu-id="790ee-180">Síť rovnocenných počítačů</span><span class="sxs-lookup"><span data-stu-id="790ee-180">Peer-to-Peer Networking</span></span>](../../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)
