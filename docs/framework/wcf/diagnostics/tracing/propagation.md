---
title: Šíření
ms.date: 03/30/2017
ms.assetid: f8181e75-d693-48d1-b333-a776ad3b382a
ms.openlocfilehash: 732ae5cb1ce311b78728f8d5de0fd9102bf32499
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84578952"
---
# <a name="propagation"></a><span data-ttu-id="b8e8d-102">Šíření</span><span class="sxs-lookup"><span data-stu-id="b8e8d-102">Propagation</span></span>
<span data-ttu-id="b8e8d-103">Toto téma popisuje šíření aktivit v modelu trasování Windows Communication Foundation (WCF).</span><span class="sxs-lookup"><span data-stu-id="b8e8d-103">This topic describes activity propagation in the Windows Communication Foundation (WCF) tracing model.</span></span>  
  
## <a name="using-propagation-to-correlate-activities-across-endpoints"></a><span data-ttu-id="b8e8d-104">Korelace aktivit mezi koncovými body pomocí šíření</span><span class="sxs-lookup"><span data-stu-id="b8e8d-104">Using Propagation to Correlate Activities Across Endpoints</span></span>  
 <span data-ttu-id="b8e8d-105">Šíření poskytuje uživateli přímou korelaci chybových trasování pro stejnou jednotku zpracování v koncových bodech aplikace, například požadavek.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-105">Propagation provides the user with direct correlation of error traces for the same unit of processing across application endpoints, for example, a request.</span></span> <span data-ttu-id="b8e8d-106">Chyby emitované v různých koncových bodech pro stejnou jednotku zpracování jsou seskupeny do stejné aktivity, dokonce i napříč doménami aplikace.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-106">Errors emitted at different endpoints for the same unit of processing are grouped in the same activity, even across application domains.</span></span> <span data-ttu-id="b8e8d-107">To se provádí prostřednictvím šíření ID aktivity v záhlavích zpráv.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-107">This is done through propagation of the activity ID in the message headers.</span></span> <span data-ttu-id="b8e8d-108">Proto pokud časový limit klienta vyprší kvůli vnitřní chybě serveru, zobrazí se obě chyby ve stejné aktivitě pro přímou korelaci.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-108">Therefore, if a client times out because of an internal error in the server, both errors appear in the same activity for direct correlation.</span></span>  
  
 <span data-ttu-id="b8e8d-109">Uděláte to tak, že použijete `ActivityTracing` nastavení, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-109">To do this, use the `ActivityTracing` setting as demonstrated in the previous example.</span></span> <span data-ttu-id="b8e8d-110">Kromě toho nastavte `propagateActivity` atribut pro `System.ServiceModel` zdroj trasování ve všech koncových bodech.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-110">In addition, set the `propagateActivity` attribute for the `System.ServiceModel` trace source at all endpoints.</span></span>  
  
```xml  
<source name="System.ServiceModel" switchValue="Verbose,ActivityTracing" propagateActivity="true" >  
```  
  
 <span data-ttu-id="b8e8d-111">Šíření aktivit je konfigurovatelná možnost, která způsobuje, že WCF přidá hlavičku do odchozích zpráv, což zahrnuje ID aktivity v TLS.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-111">Activity propagation is a configurable capability that causes WCF to add a header to outbound messages, which includes the activity ID on the TLS.</span></span> <span data-ttu-id="b8e8d-112">Zahrnutím této akce na straně serveru můžeme korelovat aktivity klientů a serverů.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-112">By including this on subsequent traces on the server side, we can correlate client and server activities.</span></span>  
  
## <a name="propagation-definition"></a><span data-ttu-id="b8e8d-113">Definice šíření</span><span class="sxs-lookup"><span data-stu-id="b8e8d-113">Propagation Definition</span></span>  
 <span data-ttu-id="b8e8d-114">GAId aktivity M se šíří na aktivitu N, pokud platí všechny následující podmínky.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-114">Activity M’s gAId is propagated to activity N if all of the following conditions apply.</span></span>  
  
- <span data-ttu-id="b8e8d-115">N se vytvoří kvůli M</span><span class="sxs-lookup"><span data-stu-id="b8e8d-115">N is created because of M</span></span>  
  
- <span data-ttu-id="b8e8d-116">GAId M se říká N.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-116">M’s gAId is known to N</span></span>  
  
