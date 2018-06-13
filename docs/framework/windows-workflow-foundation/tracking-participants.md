---
title: Sledování účastníků
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: 34f807cd8c6c227e5e60b40d1ecc01ef693f31f1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519809"
---
# <a name="tracking-participants"></a><span data-ttu-id="f72fa-102">Sledování účastníků</span><span class="sxs-lookup"><span data-stu-id="f72fa-102">Tracking Participants</span></span>
<span data-ttu-id="f72fa-103">Sledování účastníků jsou body rozšiřitelnosti, které umožňují vývojář pracovního postupu pro přístup k <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objekty a jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="f72fa-103">Tracking participants are extensibility points that allow a workflow developer to access <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objects and process them.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]<span data-ttu-id="f72fa-104"> obsahuje standardní sledování člena, který zapíše sledování záznamů jako události trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="f72fa-104"> includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="f72fa-105">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="f72fa-105">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="tracking-participants"></a><span data-ttu-id="f72fa-106">Sledování účastníků</span><span class="sxs-lookup"><span data-stu-id="f72fa-106">Tracking Participants</span></span>  
 <span data-ttu-id="f72fa-107">Sledování infrastruktury umožňuje použití filtru v odchozí záznamy sledování tak, aby účastník se mohou přihlásit k podmnožině záznamy.</span><span class="sxs-lookup"><span data-stu-id="f72fa-107">The tracking infrastructure allows the application of a filter on the outgoing tracking records such that a participant can subscribe to a subset of the records.</span></span> <span data-ttu-id="f72fa-108">Mechanismus, který chcete použít filtr je prostřednictvím profil sledování.</span><span class="sxs-lookup"><span data-stu-id="f72fa-108">The mechanism to apply a filter is through a tracking profile.</span></span>  
  
 <span data-ttu-id="f72fa-109">Windows Workflow Foundation (WF) v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] poskytuje sledování člena, který zapíše záznamy sledování relaci trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="f72fa-109">Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides a tracking participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="f72fa-110">Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="f72fa-110">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="f72fa-111">Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="f72fa-111">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="f72fa-112">Ukázka sady SDK pro sledování na základě trasování událostí pro Windows je dobrý způsob, jak Seznamte se s WF sledování pomocí účastník na základě trasování událostí pro Windows Sledování.</span><span class="sxs-lookup"><span data-stu-id="f72fa-112">The SDK sample for ETW-based tracking is a good way to get familiar with WF tracking using the ETW-based tracking participant.</span></span>  
  
## <a name="etw-tracking-participant"></a><span data-ttu-id="f72fa-113">Trasování událostí pro Windows Sledování účastník</span><span class="sxs-lookup"><span data-stu-id="f72fa-113">ETW Tracking Participant</span></span>  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]<span data-ttu-id="f72fa-114"> zahrnuje trasování událostí pro Windows Sledování člena, který zapíše záznamy sledování relaci trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="f72fa-114"> includes an ETW Tracking Participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="f72fa-115">Důvodem je velmi efektivní způsobem s minimálním dopadem na výkon aplikace a propustnost serveru.</span><span class="sxs-lookup"><span data-stu-id="f72fa-115">This is done in a very efficient manner with minimal impact to the application’s performance or to the server’s throughput.</span></span> <span data-ttu-id="f72fa-116">Výhodou použití standardní sledování účastník trasování událostí pro Windows je, že záznamy sledování, které obdrží lze zobrazit v jiné aplikaci a systém zaprotokoluje v prohlížeči událostí systému Windows.</span><span class="sxs-lookup"><span data-stu-id="f72fa-116">An advantage of using the standard ETW tracking participant is that the tracking records it receives can be viewed with the other application and system logs in the Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="f72fa-117">Standardní sledování účastník trasování událostí pro Windows je nakonfigurovat v souboru Web.config, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f72fa-117">The standard ETW tracking participant is configured in the Web.config file as shown in the following example.</span></span>  
  
```xml  
<configuration>  
  <system.web>  
    <compilation debug="true" targetFramework="4.0" />  
  </system.web>  
  <system.serviceModel>  
    <behaviors>  
      <serviceBehaviors>  
        <behavior>  
          <etwTracking profileName="Sample Tracking Profile"/>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
   <tracking>  
      <profiles>  
        <trackingProfile name="Sample Tracking Profile">  
        ….  
       </trackingProfile>  
      </profiles>  
    </tracking>  
  </system.serviceModel>  
</configuration>  
```  
  
