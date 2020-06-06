---
title: <netTcpBinding>
ms.date: 03/30/2017
helpviewer_keywords:
- netTcpBinding Element
ms.assetid: 5c5104a7-8754-4335-8233-46a45322503e
ms.openlocfilehash: c43c141093c8287adb6d5a841a43ac893deefccd
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "74139339"
---
# \<netTcpBinding>

<span data-ttu-id="3949e-101">Určuje zabezpečenou, spolehlivou a optimalizovanou vazbu vhodnou pro komunikaci mezi počítači.</span><span class="sxs-lookup"><span data-stu-id="3949e-101">Specifies a secure, reliable, optimized binding suitable for cross-machine communication.</span></span> <span data-ttu-id="3949e-102">Ve výchozím nastavení vygeneruje komunikační zásobník za běhu s zabezpečením systému Windows za účelem zabezpečení a ověřování zpráv, TCP pro doručování zpráv a kódování binárních zpráv.</span><span class="sxs-lookup"><span data-stu-id="3949e-102">By default, it generates a runtime communication stack with Windows Security for message security and authentication, TCP for message delivery, and binary message encoding.</span></span>

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<netTcpBinding>**  
  
## <a name="syntax"></a><span data-ttu-id="3949e-103">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="3949e-103">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3949e-104">Atributy a elementy</span><span class="sxs-lookup"><span data-stu-id="3949e-104">Attributes and elements</span></span>

<span data-ttu-id="3949e-105">Následující části popisují atributy, podřízené prvky a nadřazené prvky.</span><span class="sxs-lookup"><span data-stu-id="3949e-105">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3949e-106">Atributy</span><span class="sxs-lookup"><span data-stu-id="3949e-106">Attributes</span></span>  
  
