---
title: Šíření
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: f4e92c6dec163d191c507dd80bb0d9dc129c6e96
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
ms.locfileid: "33803234"
---
# <a name="propagation"></a><span data-ttu-id="3300c-102">Šíření</span><span class="sxs-lookup"><span data-stu-id="3300c-102">Propagation</span></span>
<span data-ttu-id="3300c-103">Toto téma popisuje rozšíření aktivity v modelu trasování Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="3300c-103">This topic describes activity propagation in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a><span data-ttu-id="3300c-104">Pomocí šíření pro vazbu mezi aktivitami v koncových bodů</span><span class="sxs-lookup"><span data-stu-id="3300c-104">Using Propagation to Correlate Activities Across Endpoints</span></span>  
 <span data-ttu-id="3300c-105">Šíření poskytuje možnosti pro že uživatele s přímou souvislost chyby trasování pro stejnou jednotku zpracování napříč koncovými body aplikace, například požadavek.</span><span class="sxs-lookup"><span data-stu-id="3300c-105">Propagation provides the user with direct correlation of error traces for the same unit of processing across application endpoints, for example, a request.</span></span> <span data-ttu-id="3300c-106">Vygenerované v různých koncové body pro stejnou jednotku zpracování chyby jsou seskupené do stejné aktivity, i mezi doménami aplikací.</span><span class="sxs-lookup"><span data-stu-id="3300c-106">Errors emitted at different endpoints for the same unit of processing are grouped in the same activity, even across application domains.</span></span> <span data-ttu-id="3300c-107">To se provádí prostřednictvím šíření ID aktivity v záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="3300c-107">This is done through propagation of the activity ID in the message headers.</span></span> <span data-ttu-id="3300c-108">Pokud klient časového limitu z důvodu vnitřní chyby v serveru, i chyby vypadat do stejné aktivity pro přímé korelace.</span><span class="sxs-lookup"><span data-stu-id="3300c-108">Therefore, if a client times out because of an internal error in the server, both errors appear in the same activity for direct correlation.</span></span>  
  
 <span data-ttu-id="3300c-109">Chcete-li to provést, použijte `ActivityTracing` nastavení, jak je předvedeno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="3300c-109">To do this, use the `ActivityTracing` setting as demonstrated in the previous example.</span></span> <span data-ttu-id="3300c-110">Kromě toho nastavit `propagateActivity` atribut pro `System.ServiceModel` zdroj trasování na všechny koncové body.</span><span class="sxs-lookup"><span data-stu-id="3300c-110">In addition, set the `propagateActivity` attribute for the `System.ServiceModel` trace source at all endpoints.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 <span data-ttu-id="3300c-111">Rozšíření aktivity je konfigurovat funkci, která způsobí, že WCF přidat hlavičku do odchozí zprávy, která zahrnuje ID aktivity na TLS.</span><span class="sxs-lookup"><span data-stu-id="3300c-111">Activity propagation is a configurable capability that causes WCF to add a header to outbound messages, which includes the activity ID on the TLS.</span></span> <span data-ttu-id="3300c-112">To uvedete na následné trasování na straně serveru, jsme mohou korelovat aktivity klienta a serveru.</span><span class="sxs-lookup"><span data-stu-id="3300c-112">By including this on subsequent traces on the server side, we can correlate client and server activities.</span></span>  
  
## <a name="propagation-definition"></a><span data-ttu-id="3300c-113">Definice šíření</span><span class="sxs-lookup"><span data-stu-id="3300c-113">Propagation Definition</span></span>  
 <span data-ttu-id="3300c-114">Pokud všechny následující podmínky použití aktivity M gAId rozšířena do aktivity N.</span><span class="sxs-lookup"><span data-stu-id="3300c-114">Activity M’s gAId is propagated to activity N if all of the following conditions apply.</span></span>  
  
-   <span data-ttu-id="3300c-115">N je vytvořit z důvodu M</span><span class="sxs-lookup"><span data-stu-id="3300c-115">N is created because of M</span></span>  
  
