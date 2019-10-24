---
title: Výkon Windows Workflow Foundation 4
ms.date: 03/30/2017
ms.assetid: 67d2b3e8-3777-49f8-9084-abbb33b5a766
ms.openlocfilehash: c656d1e23c7314cfd7b772faef842296d03e4af1
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "70989586"
---
# <a name="windows-workflow-foundation-4-performance"></a>Výkon Windows Workflow Foundation 4

 Microsoft [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] obsahuje zásadní revizi programovací model Windows Workflow Foundation (WF) s vysokými investicemi do výkonu.  Tato nová revize přináší významné změny návrhu z předchozích verzí [!INCLUDE[wf1](../../../includes/wf1-md.md)], které byly dodány jako součást .NET Framework 3,0 a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Byl znovu navržený z jádra programovacího modelu, modulu runtime a nástrojů, aby významně vylepšil výkon a použitelnost. Toto téma ukazuje důležité charakteristiky výkonu těchto revizí a porovnává je s předchozími verzemi.

 Výkon součásti jednotlivého pracovního postupu se zvýšil o objednávky podle velikosti mezi WF3 a WF4.  To znamená, že mezera mezi ručně kódovanými službami Windows Communication Foundation (WCF) a službami pracovního postupu WCF budou poměrně malé.  Latence pracovního postupu se výrazně snížila v WF4.  Výkon trvalosti se zvýšil o faktor 2,5-3,0.  Sledování stavu prostřednictvím sledování pracovního postupu má výrazně menší nároky na režii.  Jedná se o přesvědčivé důvody k migraci na nebo přijetí WF4 ve vašich aplikacích.

## <a name="terminology"></a>Terminologie
 Verze [!INCLUDE[wf1](../../../includes/wf1-md.md)] představená v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] bude pro zbytek tohoto tématu označovat jako WF4.  [!INCLUDE[wf1](../../../includes/wf1-md.md)] byla představena v rozhraní .NET 3,0 a měla několik menších revizí prostřednictvím [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] SP1. Verze [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Workflow Foundation bude pro zbytek tohoto tématu označovat jako WF3. WF3 se dodává v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] vedle sebe s WF4. Další informace o migraci artefaktů WF3 do WF4 najdete v tématu [Průvodce migrací programovací model Windows Workflow Foundation 4](https://go.microsoft.com/fwlink/?LinkID=153313) .

 Windows Communication Foundation (WCF) je jednotný programovací model Microsoftu pro vytváření aplikací orientovaných na služby. Byl nejprve představen jako součást .NET 3,0 společně s WF3 a teď je jednou z klíčových součástí .NET Framework.

 Windows Server AppFabric je sada integrovaných technologií, které usnadňují vytváření, škálování a správu webových a složených aplikací, které běží na službě IIS. Poskytuje nástroje pro monitorování a správu služeb a pracovních postupů. Další informace najdete v tématu [Windows Server AppFabric 1,0](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)).

## <a name="goals"></a>Hlavních
 Cílem tohoto tématu je Ukázat výkonnostní charakteristiky WF4 s daty měřenými pro různé scénáře. Poskytuje také podrobná porovnání mezi WF4 a WF3, a proto zobrazuje Skvělé vylepšení, která byla provedena v této nové revizi. Scénáře a data uvedená v tomto článku kvantifikují základní náklady na různé aspekty WF4 a WF3. Tato data jsou užitečná v seznámení s výkonnostními charakteristikami WF4 a mohou být užitečné při plánování migrace z WF3 na WF4 nebo použití WF4 při vývoji aplikací. Doporučuje se však vzít v potaz závěry z dat uvedených v tomto článku. Výkon aplikace kompozitního pracovního postupu je vysoce závislý na způsobu implementace pracovního postupu a způsobu integrace různých součástí. Jeden musí měřit jednotlivé aplikace, aby bylo možné určit výkonnostní charakteristiky této aplikace.

## <a name="overview-of-wf4-performance-enhancements"></a>Přehled vylepšení výkonu WF4
 WF4 bylo pečlivě navrženo a implementováno s vysokým výkonem a škálovatelností, které jsou popsány v následujících částech.

### <a name="wf-runtime"></a>Modul runtime WF
 V jádru modulu [!INCLUDE[wf1](../../../includes/wf1-md.md)] runtime je asynchronní Plánovač, který řídí provádění aktivit v pracovním postupu. Poskytuje výkonné a předvídatelné prováděcí prostředí pro aktivity. Prostředí má dobře definovaný kontrakt pro provádění, pokračování, dokončení, zrušení, výjimky a předvídatelný model vláken.

 V porovnání s WF3 má modul runtime WF4 efektivnější Plánovač. Využívá stejný fond vstupně-výstupních vláken, který se používá pro WCF, což je velmi efektivní při provádění dávkových pracovních položek. Fronta interních pracovních položek je optimalizována pro nejběžnější vzorce použití. Běhový modul WF4 také spravuje stavy spouštění velmi nenáročným způsobem s minimální synchronizací a logikou zpracování událostí, zatímco WF3 závisí na vysoké registraci událostí a voláních, aby prováděla komplexní synchronizaci pro přechody stavu.

### <a name="data-storage-and-flow"></a>Úložiště a tok dat
 V WF3 jsou data přidružená k aktivitě modelována prostřednictvím vlastností závislosti implementovaných <xref:System.Windows.DependencyProperty>m typu. Vzor vlastnosti závislosti byl představen v Windows Presentation Foundation (WPF). Obecně platí, že tento model je velmi flexibilní pro podporu jednoduchých datových vazeb a dalších funkcí uživatelského rozhraní. Vzor však vyžaduje, aby byly vlastnosti definovány jako statická pole v definici pracovního postupu. Pokaždé, když modul runtime [!INCLUDE[wf1](../../../includes/wf1-md.md)] nastaví nebo Získá hodnoty vlastností, zahrnuje silně váženou logiku vyhledávání.

 WF4 používá k výraznému zlepšení způsobu zpracování dat v pracovním postupu pomocí logiky nejasného rozsahu dat. Odděluje data uložená v aktivitě z dat, která se přenášejí přes hranice aktivity pomocí dvou různých konceptů: proměnné a argumenty. Při použití jasného hierarchického rozsahu pro proměnné a argumenty "in/out/InOut" jsou složitost využití dat pro aktivity výrazně snížena a životnost dat je také automaticky vymezena. Aktivity mají jasně definovaný podpis, který popisuje jeho argumenty. Pouhým zkontrolováním aktivity můžete určit, jaká data očekává, a jaká data budou vytvořená v důsledku jejího spuštění.

 V aktivitách WF3 byly inicializovány při vytvoření pracovního postupu. V aktivitách WF 4 jsou inicializovány pouze v případě, že jsou spuštěny odpovídající aktivity. To umožňuje jednodušší životní cyklus aktivity bez provádění operací inicializace/zrušení inicializace při vytvoření nové instance pracovního postupu, a proto dosáhl vyšší efektivity.