|<span data-ttu-id="3949e-107">Atribut</span><span class="sxs-lookup"><span data-stu-id="3949e-107">Attribute</span></span>|<span data-ttu-id="3949e-108">Popis</span><span class="sxs-lookup"><span data-stu-id="3949e-108">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="3949e-109"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace uzavření.</span><span class="sxs-lookup"><span data-stu-id="3949e-109">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="3949e-110">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="3949e-110">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3949e-111">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3949e-111">The default is 00:01:00.</span></span>|  
|`hostNameComparisonMode`|<span data-ttu-id="3949e-112">Určuje režim porovnání názvu hostitele HTTP, který se používá k analýze identifikátorů URI.</span><span class="sxs-lookup"><span data-stu-id="3949e-112">Specifies the HTTP hostname comparison mode used to parse URIs.</span></span> <span data-ttu-id="3949e-113">Tento atribut je typu <xref:System.ServiceModel.HostNameComparisonMode> , který označuje, zda je název hostitele použit pro dosažení služby při shodě s identifikátorem URI.</span><span class="sxs-lookup"><span data-stu-id="3949e-113">This attribute is of type <xref:System.ServiceModel.HostNameComparisonMode>, which indicates whether the hostname is used to reach the service when matching on the URI.</span></span> <span data-ttu-id="3949e-114">Výchozí hodnota je <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard> , která ignoruje název hostitele v shodě.</span><span class="sxs-lookup"><span data-stu-id="3949e-114">The default value is <xref:System.ServiceModel.HostNameComparisonMode.StrongWildcard>, which ignores the hostname in the match.</span></span>|  
|`listenBacklog`|<span data-ttu-id="3949e-115">Celé kladné číslo určující maximální počet kanálů, které čekají na přijetí na naslouchací službě.</span><span class="sxs-lookup"><span data-stu-id="3949e-115">A positive integer that specifies the maximum number of channels waiting to be accepted on the listener.</span></span> <span data-ttu-id="3949e-116">Překročení tohoto limitu se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.</span><span class="sxs-lookup"><span data-stu-id="3949e-116">Connections in excess of this limit are queued until space below the limit becomes available.</span></span> <span data-ttu-id="3949e-117">`connectionTimeout`Atribut omezuje dobu, po kterou bude klient čekat na připojení, než dojde k výjimce připojení.</span><span class="sxs-lookup"><span data-stu-id="3949e-117">The `connectionTimeout` attribute limits the time a client will wait to be connected before throwing a connection exception.</span></span> <span data-ttu-id="3949e-118">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="3949e-118">The default is 10.</span></span>|  
|`maxBufferPoolSize`|<span data-ttu-id="3949e-119">Celé číslo, které určuje maximální velikost fondu vyrovnávací paměti pro tuto vazbu.</span><span class="sxs-lookup"><span data-stu-id="3949e-119">An integer that specifies the maximum buffer pool size for this binding.</span></span> <span data-ttu-id="3949e-120">Výchozí hodnota je 512 × 1024 bajtů.</span><span class="sxs-lookup"><span data-stu-id="3949e-120">The default is 512 \* 1024 bytes.</span></span> <span data-ttu-id="3949e-121">Mnoho částí Windows Communication Foundation (WCF) používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="3949e-121">Many parts of Windows Communication Foundation (WCF) use buffers.</span></span> <span data-ttu-id="3949e-122">Vytváření a zničení vyrovnávacích pamětí pokaždé, když se používají, jsou nákladné a uvolňování paměti pro vyrovnávací paměti je také nákladné.</span><span class="sxs-lookup"><span data-stu-id="3949e-122">Creating and destroying buffers each time they are used is expensive, and garbage collection for buffers is also expensive.</span></span> <span data-ttu-id="3949e-123">Pomocí fondů vyrovnávacích pamětí můžete z fondu získat vyrovnávací paměť, použít ji a až budete hotovi, vrátit ji do fondu.</span><span class="sxs-lookup"><span data-stu-id="3949e-123">With buffer pools, you can take a buffer from the pool, use it, and return it to the pool once you are done.</span></span> <span data-ttu-id="3949e-124">Proto se zabrání režie v vytváření a zničení vyrovnávacích pamětí.</span><span class="sxs-lookup"><span data-stu-id="3949e-124">Thus the overhead in creating and destroying buffers is avoided.</span></span>|  
|`maxBufferSize`|<span data-ttu-id="3949e-125">Celé kladné číslo určující maximální velikost vyrovnávací paměti, která se používá k ukládání zpráv v paměti, v bajtech.</span><span class="sxs-lookup"><span data-stu-id="3949e-125">A positive integer that specifies the maximum size, in bytes, of the buffer used to store messages in memory.</span></span><br /><br /> <span data-ttu-id="3949e-126">Pokud se `transferMode` atribut rovná `Buffered` , tento atribut by měl být roven `maxReceivedMessageSize` hodnotě atributu.</span><span class="sxs-lookup"><span data-stu-id="3949e-126">If the `transferMode` attribute equals to `Buffered`, this attribute should be equal to the `maxReceivedMessageSize` attribute value.</span></span><br /><br /> <span data-ttu-id="3949e-127">Pokud se `transferMode` atribut rovná `Streamed` , tento atribut nemůže být větší než `maxReceivedMessageSize` hodnota atributu a měla by být alespoň velikost záhlaví.</span><span class="sxs-lookup"><span data-stu-id="3949e-127">If the `transferMode` attribute equals to `Streamed`, this attribute cannot be more than the `maxReceivedMessageSize` attribute value, and should be at least the size of the headers.</span></span><br /><br /> <span data-ttu-id="3949e-128">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="3949e-128">The default is 65536.</span></span> <span data-ttu-id="3949e-129">Další informace naleznete v tématu <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="3949e-129">For more information, see <xref:System.ServiceModel.Configuration.NetNamedPipeBindingElement.MaxBufferSize%2A>.</span></span>|  
|`maxConnections`|<span data-ttu-id="3949e-130">Celé číslo, které určuje maximální počet odchozích a příchozích připojení, které služba vytvoří nebo přijme.</span><span class="sxs-lookup"><span data-stu-id="3949e-130">An integer that specifies the maximum number of outbound and inbound connections the service will create/accept.</span></span> <span data-ttu-id="3949e-131">Příchozí a odchozí připojení se počítají na základě zvláštního limitu určeného tímto atributem.</span><span class="sxs-lookup"><span data-stu-id="3949e-131">Incoming and outgoing connections are counted against a separate limit specified by this attribute.</span></span><br /><br /> <span data-ttu-id="3949e-132">Příchozí připojení přesahující tento limit se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.</span><span class="sxs-lookup"><span data-stu-id="3949e-132">Inbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="3949e-133">Odchozí připojení přesahující limit se zařadí do fronty, dokud nebude k dispozici mezera pod limitem.</span><span class="sxs-lookup"><span data-stu-id="3949e-133">Outbound connections in excess of the limit are queued until a space below the limit becomes available.</span></span><br /><br /> <span data-ttu-id="3949e-134">Výchozí hodnota je 10.</span><span class="sxs-lookup"><span data-stu-id="3949e-134">The default is 10.</span></span>|  
|`maxReceivedMessageSize`|<span data-ttu-id="3949e-135">Celé kladné číslo určující maximální velikost zprávy v bajtech, včetně hlaviček, které lze přijmout na kanálu nakonfigurovaném pomocí této vazby.</span><span class="sxs-lookup"><span data-stu-id="3949e-135">A positive integer that specifies the maximum message size, in bytes, including headers, that can be received on a channel configured with this binding.</span></span> <span data-ttu-id="3949e-136">Odesílateli zprávy překračující tento limit obdrží chybu protokolu SOAP.</span><span class="sxs-lookup"><span data-stu-id="3949e-136">The sender of a message exceeding this limit will receive a SOAP fault.</span></span> <span data-ttu-id="3949e-137">Příjemce zprávu zruší a vytvoří záznam události v protokolu trasování.</span><span class="sxs-lookup"><span data-stu-id="3949e-137">The receiver drops the message and creates an entry of the event in the trace log.</span></span> <span data-ttu-id="3949e-138">Výchozí hodnota je 65536.</span><span class="sxs-lookup"><span data-stu-id="3949e-138">The default is 65536.</span></span>|  
|`name`|<span data-ttu-id="3949e-139">Řetězec, který obsahuje název konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="3949e-139">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="3949e-140">Tato hodnota by měla být jedinečná, protože se používá jako identifikace vazby.</span><span class="sxs-lookup"><span data-stu-id="3949e-140">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="3949e-141">Počínaje .NET Framework 4 nejsou vazby a chování nutné mít název.</span><span class="sxs-lookup"><span data-stu-id="3949e-141">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="3949e-142">Další informace o výchozích konfiguracích a Nameless vazbách a chování najdete v tématu [zjednodušená konfigurace](../../../wcf/simplified-configuration.md) a [zjednodušená konfigurace pro služby WCF](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="3949e-142">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="3949e-143"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace otevření.</span><span class="sxs-lookup"><span data-stu-id="3949e-143">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="3949e-144">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="3949e-144">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3949e-145">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3949e-145">The default is 00:01:00.</span></span>|  
|`portSharingEnabled`|<span data-ttu-id="3949e-146">Logická hodnota, která určuje, zda je pro toto připojení povoleno sdílení portu TCP.</span><span class="sxs-lookup"><span data-stu-id="3949e-146">A Boolean value that specifies whether TCP port sharing is enabled for this connection.</span></span> <span data-ttu-id="3949e-147">V takovém případě `false` Každá vazba používá vlastní výhradní port.</span><span class="sxs-lookup"><span data-stu-id="3949e-147">If this is `false`, each binding uses its own exclusive port.</span></span> <span data-ttu-id="3949e-148">Toto nastavení je relevantní pouze pro služby, protože nejsou ovlivněni klienti.</span><span class="sxs-lookup"><span data-stu-id="3949e-148">This setting is relevant only to services, because clients are not affected.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="3949e-149"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace Receive.</span><span class="sxs-lookup"><span data-stu-id="3949e-149">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="3949e-150">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="3949e-150">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3949e-151">Výchozí hodnota je 00:10:00.</span><span class="sxs-lookup"><span data-stu-id="3949e-151">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="3949e-152"><xref:System.TimeSpan>Hodnota, která určuje časový interval poskytnutý pro dokončení operace odeslání.</span><span class="sxs-lookup"><span data-stu-id="3949e-152">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="3949e-153">Tato hodnota by měla být větší nebo rovna <xref:System.TimeSpan.Zero> .</span><span class="sxs-lookup"><span data-stu-id="3949e-153">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="3949e-154">Výchozí hodnota je 00:01:00.</span><span class="sxs-lookup"><span data-stu-id="3949e-154">The default is 00:01:00.</span></span>|  
|`transactionFlow`|<span data-ttu-id="3949e-155">Logická hodnota určující, zda vazba podporuje tok dat WS-Transactions.</span><span class="sxs-lookup"><span data-stu-id="3949e-155">A Boolean value that specifies whether the binding supports flowing WS-Transactions.</span></span> <span data-ttu-id="3949e-156">Výchozí formát je `false`.</span><span class="sxs-lookup"><span data-stu-id="3949e-156">The default is `false`.</span></span>|  
|`transactionProtocol`|<span data-ttu-id="3949e-157">Určuje transakční protokol, který se má použít s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="3949e-157">Specifies the transaction protocol to be used with this binding.</span></span> <span data-ttu-id="3949e-158">Platné hodnoty jsou</span><span class="sxs-lookup"><span data-stu-id="3949e-158">Valid values are</span></span><br /><br /> <span data-ttu-id="3949e-159">– OleTransactions</span><span class="sxs-lookup"><span data-stu-id="3949e-159">-   OleTransactions</span></span><br /><span data-ttu-id="3949e-160">- WSAtomicTransactionOctober2004</span><span class="sxs-lookup"><span data-stu-id="3949e-160">-   WSAtomicTransactionOctober2004</span></span><br /><br /> <span data-ttu-id="3949e-161">Výchozí hodnota je OleTransactions.</span><span class="sxs-lookup"><span data-stu-id="3949e-161">The default is OleTransactions.</span></span> <span data-ttu-id="3949e-162">Tento atribut je typu <xref:System.ServiceModel.TransactionProtocol> .</span><span class="sxs-lookup"><span data-stu-id="3949e-162">This attribute is of type <xref:System.ServiceModel.TransactionProtocol>.</span></span>|  
|`transferMode`|<span data-ttu-id="3949e-163"><xref:System.ServiceModel.TransferMode>Hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo zpracovány nebo jsou požadavkem či odpovědí.</span><span class="sxs-lookup"><span data-stu-id="3949e-163">A <xref:System.ServiceModel.TransferMode> value that specifies whether messages are buffered or streamed or a request or response.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3949e-164">Podřízené prvky</span><span class="sxs-lookup"><span data-stu-id="3949e-164">Child elements</span></span>  
  
|<span data-ttu-id="3949e-165">Prvek</span><span class="sxs-lookup"><span data-stu-id="3949e-165">Element</span></span>|<span data-ttu-id="3949e-166">Description</span><span class="sxs-lookup"><span data-stu-id="3949e-166">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-nettcpbinding.md)|<span data-ttu-id="3949e-167">Definuje nastavení zabezpečení pro vazbu.</span><span class="sxs-lookup"><span data-stu-id="3949e-167">Defines the security settings for the binding.</span></span> <span data-ttu-id="3949e-168">Tento prvek je typu <xref:System.ServiceModel.Configuration.NetTcpSecurityElement> .</span><span class="sxs-lookup"><span data-stu-id="3949e-168">This element is of type <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>.</span></span>|  
|[\<readerQuotas>](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ms731325(v=vs.100))|<span data-ttu-id="3949e-169">Definuje omezení složitosti zpráv SOAP, které mohou být zpracovány koncovými body nakonfigurovanými s touto vazbou.</span><span class="sxs-lookup"><span data-stu-id="3949e-169">Defines the constraints on the complexity of SOAP messages that can be processed by endpoints configured with this binding.</span></span> <span data-ttu-id="3949e-170">Tento prvek je typu <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement> .</span><span class="sxs-lookup"><span data-stu-id="3949e-170">This element is of type <xref:System.ServiceModel.Configuration.XmlDictionaryReaderQuotasElement>.</span></span>|  
|[\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))|<span data-ttu-id="3949e-171">Určuje, jestli se mezi koncovými body kanálu navázaly spolehlivé relace.</span><span class="sxs-lookup"><span data-stu-id="3949e-171">Specifies if reliable sessions are established between channel endpoints.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3949e-172">Nadřazené prvky</span><span class="sxs-lookup"><span data-stu-id="3949e-172">Parent elements</span></span>  
  
