---
title: Účastníci sledování
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: 6c42712300baa6d7e12b9a29d94c925caaad5141
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699810"
---
# <a name="tracking-participants"></a><span data-ttu-id="a6e94-102">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="a6e94-102">Tracking Participants</span></span>
<span data-ttu-id="a6e94-103">Sledování účastníci jsou body rozšiřitelnosti, které umožňují vývojář pracovního postupu pro přístup k <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objektů a jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="a6e94-103">Tracking participants are extensibility points that allow a workflow developer to access <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objects and process them.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="a6e94-104">zahrnuje účastník standardní sledování, který zapíše záznamy sledování jako události trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="a6e94-104">includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="a6e94-105">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="a6e94-105">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="tracking-participants"></a><span data-ttu-id="a6e94-106">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="a6e94-106">Tracking Participants</span></span>  
 <span data-ttu-id="a6e94-107">Sledování infrastruktury umožňuje aplikaci filtru na odchozí záznamy sledování, tak, aby účastníka se přihlásit k odběru podmnožinu záznamů.</span><span class="sxs-lookup"><span data-stu-id="a6e94-107">The tracking infrastructure allows the application of a filter on the outgoing tracking records such that a participant can subscribe to a subset of the records.</span></span> <span data-ttu-id="a6e94-108">Mechanismus, který chcete použít filtr je prostřednictvím profilu sledování.</span><span class="sxs-lookup"><span data-stu-id="a6e94-108">The mechanism to apply a filter is through a tracking profile.</span></span>  
  
 <span data-ttu-id="a6e94-109">Windows Workflow Foundation (WF) v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] poskytuje sledování účastník, který zapíše záznamy sledování k relaci ETW.</span><span class="sxs-lookup"><span data-stu-id="a6e94-109">Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides a tracking participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="a6e94-110">Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="a6e94-110">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="a6e94-111">Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="a6e94-111">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="a6e94-112">Ukázka sady SDK pro sledování na základě trasování událostí pro Windows je dobrým způsobem, jak Seznamte se s pomocí trasování událostí pro Windows na základě sledování účastník sledování WF.</span><span class="sxs-lookup"><span data-stu-id="a6e94-112">The SDK sample for ETW-based tracking is a good way to get familiar with WF tracking using the ETW-based tracking participant.</span></span>  
  