### <a name="control-flow"></a>Tok řízení
 Stejně jako v libovolném programovacím jazyce poskytuje [!INCLUDE[wf1](../../../includes/wf1-md.md)] podporu pro kontrolní toky pro definice pracovních postupů tím, že zavádí sadu aktivit toku řízení pro sekvencování, cykly, větvení a jiné vzory. Pokud se v WF3 musí znovu spustit stejná aktivita, vytvoří se nový <xref:System.Workflow.ComponentModel.ActivityExecutionContext> a aktivita se naklonuje pomocí vysoké logiky serializace a deserializace na základě <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Výkon iterativních řídicích toků je obvykle mnohem pomalejší než provádění posloupnosti aktivit.

 WF4 to velmi jinak. Provede šablonu aktivity, vytvoří nový objekt vlastnosti ActivityInstance. a přidá ho do fronty plánovače. Tento celý proces zahrnuje jenom explicitní vytváření objektů a je velmi odlehčený.

### <a name="asynchronous-programming"></a>Asynchronní programování
 Aplikace obvykle mají lepší výkon a škálovatelnost s asynchronním programováním pro dlouhotrvající operace blokujících operací, jako jsou vstupně-výstupní operace nebo distribuované výpočetní operace. WF4 poskytuje asynchronní podporu prostřednictvím základních typů aktivit <xref:System.Activities.AsyncCodeActivity>, <xref:System.Activities.AsyncCodeActivity%601>. Modul runtime nativně rozumí asynchronním aktivitám a proto může automaticky vložit instanci do zóny bez trvalého uložení, zatímco asynchronní práce je nedokončená. Vlastní aktivity mohou odvozovat z těchto typů, aby prováděly asynchronní práci bez podržení vlákna plánovače pracovních postupů a blokování všech aktivit, které mohou být schopny běžet paralelně.

### <a name="messaging"></a>Messaging
 Zpočátku WF3 mít velmi omezené podpory pro zasílání zpráv prostřednictvím externích událostí nebo volání webových služeb. V .NET 3,5 můžete pracovní postupy implementovat jako klienty WCF nebo zveřejnit jako služby WCF prostřednictvím <xref:System.Workflow.Activities.SendActivity> a <xref:System.Workflow.Activities.ReceiveActivity>. V WF4 byl koncept programování zasílání zpráv na základě pracovního postupu dále posílen díky těsné integraci logiky zasílání zpráv WCF do WF.

 Jednotný kanál zpracování zpráv poskytovaný v technologii WCF v rozhraní .NET 4 pomáhá službám WF4 významně zlepšit výkon a škálovatelnost než WF3. WF4 také poskytuje bohatou podporu programování pro zasílání zpráv, která může modelovat složité vzory výměny zpráv (MEPs). Vývojáři mohou použít buď typové smlouvy o poskytování služeb, aby bylo dosaženo lepšího výkonu, aniž by bylo nutné platit náklady na serializaci. Podpora ukládání do mezipaměti kanálu na straně klienta prostřednictvím třídy <xref:System.ServiceModel.Activities.SendMessageChannelCache> v WF4 pomáhá vývojářům vytvářet rychlé aplikace s minimálním úsilím. Další informace najdete v tématu [Změna úrovní sdílení mezipaměti pro aktivity odeslat](../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).

### <a name="declarative-programming"></a>Deklarativní programování
 WF4 poskytuje čistou a jednoduchou deklarativní programovací architekturu pro modelování obchodních procesů a služeb. Programovací model podporuje plně deklarativní složení aktivit bez jakýchkoli kódů, což výrazně zjednodušuje vytváření pracovních postupů. V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] byla deklarativní programovací architektura založená na jazyce XAML sjednocena do jediného sestavení System. XAML. dll pro podporu WPF i WF.

 V WF4 poskytuje XAML skutečně deklarativní prostředí a umožňuje definovat celou definici pracovního postupu v kódu XML, odkazování na aktivity a typy sestavené pomocí .NET. To bylo obtížné dělat v WF3 s formátem XOML bez zahrnutí vlastní logiky kódu na pozadí. Nový zásobník XAML v rozhraní .NET 4 má mnohem lepší výkon při serializaci nebo deserializaci artefaktů pracovního postupu a deklarativní programování je přitažlivé a plné.

### <a name="workflow-designer"></a>Návrhář postupu provádění
 Plně deklarativní Podpora programování pro WF4 explicitně ukládá vyšší požadavky na výkon při návrhu velkých pracovních postupů. Návrhář pracovního postupu v WF4 má mnohem lepší škálovatelnost pro velké pracovní postupy, než je to pro WF3. Díky podpoře virtualizace uživatelského rozhraní může Návrhář snadno načíst velký pracovní postup 1000 aktivit během několika sekund, zatímco je téměř nemožné načíst pracovní postup s několika stovkami aktivit pomocí návrháře WF3.

## <a name="component-level-performance-comparisons"></a>Porovnání výkonu na úrovni součásti
 Tato část obsahuje data o přímých porovnáních mezi jednotlivými aktivitami v pracovních postupech WF3 a WF4.  Klíčové oblasti, jako je trvalost, mají větší dopad na výkon než jednotlivé součásti aktivity.  Zlepšení výkonu v jednotlivých součástech v WF4 je důležité, i když jsou tyto komponenty teď dostatečně rychlé, aby je bylo možné porovnat s ručními kódovanými logikami orchestrace.  Příklad, který je popsaný v následující části: "scénář kompozice služeb".

### <a name="environment-setup"></a>Nastavení prostředí
 ![Nastavení prostředí pro měření výkonu pracovního postupu](./media/performance/performance-test-environment.gif)

 Výše uvedený obrázek ukazuje konfiguraci počítače, která se používá pro měření výkonu na úrovni součásti. Jeden server a pět klientů připojených přes jedno síťové rozhraní sítě Ethernet s rychlostí 1 GB/s. Pro snazší měření je server nakonfigurovaný tak, aby používal jeden jádro serveru s duálním nebo čtyřjádrovým jádrem, na kterém běží Windows Server 2008 x86. Využití CPU systému je udržováno téměř 100%.

