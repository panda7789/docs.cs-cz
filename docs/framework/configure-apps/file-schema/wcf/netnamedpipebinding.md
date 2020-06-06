---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: f1aa68bcdda43fd77bee397c079695f7937faa52
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139465"
---
# \<netNamedPipeBinding>
<span data-ttu-id="33d45-101">Definuje vazbu, která je zabezpečená, spolehlivá a optimalizovaná pro komunikaci mezi procesy v počítači.</span><span class="sxs-lookup"><span data-stu-id="33d45-101">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="33d45-102">Ve výchozím nastavení generuje komunikační zásobník za běhu s WS-ReliableMessaging pro spolehlivost, zabezpečení přenosu pro přenos zabezpečení, pojmenované kanály pro doručení zpráv a kódování binárních zpráv.</span><span class="sxs-lookup"><span data-stu-id="33d45-102">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="33d45-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="33d45-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="33d45-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="33d45-104">Attributes and Elements</span></span>  
 <span data-ttu-id="33d45-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="33d45-105">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="33d45-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="33d45-106">Attributes</span></span>  
  
|<span data-ttu-id="33d45-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="33d45-107">Attribute</span></span>|<span data-ttu-id="33d45-108">Popis</span><span class="sxs-lookup"><span data-stu-id="33d45-108">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="33d45-109">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="33d45-109">closeTimeout</span></span>|<span data-ttu-id="33d45-110"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="33d45-110">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="33d45-111">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="33d45-111">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="33d45-112">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="33d45-112">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="33d45-113">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="33d45-113">hostNameComparisonMode</span></span>|<span data-ttu-id="33d45-114">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="33d45-114">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="33d45-115">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode> , který označuje, zda je název hostitele použit pro dosažení služby při shodě s identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="33d45-115">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="33d45-116">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="33d45-116">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="33d45-117">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="33d45-117">maxBufferPoolSize</span></span>|<span data-ttu-id="33d45-118">Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="33d45-118">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="33d45-119">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="33d45-119">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="33d45-120">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="33d45-120">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="33d45-121">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="33d45-121">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="33d45-122">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="33d45-122">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="33d45-123">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="33d45-123">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="33d45-124">Třída</span><span class="sxs-lookup"><span data-stu-id="33d45-124">maxBufferSize</span></span>|<span data-ttu-id="33d45-125">Celé kladné číslo určující maximální velikost vyrovnávací paměti, která se používá k ukládání zpráv v paměti, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="33d45-125">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="33d45-126">Pokud je vyrovnávací paměť plná, nadbytečná data zůstanou v podkladovém soketu, dokud vyrovnávací paměť neuvolní.</span><span class="sxs-lookup"><span data-stu-id="33d45-126">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="33d45-127">Tato hodnota nemůže být menší než `maxReceivedMessageSize` atribut.</span><span class="sxs-lookup"><span data-stu-id="33d45-127">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="33d45-128">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="33d45-128">The default is 65536.</span></span> <span data-ttu-id="33d45-129">Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="33d45-129">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="33d45-130">maxConnections</span><span class="sxs-lookup"><span data-stu-id="33d45-130">maxConnections</span></span>|<span data-ttu-id="33d45-131">Celé číslo, které určuje maximální počet odchozích a příchozích připojení, které služba vytvoří nebo přijme.</span><span class="sxs-lookup"><span data-stu-id="33d45-131">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="33d45-132">Příchozí a odchozí připojení se počítají na základě zvláštního limitu určeného tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="33d45-132">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="33d45-133">Příchozí připojení přesahující tento limit se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.</span><span class="sxs-lookup"><span data-stu-id="33d45-133">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="33d45-134">Odchozí připojení přesahující limit se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.</span><span class="sxs-lookup"><span data-stu-id="33d45-134">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="33d45-135">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="33d45-135">The default is 10.</span></span>|  
|<span data-ttu-id="33d45-136">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="33d45-136">maxReceivedMessageSize</span></span>|<span data-ttu-id="33d45-137">Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="33d45-137">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="33d45-138">Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="33d45-138">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="33d45-139">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="33d45-139">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="33d45-140">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="33d45-140">The default is 65536.</span></span>|  
|<span data-ttu-id="33d45-141">name</span><span class="sxs-lookup"><span data-stu-id="33d45-141">name</span></span>|<span data-ttu-id="33d45-142">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="33d45-142">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="33d45-143">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="33d45-143">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="33d45-144">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="33d45-144">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="33d45-145">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="33d45-145">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="33d45-146">openTimeout</span><span class="sxs-lookup"><span data-stu-id="33d45-146">openTimeout</span></span>|<span data-ttu-id="33d45-147"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="33d45-147">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="33d45-148">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="33d45-148">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="33d45-149">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="33d45-149">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="33d45-150">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="33d45-150">receiveTimeout</span></span>|<span data-ttu-id="33d45-151"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="33d45-151">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="33d45-152">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="33d45-152">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="33d45-153">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="33d45-153">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="33d45-154">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="33d45-154">sendTimeout</span></span>|<span data-ttu-id="33d45-155"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="33d45-155">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="33d45-156">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="33d45-156">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="33d45-157">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="33d45-157">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="33d45-158">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="33d45-158">transactionFlow</span></span>|<span data-ttu-id="33d45-159">Logická hodnota určující, zda vazba podporuje tok dat WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="33d45-159">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="33d45-160">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="33d45-160">The default is `false`.</span></span>|  
|<span data-ttu-id="33d45-161">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="33d45-161">transactionProtocol</span></span>|<span data-ttu-id="33d45-162">Určuje transakční protokol, který se má použít s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="33d45-162">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="33d45-163">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="33d45-163">Valid values are</span></span><br /><br /> <span data-ttu-id="33d45-164">– OleTransactions</span><span class="sxs-lookup"><span data-stu-id="33d45-164">-   OleTransactions</span></span><br /><span data-ttu-id="33d45-165">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="33d45-165">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="33d45-166">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="33d45-166">The default is OleTransactions.</span></span> <span data-ttu-id="33d45-167">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol> .</span><span class="sxs-lookup"><span data-stu-id="33d45-167">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="33d45-168">Třídy TransferMode</span><span class="sxs-lookup"><span data-stu-id="33d45-168">transferMode</span></span>|<span data-ttu-id="33d45-169"><xref:System.ServiceModel.TransferMode>Hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány nebo jsou požadavkem či odpovědí.</span><span class="sxs-lookup"><span data-stu-id="33d45-169">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="33d45-170">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="33d45-170">Child Elements</span></span>  
  
