---
title: "Šíření"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 17b20b76d4932272c8e2a9e26603dc8483505242
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="propagation"></a><span data-ttu-id="a77fa-102">Šíření</span><span class="sxs-lookup"><span data-stu-id="a77fa-102">Propagation</span></span>
<span data-ttu-id="a77fa-103">Toto téma popisuje rozšíření aktivity v [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] trasování modelu.</span><span class="sxs-lookup"><span data-stu-id="a77fa-103">This topic describes activity propagation in the [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] tracing model.</span></span>  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a><span data-ttu-id="a77fa-104">Pomocí šíření pro vazbu mezi aktivitami v koncových bodů</span><span class="sxs-lookup"><span data-stu-id="a77fa-104">Using Propagation to Correlate Activities Across Endpoints</span></span>  
 <span data-ttu-id="a77fa-105">Šíření poskytuje možnosti pro že uživatele s přímou souvislost chyby trasování pro stejnou jednotku zpracování napříč koncovými body aplikace, například požadavek.</span><span class="sxs-lookup"><span data-stu-id="a77fa-105">Propagation provides the user with direct correlation of error traces for the same unit of processing across application endpoints, for example, a request.</span></span> <span data-ttu-id="a77fa-106">Vygenerované v různých koncové body pro stejnou jednotku zpracování chyby jsou seskupené do stejné aktivity, i mezi doménami aplikací.</span><span class="sxs-lookup"><span data-stu-id="a77fa-106">Errors emitted at different endpoints for the same unit of processing are grouped in the same activity, even across application domains.</span></span> <span data-ttu-id="a77fa-107">To se provádí prostřednictvím šíření ID aktivity v záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="a77fa-107">This is done through propagation of the activity ID in the message headers.</span></span> <span data-ttu-id="a77fa-108">Pokud klient časového limitu z důvodu vnitřní chyby v serveru, i chyby vypadat do stejné aktivity pro přímé korelace.</span><span class="sxs-lookup"><span data-stu-id="a77fa-108">Therefore, if a client times out because of an internal error in the server, both errors appear in the same activity for direct correlation.</span></span>  
  
 <span data-ttu-id="a77fa-109">Chcete-li to provést, použijte `ActivityTracing` nastavení, jak je předvedeno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a77fa-109">To do this, use the `ActivityTracing` setting as demonstrated in the previous example.</span></span> <span data-ttu-id="a77fa-110">Kromě toho nastavit `propagateActivity` atribut pro `System.ServiceModel` zdroj trasování na všechny koncové body.</span><span class="sxs-lookup"><span data-stu-id="a77fa-110">In addition, set the `propagateActivity` attribute for the `System.ServiceModel` trace source at all endpoints.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 <span data-ttu-id="a77fa-111">Konfigurovat funkci, která způsobí, že je rozšíření aktivity [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] přidat hlavičku do odchozí zprávy, které obsahuje ID aktivity na TLS.</span><span class="sxs-lookup"><span data-stu-id="a77fa-111">Activity propagation is a configurable capability that causes [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] to add a header to outbound messages, which includes the activity ID on the TLS.</span></span> <span data-ttu-id="a77fa-112">To uvedete na následné trasování na straně serveru, jsme mohou korelovat aktivity klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="a77fa-112">By including this on subsequent traces on the server side, we can correlate client and server activities.</span></span>  
  
## <a name="propagation-definition"></a><span data-ttu-id="a77fa-113">Definice šíření</span><span class="sxs-lookup"><span data-stu-id="a77fa-113">Propagation Definition</span></span>  
 <span data-ttu-id="a77fa-114">Pokud všechny následující podmínky použití aktivity M gAId rozšířena do aktivity N.</span><span class="sxs-lookup"><span data-stu-id="a77fa-114">Activity M’s gAId is propagated to activity N if all of the following conditions apply.</span></span>  
  
-   <span data-ttu-id="a77fa-115">N je vytvořit z důvodu M</span><span class="sxs-lookup"><span data-stu-id="a77fa-115">N is created because of M</span></span>  
  
-   <span data-ttu-id="a77fa-116">Na M gAId je znám N</span><span class="sxs-lookup"><span data-stu-id="a77fa-116">M’s gAId is known to N</span></span>  
  
-   <span data-ttu-id="a77fa-117">Na N gAId se rovná gAId na M.</span><span class="sxs-lookup"><span data-stu-id="a77fa-117">N's gAId is equal to M’s gAId.</span></span>  
  
 <span data-ttu-id="a77fa-118">GAId šíří prostřednictvím záhlaví zprávy ID, jak je znázorněno v následujícím schématu XML.</span><span class="sxs-lookup"><span data-stu-id="a77fa-118">The gAId is propagated through the ActivityId message header, as illustrated in the following XML schema.</span></span>  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 <span data-ttu-id="a77fa-119">Následuje příklad záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="a77fa-119">The following is an example of the message header.</span></span>  
  
