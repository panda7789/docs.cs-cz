---
title: Výkon Windows Workflow Foundation 4
ms.date: 03/30/2017
ms.assetid: 67d2b3e8-3777-49f8-9084-abbb33b5a766
ms.openlocfilehash: 5fec41baacca0f35618dd5bc409b88ac792ad125
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182968"
---
# <a name="windows-workflow-foundation-4-performance"></a>Výkon Windows Workflow Foundation 4

 Rozhraní .NET Framework 4 obsahuje hlavní revizi nadace Windows Workflow Foundation (WF) s velkými investicemi do výkonu. Tato nová revize zavádí významné změny návrhu [!INCLUDE[wf1](../../../includes/wf1-md.md)] z předchozích verzí, které byly dodány jako součást rozhraní .NET Framework 3.0 a .NET Framework 3.5. Byl přepracován z jádra programovacího modelu, runtime a nástrojů, aby výrazně zlepšil výkon a použitelnost. Toto téma zobrazuje důležité charakteristiky výkonu těchto revizí a porovnává je s charakteristikami předchozí verze.

 Výkon jednotlivých komponent pracovního postupu se zvýšil o řád mezi wf3 a WF4.  To ponechává mezeru mezi ručně kódované služby Windows Communication Foundation (WCF) a WCF pracovního postupu služby být poměrně malé.  Latence pracovního postupu byla výrazně snížena v WF4.  Perzistence výkon zvýšil o faktor 2,5 - 3,0.  Monitorování stavu pomocí sledování pracovního postupu má výrazně menší režii.  Jedná se o přesvědčivé důvody pro migraci nebo přijmout WF4 ve vašich aplikacích.

## <a name="terminology"></a>Terminologie

 Verze [!INCLUDE[wf1](../../../includes/wf1-md.md)] zavedená v rozhraní .NET Framework 4 bude označována jako WF4 pro zbytek tohoto tématu. [!INCLUDE[wf1](../../../includes/wf1-md.md)]byl zaveden v rozhraní .NET Framework 3.0 a měl několik menších revizí prostřednictvím rozhraní .NET Framework 3.5 SP1. Verze služby Workflow Foundation rozhraní .NET Framework 3.5 bude ve zbývající části tohoto tématu označována jako WF3. WF3 je dodáván v rozhraní .NET Framework 4 vedle sebe s WF4. Další informace o migraci artefaktů WF3 na wf4 naleznete v [tématu: Průvodce migrací windows workflow foundation 4](migration-guidance.md).

 Windows Communication Foundation (WCF) je jednotný programovací model společnosti Microsoft pro vytváření aplikací orientovaných na služby. Byl poprvé zaveden jako součást rozhraní .NET 3.0 společně s WF3 a nyní je jednou z klíčových součástí rozhraní .NET Framework.

 Windows Server AppFabric je sada integrovaných technologií, které usnadňují vytváření, škálování a správu webových a složených aplikací spuštěných ve službě IIS. Poskytuje nástroje pro monitorování a správu služeb a pracovních postupů. Další informace naleznete v [tématu Windows Server AppFabric 1.0](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)).

## <a name="goals"></a>Cíle
 Cílem tohoto tématu je zobrazit charakteristiky výkonu WF4 s daty měřenými pro různé scénáře. Poskytuje také podrobné porovnání mezi WF4 a WF3, a proto ukazuje velké zlepšení, které byly provedeny v této nové revizi. Scénáře a data prezentovaná v tomto článku kvantifikují základní náklady různých aspektů WF4 a WF3. Tato data jsou užitečná při pochopení charakteristik výkonu WF4 a mohou být užitečná při plánování migrace z WF3 na WF4 nebo při použití WF4 při vývoji aplikací. Je však třeba dbát na závěry vyplývající z údajů uvedených v tomto článku. Výkon aplikace složeného pracovního postupu je vysoce závislá na tom, jak je implementován pracovní postup a jak jsou integrovány různé součásti. Jeden musí měřit každou aplikaci k určení charakteristiky výkonu této aplikace.

## <a name="overview-of-wf4-performance-enhancements"></a>Přehled vylepšení výkonu WF4
 WF4 byl pečlivě navržen a implementován s vysokým výkonem a škálovatelností, které jsou popsány v následujících částech.

### <a name="wf-runtime"></a>Čas spuštění služby WF
 Jádrem modulu [!INCLUDE[wf1](../../../includes/wf1-md.md)] runtime je asynchronní plánovač, který řídí provádění aktivit v pracovním postupu. Poskytuje performant, předvídatelné spuštění prostředí pro aktivity. Prostředí má dobře definované smlouvy pro provádění, pokračování, dokončení, zrušení, výjimky a předvídatelné modelování vláken.

 Ve srovnání s WF3 má zaběhu WF4 efektivnější plánovač. Využívá stejný fond vstupně-v., který se používá pro WCF, což je velmi efektivní při provádění dávkových pracovních položek. Fronta plánovače interních pracovních položek je optimalizována pro většinu běžných vzorců použití. Modul runtime WF4 také spravuje stavy spuštění velmi lehkým způsobem s minimální synchronizací a logikou zpracování událostí, zatímco WF3 závisí na registraci události s těžkou hmotností a vyvolání k provedení komplexní synchronizace přechodů stavu.

### <a name="data-storage-and-flow"></a>Ukládání a tok dat
 V WF3 data spojená s aktivitou je modelována <xref:System.Windows.DependencyProperty>pomocí vlastností závislostí implementovaných typem . Vzor vlastnosti závislostbyla zavedena v Systému Windows Presentation Foundation (WPF). Obecně platí, že tento vzor je velmi flexibilní pro podporu snadné datové vazby a další funkce ui. Vzorek však vyžaduje vlastnosti, které mají být definovány jako statická pole v definici pracovního postupu. Vždy, [!INCLUDE[wf1](../../../includes/wf1-md.md)] když runtime nastaví nebo získá hodnoty vlastností, zahrnuje silně váženou logiku vyhledávání.

 WF4 používá logiku oboru jasných dat k výraznému zlepšení způsobu zpracování dat v pracovním postupu. Odděluje data uložená v aktivitě od dat, která proudí přes hranice aktivity pomocí dvou různých konceptů: proměnné a argumenty. Pomocí jasné hierarchické oboru pro proměnné a "In/Out/InOut" argumenty, složitost využití dat pro aktivity je výrazně snížena a životnost dat je také automaticky vymezena. Aktivity mají dobře definovaný podpis popsaný jeho argumenty. Jednoduše kontrolou aktivity můžete určit, jaká data očekává příjem a jaká data budou vytvořena v důsledku jejího spuštění.

 V WF3 byly aktivity inicializovány při vytvoření pracovního postupu. V WF 4 aktivity jsou inicializovány pouze v případě, že příslušné aktivity jsou spuštěny. To umožňuje jednodušší životní cyklus aktivity bez provedení operací Initialize/Uninitialize při vytvoření nové instance pracovního postupu, a tím bylo dosaženo vyšší efektivity.

