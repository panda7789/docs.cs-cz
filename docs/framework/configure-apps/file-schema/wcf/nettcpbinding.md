---
title: '&lt;NetTcpBinding&gt;'
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: 0849120edf7d4b8948b3632cfe2fc81f1bdff1eb
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/09/2019
ms.locfileid: "54148185"
---
# <a name="ltnettcpbindinggt"></a><span data-ttu-id="7e2e0-102">&lt;NetTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="7e2e0-102">&lt;netTcpBinding&gt;</span></span>

<span data-ttu-id="7e2e0-103">Určuje zabezpečená, spolehlivá a optimalizovaná vazby vhodné pro komunikaci mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-103">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="7e2e0-104">Ve výchozím nastavení vygeneruje zásobník modulu runtime komunikace s Windows zabezpečení pro zabezpečení zpráv a ověřování protokolu TCP pro doručování zpráv a kódování binární zprávy.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-104">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

<span data-ttu-id="7e2e0-105">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7e2e0-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="7e2e0-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="7e2e0-106">\<bindings></span></span>  
<span data-ttu-id="7e2e0-107">\<netTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="7e2e0-107">\<netTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e2e0-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7e2e0-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7e2e0-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="7e2e0-109">Attributes and elements</span></span>

<span data-ttu-id="7e2e0-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7e2e0-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="7e2e0-111">Attributes</span></span>  
  
|<span data-ttu-id="7e2e0-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="7e2e0-112">Attribute</span></span>|<span data-ttu-id="7e2e0-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7e2e0-113">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="7e2e0-114">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="7e2e0-115">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7e2e0-116">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-116">The default is 00:01:00.</span></span>|  
|`hostnameComparisonMode`|<span data-ttu-id="7e2e0-117">Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-117">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="7e2e0-118">Tento atribut je typu `System.ServiceModel.HostnameComparisonMode`, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-118">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="7e2e0-119">Výchozí hodnota je `StrongWildcard`, které ignoruje jako název hostitele v porovnávání.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-119">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="7e2e0-120">Kladné celé číslo, určující maximální počet kanálů čekat na přijetí na naslouchací proces.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-120">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="7e2e0-121">Připojení překračující tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-121">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="7e2e0-122">`connectionTimeout` Atribut omezuje času, klient bude čekat před vyvolání výjimky připojení připojený k Internetu.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-122">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="7e2e0-123">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-123">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="7e2e0-124">Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-124">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="7e2e0-125">Výchozí hodnota je 512 \* 1024 bajtů.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-125">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="7e2e0-126">Mnoho částí Windows Communication Foundation (WCF) použít vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-126">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="7e2e0-127">Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-127">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="7e2e0-128">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-128">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="7e2e0-129">Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-129">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="7e2e0-130">Kladné celé číslo, které určuje maximální velikost v bajtech, vyrovnávací paměti používané k ukládání zpráv v paměti.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="7e2e0-131">Pokud `transferMode` atributu rovná `Buffered`, tento atribut by měl být roven `maxReceivedMessageSize` hodnotu atributu.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-131">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="7e2e0-132">Pokud `transferMode` atributu rovná `Streamed`, tento atribut nemůže být více než `maxReceivedMessageSize` hodnotu atributu a by měl mít velikost záhlaví.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-132">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="7e2e0-133">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-133">The default is 65536.</span></span> <span data-ttu-id="7e2e0-134">Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="7e2e0-135">Celé číslo, které určuje maximální počet odchozí a příchozí připojení služby vytvořit/přijme.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-135">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="7e2e0-136">Příchozí a odchozí připojení se započítávají i samostatné limit specifikovaný pro tento atribut.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-136">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="7e2e0-137">Příchozí připojení nad tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-137">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="7e2e0-138">Odchozí připojení nad tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-138">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="7e2e0-139">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-139">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="7e2e0-140">Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně záhlaví, které může být přijata v kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-140">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="7e2e0-141">Odesílatel zprávy překračující tento limit se zobrazí chyba protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-141">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="7e2e0-142">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-142">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="7e2e0-143">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-143">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="7e2e0-144">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-144">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="7e2e0-145">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-145">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="7e2e0-146">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-146">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="7e2e0-147">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="7e2e0-147">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="7e2e0-148">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-148">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="7e2e0-149">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-149">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7e2e0-150">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-150">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="7e2e0-151">Logická hodnota určující, zda je pro toto připojení povoleno sdílení portu TCP.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-151">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="7e2e0-152">Pokud je to `false`, každá vazba používá výhradně portu.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-152">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="7e2e0-153">Toto nastavení je relevantní pouze pro služby, protože klienti to nebude mít vliv.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-153">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="7e2e0-154">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-154">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="7e2e0-155">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-155">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7e2e0-156">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-156">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="7e2e0-157">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-157">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="7e2e0-158">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-158">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="7e2e0-159">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-159">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="7e2e0-160">Logická hodnota určující, zda vazba podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-160">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="7e2e0-161">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-161">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="7e2e0-162">Určuje protokol transakce, jenž má být použit s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-162">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="7e2e0-163">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="7e2e0-163">Valid values are</span></span><br /><br /> <span data-ttu-id="7e2e0-164">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="7e2e0-164">-   OleTransactions</span></span><br /><span data-ttu-id="7e2e0-165">-WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="7e2e0-165">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="7e2e0-166">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-166">The default is OleTransactions.</span></span> <span data-ttu-id="7e2e0-167">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-167">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="7e2e0-168">A <xref:System.ServiceModel.TransferMode> hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo prostřednictvím datového proudu nebo požadavek nebo odpověď.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-168">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="7e2e0-169">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="7e2e0-169">Child elements</span></span>  
  
