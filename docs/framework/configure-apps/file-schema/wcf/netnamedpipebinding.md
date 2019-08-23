---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: 475c7dfa618cffa70942fc1e02a75910da847701
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933090"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="dd90f-101">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="dd90f-101">\<netNamedPipeBinding></span></span>
<span data-ttu-id="dd90f-102">Definuje vazbu, která je zabezpečená, spolehlivá a optimalizovaná pro komunikaci mezi procesy v počítači.</span><span class="sxs-lookup"><span data-stu-id="dd90f-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="dd90f-103">Ve výchozím nastavení generuje komunikační zásobník za běhu s WS-ReliableMessaging pro spolehlivost, zabezpečení přenosu pro přenos zabezpečení, pojmenované kanály pro doručení zpráv a kódování binárních zpráv.</span><span class="sxs-lookup"><span data-stu-id="dd90f-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
 <span data-ttu-id="dd90f-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="dd90f-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dd90f-105">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="dd90f-105">\<bindings></span></span>  
<span data-ttu-id="dd90f-106">\<netNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="dd90f-106">\<netNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dd90f-107">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="dd90f-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dd90f-108">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="dd90f-108">Attributes and Elements</span></span>  
 <span data-ttu-id="dd90f-109">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="dd90f-109">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dd90f-110">Atributy</span><span class="sxs-lookup"><span data-stu-id="dd90f-110">Attributes</span></span>  
  
