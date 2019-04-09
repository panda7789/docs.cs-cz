---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: dc1af462222920c7b3c6b66c3822e7b2b326b244
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59169816"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="b6ec5-101">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="b6ec5-101">\<netNamedPipeBinding></span></span>
<span data-ttu-id="b6ec5-102">Definuje vazbu, která je zabezpečená, spolehlivá, optimalizovaná pro komunikaci mezi procesy dané stanice.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="b6ec5-103">Ve výchozím nastavení vygeneruje zásobník modulu runtime komunikace s WS-ReliableMessaging spolehlivosti, zabezpečení přenosu pro zabezpečení přenosu, pojmenované kanály pro doručování zpráv a kódování binární zprávy.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
 <span data-ttu-id="b6ec5-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="b6ec5-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="b6ec5-105">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="b6ec5-105">\<bindings></span></span>  
<span data-ttu-id="b6ec5-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="b6ec5-106">\<netNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b6ec5-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b6ec5-107">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"
           maxBufferPoolSize="Integer"
           maxBufferSize="Integer"
           maxConnections="Integer"
           maxReceivedMessageSize="Integer"
           name="String"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan"
           transactionFlow="Boolean"
           transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"
           transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">
    <security mode="None/Transport">
      <transport protectionLevel="None/Sign/EncryptAndSign" />
    </security>
    <readerQuotas maxArrayLength="Integer"
                  maxBytesPerRead="Integer"
                  maxDepth="Integer"
                  maxNameTableCharCount="Integer"
                  maxStringContentLength="Integer" />
  </binding>
</netNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b6ec5-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="b6ec5-108">Attributes and Elements</span></span>  
 <span data-ttu-id="b6ec5-109">Následující části popisují atributy, podřízené prvky a nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b6ec5-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b6ec5-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="b6ec5-110">Attributes</span></span>  
  
