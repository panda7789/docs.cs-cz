---
title: Sledování účastníci
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: e346e0df3417f6ac83854bd96d6e64dcf103ea93
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43488271"
---
# <a name="tracking-participants"></a>Sledování účastníci
Sledování účastníci jsou body rozšiřitelnosti, které umožňují vývojář pracovního postupu pro přístup k <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objektů a jejich zpracování. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)] zahrnuje účastník standardní sledování, který zapíše záznamy sledování jako události trasování událostí pro Windows (ETW). Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.  
  
## <a name="tracking-participants"></a>Sledování účastníci  
 Sledování infrastruktury umožňuje aplikaci filtru na odchozí záznamy sledování, tak, aby účastníka se přihlásit k odběru podmnožinu záznamů. Mechanismus, který chcete použít filtr je prostřednictvím profilu sledování.  
  
 Windows Workflow Foundation (WF) v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] poskytuje sledování účastník, který zapíše záznamy sledování k relaci ETW. Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru. Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč. Ukázka sady SDK pro sledování na základě trasování událostí pro Windows je dobrým způsobem, jak Seznamte se s pomocí trasování událostí pro Windows na základě sledování účastník sledování WF.  
  
## <a name="etw-tracking-participant"></a>Účastník sledování ETW  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] zahrnuje účastník sledování ETW, který zapíše záznamy sledování k relaci ETW. To je velice efektivním způsobem s minimálním dopadem na výkon vaší aplikace a propustnosti serveru. Výhodou použití standardní účastník sledování ETW je, že záznamy sledování, které obdrží lze zobrazit v aplikaci a systém zaprotokoluje v prohlížeči událostí Windows.  
  
 Standardní účastník sledování ETW konfigurován v souboru Web.config, jak je znázorněno v následujícím příkladu.  
  
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
>  Pokud `trackingProfile` název není zadaný, jako například právě `<etwTracking/>` nebo `<etwTracking profileName=""/>`, pak výchozí profil sledování tracking profile součástí [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v souboru Machine.config soubor se používá.  
  
 V souboru Machine.config výchozí profil sledování tracking profile přihlásí k záznamům instance pracovního postupu a chyb.  
  
 V trasování událostí pro Windows události se zapisují do relace ETW pomocí ID zprostředkovatele. Poskytovatel ID, které trasování událostí pro Windows pro sledování účastníka používá k zápisu sledování záznamy do trasování událostí pro Windows je definovaná v části Diagnostika souboru Web.config (v části `<system.serviceModel><diagnostics>`). Ve výchozím nastavení účastník sledování ETW používá výchozí ID poskytovatele když nebyl zadán jeden, jak je znázorněno v následujícím příkladu.  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 Následující obrázek znázorňuje tok dat prostřednictvím účastník sledování ETW sledování. Jakmile se data sledování dosáhne relace trasování událostí pro Windows, můžete získat přístup v několika způsoby. Jedním z nejužitečnějších způsobů pro přístup k těmto událostem je prostřednictvím prohlížeče událostí, běžné nástroje Windows používá k zobrazení protokolů a trasování z aplikací a služeb.  
  
 ![Tok pro sledování a trasování událostí pro Windows Sledování poskytovatele](../../../docs/framework/windows-workflow-foundation/media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")  
  
## <a name="tracking-participant-event-data"></a>Data sledování účastníků události  
 Sledování účastník serializuje data sledovaných událostí do relace trasování událostí pro Windows ve formátu jednu událost za každou sledování záznamů.  Událost je identifikována pomocí ID v rozsahu od 100 do 199. Definice událostí sledování záznamů, protože ho vygeneroval sledování účastník, najdete v článku [sledování události – referenční informace](../../../docs/framework/windows-workflow-foundation/tracking-events-reference.md) tématu.  
  
 Velikost události trasování událostí pro Windows je omezena velikost vyrovnávací paměti trasování událostí pro Windows, nebo maximální velikost datové části události trasování událostí pro Windows, podle toho, která hodnota je menší. Pokud velikost události překračuje jednu z těchto omezení trasování událostí pro Windows, událostí je zkrácena a její obsah odebrat libovolné způsobem. Selektivně se neodeberou proměnné, argumenty, poznámky a vlastní data. V případě zkrácení všechny z nich se zkrátí bez ohledu na hodnotu, která způsobila velikost události k překročení limitu trasování událostí pro Windows.  Odebrání dat je nahrazena `<item>..<item>`.  
  
 Komplexní typy, které do proměnné, argumenty a vlastní datové položky se serializují pomocí záznamu události trasování událostí pro Windows [NetDataContractSerializer třídy](https://go.microsoft.com/fwlink/?LinkId=177537). Tato třída obsahuje informace o typu modulu CLR v serializovaná datový proud XML.  
  
 Zkrácení datové části kvůli omezení trasování událostí pro Windows může způsobit duplicitní sledování záznamů odesílané do relace trasování událostí pro Windows. Tato situace může nastat, pokud více než jedna relace přijímá události a relace mají různé datové části limity pro události.  
  
 Pro relace s dolní mez události můžou být zkrácené. Účastník sledování ETW nemá žádnou znalost počet relací naslouchání událostem; Pokud je událost zkrácenému pro relaci pak účastníka opakované pokusy trasování událostí pro Windows po odeslání události. Relace, který je nakonfigurovaný tak, aby přijímal větší velikost datové části v tomto případě se zobrazí dvakrát událostí (event-zkrátí a zkrácený). Duplikace jde zakázat tím, že nakonfigurujete všechny relace trasování událostí pro Windows pomocí stejného omezení velikosti vyrovnávací paměti.  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a>Přístup k Data sledování z účastníkovi trasování událostí pro Windows v prohlížeči událostí  
 Události, které jsou zapsány do relace trasování událostí pro Windows pomocí účastník sledování ETW je možný prostřednictvím prohlížeče událostí (při použití výchozí zprostředkovatel ID). To umožňuje rychlé zobrazení sledování záznamů, které bylo aktivováno tímto pracovním postupem.  
  
> [!NOTE]
>  Sledování vyzařovaného události použití relace ID trasování událostí pro Windows v rozsahu od 100 do 199 zaznamenávat události.  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a>Chcete-li povolit zobrazení záznamů sledování v prohlížeči událostí  
  
1.  Spusťte Prohlížeč událostí (EVENTVWR. SOUBOR EXE)  
  
2.  Vyberte **Prohlížeč událostí, protokoly aplikací a služeb, Microsoft, Windows, aplikace Server-**.  
  
3.  Klikněte pravým tlačítkem a ujistěte se, že **zobrazení, zobrazení a analýzu protokolů ladění** zaškrtnuto. Pokud tomu tak není, vyberte ho, aby se vedle něj zobrazí zaškrtávací políčko. Zobrazí se **analytické**, **výkonu**, a **ladění** protokoly.  
  
4.  Klikněte pravým tlačítkem myši **analytické** přihlaste a pak vyberte **povolit protokol**. V souboru Server-Applications%4Analytic.etl %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application bude existovat do protokolu.  
  
## <a name="custom-tracking-participant"></a>Vlastní sledování účastník  
 Účastník sledování rozhraní API umožňuje rozšíření modulu runtime sledování s uživatelem zadaný sledování účastník, který může obsahovat vlastní logiku ke zpracování záznamů sledování vyzařovaného modulu runtime pracovního postupu. Chcete-li napsat vlastní sledování účastník, musí implementovat Vývojář `Track` metodu <xref:System.Activities.Tracking.TrackingParticipant> třídy. Tato metoda je volána, když modul runtime pracovního postupu je vyzařovaného záznamem sledování.  
  
 Sledování účastníci odvozovat <xref:System.Activities.Tracking.TrackingParticipant> třídy. Pokud systém <xref:System.Activities.Tracking.EtwTrackingParticipant> vydá událost událostí sledování pro Windows (ETW) pro jednotlivé záznamy sledování, přijaté. Vytvoření vlastního účastníka sledování, je vytvořená třída, která je odvozena z <xref:System.Activities.Tracking.TrackingParticipant>. K zajištění funkce základní sledování, přepsat <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>. <xref:System.Activities.Tracking.TrackingParticipant.Track%2A> je volána, když záznamem sledování posílá modulem runtime a může zpracovat požadované způsobem. V následujícím příkladu vlastní sledování účastníka třída je definována, který vysílá všechny záznamy sledování v okně konzoly. Můžete také implementovat <xref:System.Activities.Tracking.TrackingParticipant> objekt, který zpracovává sledování záznamů asynchronně pomocí jeho `BeginTrack` a `EndTrack` metody  
  
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
  
 Pokud chcete použít konkrétní sledování účastník, zaregistrujte ho s instancí pracovního postupu, který chcete sledovat, jak je znázorněno v následujícím příkladu.  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 V následujícím příkladu, pracovní postup, který se skládá z <xref:System.Activities.Statements.Sequence> aktivitu, která obsahuje <xref:System.Activities.Statements.WriteLine> vytvoření aktivity. `ConsoleTrackingParticipant` Se přidá do rozšíření a je vyvolána pracovního postupu.  
  
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
  
## <a name="see-also"></a>Viz také  
 [Windows Server App Fabric monitorování](https://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorování aplikací pomocí App Fabric](https://go.microsoft.com/fwlink/?LinkId=201275)
