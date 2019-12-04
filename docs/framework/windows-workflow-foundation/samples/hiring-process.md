---
title: Proces náboru
ms.date: 03/30/2017
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
ms.openlocfilehash: 02968acfc762550c9010dd0ed29acbca845e08bb
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715980"
---
# <a name="hiring-process"></a>Proces náboru
Tato ukázka předvádí, jak implementovat obchodní proces pomocí aktivit zasílání zpráv a dvou pracovních postupů hostovaných jako služby pracovních postupů. Tyto pracovní postupy jsou součástí infrastruktury IT fiktivní společnosti s názvem contoso, Inc.  
  
 Proces pracovního postupu `HiringRequest` (implementovaný jako <xref:System.Activities.Statements.Flowchart>) žádá o autorizaci od několika správců v organizaci. Pro dosažení tohoto cíle používá pracovní postup jiné stávající služby v organizaci (v našem případě službu doručených zpráv a organizační datovou službu implementovali jako služby pro jednoduché Windows Communication Foundation (WCF)).  
  
 Pracovní postup `ResumeRequest` (implementovaný jako <xref:System.Activities.Statements.Sequence>) zveřejňuje odeslání úlohy na externím webu péče společnosti Contoso a spravuje získávání obnovení. Publikování úlohy je dostupné na externím webu po určitou dobu (do vypršení časového limitu) nebo až do doby, kdy se zaměstnanec od společnosti Contoso rozhodne ji odebrat.  
  
 Tato ukázka demonstruje následující funkce [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]:  
  
- pracovní postupy <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Sequence> pro modelování obchodních procesů.  
  
- Služby pracovních postupů.  
  
- Aktivity zasílání zpráv.  
  
- Korelace na základě obsahu.  
  
- Vlastní aktivity (deklarativní a na základě kódu).  
  
- Trvalost systému SQL Server dodané systémem.  
  
- Vlastní <xref:System.Activities.Persistence.PersistenceParticipant>.  
  
- Vlastní sledování.  
  
- Sledování událostí pro Windows (ETW)  
  
- Složení aktivit.  
  
- <xref:System.Activities.Statements.Parallel> aktivity.  
  
- <xref:System.Activities.Statements.CancellationScope> aktivita  
  
- Trvalé časovače (<xref:System.Activities.Statements.Delay> aktivita).  
  
- Převody.  
  
- Více než jeden pracovní postup ve stejném řešení.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>Popis procesu  
 Contoso, Inc. chce mít v každé z jeho oddělení uzavřenou kontrolu nad počtem zaměstnanců. Proto si každý zaměstnanec chce zahájit nový proces náboru a musí projít schválením procesu žádosti o přijetí, aby k němu skutečně mohlo dojít. Tento proces se nazývá požadavek na proces náboru (definovaný v projektu HiringRequestService) a skládá se z následujících kroků:  
  
1. Zaměstnanec (žadatel) spustí žádost o zařazení do procesu.  
  
2. Správce žadatele musí žádost schválit:  
  
    1. Správce může žádost odmítnout.  
  
    2. Správce může žádost vrátit žadateli a získat další informace:  
  
        1. Žadatel zkontroluje a pošle žádost zpátky vedoucímu.  
  
    3. Správce může schválit.  
  
3. Poté, co správce žadatele schválí, musí žádost schválit vlastník oddělení:  
  
    1. Vlastník oddělení může odmítat.  
  
    2. Vlastník oddělení může schválit.  
  
