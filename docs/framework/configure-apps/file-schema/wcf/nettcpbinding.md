---
title: <netTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: 54e9a488b9e83b07d1d6d7e18e92ecedc5c74ea6
ms.sourcegitcommit: 01ea420eaa4bf76d5fc47673294c8881379b3369
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/06/2019
ms.locfileid: "55759181"
---
# <a name="nettcpbinding"></a><span data-ttu-id="14048-101">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="14048-101">\<netTcpBinding></span></span>

<span data-ttu-id="14048-102">Určuje zabezpečená, spolehlivá a optimalizovaná vazby vhodné pro komunikaci mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="14048-102">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="14048-103">Ve výchozím nastavení vygeneruje zásobník modulu runtime komunikace s Windows zabezpečení pro zabezpečení zpráv a ověřování protokolu TCP pro doručování zpráv a kódování binární zprávy.</span><span class="sxs-lookup"><span data-stu-id="14048-103">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

<span data-ttu-id="14048-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="14048-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="14048-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="14048-105">\<bindings></span></span>  
<span data-ttu-id="14048-106">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="14048-106">\<netTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14048-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="14048-107">Syntax</span></span>  
  
```xml  
<netTcpBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           listenBacklog="Integer"
           maxBufferPoolSize="integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="string"
           openTimeout="TimeSpan"
           portSharingEnabled="Boolean"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WSAtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <reliableSession ordered="Boolean"
                     inactivityTimeout="TimeSpan"
                     enabled="Boolean" />
    <security mode="None/Transport/Message/Both">
      <message clientCredentialType="None/Windows/UserName/Certificate/CardSpace"
               algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15" />
      <transport clientCredentialType="None/Windows/Certificate"
                 protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="14048-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="14048-108">Attributes and elements</span></span>

<span data-ttu-id="14048-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="14048-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="14048-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="14048-110">Attributes</span></span>  
  
|<span data-ttu-id="14048-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="14048-111">Attribute</span></span>|<span data-ttu-id="14048-112">Popis</span><span class="sxs-lookup"><span data-stu-id="14048-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="14048-113">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="14048-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="14048-114">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="14048-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="14048-115">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="14048-115">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="14048-116">Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="14048-116">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="14048-117">Tento atribut je typu `System.ServiceModel.HostnameComparisonMode`, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="14048-117">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="14048-118">Výchozí hodnota je `StrongWildcard`, které ignoruje jako název hostitele v porovnávání.</span><span class="sxs-lookup"><span data-stu-id="14048-118">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="14048-119">Kladné celé číslo, určující maximální počet kanálů čekat na přijetí na naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="14048-119">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="14048-120">Připojení překračující tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit.</span><span class="sxs-lookup"><span data-stu-id="14048-120">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="14048-121">`connectionTimeout` Atribut omezuje času, klient bude čekat před vyvolání výjimky připojení připojený k Internetu.</span><span class="sxs-lookup"><span data-stu-id="14048-121">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="14048-122">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="14048-122">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="14048-123">Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="14048-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="14048-124">Výchozí hodnota je 512 \* 1024 bajtů.</span><span class="sxs-lookup"><span data-stu-id="14048-124">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="14048-125">Mnoho částí Windows Communication Foundation (WCF) použít vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="14048-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="14048-126">Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné.</span><span class="sxs-lookup"><span data-stu-id="14048-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="14048-127">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="14048-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="14048-128">Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="14048-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="14048-129">Kladné celé číslo, které určuje maximální velikost v bajtech, vyrovnávací paměti používané k ukládání zpráv v paměti.</span><span class="sxs-lookup"><span data-stu-id="14048-129">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="14048-130">Pokud `transferMode` atributu rovná `Buffered`, tento atribut by měl být roven `maxReceivedMessageSize` hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="14048-130">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="14048-131">Pokud `transferMode` atributu rovná `Streamed`, tento atribut nemůže být více než `maxReceivedMessageSize` hodnotu atributu a by měl mít velikost záhlaví.</span><span class="sxs-lookup"><span data-stu-id="14048-131">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="14048-132">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="14048-132">The default is 65536.</span></span> <span data-ttu-id="14048-133">Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="14048-133">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="14048-134">Celé číslo, které určuje maximální počet odchozí a příchozí připojení služby vytvořit/přijme.</span><span class="sxs-lookup"><span data-stu-id="14048-134">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="14048-135">Příchozí a odchozí připojení se započítávají i samostatné limit specifikovaný pro tento atribut.</span><span class="sxs-lookup"><span data-stu-id="14048-135">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="14048-136">Příchozí připojení nad tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit.</span><span class="sxs-lookup"><span data-stu-id="14048-136">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="14048-137">Odchozí připojení nad tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit.</span><span class="sxs-lookup"><span data-stu-id="14048-137">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="14048-138">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="14048-138">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="14048-139">Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně záhlaví, které může být přijata v kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="14048-139">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="14048-140">Odesílatel zprávy překračující tento limit se zobrazí chyba protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="14048-140">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="14048-141">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="14048-141">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="14048-142">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="14048-142">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="14048-143">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="14048-143">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="14048-144">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="14048-144">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="14048-145">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="14048-145">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="14048-146">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="14048-146">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="14048-147">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="14048-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="14048-148">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="14048-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="14048-149">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="14048-149">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="14048-150">Logická hodnota určující, zda je pro toto připojení povoleno sdílení portu TCP.</span><span class="sxs-lookup"><span data-stu-id="14048-150">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="14048-151">Pokud je to `false`, každá vazba používá výhradně portu.</span><span class="sxs-lookup"><span data-stu-id="14048-151">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="14048-152">Toto nastavení je relevantní pouze pro služby, protože klienti to nebude mít vliv.</span><span class="sxs-lookup"><span data-stu-id="14048-152">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="14048-153">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="14048-153">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="14048-154">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="14048-154">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="14048-155">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="14048-155">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="14048-156">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="14048-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="14048-157">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="14048-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="14048-158">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="14048-158">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="14048-159">Logická hodnota určující, zda vazba podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="14048-159">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="14048-160">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="14048-160">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="14048-161">Určuje protokol transakce, jenž má být použit s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="14048-161">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="14048-162">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="14048-162">Valid values are</span></span><br /><br /> <span data-ttu-id="14048-163">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="14048-163">-   OleTransactions</span></span><br /><span data-ttu-id="14048-164">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="14048-164">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="14048-165">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="14048-165">The default is OleTransactions.</span></span> <span data-ttu-id="14048-166">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="14048-166">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="14048-167">A <xref:System.ServiceModel.TransferMode> hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo prostřednictvím datového proudu nebo požadavek nebo odpověď.</span><span class="sxs-lookup"><span data-stu-id="14048-167">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="14048-168">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="14048-168">Child elements</span></span>  
  
|<span data-ttu-id="14048-169">Prvek</span><span class="sxs-lookup"><span data-stu-id="14048-169">Element</span></span>|<span data-ttu-id="14048-170">Popis</span><span class="sxs-lookup"><span data-stu-id="14048-170">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14048-171">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="14048-171">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="14048-172">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="14048-172">Defines the security settings for the binding.</span></span> <span data-ttu-id="14048-173">Tento prvek je typu <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="14048-173">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|<span data-ttu-id="14048-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="14048-174">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="14048-175">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="14048-175">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="14048-176">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="14048-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|<span data-ttu-id="14048-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="14048-177">[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))</span></span>|<span data-ttu-id="14048-178">Určuje, pokud jsou mezi koncovými body kanál navázat spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="14048-178">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="14048-179">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="14048-179">Parent elements</span></span>  
  
|<span data-ttu-id="14048-180">Prvek</span><span class="sxs-lookup"><span data-stu-id="14048-180">Element</span></span>|<span data-ttu-id="14048-181">Popis</span><span class="sxs-lookup"><span data-stu-id="14048-181">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="14048-182">\<bindings></span><span class="sxs-lookup"><span data-stu-id="14048-182">\<bindings></span></span>](bindings.md)|<span data-ttu-id="14048-183">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="14048-183">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="14048-184">Poznámky</span><span class="sxs-lookup"><span data-stu-id="14048-184">Remarks</span></span>

<span data-ttu-id="14048-185">Tato vazba generuje runtime komunikačního balíku ve výchozím nastavení, která používá zabezpečení přenosu protokolu TCP pro doručování zpráv a zprávy v binární kódování.</span><span class="sxs-lookup"><span data-stu-id="14048-185">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="14048-186">Tato vazba je vhodné Windows Communication Foundation (WCF) poskytované systémem volbou pro komunikaci přes Intranet.</span><span class="sxs-lookup"><span data-stu-id="14048-186">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="14048-187">Výchozí konfigurace pro `netTcpBinding` je rychlejší než konfigurace poskytované `wsHttpBinding`, ale je určena pouze pro komunikaci WCF.</span><span class="sxs-lookup"><span data-stu-id="14048-187">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="14048-188">Chování zabezpečení je možné konfigurovat pomocí volitelného `securityMode` atribut.</span><span class="sxs-lookup"><span data-stu-id="14048-188">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="14048-189">Použití WS-ReliableMessaging je možné konfigurovat pomocí volitelného `reliableSessionEnabled` atribut.</span><span class="sxs-lookup"><span data-stu-id="14048-189">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="14048-190">Ale spolehlivé zasílání zpráv je vypnuto ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="14048-190">But reliable messaging is off by default.</span></span> <span data-ttu-id="14048-191">Obecně platí, HTTP vazeb poskytovaných systémem, jako `wsHttpBinding` a `basicHttpBinding` umožňují zapnout věci ve výchozím nastavení, že `netTcpBinding` vazby vypne věci ve výchozím nastavení tak, že budete muset přihlásit k získání podpory, třeba pro jeden z WS-\* specifikace.</span><span class="sxs-lookup"><span data-stu-id="14048-191">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="14048-192">To znamená, že je výchozí konfigurace pro protokol TCP rychlejší při výměně zpráv mezi koncovými body než ty, které ve výchozím nastavení nakonfigurované pro vazby protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="14048-192">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="14048-193">Příklad</span><span class="sxs-lookup"><span data-stu-id="14048-193">Example</span></span>

<span data-ttu-id="14048-194">Vazba je zadán v konfiguračních souborech pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="14048-194">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="14048-195">Typ vazby je zadán v `binding` atribut `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="14048-195">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="14048-196">Pokud chcete konfiguraci vazby netTcpBinding a některé z nastavení změnit, je potřeba definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="14048-196">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="14048-197">Koncový bod musí odkazovat na konfiguraci vazby `bindingConfiguration` atribut.</span><span class="sxs-lookup"><span data-stu-id="14048-197">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="14048-198">V následujícím příkladu je definován konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="14048-198">In the following example, a binding configuration is defined.</span></span>  
  
