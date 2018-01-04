---
title: "Sledování účastníků"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
caps.latest.revision: "24"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f335695c86037d792b17b98080b7a2e668ac1df5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="tracking-participants"></a>Sledování účastníků
Sledování účastníků jsou body rozšiřitelnosti, které umožňují vývojář pracovního postupu pro přístup k <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> objekty a jejich zpracování. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]obsahuje standardní sledování člena, který zapíše sledování záznamů jako události trasování událostí pro Windows (ETW). Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.  
  
## <a name="tracking-participants"></a>Sledování účastníků  
 Sledování infrastruktury umožňuje použití filtru v odchozí záznamy sledování tak, aby účastník se mohou přihlásit k podmnožině záznamy. Mechanismus, který chcete použít filtr je prostřednictvím profil sledování.  
  
 [!INCLUDE[wf](../../../includes/wf-md.md)]v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] poskytuje sledování člena, který zapíše záznamy sledování relaci trasování událostí pro Windows. Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru. Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč. Ukázka sady SDK pro sledování na základě trasování událostí pro Windows je dobrý způsob, jak Seznamte se s WF sledování pomocí účastník na základě trasování událostí pro Windows Sledování.  
  
## <a name="etw-tracking-participant"></a>Trasování událostí pro Windows Sledování účastník  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]zahrnuje trasování událostí pro Windows Sledování člena, který zapíše záznamy sledování relaci trasování událostí pro Windows. Důvodem je velmi efektivní způsobem s minimálním dopadem na výkon aplikace a propustnost serveru. Výhodou použití standardní sledování účastník trasování událostí pro Windows je, že záznamy sledování, které obdrží lze zobrazit v jiné aplikaci a systém zaprotokoluje v prohlížeči událostí systému Windows.  
  
 Standardní sledování účastník trasování událostí pro Windows je nakonfigurovat v souboru Web.config, jak je znázorněno v následujícím příkladu.  
  
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
>  Pokud `trackingProfile` není zadán název, například právě `<etwTracking/>` nebo `<etwTracking profileName=""/>`, pak výchozí sledování nainstalovaný s profil [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v souboru Machine.config soubor je používán.  
  
 V souboru Machine.config. výchozí sledování profil jako odběratel u záznamů instance pracovního postupu a chyb.  
  
 Trasování událostí pro Windows události se zapisují do relace trasování pomocí ID zprostředkovatele. Zprostředkovatel ID trasování sledování účastnické používá k zápisu sledování zaznamenává do trasování událostí pro Windows je definována v části Diagnostika v souboru Web.config (v části `<system.serviceModel><diagnostics>`). Ve výchozím nastavení účastník sledování ETW používá výchozí zprostředkovatel ID při nebyl zadán jeden, jak je znázorněno v následujícím příkladu.  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 Následující obrázek znázorňuje tok data prostřednictvím účastník sledování ETW sledování. Jakmile se data sledování dosáhne relace trasování událostí pro Windows, můžete získat přístup v mnoha různými způsoby. Jedním z nejužitečnějších způsobů pro přístup k těmto událostem je prostřednictvím prohlížeče událostí, běžné nástroj Windows používá k zobrazení protokolů a tras z aplikací a služeb.  
  
 ![Tok sledování a zprostředkovatele trasování událostí pro Windows Sledování](../../../docs/framework/windows-workflow-foundation/media/trackingdatathroughetwparticipant.gif "TrackingDatathroughETWParticipant")  
  
## <a name="tracking-participant-event-data"></a>Sledování dat účastnické událostí  
 Sledování účastník, který serializuje data sledovaných událostí na relaci trasování událostí pro Windows ve formátu jedna událost na záznam o sledování.  Událost je identifikován pomocí ID, které v rozsahu 100 až 199. Definice sledování události záznamy vygenerované sledování účastník, najdete v článku [sledování událostí odkaz](../../../docs/framework/windows-workflow-foundation/tracking-events-reference.md) tématu.  
  
 Velikost událost trasování událostí pro Windows je omezena velikost vyrovnávací paměti ETW, nebo podle maximální datové části pro událost trasování událostí pro Windows, podle toho, která hodnota je menší. Pokud velikost události překročí některý z těchto mezních hodnot trasování událostí pro Windows, se zkrátí události a její obsah odebrat libovolný způsobem. Selektivně se neodeberou proměnné, argumenty, poznámky a vlastní data. V případě zkrácení všechny z nich se zkrátí bez ohledu na hodnotu, která způsobila, že na velikost události překročila omezení trasování událostí pro Windows.  Odebrané data se nahradí `<item>..<item>`.  
  
 Komplexní typy, které do proměnné, argumenty, a vlastní datové položky se serializují na záznam události trasování událostí pro Windows pomocí [NetDataContractSerializer třída](http://go.microsoft.com/fwlink/?LinkId=177537). Tato třída obsahuje informace o typu CLR v serializovaný datový proud XML.  
  
 Zkrácení datové části z důvodu omezení trasování událostí pro Windows může způsobit duplicitní sledování záznamů odesílána relaci trasování událostí pro Windows. Tato situace může nastat, pokud naslouchá více než jednu relaci události, a přihlásit se k relacím omezení různé datové části události.  
  
 Pro relaci s nižší limit události mohou být zkráceny. Účastník sledování ETW nemá žádnou znalost počet relací, naslouchání událostem; Pokud událost se zkrátí pro relaci pak účastnické opakování ETW jednou odeslání události. Relace, který je nakonfigurovaný tak, aby přijímal větší velikost datové části v tomto případě získají dvakrát událostí (událost-zkrácen a zkrácený). Duplikace se dá zabránit tak, že nakonfigurujete všechny relace trasování událostí pro Windows s stejné omezení velikosti vyrovnávací paměti.  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a>Přístup ke sledování dat od účastníka trasování událostí pro Windows v prohlížeči událostí  
 Události, které se zapisují do relaci trasování událostí pro Windows účastníkem sledování, trasování událostí pro Windows je přístupná prostřednictvím prohlížeče událostí (při použití výchozí zprostředkovatel ID). To umožňuje rychle zobrazení sledování záznamů, které vyvolaly pracovního postupu.  
  
> [!NOTE]
>  Sledování záznamů události vygenerované pro událost použití relace ID trasování událostí pro Windows v rozsahu 100 až 199.  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a>Chcete-li povolit zobrazení záznamů sledování v prohlížeči událostí  
  
1.  Spuštění prohlížeče událostí (EVENTVWR. SOUBOR EXE)  
  
2.  Vyberte **Prohlížeč událostí, protokoly aplikací a služeb, aplikací společnosti Microsoft, Windows Server – aplikace**.  
  
3.  Klikněte pravým tlačítkem a ujistěte se, že **zobrazení, zobrazit ladění protokoly a** je vybrána. Pokud ne, vyberte ho tak zaškrtnutí se zobrazí vedle sebe. Zobrazí se **analytické**, **výkonu**, a **ladění** protokoly.  
  
4.  Klikněte pravým tlačítkem myši **analytické** protokolu a potom vyberte **povolit protokol**. V protokolu budou existovat v souboru Server-Applications%4Analytic.etl %SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application.  
  
## <a name="custom-tracking-participant"></a>Vlastní sledování účastník  
 Sledování účastník rozhraní API umožňuje rozšíření modulu runtime sledování s účastníkem sledování zadaný uživatelem, který může obsahovat vlastní logiky pro zpracování sledování záznamy vygenerované modulem runtime pracovního postupu. Zápis vlastní sledování účastník, musí vývojář implementovat `Track` metodu <xref:System.Activities.Tracking.TrackingParticipant> třída. Tato metoda je volána, když je záznam sledování vygenerované modulem runtime pracovního postupu.  
  
 Sledování účastníků odvozena od <xref:System.Activities.Tracking.TrackingParticipant> třídy. Poskytované systémem <xref:System.Activities.Tracking.EtwTrackingParticipant> vydá událost událostí sledování pro Windows (ETW) pro každý záznam sledování, které se získaly. Pokud chcete vytvořit vlastní sledování účastník, třídu je vytvořen, který je odvozen od <xref:System.Activities.Tracking.TrackingParticipant>. Pro zajištění základních sledování, přepsání <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>. <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>je volána, když záznam sledování odesílají modulu runtime a lze ji zpracovat požadované způsobem. V následujícím příkladu je definována účastnické třídu vlastní sledování, který vysílá všechny záznamy sledování do okna konzoly. Můžete taky implementovat <xref:System.Activities.Tracking.TrackingParticipant> objekt, který zpracovává sledování zaznamenává asynchronně pomocí jeho `BeginTrack` a `EndTrack` metody  
  
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
  
 Pokud chcete používat konkrétní sledování účastník, zaregistrujte ji pomocí k instanci pracovního postupu, který chcete sledovat, jak je znázorněno v následujícím příkladu.  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 V následujícím příkladu, pracovní postup, se skládá z <xref:System.Activities.Statements.Sequence> aktivity, která obsahuje <xref:System.Activities.Statements.WriteLine> vytvoření aktivity. `ConsoleTrackingParticipant` Se přidá do rozšíření a volána pracovního postupu.  
  
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
 [Windows Server App Fabric monitorování](http://go.microsoft.com/fwlink/?LinkId=201273)  
 [Monitorování aplikací pomocí App Fabric](http://go.microsoft.com/fwlink/?LinkId=201275)
