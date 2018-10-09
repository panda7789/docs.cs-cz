---
title: Výkon Windows Workflow Foundation 4
ms.date: 03/30/2017
ms.assetid: 67d2b3e8-3777-49f8-9084-abbb33b5a766
ms.openlocfilehash: c7dc098eee5f17e18f76c0b54a097a22f5d844b1
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873690"
---
# <a name="windows-workflow-foundation-4-performance"></a>Výkon Windows Workflow Foundation 4
Dustinu Metzgar

 Wenlong Dong

 V září roku 2010 Microsoft Corporation

 Microsoft [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] obsahuje hlavní revize Windows Workflow Foundation (WF) s rozsáhlé investice výkonu.  Tato nová revize představuje významné změny z předchozích verzí [!INCLUDE[wf1](../../../includes/wf1-md.md)] dodávané jako součást rozhraní .NET Framework 3.0 a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Byla přepracována ze základní programovací model, modul runtime a nástroje, které výrazně zlepšit výkon a použitelnost. Toto téma ukazuje důležité výkonové charakteristiky těchto revizí a porovnává je s ohledem na předchozí verzi.

 Výkon součásti jednotlivé pracovní postup se zvýšila řádově mezi WF3 a WF4.  Kvůli tomu mezera mezi dolním pevně zakódované služby Windows Communication Foundation (WCF) a služby pracovního postupu WCF poměrně malý.  Latence pracovního postupu byla v WF4 výrazně omezeno.  Trvalost výkonu se zvýšila faktor 2.5 3.0.  Monitorování stavu pomocí sledování pracovního postupu má podstatně menší nároky.  Tyto jsou přesvědčivé důvody pro migraci do nebo přijímat WF4 ve svých aplikacích.