|<span data-ttu-id="7e2e0-170">Prvek</span><span class="sxs-lookup"><span data-stu-id="7e2e0-170">Element</span></span>|<span data-ttu-id="7e2e0-171">Popis</span><span class="sxs-lookup"><span data-stu-id="7e2e0-171">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e2e0-172">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="7e2e0-172">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)|<span data-ttu-id="7e2e0-173">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-173">Defines the security settings for the binding.</span></span> <span data-ttu-id="7e2e0-174">Tento prvek je typu <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-174">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|[<span data-ttu-id="7e2e0-175">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="7e2e0-175">\<readerQuotas></span></span>](https://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="7e2e0-176">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-176">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="7e2e0-177">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-177">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[<span data-ttu-id="7e2e0-178">reliableSession</span><span class="sxs-lookup"><span data-stu-id="7e2e0-178">reliableSession</span></span>](https://msdn.microsoft.com/library/9c93818a-7dfa-43d5-b3a1-1aafccf3a00b)|<span data-ttu-id="7e2e0-179">Určuje, pokud jsou mezi koncovými body kanál navázat spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-179">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7e2e0-180">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="7e2e0-180">Parent elements</span></span>  
  
|<span data-ttu-id="7e2e0-181">Prvek</span><span class="sxs-lookup"><span data-stu-id="7e2e0-181">Element</span></span>|<span data-ttu-id="7e2e0-182">Popis</span><span class="sxs-lookup"><span data-stu-id="7e2e0-182">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7e2e0-183">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="7e2e0-183">\<bindings></span></span>](bindings.md)|<span data-ttu-id="7e2e0-184">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-184">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7e2e0-185">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7e2e0-185">Remarks</span></span>

<span data-ttu-id="7e2e0-186">Tato vazba generuje runtime komunikačního balíku ve výchozím nastavení, která používá zabezpečení přenosu protokolu TCP pro doručování zpráv a zprávy v binární kódování.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-186">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="7e2e0-187">Tato vazba je vhodné Windows Communication Foundation (WCF) poskytované systémem volbou pro komunikaci přes Intranet.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-187">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="7e2e0-188">Výchozí konfigurace pro `netTcpBinding` je rychlejší než konfigurace poskytované `wsHttpBinding`, ale je určena pouze pro komunikaci WCF.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-188">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="7e2e0-189">Chování zabezpečení je možné konfigurovat pomocí volitelného `securityMode` atribut.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-189">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="7e2e0-190">Použití WS-ReliableMessaging je možné konfigurovat pomocí volitelného `reliableSessionEnabled` atribut.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-190">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="7e2e0-191">Ale spolehlivé zasílání zpráv je vypnuto ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-191">But reliable messaging is off by default.</span></span> <span data-ttu-id="7e2e0-192">Obecně platí, HTTP vazeb poskytovaných systémem, jako `wsHttpBinding` a `basicHttpBinding` umožňují zapnout věci ve výchozím nastavení, že `netTcpBinding` vazby vypne věci ve výchozím nastavení tak, že budete muset přihlásit k získání podpory, třeba pro jeden z WS-\* specifikace.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-192">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="7e2e0-193">To znamená, že je výchozí konfigurace pro protokol TCP rychlejší při výměně zpráv mezi koncovými body než ty, které ve výchozím nastavení nakonfigurované pro vazby protokolu HTTP.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-193">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7e2e0-194">Příklad</span><span class="sxs-lookup"><span data-stu-id="7e2e0-194">Example</span></span>

<span data-ttu-id="7e2e0-195">Vazba je zadán v konfiguračních souborech pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-195">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="7e2e0-196">Typ vazby je zadán v `binding` atribut `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-196">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="7e2e0-197">Pokud chcete konfiguraci vazby netTcpBinding a některé z nastavení změnit, je potřeba definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-197">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="7e2e0-198">Koncový bod musí odkazovat na konfiguraci vazby `bindingConfiguration` atribut.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-198">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="7e2e0-199">V následujícím příkladu je definován konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="7e2e0-199">In the following example, a binding configuration is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7e2e0-200">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7e2e0-200">See also</span></span>  

- <xref:System.ServiceModel.NetTcpBinding>  
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>  
- [<span data-ttu-id="7e2e0-201">Vazby</span><span class="sxs-lookup"><span data-stu-id="7e2e0-201">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
- [<span data-ttu-id="7e2e0-202">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="7e2e0-202">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
- [<span data-ttu-id="7e2e0-203">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="7e2e0-203">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
- [<span data-ttu-id="7e2e0-204">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="7e2e0-204">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