|<span data-ttu-id="3949e-173">Prvek</span><span class="sxs-lookup"><span data-stu-id="3949e-173">Element</span></span>|<span data-ttu-id="3949e-174">Description</span><span class="sxs-lookup"><span data-stu-id="3949e-174">Description</span></span>|  
|-------------|-----------------|  
|[\<bindings>](bindings.md)|<span data-ttu-id="3949e-175">Tento prvek obsahuje kolekci standardních a vlastních vazeb.</span><span class="sxs-lookup"><span data-stu-id="3949e-175">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3949e-176">Poznámky</span><span class="sxs-lookup"><span data-stu-id="3949e-176">Remarks</span></span>

<span data-ttu-id="3949e-177">Tato vazba generuje ve výchozím nastavení zásobník pro komunikaci za běhu, který používá zabezpečení přenosu, TCP pro doručování zpráv a binární kódování zpráv.</span><span class="sxs-lookup"><span data-stu-id="3949e-177">This binding generates a run-time communication stack by default, which uses transport security, TCP for message delivery, and a binary message encoding.</span></span> <span data-ttu-id="3949e-178">Tato vazba je vhodným uživatelem určeným Windows Communication Foundation (WCF) pro komunikaci přes intranet.</span><span class="sxs-lookup"><span data-stu-id="3949e-178">This binding is an appropriate Windows Communication Foundation (WCF) system-provided choice for communicating over an Intranet.</span></span>  
  
 <span data-ttu-id="3949e-179">Výchozí konfigurace pro `netTcpBinding` je rychlejší než konfigurace, kterou poskytuje `wsHttpBinding` , ale je určena pouze pro komunikaci WCF.</span><span class="sxs-lookup"><span data-stu-id="3949e-179">The default configuration for the `netTcpBinding` is faster than the configuration provided by the `wsHttpBinding`, but it is intended only for WCF communication.</span></span> <span data-ttu-id="3949e-180">Chování zabezpečení lze konfigurovat pomocí volitelného `securityMode` atributu.</span><span class="sxs-lookup"><span data-stu-id="3949e-180">The security behavior is configurable using the optional `securityMode` attribute.</span></span> <span data-ttu-id="3949e-181">Použití WS-ReliableMessaging se dá konfigurovat pomocí volitelného `reliableSessionEnabled` atributu.</span><span class="sxs-lookup"><span data-stu-id="3949e-181">The use of WS-ReliableMessaging is configurable using the optional `reliableSessionEnabled` attribute.</span></span> <span data-ttu-id="3949e-182">Ale spolehlivé zasílání zpráv je ve výchozím nastavení vypnuté.</span><span class="sxs-lookup"><span data-stu-id="3949e-182">But reliable messaging is off by default.</span></span> <span data-ttu-id="3949e-183">Obecně platí, že vazby poskytované systémem HTTP, jako `wsHttpBinding` jsou a `basicHttpBinding` jsou nakonfigurovány tak, aby ve výchozím nastavení zapnuly hodnoty, zatímco `netTcpBinding` vazba vypíná ve výchozím nastavení, aby bylo možné získat podporu, například pro jednu ze specifikací WS-\*.</span><span class="sxs-lookup"><span data-stu-id="3949e-183">More generally, the HTTP system-provided bindings such as `wsHttpBinding` and `basicHttpBinding` are configured to turn things on by default, whereas the `netTcpBinding` binding turns things off by default so that you have to opt-in to get support, for example, for one of the WS-\* specifications.</span></span> <span data-ttu-id="3949e-184">To znamená, že výchozí konfigurace pro protokol TCP je rychlejší při výměně zpráv mezi koncovými body, než jsou nastavené pro vazby HTTP ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="3949e-184">This means that the default configuration for TCP is faster at exchanging messages between endpoints than those configured for the HTTP bindings by default.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3949e-185">Příklad</span><span class="sxs-lookup"><span data-stu-id="3949e-185">Example</span></span>