### <a name="control-flow"></a>Tok řízení
 Stejně jako v [!INCLUDE[wf1](../../../includes/wf1-md.md)] jakémkoli programovacím jazyce poskytuje podporu pro toky řízení pro definice pracovních postupů zavedením sady aktivit toku řízení pro sekvenování, opakování, větvení a další vzory. V WF3, když je třeba znovu provést stejnou <xref:System.Workflow.ComponentModel.ActivityExecutionContext> aktivitu, je vytvořena nová a aktivita je klonována pomocí <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>logiky serializace a deserializace založené na . Obvykle výkon pro iterativní řízení toků je mnohem pomalejší než provádění posloupnost aktivit.

 WF4 zpracovává to zcela odlišně. Vezme šablonu aktivity, vytvoří nový objekt ActivityInstance a přidá ji do fronty plánovače. Celý tento proces zahrnuje pouze explicitní vytváření objektů a je velmi lehký.

### <a name="asynchronous-programming"></a>Asynchronní programování
 Aplikace mají obvykle lepší výkon a škálovatelnost s asynchronním programováním pro dlouho běžící blokovací operace, jako jsou vstupně-va nebo distribuované výpočetní operace. WF4 poskytuje asynchronní podporu prostřednictvím základních typů <xref:System.Activities.AsyncCodeActivity>aktivit , <xref:System.Activities.AsyncCodeActivity%601>. Modul runtime nativně rozumí asynchronní aktivity a proto můžete automaticky umístit instanci v zóně bez trvalého výskytu, zatímco asynchronní práce je vynikající. Vlastní aktivity mohou být odvozeny z těchto typů k provádění asynchronní práce bez držení vlákna plánovače pracovního postupu a blokování všech aktivit, které mohou být možné spustit paralelně.

### <a name="messaging"></a>Zasílání zpráv
 Zpočátku WF3 měl velmi omezenou podporu zasílání zpráv prostřednictvím externích událostí nebo vyvolání webových služeb. V rozhraní .NET 3.5 mohou být pracovní postupy implementovány jako <xref:System.Workflow.Activities.SendActivity> <xref:System.Workflow.Activities.ReceiveActivity>klienti WCF nebo vystaveny jako služby WCF prostřednictvím a . V WF4, koncept programování zasílání zpráv na základě pracovního postupu byla dále posílena prostřednictvím těsné integrace wcf zasílání zpráv logiky do WF.

 Kanál pro zpracování sjednocené zprávy poskytované v WCF v .NET 4 pomáhá WF4 služby mají výrazně lepší výkon a škálovatelnost než WF3. WF4 také poskytuje bohatší podporu programování zasílání zpráv, která může modelovat složité vzory výměny zpráv (MEPs). Vývojáři mohou použít zadané smlouvy o poskytování služeb k dosažení snadného programování nebo netypových servisních smluv, aby dosáhli lepšího výkonu bez placení nákladů na serializaci. Podpora ukládání do mezipaměti kanálu <xref:System.ServiceModel.Activities.SendMessageChannelCache> na straně klienta prostřednictvím třídy v WF4 pomáhá vývojářům vytvářet rychlé aplikace s minimálním úsilím. Další informace naleznete [v tématu Změna úrovní sdílení mezipaměti pro odesílání aktivit](../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).

### <a name="declarative-programming"></a>Deklarativní programování
 WF4 poskytuje čistý a jednoduchý deklarativní programovací rámec pro modelování obchodních procesů a služeb. Programovací model podporuje plně deklarativní složení aktivit, bez kódu vedle, což výrazně zjednodušuje vytváření pracovních postupů. V rozhraní .NET Framework 4 byla deklarativní programovací architektura založená na XAML sjednocena do jednotného sestavení System.Xaml.dll pro podporu wpf i wf.

 V WF4, XAML poskytuje skutečně deklarativní prostředí a umožňuje pro celou definici pracovního postupu, které mají být definovány v XML značky, odkazování na aktivity a typy vytvořené pomocí .NET. To bylo obtížné provést v WF3 s formátem XOML bez zahrnující vlastní logiku kódu na pozadí. Nový zásobník XAML v rozhraní .NET 4 má mnohem lepší výkon při serializaci a dekonalizaci artefaktů pracovního postupu a činí deklarativní programování atraktivnější a solidnější.

### <a name="workflow-designer"></a>Návrhář postupu provádění
 Plně deklarativní programovací podpora pro WF4 explicitně ukládá vyšší požadavky na výkon času návrhu pro velké pracovní postupy. Návrhář pracovního postupu v wf4 má mnohem lepší škálovatelnost pro velké pracovní postupy než pro WF3. S podporou virtualizace ui návrhář může snadno načíst velký pracovní postup 1000 aktivit během několika sekund, zatímco je téměř nemožné načíst pracovní postup několika set aktivit s návrhářem WF3.

## <a name="component-level-performance-comparisons"></a>Porovnání výkonu na úrovni komponent
 Tato část obsahuje data o přímém porovnání mezi jednotlivými aktivitami v pracovních postupech WF3 a WF4.  Klíčové oblasti, jako je trvalost, mají hlubší dopad na výkon než jednotlivé součásti aktivity.  Zlepšení výkonu v jednotlivých komponent v WF4 jsou důležité i když proto, že komponenty jsou nyní dostatečně rychlé, aby bylo možné porovnat s ručně kódované orchestrace logiky.  Příklad, který je popsán v další části: "Scénář složení služby."

### <a name="environment-setup"></a>Nastavení prostředí
 ![Nastavení prostředí pro měření výkonu pracovního postupu](./media/performance/performance-test-environment.gif)

 Výše uvedený obrázek znázorňuje konfiguraci stroje použitou pro měření výkonu na úrovni komponent. Jeden server a pět klientů připojených přes jedno síťové rozhraní 1 Gb/s Ethernet. Pro snadné měření je server nakonfigurován tak, aby používal jedno jádro dvouprocového/čtyřjádrového serveru se systémem Windows Server 2008 x86. Využití procesoru systému je udržováno na téměř 100%.