|<span data-ttu-id="b6ec5-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="b6ec5-111">Attribute</span></span>|<span data-ttu-id="b6ec5-112">Popis</span><span class="sxs-lookup"><span data-stu-id="b6ec5-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b6ec5-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="b6ec5-113">closeTimeout</span></span>|<span data-ttu-id="b6ec5-114">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="b6ec5-115">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b6ec5-116">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="b6ec5-117">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="b6ec5-117">hostNameComparisonMode</span></span>|<span data-ttu-id="b6ec5-118">Určuje režim porovnání jména hostitele HTTP použít k analýze identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="b6ec5-119">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, což znamená, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="b6ec5-120">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, které ignoruje jako název hostitele v porovnávání.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="b6ec5-121">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="b6ec5-121">maxBufferPoolSize</span></span>|<span data-ttu-id="b6ec5-122">Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-122">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="b6ec5-123">Výchozí hodnota je 524,288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="b6ec5-123">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="b6ec5-124">Mnoho částí Windows Communication Foundation (WCF) použít vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-124">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="b6ec5-125">Vytváření a ničení pokaždé, když používají se vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměť je také náročné.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-125">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="b6ec5-126">S fondy vyrovnávací paměti může trvat vyrovnávací paměti z fondu, ho použít a vrátit do fondu, až budete hotovi.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-126">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="b6ec5-127">Proto je vyloučeno režie při vytváření a ničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-127">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="b6ec5-128">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="b6ec5-128">maxBufferSize</span></span>|<span data-ttu-id="b6ec5-129">Kladné celé číslo, které určuje maximální velikost v bajtech, vyrovnávací paměti používané k ukládání zpráv v paměti.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-129">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="b6ec5-130">Pokud vyrovnávací paměť je plná, zůstane nadbytečná data řadit v podkladové soketu, dokud znovu místnosti má vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-130">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="b6ec5-131">Tato hodnota nemůže být menší než `maxReceivedMessageSize` atribut.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-131">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="b6ec5-132">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-132">The default is 65536.</span></span> <span data-ttu-id="b6ec5-133">Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-133">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="b6ec5-134">maxConnections</span><span class="sxs-lookup"><span data-stu-id="b6ec5-134">maxConnections</span></span>|<span data-ttu-id="b6ec5-135">Celé číslo, které určuje maximální počet odchozí a příchozí připojení služby vytvořit/přijme.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-135">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="b6ec5-136">Příchozí a odchozí připojení se započítávají i samostatné limit specifikovaný pro tento atribut.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-136">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="b6ec5-137">Příchozí připojení nad tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-137">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="b6ec5-138">Odchozí připojení nad tento limit se zařadí do fronty, dokud nebude k dispozici prostor pod limit.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-138">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="b6ec5-139">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-139">The default is 10.</span></span>|  
|<span data-ttu-id="b6ec5-140">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="b6ec5-140">maxReceivedMessageSize</span></span>|<span data-ttu-id="b6ec5-141">Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně záhlaví, které může být přijata v kanálu nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-141">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="b6ec5-142">Odesílatel zprávy překračující tento limit se zobrazí chyba protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-142">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="b6ec5-143">Příjemce zahodí a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="b6ec5-144">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-144">The default is 65536.</span></span>|  
|<span data-ttu-id="b6ec5-145">name</span><span class="sxs-lookup"><span data-stu-id="b6ec5-145">name</span></span>|<span data-ttu-id="b6ec5-146">Řetězec, který obsahuje konfigurační název vazby.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-146">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="b6ec5-147">Tato hodnota by měla být jedinečný, protože se používá jako identifikace pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-147">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="b6ec5-148">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-148">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="b6ec5-149">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="b6ec5-149">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="b6ec5-150">openTimeout</span><span class="sxs-lookup"><span data-stu-id="b6ec5-150">openTimeout</span></span>|<span data-ttu-id="b6ec5-151">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="b6ec5-152">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b6ec5-153">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-153">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="b6ec5-154">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="b6ec5-154">receiveTimeout</span></span>|<span data-ttu-id="b6ec5-155">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace obdržení.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="b6ec5-156">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b6ec5-157">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-157">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="b6ec5-158">SendTimeout</span><span class="sxs-lookup"><span data-stu-id="b6ec5-158">sendTimeout</span></span>|<span data-ttu-id="b6ec5-159">A <xref:System.TimeSpan> hodnotu, která určuje, časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="b6ec5-160">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="b6ec5-161">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-161">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="b6ec5-162">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="b6ec5-162">transactionFlow</span></span>|<span data-ttu-id="b6ec5-163">Logická hodnota určující, zda vazba podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-163">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="b6ec5-164">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-164">The default is `false`.</span></span>|  
|<span data-ttu-id="b6ec5-165">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="b6ec5-165">transactionProtocol</span></span>|<span data-ttu-id="b6ec5-166">Určuje protokol transakce, jenž má být použit s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-166">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="b6ec5-167">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="b6ec5-167">Valid values are</span></span><br /><br /> <span data-ttu-id="b6ec5-168">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="b6ec5-168">-   OleTransactions</span></span><br /><span data-ttu-id="b6ec5-169">– WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="b6ec5-169">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="b6ec5-170">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-170">The default is OleTransactions.</span></span> <span data-ttu-id="b6ec5-171">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-171">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="b6ec5-172">transferMode</span><span class="sxs-lookup"><span data-stu-id="b6ec5-172">transferMode</span></span>|<span data-ttu-id="b6ec5-173">A <xref:System.ServiceModel.TransferMode> hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo prostřednictvím datového proudu nebo požadavek nebo odpověď.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-173">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b6ec5-174">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="b6ec5-174">Child Elements</span></span>  
  
