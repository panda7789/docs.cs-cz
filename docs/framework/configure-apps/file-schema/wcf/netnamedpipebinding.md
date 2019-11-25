---
title: <netNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
ms.openlocfilehash: f1aa68bcdda43fd77bee397c079695f7937faa52
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/16/2019
ms.locfileid: "74139465"
---
# <a name="netnamedpipebinding"></a><span data-ttu-id="f8a4d-101">\<netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="f8a4d-101">\<netNamedPipeBinding></span></span>
<span data-ttu-id="f8a4d-102">Definuje vazbu, která je zabezpečená, spolehlivá a optimalizovaná pro komunikaci mezi procesy v počítači.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-102">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="f8a4d-103">Ve výchozím nastavení generuje komunikační zásobník za běhu s WS-ReliableMessaging pro spolehlivost, zabezpečení přenosu pro přenos zabezpečení, pojmenované kanály pro doručení zpráv a kódování binárních zpráv.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-103">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
<span data-ttu-id="f8a4d-104">[ **\<configuration >** ](../configuration-element.md) </span><span class="sxs-lookup"><span data-stu-id="f8a4d-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f8a4d-105">&nbsp; &nbsp;[ **\<system. serviceModel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="f8a4d-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f8a4d-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<vazeb >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f8a4d-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f8a4d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<netNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="f8a4d-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8a4d-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="f8a4d-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f8a4d-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="f8a4d-109">Attributes and Elements</span></span>  
 <span data-ttu-id="f8a4d-110">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f8a4d-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="f8a4d-111">Attributes</span></span>  
  
|<span data-ttu-id="f8a4d-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="f8a4d-112">Attribute</span></span>|<span data-ttu-id="f8a4d-113">Popis</span><span class="sxs-lookup"><span data-stu-id="f8a4d-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f8a4d-114">closeTimeout</span><span class="sxs-lookup"><span data-stu-id="f8a4d-114">closeTimeout</span></span>|<span data-ttu-id="f8a4d-115">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace ukončení.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f8a4d-116">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f8a4d-117">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f8a4d-118">hostNameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="f8a4d-118">hostNameComparisonMode</span></span>|<span data-ttu-id="f8a4d-119">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="f8a4d-120">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode>, který označuje, zda se k dosažení služby při shodě s identifikátorem URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-120">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="f8a4d-121">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-121">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="f8a4d-122">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="f8a4d-122">maxBufferPoolSize</span></span>|<span data-ttu-id="f8a4d-123">Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="f8a4d-124">Výchozí hodnota je 524 288 bajtů (512 \* 1024).</span><span class="sxs-lookup"><span data-stu-id="f8a4d-124">The default is 524,288 bytes (512 \* 1024).</span></span> <span data-ttu-id="f8a4d-125">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="f8a4d-126">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="f8a4d-127">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="f8a4d-128">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="f8a4d-129">Třída</span><span class="sxs-lookup"><span data-stu-id="f8a4d-129">maxBufferSize</span></span>|<span data-ttu-id="f8a4d-130">Celé kladné číslo určující maximální velikost vyrovnávací paměti, která se používá k ukládání zpráv v paměti, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="f8a4d-131">Pokud je vyrovnávací paměť plná, nadbytečná data zůstanou v podkladovém soketu, dokud vyrovnávací paměť neuvolní.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-131">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="f8a4d-132">Tato hodnota nemůže být menší než `maxReceivedMessageSize` atribut.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-132">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="f8a4d-133">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-133">The default is 65536.</span></span> <span data-ttu-id="f8a4d-134">Další informace najdete v tématu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="f8a4d-135">maxConnections</span><span class="sxs-lookup"><span data-stu-id="f8a4d-135">maxConnections</span></span>|<span data-ttu-id="f8a4d-136">Celé číslo, které určuje maximální počet odchozích a příchozích připojení, které služba vytvoří nebo přijme.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-136">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="f8a4d-137">Příchozí a odchozí připojení se počítají na základě zvláštního limitu určeného tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-137">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="f8a4d-138">Příchozí připojení přesahující tento limit se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-138">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="f8a4d-139">Odchozí připojení přesahující limit se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-139">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="f8a4d-140">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-140">The default is 10.</span></span>|  
|<span data-ttu-id="f8a4d-141">maxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="f8a4d-141">maxReceivedMessageSize</span></span>|<span data-ttu-id="f8a4d-142">Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-142">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="f8a4d-143">Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-143">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="f8a4d-144">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-144">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="f8a4d-145">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-145">The default is 65536.</span></span>|  
|<span data-ttu-id="f8a4d-146">name</span><span class="sxs-lookup"><span data-stu-id="f8a4d-146">name</span></span>|<span data-ttu-id="f8a4d-147">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f8a4d-148">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f8a4d-149">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-149">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f8a4d-150">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f8a4d-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="f8a4d-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="f8a4d-151">openTimeout</span></span>|<span data-ttu-id="f8a4d-152">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f8a4d-153">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f8a4d-154">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f8a4d-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="f8a4d-155">receiveTimeout</span></span>|<span data-ttu-id="f8a4d-156">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f8a4d-157">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f8a4d-158">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-158">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="f8a4d-159">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="f8a4d-159">sendTimeout</span></span>|<span data-ttu-id="f8a4d-160">Hodnota <xref:System.TimeSpan>, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f8a4d-161">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f8a4d-162">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="f8a4d-163">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="f8a4d-163">transactionFlow</span></span>|<span data-ttu-id="f8a4d-164">Logická hodnota určující, zda vazba podporuje tok dat WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-164">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="f8a4d-165">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-165">The default is `false`.</span></span>|  
|<span data-ttu-id="f8a4d-166">transactionProtocol</span><span class="sxs-lookup"><span data-stu-id="f8a4d-166">transactionProtocol</span></span>|<span data-ttu-id="f8a4d-167">Určuje transakční protokol, který se má použít s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-167">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="f8a4d-168">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="f8a4d-168">Valid values are</span></span><br /><br /> <span data-ttu-id="f8a4d-169">– OleTransactions</span><span class="sxs-lookup"><span data-stu-id="f8a4d-169">-   OleTransactions</span></span><br /><span data-ttu-id="f8a4d-170">-WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="f8a4d-170">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="f8a4d-171">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-171">The default is OleTransactions.</span></span> <span data-ttu-id="f8a4d-172">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-172">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="f8a4d-173">Třídy TransferMode</span><span class="sxs-lookup"><span data-stu-id="f8a4d-173">transferMode</span></span>|<span data-ttu-id="f8a4d-174">Hodnota <xref:System.ServiceModel.TransferMode>, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány nebo jsou požadavkem či odpovědí.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-174">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f8a4d-175">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="f8a4d-175">Child Elements</span></span>  
  
|<span data-ttu-id="f8a4d-176">Prvek</span><span class="sxs-lookup"><span data-stu-id="f8a4d-176">Element</span></span>|<span data-ttu-id="f8a4d-177">Popis</span><span class="sxs-lookup"><span data-stu-id="f8a4d-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8a4d-178">> zabezpečení \<</span><span class="sxs-lookup"><span data-stu-id="f8a4d-178">\<security></span></span>](security-of-netnamedpipebinding.md)|<span data-ttu-id="f8a4d-179">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="f8a4d-180">Tento prvek je typu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-180">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|<span data-ttu-id="f8a4d-181">[\<readerQuotas >](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span><span class="sxs-lookup"><span data-stu-id="f8a4d-181">[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))</span></span>|<span data-ttu-id="f8a4d-182">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="f8a4d-183">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f8a4d-184">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="f8a4d-184">Parent Elements</span></span>  
  