### <a name="test-details"></a>Podrobnosti testu
 WF3 <xref:System.Workflow.Activities.CodeActivity> je pravděpodobně nejjednodušší aktivita, která může být použita v pracovním postupu WF3.  Aktivita volá metodu v kódu za, který programátor pracovního postupu můžete umístit vlastní kód do.  V WF4 neexistuje žádný přímý analog <xref:System.Workflow.Activities.CodeActivity> wf3, který poskytuje stejné funkce.  Všimněte si, <xref:System.Activities.CodeActivity> že je základní třídy v WF4, která nesouvisí s WF3 <xref:System.Workflow.Activities.CodeActivity>.  Autoři pracovních postupů se doporučuje vytvořit vlastní aktivity a vytvářet pouze XAML pracovní chod.  V níže uvedených testech se místo prázdného pracovního postupu WF4 používá aktivita volaná `Comment` místo prázdného. <xref:System.Workflow.Activities.CodeActivity>  Kód v `Comment` aktivitě je následující:

```csharp
[ContentProperty("Body")]
    public sealed class Comment : CodeActivity
    {
        public Comment()
            : base()
        {
        }

        [DefaultValue(null)]
        public Activity Body
        {
            get;
            set;
        }

        protected override void Execute(CodeActivityContext context)
        {
        }
    }
```

### <a name="empty-workflow"></a>Prázdný pracovní postup
 Tento test používá pracovní postup sekvence bez podřízených aktivit.

### <a name="single-activity"></a>Jedna aktivita
 Pracovní postup je sekvenční pracovní postup obsahující jednu podřízenou aktivitu.  Aktivita je <xref:System.Workflow.Activities.CodeActivity> bez kódu v případě WF3 a aktivity `Comment` v případě WF4.

### <a name="while-with-1000-iterations"></a>Zatímco s 1000 iterací
 Pracovní postup sekvence <xref:System.Activities.Statements.While> obsahuje jednu aktivitu s jednou podřízenou aktivitou ve smyčce, která neprovádí žádnou práci.

### <a name="replicator-compared-to-parallelforeach"></a>Replikátor ve srovnání s ParallelForEach
 <xref:System.Workflow.Activities.ReplicatorActivity>v WF3 má sekvenční a paralelní režimy provádění.  V sekvenčním režimu je <xref:System.Workflow.Activities.WhileActivity>výkon aktivity podobný .  Je <xref:System.Workflow.Activities.ReplicatorActivity> nejužitečnější pro paralelní spuštění.  WF4 analogpro to <xref:System.Activities.Statements.ParallelForEach%601> je aktivita.

 Následující diagram znázorňuje pracovní postupy použité pro tento test. Pracovní postup WF3 je vlevo a pracovní postup WF4 je vpravo.

 ![WF3 ReplicatorActivity a WF4 ParallelForEach](./media/performance/replicator-parallel-wf3-wf4.gif)

### <a name="sequential-workflow-with-five-activities"></a>Sekvenční pracovní postup s pěti aktivitami
 Tento test je určen k zobrazení účinku s několik aktivit spustit v pořadí.  V pořadí je pět aktivit.

### <a name="transaction-scope"></a>Rozsah transakcí
 Test oboru transakce se liší od ostatních testů mírně v tom, že nová instance pracovního postupu není vytvořena pro každou iteraci.  Místo toho je pracovní postup strukturován <xref:System.Activities.Statements.TransactionScope> s smyčkou while obsahující aktivitu obsahující jednu aktivitu, která nepracuje.  Každé spuštění dávky 50 iterací prostřednictvím while smyčky se počítá jako jedna operace.

### <a name="compensation"></a>Kompenzace
 Pracovní postup WF3 má jednu kompenzační `WorkScope`aktivitu s názvem .  Aktivita jednoduše implementuje <xref:System.Workflow.ComponentModel.ICompensatableActivity> rozhraní:

```csharp
class WorkScope :
        CompositeActivity, ICompensatableActivity
    {
        public WorkScope() : base() { }

        public WorkScope(string name)
        {
            this.Name = name;
        }

        public ActivityExecutionStatus Compensate(
            ActivityExecutionContext executionContext)
        {
            return ActivityExecutionStatus.Closed;
        }
    }
```

 Obslužná `WorkScope` rutina poruchy cílí na aktivitu. Pracovní postup WF4 je stejně zjednodušující.  A <xref:System.Activities.Statements.CompensableActivity> má tělo a odškodnění manipulátor.  Explicitní kompenzace je další v pořadí.  Aktivita těla a aktivita obslužné rutiny kompenzace jsou prázdné implementace:

```csharp
public sealed class CompensableActivityEmptyCompensation : CodeActivity
    {
        public CompensableActivityEmptyCompensation()
            : base() { }

        public Activity Body { get; set; }

        protected override void Execute(CodeActivityContext context) { }
    }
    public sealed class CompensableActivityEmptyBody : CodeActivity
    {
        public CompensableActivityEmptyBody()
            : base() { }

        public Activity Body { get; set; }

        protected override void Execute(CodeActivityContext context) { }
    }
```

Následující diagram znázorňuje pracovní postup základní kompenzace. Pracovní postup WF3 je vlevo a pracovní postup WF4 je vpravo.

![Pracovní postupy základní kompenzace WF3 a WF4](./media/performance/basic-compensation-workflows-wf3-wf4.gif)

### <a name="performance-test-results"></a>Výsledky testů výkonu

 ![Tabulka s údaji o výsledcích testu výkonu](./media/performance/performance-test-data.gif)

 ![Sloupcový graf porovnávající data testu výkonu wf3 a WF4](./media/performance/performance-test-chart.gif)

 Všechny testy se měří v pracovních postupech za sekundu s výjimkou testu oboru transakce.  Jak je vidět výše, výkon [!INCLUDE[wf1](../../../includes/wf1-md.md)] za běhu se zlepšil a plošně, zejména v oblastech, které vyžadují více spuštění stejné aktivity, jako je smyčka while.

## <a name="service-composition-scenario"></a>Scénář složení služby
 Jak je znázorněno v předchozí části "Porovnání výkonu na úrovni komponent", došlo k významnému snížení režie mezi WF3 a WF4.  Služby pracovního postupu WCF nyní mohou téměř odpovídat výkonu ručně kódovaných [!INCLUDE[wf1](../../../includes/wf1-md.md)] služeb WCF, ale stále mají všechny výhody běhu.  Tento testovací scénář porovnává službu WCF se službou pracovního postupu WCF v wf4.

### <a name="online-store-service"></a>Služba online obchodu
 Jednou ze silných stránek nadace Windows Workflow Foundation je schopnost vytvářet procesy pomocí několika služeb.  V tomto příkladu je služba online obchodu, která orchestruje dvě volání služby k nákupu objednávky.  Prvním krokem je ověření objednávky pomocí služby ověřování objednávek.  Druhým krokem je vyplnění objednávky pomocí služby Sklad.

 Dvě back-endové služby, Objednavat validace service a skladové služby, zůstávají stejné pro oba testy.  Část, která se změní, je služba online obchodu, která provádí orchestraci.  V jednom případě je služba ručně kódována jako služba WCF.  Pro druhý případ je služba zapsána jako služba pracovního postupu WCF v WF4. [!INCLUDE[wf1](../../../includes/wf1-md.md)]-specifické funkce, jako je sledování a perzistence jsou vypnuty pro tento test.