### <a name="test-details"></a>Podrobnosti testu
 @No__t_0 WF3 je pravděpodobně nejjednodušší aktivita, kterou lze použít v pracovním postupu WF3.  Aktivita volá metodu v kódu, na kterou programátor pracovního postupu může vložit vlastní kód do.  V WF4 neexistuje žádný přímý analogový WF3 <xref:System.Workflow.Activities.CodeActivity>, která poskytuje stejné funkce.  Všimněte si, že v WF4 je základní třída <xref:System.Activities.CodeActivity>, která nesouvisí s <xref:System.Workflow.Activities.CodeActivity> WF3.  Autoři pracovního postupu jsou doporučováni k vytváření vlastních aktivit a vytváření pracovních postupů pouze v jazyce XAML.  V testech níže se jako místo prázdného <xref:System.Workflow.Activities.CodeActivity> v pracovních postupech WF4 používá aktivita s názvem `Comment`.  Kód v `Comment` aktivitě je následující:

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
 Pracovní postup je sekvenční pracovní postup obsahující jednu podřízenou aktivitu.  Aktivita je <xref:System.Workflow.Activities.CodeActivity> bez kódu v případu WF3 a aktivita `Comment` v případě případu WF4.

### <a name="while-with-1000-iterations"></a>I když s 1000 iteracemi
 Pracovní postup sekvence obsahuje jednu aktivitu <xref:System.Activities.Statements.While> s jednou podřízenou aktivitou ve smyčce, která neprovádí žádnou práci.

### <a name="replicator-compared-to-parallelforeach"></a>Replikátor ve srovnání s ParallelForEach
 <xref:System.Workflow.Activities.ReplicatorActivity> v WF3 má sekvenční a paralelní režimy spuštění.  V sekvenčním režimu je výkon aktivity podobný <xref:System.Workflow.Activities.WhileActivity>.  @No__t_0 je nejužitečnější pro paralelní spouštění.  WF4 analogová pro toto je aktivita <xref:System.Activities.Statements.ParallelForEach%601>.

 Následující diagram znázorňuje pracovní postupy použité pro tento test. Pracovní postup WF3 je na levé straně a pracovní postup WF4 je na pravé straně.

 ![WF3 Aktivita ReplicatorActivity a WF4 ParallelForEach](./media/performance/replicator-parallel-wf3-wf4.gif)

### <a name="sequential-workflow-with-five-activities"></a>Sekvenční pracovní postup s pěti aktivitami
 Tento test je určen k zobrazení efektu, který provede několik aktivit v pořadí.  V sekvenci je pět aktivit.

### <a name="transaction-scope"></a>Obor transakce
 Test rozsahu transakce se mírně liší od ostatních testů v tom, že nová instance pracovního postupu není vytvořena pro každou iteraci.  Místo toho je pracovní postup strukturován pomocí smyčky while obsahující <xref:System.Activities.Statements.TransactionScope> aktivity obsahující jednu aktivitu, která nefunguje.  Každé spuštění dávky 50 iterací prostřednictvím smyčky while se počítá jako jediná operace.

### <a name="compensation"></a>Kompenzace
 Pracovní postup WF3 má jednu aktivitu Aktivita nadřazená s názvem `WorkScope`.  Aktivita jednoduše implementuje rozhraní <xref:System.Workflow.ComponentModel.ICompensatableActivity>:

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

 Obslužná rutina chyb cílí na aktivitu `WorkScope`. Pracovní postup WF4 je rovnoměrně zjednodušený.  @No__t_0 má tělo a obslužnou rutinu kompenzace.  Explicitní kompenzace je v posloupnosti další.  Aktivita aktivity těla a obslužné rutiny kompenzace jsou prázdné implementace:

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

Následující diagram znázorňuje základní pracovní postup kompenzace. Pracovní postup WF3 je na levé straně a pracovní postup WF4 je na pravé straně.

![Pracovní postupy WF3 a WF4 Basic kompenzace](./media/performance/basic-compensation-workflows-wf3-wf4.gif)

### <a name="performance-test-results"></a>Výsledky testů výkonu

 ![Tabulka zobrazující data výsledků testu výkonu](./media/performance/performance-test-data.gif)

 ![Sloupcový graf, který porovnává data testu výkonu WF3 a WF4](./media/performance/performance-test-chart.gif)

 Všechny testy se měří v pracovních postupech za sekundu s výjimkou testu rozsahu transakce.  Jak je uvedeno výše, výkon [!INCLUDE[wf1](../../../includes/wf1-md.md)] runtime se zlepšil v rámci panelu, zejména v oblastech, které vyžadují více spuštění stejné aktivity, jako je smyčka while.

## <a name="service-composition-scenario"></a>Scénář složení služby
 Jak je uvedeno v předchozí části, "porovnání výkonu na úrovni komponenty", došlo k výraznému snížení režie mezi WF3 a WF4.  Služba WCF Workflow Services může nyní téměř odpovídat výkonu ručně kódovaných služeb WCF, ale stále přináší všechny výhody [!INCLUDE[wf1](../../../includes/wf1-md.md)] runtime.  Tento testovací scénář porovnává službu WCF se službou pracovního postupu WCF v WF4.

### <a name="online-store-service"></a>Služba Online Store
 Jednou z sílu programovací model Windows Workflow Foundation je schopnost vytvářet procesy pomocí několika služeb.  V tomto příkladu je k dispozici služba online úložiště, která orchestruje dvě volání služeb k nákupu objednávky.  Prvním krokem je ověření pořadí pomocí služby ověřování objednávky.  Druhým krokem je vyplnit objednávku pomocí služby skladu.

 Tyto dvě služby back-end, pořadí ověřování služby a služby skladu, zůstávají u obou testů stejné.  Součástí změny je služba online obchodu, která provádí orchestraci.  V jednom případě je služba rukou kódovaná jako služba WCF.  Pro druhý případ se služba zapisuje jako služba pracovního postupu WCF v WF4. pro tento test jsou vypnuté funkce specifické pro [!INCLUDE[wf1](../../../includes/wf1-md.md)], jako je sledování a trvalost.

### <a name="environment"></a>Prostředí
![Nastavení prostředí pro měření výkonu](./media/performance/performance-test-environment.gif)

 Požadavky klientů jsou převedené do služby Online Store prostřednictvím protokolu HTTP z více počítačů.  Jeden počítač hostuje všechny tři služby.  Přenosová vrstva mezi službou online úložiště a back-end službami je TCP nebo HTTP.  Měření operací za sekundu vychází z počtu dokončených `PurchaseOrder` volání do služby Online Storu.  Sdružování kanálů je nová funkce, která je k dispozici v WF4.  V části WCF tohoto sdružování testovacích kanálů není tato služba vydaná, takže se ve službě Online Store použila ruční kódovaná Implementace jednoduchého sdružování.