|<span data-ttu-id="b6ec5-175">Prvek</span><span class="sxs-lookup"><span data-stu-id="b6ec5-175">Element</span></span>|<span data-ttu-id="b6ec5-176">Popis</span><span class="sxs-lookup"><span data-stu-id="b6ec5-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6ec5-177">\<security></span><span class="sxs-lookup"><span data-stu-id="b6ec5-177">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="b6ec5-178">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-178">Defines the security settings for the binding.</span></span> <span data-ttu-id="b6ec5-179">Tento prvek je typu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-179">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[<span data-ttu-id="b6ec5-180">\<readerQuotas></span><span class="sxs-lookup"><span data-stu-id="b6ec5-180">\<readerQuotas></span></span>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="b6ec5-181">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-181">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="b6ec5-182">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-182">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b6ec5-183">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="b6ec5-183">Parent Elements</span></span>  
  
|<span data-ttu-id="b6ec5-184">Prvek</span><span class="sxs-lookup"><span data-stu-id="b6ec5-184">Element</span></span>|<span data-ttu-id="b6ec5-185">Popis</span><span class="sxs-lookup"><span data-stu-id="b6ec5-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b6ec5-186">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="b6ec5-186">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="b6ec5-187">Tento prvek obsahuje sadu standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-187">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b6ec5-188">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b6ec5-188">Remarks</span></span>  
 <span data-ttu-id="b6ec5-189">`NetNamedPipeBinding` Generuje runtime komunikačního balíku ve výchozím nastavení, která používá zabezpečení přenosu pojmenované kanály pro doručování zpráv a zprávy v binární kódování.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-189">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="b6ec5-190">Tato vazba je vhodné Windows Communication Foundation (WCF) poskytované systémem volbou pro komunikaci na počítači.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-190">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="b6ec5-191">Také podporuje transakce.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-191">It also supports transactions.</span></span>  
  
 <span data-ttu-id="b6ec5-192">Výchozí konfigurace pro `NetNamedPipeBinding` se podobá konfiguraci poskytované `NetTcpBinding`, ale je jednodušší, protože implementace WCF je určená jenom pro použití na počítači a v důsledku toho nejsou zveřejněné méně funkcí.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-192">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="b6ec5-193">Nejdůležitější rozdíl je, že `securityMode` nastavení pouze nabídky `None` a `Transport` možnosti.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-193">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="b6ec5-194">Podpora protokolu SOAP zabezpečení není možné zahrnuté.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-194">SOAP security support is not an included option.</span></span> <span data-ttu-id="b6ec5-195">Chování zabezpečení je možné konfigurovat pomocí volitelného `securityMode` atribut.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-195">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b6ec5-196">Příklad</span><span class="sxs-lookup"><span data-stu-id="b6ec5-196">Example</span></span>  
 <span data-ttu-id="b6ec5-197">Následující příklad ukazuje netNamedPipeBinding vazbu, která poskytuje komunikaci mezi procesy ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-197">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="b6ec5-198">Pojmenované kanály napříč počítači nefungují.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-198">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="b6ec5-199">Vazba je zadán v konfiguračních souborech pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-199">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="b6ec5-200">Typ vazby je zadán v `binding` atribut `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-200">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="b6ec5-201">Pokud chcete konfiguraci vazby netNamedPipeBinding a některé z nastavení změnit, je nutné definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-201">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="b6ec5-202">Koncový bod musí odkazovat konfigurace vazby podle názvu pomocí `bindingConfiguration` atribut.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-202">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="b6ec5-203">V tomto příkladu má název konfigurace vazby Binding1.</span><span class="sxs-lookup"><span data-stu-id="b6ec5-203">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <host>
          <baseAddresses>
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
          </baseAddresses>
        </host>
        <!-- this endpoint is exposed at the base address provided by host: net.pipe://localhost/ServiceModelSamples/service  -->
        <endpoint address="net.pipe://localhost/ServiceModelSamples/service"
                  binding="netNamedPipeBinding"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <bindings>
      <netNamedPipeBinding>
        <binding closeTimeout="00:01:00"
                 openTimeout="00:01:00"
                 receiveTimeout="00:10:00"
                 sendTimeout="00:01:00"
                 transactionFlow="false"
                 transferMode="Buffered"
                 transactionProtocol="OleTransactions"
                 hostNameComparisonMode="StrongWildcard"
                 maxBufferPoolSize="524288"
                 maxBufferSize="65536"
                 maxConnections="10"
                 maxReceivedMessageSize="65536">
          <security mode="Transport">
            <transport protectionLevel="EncryptAndSign" />
          </security>
        </binding>
      </netNamedPipeBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a><span data-ttu-id="b6ec5-204">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b6ec5-204">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [<span data-ttu-id="b6ec5-205">\<Vytvoření vazby ></span><span class="sxs-lookup"><span data-stu-id="b6ec5-205">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
- [<span data-ttu-id="b6ec5-206">Vazby</span><span class="sxs-lookup"><span data-stu-id="b6ec5-206">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="b6ec5-207">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="b6ec5-207">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="b6ec5-208">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="b6ec5-208">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