|<span data-ttu-id="dd90f-111">Atribut</span><span class="sxs-lookup"><span data-stu-id="dd90f-111">Attribute</span></span>|<span data-ttu-id="dd90f-112">Popis</span><span class="sxs-lookup"><span data-stu-id="dd90f-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="dd90f-113">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="dd90f-113">closeTimeout</span></span>|<span data-ttu-id="dd90f-114"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="dd90f-114">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="dd90f-115">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dd90f-115">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dd90f-116">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dd90f-116">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="dd90f-117">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="dd90f-117">hostNameComparisonMode</span></span>|<span data-ttu-id="dd90f-118">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="dd90f-118">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="dd90f-119">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, který označuje, zda je název hostitele použit pro dosažení služby při shodě s identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="dd90f-119">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="dd90f-120">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="dd90f-120">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="dd90f-121">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="dd90f-121">maxBufferPoolSize</span></span>|<span data-ttu-id="dd90f-122">Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="dd90f-122">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="dd90f-123">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="dd90f-123">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="dd90f-124">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="dd90f-124">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="dd90f-125">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="dd90f-125">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="dd90f-126">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="dd90f-126">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="dd90f-127">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="dd90f-127">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="dd90f-128">Třída</span><span class="sxs-lookup"><span data-stu-id="dd90f-128">maxBufferSize</span></span>|<span data-ttu-id="dd90f-129">Celé kladné číslo určující maximální velikost vyrovnávací paměti, která se používá k ukládání zpráv v paměti, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="dd90f-129">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="dd90f-130">Pokud je vyrovnávací paměť plná, nadbytečná data zůstanou v podkladovém soketu, dokud vyrovnávací paměť neuvolní.</span><span class="sxs-lookup"><span data-stu-id="dd90f-130">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="dd90f-131">Tato hodnota nemůže být menší než `maxReceivedMessageSize` atribut.</span><span class="sxs-lookup"><span data-stu-id="dd90f-131">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="dd90f-132">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="dd90f-132">The default is 65536.</span></span> <span data-ttu-id="dd90f-133">Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="dd90f-133">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="dd90f-134">maxConnections</span><span class="sxs-lookup"><span data-stu-id="dd90f-134">maxConnections</span></span>|<span data-ttu-id="dd90f-135">Celé číslo, které určuje maximální počet odchozích a příchozích připojení, které služba vytvoří nebo přijme.</span><span class="sxs-lookup"><span data-stu-id="dd90f-135">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="dd90f-136">Příchozí a odchozí připojení se počítají na základě zvláštního limitu určeného tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="dd90f-136">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="dd90f-137">Příchozí připojení přesahující tento limit se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.</span><span class="sxs-lookup"><span data-stu-id="dd90f-137">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="dd90f-138">Odchozí připojení přesahující limit se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.</span><span class="sxs-lookup"><span data-stu-id="dd90f-138">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="dd90f-139">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="dd90f-139">The default is 10.</span></span>|  
|<span data-ttu-id="dd90f-140">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="dd90f-140">maxReceivedMessageSize</span></span>|<span data-ttu-id="dd90f-141">Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="dd90f-141">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="dd90f-142">Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="dd90f-142">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="dd90f-143">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="dd90f-143">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="dd90f-144">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="dd90f-144">The default is 65536.</span></span>|  
|<span data-ttu-id="dd90f-145">name</span><span class="sxs-lookup"><span data-stu-id="dd90f-145">name</span></span>|<span data-ttu-id="dd90f-146">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="dd90f-146">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="dd90f-147">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="dd90f-147">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="dd90f-148">[!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)]Od, není nutné, aby vazby a chování měly název.</span><span class="sxs-lookup"><span data-stu-id="dd90f-148">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="dd90f-149">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="dd90f-149">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="dd90f-150">openTimeout</span><span class="sxs-lookup"><span data-stu-id="dd90f-150">openTimeout</span></span>|<span data-ttu-id="dd90f-151"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="dd90f-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="dd90f-152">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dd90f-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dd90f-153">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dd90f-153">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="dd90f-154">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="dd90f-154">receiveTimeout</span></span>|<span data-ttu-id="dd90f-155"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="dd90f-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="dd90f-156">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dd90f-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dd90f-157">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="dd90f-157">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="dd90f-158">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="dd90f-158">sendTimeout</span></span>|<span data-ttu-id="dd90f-159"><xref:System.TimeSpan> Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="dd90f-159">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="dd90f-160">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="dd90f-160">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="dd90f-161">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="dd90f-161">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="dd90f-162">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="dd90f-162">transactionFlow</span></span>|<span data-ttu-id="dd90f-163">Logická hodnota určující, zda vazba podporuje tok dat WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="dd90f-163">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="dd90f-164">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="dd90f-164">The default is `false`.</span></span>|  
|<span data-ttu-id="dd90f-165">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="dd90f-165">transactionProtocol</span></span>|<span data-ttu-id="dd90f-166">Určuje transakční protokol, který se má použít s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="dd90f-166">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="dd90f-167">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="dd90f-167">Valid values are</span></span><br /><br /> <span data-ttu-id="dd90f-168">– OleTransactions</span><span class="sxs-lookup"><span data-stu-id="dd90f-168">-   OleTransactions</span></span><br /><span data-ttu-id="dd90f-169">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="dd90f-169">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="dd90f-170">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="dd90f-170">The default is OleTransactions.</span></span> <span data-ttu-id="dd90f-171">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="dd90f-171">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="dd90f-172">transferMode</span><span class="sxs-lookup"><span data-stu-id="dd90f-172">transferMode</span></span>|<span data-ttu-id="dd90f-173"><xref:System.ServiceModel.TransferMode> Hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány nebo jsou požadavkem či odpovědí.</span><span class="sxs-lookup"><span data-stu-id="dd90f-173">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dd90f-174">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="dd90f-174">Child Elements</span></span>  
  
|<span data-ttu-id="dd90f-175">Prvek</span><span class="sxs-lookup"><span data-stu-id="dd90f-175">Element</span></span>|<span data-ttu-id="dd90f-176">Popis</span><span class="sxs-lookup"><span data-stu-id="dd90f-176">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd90f-177">\<> zabezpečení</span><span class="sxs-lookup"><span data-stu-id="dd90f-177">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="dd90f-178">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="dd90f-178">Defines the security settings for the binding.</span></span> <span data-ttu-id="dd90f-179">Tento prvek je typu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="dd90f-179">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|<span data-ttu-id="dd90f-180">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="dd90f-180">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="dd90f-181">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="dd90f-181">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="dd90f-182">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="dd90f-182">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="dd90f-183">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="dd90f-183">Parent Elements</span></span>  
  
