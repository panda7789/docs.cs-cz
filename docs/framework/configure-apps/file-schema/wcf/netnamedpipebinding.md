---
title: "&lt;– netNamedPipeBinding&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 00a8580b-face-47a4-838d-b9fed48e72df
caps.latest.revision: "29"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7a582f009719245483bdfe9192d775347c1f1a29
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltnetnamedpipebindinggt"></a><span data-ttu-id="4bb10-102">&lt;– netNamedPipeBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="4bb10-102">&lt;netNamedPipeBinding&gt;</span></span>
<span data-ttu-id="4bb10-103">Definuje vazbu, která je zabezpečená, spolehlivé, optimalizované pro na počítač křížové proces komunikace.</span><span class="sxs-lookup"><span data-stu-id="4bb10-103">Defines a binding that is secure, reliable, optimized for on-machine cross process communication.</span></span> <span data-ttu-id="4bb10-104">Ve výchozím nastavení vygeneruje zásobníku runtime komunikaci pomocí protokolu WS-ReliableMessaging pro spolehlivost, zabezpečení přenosu pro zabezpečení přenosu, pojmenované kanály pro doručování zpráv a zprávy v binární kódování.</span><span class="sxs-lookup"><span data-stu-id="4bb10-104">By default, it generates a runtime communication stack with WS-ReliableMessaging for reliability, transport security for transfer security, named pipes for message delivery, and binary message encoding.</span></span>  
  
 <span data-ttu-id="4bb10-105">\<systém. ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="4bb10-105">\<system.ServiceModel></span></span>  
<span data-ttu-id="4bb10-106">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="4bb10-106">\<bindings></span></span>  
<span data-ttu-id="4bb10-107">\<– netNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="4bb10-107">\<netNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bb10-108">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bb10-108">Syntax</span></span>  
  