## <a name="etw-tracking-participant"></a><span data-ttu-id="a6e94-113">Účastník sledování ETW</span><span class="sxs-lookup"><span data-stu-id="a6e94-113">ETW Tracking Participant</span></span>  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="a6e94-114">zahrnuje účastník sledování ETW, který zapíše záznamy sledování k relaci ETW.</span><span class="sxs-lookup"><span data-stu-id="a6e94-114">includes an ETW Tracking Participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="a6e94-115">To je velice efektivním způsobem s minimálním dopadem na výkon vaší aplikace a propustnosti serveru.</span><span class="sxs-lookup"><span data-stu-id="a6e94-115">This is done in a very efficient manner with minimal impact to the application’s performance or to the server’s throughput.</span></span> <span data-ttu-id="a6e94-116">Výhodou použití standardní účastník sledování ETW je, že záznamy sledování, které obdrží lze zobrazit v aplikaci a systém zaprotokoluje v prohlížeči událostí Windows.</span><span class="sxs-lookup"><span data-stu-id="a6e94-116">An advantage of using the standard ETW tracking participant is that the tracking records it receives can be viewed with the other application and system logs in the Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="a6e94-117">Standardní účastník sledování ETW konfigurován v souboru Web.config, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a6e94-117">The standard ETW tracking participant is configured in the Web.config file as shown in the following example.</span></span>  
  
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
>  <span data-ttu-id="a6e94-118">Pokud `trackingProfile` název není zadaný, jako například právě `<etwTracking/>` nebo `<etwTracking profileName=""/>`, pak výchozí profil sledování tracking profile součástí [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v souboru Machine.config soubor se používá.</span><span class="sxs-lookup"><span data-stu-id="a6e94-118">If a `trackingProfile` name is not specified, such as just `<etwTracking/>` or `<etwTracking profileName=""/>`, then the default tracking profile installed with the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the Machine.config file is used.</span></span>  
  
 <span data-ttu-id="a6e94-119">V souboru Machine.config výchozí profil sledování tracking profile přihlásí k záznamům instance pracovního postupu a chyb.</span><span class="sxs-lookup"><span data-stu-id="a6e94-119">In the Machine.config file, the default tracking profile subscribes to workflow instance records and faults.</span></span>  
  
 <span data-ttu-id="a6e94-120">V trasování událostí pro Windows události se zapisují do relace ETW pomocí ID zprostředkovatele.</span><span class="sxs-lookup"><span data-stu-id="a6e94-120">In ETW, events are written to the ETW session through a provider ID.</span></span> <span data-ttu-id="a6e94-121">Poskytovatel ID, které trasování událostí pro Windows pro sledování účastníka používá k zápisu sledování záznamy do trasování událostí pro Windows je definovaná v části Diagnostika souboru Web.config (v části `<system.serviceModel><diagnostics>`).</span><span class="sxs-lookup"><span data-stu-id="a6e94-121">The provider ID that the ETW tracking participant uses for writing the tracking records to ETW is defined in the diagnostics section of the Web.config file (under `<system.serviceModel><diagnostics>`).</span></span> <span data-ttu-id="a6e94-122">Ve výchozím nastavení účastník sledování ETW používá výchozí ID poskytovatele když nebyl zadán jeden, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a6e94-122">By default, the ETW tracking participant uses a default provider ID when one has not been specified, as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 <span data-ttu-id="a6e94-123">Následující obrázek znázorňuje tok dat prostřednictvím účastník sledování ETW sledování.</span><span class="sxs-lookup"><span data-stu-id="a6e94-123">The following illustration shows the flow of tracking data through the ETW tracking participant.</span></span> <span data-ttu-id="a6e94-124">Jakmile se data sledování dosáhne relace trasování událostí pro Windows, můžete získat přístup v několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="a6e94-124">Once the tracking data reaches the ETW session, it can be accessed in a number of ways.</span></span> <span data-ttu-id="a6e94-125">Jedním z nejužitečnějších způsobů pro přístup k těmto událostem je prostřednictvím prohlížeče událostí, běžné nástroje Windows používá k zobrazení protokolů a trasování z aplikací a služeb.</span><span class="sxs-lookup"><span data-stu-id="a6e94-125">One of the most useful ways to access these events is through Event Viewer, a common Windows tool used for viewing logs and traces from applications and services.</span></span>  
  
 ![Sledování dat prostřednictvím poskytovatele trasování událostí pro Windows sledování toku.](./media/tracking-participants/tracking-data-event-tracing-windows-provider.gif)  
  
## <a name="tracking-participant-event-data"></a><span data-ttu-id="a6e94-127">Data sledování účastníků události</span><span class="sxs-lookup"><span data-stu-id="a6e94-127">Tracking Participant Event Data</span></span>  
 <span data-ttu-id="a6e94-128">Sledování účastník serializuje data sledovaných událostí do relace trasování událostí pro Windows ve formátu jednu událost za každou sledování záznamů.</span><span class="sxs-lookup"><span data-stu-id="a6e94-128">A tracking participant serializes tracked event data to an ETW session in the format of one event per tracking record.</span></span>  <span data-ttu-id="a6e94-129">Událost je identifikována pomocí ID v rozsahu od 100 do 199.</span><span class="sxs-lookup"><span data-stu-id="a6e94-129">An event is identified using an ID within the range of 100 through 199.</span></span> <span data-ttu-id="a6e94-130">Definice událostí sledování záznamů, protože ho vygeneroval sledování účastník, najdete v článku [sledování události – referenční informace](tracking-events-reference.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="a6e94-130">For definitions of the tracking event records emitted by a tracking participant, see the [Tracking Events Reference](tracking-events-reference.md) topic.</span></span>  
  
 <span data-ttu-id="a6e94-131">Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti trasování událostí pro Windows, nebo maximální velikost datové části události trasování událostí pro Windows, podle toho, která hodnota je menší.</span><span class="sxs-lookup"><span data-stu-id="a6e94-131">The size of an ETW event is limited by the ETW buffer size, or the by the maximum payload for an ETW event, whichever value is smaller.</span></span> <span data-ttu-id="a6e94-132">Pokud velikost události překračuje jednu z těchto omezení trasování událostí pro Windows, událostí je zkrácena a její obsah odebrat libovolné způsobem.</span><span class="sxs-lookup"><span data-stu-id="a6e94-132">If the size of the event exceeds either of these ETW limits, the event is truncated and its content removed in an arbitrary manner.</span></span> <span data-ttu-id="a6e94-133">Selektivně se neodeberou proměnné, argumenty, poznámky a vlastní data.</span><span class="sxs-lookup"><span data-stu-id="a6e94-133">Variables, arguments, annotations and custom data are not selectively removed.</span></span> <span data-ttu-id="a6e94-134">V případě zkrácení všechny z nich se zkrátí bez ohledu na hodnotu, která způsobila velikost události k překročení limitu trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="a6e94-134">In the case of truncation, all of these are truncated regardless of the value that caused the event size to exceed the ETW limit.</span></span>  <span data-ttu-id="a6e94-135">Odebrání dat je nahrazena `<item>..<item>`.</span><span class="sxs-lookup"><span data-stu-id="a6e94-135">The removed data is replaced with `<item>..<item>`.</span></span>  
  
 <span data-ttu-id="a6e94-136">Komplexní typy, které do proměnné, argumenty a vlastní datové položky se serializují pomocí záznamu události trasování událostí pro Windows [NetDataContractSerializer třídy](https://go.microsoft.com/fwlink/?LinkId=177537).</span><span class="sxs-lookup"><span data-stu-id="a6e94-136">Complex types in variables, arguments, and custom data items are serialized to the ETW event record using the [NetDataContractSerializer Class](https://go.microsoft.com/fwlink/?LinkId=177537).</span></span> <span data-ttu-id="a6e94-137">Tato třída obsahuje informace o typu modulu CLR v serializovaná datový proud XML.</span><span class="sxs-lookup"><span data-stu-id="a6e94-137">This class includes CLR-type information in the serialized XML steam.</span></span>  
  
 <span data-ttu-id="a6e94-138">Zkrácení datové části kvůli omezení trasování událostí pro Windows může způsobit duplicitní sledování záznamů odesílané do relace trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="a6e94-138">Truncation of payload data due to ETW limits can result in duplicate tracking records being sent to an ETW session.</span></span> <span data-ttu-id="a6e94-139">Tato situace může nastat, pokud více než jedna relace přijímá události a relace mají různé datové části limity pro události.</span><span class="sxs-lookup"><span data-stu-id="a6e94-139">This can occur if more than one session is listening for the events and the sessions have different payload limits for the events.</span></span>  
  
 <span data-ttu-id="a6e94-140">Pro relace s dolní mez události můžou být zkrácené.</span><span class="sxs-lookup"><span data-stu-id="a6e94-140">For  the session with the lower limit the event may be truncated.</span></span> <span data-ttu-id="a6e94-141">Účastník sledování ETW nemá žádnou znalost počet relací naslouchání událostem; Pokud je událost zkrácenému pro relaci pak účastníka opakované pokusy trasování událostí pro Windows po odeslání události.</span><span class="sxs-lookup"><span data-stu-id="a6e94-141">The ETW tracking participant does not have any knowledge of the number of sessions listening for the events; if an event is truncated for a session then the ETW participant retries sending the event once.</span></span> <span data-ttu-id="a6e94-142">Relace, který je nakonfigurovaný tak, aby přijímal větší velikost datové části v tomto případě se zobrazí dvakrát událostí (event-zkrátí a zkrácený).</span><span class="sxs-lookup"><span data-stu-id="a6e94-142">In this case the session that is configured to accept a larger payload size will get the event twice (the non-truncated and truncated event).</span></span> <span data-ttu-id="a6e94-143">Duplikace jde zakázat tím, že nakonfigurujete všechny relace trasování událostí pro Windows pomocí stejného omezení velikosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="a6e94-143">Duplication can be prevented by configuring all the ETW sessions with same buffer size limits.</span></span>  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a><span data-ttu-id="a6e94-144">Přístup k Data sledování z účastníkovi trasování událostí pro Windows v prohlížeči událostí</span><span class="sxs-lookup"><span data-stu-id="a6e94-144">Accessing Tracking Data from an ETW Participant in the Event Viewer</span></span>  
 <span data-ttu-id="a6e94-145">Události, které jsou zapsány do relace trasování událostí pro Windows pomocí účastník sledování ETW je možný prostřednictvím prohlížeče událostí (při použití výchozí zprostředkovatel ID).</span><span class="sxs-lookup"><span data-stu-id="a6e94-145">Events that are written to an ETW session by the ETW tracking participant can be accessed through the Event Viewer (when using the default provider ID).</span></span> <span data-ttu-id="a6e94-146">To umožňuje rychlé zobrazení sledování záznamů, které bylo aktivováno tímto pracovním postupem.</span><span class="sxs-lookup"><span data-stu-id="a6e94-146">This allows for rapidly viewing of tracking records that have been emitted by the workflow.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a6e94-147">Sledování vyzařovaného události použití relace ID trasování událostí pro Windows v rozsahu od 100 do 199 zaznamenávat události.</span><span class="sxs-lookup"><span data-stu-id="a6e94-147">Tracking record events emitted to an ETW session use event IDs in the range of 100 through 199.</span></span>  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a><span data-ttu-id="a6e94-148">Chcete-li povolit zobrazení záznamů sledování v prohlížeči událostí</span><span class="sxs-lookup"><span data-stu-id="a6e94-148">To enable viewing the Tracking Records in Event Viewer</span></span>  
  
1. <span data-ttu-id="a6e94-149">Spusťte Prohlížeč událostí (EVENTVWR. SOUBOR EXE)</span><span class="sxs-lookup"><span data-stu-id="a6e94-149">Start the Event Viewer (EVENTVWR.EXE)</span></span>  
  
2. <span data-ttu-id="a6e94-150">Vyberte **Prohlížeč událostí, protokoly aplikací a služeb, Microsoft, Windows, aplikace Server-**.</span><span class="sxs-lookup"><span data-stu-id="a6e94-150">Select **Event Viewer, Applications and Services Logs, Microsoft, Windows, Application Server-Applications**.</span></span>  
  
3. <span data-ttu-id="a6e94-151">Klikněte pravým tlačítkem a ujistěte se, že **zobrazení, zobrazení a analýzu protokolů ladění** zaškrtnuto.</span><span class="sxs-lookup"><span data-stu-id="a6e94-151">Right-click and ensure that **View, Show Analytic and Debug logs** is selected.</span></span> <span data-ttu-id="a6e94-152">Pokud tomu tak není, vyberte ho, aby se vedle něj zobrazí zaškrtávací políčko.</span><span class="sxs-lookup"><span data-stu-id="a6e94-152">If not, select it so the check mark appears next to it.</span></span> <span data-ttu-id="a6e94-153">Zobrazí se **analytické**, **výkonu**, a **ladění** protokoly.</span><span class="sxs-lookup"><span data-stu-id="a6e94-153">This displays the **Analytic**, **Perf**, and **Debug** logs.</span></span>  
  
4. <span data-ttu-id="a6e94-154">Klikněte pravým tlačítkem myši **analytické** přihlaste a pak vyberte **povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="a6e94-154">Right-click the **Analytic** log and then select **Enable Log**.</span></span> <span data-ttu-id="a6e94-155">V souboru Server-Applications%4Analytic.etl %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application bude existovat do protokolu.</span><span class="sxs-lookup"><span data-stu-id="a6e94-155">The log will exist in the %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl file.</span></span>  
  
## <a name="custom-tracking-participant"></a><span data-ttu-id="a6e94-156">Vlastní sledování účastník</span><span class="sxs-lookup"><span data-stu-id="a6e94-156">Custom Tracking Participant</span></span>  
 <span data-ttu-id="a6e94-157">Účastník sledování rozhraní API umožňuje rozšíření modulu runtime sledování s uživatelem zadaný sledování účastník, který může obsahovat vlastní logiku ke zpracování záznamů sledování vyzařovaného modulu runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a6e94-157">The tracking participant API allows extension of the tracking runtime with a user-provided tracking participant that can include custom logic to handle tracking records emitted by the workflow runtime.</span></span> <span data-ttu-id="a6e94-158">Chcete-li napsat vlastní sledování účastník, musí implementovat Vývojář `Track` metodu <xref:System.Activities.Tracking.TrackingParticipant> třídy.</span><span class="sxs-lookup"><span data-stu-id="a6e94-158">To write a custom tracking participant, the developer must implement the `Track` method on the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="a6e94-159">Tato metoda je volána, když modul runtime pracovního postupu je vyzařovaného záznamem sledování.</span><span class="sxs-lookup"><span data-stu-id="a6e94-159">This method is called when a tracking record is emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="a6e94-160">Sledování účastníci odvozovat <xref:System.Activities.Tracking.TrackingParticipant> třídy.</span><span class="sxs-lookup"><span data-stu-id="a6e94-160">Tracking participants derive from the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="a6e94-161">Pokud systém <xref:System.Activities.Tracking.EtwTrackingParticipant> vydá událost událostí sledování pro Windows (ETW) pro jednotlivé záznamy sledování, přijaté.</span><span class="sxs-lookup"><span data-stu-id="a6e94-161">The system-provided <xref:System.Activities.Tracking.EtwTrackingParticipant> emits an Event Tracking for Windows (ETW) event for each tracking record that is received.</span></span> <span data-ttu-id="a6e94-162">Vytvoření vlastního účastníka sledování, je vytvořená třída, která je odvozena z <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="a6e94-162">To create a custom tracking participant, a class is created that derives from <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="a6e94-163">K zajištění funkce základní sledování, přepsat <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="a6e94-163">To provide basic tracking functionality, override <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span></span> <span data-ttu-id="a6e94-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> je volána, když záznamem sledování posílá modulem runtime a může zpracovat požadované způsobem.</span><span class="sxs-lookup"><span data-stu-id="a6e94-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> is called when a tracking record is sent by the runtime and can be processed in the desired manner.</span></span> <span data-ttu-id="a6e94-165">V následujícím příkladu vlastní sledování účastníka třída je definována, který vysílá všechny záznamy sledování v okně konzoly.</span><span class="sxs-lookup"><span data-stu-id="a6e94-165">In the following example, a custom tracking participant class is defined that emits all tracking records to the console window.</span></span> <span data-ttu-id="a6e94-166">Můžete také implementovat <xref:System.Activities.Tracking.TrackingParticipant> objekt, který zpracovává sledování záznamů asynchronně pomocí jeho `BeginTrack` a `EndTrack` metody</span><span class="sxs-lookup"><span data-stu-id="a6e94-166">You can also implement a <xref:System.Activities.Tracking.TrackingParticipant> object that processes the tracking records asynchronously using its `BeginTrack` and `EndTrack` methods</span></span>  
  
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
  
 <span data-ttu-id="a6e94-167">Pokud chcete použít konkrétní sledování účastník, zaregistrujte ho s instancí pracovního postupu, který chcete sledovat, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="a6e94-167">To use a particular tracking participant, register it with the workflow instance that you want to track, as shown in the following example.</span></span>  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="a6e94-168">V následujícím příkladu, pracovní postup, který se skládá z <xref:System.Activities.Statements.Sequence> aktivitu, která obsahuje <xref:System.Activities.Statements.WriteLine> vytvoření aktivity.</span><span class="sxs-lookup"><span data-stu-id="a6e94-168">In the following example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> activity is created.</span></span> <span data-ttu-id="a6e94-169">`ConsoleTrackingParticipant` Se přidá do rozšíření a je vyvolána pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="a6e94-169">The `ConsoleTrackingParticipant` is added to the extensions and the workflow is invoked.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="a6e94-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a6e94-170">See also</span></span>

- [<span data-ttu-id="a6e94-171">Windows Server App Fabric monitorování</span><span class="sxs-lookup"><span data-stu-id="a6e94-171">Windows Server App Fabric Monitoring</span></span>](https://go.microsoft.com/fwlink/?LinkId=201273)
- [<span data-ttu-id="a6e94-172">Monitorování aplikací pomocí App Fabric</span><span class="sxs-lookup"><span data-stu-id="a6e94-172">Monitoring Applications with App Fabric</span></span>](https://go.microsoft.com/fwlink/?LinkId=201275)