### <a name="environment"></a>Prostředí
![Nastavení prostředí pro měření výkonu](./media/performance/performance-test-environment.gif)

 Požadavky klientů jsou prováděny ve službě Online Store prostřednictvím protokolu HTTP z více počítačů.  Jeden počítač hostuje všechny tři služby.  Transportní vrstva mezi službou online obchodu a back-endovými službami je TCP nebo HTTP.  Měření operací za sekundu je založeno `PurchaseOrder` na počtu dokončených volání do služby online obchodu.  Sdružování kanálů je nová funkce dostupná v WF4.  V WCF část tohoto sdružování testovacíkanál není k dispozici po vybalení, takže ručně kódované implementace jednoduché sdružování technika byla použita ve službě online obchodu.

### <a name="performance"></a>Výkon
![Sloupcový graf znázorňující výkon služby online služby Store](./media/performance/online-store-performance-graph.gif)

 Připojení ke službám TCP back-endbez [!INCLUDE[wf1](../../../includes/wf1-md.md)] sdružování kanálů, služba má 17,2% dopad na propustnost.  S kanálem sdružování, trest je asi 23,8%.  Pro HTTP dopad je mnohem menší: 4,3% bez sdružování a 8,1% s sdružování.  Je také důležité si uvědomit, že sdružování kanálů poskytuje velmi malou výhodu při použití protokolu HTTP.

 Zatímco je režie z wf4 runtime ve srovnání s ručně kódované WCF služby v tomto testu, může být považován za nejhorší scénář.  Dvě back-endové služby v tomto testu dělat velmi málo práce.  V reálném scénář end-to-end by tyto služby provádět dražší operace, jako je volání databáze, takže dopad na výkon transportní vrstvy méně důležité.  To to plus výhody funkcí dostupných v WF4 je Workflow Foundation životaschopnou volbou pro vytváření služeb orchestrace.

## <a name="key-performance-considerations"></a>Klíčové aspekty výkonu
 Oblasti funkcí v této části, s výjimkou interop, se dramaticky změnily mezi WF3 a WF4.  To má vliv na návrh aplikací pracovního postupu, stejně jako výkon.

#### <a name="workflow-activation-latency"></a>Latence aktivace pracovního postupu
 V aplikaci služby pracovního postupu WCF je důležitá latence pro spuštění nového pracovního postupu nebo načtení existujícího pracovního postupu, protože může být blokování.  Tento testovací případ měří hostitele WF3 XOML proti hostiteli WF4 XAMLX v typickém scénáři.

##### <a name="environment-setup"></a>Nastavení prostředí
 ![Nastavení prostředí pro testy latence a propustnosti](./media/performance/latency-throughput-environment-setup.gif)

##### <a name="test-setup"></a>Testovací nastavení
 Ve scénáři klientský počítač kontaktuje službu pracovního postupu WCF pomocí kontextové korelace.  Kontextová korelace vyžaduje zvláštní kontextovou vazbu a používá záhlaví kontextu nebo soubor cookie k propojení zpráv se správnou instancí pracovního postupu.  Má výhodu výkonu v tom, že Id korelace je umístěn v záhlaví zprávy, takže tělo zprávy není nutné analyzovat.

 Služba vytvoří nový pracovní postup s požadavkem a odešle okamžitou odpověď tak, aby měření latence nezahrnovalo čas strávený spuštěním pracovního postupu.  Pracovní postup WF3 je XOML s kódem na pozadí a pracovní postup WF4 je zcela XAML.  Pracovní postup WF4 vypadá takto:

 ![Pracovní postup obor korelace WF4](./media/performance/wf4-correlationscope-workflow.gif)

 Aktivita <xref:System.ServiceModel.Activities.Receive> vytvoří instanci pracovního postupu.  Hodnota předaná v přijaté zprávě se zobrazí ve zprávě s odpovědí.  Posloupnost následující odpověď obsahuje zbytek pracovního postupu.  Ve výše uvedeném případě se zobrazí pouze jedna aktivita komentáře.  Počet aktivit komentářů se změní, aby simuloval složitost pracovního postupu.  Aktivita komentáře je ekvivalentní <xref:System.Workflow.Activities.CodeActivity> WF3, který neprovádí žádnou práci. Další informace o aktivitě komentáře naleznete v části Porovnání výkonu na úrovni komponent dříve v tomto článku.

##### <a name="test-results"></a>Výsledky testů

 Studená a teplá latence pro služby pracovního postupu WCF:

 ![Sloupcový graf zobrazující studenou a teplou latenci pro služby pracovního postupu WCF pomocí wf3 a WF4](./media/performance/latency-results-graph.gif)

 V předchozím grafu za studena odkazuje na případ, <xref:System.ServiceModel.WorkflowServiceHost> kdy neexistuje pro daný pracovní postup.  Jinými slovy, studená latence je, když je pracovní postup používán poprvé a XOML nebo XAML je třeba zkompilovat.  Teplá latence je čas k vytvoření nové instance pracovního postupu, když typ pracovního postupu již byl zkompilován.  Složitost pracovního postupu je velmi malý rozdíl v případě WF4, ale má lineární průběh v případě WF3.

#### <a name="correlation-throughput"></a>Propustnost korelace
 WF4 zavádí novou funkci korelace založené na obsahu.  WF3 za předpokladu, pouze kontextové korelace.  Kontextová korelace může být provedena pouze přes konkrétní vazby kanálu WCF.  Id pracovního postupu je vložen do záhlaví zprávy při použití těchto vazeb.  Za běhu WF3 lze identifikovat pouze pracovní postup podle jeho ID.  Díky korelaci založené na obsahu může autor pracovního postupu vytvořit korelační klíč z příslušné části dat, jako je číslo účtu nebo ID zákazníka.

 Kontextová korelace má výhodu výkonu v tom, že korelační klíč je umístěn v záhlaví zprávy.  Klíč lze číst ze zprávy bez de-serializace/kopírování zpráv.  V korelaci založené na obsahu je korelační klíč uložen v textu zprávy.  Výraz XPath se používá k vyhledání klíče.  Náklady na toto další zpracování závisí na velikosti zprávy, hloubka klíče v těle a počet klíčů.  Tento test porovnává korelace založené na kontextu a obsahu a také ukazuje snížení výkonu při použití více klíčů.

#### <a name="environment-setup"></a>Nastavení prostředí
![Nastavení prostředí pro test výkonu pracovního postupu](./media/performance/performance-test-environment.gif)