4. Po schválení vlastníkem oddělení proces vyžaduje schválení 2 správců lidských zdrojů nebo generálního ředitele:  
  
    1. Tento proces může přejít do stavu přijato nebo odmítnuto.  
  
    2. Pokud je proces přijat, spustí se nová instance pracovního postupu `ResumeRequest` (`ResumeRequest` je propojena s HiringRequest. csproj prostřednictvím odkazu na službu.)  
  
 Jakmile manažeři schválí zařazení nového zaměstnance, HR musí příslušný kandidát najít. Tento proces provádí druhý pracovní postup (`ResumeRequest`definovaný v ResumeRequestService. csproj). Tento pracovní postup definuje proces odeslání účtování úlohy s příležitostí k práci na externím webu společnosti Contoso, přijímá životopisy od žadatelů a monitoruje stav odeslání úlohy. Pozice jsou k dispozici pro pevné časové období (do vypršení časového limitu) nebo do doby, než se rozhodne zaměstnanec z společnosti Contoso ji odebrat. Pracovní postup `ResumeRequest` sestává z následujících kroků:  
  
1. Zaměstnanci z typů společnosti Contoso v informacích o pozici a dobu trvání časového limitu. Jakmile zaměstnanci tyto informace zaúčtují, pozice se zveřejní na webu péče o péči.  
  
2. Po zveřejnění informací můžou zúčastněné strany odeslat své životopisy. Když se odešle životopis, uloží se do záznamu propojeného s otevřením úlohy.  
  
3. Žadatelé můžou odeslat pokračování, dokud časový limit nevyprší nebo někdo z oddělení IT společnosti Contoso výslovně nerozhodne, že se má odstranit, zastavením procesu.  
  
## <a name="projects-in-the-sample"></a>Projekty v ukázce  
 V následující tabulce jsou uvedeny projekty v ukázkovém řešení.  
  
|Projekt|Popis|  
|-------------|-----------------|  
|ContosoHR|Obsahuje kontrakty dat, obchodní objekty a třídy úložiště.|  
|HiringRequestService|Obsahuje definici pracovního postupu procesu žádosti o zařazení.<br /><br /> Tento projekt je implementován jako Konzolová aplikace, která hostuje pracovní postup (soubor XAML) jako službu.|  
|ResumeRequestService|Služba pracovního postupu, která shromažďuje životopisy kandidátů do vypršení časového limitu nebo se někdo rozhodne, že se má proces zastavit.<br /><br /> Tento projekt je implementován jako služba deklarativního pracovního postupu (xamlx).|  
|OrgService|Služba, která zveřejňuje informace o organizaci (zaměstnanci, pozice, PositionTypes a oddělení). Tuto službu můžete představit jako modul organizace společnosti pro plán podnikových zdrojů (ERP).<br /><br /> Tento projekt je implementován jako Konzolová aplikace, která zveřejňuje službu Windows Communication Foundation (WCF).|  
|InboxService|Doručená pošta, která obsahuje úkoly s akcemi pro zaměstnance.<br /><br /> Tento projekt je implementován jako Konzolová aplikace, která zveřejňuje službu WCF.|  
|InternalClient|Webová aplikace pro interakci s procesem. Uživatelé můžou začít, zúčastnit se a prohlížet své pracovní postupy HiringProcess. Pomocí této aplikace mohou také začít a monitorovat procesy ResumeRequest.<br /><br /> Tato lokalita je implementovaná tak, aby byla interní pro intranetovou síť společnosti Contoso. Tento projekt je implementován jako web ASP.NET.|  
|CareersWebSite|Externí web, který zveřejňuje otevřené pozice ve společnosti Contoso. Každý potenciální kandidát může přejít na tento web a odeslat obnovení.|  
  
## <a name="feature-summary"></a>Souhrn funkcí  
 Následující tabulka popisuje, jak se v této ukázce používají jednotlivé funkce.  
  
