---
title: Účastníci sledování
ms.date: 03/30/2017
ms.assetid: f13e360c-eeb7-4a49-98a0-8f6a52d64f68
ms.openlocfilehash: 45a92c3ab710fc9bc86fbf269a4672f1d34737cc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69963672"
---
# <a name="tracking-participants"></a>Účastníci sledování
Sledování účastníků je rozšiřitelné body, které umožňují vývojáři pracovního postupu <xref:System.Activities.Tracking.InteropTrackingRecord.TrackingRecord%2A> získat přístup k objektům a zpracovat je. [!INCLUDE[netfx_current_long](../../../includes/netfx-current-long-md.md)]zahrnuje standardního účastníka sledování, který zapisuje záznamy sledování jako události trasování událostí pro Windows (ETW). Je-li který nesplňuje vaše požadavky, můžete také napsat vlastní sledování účastník.  
  
## <a name="tracking-participants"></a>Účastníci sledování  
 Sledovací infrastruktura umožňuje použití filtru u odchozích záznamů sledování tak, aby se účastník mohl přihlásit k odběru podmnožiny záznamů. Mechanismus použití filtru je prostřednictvím sledovacího profilu.  
  
 Programovací model Windows Workflow Foundation (WF) v [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] nástroji poskytuje sledování účastníka, který zapisuje záznamy sledování do relace trasování událostí pro Windows. Účastník není konfigurována služba pracovního postupu přidáním specifické pro sledování chování v konfiguračním souboru. Povolení ETW umožňuje sledování účastník sledování záznamů, které mají být zobrazeny v události prohlížeč. Ukázka sady SDK pro sledování založené na ETW je dobrým způsobem, jak se seznámit se sledováním pomocí ETW na základě sledování.  
  
## <a name="etw-tracking-participant"></a>Účastník sledování ETW  
 [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)]zahrnuje účastník sledování trasování událostí pro Windows, který zapisuje záznamy sledování do relace trasování událostí pro Windows. To se provádí velice účinným způsobem s minimálním dopadem na výkon aplikace nebo na propustnost serveru. Výhodou použití standardního účastníka sledování ETW je, že záznamy sledování, které obdrží, se dají zobrazit s ostatními protokoly aplikací a systémem ve Windows Prohlížeč událostí.  
  
 Standardní účastník sledování ETW je nakonfigurovaný v souboru Web. config, jak je znázorněno v následujícím příkladu.  
  
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
> Pokud název není zadán, například pouze `<etwTracking/>` nebo `<etwTracking profileName=""/>`, [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] pak je použit výchozí profil sledování nainstalovaný v souboru Machine. config. `trackingProfile`  
  
 V souboru Machine. config se výchozí profil sledování přihlašuje k odběru záznamů a chyb instancí pracovního postupu.  
  
 V trasování událostí pro Windows se události zapisují do relace ETW prostřednictvím ID poskytovatele. ID zprostředkovatele, které účastník sledování ETW používá pro zápis záznamů sledování do ETW, je definováno v části Diagnostika v souboru Web. config (v části `<system.serviceModel><diagnostics>`). Ve výchozím nastavení používá účastník sledování ETW výchozí ID poskytovatele, pokud nebyl zadán, jak je znázorněno v následujícím příkladu.  
  
```xml  
<system.serviceModel>  
        <diagnostics etwProviderId="52A3165D-4AD9-405C-B1E8-7D9A257EAC9F" />  
```  
  
 Následující ilustrace znázorňuje tok sledování dat prostřednictvím účastníka sledování trasování událostí pro Windows. Jakmile se data sledování dorazí na relaci trasování událostí pro Windows, dá se k ní dostat několika způsoby. Jedním z nejužitečnějších způsobů, jak získat přístup k těmto událostem, je prostřednictvím Prohlížeč událostí, což je běžný nástroj pro Windows, který se používá k zobrazení protokolů a trasování z aplikací a služeb.  
  
 ![Tok sledování dat prostřednictvím zprostředkovatele sledování ETW.](./media/tracking-participants/tracking-data-event-tracing-windows-provider.gif)  
  