-   <span data-ttu-id="3300c-116">Na M gAId je znám N</span><span class="sxs-lookup"><span data-stu-id="3300c-116">M’s gAId is known to N</span></span>  
  
-   <span data-ttu-id="3300c-117">Na N gAId se rovná gAId na M.</span><span class="sxs-lookup"><span data-stu-id="3300c-117">N's gAId is equal to M’s gAId.</span></span>  
  
 <span data-ttu-id="3300c-118">GAId šíří prostřednictvím záhlaví zprávy ID, jak je znázorněno v následujícím schématu XML.</span><span class="sxs-lookup"><span data-stu-id="3300c-118">The gAId is propagated through the ActivityId message header, as illustrated in the following XML schema.</span></span>  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 <span data-ttu-id="3300c-119">Následuje příklad záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="3300c-119">The following is an example of the message header.</span></span>  
  
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
  
## <a name="propagation-and-activity-boundaries"></a><span data-ttu-id="3300c-120">Šíření a hranice aktivity</span><span class="sxs-lookup"><span data-stu-id="3300c-120">Propagation and Activity Boundaries</span></span>  
 <span data-ttu-id="3300c-121">Při šíření ID aktivity napříč koncovými body, příjemce zprávu vysílá spuštění a zastavení trasování s ID tohoto (šířený) aktivity.</span><span class="sxs-lookup"><span data-stu-id="3300c-121">When the activity ID is propagated across endpoints, the message receiver emits a Start and Stop traces with that (propagated) activity ID.</span></span> <span data-ttu-id="3300c-122">Je proto zahájení a ukončení trasování s této gAId z každého zdroje trasování.</span><span class="sxs-lookup"><span data-stu-id="3300c-122">Therefore, there is a Start and Stop trace with that gAId from each trace source.</span></span> <span data-ttu-id="3300c-123">Když koncových bodů jsou v rámci jednoho procesu a používají stejný název zdroj trasování, vytvoří se víc zahájení a ukončení se stejným umístěné (stejné gAId, stejný zdroj trasování, stejný postup).</span><span class="sxs-lookup"><span data-stu-id="3300c-123">If the endpoints are in the same process and use the same trace source name, multiple Start and Stop with the same lAId (same gAId, same trace source, same process) are created.</span></span>  
  
## <a name="synchronization"></a><span data-ttu-id="3300c-124">Synchronizace</span><span class="sxs-lookup"><span data-stu-id="3300c-124">Synchronization</span></span>  
 <span data-ttu-id="3300c-125">Pokud chcete synchronizovat události napříč koncovými body, které běží na různé počítače, CorrelationId vkládá záhlaví aktivity, který se rozšíří do zpráv.</span><span class="sxs-lookup"><span data-stu-id="3300c-125">To synchronize events across endpoints that run on different machines, a CorrelationId is added to the ActivityId header that is propagated in messages.</span></span> <span data-ttu-id="3300c-126">Toto ID můžete použít nástroje pro synchronizaci události mezi počítači se službou hodiny nesoulad mezi databází.</span><span class="sxs-lookup"><span data-stu-id="3300c-126">Tools can use this ID to synchronize events across machines with clock discrepancy.</span></span> <span data-ttu-id="3300c-127">Konkrétně nástroj prohlížeče trasování služeb používá toto ID pro zobrazující zprávu toků mezi koncovými body.</span><span class="sxs-lookup"><span data-stu-id="3300c-127">Specifically, the Service Trace Viewer tool uses this ID for showing message flows between endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3300c-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="3300c-128">See Also</span></span>  
 [<span data-ttu-id="3300c-129">Konfigurace trasování</span><span class="sxs-lookup"><span data-stu-id="3300c-129">Configuring Tracing</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
 [<span data-ttu-id="3300c-130">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="3300c-130">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [<span data-ttu-id="3300c-131">Scénáře komplexního trasování</span><span class="sxs-lookup"><span data-stu-id="3300c-131">End-To-End Tracing Scenarios</span></span>](../../../../../docs/framework/wcf/diagnostics/tracing/end-to-end-tracing-scenarios.md)  
 [<span data-ttu-id="3300c-132">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="3300c-132">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