```xml  
<services>
  <service name="Microsoft.ServiceModel.Samples.CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    ...
    <endpoint address=""
              binding="netTcpBinding"
              contract="Microsoft.ServiceModel.Samples.ICalculator" />
    ...
  </service>
</services>
<bindings>
  <netTcpBinding>
    <binding closeTimeout="00:01:00"
             openTimeout="00:01:00"
             receiveTimeout="00:10:00"
             sendTimeout="00:01:00"
             transactionFlow="false"
             transferMode="Buffered"
             transactionProtocol="OleTransactions"
             hostNameComparisonMode="StrongWildcard"
             listenBacklog="10"
             maxBufferPoolSize="524288"
             maxBufferSize="65536"
             maxConnections="10"
             maxReceivedMessageSize="65536">
      <readerQuotas maxDepth="32"
                    maxStringContentLength="8192"
                    maxArrayLength="16384"
                    maxBytesPerRead="4096"
                    maxNameTableCharCount="16384" />
      <reliableSession ordered="true"
                       inactivityTimeout="00:10:00"
                       enabled="false" />
      <security mode="Transport">
        <transport clientCredentialType="Windows" protectionLevel="EncryptAndSign" />
      </security>
    </binding>
  </netTcpBinding>
</bindings>
```  
  
## <a name="see-also"></a><span data-ttu-id="14048-199">Viz také:</span><span class="sxs-lookup"><span data-stu-id="14048-199">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [<span data-ttu-id="14048-200">Vazby</span><span class="sxs-lookup"><span data-stu-id="14048-200">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="14048-201">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="14048-201">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="14048-202">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="14048-202">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="14048-203">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="14048-203">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