|Funkce|Popis|Projekt|  
|-------------|-----------------|-------------|  
|Vývojový diagram|Obchodní proces je reprezentován jako vývojový diagram. Tento popis vývojového diagramu představuje proces stejným způsobem jako obchodní oddělení v programu Tabule.|HiringRequestService|  
|Služby pracovních postupů|Vývojový diagram s definicí procesu je hostovaný ve službě (v tomto příkladu je služba hostovaná v konzolové aplikaci).|HiringRequestService|  
|Aktivity zasílání zpráv|Vývojový diagram používá aktivity zasílání zpráv dvěma způsoby:<br /><br /> – Chcete-li získat informace od uživatele (pro přijímání rozhodnutí a souvisejících informací v každém kroku schválení).<br />– Pro interakci s ostatními stávajícími službami (InboxService a OrgDataService, které se používají prostřednictvím odkazů na služby).|HiringRequestService|  
|Korelace na základě obsahu|Zprávy o schválení korelují s vlastností ID žádosti o přijetí:<br /><br /> – Při spuštění procesu se korelační popisovač inicializuje s ID požadavku.<br />-Příchozí zprávy o schválení korelují podle ID (první parametr každé zprávy schválení je ID žádosti).|HiringRequestService / ResumeRequestService|  
|Vlastní aktivity (deklarativní a kód založený na kódu)|V této ukázce je několik vlastních aktivit:<br /><br /> -   `SaveActionTracking`: Tato aktivita vygeneruje vlastní <xref:System.Activities.Tracking.TrackingRecord> (pomocí <xref:System.Activities.NativeActivityContext.Track%2A>). Tato aktivita se vytvořila pomocí imperativního kódu, který rozšiřuje <xref:System.Activities.NativeActivity>.<br />-   `GetEmployeesByPositionTypes`: Tato aktivita obdrží seznam identifikátorů typu pozice a vrátí seznam osob, které mají tuto pozici ve společnosti Contoso. Tato aktivita se vytvořila deklarativně (pomocí návrháře aktivit).<br />-   `SaveHiringRequestInfo`: Tato aktivita ukládá informace o `HiringRequest` (pomocí `HiringRequestRepository.Save`). Tato aktivita se vytvořila pomocí imperativního kódu, který rozšiřuje <xref:System.Activities.CodeActivity>.|HiringRequestService|  
|Trvalost SQL Server poskytované systémem|Instance <xref:System.ServiceModel.Activities.WorkflowServiceHost>, která je hostitelem definice procesu vývojového diagramu, je nakonfigurovaná tak, aby používala stálost SQL Server poskytovanou systémem.|HiringRequestService / ResumeRequestService|  
|Vlastní sledování|Ukázka zahrnuje vlastního účastníka sledování, který ukládá historii `HiringRequestProcess` (Tato akce znamená, jakou akci byly provedeny, kdy a kdy). Zdrojový kód je ve složce sledování HiringRequestService.|HiringRequestService|  
|Sledování ETW|Sledování ETW zadané systémem se konfiguruje v souboru App. config ve službě HiringRequestService.|HiringRequestService|  
|Složení aktivit|Definice procesu využívá bezplatné složení <xref:System.Activities.Activity>. Vývojový diagram obsahuje několik sekvencí a paralelních aktivit, které zároveň obsahují další aktivity (a tak dále).|HiringRequestService|  
|Paralelní aktivity|-   <xref:System.Activities.Statements.ParallelForEach%601> se používá k registraci do doručené pošty správců generálního ředitelů a lidských zdrojů (čeká se na krok schvalování dvou správců lidských zdrojů).<br />k provedení některých úloh vyčištění v dokončených a odmítnutých krocích se používá -   <xref:System.Activities.Statements.Parallel>.|HiringRequestService|  
|Zrušení modelu|Vývojový diagram používá <xref:System.Activities.Statements.CancellationScope> k vytvoření chování zrušení (v tomto případě provede nějaké vyčištění).|HiringRequestService|  
|Účastník Persistence zákazníka|`HiringRequestPersistenceParticipant` ukládá data z proměnné pracovního postupu do tabulky uložené v databázi společnosti Contoso HR.|HiringRequestService|  
|Služby pracovních postupů|`ResumeRequestService` je implementováno pomocí služeb pracovního postupu. Informace o definici a službě pracovního postupu jsou obsaženy v ResumeRequestService. xamlx. Služba je nakonfigurovaná tak, aby používala trvalost a sledování.|ResumeRequestService|  
|Trvalé časovače|`ResumeRequestService` používá k definování trvání zaúčtování úlohy trvalé časovače (po vypršení časového limitu je publikování úlohy uzavřeno).|ResumeRequestService|  
|Transakce|<xref:System.Activities.Statements.TransactionScope> slouží k zajištění konzistence dat v rámci provádění několika aktivit (při přijetí nového obnovení).|ResumeRequestService|  
|Transakce|Vlastní účastník trvalosti (`HiringRequestPersistenceParticipant`) a vlastní účastník sledování (`HistoryFileTrackingParticipant`) používají stejnou transakci.|HiringRequestService|  
|Použití [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v aplikacích ASP.NET.|K pracovním postupům se dostanete ze dvou aplikací ASP.NET.|InternalClient / CareersWebSite|  
  
## <a name="data-storage"></a>Úložiště dat  
 Data jsou uložena v databázi SQL Server s názvem `ContosoHR` (skript pro vytvoření této databáze se nachází ve složce `DbSetup`). Instance pracovních postupů jsou uloženy v databázi SQL Server s názvem `InstanceStore` (skripty pro vytvoření úložiště instancí jsou součástí distribuce [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)]).  
  
 Obě databáze jsou vytvořeny spuštěním skriptu Setup. cmd z Developer Command Prompt pro aplikaci Visual Studio.  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
  