> [!NOTE]
>  <span data-ttu-id="f72fa-118">Pokud `trackingProfile` není zadán název, například právě `<etwTracking/>` nebo `<etwTracking profileName=""/>`, pak výchozí sledování nainstalovaný s profil [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v souboru Machine.config soubor je používán.</span><span class="sxs-lookup"><span data-stu-id="f72fa-118">If a `trackingProfile` name is not specified, such as just `<etwTracking/>` or `<etwTracking profileName=""/>`, then the default tracking profile installed with the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the Machine.config file is used.</span></span>  
  
 <span data-ttu-id="f72fa-119">V souboru Machine.config. výchozí sledování profil jako odběratel u záznamů instance pracovního postupu a chyb.</span><span class="sxs-lookup"><span data-stu-id="f72fa-119">In the Machine.config file, the default tracking profile subscribes to workflow instance records and faults.</span></span>  
  
 <span data-ttu-id="f72fa-120">Trasování událostí pro Windows události se zapisují do relace trasování pomocí ID zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="f72fa-120">In ETW, events are written to the ETW session through a provider ID.</span></span> <span data-ttu-id="f72fa-121">Zprostředkovatel ID trasování sledování účastnické používá k zápisu sledování zaznamenává do trasování událostí pro Windows je definována v části Diagnostika v souboru Web.config (v části `<system.serviceModel><diagnostics>`).</span><span class="sxs-lookup"><span data-stu-id="f72fa-121">The provider ID that the ETW tracking participant uses for writing the tracking records to ETW is defined in the diagnostics section of the Web.config file (under `<system.serviceModel><diagnostics>`).</span></span> <span data-ttu-id="f72fa-122">Ve výchozím nastavení účastník sledování ETW používá výchozí zprostředkovatel ID při nebyl zadán jeden, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f72fa-122">By default, the ETW tracking participant uses a default provider ID when one has not been specified, as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 <span data-ttu-id="f72fa-123">Následující obrázek znázorňuje tok data prostřednictvím účastník sledování ETW sledování.</span><span class="sxs-lookup"><span data-stu-id="f72fa-123">The following illustration shows the flow of tracking data through the ETW tracking participant.</span></span> <span data-ttu-id="f72fa-124">Jakmile se data sledování dosáhne relace trasování událostí pro Windows, můžete získat přístup v mnoha různými způsoby.</span><span class="sxs-lookup"><span data-stu-id="f72fa-124">Once the tracking data reaches the ETW session, it can be accessed in a number of ways.</span></span> <span data-ttu-id="f72fa-125">Jedním z nejužitečnějších způsobů pro přístup k těmto událostem je prostřednictvím prohlížeče událostí, běžné nástroj Windows používá k zobrazení protokolů a tras z aplikací a služeb.</span><span class="sxs-lookup"><span data-stu-id="f72fa-125">One of the most useful ways to access these events is through Event Viewer, a common Windows tool used for viewing logs and traces from applications and services.</span></span>  
  
 <span data-ttu-id="f72fa-126">![Tok sledování a zprostředkovatele trasování událostí pro Windows Sledování](../../../docs/framework/windows-workflow-foundation/media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")</span><span class="sxs-lookup"><span data-stu-id="f72fa-126">![The flow of Tracking and ETW Tracking Provider](../../../docs/framework/windows-workflow-foundation/media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")</span></span>  
  
## <a name="tracking-participant-event-data"></a><span data-ttu-id="f72fa-127">Sledování dat účastnické událostí</span><span class="sxs-lookup"><span data-stu-id="f72fa-127">Tracking Participant Event Data</span></span>  
 <span data-ttu-id="f72fa-128">Sledování účastník, který serializuje data sledovaných událostí na relaci trasování událostí pro Windows ve formátu jedna událost na záznam o sledování.</span><span class="sxs-lookup"><span data-stu-id="f72fa-128">A tracking participant serializes tracked event data to an ETW session in the format of one event per tracking record.</span></span>  <span data-ttu-id="f72fa-129">Událost je identifikován pomocí ID, které v rozsahu 100 až 199.</span><span class="sxs-lookup"><span data-stu-id="f72fa-129">An event is identified using an ID within the range of 100 through 199.</span></span> <span data-ttu-id="f72fa-130">Definice sledování události záznamy vygenerované sledování účastník, najdete v článku [sledování událostí odkaz](../../../docs/framework/windows-workflow-foundation/tracking-events-reference.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="f72fa-130">For definitions of the tracking event records emitted by a tracking participant, see the [Tracking Events Reference](../../../docs/framework/windows-workflow-foundation/tracking-events-reference.md) topic.</span></span>  
  
 <span data-ttu-id="f72fa-131">Velikost událost trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW, nebo podle maximální datové části pro událost trasování událostí pro Windows, podle toho, která hodnota je menší.</span><span class="sxs-lookup"><span data-stu-id="f72fa-131">The size of an ETW event is limited by the ETW buffer size, or the by the maximum payload for an ETW event, whichever value is smaller.</span></span> <span data-ttu-id="f72fa-132">Pokud velikost události překročí některý z těchto mezních hodnot trasování událostí pro Windows, se zkrátí události a její obsah odebrat libovolný způsobem.</span><span class="sxs-lookup"><span data-stu-id="f72fa-132">If the size of the event exceeds either of these ETW limits, the event is truncated and its content removed in an arbitrary manner.</span></span> <span data-ttu-id="f72fa-133">Selektivně se neodeberou proměnné, argumenty, poznámky a vlastní data.</span><span class="sxs-lookup"><span data-stu-id="f72fa-133">Variables, arguments, annotations and custom data are not selectively removed.</span></span> <span data-ttu-id="f72fa-134">V případě zkrácení všechny z nich se zkrátí bez ohledu na hodnotu, která způsobila, že na velikost události překročila omezení trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="f72fa-134">In the case of truncation, all of these are truncated regardless of the value that caused the event size to exceed the ETW limit.</span></span>  <span data-ttu-id="f72fa-135">Odebrané data se nahradí `<item>..<item>`.</span><span class="sxs-lookup"><span data-stu-id="f72fa-135">The removed data is replaced with `<item>..<item>`.</span></span>  
  
 <span data-ttu-id="f72fa-136">Komplexní typy, které do proměnné, argumenty, a vlastní datové položky se serializují na záznam události trasování událostí pro Windows pomocí [NetDataContractSerializer třída](http://go.microsoft.com/fwlink/?LinkId=177537).</span><span class="sxs-lookup"><span data-stu-id="f72fa-136">Complex types in variables, arguments, and custom data items are serialized to the ETW event record using the [NetDataContractSerializer Class](http://go.microsoft.com/fwlink/?LinkId=177537).</span></span> <span data-ttu-id="f72fa-137">Tato třída obsahuje informace o typu CLR v serializovaný datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="f72fa-137">This class includes CLR-type information in the serialized XML steam.</span></span>  
  
 <span data-ttu-id="f72fa-138">Zkrácení datové části z důvodu omezení trasování událostí pro Windows může způsobit duplicitní sledování záznamů odesílána relaci trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="f72fa-138">Truncation of payload data due to ETW limits can result in duplicate tracking records being sent to an ETW session.</span></span> <span data-ttu-id="f72fa-139">Tato situace může nastat, pokud naslouchá více než jednu relaci události, a přihlásit se k relacím omezení různé datové části události.</span><span class="sxs-lookup"><span data-stu-id="f72fa-139">This can occur if more than one session is listening for the events and the sessions have different payload limits for the events.</span></span>  
  
 <span data-ttu-id="f72fa-140">Pro relaci s nižší limit události mohou být zkráceny.</span><span class="sxs-lookup"><span data-stu-id="f72fa-140">For  the session with the lower limit the event may be truncated.</span></span> <span data-ttu-id="f72fa-141">Účastník sledování ETW nemá žádnou znalost počet relací, naslouchání událostem; Pokud událost se zkrátí pro relaci pak účastnické opakování ETW jednou odeslání události.</span><span class="sxs-lookup"><span data-stu-id="f72fa-141">The ETW tracking participant does not have any knowledge of the number of sessions listening for the events; if an event is truncated for a session then the ETW participant retries sending the event once.</span></span> <span data-ttu-id="f72fa-142">Relace, který je nakonfigurovaný tak, aby přijímal větší velikost datové části v tomto případě získají dvakrát událostí (událost-zkrácen a zkrácený).</span><span class="sxs-lookup"><span data-stu-id="f72fa-142">In this case the session that is configured to accept a larger payload size will get the event twice (the non-truncated and truncated event).</span></span> <span data-ttu-id="f72fa-143">Duplikace se dá zabránit tak, že nakonfigurujete všechny relace trasování událostí pro Windows s stejné omezení velikosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="f72fa-143">Duplication can be prevented by configuring all the ETW sessions with same buffer size limits.</span></span>  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a><span data-ttu-id="f72fa-144">Přístup ke sledování dat od účastníka trasování událostí pro Windows v prohlížeči událostí</span><span class="sxs-lookup"><span data-stu-id="f72fa-144">Accessing Tracking Data from an ETW Participant in the Event Viewer</span></span>  
 <span data-ttu-id="f72fa-145">Události, které se zapisují do relaci trasování událostí pro Windows účastníkem sledování, trasování událostí pro Windows je přístupná prostřednictvím prohlížeče událostí (při použití výchozí zprostředkovatel ID).</span><span class="sxs-lookup"><span data-stu-id="f72fa-145">Events that are written to an ETW session by the ETW tracking participant can be accessed through the Event Viewer (when using the default provider ID).</span></span> <span data-ttu-id="f72fa-146">To umožňuje rychle zobrazení sledování záznamů, které vyvolaly pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f72fa-146">This allows for rapidly viewing of tracking records that have been emitted by the workflow.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f72fa-147">Sledování záznamů události vygenerované pro událost použití relace ID trasování událostí pro Windows v rozsahu 100 až 199.</span><span class="sxs-lookup"><span data-stu-id="f72fa-147">Tracking record events emitted to an ETW session use event IDs in the range of 100 through 199.</span></span>  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a><span data-ttu-id="f72fa-148">Chcete-li povolit zobrazení záznamů sledování v prohlížeči událostí</span><span class="sxs-lookup"><span data-stu-id="f72fa-148">To enable viewing the Tracking Records in Event Viewer</span></span>  
  
1.  <span data-ttu-id="f72fa-149">Spuštění prohlížeče událostí (EVENTVWR. SOUBOR EXE)</span><span class="sxs-lookup"><span data-stu-id="f72fa-149">Start the Event Viewer (EVENTVWR.EXE)</span></span>  
  
2.  <span data-ttu-id="f72fa-150">Vyberte **Prohlížeč událostí, protokoly aplikací a služeb, aplikací společnosti Microsoft, Windows Server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="f72fa-150">Select **Event Viewer, Applications and Services Logs, Microsoft, Windows, Application Server-Applications**.</span></span>  
  
3.  <span data-ttu-id="f72fa-151">Klikněte pravým tlačítkem a ujistěte se, že **zobrazení, zobrazit ladění protokoly a** je vybrána.</span><span class="sxs-lookup"><span data-stu-id="f72fa-151">Right-click and ensure that **View, Show Analytic and Debug logs** is selected.</span></span> <span data-ttu-id="f72fa-152">Pokud ne, vyberte ho tak zaškrtnutí se zobrazí vedle sebe.</span><span class="sxs-lookup"><span data-stu-id="f72fa-152">If not, select it so the check mark appears next to it.</span></span> <span data-ttu-id="f72fa-153">Zobrazí se **analytické**, **výkonu**, a **ladění** protokoly.</span><span class="sxs-lookup"><span data-stu-id="f72fa-153">This displays the **Analytic**, **Perf**, and **Debug** logs.</span></span>  
  
4.  <span data-ttu-id="f72fa-154">Klikněte pravým tlačítkem myši **analytické** protokolu a potom vyberte **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="f72fa-154">Right-click the **Analytic** log and then select **Enable Log**.</span></span> <span data-ttu-id="f72fa-155">V protokolu budou existovat v souboru Server-Applications%4Analytic.etl %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application.</span><span class="sxs-lookup"><span data-stu-id="f72fa-155">The log will exist in the %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl file.</span></span>  
  
## <a name="custom-tracking-participant"></a><span data-ttu-id="f72fa-156">Vlastní sledování účastník</span><span class="sxs-lookup"><span data-stu-id="f72fa-156">Custom Tracking Participant</span></span>  
 <span data-ttu-id="f72fa-157">Sledování účastník rozhraní API umožňuje rozšíření modulu runtime sledování s účastníkem sledování zadaný uživatelem, který může obsahovat vlastní logiky pro zpracování sledování záznamy vygenerované modulem runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f72fa-157">The tracking participant API allows extension of the tracking runtime with a user-provided tracking participant that can include custom logic to handle tracking records emitted by the workflow runtime.</span></span> <span data-ttu-id="f72fa-158">Zápis vlastní sledování účastník, musí vývojář implementovat `Track` metodu <xref:System.Activities.Tracking.TrackingParticipant> třída.</span><span class="sxs-lookup"><span data-stu-id="f72fa-158">To write a custom tracking participant, the developer must implement the `Track` method on the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="f72fa-159">Tato metoda je volána, když je záznam sledování vygenerované modulem runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f72fa-159">This method is called when a tracking record is emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="f72fa-160">Sledování účastníků odvozena od <xref:System.Activities.Tracking.TrackingParticipant> třídy.</span><span class="sxs-lookup"><span data-stu-id="f72fa-160">Tracking participants derive from the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="f72fa-161">Poskytované systémem <xref:System.Activities.Tracking.EtwTrackingParticipant> vydá událost událostí sledování pro Windows (ETW) pro každý záznam sledování, které se získaly.</span><span class="sxs-lookup"><span data-stu-id="f72fa-161">The system-provided <xref:System.Activities.Tracking.EtwTrackingParticipant> emits an Event Tracking for Windows (ETW) event for each tracking record that is received.</span></span> <span data-ttu-id="f72fa-162">Pokud chcete vytvořit vlastní sledování účastník, třídu je vytvořen, který je odvozen od <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="f72fa-162">To create a custom tracking participant, a class is created that derives from <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="f72fa-163">Pro zajištění základních sledování, přepsání <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="f72fa-163">To provide basic tracking functionality, override <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span></span> <span data-ttu-id="f72fa-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> je volána, když záznam sledování odesílají modulu runtime a lze ji zpracovat požadované způsobem.</span><span class="sxs-lookup"><span data-stu-id="f72fa-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> is called when a tracking record is sent by the runtime and can be processed in the desired manner.</span></span> <span data-ttu-id="f72fa-165">V následujícím příkladu je definována účastnické třídu vlastní sledování, který vysílá všechny záznamy sledování do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="f72fa-165">In the following example, a custom tracking participant class is defined that emits all tracking records to the console window.</span></span> <span data-ttu-id="f72fa-166">Můžete taky implementovat <xref:System.Activities.Tracking.TrackingParticipant> objekt, který zpracovává sledování zaznamenává asynchronně pomocí jeho `BeginTrack` a `EndTrack` metody</span><span class="sxs-lookup"><span data-stu-id="f72fa-166">You can also implement a <xref:System.Activities.Tracking.TrackingParticipant> object that processes the tracking records asynchronously using its `BeginTrack` and `EndTrack` methods</span></span>  
  
```csharp  
class ConsoleTrackingParticipant : TrackingParticipant  
{  
    protected override void Track(TrackingRecord record, TimeSpan timeout)  
    {  
        if (record != null)  
        {  
            Console.WriteLine("=================================");  
            Console.WriteLine(record);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="f72fa-167">Pokud chcete používat konkrétní sledování účastník, zaregistrujte ji pomocí k instanci pracovního postupu, který chcete sledovat, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="f72fa-167">To use a particular tracking participant, register it with the workflow instance that you want to track, as shown in the following example.</span></span>  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="f72fa-168">V následujícím příkladu, pracovní postup, se skládá z <xref:System.Activities.Statements.Sequence> aktivity, která obsahuje <xref:System.Activities.Statements.WriteLine> vytvoření aktivity.</span><span class="sxs-lookup"><span data-stu-id="f72fa-168">In the following example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> activity is created.</span></span> <span data-ttu-id="f72fa-169">`ConsoleTrackingParticipant` Se přidá do rozšíření a volána pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="f72fa-169">The `ConsoleTrackingParticipant` is added to the extensions and the workflow is invoked.</span></span>  
  
```csharp  
Activity activity= new Sequence()  
{  
    Activities =  
    {  
        new WriteLine()  
        {  
            Text = "Hello World."  
        }  
    }  
};  
  
WorkflowApplication instance = new WorkflowApplication(activity);  
  
instance.Extensions.Add(new ConsoleTrackingParticipant());  
  instance.Completed = delegate(WorkflowApplicationCompletedEventArgs e)  
            {  
                Console.WriteLine("workflow instance completed, Id = " + instance.Id);  
                resetEvent.Set();  
            };  
            instance.Run();  
            Console.ReadLine();  
```  
  
## <a name="see-also"></a><span data-ttu-id="f72fa-170">Viz také</span><span class="sxs-lookup"><span data-stu-id="f72fa-170">See Also</span></span>  
 [<span data-ttu-id="f72fa-171">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="f72fa-171">Windows Server App Fabric Monitoring</span></span>](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [<span data-ttu-id="f72fa-172">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="f72fa-172">Monitoring Applications with App Fabric</span></span>](http://go.microsoft.com/fwlink/?LinkId=201275)