<span data-ttu-id="3949e-186">Vazba je určena v konfiguračních souborech pro klienta a službu.</span><span class="sxs-lookup"><span data-stu-id="3949e-186">The binding is specified in the configuration files for the client and service.</span></span> <span data-ttu-id="3949e-187">Typ vazby je určen v `binding` atributu `<endpoint>` elementu.</span><span class="sxs-lookup"><span data-stu-id="3949e-187">The binding type is specified in the `binding` attribute of the `<endpoint>` element.</span></span> <span data-ttu-id="3949e-188">Pokud chcete nakonfigurovat vazbu netTcpBinding a změnit některá její nastavení, je nutné definovat konfiguraci vazby.</span><span class="sxs-lookup"><span data-stu-id="3949e-188">If you want to configure the netTcpBinding binding and change some of its settings, it is necessary to define a binding configuration.</span></span> <span data-ttu-id="3949e-189">Koncový bod musí odkazovat na konfiguraci vazby s `bindingConfiguration` atributem.</span><span class="sxs-lookup"><span data-stu-id="3949e-189">The endpoint must reference the binding configuration with a `bindingConfiguration` attribute.</span></span> <span data-ttu-id="3949e-190">V následujícím příkladu je definována konfigurace vazby.</span><span class="sxs-lookup"><span data-stu-id="3949e-190">In the following example, a binding configuration is defined.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3949e-191">Viz také</span><span class="sxs-lookup"><span data-stu-id="3949e-191">See also</span></span>

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement>
- [<span data-ttu-id="3949e-192">Vazby</span><span class="sxs-lookup"><span data-stu-id="3949e-192">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="3949e-193">Konfigurace vazeb poskytovaných systémem</span><span class="sxs-lookup"><span data-stu-id="3949e-193">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="3949e-194">Používání vazeb ke konfiguraci služeb a klientů</span><span class="sxs-lookup"><span data-stu-id="3949e-194">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