### <a name="performance"></a>Výkon
![Sloupcový graf zobrazující výkon služby Online Store](./media/performance/online-store-performance-graph.gif)

 Při připojení ke službám back-end TCP bez sdružování kanálů má služba [!INCLUDE[wf1](../../../includes/wf1-md.md)] k propustnosti 17,2% vliv.  Díky sdružování kanálů je penalizace o 23,8%.  V případě protokolu HTTP je dopad mnohem menší: 4,3% bez sdružování a 8,1% s fondem.  Je také důležité si uvědomit, že sdružování kanálů při použití HTTP nabízí velmi malou výhodu.

 I když existuje režie z WF4 runtime v porovnání s rukou kódované služby WCF v tomto testu, může být považována za nejhorší případ.  Tyto dvě back-end služby v tomto testu provede velmi málo práce.  V reálném čase by tyto služby prováděly dražší operace, jako jsou volání databáze, což vede k tomu, že vliv přenosové vrstvy na výkon je méně důležitý.  To navíc přináší výhody funkcí, které jsou k dispozici v WF4, díky tomu je pro vytváření služeb Orchestration Foundation vhodným způsobem.

## <a name="key-performance-considerations"></a>Klíčové požadavky na výkon
 Oblasti funkcí v této části, s výjimkou spolupráce, se výrazně změnily mezi WF3 a WF4.  To má vliv na návrh aplikací pracovních postupů i na výkon.

#### <a name="workflow-activation-latency"></a>Latence aktivace pracovního postupu
 V aplikaci služby pracovního postupu WCF je latence pro spuštění nového pracovního postupu nebo načítání existujícího pracovního postupu důležitá, protože může být blokování.  Tento testovací případ měří hostitele WF3 XOML proti hostiteli WF4 XAMLX v typickém scénáři.

##### <a name="environment-setup"></a>Nastavení prostředí
 ![Nastavení prostředí pro latenci a testy propustnosti](./media/performance/latency-throughput-environment-setup.gif)

##### <a name="test-setup"></a>Nastavení testu
 Ve scénáři klientský počítač kontaktuje službu pracovního postupu WCF pomocí korelace založené na kontextu.  Korelace kontextu vyžaduje speciální vazbu kontextu a používá hlavičku kontextu nebo soubor cookie k propojení zpráv se správnou instancí pracovního postupu.  Má přínos pro zvýšení výkonu v případě, že je v záhlaví zprávy umístěný identifikátor korelace, aby tělo zprávy nebylo nutné analyzovat.

 Služba vytvoří nový pracovní postup s požadavkem a pošle okamžitou odezvu tak, aby měření latence nezahrnovalo čas strávený spouštěním pracovního postupu.  Pracovní postup WF3 je souborem XOML s kódem na pozadí a pracovní postup WF4 je zcela XAML.  Pracovní postup WF4 vypadá takto:

 ![Pracovní postup oboru korelace WF4](./media/performance/wf4-correlationscope-workflow.gif)

 Aktivita <xref:System.ServiceModel.Activities.Receive> vytvoří instanci pracovního postupu.  Hodnota předaná v přijaté zprávě se zobrazí ve zprávě odpovědi.  Sekvence, která následuje po odpovědi, obsahuje zbytek pracovního postupu.  Ve výše uvedeném případě se zobrazí pouze jedna aktivita komentáře.  Počet aktivit komentářů se změnil, aby se simulovala složitost pracovního postupu.  Aktivita komentáře je ekvivalentní WF3 <xref:System.Workflow.Activities.CodeActivity>, která neprovede žádnou práci. Další informace o aktivitě komentářů naleznete v části porovnání výkonu na úrovni komponenty výše v tomto článku.

##### <a name="test-results"></a>Výsledky testů

 Latence a doba zahřívání pro služby pracovního postupu WCF:

 ![Sloupcový graf znázorňující latenci a latenci pro služby pracovního postupu WCF využívající WF3 a WF4](./media/performance/latency-results-graph.gif)

 V předchozím grafu se studenou odkazuje na případ, kdy pro daný pracovní postup neexistuje existující <xref:System.ServiceModel.WorkflowServiceHost>.  Jinými slovy, studená latence je při prvním použití pracovního postupu a soubor XOML nebo XAML musí být zkompilován.  Doba zahřívání je čas vytvoření nové instance pracovního postupu v případě, že byl typ pracovního postupu již zkompilován.  Složitost pracovního postupu způsobuje velmi malý rozdíl v WF4 případu, ale v případu WF3 má lineární průběh.

#### <a name="correlation-throughput"></a>Propustnost korelace
 WF4 zavádí novou funkci korelace založenou na obsahu.  WF3 poskytuje pouze korelaci na základě kontextu.  Korelace na základě kontextu by se dala provést jenom přes konkrétní vazby kanálu WCF.  ID pracovního postupu je vloženo do záhlaví zprávy při použití těchto vazeb.  Běhový modul WF3 mohl identifikovat pouze pracovní postup podle jeho ID.  V případě korelace na základě obsahu může autor pracovního postupu vytvořit korelační klíč ze relevantního data, jako je číslo účtu nebo ID zákazníka.

 Korelace založená na kontextu má výkonovou výhodu v tom, že korelační klíč je umístěný v záhlaví zprávy.  Klíč lze číst ze zprávy bez zrušení serializace/zprávy-kopírování.  V rámci korelace na základě obsahu je korelační klíč uložený v těle zprávy.  K vyhledání klíče se používá výraz XPath.  Náklady na toto dodatečné zpracování závisí na velikosti zprávy, hloubce klíče v těle a na počtu klíčů.  Tento test porovnává kontextovou a korelaci založenou na obsahu a také ukazuje snížení výkonu při použití více klíčů.

#### <a name="environment-setup"></a>Nastavení prostředí
![Nastavení prostředí pro test výkonnosti pracovního postupu](./media/performance/performance-test-environment.gif)