- <span data-ttu-id="b8e8d-117">GAId se rovná gAId M.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-117">N's gAId is equal to M’s gAId.</span></span>  
  
 <span data-ttu-id="b8e8d-118">GAId je šířena prostřednictvím hlavičky zprávy ActivityId, jak je znázorněno v následujícím schématu XML.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-118">The gAId is propagated through the ActivityId message header, as illustrated in the following XML schema.</span></span>  
  
```xml  
<xsd:element name="ActivityId" type="integer" minOccurs="0">  
  <xsd:attribute name="CorrelationId" type="integer" minOccurs="0"/>  
</xsd:element>  
```  
  
 <span data-ttu-id="b8e8d-119">Následuje příklad záhlaví zprávy.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-119">The following is an example of the message header.</span></span>  
  
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
          <a:Address>http://www.w3.org/2005/08/addressing/anonymous</a:Address>  
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
  
## <a name="propagation-and-activity-boundaries"></a><span data-ttu-id="b8e8d-120">Hranice šíření a aktivity</span><span class="sxs-lookup"><span data-stu-id="b8e8d-120">Propagation and Activity Boundaries</span></span>  
 <span data-ttu-id="b8e8d-121">Pokud je ID aktivity šířeno napříč koncovými body, příjemce zprávy vyšle trasování spuštění a zastavení s tímto (šířeným) ID aktivity.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-121">When the activity ID is propagated across endpoints, the message receiver emits a Start and Stop traces with that (propagated) activity ID.</span></span> <span data-ttu-id="b8e8d-122">Z každého zdroje trasování proto existuje spuštění a zastavení trasování s tímto gAId.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-122">Therefore, there is a Start and Stop trace with that gAId from each trace source.</span></span> <span data-ttu-id="b8e8d-123">Pokud jsou koncové body ve stejném procesu a používají stejný název zdroje trasování, vytvoří se několik spuštění a zastavení se stejným systémem (stejné gAId, stejný zdroj trasování, stejný proces).</span><span class="sxs-lookup"><span data-stu-id="b8e8d-123">If the endpoints are in the same process and use the same trace source name, multiple Start and Stop with the same lAId (same gAId, same trace source, same process) are created.</span></span>  
  
## <a name="synchronization"></a><span data-ttu-id="b8e8d-124">Synchronizace</span><span class="sxs-lookup"><span data-stu-id="b8e8d-124">Synchronization</span></span>  
 <span data-ttu-id="b8e8d-125">K synchronizaci událostí mezi koncovými body, které běží na různých počítačích, se do hlavičky ActivityId, která se šíří ve zprávách, přidá ID korelace.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-125">To synchronize events across endpoints that run on different machines, a CorrelationId is added to the ActivityId header that is propagated in messages.</span></span> <span data-ttu-id="b8e8d-126">Pomocí tohoto ID můžou nástroje synchronizovat události napříč počítači s nesouladem hodin.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-126">Tools can use this ID to synchronize events across machines with clock discrepancy.</span></span> <span data-ttu-id="b8e8d-127">Konkrétně nástroj pro prohlížeč trasování služby používá toto ID pro zobrazení toků zpráv mezi koncovými body.</span><span class="sxs-lookup"><span data-stu-id="b8e8d-127">Specifically, the Service Trace Viewer tool uses this ID for showing message flows between endpoints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8e8d-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="b8e8d-128">See also</span></span>

- [<span data-ttu-id="b8e8d-129">Konfigurace trasování</span><span class="sxs-lookup"><span data-stu-id="b8e8d-129">Configuring Tracing</span></span>](configuring-tracing.md)
- [<span data-ttu-id="b8e8d-130">Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů</span><span class="sxs-lookup"><span data-stu-id="b8e8d-130">Using Service Trace Viewer for Viewing Correlated Traces and Troubleshooting</span></span>](using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [<span data-ttu-id="b8e8d-131">Scénáře komplexního trasování</span><span class="sxs-lookup"><span data-stu-id="b8e8d-131">End-To-End Tracing Scenarios</span></span>](end-to-end-tracing-scenarios.md)
- [<span data-ttu-id="b8e8d-132">Prohlížeč trasování služeb (SvcTraceViewer.exe)</span><span class="sxs-lookup"><span data-stu-id="b8e8d-132">Service Trace Viewer Tool (SvcTraceViewer.exe)</span></span>](../../service-trace-viewer-tool-svctraceviewer-exe.md)