#### <a name="test-setup"></a>Testovací nastavení
![Test pracovního postupu propustnost propustnost korelace](./media/performance/correlation-throughput-workflow.gif "Nastavení testu pracovního postupu propustnost propustnost")

 Předchozí pracovní postup je stejný jako v části [Trvalosti.](#persistence) Pro korelace testy bez trvalosti neexistuje žádný zprostředkovatel trvalosti nainstalován v době runtime. Korelace se vyskytuje na dvou místech: CreateOrder a CompleteOrder.

#### <a name="test-results"></a>Výsledky testů
![Propustnost korelace](./media/performance/correlation-throughput-graph.gif "Graf propustnost korelace")

 Tento graf ukazuje snížení výkonu jako počet klíčů používaných v korelaci založené na obsahu zvyšuje.  Podobnost v křivkách mezi protokoly TCP a HTTP označuje režii spojenou s těmito protokoly.

#### <a name="correlation-with-persistence"></a>Korelace s perzistencí
 U trvalého pracovního postupu se tlak procesoru z korelace založené na obsahu přesouvá z modulu runtime pracovního postupu do databáze SQL.  Uložené procedury ve zprostředkovateli trvalosti SQL provést práci odpovídající klíče najít příslušný pracovní postup.

 ![Spojnicový graf znázorňující výsledky korelace a perzistence](./media/performance/correlation-persistence-graph.gif)

 Kontextová korelace je stále rychlejší než korelace založená na obsahu.  Rozdíl je však méně výrazný jako trvalost má větší vliv na výkon než korelace.

### <a name="complex-workflow-throughput"></a>Propustnost komplexního pracovního postupu
 Složitost pracovního postupu se neměří pouze počtem aktivit.  Složené aktivity mohou obsahovat mnoho podřízených a tyto podřízené osoby mohou být také složené aktivity.  S tím, jak se zvyšuje počet úrovní vnoření, se zvyšuje i počet aktivit, které mohou být aktuálně ve spuštěném stavu, a počet proměnných, které mohou být ve stavu.  Tento test porovnává propustnost mezi WF3 a WF4 při provádění složitých pracovních postupů.

### <a name="test-setup"></a>Testovací nastavení
 Tyto testy byly provedeny na počítači Intel Xeon X5355 @ 2.66GHz 4-way s 4GB RAM se systémem Windows Server 2008 x64.  Testovací kód běží v jednom procesu s jedním vláknem na jádro k dosažení 100 % využití procesoru.

 Pracovní postupy generované pro tento test mají dvě hlavní proměnné: hloubku a počet aktivit v každé sekvenci.  Každá úroveň hloubky zahrnuje paralelní aktivitu, zatímco smyčka, rozhodnutí, přiřazení a sekvence.  V návrháři WF4 na obrázku níže je zobrazen vývojový diagram nejvyšší úrovně.  Každá aktivita vývojového diagramu se podobá hlavnímu vývojovému diagramu.  Může být užitečné myslet na fraktál při zobrazení tohoto pracovního postupu, kde je hloubka omezena na parametry testu.

 Počet aktivit v daném testu je určen hloubkou a počtem aktivit na posloupnost.  Následující rovnice vypočítá počet aktivit v testu WF4:

 ![Rovnice pro výpočet počtu aktivit](./media/performance/number-activities-equation.gif)

 Počet aktivit testu WF3 lze vypočítat s mírně odlišnou rovnicí z důvodu další sekvence:

 ![Rovnice pro výpočet počtu aktivit WF3](./media/performance/wf3-number-activities-equation.gif)

 Kde d je hloubka a a je počet aktivit na posloupnost.  Logika těchto rovnic spočívá v tom, že první konstanta vynásobená a je počet sekvencí a druhá konstanta je statický počet aktivit na aktuální úrovni.  V každém vývojovém diagramu jsou tři podřízené aktivity vývojového diagramu.  V dolní úrovni hloubky jsou tyto vývojové diagramy prázdné, ale na ostatních úrovních jsou kopiemi hlavního vývojového diagramu.  Počet aktivit v definici pracovního postupu jednotlivých variant testu je uveden v následující tabulce:

 ![Tabulka s počtem aktivit použitých v jednotlivých testech](./media/performance/workflow-variation-compare-table.gif)

 Počet aktivit v definici pracovního postupu se s každou úrovní hloubky prudce zvyšuje.  Ale pouze jedna cesta na rozhodovací bod je spuštěn a v dané instanci pracovního postupu, takže jsou provedeny pouze malé podmnožiny skutečné aktivity.

 ![Vývojový diagram pracovního postupu komplexní propustnost](./media/performance/complex-workflow-throughput-workflow.gif)

 Pro wf3 byl vytvořen ekvivalentní pracovní postup. Návrhář WF3 zobrazuje celý pracovní postup v oblasti návrhu namísto vnoření, proto je příliš velký pro zobrazení v tomto tématu. Fragment pracovního postupu je uveden níže.

 ![Fragment vývojového diagramu pracovního postupu WF3](./media/performance/wf3-workflow-snippet.gif)

 Chcete-li uplatnit vnoření v extrémním případě, jiný pracovní postup, který je součástí tohoto testu používá 100 vnořené sekvence.  V nejvnitřnější sekvenci je jeden `Comment` nebo <xref:System.Workflow.Activities.CodeActivity>.

 ![Vývojový diagram vnořené sekvence](./media/performance/nested-sequence-workflow.gif)

 Sledování a trvalost se nepoužívají jako součást tohoto testu.

### <a name="test-results"></a>Výsledky testů
 ![Sloupcový graf zobrazující výsledky výkonu propustností](./media/performance/throughput-performance-results.gif)

 I při složitých pracovních postupech s velkým množstvím hloubky a vysokým počtem aktivit jsou výsledky výkonu konzistentní s jinými čísly propustnosti zobrazenými dříve v tomto článku.  Propustnost WF4 je řádově rychlejší a musí být porovnána v logaritmickém měřítku.

### <a name="memory"></a>Memory (Paměť)
 Režie paměti windows workflow foundation se měří ve dvou klíčových oblastech: složitost pracovního postupu a počet definic pracovních postupů.  Měření paměti byla provedena na 64bitové pracovní stanici se systémem Windows 7.  Existuje mnoho způsobů, jak získat měření velikosti pracovní sady, jako je sledování čítačů výkonu, dotazování Environment.WorkingSet nebo pomocí nástroje, jako je VMMap k dispozici od [VMMap](/sysinternals/downloads/vmmap). K získání a ověření výsledků každého testu byla použita kombinace metod.

### <a name="workflow-complexity-test"></a>Test složitosti pracovního postupu
 Test složitosti pracovního postupu měří rozdíl pracovní sady na základě složitosti pracovního postupu.  Kromě složitých pracovních postupů použitých v předchozí části jsou přidány nové varianty, které pokrývají dva základní případy: jeden pracovní postup aktivity a posloupnost s aktivitami 1000.  Pro tyto testy pracovní postupy jsou inicializovány a provedeny k dokončení v jedné sériové smyčky po dobu jedné minuty.  Každá varianta testu je spuštěna třikrát a zaznamenaná data jsou průměrem těchto tří spuštění.

 Dva nové základní testy mají pracovní postupy, které vypadají jako ty, které jsou uvedeny níže:

 ![Složitý pracovní postup pro WF3 i WF4](./media/performance/complex-workflow-wf3-wf4.gif)

 Ve výše uvedeném pracovním <xref:System.Workflow.Activities.CodeActivity> postupu WF3 se používají prázdné aktivity.  Výše uvedený pracovní `Comment` postup WF4 používá aktivity.  Aktivita `Comment` byla popsána v části Porovnání výkonu na úrovni komponent dříve v tomto článku.

 ![Sloupcový graf zobrazující komplexní využití paměti pracovního postupu pro pracovní postupy WF3 a WF4](./media/performance/complex-memory-usage-wf3-wf4.gif)

 Jedním z jasných trendů, které si můžete všimnout v tomto grafu, je, že vnoření má relativně minimální dopad na využití paměti v WF3 i WF4.  Nejvýznamnější dopad paměti pochází z počtu aktivit v daném pracovním postupu.  Vzhledem k datům z sekvence 1000, komplexní hloubky 5 sekvence 5 a komplexní hloubky 7 sekvenčních 1 variant, je zřejmé, že jak počet aktivit vstupuje do tisíců, zvýšení využití paměti se stává výraznější.  V extrémním případě (hloubka 7 sekvence 1), kde jsou ~ 29 kB aktivity, WF4 používá téměř 79 % méně paměti než WF3.

### <a name="multiple-workflow-definitions-test"></a>Test definic více pracovních postupů
 Měření paměti na definici pracovního postupu je rozděleno do dvou různých testů z důvodu dostupných možností pro hostování pracovních postupů v wf3 a WF4.  Testy jsou spouštěny jiným způsobem než test složitosti pracovního postupu v tom, že daný pracovní postup je instance a provedeny pouze jednou na definici.  Důvodem je, že definice pracovního postupu a jeho hostitele zůstávají v paměti po dobu životnosti AppDomain.  Paměť používaná spuštěním dané instance pracovního postupu by měla být vyčištěna během uvolňování paměti.  Pokyny pro migraci pro WF4 obsahuje podrobnější informace o možnostech hostování. Další informace naleznete v [tématu WF Migration Cookbook: Workflow Hosting](migration-guidance.md).

 Vytvoření mnoha definic pracovního postupu pro test definice pracovního postupu lze provést několika způsoby.  Například lze použít generování kódu k vytvoření sady 1000 pracovních postupů, které jsou identické s výjimkou názvu a uložit každý z těchto pracovních postupů do samostatných souborů.  Tento přístup byl přijat pro test hostovaný konzolou.  V WF3 <xref:System.Workflow.Runtime.WorkflowRuntime> byla třída použita ke spuštění definic pracovního postupu.  WF4 můžete <xref:System.Activities.WorkflowApplication> použít k vytvoření jedné instance <xref:System.Activities.WorkflowInvoker> pracovního postupu nebo přímo použít ke spuštění aktivity, jako by se jednalo o volání metody.  <xref:System.Activities.WorkflowApplication>je hostitelem jedné instance pracovního postupu a <xref:System.Workflow.Runtime.WorkflowRuntime> má bližší paritu funkce tak, aby byl použit v tomto testu.

 Při hostování pracovních postupů ve službách <xref:System.Web.Hosting.VirtualPathProvider> IIS <xref:System.ServiceModel.WorkflowServiceHost> je možné použít a vytvořit nový namísto generování všech souborů XAMLX nebo XOML.  Zpracovává <xref:System.Web.Hosting.VirtualPathProvider> příchozí požadavek a odpoví "virtuální soubor", který lze načíst z databáze nebo v tomto případě generované za běhu.  Proto není nutné vytvářet 1000 fyzických souborů.

 Definice pracovního postupu použité v testu konzoly byly jednoduché sekvenční pracovní postupy s jedinou aktivitou.  Jediná aktivita byla <xref:System.Workflow.Activities.CodeActivity> prázdná pro případ `Comment` WF3 a aktivita pro případ WF4.  Případ hostovaný službou IIS používal pracovní postupy, které začínají při přijetí zprávy a končí odesláním odpovědi:

Následující obrázek znázorňuje pracovní postup WF3 s receiveActivity a pracovní postup WF4 se vzorem požadavku a odpovědi:

 ![Služby pracovního postupu v wf3 a WF4](./media/performance/workflow-receive-activity.gif)

 V následující tabulce je uvedena delta v pracovní sadě mezi jednou definicí pracovního postupu a definicemi 1001:

|Možnosti hostování|Delta pracovní sady WF3|Delta pracovní sady WF4|
|---------------------|---------------------------|---------------------------|
|Pracovní postupy hostované konzolou aplikace|18 MB|9 MB|
|Služby pracovního postupu hostované službou IIS|446 MB|364 MB|

 Hostování definic pracovních postupů ve službě IIS <xref:System.ServiceModel.WorkflowServiceHost>spotřebovává mnohem více paměti z důvodu , podrobné artefakty služby WCF a logiku zpracování zpráv přidružené k hostiteli.

 Pro hostování konzoly v WF3 byly pracovní postupy implementovány v kódu namísto XOML.  Ve službě WF4 je výchozí použití XAML.  XAML je uložen jako vložený prostředek v sestavení a kompilován za běhu, aby byla zajištěna implementace pracovního postupu.  K tomuto procesu jsou přidruženy určité režie.  Aby bylo možné provést spravedlivé srovnání mezi WF3 a WF4, kódované pracovní postupy byly použity namísto XAML.  Příklad jednoho z pracovních postupů WF4 je uveden níže:

```csharp
public class Workflow1 : Activity
{
    protected override Func<Activity> Implementation
    {
        get
        {
            return new Func<Activity>(() =>
            {
                return new Sequence
                {
                    Activities = {
                        new Comment()
                    }
                };
            });
        }
        set
        {
            base.Implementation = value;
        }
    }
}
```

 Existuje mnoho dalších faktorů, které mohou ovlivnit spotřebu paměti. Stejná rada pro všechny spravované programy stále platí.  V prostředích hostovaných službou <xref:System.ServiceModel.WorkflowServiceHost> IIS zůstane objekt vytvořený pro definici pracovního postupu v paměti, dokud nebude fond aplikací recyklován.  To je třeba mít na paměti při psaní rozšíření.  Také je nejlepší vyhnout se "globálním" proměnným (proměnné s vymezeným rozsahem celého pracovního postupu) a omezit rozsah proměnných, kdykoli je to možné.

## <a name="workflow-runtime-services"></a>Služby runtime pracovního postupu

### <a name="persistence"></a>Uchování
 WF3 a WF4 obě doručují s poskytovatelem trvalosti SQL.  Poskytovatel trvalosti SQL WF3 je jednoduchá implementace, která serializuje instanci pracovního postupu a ukládá ji do objektu blob.  Z tohoto důvodu závisí výkon tohoto zprostředkovatele do značné míry na velikosti instance pracovního postupu.  V WF3 velikost instance může zvýšit z mnoha důvodů, jak je popsáno dříve v tomto dokumentu.  Mnoho zákazníků se rozhodne nepoužívat výchozího zprostředkovatele trvalosti SQL, protože ukládání serializované instance v databázi neposkytuje žádný přehled o stavu pracovního postupu.  Chcete-li najít konkrétní pracovní postup bez znalosti ID pracovního postupu, je třeba rekonstruovat každou trvalou instanci a prozkoumat obsah.  Mnoho vývojářů raději psát své vlastní poskytovatele vytrvalosti k překonání této překážky.

 Wf4 SQL trvalost zprostředkovatel se pokusil vyřešit některé z těchto problémů.  Tabulky trvalosti zveřejňují určité informace, jako jsou aktivní záložky a promotable vlastnosti.  Nová funkce korelace založená na obsahu v WF4 by nefungovala dobře pomocí přístupu trvalosti SQL WF3, který vyvolal některé změny v organizaci instance trvalého pracovního postupu.  To zkomplikuje úlohu zprostředkovatele trvalosti a klade zvláštní důraz na databázi.

### <a name="environment-setup"></a>Nastavení prostředí
![Nastavení prostředí pro test výkonu pracovního postupu](./media/performance/performance-test-environment.gif)

### <a name="test-setup"></a>Testovací nastavení
 I s vylepšenou sadou funkcí a lepším zpracováním souběžnosti je zprostředkovatel trvalosti SQL v WF4 rychlejší než poskytovatel v WF3.  Chcete-li předvést toto, dva pracovní postupy, které provádějí v podstatě stejné operace v WF3 a WF4 jsou porovnány níže.

 ![Pracovní postup trvalosti v WF3 vlevo a WF4 vpravo](./media/performance/persist-workflow-wf3-wf4.gif)

 Oba pracovní postupy jsou vytvořeny přijatou zprávou.  Po odeslání počáteční odpovědi je pracovní postup trvalý.  V případě WF3 prázdné <xref:System.Workflow.ComponentModel.TransactionScopeActivity> slouží k zahájení trvalosti.  Totéž by mohlo být dosaženo v WF3 označením aktivity jako "přetrvávají na blízko."  Druhá, korelační zpráva dokončí pracovní postup.  Pracovní postupy jsou trvalé, ale nejsou uvolněny.

### <a name="test-results"></a>Výsledky testů
 ![Sloupcový graf zobrazující trvalost propustnost](./media/performance/throughput-persistence-graph.gif)

 Při přenosu mezi klientem a střední vrstvy je HTTP, trvalost v WF4 ukazuje zlepšení 2,6 krát.  Přenos TCP zvyšuje tento faktor na 3,0 krát.  Ve všech případech využití procesoru na střední vrstvě je 98 % nebo vyšší.  Důvod, proč je propustnost WF4 větší, je způsoben rychlejším runtime pracovního postupu.  Velikost serializované instance je nízká pro oba případy a není hlavním přispívajícím prvkem v této situaci.

 Pracovní postupy WF3 a WF4 v tomto testu používají aktivitu k explicitnímu označení, kdy by mělo dojít k trvalozosti.  To má tu výhodu, že přetrvává pracovní postup bez jeho uvolnění.  V WF3 je také možné zachovat <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> pomocí funkce, ale to uvolní instanci pracovního postupu z paměti.  Pokud vývojář pomocí WF3 chce zajistit, že pracovní postup přetrvává v určitých bodech, musí buď změnit definici pracovního postupu nebo zaplatit náklady na uvolnění a opětovné načtení instance pracovního postupu.  Nová funkce v WF4 umožňuje zachovat bez <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>uvolnění: .  Tato funkce umožňuje instance pracovního postupu zachovat při nečinnosti, ale zůstat v paměti, dokud není <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> splněna prahová hodnota nebo spuštění je obnovena.

 Všimněte si, že wf4 SQL perzistence zprostředkovatele provádí více práce v databázové vrstvě.  Databáze SQL se může stát kritickým bodem, takže je důležité sledovat využití procesoru a disku.  Nezapomeňte zahrnout následující čítače výkonu z databáze SQL při testování výkonu pracovního postupu aplikací:

- Fyzický\\disk %Čas čtení disku

- Fyzický\\disk % čas disku

- Fyzický\\disk % doba zápisu na disk

- Fyzická\\doba odvráceného disku - délka fronty disku

- Délka fronty čtení disku PhysicalDisk\Avg. Disk

- PhysicalDisk\Avg. Délka fronty zápisu disku

- Fyzická doba/Aktuální délka fronty disku

- Informace\\o procesoru % času procesoru

- SQLServer:Západky\Průměrná čekací doba západky (ms)

- SQLServer:západky\Západka čeká/s

### <a name="tracking"></a>Sledování
 Sledování pracovního postupu lze použít ke sledování průběhu pracovního postupu.  Informace, které jsou zahrnuty v události sledování je určena sledování profilu.  Čím složitější je profil sledování, tím dražší je sledování.

 WF3 dodáván s službou sledování založené na SQL.  Tato služba může fungovat v dávkových a nedávkových režimech.  V nedávkovém režimu jsou sledování událostí zapsány přímo do databáze.  V dávkovém režimu jsou události sledování shromažďovány do stejné dávky jako stav instance pracovního postupu.  Dávkový režim má nejlepší výkon pro nejširší škálu návrhů pracovních postupů.  Dávkování však může mít negativní dopad na výkon, pokud pracovní postup spustí mnoho aktivit bez trvalého a tyto aktivity jsou sledovány.  To by se běžně stalo ve smyčkách a nejlepší způsob, jak se tomuto scénáři vyhnout, je navrhnout velké smyčky, které obsahují bod trvalosti.  Zavedení bodu trvalosti do smyčky může negativně ovlivnit výkon, takže je důležité měřit náklady každého z nich a přijít s rovnováhou.

 WF4 není dodáván se službou sledování SQL.  Záznam informace o sledování do databáze SQL lze lépe zpracovat z aplikačního serveru, nikoli zabudované do rozhraní .NET Framework. Proto sql sledování je nyní zpracována AppFabric.  Zprostředkovatel sledování out-of-the-box v WF4 je založen na trasování událostí pro Windows (ETW).

 ETW je systém událostí na úrovni jádra s nízkou latencí zabudovaný do systému Windows.  Používá model zprostředkovatele nebo spotřebitele, který umožňuje pouze vynaložit sankci za trasování událostí, pokud je skutečně spotřebitel.  Kromě událostí jádra, jako je procesor, disk, paměť a využití sítě, mnoho aplikací využívá také ETW.  Události ETW jsou výkonnější než čítače výkonu v tom, že události lze přizpůsobit aplikaci.  Událost může obsahovat text, například ID pracovního postupu nebo informační zprávu.  Události jsou také rozděleny do kategorií s bitové masky tak, aby náročné určitou podmnožinu událostí bude mít menší dopad na výkon než zachycení všech událostí.

 Výhody přístupu pomocí ETW pro sledování namísto SQL patří:

- Kolekce událostí sledování lze oddělit do jiného procesu.  To poskytuje větší flexibilitu v tom, jak jsou zaznamenány události.

- ETW sledování událostí lze snadno kombinovat s WCF ETW události nebo jiných poskytovatelů ETW, jako je například SQL Server nebo poskytovatele jádra.

- Autoři pracovního postupu nemusí měnit pracovní postup, aby lépe fungoval s konkrétní implementací sledování, jako je například dávkový režim služby sledování SQL WF3.

- Správce může sledování zapnout nebo vypnout bez recyklace hostitelského procesu.

 Výhody výkonu pro sledování ETW přicházejí s nevýhodou.  Události ETW mohou být ztraceny, pokud je systém pod silným tlakem zdrojů.  Zpracování událostí není určen k zablokování normální spuštění programu, a proto není zaručeno, že všechny Události ETW budou vysílány svým předplatitelům.  Díky tomu je sledování ETW skvělé pro sledování stavu, ale není vhodné pro auditování.

 Zatímco WF4 nemá zprostředkovatele sledování SQL, AppFabric nemá.  AppFabric je SQL sledování přístup je přihlásit k odběru událostí ETW se službou systému Windows, která dávky události a zapíše je do tabulky SQL určené pro rychlé vložení.  Samostatná úloha vyčerpádata z této tabulky a reformy do tabulky vytváření sestav, které lze zobrazit na řídicím panelu AppFabric.  To znamená, že dávka sledování událostí je zpracována nezávisle na pracovním postupu, ze kterého pochází, a proto nemusí čekat na bod trvalosti před zaznamenáním.

 ETW události lze zaznamenávat pomocí nástrojů, jako je logman nebo xperf.  Kompaktní soubor ETL lze zobrazit pomocí nástroje, jako je xperfview, nebo převeden do čitelnějšího formátu, například XML, s tracerpt.  V WF3 jedinou možností pro získání sledování událostí bez databáze SQL je vytvořit vlastní sledování služby. Další informace o ETW naleznete v [tématu WCF Services and Event Tracing for Windows](../wcf/samples/wcf-services-and-event-tracing-for-windows.md) and [Event Tracing - Windows applications](/windows/desktop/etw/event-tracing-portal).

 Povolení sledování pracovního postupu bude mít vliv na výkon v různé míře.  Níže uvedené měřítko používá nástroj logman ke spotřebování událostí sledování ETW a jejich zaznamenání do souboru ETL.  Náklady na sledování SQL v AppFabric není v oboru tohoto článku.  Základní profil sledování, který se také používá v AppFabric, je zobrazen v tomto benchmarku.  Zahrnuty jsou také náklady na sledování pouze událostí sledování stavu.  Tyto události jsou užitečné pro řešení problémů a určení průměrné propustnost systému.

### <a name="environment-setup"></a>Nastavení prostředí
 ![Nastavení prostředí pro test výkonu pracovního postupu](./media/performance/performance-test-environment.gif)

### <a name="test-results"></a>Výsledky testů

 ![Sloupcový graf zobrazující náklady na sledování pracovního postupu](./media/performance/workflow-tracking-costs.gif)

 Monitorování stavu má zhruba 3% vliv na propustnost.  Základní náklady profilu se pohybují kolem 8 %.

## <a name="interop"></a>Zprostředkovatel komunikace
 WF4 je téměř kompletní [!INCLUDE[wf1](../../../includes/wf1-md.md)] přepsání, a proto WF3 pracovních postupů a aktivity nejsou přímo kompatibilní s WF4.  Mnoho zákazníků, kteří přijali Windows Workflow Foundation brzy bude mít in-house nebo definice pracovních postupů třetích stran a vlastní aktivity pro WF3.  Jedním ze způsobů, jak usnadnit přechod na WF4, je použití aktivity Interop, která může provádět aktivity WF3 z pracovního postupu WF4.  Doporučuje se, <xref:System.Activities.Statements.Interop> aby se aktivita používala pouze v případě potřeby. Další informace o migraci na WF4 najdete v [pokynech pro migraci WF4](migration-guidance.md).

### <a name="environment-setup"></a>Nastavení prostředí
 ![Nastavení prostředí pro test výkonu pracovního postupu](./media/performance/performance-test-environment.gif)

### <a name="test-results"></a>Výsledky testů

V následující tabulce jsou uvedeny výsledky spuštění pracovního postupu obsahujícího pět aktivit v sekvenci v různých konfiguracích.

|Test|Propustnost (pracovní postupy/s)|
|----------|-----------------------------------|
|Sekvence WF3 v běhu WF3|1,576|
|Sekvence WF3 v běhu WF4 pomocí interopu|2,745|
|Sekvence WF4|153,582|

 Tam je pozoruhodný nárůst výkonu pomocí Interop přes rovnou WF3.  Ve srovnání s aktivitami WF4 je však zvýšení zanedbatelné.

## <a name="summary"></a>Souhrn
 Velké investice do výkonu wf4 se vyplatily v mnoha klíčových oblastech.  Výkon jednotlivých komponent pracovního postupu je v některých případech stokrát [!INCLUDE[wf1](../../../includes/wf1-md.md)] rychlejší v WF4 ve srovnání s WF3 z důvodu štíhlejší hoběhu.  Latence čísla jsou výrazně lepší stejně.  To znamená, že [!INCLUDE[wf1](../../../includes/wf1-md.md)] snížení výkonu pro použití na rozdíl od ruční kódování WCF [!INCLUDE[wf1](../../../includes/wf1-md.md)]orchestrace služby je velmi malý vzhledem k přidané výhody použití .  Perzistence výkon zvýšil o faktor 2,5 - 3,0.  Monitorování stavu pomocí sledování pracovního postupu má nyní velmi malou režii.  Komplexní sada průvodců migrace jsou k dispozici pro ty, kteří zvažují přechod z WF3 na WF4.  To vše by mělo wf4 atraktivní volbou pro psaní složitých aplikací.
