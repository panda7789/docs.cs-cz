---
title: Proces náboru
ms.date: 03/30/2017
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
ms.openlocfilehash: ade72422d29d170e9c80f602f151ce765a1a00f7
ms.sourcegitcommit: e48a54ebe62e874500a7043f6ee0b77a744d55b4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2020
ms.locfileid: "80291685"
---
# <a name="hiring-process"></a>Proces náboru
Tato ukázka ukazuje, jak implementovat obchodní proces pomocí zasílání zpráv aktivity a dva pracovní postupy hostované jako služby pracovního postupu. Tyto pracovní postupy jsou součástí IT infrastruktury fiktivní společnosti contoso, Inc.  
  
 Proces `HiringRequest` pracovního postupu <xref:System.Activities.Statements.Flowchart>(implementovaný jako ) požádá o autorizaci od několika manažerů v organizaci. K dosažení tohoto cíle pracovní postup používá další existující služby v organizaci (v našem případě služby doručené pošty a organizační datové služby implementované jako běžné služby Windows Communication Foundation (WCF).  
  
 Pracovní `ResumeRequest` postup (implementovaný jako <xref:System.Activities.Statements.Sequence>) publikuje pracovní pozici na externím webu společnosti Contoso a spravuje získávání životopisů. Zaúčtování projektu je k dispozici na externím webu po pevně stanovenou dobu (do vypršení časového limitu) nebo dokud se zaměstnanec společnosti Contoso nerozhodne jej odebrat.  
  
 Tento vzorek ukazuje následující [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]vlastnosti :  
  
- <xref:System.Activities.Statements.Flowchart>a <xref:System.Activities.Statements.Sequence> pracovní postupy pro modelování obchodních procesů.  
  
- Služby pracovního postupu.  
  
- Aktivity zasílání zpráv.  
  
- Korelace založená na obsahu.  
  
- Vlastní aktivity (deklarativní a založené na kódu).  
  
- Trvalosti serveru SQL poskytovanésystémem.  
  
- Vlastní <xref:System.Activities.Persistence.PersistenceParticipant>.  
  
- Vlastní sledování.  
  
- Sledování událostí pro sledování systému Windows (ETW).  
  
- Složení činností.  
  
- <xref:System.Activities.Statements.Parallel>Činnosti.  
  
- <xref:System.Activities.Statements.CancellationScope>Činnosti.  
  
- Trvalé časovače<xref:System.Activities.Statements.Delay> (aktivita).  
  
- Transakce.  
  
- Více než jeden pracovní postup ve stejném řešení.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>Popis procesu  
 Contoso, Inc. chce mít úzkou kontrolu nad počtem zaměstnanců v každém ze svých oddělení. Proto kdykoli však chce zaměstnanec zahájit nový proces náboru, musí projít schválením procesu žádosti o přijetí, než k náboru skutečně dojde. Tento proces se nazývá požadavek procesu náboru (definovaný v projektu HiringRequestService) a skládá se z následujících kroků:  
  
1. Zaměstnanec (žadatel) spustí žádost o proces náboru.  
  
2. Vedoucí žádosti musí žádost schválit:  
  
    1. Vedoucí může žádost odmítnout.  
  
    2. Vedoucí může vrátit požadavek žadateli pro další informace:  
  
        1. Žadatel zkontroluje a odešle požadavek zpět manažerovi.  
  
    3. Manažer může schválit.  
  
3. Poté, co vedoucí uchazeče schválí, musí vlastník oddělení žádost schválit:  
  
    1. Majitel oddělení může odmítnout.  
  
    2. Majitel oddělení může schválit.  
  
4. Poté, co vlastník oddělení schválí, proces vyžaduje schválení 2 HR manažerů nebo generálního ředitele:  
  
    1. Proces může přejít do přijatého nebo odmítnutého stavu.  
  
    2. Pokud je proces přijat, je `ResumeRequest` spuštěna nová`ResumeRequest` instance pracovního postupu (je propojena s HiringRequest.csproj prostřednictvím odkazu na službu.)  
  
 Jakmile manažeři schválí přijetí nového zaměstnance, hr musí najít vhodného kandidáta. Tento proces se provádí druhý`ResumeRequest`pracovní postup ( , definované v ResumeRequestService.csproj). Tento pracovní postup definuje proces odesílání pracovního místa s kariérní příležitostí na externí web Kariéra společnosti Contoso, přijímá životopisy od uchazečů a sleduje stav pracovního příspěvku. Pozice jsou k dispozici na dobu určitou (do uplynutí doby) nebo dokud se zaměstnanec společnosti Contoso nerozhodne je odebrat. Pracovní `ResumeRequest` postup se skládá z následujících kroků:  
  
1. Zaměstnanec společnosti Contoso zadá informace o pozici a době trvání časového plánu. Jakmile zaměstnanec zadá v těchto informacích, pozice je zaúčtována na webu Kariéra.  
  
2. Jakmile jsou informace zveřejněny, mohou zúčastněné strany předložit své životopisy. Po odeslání je životopis uložen v záznamu propojeném s otevřením úlohy.  
  
3. Žadatelé mohou odeslat životopisy, dokud nevyprší časový limit nebo se někdo z personálního oddělení společnosti Contoso výslovně rozhodne zrušit účtování zastavením procesu.  
  
## <a name="projects-in-the-sample"></a>Projekty ve vzorku  
 V následující tabulce jsou uvedeny projekty v ukázkovém řešení.  
  
|Project|Popis|  
|-------------|-----------------|  
|Společnost ContosoHR|Obsahuje kontrakty dat, obchodní objekty a třídy úložiště.|  
|Služba HiringRequestService|Obsahuje definici pracovního postupu procesu žádosti o přijetí.<br /><br /> Tento projekt je implementován jako konzolová aplikace, která sama hostuje pracovní postup (soubor xaml) jako službu.|  
|Služba ResumeRequestService|Služba pracovního postupu, která shromažďuje životopisy od kandidátů, dokud nevyprší časový limit nebo se někdo nerozhodne, že proces musí být zastaven.<br /><br /> Tento projekt je implementován jako deklarativní služba pracovního postupu (xamlx).|  
|Služba OrgService|Služba, která zveřejňuje informace o organizaci (zaměstnanci, pozice, PositionTypes a oddělení). Tuto službu si můžete myslet jako modul Organizace společnosti plánu ERP (Enterprise Resource Plan).<br /><br /> Tento projekt je implementován jako konzolová aplikace, která zveřejňuje službu WCF (Windows Communication Foundation).|  
|Služba Doručená pošta|Doručená pošta, která obsahuje užitečné úkoly pro zaměstnance.<br /><br /> Tento projekt je implementován jako konzolová aplikace, která zveřejňuje službu WCF.|  
|Interní klient|Webová aplikace pro interakci s procesem. Uživatelé mohou spouštět, účastnit se a zobrazit své pracovní postupy procesu náboru. Pomocí této aplikace mohou také spustit a sledovat procesy ResumeRequest.<br /><br /> Tato stránka je implementována tak, aby byla interní v intranetu společnosti Contoso. Tento projekt je implementován jako ASP.NET webu.|  
|CareersWebSite|Externí web, který zveřejňuje otevřené pozice v aplikaci Contoso. Každý potenciální kandidát může přejít na tento web a odeslat životopis.|  
  
## <a name="feature-summary"></a>Shrnutí funkce  
 Následující tabulka popisuje, jak se jednotlivé funkce používají v této ukázce.  
  
|Funkce|Popis|Project|  
|-------------|-----------------|-------------|  
|Vývojový diagram|Obchodní proces je reprezentován jako vývojový diagram . Tento popis vývojového diagramu představuje proces stejným způsobem, ve kterém by podnik nakreslil na tabuli.|Služba HiringRequestService|  
|Služby pracovního postupu|Vývojový diagram s definicí procesu je hostován ve službě (v tomto příkladu je služba hostována v konzolové aplikaci).|Služba HiringRequestService|  
|Aktivity zasílání zpráv|Vývojový diagram používá aktivity zasílání zpráv dvěma způsoby:<br /><br /> - Chcete-li získat informace od uživatele (přijímat rozhodnutí a související informace v každém kroku schválení).<br />- Pro interakci s jinými existujícími službami (InboxService a OrgDataService, používané prostřednictvím odkazů na služby).|Služba HiringRequestService|  
|Korelace založená na obsahu|Zprávy o schválení korelují s vlastností ID žádosti o přijetí:<br /><br /> - Při spuštění procesu je popisovač korelace inicializován id požadavku.<br />- Příchozí schvalovací zprávy korelují s jejich ID (prvním parametrem každé zprávy o schválení je ID požadavku).|NáborRequestService / ResumeRequestService|  
|Vlastní aktivity (deklarativní a založené na kódu)|V této ukázce je několik vlastních aktivit:<br /><br /> -   `SaveActionTracking`: Tato aktivita <xref:System.Activities.Tracking.TrackingRecord> vydává <xref:System.Activities.NativeActivityContext.Track%2A>vlastní (pomocí). Tato aktivita byla vytvořena pomocí <xref:System.Activities.NativeActivity>imperativního rozšíření kódu .<br />-   `GetEmployeesByPositionTypes`: Tato aktivita obdrží seznam ID typu pozice a vrátí seznam osob, které mají tuto pozici v Contoso. Tato aktivita byla napsána deklarativně (pomocí návrháře aktivit).<br />-   `SaveHiringRequestInfo`: Tato aktivita ukládá `HiringRequest` informace `HiringRequestRepository.Save`(pomocí). Tato aktivita byla vytvořena pomocí <xref:System.Activities.CodeActivity>imperativního rozšíření kódu .|Služba HiringRequestService|  
|Trvalosti serveru SQL Server poskytovaného systémem|Instance, <xref:System.ServiceModel.Activities.WorkflowServiceHost> která je hostitelem definice procesu vývojového diagramu, je nakonfigurována tak, aby používala trvalost serveru SQL Server poskytovaného systémem.|NáborRequestService / ResumeRequestService|  
|Vlastní sledování|Ukázka obsahuje vlastní účastníksledování, který ukládá `HiringRequestProcess` historii (to zaznamenává, jaká akce byla provedena, kým a kdy). Zdrojový kód je ve složce Sledování HiringRequestService.|Služba HiringRequestService|  
|Sledování ETW|Systémem poskytované Sledování ETW je konfigurováno v souboru App.config ve službě HiringRequestService.|Služba HiringRequestService|  
|Složení činností|Definice procesu používá volné <xref:System.Activities.Activity>složení . Vývojový diagram obsahuje několik sequence a paralelní aktivity, které současně obsahují další aktivity (a tak dále).|Služba HiringRequestService|  
|Paralelní aktivity|-   <xref:System.Activities.Statements.ParallelForEach%601>se používá k paralelní registraci do složky Inbox generálního ředitele a hr manažerů (čekání na dva kroky schválení HR manažerů).<br />-   <xref:System.Activities.Statements.Parallel>Se používá k některým úkolům čištění v krocích Dokončeno a Odmítnuto|Služba HiringRequestService|  
|Zrušení modelu|Vývojový diagram <xref:System.Activities.Statements.CancellationScope> používá k vytvoření zrušení chování (v tomto případě to dělá některé vyčištění.)|Služba HiringRequestService|  
|Účastník trvalosti zákazníka|`HiringRequestPersistenceParticipant`ukládá data z proměnné pracovního postupu do tabulky uložené v databázi Contoso HR.|Služba HiringRequestService|  
|Služby pracovních postupů|`ResumeRequestService`implementována pomocí služeb pracovního postupu. Definice pracovního postupu a informace o službě jsou obsaženy v souboru ResumeRequestService.xamlx. Služba je nakonfigurována tak, aby používala trvalost a sledování.|Služba ResumeRequestService|  
|Odolné časovače|`ResumeRequestService`používá trvalé časovače k definování doby trvání zaúčtování projektu (jakmile vyprší časový limit, je účtování projektu uzavřeno).|Služba ResumeRequestService|  
|Transakce|<xref:System.Activities.Statements.TransactionScope>se používá k zajištění konzistentnosti dat v rámci provádění několika činností (při přijetí nového životopisu).|Služba ResumeRequestService|  
|Transakce|Vlastní účastník trvalosti`HiringRequestPersistenceParticipant`( ) a`HistoryFileTrackingParticipant`vlastní účastník sledování ( ) používají stejnou transakci.|Služba HiringRequestService|  
|Použití [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v ASP.NET aplikacích.|Pracovní postupy jsou přístupné ze dvou aplikací ASP.NET.|Interníklient / CareersWebSite|  
  
## <a name="data-storage"></a>Úložiště dat  
 Data jsou uložena v `ContosoHR` databázi SERVERU SQL Server s `DbSetup` názvem (skript pro vytvoření této databáze je umístěn ve složce). Instance pracovního postupu jsou uloženy `InstanceStore` v databázi serveru SQL Server s [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] názvem (skripty pro vytvoření úložiště instancí jsou součástí distribuce).  
  
 Obě databáze jsou vytvořeny spuštěním skriptu Setup.cmd z příkazového řádku pro vývojáře pro sady Visual Studio.  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
  
#### <a name="to-create-the-databases"></a>Vytvoření databází  
  
1. Otevřete příkazový řádek pro vývojáře pro Visual Studio.  
  
2. Přejděte do složky s ukázkou.  
  
3. Spusťte soubor Setup.cmd.  
  
4. Ověřte, zda `ContosoHR` `InstanceStore` byly dvě databáze a byly vytvořeny v aplikaci SQL Express.  
  
#### <a name="to-set-up-the-solution-for-execution"></a>Nastavení řešení pro spuštění  
  
1. Spusťte sadu Visual Studio jako správce. Otevřít soubor HiringRequest.sln.  
  
2. Klepněte pravým tlačítkem myši na řešení v **Průzkumníku řešení** a vyberte **příkaz Vlastnosti**.  
  
3. Vyberte možnost **Více projektů po spuštění** a nastavte na **start** **služby CareersWebSite**, **InternalClient**, **HiringRequestService**a **ResumeRequestService** . Ponechejte **ContosoHR**, **InboxService**a **OrgService** jako Žádné.  
  
4. Vytvořte řešení stisknutím kombinace kláves CTRL+SHIFT+B. Ověřte, zda bylo sestavení úspěšné.  
  
#### <a name="to-run-the-solution"></a>Spuštění řešení  
  
1. Po sestavení řešení spusťte stisknutím kombinace kláves CTRL+F5 bez ladění. Ověřte, zda byly spuštěny všechny služby.  
  
2. V řešení klepněte pravým tlačítkem myši na příkaz **InternalClient** a potom vyberte příkaz **Zobrazit v prohlížeči**. Zobrazí se `InternalClient` výchozí stránka pro Ujistěte se, že jsou spuštěny služby, a klikněte na odkaz.  
  
3. Zobrazí se modul **Požadavek na přijetí.** Můžete sledovat scénář podrobně zde.  
  
4. Po `HiringRequest` dokončení můžete spustit . `ResumeRequest` Můžete sledovat scénář podrobně zde.  
  
5. Po `ResumeRequest` odeslání je k dispozici na veřejném webu (Web Společnosti Contoso Careers). Chcete-li zobrazit pracovní pozici (a ucházet se o pozici), přejděte na web Kariéra.  
  
6. Klepněte v řešení pravým tlačítkem myši na příkaz **CareersWebSite** a vyberte příkaz **Zobrazit v prohlížeči**.  
  
7. Přejděte zpět `InternalClient` na příkaz InterNě klepněte pravým tlačítkem myši na **položku InternalClient** v řešení a vyberte možnost **Zobrazit v prohlížeči**.  
  
8. Kliknutím na odkaz Práce v horní nabídce doručené **pošty** přejděte do části **JobPostings.** Můžete sledovat scénář podrobně zde.  
  
## <a name="scenarios"></a>Scénáře  
  
### <a name="hiring-request"></a>Žádost o přijetí  
  
1. Michael Alexander (Softwarový inženýr) chce požádat o novou pozici pro pronájem softwarového inženýra v testu (SDET) v oddělení inženýrství, který má alespoň 3 roky zkušeností v C#.  
  
2. Po vytvoření se žádost zobrazí v Doručená pošta Michaela (klikněte na **Aktualizovat,** pokud nevidíte požadavek) a čeká na schválení Petera Brehma, který je Michaelovým manažerem.  
  
3. Peter chce jednat na Michaelovu žádost. Myslí si, že pozice vyžaduje 5 let zkušeností c# místo 3, a tak posílá své připomínky zpět k přezkoumání.  
  
4. Michael vidí zprávu ve své e-mailové schránky od svého manažera a chce jednat. Michael vidí historii žádosti o pozici a souhlasí s Peterem. Michael upraví popis tak, aby vyžadoval 5 let zkušeností jazyka C# a přijme změnu.  
  
5. Peter jedná na Michaelovu upravenou žádost a přijímá ji. Žádost nyní musí schválit ředitel inženýrství Tsvi Reiter.  
  
6. Tsvi Reiter chce žádost urychlit, a tak se k tomu vyjádřil, že žádost je naléhavá, a přijímá ji.  
  
7. Žádost musí nyní schválit dva hr manažeři nebo generální ředitel. Generální ředitel, Brian Richard Goldstein, vidí naléhavou žádost Tsvi. Na žádost jedná tak, že ji přijímá, čímž obchází schválení dvěma hr manažery.  
  
8. Žádost je odebrána z Doručená pošta Michaela a proces náboru SDET nyní začala.  
  
### <a name="start-resume-request"></a>Zahájit požadavek na obnovení  
  
1. Nyní pozice úlohy čeká na odeslání na externí web, kde mohou uživatelé podat žádost (můžete ji vidět kliknutím na odkaz **Pracovní příspěvky).** V současné době je pracovní pozice sedí s hr zástupce, který je zodpovědný za dokončení pracovní pozice a vysílání je.  
  
2. Hr chce upravit tuto pracovní pozici (kliknutím na odkaz **Upravit)** nastavením časového odčasového času 60 minut (v reálném životě to mohou být dny nebo týdny). Časový čas umožňuje vypnutí pozice úlohy z externího webu podle zadaného času.  
  
3. Po uložení upravené pozice úlohy se zobrazí na kartě Přijímací životopisy (aktualizujte webovou stránku, abyste viděli novou pozici **úlohy).**  
  
### <a name="collecting-resumes"></a>Shromažďování životopisů  
  
1. Pozice úlohy by se měla zobrazit na externím webu. Jako osoba, která má zájem o zaměstnání, můžete požádat o tuto pozici a předložit svůj životopis.  
  
2. Pokud se vrátíte do služby Seznam zaúčtování práce, můžete "zobrazit životopisy", které byly dosud shromážděny.  
  
3. Hr může také přestat shromažďovat životopisy (například po identifikaci správného kandidáta).  
  
## <a name="troubleshooting"></a>Řešení potíží  
  
1. Ujistěte se, že používáte Visual Studio s oprávněními správce.  
  
2. Pokud se nepodaří vytvořit řešení, ověřte následující:  
  
    - Odkaz na `ContosoHR` nechybí v `InternalClient` `CareersWebSite` nebo projekty.  
  
3. Pokud se řešení nepodaří spustit, ověřte následující:  
  
    1. Všechny služby jsou spuštěny.  
  
    2. Odkazy na služby jsou aktualizovány.  
  
        1. Otevření složky App_WebReferences  
  
        2. Klepněte pravým tlačítkem myši na **položku Contoso** a vyberte možnost **Aktualizovat odkazy na web/službu**.  
  
        3. Znovu sestavte řešení stisknutím kombinace kláves CTRL+SHIFT+B v sadě Visual Studio.  
  
## <a name="uninstalling"></a>Odinstalování  
  
1. Odstraňte úložiště instancí serveru SQL Server spuštěním souboru Cleanup.bat, který se nachází ve složce DbSetup.  
  
2. Odstraňte zdrojový kód z pevného disku.