#### <a name="test-setup"></a>Nastavení testu
![Test pracovního postupu propustnosti korelace](./media/performance/correlation-throughput-workflow.gif "Nastavení testu pracovního postupu propustnosti korelace")

 Předchozí pracovní postup je stejný jako použitý v oddílu [Persistence](#persistence) . Pro testy korelace bez trvalosti není v modulu runtime nainstalována žádná Zprostředkovatel trvalosti. Korelace probíhá na dvou místech: CreateOrder a CompleteOrder.

#### <a name="test-results"></a>Výsledky testů
![Propustnost korelace](./media/performance/correlation-throughput-graph.gif "Graf propustnosti korelace")

 Tento graf znázorňuje snížení výkonu, protože se zvyšuje počet klíčů použitých při korelace na základě obsahu.  Podobnost na křivích mezi TCP a HTTP indikuje režii spojenou s těmito protokoly.

#### <a name="correlation-with-persistence"></a>Korelace s persistencí
 U trvalého pracovního postupu se zatížení procesoru z korelace na základě obsahu posouvá z modulu runtime pracovního postupu do databáze SQL.  Úložné procedury ve zprostředkovateli trvalosti SQL prohledají práci odpovídající klíčům, aby našli příslušný pracovní postup.

 ![Spojnicový graf znázorňující výsledky korelace a trvalosti](./media/performance/correlation-persistence-graph.gif)

 Korelace založená na kontextu je stále rychlejší než korelace na základě obsahu.  Rozdíl je však méně vyslovný, protože trvalost má větší vliv na výkon než korelace.

### <a name="complex-workflow-throughput"></a>Složitá propustnost pracovního postupu
 Složitost pracovního postupu není měřena pouze počtem aktivit.  Složené aktivity mohou obsahovat mnoho podřízených objektů a podřízené aktivity mohou být také složené aktivity.  Jak roste počet úrovní vnoření, tak počet aktivit, které mohou být aktuálně ve spuštěném stavu, a počet proměnných, které mohou být ve stavu.  Tento test porovnává propustnost mezi WF3 a WF4 při provádění složitých pracovních postupů.

### <a name="test-setup"></a>Nastavení testu
 Tyto testy byly spuštěny na počítači Intel Xeon X5355 @ 8jádrový 2,66 GHz a 4 GB paměti RAM se systémem Windows Server 2008 x64.  Testovací kód se spustí v jednom procesu s jedním vláknem na jádro, abyste dosáhli 100% využití CPU.

 Pracovní postupy vygenerované pro tento test mají dvě hlavní proměnné: hloubku a počet aktivit v jednotlivých sekvencích.  Každá úroveň hloubky zahrnuje paralelní aktivity, zatímco smyčky, rozhodnutí, přiřazení a sekvence.  V následujícím obrázku návrháře WF4 je graf toku nejvyšší úrovně obrázek.  Každá aktivita vývojového diagramu se podobá hlavnímu vývojovému diagramu.  Může být užitečné si představit Fractal při Picturing tohoto pracovního postupu, kde hloubka je omezená na parametry testu.

 Počet aktivit v daném testu je určen hloubkou a počtem aktivit na sekvenci.  Následující rovnice vypočítá počet aktivit v testu WF4:

 ![Rovnice pro výpočet počtu aktivit](./media/performance/number-activities-equation.gif)

 Počet aktivit testu WF3 lze vypočítat s mírně odlišnou rovnicí z důvodu nadbytečné posloupnosti:

 ![Rovnice pro výpočet počtu aktivit WF3](./media/performance/wf3-number-activities-equation.gif)

 Kde d je hloubka a je počet aktivit na sekvenci.  Logika za těmito rovnice je, že první konstanta vynásobená, je počet sekvencí a druhá konstanta je statickým počtem aktivit na aktuální úrovni.  V každém vývojovém diagramu jsou tři podřízené aktivity vývojového diagramu.  U nejnižší úrovně hloubky jsou tyto vývojové diagramy prázdné, ale na ostatních úrovních jsou kopie hlavního vývojového diagramu.  Počet aktivit v definici pracovního postupu každé variace testu je uveden v následující tabulce:

 ![Tabulka, která zobrazuje počet aktivit použitých v každém testu](./media/performance/workflow-variation-compare-table.gif)

 Počet aktivit v definici pracovního postupu se prudce zvyšuje s každou úrovní hloubky.  Ale v dané instanci pracovního postupu se spustí jenom jedna cesta na bod rozhodování, takže se spustí jenom malá podmnožina skutečných aktivit.

 ![Vývojový diagram pracovního postupu komplexní propustnosti](./media/performance/complex-workflow-throughput-workflow.gif)

 Pro WF3 byl vytvořen ekvivalentní pracovní postup. Návrhář WF3 zobrazí celý pracovní postup v oblasti návrhu místo vnoření, proto je pro zobrazení v tomto tématu příliš velký. Níže je uveden fragment pracovního postupu.

 ![Fragment pro vývojový diagram pracovního postupu WF3](./media/performance/wf3-workflow-snippet.gif)

 Pro vykonávání vnoření do extrémního případu používá jiný pracovní postup, který je součástí tohoto testu, použití vnořených sekvencí 100.  V nejvnitřnější sekvenci je jeden `Comment` nebo <xref:System.Workflow.Activities.CodeActivity>.

 ![Vývojový diagram vnořené sekvence](./media/performance/nested-sequence-workflow.gif)

 Sledování a trvalost se v rámci tohoto testu nepoužívají.

### <a name="test-results"></a>Výsledky testů
 ![Sloupcový graf znázorňující výsledky propustnosti výkonu](./media/performance/throughput-performance-results.gif)

 I u složitých pracovních postupů s hodně hloubkou a vysokým počtem aktivit jsou výsledky výkonu konzistentní s ostatními čísly propustnosti, které jsou uvedené dříve v tomto článku.  WF4's propustnost je rychlejší a musí se porovnávat podle logaritmické stupnice.

### <a name="memory"></a>Rezident
 Režie paměti programovací model Windows Workflow Foundation se měří ve dvou klíčových oblastech: složitost pracovního postupu a počet definicí pracovních postupů.  Měření paměti byla provedena na pracovní stanici Windows 7 64.  Existuje mnoho způsobů, jak získat měření velikosti pracovní sady, jako jsou čítače výkonu monitorování, prostředí cyklického dotazování. WorkingSet nebo použití nástroje, jako je VMMap, který je k dispozici v [VMMap](/sysinternals/downloads/vmmap). Kombinace metod byla použita k získání a ověření výsledků každého testu.

### <a name="workflow-complexity-test"></a>Test složitosti pracovního postupu
 Test složitosti pracovního postupu měří rozdíl pracovní sady na základě složitosti pracovního postupu.  Kromě složitých pracovních postupů použitých v předchozí části se přidávají nové variace, které se týkají dvou základních případů: pracovní postup jedné aktivity a sekvence s 1000 aktivitami.  Pro tyto testy jsou pracovní postupy inicializovány a provedeny k dokončení jedné sériové smyčky po dobu jedné minuty.  Každá variace testu se spouští třikrát a zaznamenaná data jsou průměrem těchto tří spuštění.

 Tyto dva nové základní testy mají pracovní postupy, které vypadají jako v následujícím příkladu:

 ![Složitý pracovní postup pro WF3 i WF4](./media/performance/complex-workflow-wf3-wf4.gif)

 V pracovním postupu WF3 uvedeném výše se používají prázdné aktivity <xref:System.Workflow.Activities.CodeActivity>.  Pracovní postup WF4 výše používá aktivity `Comment`.  Aktivita `Comment` byla popsána v části porovnání výkonu na úrovni komponenty výše v tomto článku.

 ![Sloupcový graf znázorňující komplexní využití paměti pracovního postupu pro pracovní postupy WF3 a WF4](./media/performance/complex-memory-usage-wf3-wf4.gif)

 Jedním z jasných trendů, které je potřeba odvšimnout v tomto grafu, je, že vnořování má poměrně minimální dopad na využití paměti v WF3 i WF4.  Nejvýznamnější dopad na paměť pochází z počtu aktivit v daném pracovním postupu.  S ohledem na data z sekvence 1000, komplexní hloubky 5 sekvence 5 a složitá hloubka 7 sekvence 1, je zřejmé, že když počet aktivit vstoupí do tisíců, zvýšení využití paměti bude poznatelný.  V extrémním případě (hloubka 7 sekvence 1), kde se nacházejí ne29K aktivity, WF4 používá téměř 79% méně paměti než WF3.

### <a name="multiple-workflow-definitions-test"></a>Test vícenásobných pracovních postupů
 Měření paměti na definici pracovního postupu je rozděleno do dvou různých testů z důvodu dostupných možností pro hostování pracovních postupů v WF3 a WF4.  Testy jsou spouštěny jiným způsobem než test složitosti pracovního postupu v tom, že daný pracovní postup je instance a proveden pouze jednou pro každou definici.  Důvodem je, že definice pracovního postupu a jeho hostitel zůstane v paměti pro celou dobu životnosti domény AppDomain.  Paměť používaná při spuštění dané instance pracovního postupu by měla být vyčištěna během uvolňování paměti.  Pokyny k migraci pro WF4 obsahují podrobnější informace o možnostech hostování. Další informace najdete v tématu [Migrace WF kuchařka: Hostování pracovního postupu](https://go.microsoft.com/fwlink/?LinkID=153313).

 Vytvoření mnoha definicí pracovních postupů pro test definice pracovního postupu lze provést několika způsoby.  Například jedna by mohla použít generování kódu k vytvoření sady 1000 pracovních postupů, které jsou identické s výjimkou názvu a uložení každého z těchto pracovních postupů do samostatných souborů.  Tento přístup byl proveden pro test hostovaný v konzole.  V WF3 se ke spuštění definice pracovního postupu použila třída <xref:System.Workflow.Runtime.WorkflowRuntime>.  WF4 může buď pomocí <xref:System.Activities.WorkflowApplication> vytvořit jednu instanci pracovního postupu nebo přímo použít <xref:System.Activities.WorkflowInvoker> ke spuštění aktivity, jako by šlo o volání metody.  <xref:System.Activities.WorkflowApplication> je hostitel jedné instance pracovního postupu a má pro <xref:System.Workflow.Runtime.WorkflowRuntime> paritu funkcí, které byly použity v tomto testu.

 Při hostování pracovních postupů ve službě IIS je možné použít <xref:System.Web.Hosting.VirtualPathProvider> k vytvoření nového <xref:System.ServiceModel.WorkflowServiceHost> namísto generování všech souborů XAMLX nebo XOML.  @No__t_0 zpracuje příchozí požadavek a odpoví "virtuálním souborem", který lze načíst z databáze nebo v tomto případě vygenerovaného za běhu.  Je proto nutné vytvořit 1000 fyzických souborů.

 Definice pracovního postupu použité v testu konzoly byly jednoduché sekvenční pracovní postupy s jednou aktivitou.  Jediná aktivita byla prázdná <xref:System.Workflow.Activities.CodeActivity> pro případ WF3 a aktivitu `Comment` pro případ WF4.  Případ hostovaný v rámci služby IIS používaný při přijímání zprávy a ukončení odeslání odpovědi:

Následující obrázek znázorňuje WF3 pracovní postup s ReceiveActivity a pracovním postupem WF4 se vzorem požadavků a odpovědí:

 ![Služby pracovních postupů v WF3 a WF4](./media/performance/workflow-receive-activity.gif)

 Následující tabulka ukazuje rozdíl v pracovní sadě mezi definicí jedné pracovní postup a definicemi 1001:

|Možnosti hostování|Rozdíl pracovní sady WF3|Rozdíl pracovní sady WF4|
|---------------------|---------------------------|---------------------------|
|Hostované pracovní postupy konzolové aplikace|18 MB|9 MB|
|Služby pracovních postupů hostovaných službou IIS|446 MB|364 MB|

 Hostování definic pracovních postupů ve službě IIS spotřebovává mnohem více paměti z důvodu <xref:System.ServiceModel.WorkflowServiceHost>, podrobných artefaktů služby WCF a logiky zpracování zpráv, která je přidružena k hostiteli.

 Pro hostování konzoly nástroje v WF3 byly pracovní postupy implementovány v kódu místo XOML.  Ve výchozím nastavení je použita hodnota XAML v WF4.  XAML je uložen jako vložený prostředek v sestavení a zkompilován během běhu za účelem zajištění implementace pracovního postupu.  K tomuto procesu je spojená nějaká režie.  Aby bylo možné provést spravedlivé porovnání mezi WF3 a WF4, byly použity kódované pracovní postupy namísto XAML.  Příklad jednoho z pracovních postupů WF4 je uveden níže:

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

 Existuje mnoho dalších faktorů, které mohou ovlivnit spotřebu paměti. Pro všechny spravované programy se stále platí stejná doporučení.  V prostředích hostovaných službou IIS zůstane objekt <xref:System.ServiceModel.WorkflowServiceHost> vytvořený pro definici pracovního postupu v paměti, dokud se fond aplikací recykluje.  To by mělo být při psaní rozšíření zachováno.  Je také vhodné se vyhnout "globálním" proměnným (proměnné v oboru celého pracovního postupu) a omezit rozsah proměnných, pokud je to možné.

## <a name="workflow-runtime-services"></a>Běhové služby pracovních postupů

### <a name="persistence"></a>Dočasné
 WF3 a WF4 se dodávají se zprostředkovatelem trvalosti SQL.  Zprostředkovatel trvalosti SQL WF3 je jednoduchá implementace, která serializace instanci pracovního postupu a ukládá ji do objektu BLOB.  Z tohoto důvodu výkon tohoto zprostředkovatele závisí silně na velikosti instance pracovního postupu.  V WF3 se velikost instance může zvětšit z mnoha důvodů, jak je popsáno výše v tomto dokumentu.  Mnoho zákazníků nepoužívá výchozího poskytovatele trvalosti SQL, protože ukládání serializovaných instancí v databázi neposkytuje žádnou viditelnost stavu pracovního postupu.  Aby bylo možné najít konkrétní pracovní postup bez znalosti ID pracovního postupu, bude nutné, aby bylo možné deserializovat každou trvalou instanci a prohlédnout si obsah.  Mnoho vývojářů preferuje psaní vlastních poskytovatelů trvalosti pro překonání této překážky.

 Zprostředkovatel trvalosti WF4 SQL se pokusil vyřešit některé z těchto otázek.  Dočasné tabulky zveřejňují určité informace, jako jsou aktivní záložky a vlastnosti k vlastnost.  Nová funkce korelace na základě obsahu v WF4 nefunguje správně s využitím přístupu WF3 SQL pro trvalost, který v organizaci trvalé instance pracovního postupu způsobil nějakou změnu.  Díky tomu je úloha poskytovatele trvalější a přináší další zátěž v databázi.

### <a name="environment-setup"></a>Nastavení prostředí
![Nastavení prostředí pro test výkonnosti pracovního postupu](./media/performance/performance-test-environment.gif)

### <a name="test-setup"></a>Nastavení testu
 I s vylepšenou sadou funkcí a lepším zpracováním souběžnosti je poskytovatel SQL trvalosti v WF4 rychlejší než poskytovatel v WF3.  Aby se to předvedlo, dva pracovní postupy, které provádějí v podstatě stejné operace v WF3 a WF4, jsou porovnávány níže.

 ![Pracovní postup trvalosti v WF3 vlevo a WF4 na pravé straně](./media/performance/persist-workflow-wf3-wf4.gif)

 Oba pracovní postupy jsou vytvářeny přijatou zprávou.  Po odeslání počáteční odpovědi se pracovní postup trvale zachová.  V případě WF3 je k zahájení trvalosti použita prázdná <xref:System.Workflow.ComponentModel.TransactionScopeActivity>.  Totéž lze dosáhnout v WF3 označením aktivity jako "trvale při zavření".  Druhá, korelační zpráva dokončí pracovní postup.  Pracovní postupy jsou trvalé, ale nejsou uvolněny.

### <a name="test-results"></a>Výsledky testů
 ![Sloupcový graf znázorňující trvalost propustnosti](./media/performance/throughput-persistence-graph.gif)

 Když je přenos mezi klientem a střední vrstvou HTTP, trvalost v WF4 zobrazuje vylepšení 2,6 časů.  Přenos TCP zvyšuje tento faktor na 3,0 časů.  Ve všech případech je využití procesoru na střední úrovni 98% nebo vyšší.  Důvodem, proč je WF4 propustnost větší, je z důvodu rychlejšího modulu runtime pracovního postupu.  Velikost serializované instance je pro oba případy nízká a není hlavním přispívajícím prvkem v této situaci.

 Pracovní postupy WF3 i WF4 v tomto testu používají aktivitu k explicitnímu označení toho, kdy by trvala trvalá situace.  Výhodou je zachování pracovního postupu bez jeho uvolnění.  V WF3 je také možné trvale zachovat pomocí funkce <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A>, ale uvolní instanci pracovního postupu z paměti.  Pokud vývojář používající WF3 chce zajistit, že pracovní postup v určitých bodech přetrvává, musí buď upravit definici pracovního postupu, nebo platit náklady na uvolnění a opětovné načtení instance pracovního postupu.  Nová funkce v WF4 umožňuje zachovat bez uvolnění: <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>.  Tato funkce umožňuje, aby se instance pracovního postupu trvala při nečinnosti, ale zůstala v paměti, dokud není splněna prahová hodnota <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> nebo dokud nebude vykonání obnoveno.

 Všimněte si, že zprostředkovatel trvalosti WF4 SQL provádí více práce v databázové vrstvě.  SQL Database se může stát kritickým bodem, takže je důležité monitorovat využití procesoru a disku.  Nezapomeňte do aplikace pracovní postup testování výkonu zahrnout následující čítače výkonu z databáze SQL:

- Fyzický disk \\% doba čtení disku

- Fyzický disk \\% času disku

- Fyzický disk \\% času zápisu na disk

- Fyzický disk \\% Průměrná délka fronty disku

- Délka fronty čtení z disku fyzický

- Délka fronty zápisu na disk fyzický

- Délka fronty disku fyzický

- Informace o procesoru \\% času procesoru

- SQLServer: Latches\Average doba čekání na západku (MS)

- SQLServer: Latches\Latch čeká za sekundu.

### <a name="tracking"></a>Sledování
 Sledování pracovního postupu lze použít ke sledování průběhu pracovního postupu.  Informace, které jsou součástí sledovacích událostí, jsou určeny profilem sledování.  Čím komplexnější profil sledování, tím dražší sledování se stane.

 WF3 se dodává se službou sledování založené na SQL.  Tato služba může pracovat v režimech v dávce i v jiných dávkách.  V režimu bez dávek jsou sledování událostí zapisovány přímo do databáze.  V dávkovém režimu jsou sledování událostí shromažďovány do stejné dávky jako stav instance pracovního postupu.  Dávkový režim má nejlepší výkon pro nejširší škálu návrhů pracovního postupu.  Dávkování ale může mít negativní dopad na výkon, pokud pracovní postup spouští mnoho aktivit bez zachování a aktivity jsou sledovány.  K tomu obvykle dochází ve smyčce a nejlepším způsobem, jak se tomuto scénáři vyhnout, je navrhovat velké smyčky, aby obsahovaly trvalý bod.  Představení bodu trvalosti do smyčky může negativně ovlivnit výkon, takže je důležité změřit náklady na jednotlivé a se zaměřením na rovnováhu.

 WF4 se nedodává se službou sledování SQL.  Zaznamenávání informací o sledování do databáze SQL je možné zpracovat lépe z aplikačního serveru, nikoli z integrovaného do .NET Framework. Proto je sledování SQL teď zpracováváno pomocí technologie AppFabric.  Dodaný Zprostředkovatel sledování v WF4 je založený na trasování událostí pro Windows (ETW).

 ETW je systém událostí s nízkou latencí, který je součástí systému Windows na úrovni jádra.  Používá model poskytovatele/příjemce, který umožňuje, aby bylo možné pouze vytvořit pokutu pro trasování událostí v případě, že existuje skutečný příjemce.  Kromě událostí jádra, jako je procesor, disk, paměť a využití sítě, mnoho aplikací využívá i trasování událostí pro Windows.  Události ETW jsou výkonnější než čítače výkonu v tom, že události lze přizpůsobit aplikaci.  Událost může obsahovat text, jako je ID pracovního postupu nebo informační zpráva.  Události jsou také zařazeny do kategorií vyčíslení, takže využívání určité podmnožiny událostí bude mít menší dopad na výkon než zachycení všech událostí.

 Výhody použití ETW pro sledování místo SQL include:

- Kolekce sledovacích událostí může být oddělena jiným procesem.  Díky tomu je větší flexibilita při zaznamenávání událostí.

- Události sledování ETW jsou snadno kombinovány s událostmi ETW WCF nebo jinými zprostředkovateli trasování událostí pro Windows, jako je SQL Server nebo zprostředkovatel jádra.

- Autoři pracovních postupů nemusí měnit pracovní postup, aby bylo možné lépe pracovat s určitou implementací sledování, jako je například režim dávky služby sledování SQL WF3.

- Správce může zapnout nebo vypnout sledování bez recyklace procesu hostitele.

 Výhody sledování trasování událostí pro Windows přináší nevýhodný výkon.  Události trasování událostí pro Windows se můžou ztratit, pokud je systém v intenzivním tlaku na zdroje.  Zpracování událostí není určeno k blokování normálního spuštění programu, a proto není zaručeno, že všechny události ETW budou všesměrově vysílané svým předplatitelům.  Díky tomu je sledování ETW Skvělé pro monitorování stavu, ale není vhodné pro auditování.

 I když WF4 nemá poskytovatele sledování SQL, technologie AppFabric dělá.  Přístup ke sledování SQL pro AppFabric je přihlášení k odběru událostí ETW pomocí služby systému Windows, která události zapisuje a zapisuje je do tabulky SQL navržené pro rychlé vložení.  Samostatná úloha vyprázdní data z této tabulky a reformuje je do tabulek pro vytváření sestav, které lze zobrazit na řídicím panelu AppFabric.  To znamená, že dávka sledování událostí je zpracována nezávisle na pracovním postupu, ze kterého pochází, a proto nemusí čekat na bod trvalosti před nahráním.

 Události trasování událostí pro Windows se dají zaznamenávat pomocí nástrojů, jako je například Logman nebo Xperf.  Kompaktní soubor ETL lze zobrazit pomocí nástroje, jako je například xperfview nebo převeden do čitelnějšího formátu, jako je například XML, pomocí rozhraní Tracerpt.  V WF3 je jediná možnost, jak získat události sledování bez databáze SQL, vytvořit vlastní službu sledování. Další informace o trasování událostí pro Windows najdete v tématu [služby WCF a trasování událostí pro Windows](../wcf/samples/wcf-services-and-event-tracing-for-windows.md) a [trasování událostí – aplikace pro Windows](/windows/desktop/etw/event-tracing-portal).

 Povolení sledování pracovního postupu bude mít vliv na výkon v různých stupních.  Srovnávací test používá nástroj Logman ke zpracování událostí sledování ETW a jejich zaznamenávání do souboru ETL.  Náklady na sledování SQL v rozhraní AppFabric nejsou v rozsahu tohoto článku.  V tomto srovnávacím testu se zobrazí základní profil sledování, který se používá také v rozhraní AppFabric.  Zahrnuje také náklady na sledování pouze událostí monitorování stavu.  Tyto události jsou užitečné pro řešení problémů a určení průměrné propustnosti systému.

### <a name="environment-setup"></a>Nastavení prostředí
 ![Nastavení prostředí pro test výkonnosti pracovního postupu](./media/performance/performance-test-environment.gif)

### <a name="test-results"></a>Výsledky testů

 ![Sloupcový graf znázorňující náklady sledování pracovního postupu](./media/performance/workflow-tracking-costs.gif)

 Monitorování stavu má přibližně 3% dopad na propustnost.  Náklady na základní profil jsou přibližně 8%.

## <a name="interop"></a>Zprostředkovatel komunikace
 WF4 je skoro úplný přepis [!INCLUDE[wf1](../../../includes/wf1-md.md)], takže pracovní postupy a aktivity WF3 nejsou přímo kompatibilní s WF4.  Mnoho zákazníků, kteří programovací model Windows Workflow Foundation brzkém rozhodnutím, bude mít interní nebo vlastní definice pracovních postupů třetích stran a vlastní aktivity pro WF3.  Jedním ze způsobů, jak usnadnit přechod na WF4, je použití aktivity spolupráce, která může provádět aktivity WF3 z pracovního postupu WF4.  Doporučuje se, aby se <xref:System.Activities.Statements.Interop> aktivita používala pouze v případě potřeby. Další informace o migraci na WF4 najdete v [pokynech k migraci WF4](https://go.microsoft.com/fwlink/?LinkID=153313).

### <a name="environment-setup"></a>Nastavení prostředí
 ![Nastavení prostředí pro test výkonnosti pracovního postupu](./media/performance/performance-test-environment.gif)

### <a name="test-results"></a>Výsledky testů
 
V následující tabulce jsou uvedeny výsledky spuštění pracovního postupu obsahujícího pět aktivit v posloupnosti v různých konfiguracích.

|Test|Propustnost (pracovní postupy/s)|
|----------|-----------------------------------|
|Sekvence WF3 v modulu runtime WF3|1 576|
|Sekvence WF3 v modulu runtime WF4 pomocí spolupráce|2 745|
|WF4 sekvence|153 582|

 Existuje významné zvýšení výkonu při použití zprostředkovatele komunikace přes rovnou WF3.  Nicméně při porovnání s aktivitami WF4 je nárůst zanedbatelný.

## <a name="summary"></a>Souhrn
 Velké investice do výkonu pro WF4 se v mnoha důležitých oblastech vyplácejí.  Výkon součásti pro jednotlivé pracovní postupy je v některých případech rychlejší v WF4 ve srovnání s WF3 z důvodu [!INCLUDE[wf1](../../../includes/wf1-md.md)]ho modulu runtime pro štíhlou dobu.  Hodnoty latence jsou také výrazně lepší.  To znamená, že snížení výkonu při použití [!INCLUDE[wf1](../../../includes/wf1-md.md)] na rozdíl od ručního kódování služeb orchestrace WCF je velmi malé, protože přináší přidané výhody použití [!INCLUDE[wf1](../../../includes/wf1-md.md)].  Výkon trvalosti se zvýšil o faktor 2,5-3,0.  Sledování stavu pomocí sledování pracovního postupu teď má velmi malou režii.  K dispozici je komplexní sada průvodců migrací, které zvažuje přesun z WF3 do WF4.  To vše by mělo WF4 být atraktivní možností pro psaní složitých aplikací.