|<span data-ttu-id="33d45-171">Prvek</span><span class="sxs-lookup"><span data-stu-id="33d45-171">Element</span></span>|<span data-ttu-id="33d45-172">Description</span><span class="sxs-lookup"><span data-stu-id="33d45-172">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-netnamedpipebinding.md)|<span data-ttu-id="33d45-173">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="33d45-173">Defines the security settings for the binding.</span></span> <span data-ttu-id="33d45-174">Tento prvek je typu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement> .</span><span class="sxs-lookup"><span data-stu-id="33d45-174">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="33d45-175">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="33d45-175">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="33d45-176">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="33d45-176">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="33d45-177">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="33d45-177">Parent Elements</span></span>  
  
|<span data-ttu-id="33d45-178">Prvek</span><span class="sxs-lookup"><span data-stu-id="33d45-178">Element</span></span>|<span data-ttu-id="33d45-179">Description</span><span class="sxs-lookup"><span data-stu-id="33d45-179">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="33d45-180">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="33d45-180">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="33d45-181">Poznámky</span><span class="sxs-lookup"><span data-stu-id="33d45-181">Remarks</span></span>  
 <span data-ttu-id="33d45-182">`NetNamedPipeBinding`Vygeneruje ve výchozím nastavení zásobník pro komunikaci za běhu, který používá zabezpečení přenosu, pojmenované kanály pro doručení zprávy a kódování binárních zpráv.</span><span class="sxs-lookup"><span data-stu-id="33d45-182">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="33d45-183">Tato vazba je vhodná volba pro Windows Communication Foundation (WCF) poskytovaná pro komunikaci v počítači.</span><span class="sxs-lookup"><span data-stu-id="33d45-183">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="33d45-184">Podporuje také transakce.</span><span class="sxs-lookup"><span data-stu-id="33d45-184">It also supports transactions.</span></span>  
  
 <span data-ttu-id="33d45-185">Výchozí konfigurace pro `NetNamedPipeBinding` je podobná konfiguraci, kterou poskytuje `NetTcpBinding` , ale je jednodušší, protože implementace služby WCF je určena pouze pro použití v počítači a v důsledku toho je k dispozici méně vydaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="33d45-185">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="33d45-186">Nejvýznamnějším rozdílem je, že `securityMode` nastavení nabízí jenom `None` Možnosti a `Transport` .</span><span class="sxs-lookup"><span data-stu-id="33d45-186">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="33d45-187">Podpora zabezpečení SOAP není zahrnutá možnost.</span><span class="sxs-lookup"><span data-stu-id="33d45-187">SOAP security support is not an included option.</span></span> <span data-ttu-id="33d45-188">Chování zabezpečení lze konfigurovat pomocí volitelného `securityMode` atributu.</span><span class="sxs-lookup"><span data-stu-id="33d45-188">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="33d45-189">Příklad</span><span class="sxs-lookup"><span data-stu-id="33d45-189">Example</span></span>  
 <span data-ttu-id="33d45-190">Následující příklad ukazuje vazbu netNamedPipeBinding, která poskytuje komunikaci mezi procesy ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="33d45-190">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="33d45-191">Pojmenované kanály nefungují napříč počítači.</span><span class="sxs-lookup"><span data-stu-id="33d45-191">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="33d45-192">Vazba je určena v konfiguračních souborech pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="33d45-192">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="33d45-193">Typ vazby je určen v `binding` atributu `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="33d45-193">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="33d45-194">Pokud chcete nakonfigurovat vazbu netNamedPipeBinding a změnit některá její nastavení, musíte definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="33d45-194">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="33d45-195">Koncový bod musí odkazovat na konfiguraci vazby podle názvu s `bindingConfiguration` atributem.</span><span class="sxs-lookup"><span data-stu-id="33d45-195">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="33d45-196">V tomto příkladu má konfigurace vazby název Binding1.</span><span class="sxs-lookup"><span data-stu-id="33d45-196">In this example, the binding configuration is named Binding1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="33d45-197">Viz také</span><span class="sxs-lookup"><span data-stu-id="33d45-197">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [\<binding>](bindings.md)
- [<span data-ttu-id="33d45-198">Vazby</span><span class="sxs-lookup"><span data-stu-id="33d45-198">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="33d45-199">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="33d45-199">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="33d45-200">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="33d45-200">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
