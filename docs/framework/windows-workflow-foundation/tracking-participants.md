---
title: Účastníci sledování
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: a033b65125a562307c6247eeda93dcacb31f5382
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837646"
---
# <a name="tracking-participants"></a><span data-ttu-id="9f116-102">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="9f116-102">Tracking Participants</span></span>
<span data-ttu-id="9f116-103">Sledování účastníků je rozšiřitelné body, které umožňují vývojářům pracovního postupu získat přístup k <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objektům a zpracovat je.</span><span class="sxs-lookup"><span data-stu-id="9f116-103">Tracking participants are extensibility points that allow a workflow developer to access <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objects and process them.</span></span> [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] <span data-ttu-id="9f116-104">zahrnuje standardního účastníka sledování, který zapisuje záznamy sledování jako události trasování událostí pro Windows (ETW).</span><span class="sxs-lookup"><span data-stu-id="9f116-104">includes a standard tracking participant that writes tracking records as Event Tracing for Windows (ETW) events.</span></span> <span data-ttu-id="9f116-105">Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.</span><span class="sxs-lookup"><span data-stu-id="9f116-105">If that does not meet your requirements, you can also write a custom tracking participant.</span></span>  
  
## <a name="tracking-participants"></a><span data-ttu-id="9f116-106">Účastníci sledování</span><span class="sxs-lookup"><span data-stu-id="9f116-106">Tracking Participants</span></span>  
 <span data-ttu-id="9f116-107">Sledovací infrastruktura umožňuje použití filtru u odchozích záznamů sledování tak, aby se účastník mohl přihlásit k odběru podmnožiny záznamů.</span><span class="sxs-lookup"><span data-stu-id="9f116-107">The tracking infrastructure allows the application of a filter on the outgoing tracking records such that a participant can subscribe to a subset of the records.</span></span> <span data-ttu-id="9f116-108">Mechanismus použití filtru je prostřednictvím sledovacího profilu.</span><span class="sxs-lookup"><span data-stu-id="9f116-108">The mechanism to apply a filter is through a tracking profile.</span></span>  
  
 <span data-ttu-id="9f116-109">Programovací model Windows Workflow Foundation (WF) v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] poskytuje sledování účastníka, který zapisuje záznamy sledování do relace trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="9f116-109">Windows Workflow Foundation (WF) in [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] provides a tracking participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="9f116-110">Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru.</span><span class="sxs-lookup"><span data-stu-id="9f116-110">The participant is configured on a workflow service by adding a tracking-specific behavior in a configuration file.</span></span> <span data-ttu-id="9f116-111">Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč.</span><span class="sxs-lookup"><span data-stu-id="9f116-111">Enabling an ETW tracking participant allows tracking records to be viewed in the event viewer.</span></span> <span data-ttu-id="9f116-112">Ukázka sady SDK pro sledování založené na ETW je dobrým způsobem, jak se seznámit se sledováním pomocí ETW na základě sledování.</span><span class="sxs-lookup"><span data-stu-id="9f116-112">The SDK sample for ETW-based tracking is a good way to get familiar with WF tracking using the ETW-based tracking participant.</span></span>  
  