|<span data-ttu-id="f8a4d-185">Prvek</span><span class="sxs-lookup"><span data-stu-id="f8a4d-185">Element</span></span>|<span data-ttu-id="f8a4d-186">Popis</span><span class="sxs-lookup"><span data-stu-id="f8a4d-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f8a4d-187">vazby\<</span><span class="sxs-lookup"><span data-stu-id="f8a4d-187">\<bindings></span></span>](bindings.md)|<span data-ttu-id="f8a4d-188">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f8a4d-189">Poznámky</span><span class="sxs-lookup"><span data-stu-id="f8a4d-189">Remarks</span></span>  
 <span data-ttu-id="f8a4d-190">`NetNamedPipeBinding` generuje ve výchozím nastavení zásobník pro komunikaci za běhu, který používá zabezpečení přenosu, pojmenované kanály pro doručení zpráv a kódování binárních zpráv.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-190">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="f8a4d-191">Tato vazba je vhodná volba pro Windows Communication Foundation (WCF) poskytovaná pro komunikaci v počítači.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-191">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="f8a4d-192">Podporuje také transakce.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-192">It also supports transactions.</span></span>  
  
 <span data-ttu-id="f8a4d-193">Výchozí konfigurace `NetNamedPipeBinding` je podobná konfiguraci, kterou poskytuje `NetTcpBinding`, ale je jednodušší, protože implementace WCF je určena pouze pro použití v počítači a v důsledku toho je k dispozici méně vydaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-193">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="f8a4d-194">Nejvýznamnějším rozdílem je, že nastavení `securityMode` nabízí jenom možnosti `None` a `Transport`.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-194">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="f8a4d-195">Podpora zabezpečení SOAP není zahrnutá možnost.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-195">SOAP security support is not an included option.</span></span> <span data-ttu-id="f8a4d-196">Chování zabezpečení lze konfigurovat pomocí volitelného atributu `securityMode`.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-196">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8a4d-197">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8a4d-197">Example</span></span>  
 <span data-ttu-id="f8a4d-198">Následující příklad ukazuje vazbu netNamedPipeBinding, která poskytuje komunikaci mezi procesy ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-198">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="f8a4d-199">Pojmenované kanály nefungují napříč počítači.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-199">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="f8a4d-200">Vazba je určena v konfiguračních souborech pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-200">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="f8a4d-201">Typ vazby je určen v atributu `binding` `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-201">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="f8a4d-202">Pokud chcete nakonfigurovat vazbu netNamedPipeBinding a změnit některá její nastavení, musíte definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-202">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="f8a4d-203">Koncový bod musí odkazovat na konfiguraci vazby podle názvu s atributem `bindingConfiguration`.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-203">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="f8a4d-204">V tomto příkladu má konfigurace vazby název Binding1.</span><span class="sxs-lookup"><span data-stu-id="f8a4d-204">In this example, the binding configuration is named Binding1.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f8a4d-205">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8a4d-205">See also</span></span>

- <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- [<span data-ttu-id="f8a4d-206">vazba \<</span><span class="sxs-lookup"><span data-stu-id="f8a4d-206">\<binding></span></span>](bindings.md)
- [<span data-ttu-id="f8a4d-207">Vazby</span><span class="sxs-lookup"><span data-stu-id="f8a4d-207">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f8a4d-208">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="f8a4d-208">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f8a4d-209">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="f8a4d-209">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