## <a name="tracking-participant-event-data"></a>Sledování dat událostí účastníka  
 Účastník sledování rozserializován data sledovaných událostí do relace ETW ve formátu jedné události na záznam sledování.  Událost se identifikuje pomocí ID v rozsahu 100 až 199. Definice záznamů událostí sledování, které generuje účastník sledování, najdete v tématu [sledovací události – referenční](tracking-events-reference.md) informace.  
  
 Velikost události ETW je omezená velikostí vyrovnávací paměti ETW nebo maximální datovou částí pro událost ETW, podle toho, jaká hodnota je menší. Pokud velikost události překročí jedno z těchto limitů ETW, událost se zkrátí a její obsah se odebere libovolným způsobem. Proměnné, argumenty, poznámky a vlastní data nejsou selektivně odebírány. V případě zkrácení jsou všechny tyto hodnoty zkráceny bez ohledu na hodnotu, která způsobila, že velikost události překročila limit ETW.  Odebraná data se nahradí `<item>..<item>`.  
  
 Komplexní typy v proměnných, argumentech a vlastních datových položkách jsou serializovány do záznamu události ETW pomocí [třídy NetDataContractSerializer](https://go.microsoft.com/fwlink/?LinkId=177537). Tato třída zahrnuje informace o typu CLR v serializované parní XML.  
  
 Zkrácení dat datové části z důvodu omezení ETW může mít za následek duplicitní záznamy sledování, které jsou odesílány do relace trasování událostí pro Windows. Tato situace může nastat, pokud více než jedna relace naslouchá událostem a relace mají pro události jiné limity zatížení.  
  
 Pro relaci s nižším limitem může být událost zkrácena. Účastník sledování ETW nemá žádné znalosti o počtu relací, které na události naslouchá. Pokud je událost pro relaci zkrácená, pak se pokusy účastníka trasování událostí pro Windows odešlou událost. V takovém případě by relace, která je nakonfigurovaná tak, aby přijímala větší velikost datové části, měla událost dvakrát (událost, která není zkrácená a zkrácená). Duplikaci lze zabránit konfigurací všech relací ETW se stejnými limity velikosti vyrovnávací paměti.  
  
## <a name="accessing-tracking-data-from-an-etw-participant-in-the-event-viewer"></a>Přístup k datům sledování z účastníka ETW v Prohlížeč událostí  
 Události, které jsou zapsány do relace ETW pomocí účastníka sledování ETW, jsou k dispozici prostřednictvím Prohlížeč událostí (při použití výchozího ID poskytovatele). To umožňuje rychle zobrazit záznamy sledování, které byly vygenerovány pracovním postupem.  
  
> [!NOTE]
> Sledování událostí záznamu emitovaných v relaci ETW používají ID událostí v rozsahu od 100 do 199.  
  
#### <a name="to-enable-viewing-the-tracking-records-in-event-viewer"></a>Povolení zobrazení záznamů sledování v Prohlížeč událostí  
  
1. Spusťte Prohlížeč událostí (EVENTVWR. PROGRAMU  
  
2. Vyberte **Prohlížeč událostí, protokoly aplikací a služeb, Microsoft, Windows, aplikační server – aplikace**.  
  
3. Klikněte pravým tlačítkem a ujistěte se, že je vybraná možnost **Zobrazit, zobrazit protokoly pro analýzu a ladění** . Pokud ne, vyberte ho, aby se vedle něho zobrazila značka zaškrtnutí. Tím se zobrazí protokoly o **analýze**, **výkonu**a **ladění** .  
  
4. Klikněte pravým tlačítkem na **analytický** protokol a pak vyberte **Povolit protokol**. Protokol bude existovat v souboru nalytic. ETL%SystemRoot%\System32\Winevt\Logs\Microsoft-Windows-Application Server-Applications% 4.  
  
## <a name="custom-tracking-participant"></a>Účastník vlastního sledování  
 Rozhraní API sledování účastníka umožňuje rozšíření sledovacího prostředí sledování s uživatelem poskytnutým účastníkem sledování, které může zahrnovat vlastní logiku pro zpracování záznamů sledování generovaných modulem runtime pracovního postupu. Chcete-li napsat vlastního účastníka sledování, je nutné, `Track` aby vývojář implementoval <xref:System.Activities.Tracking.TrackingParticipant> metodu pro třídu. Tato metoda je volána, když je záznam sledování generován modulem runtime pracovního postupu.  
  
 Sledování účastníků odvozených od <xref:System.Activities.Tracking.TrackingParticipant> třídy. Zadaný <xref:System.Activities.Tracking.EtwTrackingParticipant> systém vygeneruje událost trasování událostí pro Windows (ETW) pro každý přijatý záznam sledování. Chcete-li vytvořit vlastního účastníka sledování, je vytvořena třída, která je <xref:System.Activities.Tracking.TrackingParticipant>odvozena z. Chcete-li poskytnout základní funkce sledování <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>, přepište. <xref:System.Activities.Tracking.TrackingParticipant.Track%2A>je volána, když je záznam sledování odesílán modulem runtime a lze jej zpracovat požadovaným způsobem. V následujícím příkladu je definována třída vlastního účastníka sledování, která generuje všechny záznamy sledování do okna konzoly. Můžete také implementovat <xref:System.Activities.Tracking.TrackingParticipant> objekt, který zpracovává záznamy sledování asynchronně pomocí svých `BeginTrack` metod a `EndTrack` .  
  
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
  
 Chcete-li použít konkrétního účastníka sledování, zaregistrujte jej s instancí pracovního postupu, kterou chcete sledovat, jak je znázorněno v následujícím příkladu.  
  
```csharp  
myInstance.Extensions.Add(new ConsoleTrackingParticipant());  
```  
  
 V následujícím příkladu je vytvořen pracovní postup, který se skládá <xref:System.Activities.Statements.Sequence> z aktivity, která <xref:System.Activities.Statements.WriteLine> obsahuje aktivitu. `ConsoleTrackingParticipant` Přidá se do rozšíření a vyvolá se pracovní postup.  
  
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
  
## <a name="see-also"></a>Viz také:

- [Monitorování Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201273)
- [Monitorování aplikací pomocí prostředků infrastruktury aplikace](https://go.microsoft.com/fwlink/?LinkId=201275)