```xml  
<netNamedPipeBinding>  
   <binding   
      closeTimeout="TimeSpan"  
      hostNameComparisonMode="StrongWildCard/Exact/WeakWildcard"  
      maxBufferPoolSize="Integer"  
      maxBufferSize="Integer"  
      maxConnections="Integer"   
      maxReceivedMessageSize="Integer"  
            name="string"  
      openTimeout="TimeSpan"   
      receiveTimeout="TimeSpan"  
      sendTimeout="TimeSpan"  
      transactionFlow="Boolean"  
      transactionProtocol="OleTransactions/WS-AtomicTransactionOctober2004"  
            transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse"  
      <security mode="None/Transport">  
            <transport  protectionLevel="None/Sign/EncryptAndSign" />  
      </security>  
       <readerQuotas             maxArrayLength="Integer"            maxBytesPerRead="Integer"            maxDepth="Integer"             maxNameTableCharCount="Integer"                     maxStringContentLength="Integer" />   </binding>  
</netNamedPipeBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4bb10-109">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="4bb10-109">Attributes and Elements</span></span>  
 <span data-ttu-id="4bb10-110">Následující části popisují nadřazené elementy, atributy a podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4bb10-110">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4bb10-111">Atributy</span><span class="sxs-lookup"><span data-stu-id="4bb10-111">Attributes</span></span>  
  
|<span data-ttu-id="4bb10-112">Atribut</span><span class="sxs-lookup"><span data-stu-id="4bb10-112">Attribute</span></span>|<span data-ttu-id="4bb10-113">Popis</span><span class="sxs-lookup"><span data-stu-id="4bb10-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4bb10-114">Intervalu</span><span class="sxs-lookup"><span data-stu-id="4bb10-114">closeTimeout</span></span>|<span data-ttu-id="4bb10-115">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="4bb10-115">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="4bb10-116">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4bb10-116">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4bb10-117">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4bb10-117">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4bb10-118">hostnameComparisonMode</span><span class="sxs-lookup"><span data-stu-id="4bb10-118">hostnameComparisonMode</span></span>|<span data-ttu-id="4bb10-119">Určuje režim porovnání hostname HTTP použitá k analýze identifikátory URI.</span><span class="sxs-lookup"><span data-stu-id="4bb10-119">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="4bb10-120">Tento atribut je typu `System.ServiceModel.HostnameComparisonMode`, což naznačuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.</span><span class="sxs-lookup"><span data-stu-id="4bb10-120">This attribute is of type `System.ServiceModel.HostnameComparisonMode`, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="4bb10-121">Výchozí hodnota je `StrongWildcard`, který ignoruje název hostitele se shodují.</span><span class="sxs-lookup"><span data-stu-id="4bb10-121">The default value is `StrongWildcard`, which ignores the hostname in the match.</span></span>|  
|<span data-ttu-id="4bb10-122">maxBufferPoolSize</span><span class="sxs-lookup"><span data-stu-id="4bb10-122">maxBufferPoolSize</span></span>|<span data-ttu-id="4bb10-123">Celé číslo, které určuje velikost fondu maximální vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="4bb10-123">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="4bb10-124">Výchozí hodnota je 524,288 bajtů (512 * 1024).</span><span class="sxs-lookup"><span data-stu-id="4bb10-124">The default is 524,288 bytes (512 * 1024).</span></span> <span data-ttu-id="4bb10-125">Mnoho části služby Windows Communication Foundation (WCF) pomocí vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4bb10-125">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="4bb10-126">Vytváření a zničení pokaždé, když se používají vyrovnávací paměti je nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="4bb10-126">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="4bb10-127">S fondy vyrovnávací paměti můžete provést vyrovnávací paměti z fondu, ho použít a po dokončení se vraťte do fondu.</span><span class="sxs-lookup"><span data-stu-id="4bb10-127">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="4bb10-128">Proto je předejde režijní náklady v vytváření a zničení vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4bb10-128">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|<span data-ttu-id="4bb10-129">maxBufferSize</span><span class="sxs-lookup"><span data-stu-id="4bb10-129">maxBufferSize</span></span>|<span data-ttu-id="4bb10-130">Kladné celé číslo, které určuje maximální velikost v bajtech vyrovnávací paměti používané k uložení zpráv v paměti.</span><span class="sxs-lookup"><span data-stu-id="4bb10-130">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span> <span data-ttu-id="4bb10-131">Pokud vyrovnávací paměť je plná, zůstane nadbytečná data v podkladové soketu, dokud znovu místnosti má vyrovnávací paměť.</span><span class="sxs-lookup"><span data-stu-id="4bb10-131">If the buffer is full, excess data remains in the underlying socket until the buffer has room again.</span></span> <span data-ttu-id="4bb10-132">Hodnota nesmí být menší než `maxReceivedMessageSize` atribut.</span><span class="sxs-lookup"><span data-stu-id="4bb10-132">This value cannot be less than `maxReceivedMessageSize` attribute.</span></span> <span data-ttu-id="4bb10-133">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="4bb10-133">The default is 65536.</span></span> <span data-ttu-id="4bb10-134">Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="4bb10-134">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|<span data-ttu-id="4bb10-135">maxConnections</span><span class="sxs-lookup"><span data-stu-id="4bb10-135">maxConnections</span></span>|<span data-ttu-id="4bb10-136">Celé číslo, které určuje maximální počet odchozí a příchozí připojení služby bude vytvoření/přijmout.</span><span class="sxs-lookup"><span data-stu-id="4bb10-136">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="4bb10-137">Příchozí a odchozí připojení, se počítají oproti samostatné limitu určeného tento atribut.</span><span class="sxs-lookup"><span data-stu-id="4bb10-137">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="4bb10-138">Příchozí připojení nad tento limit jsou zařazeny do fronty, dokud nebude k dispozici místo pod limit.</span><span class="sxs-lookup"><span data-stu-id="4bb10-138">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="4bb10-139">Odchozí připojení nad tento limit jsou zařazeny do fronty, dokud nebude k dispozici místo pod limit.</span><span class="sxs-lookup"><span data-stu-id="4bb10-139">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="4bb10-140">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="4bb10-140">The default is 10.</span></span>|  
|<span data-ttu-id="4bb10-141">MaxReceivedMessageSize</span><span class="sxs-lookup"><span data-stu-id="4bb10-141">maxReceivedMessageSize</span></span>|<span data-ttu-id="4bb10-142">Kladné celé číslo, které určuje maximální velikost zprávy, v bajtech, včetně hlavičky, které můžou přijímat na kanál nakonfigurovaným s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="4bb10-142">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="4bb10-143">Odesílatel zprávy překročení tohoto limitu obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="4bb10-143">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="4bb10-144">Příjemce zahodí zprávy a vytvoří položku události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="4bb10-144">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="4bb10-145">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="4bb10-145">The default is 65536.</span></span>|  
|<span data-ttu-id="4bb10-146">name</span><span class="sxs-lookup"><span data-stu-id="4bb10-146">name</span></span>|<span data-ttu-id="4bb10-147">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="4bb10-147">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="4bb10-148">Tato hodnota musí být jedinečný, protože je používán jako identifikaci pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="4bb10-148">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="4bb10-149">Počínaje [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], vazby a chování nemusí mít název.</span><span class="sxs-lookup"><span data-stu-id="4bb10-149">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="4bb10-150">Další informace o výchozí konfigurace a nameless vazby a chování najdete v tématu [zjednodušená konfigurace](../../../../../docs/framework/wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="4bb10-150">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|<span data-ttu-id="4bb10-151">openTimeout</span><span class="sxs-lookup"><span data-stu-id="4bb10-151">openTimeout</span></span>|<span data-ttu-id="4bb10-152">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro otevřete na dokončení operace.</span><span class="sxs-lookup"><span data-stu-id="4bb10-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="4bb10-153">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4bb10-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4bb10-154">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4bb10-154">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4bb10-155">receiveTimeout</span><span class="sxs-lookup"><span data-stu-id="4bb10-155">receiveTimeout</span></span>|<span data-ttu-id="4bb10-156">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro na dokončení operace příjmu.</span><span class="sxs-lookup"><span data-stu-id="4bb10-156">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="4bb10-157">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4bb10-157">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4bb10-158">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="4bb10-158">The default is 00:10:00.</span></span>|  
|<span data-ttu-id="4bb10-159">sendTimeout</span><span class="sxs-lookup"><span data-stu-id="4bb10-159">sendTimeout</span></span>|<span data-ttu-id="4bb10-160">A <xref:System.TimeSpan> hodnotu, která určuje interval čas zadaný pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="4bb10-160">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="4bb10-161">Tato hodnota by měla být větší než nebo rovna hodnotě <xref:System.TimeSpan.Zero>.</span><span class="sxs-lookup"><span data-stu-id="4bb10-161">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="4bb10-162">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="4bb10-162">The default is 00:01:00.</span></span>|  
|<span data-ttu-id="4bb10-163">transactionFlow</span><span class="sxs-lookup"><span data-stu-id="4bb10-163">transactionFlow</span></span>|<span data-ttu-id="4bb10-164">Logická hodnota, která určuje, zda vazby podporuje průchodu WS-transakce.</span><span class="sxs-lookup"><span data-stu-id="4bb10-164">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="4bb10-165">Výchozí hodnota je `false`.</span><span class="sxs-lookup"><span data-stu-id="4bb10-165">The default is `false`.</span></span>|  
|<span data-ttu-id="4bb10-166">TransactionProtocol</span><span class="sxs-lookup"><span data-stu-id="4bb10-166">transactionProtocol</span></span>|<span data-ttu-id="4bb10-167">Určuje protokol transakce, který se má použít s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="4bb10-167">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="4bb10-168">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="4bb10-168">Valid values are</span></span><br /><br /> <span data-ttu-id="4bb10-169">-OleTransactions</span><span class="sxs-lookup"><span data-stu-id="4bb10-169">-   OleTransactions</span></span><br /><span data-ttu-id="4bb10-170">WS-AtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="4bb10-170">-   WS-AtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="4bb10-171">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="4bb10-171">The default is OleTransactions.</span></span> <span data-ttu-id="4bb10-172">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol>.</span><span class="sxs-lookup"><span data-stu-id="4bb10-172">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|<span data-ttu-id="4bb10-173">transferMode</span><span class="sxs-lookup"><span data-stu-id="4bb10-173">transferMode</span></span>|<span data-ttu-id="4bb10-174">A <xref:System.ServiceModel.TransferMode> hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo prostřednictvím datového proudu nebo požadavku nebo odpovědi.</span><span class="sxs-lookup"><span data-stu-id="4bb10-174">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4bb10-175">Podřízené elementy</span><span class="sxs-lookup"><span data-stu-id="4bb10-175">Child Elements</span></span>  
  
|<span data-ttu-id="4bb10-176">Prvek</span><span class="sxs-lookup"><span data-stu-id="4bb10-176">Element</span></span>|<span data-ttu-id="4bb10-177">Popis</span><span class="sxs-lookup"><span data-stu-id="4bb10-177">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4bb10-178">\<zabezpečení ></span><span class="sxs-lookup"><span data-stu-id="4bb10-178">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-netnamedpipebinding.md)|<span data-ttu-id="4bb10-179">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="4bb10-179">Defines the security settings for the binding.</span></span> <span data-ttu-id="4bb10-180">Tento element je typu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span><span class="sxs-lookup"><span data-stu-id="4bb10-180">This element is of type <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>.</span></span>|  
|[<span data-ttu-id="4bb10-181">\<readerQuotas ></span><span class="sxs-lookup"><span data-stu-id="4bb10-181">\<readerQuotas></span></span>](http://msdn.microsoft.com/library/3e5e42ff-cef8-478f-bf14-034449239bfd)|<span data-ttu-id="4bb10-182">Definuje omezení na složitosti protokolu SOAP zprávy, které lze zpracovat koncovými body, které jsou konfigurovány pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="4bb10-182">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="4bb10-183">Tento element je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span><span class="sxs-lookup"><span data-stu-id="4bb10-183">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4bb10-184">Nadřazené elementy</span><span class="sxs-lookup"><span data-stu-id="4bb10-184">Parent Elements</span></span>  
  
|<span data-ttu-id="4bb10-185">Prvek</span><span class="sxs-lookup"><span data-stu-id="4bb10-185">Element</span></span>|<span data-ttu-id="4bb10-186">Popis</span><span class="sxs-lookup"><span data-stu-id="4bb10-186">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4bb10-187">\<vazby ></span><span class="sxs-lookup"><span data-stu-id="4bb10-187">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="4bb10-188">Tento prvek obsahuje kolekci standardní a vlastní vazby.</span><span class="sxs-lookup"><span data-stu-id="4bb10-188">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bb10-189">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4bb10-189">Remarks</span></span>  
 <span data-ttu-id="4bb10-190">`NetNamedPipeBinding` Generuje běhu komunikačního balíku ve výchozím nastavení, která používá zabezpečení přenosu pojmenované kanály pro doručování zpráv a zprávy v binární kódování.</span><span class="sxs-lookup"><span data-stu-id="4bb10-190">The `NetNamedPipeBinding` generates a run-time communication stack by default, which uses transport security, named pipes for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="4bb10-191">Tato vazba je vhodné Windows Communication Foundation (WCF) poskytované systémem volbou pro komunikaci ve počítače.</span><span class="sxs-lookup"><span data-stu-id="4bb10-191">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for on-machine communication.</span></span> <span data-ttu-id="4bb10-192">Také podporuje transakce.</span><span class="sxs-lookup"><span data-stu-id="4bb10-192">It also supports transactions.</span></span>  
  
 <span data-ttu-id="4bb10-193">Výchozí konfiguraci pro `NetNamedPipeBinding` je podobná konfigurace poskytované `NetTcpBinding`, ale je jednodušší, protože implementace WCF je určená jenom pro použití ve počítač a v důsledku toho jsou méně zveřejněné funkce.</span><span class="sxs-lookup"><span data-stu-id="4bb10-193">The default configuration for the `NetNamedPipeBinding` is similar to the configuration provided by the `NetTcpBinding`, but it is simpler because the WCF implementation is only meant for on-machine use and consequently there are fewer exposed features.</span></span> <span data-ttu-id="4bb10-194">Nejdůležitější rozdíl je, že `securityMode` nastavení pouze nabídky `None` a `Transport` možnosti.</span><span class="sxs-lookup"><span data-stu-id="4bb10-194">The most notable difference is that the `securityMode` setting only offers the `None` and `Transport` options.</span></span> <span data-ttu-id="4bb10-195">Podpora protokolu SOAP zabezpečení není zahrnuta možnost.</span><span class="sxs-lookup"><span data-stu-id="4bb10-195">SOAP security support is not an included option.</span></span> <span data-ttu-id="4bb10-196">Chování zabezpečení je možné konfigurovat pomocí volitelné `securityMode` atribut.</span><span class="sxs-lookup"><span data-stu-id="4bb10-196">The security behavior is configurable using the optional `securityMode` attribute.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bb10-197">Příklad</span><span class="sxs-lookup"><span data-stu-id="4bb10-197">Example</span></span>  
 <span data-ttu-id="4bb10-198">Následující příklad ukazuje – netNamedPipeBinding vazby, která poskytuje komunikaci mezi procesy ve stejném počítači.</span><span class="sxs-lookup"><span data-stu-id="4bb10-198">The following example demonstrates the netNamedPipeBinding binding, which provides cross-process communication on the same machine.</span></span> <span data-ttu-id="4bb10-199">Pojmenované kanály nefungují mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="4bb10-199">Named pipes do not work across machines.</span></span>  
  
 <span data-ttu-id="4bb10-200">Vazba je zadána v konfiguračních souborech pro klienta a služby.</span><span class="sxs-lookup"><span data-stu-id="4bb10-200">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="4bb10-201">Typ vazby je zadán v `binding` atribut `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="4bb10-201">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="4bb10-202">Pokud chcete nakonfigurovat – netNamedPipeBinding vazby a některá z jeho nastavení změnit, je nutné zadat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="4bb10-202">If you want to configure the netNamedPipeBinding binding and change some of its settings, you must define a binding configuration.</span></span> <span data-ttu-id="4bb10-203">Koncový bod musí odkazovat Konfigurace vazeb podle názvu s `bindingConfiguration` atribut.</span><span class="sxs-lookup"><span data-stu-id="4bb10-203">The endpoint must reference the binding configuration by name with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="4bb10-204">V tomto příkladu je vazba konfigurace s názvem Binding1.</span><span class="sxs-lookup"><span data-stu-id="4bb10-204">In this example, the binding configuration is named Binding1.</span></span>  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
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
        <binding   
                 closeTimeout="00:01:00"  
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
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4bb10-205">Viz také</span><span class="sxs-lookup"><span data-stu-id="4bb10-205">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement>  
 <xref:System.ServiceModel.NetNamedPipeBinding>  
 [<span data-ttu-id="4bb10-206">\<Vazba ></span><span class="sxs-lookup"><span data-stu-id="4bb10-206">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)  
 [<span data-ttu-id="4bb10-207">Vazby</span><span class="sxs-lookup"><span data-stu-id="4bb10-207">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="4bb10-208">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="4bb10-208">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="4bb10-209">Používání vazeb ke konfiguraci služby Windows Communication Foundation a klienty</span><span class="sxs-lookup"><span data-stu-id="4bb10-209">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)