#### <a name="to-create-the-databases"></a>Vytvoření databází  
  
1. Otevřete Developer Command Prompt pro Visual Studio.  
  
2. Přejděte do složky Sample.  
  
3. Spusťte Setup. cmd.  
  
4. Ověřte, že se v SQL Express vytvořily tyto dvě databáze `ContosoHR` a `InstanceStore`.  
  
#### <a name="to-set-up-the-solution-for-execution"></a>Nastavení řešení pro provádění  
  
1. Spusťte sadu Visual Studio jako správce. Otevřete HiringRequest. sln.  
  
2. Klikněte pravým tlačítkem na řešení v **Průzkumník řešení** a vyberte **vlastnosti**.  
  
3. Vyberte možnost **více projektů po spuštění** a pro **začátek**nastavte **CareersWebSite**, **InternalClient**, **HiringRequestService**a **ResumeRequestService** . Nechejte **ContosoHR**, **InboxService**a **OrgService** jako žádné.  
  
4. Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B. Ověřte, že sestavení proběhlo úspěšně.  
  
#### <a name="to-run-the-solution"></a>Spuštění řešení  
  
1. Po sestavení řešení stiskněte kombinaci kláves CTRL + F5 a spusťte bez ladění. Ověřte, zda byly spuštěny všechny služby.  
  
2. V řešení klikněte pravým tlačítkem na **InternalClient** a pak vyberte **Zobrazit v prohlížeči**. Zobrazí se výchozí stránka pro `InternalClient`. Zajistěte, aby služba běžela, a klikněte na odkaz.  
  
3. Zobrazí se modul **HiringRequest** . Můžete postupovat podle scénáře, který je zde popsán.  
  
4. Po dokončení `HiringRequest` můžete `ResumeRequest`spustit. Můžete postupovat podle scénáře, který je zde popsán.  
  
5. Když je `ResumeRequest` publikovaný, je k dispozici na veřejném webu (na webu péče společnosti Contoso). Chcete-li zobrazit zaúčtování úlohy (a použít pro pozici), přejděte na web pro péči o péče.  
  
6. V řešení klikněte pravým tlačítkem na **CareersWebSite** a vyberte **Zobrazit v prohlížeči**.  
  
7. Kliknutím pravým tlačítkem myši na **InternalClient** v řešení a výběrem **zobrazení v prohlížeči**přejděte zpět na `InternalClient`.  
  
8. Přejděte do části **jobpostings** kliknutím na odkaz **účtování úlohy** v horní nabídce Doručená pošta. Můžete postupovat podle scénáře, který je zde popsán.  
  
## <a name="scenarios"></a>Scénáře  
  
### <a name="hiring-request"></a>Žádost o pronájem  
  
