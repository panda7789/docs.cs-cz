---
title: Výkon systému Windows Workflow Foundation 4
ms.date: 03/30/2017
ms.assetid: 67d2b3e8-3777-49f8-9084-abbb33b5a766
ms.openlocfilehash: 793645c442e960c43f00c3ea3c9b636a4c539706
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="windows-workflow-foundation-4-performance"></a>Výkon systému Windows Workflow Foundation 4
Dustinu Metzgar  
  
 Wenlong Dong  
  
 V září roku 2010 Microsoft Corporation  
  
 Microsoft [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] obsahuje hlavní revizi Windows Workflow Foundation (WF) s velkou investic ve výkonu.  Tato nová revize představuje významné návrhu změny z předchozích verzí [!INCLUDE[wf1](../../../includes/wf1-md.md)] dodávané jako součást rozhraní .NET Framework 3.0 a [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Byla přepracována ze základní programovací model, modulu runtime a nástrojů výrazně zlepšit výkon a použitelnost. Toto téma ukazuje důležité výkonové charakteristiky tyto revize a porovná je s ohledem na předchozí verzi.  
  
 Výkon součásti jednotlivé pracovní postup se zvýšila pořadí podle velikosti mezi WF3 a WF4.  Zůstane mezery mezi zakódovaným na straně služby Windows Communication Foundation (WCF) a [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služeb pracovních postupů poměrně malý.  Latence pracovního postupu byla výrazně snižuje v WF4.  Trvalost výkonu zvýšilo faktorem 2.5 3.0.  Monitorování stavu prostřednictvím pracovního postupu pro sledování má výrazně menší režijní náklady.  Tyto jsou přesvědčivé migraci na nebo přijmout WF4 ve svých aplikacích.  
  
## <a name="terminology"></a>Terminologie  
 Verze [!INCLUDE[wf1](../../../includes/wf1-md.md)] byla zavedená v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] budeme ho označovat jako WF4 pro zbývající část tohoto tématu.  [!INCLUDE[wf1](../../../includes/wf1-md.md)] bylo zavedeno v rozhraní .net 3.0 a měl několik menších revize prostřednictvím [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] SP1. [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Verzi Workflow Foundation budeme ho označovat jako WF3 pro zbývající část tohoto tématu. WF3 se dodává v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] -souběžného s WF4. Další informace o migraci artefaktů WF3 a WF4 v tématu: [příručka k migraci 4 Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=153313)  
  
 Windows Communication Foundation (WCF) je jednotný programovací model pro vytváření aplikací orientovaných na služby společnosti Microsoft. To bylo poprvé dostupné v rámci rozhraní .net 3.0 společně s WF3 a nyní je jedním z klíčových součástí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Windows Server AppFabric je sada integrovaných technologií, které usnadňují sestavování, škálování a správu webových a kompozitních aplikací, které běží ve službě IIS. Poskytuje nástroje pro sledování a správu služeb a pracovních postupů. Další informace najdete v tématu [Windows Server AppFabric](http://msdn.microsoft.com/windowsserver/ee695849.aspx)  
  
## <a name="goals"></a>Cíle  
 Cílem tohoto tématu je zobrazit charakteristiky výkonu už WF4 s daty měří pro různé scénáře. Také poskytuje podrobné porovnání mezi WF4 a WF3 a proto zobrazí velký vylepšení, které byly provedeny v této nové revize. Scénáře a data uvedená v tomto článku vyčíslení základní náklady na různých aspektů WF4 a WF3. Tato data jsou užitečné porozumět charakteristiky výkonu už WF4 a mohou být užitečné při plánování migrace z WF3 do WF4 nebo pomocí WF4 při vývoji aplikace. Nicméně mělo dbát v závěry z data uvedená v tomto článku. Výkon aplikace složené pracovního postupu je vysoce závisí na tom, jak je implementována pracovního postupu a jak různé součásti jsou integrované. Jeden musí měřit každá aplikace k určení výkonové charakteristiky této aplikace.  
  
## <a name="overview-of-wf4-performance-enhancements"></a>Přehled WF4 vylepšení výkonu  
 WF4 pečlivě byl navržen a implementuje pomocí vysoký výkon a škálovatelnost, které jsou popsané v následujících částech.  
  
### <a name="wf-runtime"></a>Modul Runtime pracovního postupu  
 Základem [!INCLUDE[wf1](../../../includes/wf1-md.md)] runtime je asynchronní Plánovač, který řídí provádění aktivity v pracovním postupu. Poskytuje původce, předvídatelný spuštění prostředí pro aktivity. Prostředí má kontraktu dobře definovaný pro spuštění, pokračování, dokončení, zrušení, výjimky a předvídatelný model vláken.  
  
 Oproti WF3 má modul runtime WF4 efektivnější plánovače. Využívá stejný fond vláken vstupně-výstupních operací, který se používá pro [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], což je velmi efektivní i při provádění zpracovat v dávce pracovní položky. Fronta plánovače interní pracovních položek je optimalizovaná pro nejběžnější vzorce používání. Modul runtime WF4 také spravuje stavy provádění způsobem, velmi šedé – s minimálním synchronizace a zpracování logiku, zatímco WF3 závisí na události zobrazené – registrace a volání provádět komplexní synchronizace přechodů mezi stavy událostí.  
  
### <a name="data-storage-and-flow"></a>Úložiště dat a toku  
 V WF3, se data přidružená k aktivitě s modelováním pomocí vlastností závislostí implementované typ <xref:System.Windows.DependencyProperty>. Vzor vlastnost závislosti byla zavedena v systému Windows Presentation Foundation (WPF). Tento vzor je obecně velmi flexibilní podporu snadno datové vazby a dalších funkcí uživatelského rozhraní. Vzor však vyžaduje vlastnosti, které chcete definovat jako statických polí v definici pracovního postupu. Vždy, když [!INCLUDE[wf1](../../../includes/wf1-md.md)] runtime Nastaví nebo získá hodnoty vlastností, se týká logiku výraznou vážené hledání.  
  
 WF4 používá vymazat data rozsahu logiku k výraznému zlepšení zpracování dat v pracovním postupu. Ji odděluje data uložená v aktivitě z data, která je předávaných napříč hranicemi aktivity pomocí dvou různých koncepty: proměnné a argumenty. Pomocí zrušte hierarchické obor pro proměnné a argumenty "V/Out nebo InOut" je výrazně snížit složitost dat využití pro aktivity a doba platnosti dat je také automaticky obor. Aktivity mají dobře definovaný podpis popsaného její argumenty. Jednoduše zkontrolováním aktivitu můžete určit, jaká data se očekává, že pro příjem a jaká data budou vytvořeny ho jako výsledek jeho spuštění.  
  
 V WF3 aktivity byly inicializovány při vytvoření pracovního postupu. 4 WF se inicializují aktivity jenom v případě, že jsou prováděny odpovídající aktivity. To umožňuje jednodušší životního cyklu aktivity bez provádění operací inicializovat/Uninitialize, když se vytvoří novou instanci pracovního postupu a proto má dosáhnout další efektivitu  
  
### <a name="control-flow"></a>Tok řízení  
 Jako v případě žádný programovací jazyk [!INCLUDE[wf1](../../../includes/wf1-md.md)] poskytuje podporu pro ovládací prvek toky definice pracovního postupu zavedením sadu aktivity toku řízení pro pořadí, ve smyčce, větvení a další. V WF3, pokud se stejná aktivita je třeba znovu provést, a nové <xref:System.Workflow.ComponentModel.ActivityExecutionContext> je vytvořena a aktivity naklonována prostřednictvím zobrazené – serializace a deserializace logiku, na základě <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Výkon pro iterativní řízení toky je obvykle mnohem nižší než provádění posloupnost aktivit.  
  
 WF4 zpracovává to poměrně jiným způsobem. Přebírá šablony aktivit, vytvoří nový objekt vlastnosti ActivityInstance a přidá ji do fronty plánovače. Tento celý proces pouze zahrnuje vytvoření explicitní objektu a je velmi šedé.  
  
### <a name="asynchronous-programming"></a>Asynchronní programování  
 Aplikace obvykle mají lepší výkon a škálovatelnost asynchronní programování distribuovaná výpočetní činností nebo dlouhotrvající blokování operací, jako je vstupně-výstupních operací. Poskytuje asynchronní podpora prostřednictvím základní aktivitě typy WF4 <xref:System.Activities.AsyncCodeActivity>, <xref:System.Activities.AsyncCodeActivity%601>. Modul runtime nativně rozumí asynchronní aktivity a proto můžete automaticky umístí instance v zóně no-persist při nezpracovaných asynchronní pracovní. Vlastní aktivity lze odvozovat od tyto typy pro práci asynchronní bez podržte podprocesu plánovače pracovního postupu a blokuje veškeré aktivity, které pravděpodobně bude moci spustit souběžně.  
  
### <a name="messaging"></a>Zasílání zpráv  
 WF3 měl původně velmi omezená podpora zasílání zpráv prostřednictvím externí události nebo webové služby volání. V rozhraní .net 3.5, může být pracovních implementovaný jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klienty nebo zveřejněné jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služeb prostřednictvím <xref:System.Workflow.Activities.SendActivity> a <xref:System.Workflow.Activities.ReceiveActivity>. V WF4, má se další posílit koncept založené na pracovním postupu zasílání zpráv programování prostřednictvím těsná integrace [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] logiku pro zasílání zpráv do pracovního postupu.  
  
 Uvedené v kanálu zpracování jednotná zprávy [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] v rozhraní .net 4 pomáhá WF4 služeb má výrazně lepší výkon a škálovatelnost než WF3. WF4 také poskytuje bohatší zasílání zpráv programovací podporu, který může model komplexní zpráva vzory Exchange (MEPs). Vývojáři mohou pomocí buď kontrakty typové služeb k dosažení snadno programování nebo kontrakty beztypové služeb můžete dosáhnout lepšího výkonu bez placení náklady na serializaci. Ukládání do mezipaměti podpory prostřednictvím kanálu na straně klienta <xref:System.ServiceModel.Activities.SendMessageChannelCache> třídy v WF4 pomáhá vývojářům vytvářet rychlé aplikace s minimálním úsilím. Další informace najdete v tématu [změna úrovní sdílení mezipaměti pro aktivity odesílání](../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).  
  
### <a name="declarative-programming"></a>Deklarativní programování  
 WF4 poskytuje vyčištění a jednoduchý deklarativní programovací rozhraní modelu obchodních procesů a služeb. Programovací model podporuje plně deklarativního složení aktivity, s žádný kód – vedle, výrazně zjednodušuje vytváření pracovního postupu. V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], založených na XAML deklarativní programovacím rozhraní má byla unified do jednoho sestavení System.Xaml.dll pro podporu WPF a WF.  
  
 V WF4 XAML poskytuje skutečně deklarativní prostředí a umožňuje pro celý definici pracovního postupu být definován v kódu XML, odkazující na typy vytvořené pomocí rozhraní .NET a aktivity. To bylo obtížné dělat v WF3 s formát XOML bez zásahu logiku vlastního kódu. Novým zásobníkem XAML v rozhraní .net 4 má mnohem lepší výkon při serializaci nebo deserializaci artefakty pracovního postupu a díky deklarativní programování více přitažlivé a plnou.  
  
### <a name="workflow-designer"></a>Návrhář postupu provádění  
 Plně deklarativního programování podpora WF4 explicitně ukládá vyšší požadavky pro návrh doba pro velké pracovní postupy. Návrhář postupu provádění v WF4 má mnohem lepší škálovatelnost než pro velké pracovní postupy pro WF3. S podporou virtualizace uživatelského rozhraní návrháře můžete snadno načíst velké pracovního postupu aktivit 1000 za několik sekund, i když je téměř možné načíst několik set aktivit pracovního postupu pomocí návrháře WF3.  
  
## <a name="component-level-performance-comparisons"></a>Porovnání výkonu úrovni součástí  
 Tato část obsahuje data na přímé porovnání mezi jednotlivé aktivity v WF3 a WF4 pracovních postupů.  Klíčové oblasti jako trvalost mít více velký dopad na výkon než komponenty jednotlivé aktivity.  Vylepšení výkonu v jednotlivých součástí v nástroji WF4 jsou ale důležité, protože se teď dostatečně rychlé proti programového ruční orchestration logiku součásti.  Následuje příklad je popsaná v následující části: "Service složení scénář."  
  
### <a name="environment-setup"></a>Nastavení prostředí  
 ![Pracovní postup prostředí pro testování výkonu](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
 Výše uvedené schéma ukazuje konfiguraci počítače používá k měření výkonu úrovni součásti. Jeden server a pět klienti připojení více než jedno síťové rozhraní sítě Ethernet 1 GB/s. Pro snadné měření server konfigurován pro použití jediného jádra dual-proc/čtyřjádrový serveru se systémem Windows Server 2008 x86. Systém využití procesoru je udržován na úrovni téměř 100 %.  
  
### <a name="test-details"></a>Podrobnosti o testu  
 WF3 <xref:System.Workflow.Activities.CodeActivity> je pravděpodobně nejjednodušší aktivity, který můžete použít v pracovním postupu WF3.  Aktivity volá metodu v modelu code-behind, programátorů pracovního postupu můžete vložit do vlastní kód.  V WF4, neexistuje žádné přímé analogovým k WF3 <xref:System.Workflow.Activities.CodeActivity> , nabízí stejné funkce.  Všimněte si, že je <xref:System.Activities.CodeActivity> základní třídy v WF4, která nesouvisí se WF3 <xref:System.Workflow.Activities.CodeActivity>.  Autoři pracovního postupu se doporučuje vytvořit vlastní aktivity a vytváření pracovních postupů jen XAML.  V testech níže volá aktivita `Comment` použijí se místo prázdnou <xref:System.Workflow.Activities.CodeActivity> v pracovních postupech WF4.  Kód `Comment` aktivity je následující:  
  
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
  
### <a name="empty-workflow"></a>Prázdný pracovního postupu  
 Tento test používá pracovní postup pořadí s žádné podřízené aktivity.  
  
### <a name="single-activity"></a>Jediné aktivity  
 Pracovní postup je pořadí pracovní postup obsahující jednu podřízenou aktivitu.  Je aktivita <xref:System.Workflow.Activities.CodeActivity> s žádný kód v případě, že WF3 a `Comment` aktivity v případě, že WF4.  
  
### <a name="while-with-1000-iterations"></a>Chvíli s 1000 iterací  
 Pořadí pracovní postup obsahuje jeden <xref:System.Activities.Statements.While> aktivitu jednu podřízenou aktivity ve smyčce, který neprovádí veškerou práci.  
  
### <a name="replicator-compared-to-parallelforeach"></a>Replikátor ve srovnání s ParallelForEach  
 <xref:System.Workflow.Activities.ReplicatorActivity> v WF3 má postupného a paralelní provádění režimy.  V režimu sekvenční aktivity výkon je podobná <xref:System.Workflow.Activities.WhileActivity>.  <xref:System.Workflow.Activities.ReplicatorActivity> Je nejvhodnější pro paralelní zpracování.  Je analogovým WF4 pro tento <xref:System.Activities.Statements.ParallelForEach%601> aktivity.  
  
 Následující diagram znázorňuje použít pro tento test pracovních postupů. Pracovní postup WF3 je na levé straně a pracovní postup WF4 je na pravé straně.  
  
 ![WF3 ReplicatorActivity a WF4 ParallelForEach](../../../docs/framework/windows-workflow-foundation/media/replicatorandparallelforeach.gif "ReplicatorAndParallelForEach")  
  
### <a name="sequential-workflow-with-five-activities"></a>Sekvenční pracovní postup s pěti aktivity  
 Tento test slouží k zobrazení účinku s několika aktivity spustit v pořadí.  V pořadí jsou pět aktivity.  
  
### <a name="transaction-scope"></a>Oboru transakce  
 Test oboru transakce z jiné testy se mírně liší v, že pro každé iteraci není vytvořena nová instance pracovního postupu.  Místo toho strukturovaná pracovního postupu s chvíli obsahující smyčky <xref:System.Activities.Statements.TransactionScope> aktivity obsahující jediné aktivity, která nemá žádné kroky.  Každé spuštění dávky 50 iterací prostřednictvím klienta při smyčky se počítá jako jednu operaci.  
  
### <a name="compensation"></a>kompenzace  
 Pracovní postup WF3 má aktivita jediné aktivity s názvem `WorkScope`.  Aktivity jednoduše implementuje <xref:System.Workflow.ComponentModel.ICompensatableActivity> rozhraní:  
  
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
  
 Cíle obslužná rutina chyby `WorkScope` aktivity. Pracovní postup WF4 je stejně zneužívající vlastností prohlížeče.  A <xref:System.Activities.Statements.CompensableActivity> má text a kompenzace obslužná rutina.  Explicitní compensate je další v pořadí.  Aktivita textu a činnost kompenzace obslužnou rutinu jsou obě prázdný implementace:  
  
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
  
 Obrázek 2 – WF3 (vlevo) a pracovních postupů (vpravo) základní kompenzace WF4  
  
### <a name="performance-test-results"></a>Výsledky testu výkonu  
 ![Výsledky testu výkonu](../../../docs/framework/windows-workflow-foundation/media/performancedata.gif "objektů PerformanceData")  
  
 ![Graf výkonu testovací Data](../../../docs/framework/windows-workflow-foundation/media/performancetestchart.gif "PerformanceTestChart")  
  
 Všechny testy se měří v pracovních postupech za sekundu s výjimkou test oboru transakce.  Jak je vidět výše, [!INCLUDE[wf1](../../../includes/wf1-md.md)] napříč Tabule, hlavně v oblastech, které vyžadují více spuštěních se stejná aktivita jako chvíli je vylepšený výkon modulu runtime smyčky.  
  
## <a name="service-composition-scenario"></a>Scénář složení služby  
 Jak je znázorněno v předchozí části, "porovnání výkonu úrovni součástí," došlo k výraznému snížení režie mezi WF3 a WF4.  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby pracovních postupů může nyní téměř odpovídat výkon programového ruční [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služeb i nadále však mají všechny výhody [!INCLUDE[wf1](../../../includes/wf1-md.md)] modulu runtime.  Tento scénář testovací porovná [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby proti [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby pracovního postupu v WF4.  
  
### <a name="online-store-service"></a>Služba online úložiště  
 Jednou z výhod modelu Windows Workflow Foundation je schopnost tvoří procesů pomocí několika služeb.  V tomto příkladu je služby online úložiště, které orchestrují dvě volání služby k nákupu pořadí.  Prvním krokem je ověřit pomocí služby ověřování pořadí pořadí.  Druhým krokem je k vyplnění pořadí pomocí služby skladu.  
  
 Dvě služby back-end pořadí ověřování služby a služby skladu, zůstávají stejné pro oba testy.  Část, která se změní je Online služba úložiště, která provádí orchestration.  V jednom případě služba je ruční programového jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby.  V případech, služba je zapsána jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby pracovního postupu v WF4. [!INCLUDE[wf1](../../../includes/wf1-md.md)]-specifické funkce, jako jsou sledování a trvalost jsou vypnuté pro tento test.  
  
### <a name="environment"></a>Prostředí  
 ![Pracovní postup prostředí pro testování výkonu](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
 Ke službě Online úložiště prostřednictvím protokolu HTTP z několika počítačů jsou vytvářeny požadavky klienta.  Jeden počítač hostuje všechny tři služby.  Přenosová vrstva mezi Online úložiště služby a služby back-end je TCP nebo HTTP.  Měření operací za sekundu je založena na počtu dokončené `PurchaseOrder` volání provedená do Online služby úložiště.  Sdružování kanál je nová funkce v WF4 k dispozici.  V [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] část sdružování kanál tento test není zadaný ihned, tak na straně programového Implementace jednoduchého technika sdružování byl použit v Online službě úložiště.  
  
### <a name="performance"></a>Výkon  
 ![Graf výkonu služby online úložiště](../../../docs/framework/windows-workflow-foundation/media/onlinestoreperfgraph.gif "OnlineStorePerfGraph")  
  
 Připojování k back-end TCP služby bez sdružování kanál, [!INCLUDE[wf1](../../../includes/wf1-md.md)] služby má 17.2 % dopad na propustnost.  Sdružování kanál, snížení je přibližně 23,8 %.  Pro protokol HTTP, dopad je mnohem menší: % 4.3 bez sdružování a 8.1 % sdružování.  Je také důležité si uvědomit, že kanál sdružování poskytuje velmi málo výhodné při použití protokolu HTTP.  
  
 Zatímco režie z modulu runtime WF4 v porovnání s ruční programového [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby v tomto testu, se může považovat za nejhoršího.  Tyto dvě služby back-end v tento test provést uživatele příliš mnoho zásahů.  Ve scénáři skutečných začátku do konce by tyto služby provedl nákladnější operací, jako je volání databáze, což dopad na výkon z přenosové vrstvy méně důležité.  To plus výhod funkcí dostupných ve WF4 díky přijatelná volba pro vytváření služeb orchestration Workflow Foundation.  
  
## <a name="key-performance-considerations"></a>Faktory ovlivňující výkon klíče  
 Oblasti funkcí v této části, s výjimkou zprostředkovatel komunikace s objekty, výrazně změnily mezi WF3 a WF4.  Tato akce ovlivní návrhu aplikace pracovního postupu, jakož i výkon.  
  
#### <a name="workflow-activation-latency"></a>Pracovní postup aktivace latence  
 V [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikace služby pracovního postupu, je důležité, protože může být blokování latence pro spuštění nového pracovního postupu nebo načítání existující pracovního postupu.  Tento testovací případ opatření proti WF4 XAMLX hostitele v Typický scénář hostitel WF3 XOML.  
  
##### <a name="environment-setup"></a>Nastavení prostředí  
 ![Nastavení prostředí pro testování latence a propustnosti](../../../docs/framework/windows-workflow-foundation/media/latencyandthroughputenvironment.gif "LatencyAndThroughputEnvironment")  
  
##### <a name="test-setup"></a>Nastavení testu  
 Ve scénáři, kontakty klientské počítače [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] služby pracovního postupu pomocí korelace na základě kontextu.  Korelace kontextové vyžaduje speciální kontextu vazby a pomocí kontextu hlavičky nebo soubor cookie se týkají zprávy k instanci pracovního postupu správné.  Má výkonu využívat v tom, že korelace, které Id se nachází v záhlaví zprávy, takže není nutné analyzovat tělo zprávy. Další informace o kontextu korelace najdete v části [korelace kontextové výměny](../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)  
  
 Služba bude vytvoření nového pracovního postupu s požadavkem a odeslat okamžitou reakci, takže měření latence nezahrnuje času stráveného při spuštění pracovního postupu.  Pracovní postup WF3 je XOML s kódu na pozadí a je zcela v pracovním postupu WF4 XAML.  Pracovní postup WF4 vypadá takto:  
  
 ![Obor 4 korelace WF](../../../docs/framework/windows-workflow-foundation/media/correlationscopeworkflow.gif "CorrelationScopeWorkflow")  
  
 <xref:System.ServiceModel.Activities.Receive> Aktivity vytvoří instanci pracovního postupu.  Hodnota předaná přijaté zprávy je opakována v odpovědi.  Sekvence následující odpovědi obsahuje rest pracovního postupu.  V případě výše uvedené se zobrazí pouze jeden komentář aktivity.  Počet aktivit, komentář se změní na simulovat složitost pracovního postupu.  Komentář aktivity je ekvivalentní WF3 <xref:System.Workflow.Activities.CodeActivity> který provede žádné kroky. Další informace o aktivitě komentář najdete v části "porovnání výkonu úrovni součástí" dříve v tomto článku.  
  
##### <a name="test-results"></a>Výsledky testů  
 ![Latence výsledky](../../../docs/framework/windows-workflow-foundation/media/latencyresultsgraph.gif "LatencyResultsGraph")  
  
 Obrázek 3 – studených a tedy latence pro pracovní postup služby WCF  
  
 V tomto grafu výše, uloží málo používaná data odkazuje tento případ níž se nachází, není existující <xref:System.ServiceModel.WorkflowServiceHost> pro daný pracovní postup.  Studené latence je jinými slovy, když pracovní postup se používá první a XOML nebo XAML, musí být zkompilovány.  Záložním latence je čas vytvořit novou instanci pracovního postupu, když typ pracovního postupu je již kompilovaná.  Složitost pracovního postupu způsobuje velmi malé rozdíly v případě, že WF4, ale má lineární postupu v případě, že WF3.  
  
#### <a name="correlation-throughput"></a>Propustnost korelace  
 WF4 zavádí novou funkci korelace na základě obsahu.  WF3 k dispozici pouze na základě kontextu korelace.  Korelace na základě kontextu může provést jenom prostřednictvím konkrétní [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] kanálu vazby.  Při použití těchto vazeb, vloží se Id pracovního postupu do záhlaví zprávy.  Modul runtime WF3 by šlo identifikovat pouze pracovní postup pomocí jeho Id.  S korelace na základě obsahu Autor pracovního postupu můžete vytvořit klíč mimo relevantní část dat, jako je číslo účtu nebo zákazníků ID korelace Další informace o korelace na základě obsahu naleznete v části [korelace na základě obsahu](../../../docs/framework/wcf/feature-details/content-based-correlation.md).  
  
 Korelace na základě kontextu má výhody výkonu v tomto klíči korelace se nachází v záhlaví zprávy.  Klíče může číst ze zprávy bez deaktivuje-serialization/zpráva kopírování.  V korelace na základě obsahu korelace klíč uložen v textu zprávy.  Výraz XPath je používaná k nalezení klíč.  Náklady na další zpracování, závisí na velikosti zprávy, hloubku klíče v těle a počet klíčů.  Tento test porovná korelace na základě kontextu a obsahu a také ukazuje snížení výkonu při použití více klíčů.  
  
#### <a name="environment-setup"></a>Nastavení prostředí  
 ![Pracovní postup prostředí pro testování výkonu](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
#### <a name="test-setup"></a>Nastavení testu  
 ![Korelace propustnost pracovní postup Test](../../../docs/framework/windows-workflow-foundation/media/correlationthroughputworkflow.gif "CorrelationThroughputWorkflow")  
  
 Pracovní postup uvedené výše je stejný jako ten, používá v níže uvedené části "Trvalost".  Pro testy korelace bez trvalost není žádný zprostředkovatel trvalost nainstalován v modulu runtime.  Korelace dojde na dvou místech: CreateOrder a CompleteOrder.  
  
#### <a name="test-results"></a>Výsledky testů  
 ![Korelace propustnost](../../../docs/framework/windows-workflow-foundation/media/correlationthroughputgraph.gif "CorrelationThroughputGraph")  
  
 Tento graf znázorňuje k poklesu výkonu jako počet klíčů používaných v zvyšuje korelace na základě obsahu.  Podobnost v křivek mezi TCP a HTTP označuje režie spojená s tyto protokoly.  
  
#### <a name="correlation-with-persistence"></a>Korelace s trvalost  
 V pracovním postupu trvalou zatížení procesoru z korelace na základě obsahu posune z modulu runtime pracovního postupu k databázi SQL.  Uložené procedury ve zprostředkovateli trvalost SQL práci odpovídající klíče najít odpovídající pracovní postup.  
  
 ![Korelace a trvalost výsledků](../../../docs/framework/windows-workflow-foundation/media/correlationandpersistencegraph.gif "CorrelationAndPersistenceGraph")  
  
 Korelace na základě kontextu je stále rychlejší než korelace na základě obsahu.  Rozdíl je ale, že menší vyslovováno jako trvalost má další dopad na výkon než korelace.  
  
### <a name="complex-workflow-throughput"></a>Komplexní pracovní postup propustnost  
 Složitost pracovního postupu není měřit pouze počet aktivit.  Složené aktivity může obsahovat mnoho podřízené objekty a tyto děti může být také složené aktivity.  Jako počet úrovní vnoření zvyšuje takže nemá počet aktivit, které může být aktuálně ve spuštěném stavu a počet proměnných, které mohou být ve stavu.  Tento test porovná propustnost mezi WF3 a WF4 při provádění komplexní pracovní postupy.  
  
### <a name="test-setup"></a>Nastavení testu  
 Tyto testy byly provedeny u Intel Xeon X5355 @ 2,66 GHz 4 způsob počítače s 4 GB paměti RAM systémem Windows Server 2008 x64.  Spustí kód nástroje test v jediném procesu s jedno vlákno na jeden jádra k dosažení 100 % využití procesoru.  
  
 Pracovní postupy pro tento test generovány mít dvě hlavní proměnné: hloubkou a počet aktivit v každé pořadí.  Každá úroveň hloubky zahrnuje paralelní aktivity, při smyčky, rozhodnutí, přiřazení a pořadí.  V Návrháři WF4 následujících obrázcích je nejvyšší úrovně vývojový diagram obrázku.  Každá aktivita vývojový diagram vypadá takto: hlavní vývojový diagram.  To může být vhodné zamyslet nad fraktálový při picturing tento pracovní postup, kde je omezený na parametry testu hloubka.  
  
 Počet aktivit v dané testu je dáno hloubkou a počet aktivit na pořadí.  Následující rovnice vypočítá počet aktivit v testu WF4:  
  
 ![Rovnice vypočítat počet aktivit](../../../docs/framework/windows-workflow-foundation/media/numberofactivitiesequation.gif "NumberOfActivitiesEquation")  
  
 Počet aktivit WF3 test můžete vypočítat se mírně liší rovnice z důvodu navíc pořadí:  
  
 ![Rovnice vypočítat počet aktivit](../../../docs/framework/windows-workflow-foundation/media/w3numberofactivitiesequation.gif "W3NumberOfActivitiesEquation")  
  
 Kde d hloubka a je počet aktivit na pořadí.  Logika za tyto vzorce je, že první konstanta násobí hodnotou a, číslo sekvence a druhý konstanta je statický počet aktivit na aktuální úrovni.  Existují tři vývojový diagram podřízené aktivity v každé vývojový diagram.  Na nejnižší úrovni hloubka na jiných úrovních jsou kopie hlavní vývojový diagram však tyto vývojových diagramech jsou prázdné.  Počet aktivit v každé testovací variace definice pracovního postupu je uvedené v následující tabulce:  
  
 ![Porovná počet aktivit používaných v každém testu](../../../docs/framework/windows-workflow-foundation/media/comparechart.gif "CompareChart")  
  
 Počet aktivit v definici pracovního postupu se zvyšuje prudce s každou úroveň hloubky.  Se spustí jenom jednu cestu za kritériem při rozhodování, ale v instanci daného pracovního postupu, takže jenom malou část skutečné aktivity provedení.  
  
 ![Komplexní pracovní postup](../../../docs/framework/windows-workflow-foundation/media/complexworkflowthroughputworkflow.gif "ComplexWorkflowThroughputWorkflow")  
  
 Ekvivalentní pracovní postup byl vytvořen pro WF3. Návrhář WF3 zobrazí celý pracovní postup v oblasti návrhu místo vnoření, proto, že je příliš dlouhý pro zobrazení v tomto tématu. Fragment pracovního postupu jsou uvedeny níže.  
  
 ![WF3 Pracovní postup](../../../docs/framework/windows-workflow-foundation/media/wf3workflow.gif "WF3Workflow")  
  
 Vykonávat vnoření v extreme případě používá jiný pracovní postup, který je součástí tento test 100 vnořené pořadí.  V nejvnitřnější pořadí je jediný `Comment` nebo <xref:System.Workflow.Activities.CodeActivity>.  
  
 ![Vnořené pořadí](../../../docs/framework/windows-workflow-foundation/media/nestedsequencewf.gif "NestedSequenceWF")  
  
 Sledování a trvalost nejsou použity jako součást tento test.  
  
### <a name="test-results"></a>Výsledky testů  
 ![Diagram propustnosti](../../../docs/framework/windows-workflow-foundation/media/testresults1.gif "TestResults1")  
  
 I komplexní pracovních s mnoha hloubky a vysoký počet aktivit, výsledky výkonu jsou konzistentní s další propustnost čísla uvedené dříve v tomto článku.  Propustnost WF4 na pořadí podle velikosti je rychlejší a má být porovnána na logaritmickém měřítku.  
  
### <a name="memory"></a>Paměť  
 Nároky na paměť modelu Windows Workflow Foundation se měří v dvě klíčové oblasti: pracovní postup složitost a počet definicí pracovního postupu.  Paměť měření byly provedeny na pracovní stanici 64bitová verze Windows 7.  Existuje mnoho způsobů, jak získat měření velikost pracovní sady například monitorování čítače výkonu, dotazování Environment.WorkingSet nebo pomocí nástroje, například VMMap dostupné z [VMMap](http://technet.microsoft.com/sysinternals/dd535533.aspx). Kombinaci metod byl použit k získání a ověřte výsledky testu.  
  
### <a name="workflow-complexity-test"></a>Test složitost pracovního postupu  
 Pracovní postup složitost otestovat míry pracovní nastavena rozdíl podle složitosti pracovního postupu.  Kromě komplexní pracovní postupy použité v předchozí části, se přidají nové varianty pro dvě základní případy: jediné aktivity pracovního postupu a pořadí s aktivitami 1000.  Pro tyto testy jsou pracovní postupy inicializován a provést dokončen v jedinou smyčku. sériové po dobu jedné minuty.  Každý test variace běží třikrát a data zaznamenaná je průměr těchto tří spustí.  
  
 Dva nové základní testy mít pracovní postupy, které vypadají stejně jako vidíte níže:  
  
 ![Komplexní pracovní postupy](../../../docs/framework/windows-workflow-foundation/media/complexworkflowboth.gif "ComplexWorkflowBoth")  
  
 V pracovním postupu WF3 uvedené výše, prázdný <xref:System.Workflow.Activities.CodeActivity> aktivity se používají.  Pracovní postup WF4 výše používá `Comment` aktivity.  `Comment` Aktivita byla popsaný v části porovnání výkonu úrovni součástí výše v tomto článku.  
  
 ![Graf využití paměti](../../../docs/framework/windows-workflow-foundation/media/complexmemoryusage.gif "ComplexMemoryUsage")  
  
 Jedním z zrušte trendy Všimněte v tomto grafu je, že vnoření má poměrně minimální dopad na využití paměti v WF3 a WF4.  Nejvýraznější dopad paměti pochází z počet aktivit v daném pracovním postupu.  Vzhledem data z pořadí 1000, komplexní hloubka 5 pořadí 5 a komplexní hloubka 7 pořadí 1 variace, je zřejmé, že jako počet aktivit, zadá tisíců, nárůst využití paměti se více pozná.  V případě extrémně (hloubku 7 pořadí 1) tam, kde jsou aktivity tisíc ~ 29, WF4 používá téměř 79 % méně paměti, než je WF3.  
  
### <a name="multiple-workflow-definitions-test"></a>Více testů definice pracovního postupu  
 Měření paměť na definice pracovního postupu je rozdělena na dva různé testy z důvodu dostupné možnosti pro hostování pracovních postupů v WF3 a WF4.  Testy se spouštějí jiným způsobem než pracovní postup test složitost v, aby instance a provést pouze jednou za definice daného pracovního postupu.  Je to proto, že definice pracovního postupu a jeho hostitel zůstanou v paměti pro dobu životnosti domény aplikace.  Paměť použitá spuštěním instanci daného pracovního postupu by měla být vyčištěna během uvolňování paměti.  Migrace pokyny pro WF4 obsahuje podrobnější informace o možnosti hostování. Další informace najdete v tématu [WF migrace kuchařka: pracovní postup hostování](http://go.microsoft.com/fwlink/?LinkID=153313).  
  
 Vytváření mnoho definice pracovního postupu pro definici pracovního postupu test lze provést několika způsoby.  Například jeden pomocí generování kódu můžete vytvořit sadu 1000 pracovní postupy, které jsou stejné s výjimkou v názvu a každý z těchto pracovních postupů uložit do samostatných souborů.  Tento přístup, nebyla provedena pro test hostovaných v konzole.  V WF3 <xref:System.Workflow.Runtime.WorkflowRuntime> třída se používá ke spouštění definice pracovního postupu.  Můžete buď používat WF4 <xref:System.Activities.WorkflowApplication> k vytvoření instance jednoho pracovního postupu nebo přímo <xref:System.Activities.WorkflowInvoker> ke spuštění aktivity, jako by šlo volání metody.  <xref:System.Activities.WorkflowApplication> je hostitelem instance jednoho pracovního postupu a má blíže parity funkcí k <xref:System.Workflow.Runtime.WorkflowRuntime> tak, aby byl použit v tomto testu.  
  
 Při hostování pracovních postupů ve službě IIS je možné použít <xref:System.Web.Hosting.VirtualPathProvider> pro vytvoření nového <xref:System.ServiceModel.WorkflowServiceHost> místo aby generovala všechny soubory XAMLX nebo XOML.  <xref:System.Web.Hosting.VirtualPathProvider> Zpracuje příchozí požadavek a odpoví "virtuální soubor", lze načíst z databáze nebo, v takovém případě vytvořit za chodu.  Proto není nutné vytvořit fyzické soubory 1000.  
  
 Definice pracovního postupu v konzole testu byly jednoduchý sekvenční pracovní postupy pomocí jediné aktivity.  Jediné aktivity byl prázdnou <xref:System.Workflow.Activities.CodeActivity> pro případ WF3 a `Comment` aktivity pro případ WF4.  Tento případ hostované službou IIS použít pracovní postupy, které začínají na příjem zprávy a end na odeslání odpovědi:  
  
 ![Služby pracovních postupů v WF3 a WF4](../../../docs/framework/windows-workflow-foundation/media/receiveworkflowboth.gif "ReceiveWorkflowBoth")  
  
 Obrázek 4 – pracovní postup WF3 s ReceiveActivity a WF4 pracovního postupu pomocí vzoru požadavků a odpovědí  
  
 Následující tabulka ukazuje rozdíl v pracovní sadě mezi definici jednoho pracovního postupu a definice 1001:  
  
|Možnosti hostování|WF3 Rozdíl pracovní sady|WF4 Rozdíl pracovní sady|  
|---------------------|---------------------------|---------------------------|  
|Konzolové aplikace hostované pracovních postupů|18 MB|9 MB|  
|Služby pracovních postupů, hostovaná IIS|446 MB|364 MB|  
  
 Hostování definice pracovního postupu ve službě IIS využívá mnohem víc paměti z důvodu <xref:System.ServiceModel.WorkflowServiceHost>, podrobné [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] artefaktů služby a zpracovává logiku spojovanou s hostitelem zprávy.  
  
 Pro hostování pracovních postupů v WF3 konzolu byly implementovány v kódu místo XOML.  Ve výchozím nastavení se v WF4 použít XAML.  XAML je uložena jako vložený prostředek v sestavení a kompilované za běhu k zajištění implementace pracovního postupu.  Je některé režijní náklady spojené s tímto procesem.  Aby bylo možné správného porovnání mezi WF3 a WF4, programové pracovních používaly místo XAML.  Příklad WF4 pracovních postupů, je zobrazena níže:  
  
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
  
 Existuje mnoho dalších faktorů, které můžou ovlivnit využití paměti. Stejné Rady pro všechny spravované programy stále platí.  V prostředích IIS hostované <xref:System.ServiceModel.WorkflowServiceHost> objekt vytvořený pro definici pracovního postupu zůstává v paměti, dokud dojde k recyklování fondu aplikací.  To by měly být udržovány na paměti, při zápisu rozšíření.  Je také vhodné vyhnout "globální" proměnné (proměnné omezená na celý pracovní postup) a omezit rozsah proměnné, pokud je to možné.  
  
## <a name="workflow-runtime-services"></a>Služby modulu Runtime pracovního postupu  
  
### <a name="persistence"></a>Trvalost  
 WF3 a WF4 obě dodávají spolu s trvalost zprostředkovatele SQL.  Zprostředkovatel trvalost WF3 SQL je jednoduché implementace, který serializuje instance pracovního postupu a ukládá je do objektu BLOB.  Z tohoto důvodu výkon tohoto zprostředkovatele výraznou závisí na velikosti k instanci pracovního postupu.  V WF3 může zvýšit velikost instance z mnoha důvodů, jak je popsané dříve v tomto dokumentu.  Mnoho zákazníků rozhodnout použít výchozího poskytovatele trvalost SQL, protože ukládání serializovaných instance v databázi poskytuje žádné přehled o stavu pracovního postupu.  Chcete-li vyhledat konkrétní pracovní postup bez znalosti id pracovního postupu, jeden musel deserializovat každou trvalou instanci a zkontrolujte obsah.  Zápis vlastních poskytovatelů trvalost k překonání tuto překážku přednost tomu celá řada vývojářů.  
  
 Zprostředkovatel trvalost WF4 SQL se pokusila některé tyto problémy vyřešit.  V tabulkách trvalost vystavit určité informace, jako je active záložky a možné zvýšit vlastnosti.  Nová funkce korelace na základě obsahu v WF4 nebude provádět i pomocí přístup trvalost WF3 SQL, kde má řízené některé změny v organizaci k instanci pracovního postupu trvalý.  To usnadňuje složitější úlohy zprostředkovatele trvalosti a vloží navíc přízvuk v databázi.  
  
### <a name="environment-setup"></a>Nastavení prostředí  
 ![Pracovní postup prostředí pro testování výkonu](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
### <a name="test-setup"></a>Nastavení testu  
 I když sada vylepšené funkcí a lepší souběžnosti zpracování je rychlejší než zprostředkovatele v WF3 trvalost zprostředkovatele SQL v WF4.  K prezentují to, jsou dva pracovní postupy, které provádějí v podstatě stejné operace v WF3 a WF4 porovná níže.  
  
 ![Trvalost pracovních](../../../docs/framework/windows-workflow-foundation/media/persistworkflow.gif "PersistWorkflow")  
  
 Obrázek 5 – pracovní postup trvalost v WF3 na levé a WF4 vpravo  
  
 Oba dva pracovní postupy jsou vytvořené pomocí přijaté zprávy.  Po odeslání počáteční odpovědět, je trvalé pracovního postupu.  V případě WF3 prázdnou <xref:System.Workflow.ComponentModel.TransactionScopeActivity> se použilo k zahájení trvalost.  Stejné by mohl dosáhnout WF3 označením aktivitu jako "zachovat při zavření."  Druhý, korelační zpráva dokončení pracovního postupu.  Pracovní postupy jsou nastavené jako trvalé, ale není odpojeno.  
  
### <a name="test-results"></a>Výsledky testů  
 ![Propustnost trvalost](../../../docs/framework/windows-workflow-foundation/media/throughputpersistence.gif "ThroughputPersistence")  
  
 Při přenosu mezi klientem a střední vrstvy, je HTTP, zobrazuje trvalost v WF4 zlepšení 2.6 časy.  Přenos TCP zvyšuje faktor 3.0 časy.  Ve všech případech je využití procesoru na střední vrstvě 98 % nebo vyšší.  Z důvodu, že WF4 propustnost je větší je z důvodu rychlejší modulu runtime pracovního postupu.  Velikost serializovaných instance je nízké obou případech a není hlavní přispívajících element v této situaci.  
  
 WF3 i WF4 pracovní postupy v tomto testu použít aktivitu do explicitně o tom, kdy má dojít k trvalost.  To má výhodu setrvání pracovního postupu bez uvolnění ho.  V WF3, je také možné zachovat pomocí <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> funkce, ale uvolní instanci pracovního postupu z paměti.  Pokud vývojář pomocí WF3 chce Ujistěte se, že pracovní postup přetrvává v určitých bodech, budou mít buď alter definice pracovního postupu nebo zaplacení náklady pro uvolnění a znovu načítání instance pracovního postupu.  Nová funkce v WF4 umožňuje zachovat bez uvolnění: <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>.  Tato funkce umožňuje k instanci pracovního postupu na nastavit jako trvalý v nečinnosti, ale zůstane paměť, dokud <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> dosáhla prahová hodnota nebo provedení obnovení.  
  
 Pamatujte, že zprostředkovatel trvalost WF4 SQL další práci v databázové vrstvy.  Databáze SQL se může stát úzkým místem, je důležité monitorovat existuje využití procesoru a disku.  Nezapomeňte zahrnout následující čítače výkonu z SQL databáze při testování pracovního postupu aplikace výkonu:  
  
-   Fyzický disk\\čas čtení disku %  
  
-   Fyzický disk\\% času disku  
  
-   Fyzický disk\\disku % času zápisu  
  
-   Fyzický disk\\% střední Délka fronty disku  
  
-   Fyzický. Délka fronty disku pro čtení  
  
-   Fyzický. Délka fronty disku zápisu  
  
-   Délka fronty disku PhysicalDisk\Current  
  
-   Informace o procesoru\\% času procesoru  
  
-   Doba čekání západky SQLServer:Latches\Average (ms)  
  
-   SQLServer:Latches\Latch počká za sekundu  
  
### <a name="tracking"></a>Sledování  
 Pracovní postup sledování umožňuje sledovat průběh pracovního postupu.  Informace, které je součástí sledování událostí je určen podle profil sledování.  Složitější profilem sledování nákladnější sledování se změní.  
  
 WF3 dodávané se službou sledování na základě SQL.  Tato služba může fungovat v režimech dávkové a jiných-zpracovat v dávce.  V režimu bez-zpracovat v dávce sledování událostí se zapisují přímo do databáze.  V režimu dávkové sledování událostí se shromažďují do dávky stejné jako stav instance pracovního postupu.  Dávkové režim má nejlepší výkon pro širokou škálu návrhů pracovního postupu.  Dávkování však může mít negativním dopadem na výkon Pokud pracovní postup spouští řada aktivit bez zachování a tyto aktivity jsou sledovány.  To by běžně se stalo v smyčky a nejlepší způsob, jak se vyhnout tento scénář je k návrhu velké smyčky tak, aby obsahovala bod trvalost.  Úvod do smyčky bod trvalost může mít nepříznivý vliv i výkon, proto je důležité pro měření náklady na jednotlivých a spolu rovnováhu.  
  
 WF4 není součástí SQL služby pro sledování.  Záznam informace o sledování k databázi SQL může být zpracovává lépe ze serveru aplikace nemusí součástí [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. Proto sledování SQL je nyní provádí AppFabric.  Zprostředkovatel sledování se na pole v WF4 je založena na trasování událostí pro Windows (ETW).  
  
 Trasování událostí pro Windows je systém jádra úroveň, s nízkou latencí událostí součástí systému Windows.  Používá zprostředkovatele nebo příjemce model, který umožňuje pouze způsobit snížení pro trasování událostí, pokud je ve skutečnosti příjemce.  Kromě události kernel například procesoru, disku, paměť a využití sítě mnoho aplikací také využívají trasování událostí pro Windows.  Události trasování událostí pro Windows jsou výkonnější než čítače výkonu v této události lze přizpůsobit k aplikaci.  Událost může obsahovat text například ID pracovního postupu nebo informační zpráva.  Navíc události jsou klasifikovány s bitovou masku tak, aby využívání určité podmnožiny události bude mít menší dopad na výkon než zaznamenávání všechny události.  
  
 Výhody tohoto přístupu pomocí trasování událostí pro Windows pro sledování místo SQL patří:  
  
-   Kolekce sledování událostí je možné oddělit k jinému procesu.  To dává větší flexibilitu v tom, jak události se zaznamenávají.  
  
-   Události trasování sledování událostí snadno spolu se [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] trasování událostí nebo jiných zprostředkovatelů trasování událostí pro Windows, např. zprostředkovatele SQL Server nebo jádra.  
  
-   Autoři pracovního postupu, není potřeba změnit pracovní postup lépe pracovat s konkrétní sledování provádění, například službu sledování WF3 SQL dávkovém režimu.  
  
-   Správce může povolit sledování zapnout nebo vypnout bez recyklace procesu hostitele.  
  
 Výhody výkonu pro sledování trasování událostí pro Windows jsou součástí nevýhodou.  Pokud systém je přetížena intenzivního prostředků, může dojít ke ztrátě událostí trasování událostí pro Windows.  Zpracování událostí není určena pro blokování spuštění normální programu a proto není zaručeno, že se všechny události trasování událostí pro Windows jejich odběratelům všesměrového vysílání.  Díky tomu sledování ETW výborně hodí pro sledování stavu, ale není vhodný pro auditování.  
  
 Při WF4 nemá sledování zprostředkovatele SQL, nemá AppFabric.  Přístup sledování SQL na AppFabric je přihlásit k odběru událostí trasování událostí pro Windows pomocí služby systému Windows, který dávek události a zapisuje je do tabulky SQL určený pro rychlé vložení.  Samostatná úloha odstraňuje data z této tabulky a reforms do tabulky, které lze zobrazit na řídicím panelu AppFabric sestav.  To znamená, zpracovává nezávislé pracovního postupu ho pochází a proto nemusí čekat na bod trvalost před zápisem dávky sledování událostí.  
  
 Nástroje, například logman nebo xperf můžete zaznamenat události trasování událostí.  Soubor compact ETL můžete převést do čitelnějšího formátu, například XML, s tracerpt nebo zobrazit pomocí některého nástroje, například xperfview.  Jedinou možností pro získání sledování událostí bez databáze SQL WF3, je vytvoření vlastní sledování služby. Další informace o trasování událostí pro Windows najdete v tématu [služby WCF a trasování událostí pro Windows](../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) a [trasování událostí pro Windows](http://msdn.microsoft.com/library/ff190903.aspx\)).  
  
 Povolení sledování workflowu bude mít dopad na výkon v různých stupňů.  Níže srovnávacího testu používá nástroj logman k využívat trasování sledování událostí a zapisuje je do souboru ETL.  Náklady na sledování v AppFabric SQL není v oboru tohoto článku.  Profil základní sledování, používat i v AppFabric, se zobrazí v této srovnávacího testu.  Také zahrnuty jsou náklady na sledování jenom události sledování stavu.  Tyto události jsou užitečné pro řešení problémů a určení, průměrná propustnost systému.  
  
### <a name="environment-setup"></a>Nastavení prostředí  
 ![Pracovní postup prostředí pro testování výkonu](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
### <a name="test-results"></a>Výsledky testů  
 ![Pracovní postup trasování náklady](../../../docs/framework/windows-workflow-foundation/media/workflowtracingcost.gif "WorkflowTracingCost")  
  
 Sledování stavu zhruba má 3 % dopad na propustnost.  Náklady na základní profil je přibližně 8 %.  
  
## <a name="interop"></a>Zprostředkovatel komunikace s objekty  
 WF4 je téměř dokončena přepisování z [!INCLUDE[wf1](../../../includes/wf1-md.md)] a proto nejsou přímo kompatibilní s WF4 WF3 pracovních postupů a aktivit.  Mnoho zákazníků, které již v rané fázi přijaly modelu Windows Workflow Foundation, bude mít pro WF3 definice pracovního postupu interní nebo třetích stran a vlastní aktivity.  Jedním ze způsobů k usnadnění přechodu na WF4 je pomocí zprostředkovatele komunikace s objekty aktivity, které můžete provést WF3 aktivitám v pracovním postupu WF4.  Dále je doporučeno <xref:System.Activities.Statements.Interop> aktivity použít pouze v případě potřeby. Další informace o migraci na WF4 podívejte se [WF4 migrace pokyny](http://go.microsoft.com/fwlink/?LinkID=153313).  
  
### <a name="environment-setup"></a>Nastavení prostředí  
 ![Pracovní postup prostředí pro testování výkonu](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
### <a name="test-results"></a>Výsledky testů  
 Následující tabulka ukazuje výsledky spuštění pracovního postupu obsahující pět aktivity v pořadí, v různých konfiguracích.  
  
|Test|Propustnost (pracovních za sekundu)|  
|----------|-----------------------------------|  
|Pořadí WF3 v WF3 runtime|1,576|  
|Pořadí WF3 v WF4 runtime pomocí zprostředkovatele komunikace|2,745|  
|WF4 pořadí|153,582|  
  
 Je zvýšení výkonu upozorňují na důležité k pomocí zprostředkovatele komunikace přes přímých WF3.  Pokud však porovná WF4 aktivity, zvýšení nebude nepatrné.  
  
## <a name="summary"></a>Souhrn  
 Velkou investice do výkon WF4 mít placené v mnoha oblastech zásadní.  Výkon součásti jednotlivých pracovního postupu se v některých případech stovky rychlejší v porovnání s WF3 kvůli leaner WF4 [!INCLUDE[wf1](../../../includes/wf1-md.md)] modulu runtime.  Latence čísla jsou také výrazně lepší.  To znamená snížení výkonu pro používání [!INCLUDE[wf1](../../../includes/wf1-md.md)] oproti ruční kódování [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] orchestration services je velmi malé zvažování přidané výhody použití [!INCLUDE[wf1](../../../includes/wf1-md.md)].  Trvalost výkonu zvýšilo faktorem 2.5 3.0.  Monitorování stavu prostřednictvím pracovního postupu pro sledování teď má velmi malé režijní náklady.  Komplexní sadu příručkách pro migraci jsou k dispozici pro ty, které jsou s přesun z WF3 na WF4.  Všechny tyto měli WF4 atraktivní možnost pro psaní komplexních aplikací.  
  
## <a name="acknowledgements"></a>Potvrzení  
 Mnoho díky následující přispěvatelé a recenzenti pro jejich úsilí:  
  
-   Leon Welicki společnost Microsoft Corporation  
  
-   Ryszard Kwiecinski, Microsoft Corporation.  
  
-   Emil Velinov společnost Microsoft Corporation  
  
-   Jan Talbert společnost Microsoft Corporation  
  
-   Bob Schmidt společnost Microsoft Corporation  
  
-   Stefan Batres společnost Microsoft Corporation