## <a name="etw-tracking-participant"></a><span data-ttu-id="9f116-113">Účastník sledování ETW</span><span class="sxs-lookup"><span data-stu-id="9f116-113">ETW Tracking Participant</span></span>  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] <span data-ttu-id="9f116-114">obsahuje účastník sledování ETW, který zapisuje záznamy sledování do relace trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="9f116-114">includes an ETW Tracking Participant that writes the tracking records to an ETW session.</span></span> <span data-ttu-id="9f116-115">To se provádí velice účinným způsobem s minimálním dopadem na výkon aplikace nebo na propustnost serveru.</span><span class="sxs-lookup"><span data-stu-id="9f116-115">This is done in a very efficient manner with minimal impact to the application’s performance or to the server’s throughput.</span></span> <span data-ttu-id="9f116-116">Výhodou použití standardního účastníka sledování ETW je, že záznamy sledování, které obdrží, se dají zobrazit s ostatními protokoly aplikací a systémem ve Windows Prohlížeč událostí.</span><span class="sxs-lookup"><span data-stu-id="9f116-116">An advantage of using the standard ETW tracking participant is that the tracking records it receives can be viewed with the other application and system logs in the Windows Event Viewer.</span></span>  
  
 <span data-ttu-id="9f116-117">Standardní účastník sledování ETW je nakonfigurovaný v souboru Web. config, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9f116-117">The standard ETW tracking participant is configured in the Web.config file as shown in the following example.</span></span>  
  
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
> <span data-ttu-id="9f116-118">Pokud není zadán název `trackingProfile`, například pouze `<etwTracking/>` nebo `<etwTracking profileName=""/>`, je použit výchozí profil sledování nainstalovaný spolu s [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v souboru Machine. config.</span><span class="sxs-lookup"><span data-stu-id="9f116-118">If a `trackingProfile` name is not specified, such as just `<etwTracking/>` or `<etwTracking profileName=""/>`, then the default tracking profile installed with the [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] in the Machine.config file is used.</span></span>  
  
 <span data-ttu-id="9f116-119">V souboru Machine. config se výchozí profil sledování přihlašuje k odběru záznamů a chyb instancí pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9f116-119">In the Machine.config file, the default tracking profile subscribes to workflow instance records and faults.</span></span>  
  
 <span data-ttu-id="9f116-120">V trasování událostí pro Windows se události zapisují do relace ETW prostřednictvím ID poskytovatele.</span><span class="sxs-lookup"><span data-stu-id="9f116-120">In ETW, events are written to the ETW session through a provider ID.</span></span> <span data-ttu-id="9f116-121">ID zprostředkovatele, které účastník sledování ETW používá pro zápis záznamů sledování do ETW, je definováno v části Diagnostika v souboru Web. config (v části `<system.serviceModel><diagnostics>`).</span><span class="sxs-lookup"><span data-stu-id="9f116-121">The provider ID that the ETW tracking participant uses for writing the tracking records to ETW is defined in the diagnostics section of the Web.config file (under `<system.serviceModel><diagnostics>`).</span></span> <span data-ttu-id="9f116-122">Ve výchozím nastavení používá účastník sledování ETW výchozí ID poskytovatele, pokud nebyl zadán, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9f116-122">By default, the ETW tracking participant uses a default provider ID when one has not been specified, as shown in the following example.</span></span>  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 <span data-ttu-id="9f116-123">Následující ilustrace znázorňuje tok sledování dat prostřednictvím účastníka sledování trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="9f116-123">The following illustration shows the flow of tracking data through the ETW tracking participant.</span></span> <span data-ttu-id="9f116-124">Jakmile se data sledování dorazí na relaci trasování událostí pro Windows, dá se k ní dostat několika způsoby.</span><span class="sxs-lookup"><span data-stu-id="9f116-124">Once the tracking data reaches the ETW session, it can be accessed in a number of ways.</span></span> <span data-ttu-id="9f116-125">Jedním z nejužitečnějších způsobů, jak získat přístup k těmto událostem, je prostřednictvím Prohlížeč událostí, což je běžný nástroj pro Windows, který se používá k zobrazení protokolů a trasování z aplikací a služeb.</span><span class="sxs-lookup"><span data-stu-id="9f116-125">One of the most useful ways to access these events is through Event Viewer, a common Windows tool used for viewing logs and traces from applications and services.</span></span>  
  
 ![Tok sledování dat prostřednictvím zprostředkovatele sledování ETW.](./media/tracking-participants/tracking-data-event-tracing-windows-provider.gif)  
  
## <a name="tracking-participant-event-data"></a><span data-ttu-id="9f116-127">Sledování dat událostí účastníka</span><span class="sxs-lookup"><span data-stu-id="9f116-127">Tracking Participant Event Data</span></span>  
 <span data-ttu-id="9f116-128">Účastník sledování rozserializován data sledovaných událostí do relace ETW ve formátu jedné události na záznam sledování.</span><span class="sxs-lookup"><span data-stu-id="9f116-128">A tracking participant serializes tracked event data to an ETW session in the format of one event per tracking record.</span></span>  <span data-ttu-id="9f116-129">Událost se identifikuje pomocí ID v rozsahu 100 až 199.</span><span class="sxs-lookup"><span data-stu-id="9f116-129">An event is identified using an ID within the range of 100 through 199.</span></span> <span data-ttu-id="9f116-130">Definice záznamů událostí sledování, které generuje účastník sledování, najdete v tématu [sledovací události – referenční](tracking-events-reference.md) informace.</span><span class="sxs-lookup"><span data-stu-id="9f116-130">For definitions of the tracking event records emitted by a tracking participant, see the [Tracking Events Reference](tracking-events-reference.md) topic.</span></span>  
  
 <span data-ttu-id="9f116-131">Velikost události ETW je omezená velikostí vyrovnávací paměti ETW nebo maximální datovou částí pro událost ETW, podle toho, jaká hodnota je menší.</span><span class="sxs-lookup"><span data-stu-id="9f116-131">The size of an ETW event is limited by the ETW buffer size, or the by the maximum payload for an ETW event, whichever value is smaller.</span></span> <span data-ttu-id="9f116-132">Pokud velikost události překročí jedno z těchto limitů ETW, událost se zkrátí a její obsah se odebere libovolným způsobem.</span><span class="sxs-lookup"><span data-stu-id="9f116-132">If the size of the event exceeds either of these ETW limits, the event is truncated and its content removed in an arbitrary manner.</span></span> <span data-ttu-id="9f116-133">Proměnné, argumenty, poznámky a vlastní data nejsou selektivně odebírány.</span><span class="sxs-lookup"><span data-stu-id="9f116-133">Variables, arguments, annotations and custom data are not selectively removed.</span></span> <span data-ttu-id="9f116-134">V případě zkrácení jsou všechny tyto hodnoty zkráceny bez ohledu na hodnotu, která způsobila, že velikost události překročila limit ETW.</span><span class="sxs-lookup"><span data-stu-id="9f116-134">In the case of truncation, all of these are truncated regardless of the value that caused the event size to exceed the ETW limit.</span></span>  <span data-ttu-id="9f116-135">Odebraná data se nahradí `<item>..<item>`.</span><span class="sxs-lookup"><span data-stu-id="9f116-135">The removed data is replaced with `<item>..<item>`.</span></span>  
  
 <span data-ttu-id="9f116-136">Komplexní typy v proměnných, argumentech a vlastních datových položkách jsou serializovány do záznamu události ETW pomocí třídy <xref:System.Runtime.Serialization.NetDataContractSerializer>.</span><span class="sxs-lookup"><span data-stu-id="9f116-136">Complex types in variables, arguments, and custom data items are serialized to the ETW event record using the <xref:System.Runtime.Serialization.NetDataContractSerializer> class.</span></span> <span data-ttu-id="9f116-137">Tato třída zahrnuje informace o typu CLR v serializované parní XML.</span><span class="sxs-lookup"><span data-stu-id="9f116-137">This class includes CLR-type information in the serialized XML steam.</span></span>  
  
 <span data-ttu-id="9f116-138">Zkrácení dat datové části z důvodu omezení ETW může mít za následek duplicitní záznamy sledování, které jsou odesílány do relace trasování událostí pro Windows.</span><span class="sxs-lookup"><span data-stu-id="9f116-138">Truncation of payload data due to ETW limits can result in duplicate tracking records being sent to an ETW session.</span></span> <span data-ttu-id="9f116-139">Tato situace může nastat, pokud více než jedna relace naslouchá událostem a relace mají pro události jiné limity zatížení.</span><span class="sxs-lookup"><span data-stu-id="9f116-139">This can occur if more than one session is listening for the events and the sessions have different payload limits for the events.</span></span>  
  
 <span data-ttu-id="9f116-140">Pro relaci s nižším limitem může být událost zkrácena.</span><span class="sxs-lookup"><span data-stu-id="9f116-140">For  the session with the lower limit the event may be truncated.</span></span> <span data-ttu-id="9f116-141">Účastník sledování ETW nemá žádné znalosti o počtu relací, které na události naslouchá. Pokud je událost pro relaci zkrácená, pak se pokusy účastníka trasování událostí pro Windows odešlou událost.</span><span class="sxs-lookup"><span data-stu-id="9f116-141">The ETW tracking participant does not have any knowledge of the number of sessions listening for the events; if an event is truncated for a session then the ETW participant retries sending the event once.</span></span> <span data-ttu-id="9f116-142">V takovém případě by relace, která je nakonfigurovaná tak, aby přijímala větší velikost datové části, měla událost dvakrát (událost, která není zkrácená a zkrácená).</span><span class="sxs-lookup"><span data-stu-id="9f116-142">In this case the session that is configured to accept a larger payload size will get the event twice (the non-truncated and truncated event).</span></span> <span data-ttu-id="9f116-143">Duplikaci lze zabránit konfigurací všech relací ETW se stejnými limity velikosti vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="9f116-143">Duplication can be prevented by configuring all the ETW sessions with same buffer size limits.</span></span>  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a><span data-ttu-id="9f116-144">Přístup k datům sledování z účastníka ETW v Prohlížeč událostí</span><span class="sxs-lookup"><span data-stu-id="9f116-144">Accessing Tracking Data from an ETW Participant in the Event Viewer</span></span>  
 <span data-ttu-id="9f116-145">Události, které jsou zapsány do relace ETW pomocí účastníka sledování ETW, jsou k dispozici prostřednictvím Prohlížeč událostí (při použití výchozího ID poskytovatele).</span><span class="sxs-lookup"><span data-stu-id="9f116-145">Events that are written to an ETW session by the ETW tracking participant can be accessed through the Event Viewer (when using the default provider ID).</span></span> <span data-ttu-id="9f116-146">To umožňuje rychle zobrazit záznamy sledování, které byly vygenerovány pracovním postupem.</span><span class="sxs-lookup"><span data-stu-id="9f116-146">This allows for rapidly viewing of tracking records that have been emitted by the workflow.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="9f116-147">Sledování událostí záznamu emitovaných v relaci ETW používají ID událostí v rozsahu od 100 do 199.</span><span class="sxs-lookup"><span data-stu-id="9f116-147">Tracking record events emitted to an ETW session use event IDs in the range of 100 through 199.</span></span>  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a><span data-ttu-id="9f116-148">Povolení zobrazení záznamů sledování v Prohlížeč událostí</span><span class="sxs-lookup"><span data-stu-id="9f116-148">To enable viewing the Tracking Records in Event Viewer</span></span>  
  
1. <span data-ttu-id="9f116-149">Spusťte Prohlížeč událostí (EVENTVWR. PROGRAMU</span><span class="sxs-lookup"><span data-stu-id="9f116-149">Start the Event Viewer (EVENTVWR.EXE)</span></span>  
  
2. <span data-ttu-id="9f116-150">Vyberte **Prohlížeč událostí, protokoly aplikací a služeb, Microsoft, Windows, aplikační server – aplikace**.</span><span class="sxs-lookup"><span data-stu-id="9f116-150">Select **Event Viewer, Applications and Services Logs, Microsoft, Windows, Application Server-Applications**.</span></span>  
  
3. <span data-ttu-id="9f116-151">Klikněte pravým tlačítkem a ujistěte se, že je vybraná možnost **Zobrazit, zobrazit protokoly pro analýzu a ladění** .</span><span class="sxs-lookup"><span data-stu-id="9f116-151">Right-click and ensure that **View, Show Analytic and Debug logs** is selected.</span></span> <span data-ttu-id="9f116-152">Pokud ne, vyberte ho, aby se vedle něho zobrazila značka zaškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="9f116-152">If not, select it so the check mark appears next to it.</span></span> <span data-ttu-id="9f116-153">Tím se zobrazí protokoly o **analýze**, **výkonu**a **ladění** .</span><span class="sxs-lookup"><span data-stu-id="9f116-153">This displays the **Analytic**, **Perf**, and **Debug** logs.</span></span>  
  
4. <span data-ttu-id="9f116-154">Klikněte pravým tlačítkem na **analytický** protokol a pak vyberte **Povolit protokol**.</span><span class="sxs-lookup"><span data-stu-id="9f116-154">Right-click the **Analytic** log and then select **Enable Log**.</span></span> <span data-ttu-id="9f116-155">Protokol bude existovat v souboru nalytic. ETL%SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications %4.</span><span class="sxs-lookup"><span data-stu-id="9f116-155">The log will exist in the %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications%4Analytic.etl file.</span></span>  
  
## <a name="custom-tracking-participant"></a><span data-ttu-id="9f116-156">Účastník vlastního sledování</span><span class="sxs-lookup"><span data-stu-id="9f116-156">Custom Tracking Participant</span></span>  
 <span data-ttu-id="9f116-157">Rozhraní API sledování účastníka umožňuje rozšíření sledovacího prostředí sledování s uživatelem poskytnutým účastníkem sledování, které může zahrnovat vlastní logiku pro zpracování záznamů sledování generovaných modulem runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9f116-157">The tracking participant API allows extension of the tracking runtime with a user-provided tracking participant that can include custom logic to handle tracking records emitted by the workflow runtime.</span></span> <span data-ttu-id="9f116-158">Chcete-li napsat vlastního účastníka sledování, vývojář musí implementovat metodu `Track` třídy <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="9f116-158">To write a custom tracking participant, the developer must implement the `Track` method on the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="9f116-159">Tato metoda je volána, když je záznam sledování generován modulem runtime pracovního postupu.</span><span class="sxs-lookup"><span data-stu-id="9f116-159">This method is called when a tracking record is emitted by the workflow runtime.</span></span>  
  
 <span data-ttu-id="9f116-160">Sledování účastníků je odvozeno od <xref:System.Activities.Tracking.TrackingParticipant> třídy.</span><span class="sxs-lookup"><span data-stu-id="9f116-160">Tracking participants derive from the <xref:System.Activities.Tracking.TrackingParticipant> class.</span></span> <span data-ttu-id="9f116-161">Zadaný systém <xref:System.Activities.Tracking.EtwTrackingParticipant> emituje událost sledování událostí pro Windows (ETW) pro každý přijatý záznam sledování.</span><span class="sxs-lookup"><span data-stu-id="9f116-161">The system-provided <xref:System.Activities.Tracking.EtwTrackingParticipant> emits an Event Tracking for Windows (ETW) event for each tracking record that is received.</span></span> <span data-ttu-id="9f116-162">Chcete-li vytvořit vlastního účastníka sledování, je vytvořena třída, která je odvozena z <xref:System.Activities.Tracking.TrackingParticipant>.</span><span class="sxs-lookup"><span data-stu-id="9f116-162">To create a custom tracking participant, a class is created that derives from <xref:System.Activities.Tracking.TrackingParticipant>.</span></span> <span data-ttu-id="9f116-163">Chcete-li poskytnout základní funkce sledování, přepište <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f116-163">To provide basic tracking functionality, override <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>.</span></span> <span data-ttu-id="9f116-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> se volá, když se záznam sledování pošle za běhu a dá se zpracovat požadovaným způsobem.</span><span class="sxs-lookup"><span data-stu-id="9f116-164"><xref:System.Activities.Tracking.TrackingParticipant.Track%2A> is called when a tracking record is sent by the runtime and can be processed in the desired manner.</span></span> <span data-ttu-id="9f116-165">V následujícím příkladu je definována třída vlastního účastníka sledování, která generuje všechny záznamy sledování do okna konzoly.</span><span class="sxs-lookup"><span data-stu-id="9f116-165">In the following example, a custom tracking participant class is defined that emits all tracking records to the console window.</span></span> <span data-ttu-id="9f116-166">Můžete také implementovat objekt <xref:System.Activities.Tracking.TrackingParticipant>, který asynchronně zpracovává záznamy sledování pomocí jeho `BeginTrack` a `EndTrack` metod.</span><span class="sxs-lookup"><span data-stu-id="9f116-166">You can also implement a <xref:System.Activities.Tracking.TrackingParticipant> object that processes the tracking records asynchronously using its `BeginTrack` and `EndTrack` methods</span></span>  
  
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
  
 <span data-ttu-id="9f116-167">Chcete-li použít konkrétního účastníka sledování, zaregistrujte jej s instancí pracovního postupu, kterou chcete sledovat, jak je znázorněno v následujícím příkladu.</span><span class="sxs-lookup"><span data-stu-id="9f116-167">To use a particular tracking participant, register it with the workflow instance that you want to track, as shown in the following example.</span></span>  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 <span data-ttu-id="9f116-168">V následujícím příkladu se vytvoří pracovní postup, který se skládá z <xref:System.Activities.Statements.Sequence> aktivity, která obsahuje aktivitu <xref:System.Activities.Statements.WriteLine>.</span><span class="sxs-lookup"><span data-stu-id="9f116-168">In the following example, a workflow that consists of a <xref:System.Activities.Statements.Sequence> activity that contains a <xref:System.Activities.Statements.WriteLine> activity is created.</span></span> <span data-ttu-id="9f116-169">`ConsoleTrackingParticipant` se přidá do rozšíření a vyvolají se pracovní postup.</span><span class="sxs-lookup"><span data-stu-id="9f116-169">The `ConsoleTrackingParticipant` is added to the extensions and the workflow is invoked.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9f116-170">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9f116-170">See also</span></span>

- <span data-ttu-id="9f116-171">[Monitorování Windows Server App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9f116-171">[Windows Server App Fabric Monitoring](https://docs.microsoft.com/previous-versions/appfabric/ee677251(v=azure.10))</span></span>
- <span data-ttu-id="9f116-172">[Monitorování aplikací pomocí prostředků infrastruktury aplikace](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span><span class="sxs-lookup"><span data-stu-id="9f116-172">[Monitoring Applications with App Fabric](https://docs.microsoft.com/previous-versions/appfabric/ee677276(v=azure.10))</span></span>