## <a name="terminology"></a>Terminologie
 Verze [!INCLUDE[wf1](../../../includes/wf1-md.md)] zavedený [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] bude označovat jako WF4 pro zbývající část tohoto tématu.  [!INCLUDE[wf1](../../../includes/wf1-md.md)] byla zavedena v rozhraní .net 3.0 a má několik vedlejších revize prostřednictvím [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] SP1. [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Verzi Workflow Foundation bude označovat jako WF3 pro zbývající část tohoto tématu. Je součástí WF3 [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] – souběžně s WF4. Další informace o migraci WF3 artefakty, které WF4 naleznete v tématu: [Windows Workflow Foundation 4 Průvodce migrací](https://go.microsoft.com/fwlink/?LinkID=153313)

 Windows Communication Foundation (WCF) je jednotný programovací model pro vytváření aplikací orientovaných na služby od Microsoftu. Bylo poprvé dostupné jako součást .net 3.0 spolu s WF3 a nyní je jedním z klíčových součástí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].

 Windows Server AppFabric je sada integrovaných technologií, které usnadňují vytváření, škálování a správu webových a kompozitních aplikací, které běží ve službě IIS. Poskytuje nástroje pro monitorování a správu služeb a pracovních postupů. Další informace najdete v tématu [Windows Server AppFabric](https://msdn.microsoft.com/windowsserver/ee695849.aspx)

## <a name="goals"></a>Cíle
 Cílem tohoto tématu je zobrazit charakteristiky výkonu WF4 s daty měří pro různé scénáře. Také poskytuje podrobné porovnání WF4 a WF3 a proto zobrazuje skvělé vylepšení, které byly provedeny v této nové revize. Scénáře a data uvedená v tomto článku vyčíslení základní náklady na různé aspekty WF4 a WF3. Tato data je užitečné porozumět charakteristiky výkonu WF4 a mohou být užitečné při plánování migrace z WF3 do WF4 nebo pomocí WF4 při vývoji aplikace. Však mělo dbát v závěry z data uvedená v tomto článku. Výkon aplikace složený pracovního postupu je vysoce závislé na tom, jak je implementován pracovního postupu a jak různé součásti jsou integrovány. Jeden musí měření každou aplikaci k určení výkonové charakteristiky této aplikace.

## <a name="overview-of-wf4-performance-enhancements"></a>Přehled vylepšení výkonu WF4
 WF4 pečlivě byly navrženy a implementovány s vysokým výkonem a škálovatelností, které jsou popsány v následujících částech.

### <a name="wf-runtime"></a>Modul Runtime pracovního postupu
 V jádru služby [!INCLUDE[wf1](../../../includes/wf1-md.md)] modul runtime je asynchronní plánovače, který řídí spuštění aktivity v pracovním postupu. Poskytuje výkonný, předvídatelný spouštěcí prostředí pro aktivity. Prostředí má dobře definované smlouvy pro spuštění, pokračování, dokončování, zrušení, výjimky a předvídatelné modelu vláken.

 Porovnání WF3 má modul runtime WF4 efektivnější plánovače. Využívá stejné fondu vláken vstupně-výstupních operací, který se používá pro službu WCF, což je velmi efektivní při provádění dávkových pracovních položek. Fronty plánovače interní pracovní položky je optimalizovaná pro nejběžnější vzory využití. Modul runtime WF4 také spravuje stavy provádění tak velmi nenáročné s minimálními synchronizace a zpracování logiku, zatímco WF3 závisí na události zobrazené – registrace a vyvolání provádět komplexní synchronizace pro přechodů mezi stavy událostí.

### <a name="data-storage-and-flow"></a>Úložiště dat a toku
 V WF3, data spojená s aktivitou modelováním pomocí vlastnosti závislosti daným typem implementováno <xref:System.Windows.DependencyProperty>. Vzor závislostí vlastnost byla zavedena ve Windows Presentation Foundation (WPF). Obecně platí tento vzor je velmi flexibilní podporu jednoduché datové vazby a další funkce uživatelského rozhraní. Vzor ale vyžaduje vlastnosti, které mají být definovány jako statické pole v definici pracovního postupu. Pokaždé, když [!INCLUDE[wf1](../../../includes/wf1-md.md)] runtime Nastaví nebo získá hodnoty vlastností, zahrnuje logiku silně váha vyhledávání.

 WF4 používá vymazat data rozsahu logiky výrazně zlepšit způsob zpracování dat v pracovním postupu. Rozděluje data uložená v nějaké aktivitě z data, která se přenášejí přes hranice aktivity s použitím dva různé koncepty: proměnné a argumenty. Pomocí vymazat hierarchického oboru proměnné a argumenty "V/Out nebo InOut" složitosti dat využití pro aktivity došlo k podstatnému omezení a životního cyklu dat má také automaticky obor. Aktivity mají jasně definovaných podpis popsal svých argumentů. Jednoduše zkontrolováním aktivity můžete určit, jaká data se očekává, že pro příjem a jaká data se budou vytvářet pomocí něj v důsledku jeho spuštění.

 V WF3 aktivity byly inicializovány při vytvoření pracovního postupu. V WF 4 aktivity jsou inicializovány pouze v případě, že jsou spuštěny odpovídající aktivity. To umožňuje jednodušší životní cyklus aktivity bez provedení inicializace nebo volání metody Uninitialize operace při nové instance pracovního postupu je vytvořena a získala tedy další efektivity

### <a name="control-flow"></a>Tok řízení
 Stejně jako v jakémkoli programovacím jazyce a [!INCLUDE[wf1](../../../includes/wf1-md.md)] poskytuje podporu pro ovládací prvek toky pro definice pracovního postupu pomocí Představujeme sadu aktivity toku řízení pro sekvencování, využívat konstruktory cyklů, větvení a jiné vzory. V WF3, když se stejná aktivita je nutné znovu spustit, nový <xref:System.Workflow.ComponentModel.ActivityExecutionContext> se vytvoří a aktivity naklonování prostřednictvím náročné serializace a deserializace logiky na základě <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Výkon pro toky iterativní ovládací prvek je obvykle mnohem pomalejší než provádí sekvenci aktivit.

 WF4 zpracovává to úplně jinak. Přijímá šablona aktivity, vytvoří nový objekt vlastnosti ActivityInstance a přidá ji do fronty plánovače. Tento celý proces pouze zahrnuje explicitní vytváření objektů a je velmi zjednodušené.

### <a name="asynchronous-programming"></a>Asynchronní programování
 Aplikace obvykle mají lepší výkon a škálovatelnost s asynchronním programování pro dlouho běžící blokující operace, jako jsou vstupně-výstupních operací nebo distribuované výpočetní operace. Poskytuje asynchronní podporu prostřednictvím základní aktivity typů WF4 <xref:System.Activities.AsyncCodeActivity>, <xref:System.Activities.AsyncCodeActivity%601>. Modul runtime nativně podporuje asynchronní aktivity a proto můžou automaticky vložit instanci no-persist zóny během nezpracovaný asynchronní práce. Vlastní aktivity lze odvodit z těchto typů provádět asynchronní práce bez podržení Plánovač vlákna pracovního postupu a blokuje veškeré aktivity, které může být možné spouštět paralelně.

### <a name="messaging"></a>Zasílání zpráv
 WF3 měl původně velmi omezenou podporu zasílání zpráv prostřednictvím externí události nebo webové služby volání. V rozhraní .net 3.5, může být pracovní postupy implementovaná jako klienti WCF nebo vystavený jako služba WCF services přes <xref:System.Workflow.Activities.SendActivity> a <xref:System.Workflow.Activities.ReceiveActivity>. V WF4 koncept zasílání zpráv programování založené na pracovních postupech je dále posílena Díky těsné integraci logiku pro zasílání zpráv do pracovního postupu WCF.

 Kanál zpracování jednotné zasílání zpráv, které jsou součástí WCF v rozhraní .net 4 pomáhá WF4 služby mají výrazně lepší výkon a škálovatelnost než WF3. WF4 také podporuje bohatší zasílání zpráv programování, které lze modelovat složité vzorce výměny zpráv (MEPs). Vývojáři můžete použít buď zadaný servisní smlouvy dosáhnout snadné programování nebo netypové servisní smlouvy můžete dosáhnout lepšího výkonu bez nutnosti platit náklady na serializaci. Ukládání do mezipaměti podporu prostřednictvím kanálů na straně klienta <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy v WF4 pomáhá vývojářům vestavět rychlé aplikace s minimálním úsilím. Další informace najdete v tématu [změna úrovní sdílení mezipaměti pro aktivity odesílání](../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).

### <a name="declarative-programming"></a>Deklarativní programování
 WF4 poskytuje vyčistit a jednoduchý deklarativní programovací rozhraní pro modelování obchodních procesů a služeb. Programovací model podporuje plně deklarativního složení aktivit se žádný kód – vedle, což výrazně zjednodušuje vytváření pracovního postupu. V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], založené na XAML deklarativní programovací rozhraní má sjednocené do jednoho sestavení System.Xaml.dll pro podporu WPF a WF.

 XAML v WF4, poskytuje skutečně deklarativní prostředí a umožňuje celý definice pracovního postupu definovat kód XML, odkazující na činnosti a typy, které jsou vytvořené pomocí .NET. To bylo obtížné v WF3 dělat s formát XOML bez zásahu logiku vlastního kódu. Nový zásobník XAML v rozhraní .net 4 má mnohem lepší výkon při serializaci/deserializaci artefakty pracovního postupu a díky tomu je atraktivní a solid deklarativní programování.

### <a name="workflow-designer"></a>Návrhář postupu provádění
 Plně deklarativního programovací podpora WF4 explicitně ukládá vyšším požadavkům na výkon času návrhu pro velké pracovních postupů. Návrháři pracovních postupů v WF4 má mnohem lepší škálovatelnost než pro velké pracovní postupy pro WF3. S podporou virtualizace uživatelského rozhraní Návrhář můžete snadno načíst velké pracovního postupu 1000 aktivit za pár sekund, i když je téměř nemožné načíst několik stovek aktivit pracovního postupu pomocí návrháře WF3.

## <a name="component-level-performance-comparisons"></a>Porovnání komponenty úroveň výkonu
 Tato část obsahuje data na přímé porovnání mezi jednotlivé aktivity v pracovních postupech WF3 a WF4.  Klíčové oblasti, například trvalost mít mnohem důkladnější dopad na výkon než komponenty jednotlivých aktivit.  Vylepšení výkonu v jednotlivých součástí v WF4 jsou ale důležité, protože se teď dostatečně rychle, který se má porovnat proti logiku straně pevně zakódované Orchestrace součásti.  Následuje příklad je popsaný v následující části: "Scénář služeb složení."

### <a name="environment-setup"></a>Nastavení prostředí
 ![Pracovní postup prostředí pro testování výkonu](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")

 Výše uvedené schéma ukazuje konfiguraci počítače pro měření výkonu na úrovni součásti. Jeden server a pět klienti připojení více než jedno síťové rozhraní Ethernet 1 GB/s. Pro snadné měření je server nakonfigurován na použití jediného jádra dual-proc/čtyřjádrový serveru se systémem Windows Server 2008 x86. Využití procesoru v systému je udržován na úrovni téměř 100 %.

### <a name="test-details"></a>Podrobnosti o testu
 WF3 <xref:System.Workflow.Activities.CodeActivity> je pravděpodobně nejjednodušším aktivity, která lze použít v pracovním postupu WF3.  Aktivity volá metodu v kódu, který programátor pracovního postupu můžete umístit do vlastního kódu.  Na WF4, není k dispozici na WF3 žádné přímou obdobu jmenovek <xref:System.Workflow.Activities.CodeActivity> , který poskytuje stejné funkce.  Všimněte si, že je <xref:System.Activities.CodeActivity> základní třídy v WF4, které nesouvisí WF3 <xref:System.Workflow.Activities.CodeActivity>.  Autoři pracovního postupu se doporučuje vytvořit vlastní aktivity a vytvářet pracovní postupy pouze pro XAML.  Ve níže testy s názvem aktivita `Comment` použijí se místo prázdná <xref:System.Workflow.Activities.CodeActivity> v pracovních postupech WF4.  Kód v `Comment` aktivit vypadá takto:

```
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
 Tento test používá pracovní postup pořadí bez podřízených aktivit.

### <a name="single-activity"></a>Jedna aktivita
 Pracovní postup je pořadí pracovní postup obsahující jednu podřízenou aktivitu.  Aktivita je <xref:System.Workflow.Activities.CodeActivity> bez kódu v případě WF3 a `Comment` aktivitu v případě WF4.

### <a name="while-with-1000-iterations"></a>Při s 1000 iterací
 Pracovní postup posloupnost obsahuje jeden <xref:System.Activities.Statements.While> aktivity s jednu podřízenou aktivitou ve smyčce, který neprovádí žádnou práci.

### <a name="replicator-compared-to-parallelforeach"></a>Replikace ve srovnání s ParallelForEach
 <xref:System.Workflow.Activities.ReplicatorActivity> v WF3 má režimy paralelní a sekvenční provádění.  Do sekvenčního režimu výkonu aktivity se podobá <xref:System.Workflow.Activities.WhileActivity>.  <xref:System.Workflow.Activities.ReplicatorActivity> Je zvláště užitečná pro paralelní zpracování.  Je obdobu jmenovek WF4 to <xref:System.Activities.Statements.ParallelForEach%601> aktivity.

 Následující diagram znázorňuje pracovních postupech, používat pro tento test. Pracovní postup WF3 je na levé straně a pracovní postup WF4 je na pravé straně.

 ![WF3 Aktivitou typu ReplicatorActivity a WF4 ParallelForEach](../../../docs/framework/windows-workflow-foundation/media/replicatorandparallelforeach.gif "ReplicatorAndParallelForEach")

### <a name="sequential-workflow-with-five-activities"></a>Sekvenční pracovní postup s pěti aktivity
 Tento test slouží k zobrazení účinek s několika sekvenční aktivity.  Existuje pět aktivit v sekvenci.

### <a name="transaction-scope"></a>Obor transakce
 Test oboru transakce z jiných testů se mírně liší v tom, že pro každou iteraci není vytvořena nová instance pracovního postupu.  Místo toho strukturovaná pracovního postupu s nějakou obsahující smyčky <xref:System.Activities.Statements.TransactionScope> aktivity, který obsahuje jednu aktivitu, která nemá žádné pracovní.  Každé spuštění služby batch pomocí while 50 iterací smyčky se přitom počítá jako jediná operace.

### <a name="compensation"></a>Kompenzace
 Pracovní postup WF3 obsahuje jednu aktivitu aktivita s názvem `WorkScope`.  Aktivita jednoduše implementuje <xref:System.Workflow.ComponentModel.ICompensatableActivity> rozhraní:

```
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

 Cíle obslužná rutina chyby `WorkScope` aktivity. Pracovní postup WF4 je stejně zjednodušenou.  A <xref:System.Activities.Statements.CompensableActivity> má tělo a obslužnou rutinu kompenzace.  Explicitní funkce compensate se chystá v sekvenci.  Aktivitu tělo a obslužnou rutinu kompenzace aktivity kompenzace jsou oba prázdná implementace:

```
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

 ![Pracovní postupy základní kompenzace WF3 a WF](../../../docs/framework/windows-workflow-foundation/media/basiccompensationworkflows.gif "BasicCompensationWorkflows")

 Obrázek 2 – WF3 (vlevo) a pracovní postupy (vpravo) základní kompenzace WF4

### <a name="performance-test-results"></a>Výsledky testů výkonu
 ![Výsledky testů výkonu](../../../docs/framework/windows-workflow-foundation/media/performancedata.gif "elementu PerformanceData")

 ![Graf dat výkonu testu](../../../docs/framework/windows-workflow-foundation/media/performancetestchart.gif "PerformanceTestChart")

 Všechny testy se měří v pracovní postupy za sekundu, s výjimkou testovacího oboru transakce.  Jak je vidět výše, [!INCLUDE[wf1](../../../includes/wf1-md.md)] na panelu, zejména v oblasti, které vyžadují více provedení aktivity jako while se zvýšil výkon modulu runtime smyčky.

## <a name="service-composition-scenario"></a>Scénář služby sestavení
 Jak je znázorněno v předchozí části "součást úrovně výkonu porovnávání," došlo k významnému snížení režie mezi WF3 a WF4.  Můžete teď téměř odpovídá výkonu ručně pevně zakódované služeb WCF ale stále mít všechny výhody služby pracovního postupu WCF [!INCLUDE[wf1](../../../includes/wf1-md.md)] modulu runtime.  Tento scénář testování porovnává proti služby pracovního postupu WCF v WF4 ve službě WCF.

### <a name="online-store-service"></a>Služby Online Store
 Jednou z výhod modelu Windows Workflow Foundation je schopnost compose procesy pomocí několika služeb.  V tomto příkladu je službě online úložiště, která orchestruje dvě volání služby nákupní objednávky.  Prvním krokem je ověření pomocí služby ověřování objednávka pořadí.  Druhým krokem je tak, aby vyplnil pořadí pomocí služba datového skladu.

 Dva back-endových služeb, pořadí ověřování služba a služba datového skladu, zůstávají stejné pro oba testy.  Část, která se mění je Online služba Store, který provádí orchestraci.  V jednom případě je služba ručně pevně zakódované jako služba WCF.  Případě služby je zapsán jako pracovní postup služby WCF ve WF4. [!INCLUDE[wf1](../../../includes/wf1-md.md)]-konkrétní funkce, jako je sledování a stálost jsou vypnuté pro tento test.

### <a name="environment"></a>Prostředí
 ![Pracovní postup prostředí pro testování výkonu](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")

 Z několika počítačů jsou vytvářeny požadavky klienta ke službě Store Online přes protokol HTTP.  Jeden počítač hostuje všechny tři služby.  Přenosová vrstva mezi Online službu Store a back-endových služeb je TCP nebo HTTP.  Měření operací za sekundu je založena na počet dokončených `PurchaseOrder` volání na Online službu Store.  Sdružování kanálu je k dispozici v WF4 novou funkci.  V WCF část sdružování tento test kanálu není k dispozici ihned tak ruční pevně zakódované implementace jednoduché techniky sdružování byl použit v Online službě Store.

### <a name="performance"></a>Výkon
 ![Graf výkonu služby Online Store](../../../docs/framework/windows-workflow-foundation/media/onlinestoreperfgraph.gif "OnlineStorePerfGraph")

 Připojení k back-endových služeb TCP bez sdružování kanál [!INCLUDE[wf1](../../../includes/wf1-md.md)] služba má 17.2 % dopad na propustnost.  Sdružování kanál sankce je přibližně % 23,8.  Pro protokol HTTP, dopad je mnohem méně: % 4.3 bez sdružování a % 8.1 s sdružování.  Je také důležité si uvědomit, že kanál sdružování poskytuje velmi málo výhodné při použití protokolu HTTP.

 Zatímco je režie z modulu runtime WF4 v porovnání s ruční pevně zakódované služby WCF v tomto testu, může za nejhorším případě.  Dvě back-end služby v tomto testu se příliš mnoho zásahů.  V případě reálné začátku do konce v těchto služeb by činností, dražší, jako je volání databáze, což dopad na výkon z přenosové vrstvy méně důležité.  To a výhody funkcí dostupných v WF4 díky přijatelné volba pro vytvoření orchestračních službách Workflow Foundation.

## <a name="key-performance-considerations"></a>Důležité informace o výkonu
 Oblasti funkcí v této části, s výjimkou komunikace, výrazně změnili mezi WF3 a WF4.  To má vliv na návrh aplikací pracovních postupů, jakož i výkon.

#### <a name="workflow-activation-latency"></a>Pracovní postup aktivace latence
 V aplikaci služby pracovního postupu WCF je důležité, protože může být blokování latence pro spouštění nového pracovního postupu nebo načítání stávajícím pracovním postupu.  Tento testovací případ opatření proti WF4 XAMLX hostitele v rámci typického scénáře hostitele WF3 XOML.

##### <a name="environment-setup"></a>Nastavení prostředí
 ![Nastavení prostředí pro testy latenci a propustnost](../../../docs/framework/windows-workflow-foundation/media/latencyandthroughputenvironment.gif "LatencyAndThroughputEnvironment")

##### <a name="test-setup"></a>Nastavení testu
 Ve scénáři klientský počítač kontaktuje služby pracovního postupu WCF pomocí korelace na základě kontextu.  Korelace kontextové vyžaduje speciální kontextu vazby a zpráv se týkají instance správné pracovního postupu pomocí hlavičku kontextu nebo soubor cookie.  Má výkonu, která přináší korelace, které Id se nachází v záhlaví zprávy, takže není nutné analyzovat tělo zprávy.

 Službu vytvoříte nový pracovní postup s požadavkem a odeslat okamžitou reakci, takže měření latence nezahrnuje čas strávený spuštění pracovního postupu.  Je pracovní postup WF3 XOML s kódem na pozadí a je zcela v pracovním postupu WF4 XAML.  Pracovní postup WF4 vypadá takto:

 ![WF 4 korelace oboru](../../../docs/framework/windows-workflow-foundation/media/correlationscopeworkflow.gif "CorrelationScopeWorkflow")

 <xref:System.ServiceModel.Activities.Receive> Aktivita vytvoří instanci pracovního postupu.  Hodnotu předanou v přijaté zprávě se budou vypisovat ve zprávě odpovědi.  Pořadí následující odpověď obsahuje zbývající části pracovního postupu.  Ve výše uvedeném případě se zobrazí pouze jeden komentář aktivity.  Počet aktivit komentář se změní na simulovat složitost pracovního postupu.  Aktivita komentář je ekvivalentní WF3 <xref:System.Workflow.Activities.CodeActivity> , který provede žádná práce. Další informace o aktivitě komentář najdete v oddílu "porovnání výkonu úrovni součástí" výše v tomto článku.

##### <a name="test-results"></a>Výsledky testů
 ![Latence výsledky](../../../docs/framework/windows-workflow-foundation/media/latencyresultsgraph.gif "LatencyResultsGraph")

 Obrázek 3 – studených a vyzkoušeli latence pro služby pracovního postupu WCF

 V grafu nahoře studeného odkazuje na tento případ tam, kde není nedoběhla <xref:System.ServiceModel.WorkflowServiceHost> pro daný pracovní postup.  Studená latence je jinými slovy, když pracovní postup se používá pro první a XOML nebo XAML musí být zkompilována.  Horké latence je čas při vytváření nové instance pracovního postupu, když typ pracovního postupu již byla zkompilována.  Složitost pracovního postupu je jen malý rozdíl v případě WF4, ale má většinou lineární posloupnost v případě WF3.

#### <a name="correlation-throughput"></a>Propustnost korelace
 WF4 zavádí nové funkce založené na obsahu korelace.  WF3 k dispozici pouze korelace na základě kontextu.  Korelace na základě kontextu může provést jenom přes konkrétní vazby kanálu WCF.  Id pracovního postupu je vložen do záhlaví zprávy při používání těchto vazeb.  Modul runtime WF3 pouze zjistit pracovního postupu pomocí jeho Id.  Pomocí korelace na základě obsahu Autor pracovního postupu můžete vytvořit klíč korelace mimo relevantní část dat, jako je číslo účtu nebo zákazník Id.

 Korelace na základě kontextu má výkonu výhodu v tom, že klíč korelace se nachází v záhlaví zprávy.  Klíče může číst ze zprávy bez rušení-serialization/zprávu kopírování.  V korelace na základě obsahu se má uložit klíč korelace v textu zprávy.  Výraz XPath je používaná k nalezení klíč.  Náklady na tento další zpracování závisí na velikosti zprávy hloubky klíče v těle a počet klíčů.  Tento test porovná korelace na základě kontextu a obsahu a také ukazuje snížení výkonu, při použití více klíčů.

#### <a name="environment-setup"></a>Nastavení prostředí
 ![Pracovní postup prostředí pro testování výkonu](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")

#### <a name="test-setup"></a>Nastavení testu
 ![Srovnávací Test pracovního postupu propustnost](../../../docs/framework/windows-workflow-foundation/media/correlationthroughputworkflow.gif "CorrelationThroughputWorkflow")

 Výše uvedené pracovní postup je stejný jako ten používá v níže uvedené části "Trvalost".  Pro srovnávací testy bez trvalost není žádný poskytovatel trvalého nainstalované v modulu runtime.  Korelace dochází na dvou místech: CreateOrder a CompleteOrder.

#### <a name="test-results"></a>Výsledky testů
 ![Korelace propustnost](../../../docs/framework/windows-workflow-foundation/media/correlationthroughputgraph.gif "CorrelationThroughputGraph")

 Tento graf ukazuje ke snížení výkonu jako počet klíčů používaných pro zvýšení korelace na základě obsahu.  Podobnosti křivky mezi TCP nebo HTTP označuje režii spojenou s tyto protokoly.

#### <a name="correlation-with-persistence"></a>Korelace s trvalostí
 S trvalou pracovního postupu zatížení procesoru z korelace na základě obsahu přesouvá z modulu runtime pracovního postupu do služby SQL database.  Uložených procedur na SQL poskytovatele trvalého chování práci shodujících se klíčích najít odpovídající pracovního postupu.

 ![Korelace a stálost výsledky](../../../docs/framework/windows-workflow-foundation/media/correlationandpersistencegraph.gif "CorrelationAndPersistenceGraph")

 Korelace na základě kontextu je stále vyšší než korelace na základě obsahu.  Rozdíl je ale, že menší vyslovováno trvalost má mít větší vliv na výkon než korelace.

### <a name="complex-workflow-throughput"></a>Propustnost komplexní pracovní postup
 Složitost pracovního postupu není změřit pouze podle počtu aktivit.  Složené aktivity může obsahovat mnoho podřízených objektů a tyto podřízené objekty mohou být také složených aktivit.  Jako počet úrovní vnoření zvýšení postupy zločinců se počet aktivit, které mohou být aktuálně v prováděného stavu a počtu proměnných, které mohou být ve stavu.  Tento test porovnává propustnosti mezi WF3 a WF4 při provádění komplexní pracovní postupy.

### <a name="test-setup"></a>Nastavení testu
 Tyto testy byly spuštěny na Intel Xeon X5355 @ 2,66 GHz počítač 4-způsob, jak s 4 GB paměti RAM, s Windows serverem 2008 x64.  Testovací kód je spuštěn v jediném procesu s jedním vláknem na jádro k dosažení 100 % využití CPU.

 Pracovní postupy pro tento test vygenerovat mají dvou hlavních proměnných: hloubka a počet aktivit v každé posloupnosti.  Každá úroveň hloubky zahrnuje paralelní aktivity při smyčky, rozhodnutí, přiřazení a pořadí.  V Návrháři WF4 na obrázku níže je nejvyšší úrovně vývojový diagram na obrázku.  Každý vývojový diagram aktivity se podobá hlavní vývojový diagram.  Může být užitečné si představit fraktálový při picturing tento pracovní postup, kde je omezená na parametry testu hloubku.

 Počet aktivit v rámci daného testu je určeno hloubky a počet aktivit za pořadí.  Do následující rovnice vypočítá počet aktivit v WF4 testu:

 ![Rovnice vypočítat počet aktivit](../../../docs/framework/windows-workflow-foundation/media/numberofactivitiesequation.gif "NumberOfActivitiesEquation")

 Nelze vypočítat počet aktivit WF3 testů se mírně liší rovnice kvůli navíc pořadí:

 ![Rovnice vypočítat počet aktivit](../../../docs/framework/windows-workflow-foundation/media/w3numberofactivitiesequation.gif "W3NumberOfActivitiesEquation")

 Kde je hloubka d a je počet aktivit za pořadí.  Logika za tyto rovnice je, že první konstanta vynásobené, je číslo pořadí a druhá konstanta je statický počet aktivit v aktuální úroveň.  Existují tři podřízené aktivity flowchart v každé vývojový diagram.  Na nejnižší úrovni hloubka na jiných úrovních kopie hlavní vývojový diagram jsou však tyto vývojové diagramy jsou prázdné.  Počet aktivit v definici pracovního postupu pro každý test variace je uvedeno v následující tabulce:

 ![Porovná počet aktivit používaných v každém testovacím](../../../docs/framework/windows-workflow-foundation/media/comparechart.gif "CompareChart")

 Počet aktivit v definici pracovního postupu prudce zvyšuje s každou úroveň hloubky.  Spustí jenom jednu cestu na posledním bodem rozhodnutí v instanci daného pracovního postupu, provádějí pouze malou podmnožinu skutečné aktivity.

 ![Komplexní pracovní postup](../../../docs/framework/windows-workflow-foundation/media/complexworkflowthroughputworkflow.gif "ComplexWorkflowThroughputWorkflow")

 Ekvivalentní pracovní postup byl vytvořen pro WF3. Návrhář WF3 ukazuje celý pracovní postup v oblasti návrhu místo vnoření, proto, že je příliš dlouhý pro zobrazení v tomto tématu. Fragment kódu pracovního postupu je uveden níže.

 ![WF3 Pracovní postup](../../../docs/framework/windows-workflow-foundation/media/wf3workflow.gif "WF3Workflow")

 Vykonávat vnoření v extrémním případě používá jiný pracovní postup, který je součástí tohoto testu 100 vnořené sekvence.  Nejvnitřnější postupně se jeden `Comment` nebo <xref:System.Workflow.Activities.CodeActivity>.

 ![Vnořené sekvence](../../../docs/framework/windows-workflow-foundation/media/nestedsequencewf.gif "NestedSequenceWF")

 Sledování a stálost nejsou použity jako součást tohoto testu.

### <a name="test-results"></a>Výsledky testů
 ![Graf propustnosti](../../../docs/framework/windows-workflow-foundation/media/testresults1.gif "TestResults1")

 I s komplexní pracovní postupy s mnoha hloubky a vysoký počet aktivit výsledky výkonu jsou konzistentní s jinými propustnost čísly uvedené dříve v tomto článku.  Propustnost vaší WF4 je řádově rychleji a má být porovnána na logaritmickém měřítku.

### <a name="memory"></a>Paměť
 Nároky na paměť Windows Workflow Foundation se měří v dvě klíčové oblasti: pracovní postup složitost a počet definice pracovního postupu.  Měření paměti byly provedeny na pracovní stanici, 64bitová verze Windows 7.  Existuje mnoho způsobů, jak získat měření velikost pracovní sady například monitorování čítače výkonu, dotazování Environment.WorkingSet nebo pomocí některého nástroje, například VMMap dostupné z [VMMap](https://technet.microsoft.com/sysinternals/dd535533.aspx). Kombinace metod byla použita pro získání a ověřit výsledky jednotlivých testů.

### <a name="workflow-complexity-test"></a>Test složitost pracovního postupu
 Pracovní postup složitost zkušební měření pracovní sada rozdíl podle složitosti pracovního postupu.  Kromě komplexní pracovní postupy používají v předchozí části, se přidají nové variace pro dvě základní případy: jedna aktivita pracovního postupu a pořadí s aktivitami 1000.  Pro tyto testy jsou pracovní postupy inicializován a provést do dokončení jedinou smyčku sériového portu po dobu jedné minuty.  Variace každý test běží třikrát a data zaznamenaná průměr těchto tří spuštění.

 Dvě nové základní testy mají pracovní postupy, které vypadají jako ty, jak vidíte níže:

 ![Komplexní pracovní postupy](../../../docs/framework/windows-workflow-foundation/media/complexworkflowboth.gif "ComplexWorkflowBoth")

 V pracovním postupu WF3 uvedené výše, prázdná <xref:System.Workflow.Activities.CodeActivity> aktivity se používají.  Pracovní postup WF4 výše používá `Comment` aktivity.  `Comment` Aktivity byl popsaný v části porovnání výkonu úrovni součástí výše v tomto článku.

 ![Graf využití paměti](../../../docs/framework/windows-workflow-foundation/media/complexmemoryusage.gif "ComplexMemoryUsage")

 Jedním z vymazat trendy a Všimněte si v tomto grafu je, že vnoření má poměrně minimální dopad na využití paměti v WF3 a WF4.  Nejvýraznější dopad paměti pochází z počet aktivit v daném pracovním postupu.  Zadaný data z pořadí 1000, komplexní hloubky 5 pořadí 5 a komplexní hloubky 7 pořadí 1 variace, je jasné, že počet aktivit v tisíců, zvýšení využití paměti bude snadněji postřehnutelné.  V případě extreme (hloubky 7 pořadí 1) Pokud jsou aktivity K ~ 29, WF4 používá téměř 79 % méně paměti, než je WF3.

### <a name="multiple-workflow-definitions-test"></a>Více testů definice pracovního postupu
 Měření paměti na definice pracovního postupu je rozdělena na dva různé testy z důvodu dostupné možnosti pro hostování pracovních postupů v WF3 a WF4.  Daný pracovní postup je instance a provede pouze jednou za definici jiným způsobem než pracovní postup test složitost spuštění testů.  Je to proto, že definice pracovního postupu a jeho hostitelem zůstanou v paměti dobu životnosti domény aplikace.  Paměť používanou spuštěnou instanci dané pracovní postup by měla být vyčištěna během uvolňování paměti.  Pokyny k migraci pro WF4 obsahuje podrobné informace o možnosti hostování. Další informace najdete v tématu [kuchařka pro migraci WF: hostování pracovního postupu](https://go.microsoft.com/fwlink/?LinkID=153313).

 Vytvoření mnoha definice pracovního postupu pro definici pracovního postupu testu můžete udělat několika způsoby.  Například jeden použít generování kódu pro vytvoření sady 1000 pracovních postupů, které jsou identické, s výjimkou v názvu a každá z těchto pracovních postupů uložit do samostatných souborů.  Tento přístup byla získána pro test hostované v konzole.  V WF3 <xref:System.Workflow.Runtime.WorkflowRuntime> třídy byl použit ke spuštění definice pracovního postupu.  Můžete použít WF4 <xref:System.Activities.WorkflowApplication> k vytvoření instance jednoho pracovního postupu nebo přímo <xref:System.Activities.WorkflowInvoker> ke spuštění aktivity, jako by šlo volání metody.  <xref:System.Activities.WorkflowApplication> je hostitel instance jednoho pracovního postupu a má blíže paritu funkcí pro <xref:System.Workflow.Runtime.WorkflowRuntime> tak, aby byl použit v tomto testu.

 Při hostování pracovních postupů ve službě IIS je možné použít <xref:System.Web.Hosting.VirtualPathProvider> k vytvoření nového <xref:System.ServiceModel.WorkflowServiceHost> místo aby generovala všechny soubory XAMLX nebo XOML.  <xref:System.Web.Hosting.VirtualPathProvider> Zpracuje příchozí požadavek a odpověď vrátí "virtuální soubor", který lze načíst z databáze nebo, v tomto případě vygenerované v reálném čase.  Proto není nutné vytvořit 1000 fyzické soubory.

 Definice pracovního postupu používá v testovací konzole se jednoduchý sekvenční pracovní postupy s jednou aktivitou.  Jedna aktivita byla prázdná <xref:System.Workflow.Activities.CodeActivity> pro případ WF3 a `Comment` aktivita WF4 případu.  Případ hostované službou IIS použít pracovní postupy, které začínají na příjem zprávy a končí odeslání odpovědi:

 ![Služby pracovních postupů v WF3 a WF4](../../../docs/framework/windows-workflow-foundation/media/receiveworkflowboth.gif "ReceiveWorkflowBoth")

 Obrázek 4 – pracovní postup WF3 s ReceiveActivity a WF4 pracovního postupu pomocí vzoru žádostí a odpovědí

 Následující tabulka ukazuje rozdíly v pracovní sadě mezi definici jednoho pracovního postupu a 1001 definice:

|Možnosti hostování|WF3 Rozdíl pracovní sady|WF4 Rozdíl pracovní sady|
|---------------------|---------------------------|---------------------------|
|Konzolová aplikace hostovaných pracovních postupů|18 MB|9 MB|
|Služby pracovních postupů, hostovaná IIS|446 MB|364 MB|

 Hostování definice pracovního postupu ve službě IIS spotřebovává víc paměti z důvodu <xref:System.ServiceModel.WorkflowServiceHost>, podrobné artefaktů služby WCF a zpracovává logiku spojovanou s hostitelem zprávy.

 Pro konzolu hostování pracovních postupů v WF3 byly implementovány v kódu namísto XOML.  Výchozí hodnota je použití XAML v WF4.  XAML je uložen jako vložený prostředek v sestavení a zkompilován za běhu k poskytování provádění pracovního postupu.  Není k dispozici režijní náklady spojené s tímto procesem.  Aby bylo možné provést porovnání WF3 a WF4, programové pracovních postupů používaly místo XAML.  Níže je uveden příklad jednoho z pracovních postupů WF4:

```
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

 Existuje mnoho dalších faktorů, které můžou ovlivnit využití paměti. Stále platí stejné pokyny pro všechny spravované aplikace.  V prostředí hostované službou IIS <xref:System.ServiceModel.WorkflowServiceHost> zůstane objekt vytvořený pro definici pracovního postupu v paměti, dokud se fond aplikací recykluje.  To by měl zachovaná v paměti, při psaní rozšíření.  Je také vhodné vyhnout "globální" proměnné (proměnné s rozsahem celého pracovního postupu) a omezit její obor proměnné, kdykoli je to možné.

## <a name="workflow-runtime-services"></a>Služby modulu Runtime pracovního postupu

### <a name="persistence"></a>Trvalost
 WF3 a WF4 obě dodání pomocí poskytovatele trvalosti SQL.  Poskytovatel trvalého WF3 SQL je jednoduché implementace, který serializuje instance pracovního postupu a uloží je do objektu BLOB.  Z tohoto důvodu výkonu tohoto zprostředkovatele silně závisí na velikosti instance pracovního postupu.  V WF3 může zvýšit velikost instance celé řady důvodů, jak je popsáno dříve v tomto dokumentu.  Mnozí zákazníci zvolit nepoužívání výchozího poskytovatele trvalosti SQL, protože ukládání serializovanou instanci databáze poskytuje žádné přehled o stavu pracovního postupu.  Aby bylo možné najít určitý pracovní postup bez znalosti id pracovního postupu, jeden musel deserializovat každou trvalou instanci a zkontrolovat obsah.  Mnoho vývojářů chtít napsat vlastní trvalost poskytovatele překonat tuto překážku.

 Poskytovatel trvalého WF4 SQL má pokusili vyřešit některé z těchto úkonů.  Trvalost tabulky vystavit určité informace, jako je active záložek a možné zařazení vlastnosti.  Nové funkce založené na obsahu korelace v WF4 nebude provádět i pomocí trvalosti přístup WF3 SQL, které je řízené některé změny v organizaci trvalými instancemi pracovního postupu.  To usnadňuje práci poskytovatele trvalého chování s mnohem složitější a vloží další zátěže v databázi.

### <a name="environment-setup"></a>Nastavení prostředí
 ![Pracovní postup prostředí pro testování výkonu](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")

### <a name="test-setup"></a>Nastavení testu
 Ještě se sada vylepšení funkcí a lepší souběžnosti zpracování je vyšší než poskytovatele v WF3 poskytovatele trvalosti SQL v WF4.  K prezentaci to, jsou porovnány dva pracovní postupy, které provádějí v podstatě stejné operace v WF3 a WF4 níže.

 ![Pracovní postupy pro trvalost](../../../docs/framework/windows-workflow-foundation/media/persistworkflow.gif "PersistWorkflow")

 Obrázek 5 – trvalost pracovního postupu v WF3 na vlevo a vpravo WF4

 Dva pracovní postupy jsou obě vytvořené přijaté zprávy.  Po odeslání odpovědi na počáteční, je trvalá pracovního postupu.  V případě WF3 prázdnou <xref:System.Workflow.ComponentModel.TransactionScopeActivity> slouží k zahájení stálost.  Stejné lze dosáhnout v WF3 označením aktivitu jako "zachovat na Zavřít."  Druhý, korelační zpráva nedokončí pracovního postupu.  Pracovní postupy jsou trvalé, ale není byla uvolněna.

### <a name="test-results"></a>Výsledky testů
 ![Trvalost propustnost](../../../docs/framework/windows-workflow-foundation/media/throughputpersistence.gif "ThroughputPersistence")

 Při přenosu mezi klientem a střední vrstvy, je HTTP, ukazuje přetrvání WF4 zlepšení 2.6 dob.  Přenos TCP zvyšuje faktor 3.0 časech.  Ve všech případech je využití procesoru ve střední vrstvě 98 % nebo vyšší.  Z důvodu, že je větší propustnost WF4 je z důvodu rychlejší modulu runtime pracovního postupu.  Velikost serializované instanci je nízká pro oba případy a není elementem hlavní přispívající v této situaci.

 WF3 i WF4 pracovní postupy v tomto testu pomocí aktivity explicitně o tom, kdy by mělo dojít k trvalosti.  To má výhodu uchování pracovního postupu bez uvolnění ho.  V WF3, je také možné zachovat pomocí <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> funkce, ale uvolní instanci pracovního postupu z paměti.  Pokud vývojář pomocí WF3 chce zajistit, aby že pracovní postup se opakuje v určitých bodech, buď musí změnit definice pracovního postupu ani platit náklady pro uvolnění a opětovné načtení instance pracovního postupu.  Nová funkce v WF4 díky tomu je možné zachovat bez uvolnění: <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>.  Tato funkce umožňuje nastavit jako trvalý v nečinnosti, ale zůstanou v paměti do instance pracovního postupu <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> při dosažení prahové hodnoty nebo spouštění se obnoví.

 Všimněte si, že poskytovatele trvalého chování WF4 SQL provede další práci na úrovni databáze.  Databáze SQL se může stát kritickým bodem, proto je důležité monitorovat využití procesoru a disku existuje.  Nezapomeňte uvést následující čítače výkonu z SQL database při testování aplikací pracovních postupů výkonu:

-   Fyzický disk\\doba čtení disku v %

-   Fyzický disk\\% času disku

-   Fyzický disk\\čas zápisu disku v %

-   Fyzický disk\\průměrný % Délka fronty disku

-   PhysicalDisk\Avg. Délka fronty disku pro čtení

-   PhysicalDisk\Avg. Délka fronty disku zápisu

-   Délka fronty disku PhysicalDisk\Current

-   Informace o procesoru\\čas procesoru v %

-   Doba čekání západky překročila SQLServer:Latches\Average (ms)

-   SQLServer:Latches\Latch čekání za sekundu

### <a name="tracking"></a>Sledování
 Sledování pracovního postupu je možné sledovat průběh pracovního postupu.  Informace, které je součástí událostí sledování je určen v rámci profilu sledování.  Složitější profilu sledování dražší sledování se změní.

 WF3 odeslaná službou sledování na základě SQL.  Tato služba může fungovat v režimech dávkové a dávce.  V režim sledování události se zapisují přímo do databáze.  Sledování události se shromažďují do stejné dávky jako stav instance pracovního postupu, v dávkové režimu.  Dávkový režim má nejlepšího výkonu pro širokou škálu návrhů pracovního postupu.  Dávkování však může mít dopad na výkon negativní pokud pracovní postup probíhá bez zachování řada aktivit a tyto aktivity jsou sledovány.  To by stávat ve smyčkách a nejlepší způsob, jak se vyhnout této situaci je návrh velké smyčky tak, aby obsahovala bod trvalosti.  Úvod do trvalého bod do smyčky může negativně ovlivnit výkon stejně, proto je důležité pro měření náklady na každého a najít rovnováhu.

 WF4 není součástí SQL služby sledování.  Záznam sledování informací do databáze SQL může být lépe zpracovává z aplikačního serveru spíše než integrované do [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Proto sledování SQL je nyní zpracovat AppFabric.  Poskytovatel sledování out-of-the-box v WF4 je založena na trasování událostí pro Windows (ETW).

 Trasování událostí pro Windows je systém událostí na úrovni jádra, s nízkou latencí integrovaný do Windows.  Používá model poskytovatele/konzumenta, který umožňuje pouze účtovat penalizace pro trasování událostí, když je ve skutečnosti příjemce.  Kromě události jádra například procesoru, disku, paměti a využití sítě mnoho aplikací také využívat trasování událostí pro Windows.  Události trasování událostí pro Windows jsou výkonnější než čítače výkonu, události lze přizpůsobit, aby aplikace.  Události může obsahovat text, například ID pracovního postupu nebo informační zpráva.  Také události jsou uspořádané do kategorií pomocí bitovými maskami tak, aby využívání podmnožinu událostí bude mít menší dopad na výkon než zachytávání všechny události.

 K přístupu pomocí trasování událostí pro Windows pro sledování místo SQL k výhodám patří:

-   Kolekce sledování událostí je možné oddělit na jiný proces.  To poskytuje větší flexibilitu v tom, jak jsou zaznamenány události.

-   Události trasování událostí pro Windows Sledování snadno spolu se události trasování událostí pro Windows WCF nebo jiné poskytovatele trasování událostí pro Windows, např. zprostředkovatele SQL Server nebo jádra.

-   Autoři pracovního postupu není nutné změnit pracovní postup fungovat lépe u konkrétní sledování provádění, jako je například služba sledování WF3 SQL dávkovém režimu.

-   Správce může zapnout sledování nebo vypnout bez recyklace hostitelský proces.

 Nevýhodou jsou dostupné výhody výkonu pro sledování trasování událostí pro Windows.  Události trasování událostí pro Windows může dojít ke ztrátě, pokud je systém náročnými prostředků tím snižuje jejich přetížení.  Zpracování události není určena k bloku vykonávání programu normální a proto není zaručeno, že všechny události trasování událostí pro Windows se bude vysílat jejich odběratelům.  Díky tomu trasování událostí pro Windows Sledování skvěle hodí k monitorování stavu, ale není vhodný pro auditování.

 Zatímco WF4 nemá zprostředkovatele SQL sledování, nemá AppFabric.  Postup sledování AppFabric SQL je přihlášení k odběru událostí trasování událostí pro Windows pomocí služby Windows, která seskupuje události do dávek a zapisuje je do tabulky SQL navržený pro rychlé vkládání.  Samostatná úloha se vyprázdní data z této tabulky a reforms do tabulky, které lze zobrazit na řídicím panelu AppFabric sestav.  To znamená, že zpracovává nezávisle na pracovní postup pochází a proto nebude muset čekat na stálost bod zaznamenávány dávku sledování událostí.

 Pomocí nástrojů, jako je logman nebo xperf lze zaznamenat události trasování událostí pro Windows.  Komprimovat soubor ETL můžete zobrazit pomocí některého nástroje, například xperfview nebo převést na přehlednějším tvaru, jako jsou XML, s tracerpt.  V WF3 je jedinou možností, jak získat sledování událostí bez databáze SQL k vytvoření vlastní sledování služby. Další informace o trasování událostí pro Windows najdete v tématu [služby WCF a události trasování pro Windows](../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) a [události trasování pro Windows](https://msdn.microsoft.com/library/ff190903.aspx\)).

 Povolení pracovního postupu pro sledování bude mít vliv na výkon v různých úrovních.  Níže srovnávacích testů pomocí nástroje logman využívat trasování událostí pro Windows Sledování událostí a zapisuje je do souboru ETL.  Náklady na SQL sledování v AppFabric není v rámci tohoto článku.  Základní sledování profil, používá se také v AppFabric, se zobrazí v tomto testu výkonnosti.  Obsahuje taky jsou náklady pouze událostech monitorování stavu sledování.  Tyto události jsou užitečné při řešení potíží a určení průměrná propustnost systému.

### <a name="environment-setup"></a>Nastavení prostředí
 ![Pracovní postup prostředí pro testování výkonu](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")

### <a name="test-results"></a>Výsledky testů
 ![Pracovní postup sledování nákladů](../../../docs/framework/windows-workflow-foundation/media/workflowtracingcost.gif "WorkflowTracingCost")

 Monitorování stavu zhruba má 3 % dopad na propustnost.  Náklady na základní profil je přibližně 8 %.

## <a name="interop"></a>Zprostředkovatel komunikace s objekty
 WF4 je téměř dokončena přepisování [!INCLUDE[wf1](../../../includes/wf1-md.md)] a proto nejsou přímo kompatibilní s WF4 WF3 pracovních postupů a aktivit.  Mnoho zákazníků, které již v rané fázi přijetím modelu Windows Workflow Foundation, bude mít pro WF3 třetí strany ani interní definice pracovního postupu a vlastní aktivity.  Jedním ze způsobů pro usnadnění přechodu na WF4 je použití aktivity spolupráce, který můžete spustit WF3 aktivitám v pracovním postupu WF4.  Dále je doporučeno <xref:System.Activities.Statements.Interop> aktivity použít pouze v případě potřeby. Další informace o migraci na WF4 podívejte [pokyny k migraci WF4](https://go.microsoft.com/fwlink/?LinkID=153313).

### <a name="environment-setup"></a>Nastavení prostředí
 ![Pracovní postup prostředí pro testování výkonu](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")

### <a name="test-results"></a>Výsledky testů
 Následující tabulka ukazuje výsledky spuštění pracovního postupu obsahuje pět aktivit v sekvenci v různých konfiguracích.

|Test|Propustnost (pracovní postupy za sekundu)|
|----------|-----------------------------------|
|Pořadí WF3 WF3 runtime|1,576|
|Pořadí WF3 v modulu runtime WF4 pomocí zprostředkovatele komunikace|2,745|
|WF4 pořadí|153,582|

 Se zvýší významné výkonu pomocí zprostředkovatele komunikace přes přímé WF3.  Při porovnání proti WF4 aktivity, zvýšení ale zanedbatelné.

## <a name="summary"></a>Souhrn
 Rozsáhlé investice výkonu pro WF4 zaplatily v mnoha oblastech zásadní význam.  Výkon součásti jednotlivé pracovní postup je v některých případech stovky rychlejší v WF4 ve srovnání s WF3 kvůli štíhlejší [!INCLUDE[wf1](../../../includes/wf1-md.md)] modulu runtime.  Latence jsou výrazně lepší také.  To znamená snížení výkonu v důsledku použití [!INCLUDE[wf1](../../../includes/wf1-md.md)] na rozdíl od ručního kódování Orchestrace WCF je velmi malý, zvažujete přidání výhody používání služby [!INCLUDE[wf1](../../../includes/wf1-md.md)].  Trvalost výkonu se zvýšila faktor 2.5 3.0.  Monitorování stavu pomocí pracovního postupu pro sledování teď má velmi nízkou režií.  Jsou k dispozici pro ty, které zvažují přechod ze WF3 na WF4 komplexní sadu příručkách pro migraci.  To vše třeba WF4 atraktivní volba pro psaní komplexních aplikací.

## <a name="acknowledgements"></a>Potvrzení
 Mnoho díky následujícím přispěvatelů a recenzenty pro své úsilí:

-   Leon Welicki, Microsoft Corporation

-   Ryszard Kwiecinski, Microsoft Corporation.

-   Emil Velinov, Microsoft Corporation

-   Tomáš Talbert, Microsoft Corporation

-   Bob Schmidt, Microsoft Corporation

-   Stefan Batres, Microsoft Corporation