|<span data-ttu-id="dd90f-184">Prvek</span><span class="sxs-lookup"><span data-stu-id="dd90f-184">Element</span></span>|<span data-ttu-id="dd90f-185">Popis</span><span class="sxs-lookup"><span data-stu-id="dd90f-185">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dd90f-186">\<> vazeb</span><span class="sxs-lookup"><span data-stu-id="dd90f-186">\<bindings></span></span>](bindings.md)|<span data-ttu-id="dd90f-187">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="dd90f-187">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dd90f-188">Poznámky</span><span class="sxs-lookup"><span data-stu-id="dd90f-188">Remarks</span></span>  
 <span data-ttu-id="dd90f-189">`NetNamedPipeBinding` Vygeneruje ve výchozím nastavení zásobník pro komunikaci za běhu, který používá zabezpečení přenosu, pojmenované kanály pro doručení zprávy a kódování binárních zpráv.</span><span class="sxs-lookup"><span data-stu-id="dd90f-189">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="dd90f-190">Tato vazba je vhodná volba pro Windows Communication Foundation (WCF) poskytovaná pro komunikaci v počítači.</span><span class="sxs-lookup"><span data-stu-id="dd90f-190">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="dd90f-191">Podporuje také transakce.</span><span class="sxs-lookup"><span data-stu-id="dd90f-191">It also supports transactions.</span></span>  
  
 <span data-ttu-id="dd90f-192">Výchozí konfigurace pro `NetNamedPipeBinding` je podobná konfiguraci `NetTcpBinding`, kterou poskytuje, ale je jednodušší, protože implementace služby WCF je určena pouze pro použití v počítači a v důsledku toho je k dispozici méně vydaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="dd90f-192">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="dd90f-193">Nejvýznamnějším rozdílem je, že `securityMode` nastavení `None` nabízí jenom možnosti a `Transport` .</span><span class="sxs-lookup"><span data-stu-id="dd90f-193">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="dd90f-194">Podpora zabezpečení SOAP není zahrnutá možnost.</span><span class="sxs-lookup"><span data-stu-id="dd90f-194">SOAP security support is not an included option.</span></span> <span data-ttu-id="dd90f-195">Chování zabezpečení lze konfigurovat pomocí volitelného `securityMode` atributu.</span><span class="sxs-lookup"><span data-stu-id="dd90f-195">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="dd90f-196">Příklad</span><span class="sxs-lookup"><span data-stu-id="dd90f-196">Example</span></span>  
 <span data-ttu-id="dd90f-197">Následující příklad ukazuje vazbu netNamedPipeBinding, která poskytuje komunikaci mezi procesy ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="dd90f-197">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="dd90f-198">Pojmenované kanály nefungují napříč počítači.</span><span class="sxs-lookup"><span data-stu-id="dd90f-198">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="dd90f-199">Vazba je určena v konfiguračních souborech pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="dd90f-199">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="dd90f-200">Typ vazby je určen v `binding` atributu `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="dd90f-200">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="dd90f-201">Pokud chcete nakonfigurovat vazbu netNamedPipeBinding a změnit některá její nastavení, musíte definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="dd90f-201">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="dd90f-202">Koncový bod musí odkazovat na konfiguraci vazby podle názvu s `bindingConfiguration` atributem.</span><span class="sxs-lookup"><span data-stu-id="dd90f-202">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="dd90f-203">V tomto příkladu má konfigurace vazby název Binding1.</span><span class="sxs-lookup"><span data-stu-id="dd90f-203">In this example, the binding configuration is named Binding1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="dd90f-204">Viz také:</span><span class="sxs-lookup"><span data-stu-id="dd90f-204">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [<span data-ttu-id="dd90f-205">\<> vazby</span><span class="sxs-lookup"><span data-stu-id="dd90f-205">\<binding></span></span>](../../../misc/binding.md)
- [<span data-ttu-id="dd90f-206">Vazby</span><span class="sxs-lookup"><span data-stu-id="dd90f-206">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="dd90f-207">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="dd90f-207">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="dd90f-208">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="dd90f-208">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