1. Michael Alexander (Software inženýr) chce požádat o novou pozici pro poskytování softwarových inženýrů v testu (člověk) v technickém oddělení, který má alespoň 3 roky zkušeností C#.  
  
2. Po vytvoření se žádost zobrazí v doručené poště Michael (klikněte na **aktualizovat** , pokud se žádost nezobrazuje) čeká se na schválení uživatele Petr Brehm, který je nadřízeného.  
  
3. Petr chce jednat na žádost Michael. Domnívá se, že pozice bude C# mít 5 let zkušeností místo 3, takže pošle své komentáře zpátky ke kontrole.  
  
4. Michal uvidí zprávu ve své doručené poště od jejího manažera a chce jednat. Michal uvidí historii žádosti o pozici a souhlasí s Petra. Michal upraví popis, aby vyžadoval 5 let C# zkušeností a přijal změnu.  
  
5. Petr pracuje na upravené žádosti Michael a přijímá je. Žádost teď musí schválit ředitel inženýrů, Tsvi Reiter.  
  
6. Tsvi Reiter chce tuto žádost urychlit, takže vloží komentář, který říká, že žádost je naléhavá a přijímá.  
  
7. Žádost se teď musí schválit pomocí dvou správců lidských zdrojů nebo generálního ředitele. Generální ředitel, Brian Richard Goldstein, se dohlíží na naléhavou žádost Tsvi. Na žádost reaguje tím, že ji přijme, čímž vynechá schválení dvou správců lidských zdrojů.  
  
8. Požadavek se odebere z doručené pošty Michael a proces zajímání člověk se teď začal.  
  
### <a name="start-resume-request"></a>Spustit obnovení žádosti  
  
1. Nyní bude pozice úlohy čekat na zveřejnění na externím webu, kde se můžou lidé použít (můžete se podívat na odkaz pro **zaúčtování úloh** ). V současné době se pozice úlohy koná se zástupcem na HR, který zodpovídá za dokončení pozice úlohy a jejich odeslání.  
  
2. HR chce upravit tuto pozici úlohy (kliknutím na odkaz pro **Úpravy** ) nastavením časového limitu 60 minut (v reálném čase může to být dny nebo týdny). Časový limit umožňuje, aby se pozice úlohy vypnula na externím webu v závislosti na zadaném čase.  
  
3. Po uložení upravované pozice úlohy se zobrazí na kartě pokračování po **obnovení** (aktualizace webové stránky, aby se zobrazila nová pozice v úloze).  
  
### <a name="collecting-resumes"></a>Shromažďování pokračování  
  
1. Pozice úlohy by se měla zobrazit na externím webu. Jako osoba, která se zajímá o použití pro úlohu, můžete požádat o tuto pozici a odeslat obnovení.  
  
2. Pokud se vrátíte zpět ke službě seznam účtování úloh, můžete si Zobrazit obnovená obnovení, která jsou zatím shromážděná.  
  
3. HR může také přestat shromažďovat pokračování (například po identifikaci správného kandidáta).  
  
## <a name="troubleshooting"></a>Odstraňování problémů  
  
1. Ujistěte se, že používáte aplikaci Visual Studio s oprávněními správce.  
  
2. Pokud se řešení nepodařilo sestavit, ověřte následující:  
  
    - Odkaz na `ContosoHR` v projektech `InternalClient` nebo `CareersWebSite` chybí.  
  
3. Pokud se řešení nepovede spustit, ověřte následující:  
  
    1. Všechny služby jsou spuštěné.  
  
    2. Odkazy na službu jsou aktualizované.  
  
        1. Otevřete složku App_WebReferences  
  
        2. Klikněte pravým tlačítkem myši na **Contoso** a vyberte **aktualizovat odkazy na web/služby**.  
  
        3. Znovu sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B v aplikaci Visual Studio.  
  
## <a name="uninstalling"></a>Odinstalace  
  
1. Odstraňte úložiště instancí SQL Server spuštěním programu Cleanup. bat, který je umístěný ve složce nástroj DBSetup.  
  
2. Odstraňte zdrojový kód z pevného disku.