```xml  
<MessageLogTraceRecord>  
  <s:Envelope xmlns:s="http://www.w3.org/2003/05/soap-envelope"     
                      xmlns:a="http://www.w3.org/2005/08/addressing">  
    <s:Header>  
      <a:Action s:mustUnderstand="1">http://Microsoft.ServiceModel.Samples/ICalculator/Subtract  
      </a:Action>  
      <a:MessageID>urn:uuid:f0091eae-d339-4c7e-9408-ece34602f1ce  
      </a:MessageID>  
      <ActivityId CorrelationId="f94c6af1-7d5d-4295-b693-4670a8a0ce34"   
  
               xmlns="http://schemas.microsoft.com/2004/09/ServiceModel/Diagnostics">  
        17f59a29-b435-4a15-bf7b-642ffc40eac8  
      </ActivityId>  
      <a:ReplyTo>  
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous  
          </a:Address>  
      </a:ReplyTo>  
      <a:To s:mustUnderstand="1">net.tcp://localhost/servicemodelsamples/service</a:To>  
   </s:Header>  
   <s:Body>  
     <Subtract xmlns="http://Microsoft.ServiceModel.Samples">  
       <n1>145</n1>  
       <n2>76.54</n2>  
     </Subtract>  
   </s:Body>  
  </s:Envelope>  
</MessageLogTraceRecord>  
```  
  
## <a name="propagation-and-activity-boundaries"></a><span data-ttu-id="a77fa-120">Šíření a hranice aktivity</span><span class="sxs-lookup"><span data-stu-id="a77fa-120">Propagation and Activity Boundaries</span></span>  
 <span data-ttu-id="a77fa-121">Při šíření ID aktivity napříč koncovými body, příjemce zprávu vysílá spuštění a zastavení trasování s ID tohoto (šířený) aktivity.</span><span class="sxs-lookup"><span data-stu-id="a77fa-121">When the activity ID is propagated across endpoints, the message receiver emits a Start and Stop traces with that (propagated) activity ID.</span></span> <span data-ttu-id="a77fa-122">Je proto zahájení a ukončení trasování s této gAId z každého zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="a77fa-122">Therefore, there is a Start and Stop trace with that gAId from each trace source.</span></span> <span data-ttu-id="a77fa-123">Když koncových bodů jsou v rámci jednoho procesu a používají stejný název zdroj trasování, vytvoří se víc zahájení a ukončení se stejným umístěné (stejné gAId, stejný zdroj trasování, stejný postup).</span><span class="sxs-lookup"><span data-stu-id="a77fa-123">If the endpoints are in the same process and use the same trace source name, multiple Start and Stop with the same lAId (same gAId, same trace source, same process) are created.</span></span>  
  
## <a name="synchronization"></a><span data-ttu-id="a77fa-124">Synchronizace</span><span class="sxs-lookup"><span data-stu-id="a77fa-124">Synchronization</span></span>  
 <span data-ttu-id="a77fa-125">Pokud chcete synchronizovat události napříč koncovými body, které běží na různé počítače, CorrelationId vkládá záhlaví aktivity, který se rozšíří do zpráv.</span><span class="sxs-lookup"><span data-stu-id="a77fa-125">To synchronize events across endpoints that run on different machines, a CorrelationId is added to the ActivityId header that is propagated in messages.</span></span> <span data-ttu-id="a77fa-126">Toto ID můžete použít nástroje pro synchronizaci události mezi počítači se službou hodiny nesoulad mezi databází.</span><span class="sxs-lookup"><span data-stu-id="a77fa-126">Tools can use this ID to synchronize events across machines with clock discrepancy.</span></span> <span data-ttu-id="a77fa-127">Konkrétně nástroj prohlížeče trasování služeb používá toto ID pro zobrazující zprávu toků mezi koncovými body.</span><span class="sxs-lookup"><span data-stu-id="a77fa-127">Specifically, the Service Trace Viewer tool uses this ID for showing message flows between endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a77fa-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="a77fa-128">See Also</span></span>  
 [<span data-ttu-id="a77fa-129">Konfigurace trasování</span><span class="sxs-lookup"><span data-stu-id="a77fa-129">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="a77fa-130">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="a77fa-130">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="a77fa-131">Scénáře komplexního trasování</span><span class="sxs-lookup"><span data-stu-id="a77fa-131">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="a77fa-132">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="a77fa-132">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
