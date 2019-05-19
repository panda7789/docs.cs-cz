---
title: Proces náboru
ms.date: 03/30/2017
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
ms.openlocfilehash: 685798ceab5e14169af6bdf16ce30a0f6548dc8c
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881902"
---
# <a name="hiring-process"></a>Proces náboru
Tento příklad ukazuje, jak implementovat obchodních procesů pomocí aktivit zasílání zpráv a dva pracovní postupy hostovaný jako služeb pracovních postupů. Tyto pracovní postupy jsou součástí infrastruktury IT fiktivní společnosti s názvem Contoso, Inc.  
  
 `HiringRequest` Pracovní postup (implementovaná jako <xref:System.Activities.Statements.Flowchart>) požádá o autorizaci z několika správci v organizaci. K dosažení tohoto cíle, pracovní postup používá jiné existující služby v organizaci (v našem případě doručené pošty služby a služby firemní data, implementovat jako obyčejný služby Windows Communication Foundation (WCF)).  
  
 `ResumeRequest` Pracovního postupu (implementovaná jako <xref:System.Activities.Statements.Sequence>) publikuje úlohu přispíváte ve společnosti Contoso kariéru na externí webovou stránku a spravuje pořízení obnoví. Účtování úloh je k dispozici v externí Web site na pevné období (dokud vyprší časový limit), nebo dokud zaměstnanci ze společnosti Contoso rozhodne ho odebrat.  
  
 Tato ukázka demonstruje následující funkce [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]:  
  
- <xref:System.Activities.Statements.Flowchart> a <xref:System.Activities.Statements.Sequence> pracovních postupů pro modelování obchodních procesů.  
  
- Služby pracovních postupů.  
  
- Aktivity zasílání zpráv.  
  
- Korelace na základě obsahu.  
  
- Vlastní aktivity (deklarativní a založený na kódu).  
  
- Zadaný systém SQL server trvalosti.  
  
- Vlastní <xref:System.Activities.Persistence.PersistenceParticipant>.  
  
- Vlastní sledování.  
  
- Událost sledování pro sledování Windows (ETW).  
  
- Složení aktivit.  
  
- <xref:System.Activities.Statements.Parallel> aktivity.  
  
- <xref:System.Activities.Statements.CancellationScope> aktivita.  
  
- Trvalý časovače (<xref:System.Activities.Statements.Delay> aktivit).  
  
- Transakce.  
  
- Více než jeden pracovní postup ve stejném řešení.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>Popis procesu  
 Společnosti Contoso, Inc. chce mít Zavřít kontrolu nad zaměstnanců v každém z její oddělení. Proto můžete kdykoli spustit nový proces náborovou chce, aby každý zaměstnanec, musí projít náborovou proces žádosti o schválení přijetí můžete skutečně došlo. Tento proces se nazývá náborovou požadavek na proces (definované v projektu HiringRequestService) a se skládá z následujících kroků:  
  
1. Zaměstnanec (žadateli) spustí náborovou požadavek na proces.  
  
2. Žadatele správce musí schválit žádost:  
  
    1. Správce může zamítnout žádosti.  
  
    2. Správce může vrátit žádost žadateli pro další informace:  
  
        1. Žadatel zkontroluje a odešle žádost o zpět do správce.  
  
    3. Můžete schválit správce.  
  
3. Poté, co správce žadatele schválí, musíte tuto žádost schválit vlastníka oddělení:  
  
    1. Vlastník oddělení může zamítnout.  
  
    2. Vlastník oddělení můžete schválit.  
  
4. Po vlastníka oddělení schválí, vyžaduje proces schvalování 2 HR správci nebo CEO:  
  
    1. Proces můžete přejít na stav přijetí nebo odmítnutí.  
  
    2. Pokud je proces přijat, novou instanci třídy `ResumeRequest` spuštění pracovního postupu (`ResumeRequest` je propojený s HiringRequest.csproj prostřednictvím odkazu na službu.)  
  
 Jakmile vedoucí schválil náboru nových zaměstnanců, HR musí najít vhodným kandidátem. Tento proces se provádí pomocí druhého pracovního postupu (`ResumeRequest`definované v ResumeRequestService.csproj). Tento pracovní postup definuje proces pro odeslání úlohy účtování příležitost kariéru na externí web kariéru Web společnosti Contoso, přijímá obnoví z žadatelé a sleduje stav úlohy účtování. Pozice jsou k dispozici pro pevné časové období (do čas vypršení platnosti) nebo dokud se zaměstnanci ze společnosti Contoso rozhodne ho odebrat. `ResumeRequest` Pracovní postup se skládá z následujících kroků:  
  
1. Zaměstnanci ze společnosti Contoso typů v informacích o umístění a dobu trvání časového limitu. Jakmile typy zaměstnanců v těchto informací pozice publikování na webu kariéru.  
  
2. Po publikování informací zúčastněným stranám, můžete zadat jejich obnoví. Při odeslání obnovit je uložen v záznamu propojené s levou úlohu.  
  
3. Žadatel můžete odeslat obnoví, až do vypršení časového limitu nebo někdo z oddělení lidských zdrojů Contoso rozhodne odebrat účtování zastavením procesu.  
  
## <a name="projects-in-the-sample"></a>Projekty v ukázce  
 V následující tabulce jsou uvedeny projekty v ukázkovém řešení.  
  
|Project|Popis|  
|-------------|-----------------|  
|ContosoHR|Obsahuje kontraktů dat, obchodní objekty a třídy úložiště.|  
|HiringRequestService|Obsahuje definice pracovního postupu zařazením proces žádosti o.<br /><br /> Tento projekt je implementovaný jako konzolové aplikace, který je hostitelem svým pracovního postupu (souboru xaml) jako službu.|  
|ResumeRequestService|Služby pracovních postupů, která shromažďuje obnoví kandidáty, než vyprší časový limit nebo někdo rozhodne, že proces je nutné ho zastavit.<br /><br /> Tento projekt je implementovaný jako služby (xamlx) deklarativní pracovního postupu.|  
|OrgService|Služba, která organizace (zaměstnanci, pozice, PositionTypes a oddělení). Tato služba si lze představit jako modul společnosti organizace ze plánování ERP (Enterprise Resource).<br /><br /> Tento projekt je implementovaný jako konzolovou aplikaci, která poskytuje služby Windows Communication Foundation (WCF).|  
|InboxService|Doručené pošty, která obsahuje úkoly pro zaměstnance.<br /><br /> Tento projekt je implementovaný jako konzolovou aplikaci, která poskytuje služby WCF.|  
|InternalClient|Webová aplikace pro interakci s procesem. Uživatele můžete spustit, zapojit a zobrazit jejich HiringProcess pracovních postupů. Pomocí této aplikace, můžete také spuštění a monitorování ResumeRequest procesy.<br /><br /> Tento web je potřebná k dosažení interní do intranetu společnosti Contoso. Tento projekt je implementovaný jako webu technologie ASP.NET.|  
|CareersWebSite|Externí web, který zpřístupňuje volná ve společnosti Contoso. Všechny potenciální Release candidate můžete přejít na tomto webu a Odeslat životopis.|  
  
## <a name="feature-summary"></a>Souhrn funkcí  
 Následující tabulka popisuje, jak se jednotlivé funkce používá v této ukázce.  
  
|Funkce|Popis|Project|  
|-------------|-----------------|-------------|  
|Vývojový diagram|Vývojový diagram je reprezentován obchodních procesů. Tento popis vývojový diagram představuje proces stejným způsobem, ve kterém firma by čerpali ho v tabuli.|HiringRequestService|  
|Služby pracovních postupů|Vývojový diagram s definicí procesu je hostovaný ve službě (v tomto příkladu služba je hostována v konzolové aplikaci).|HiringRequestService|  
|Aktivity zasílání zpráv|Vývojový diagram používá zasílání zpráv aktivity dvěma způsoby:<br /><br /> -K získání informací od uživatele (Chcete-li přijímat rozhodnutí a související informace v každém kroku schválení).<br />-K interakci s ostatními existující službami (InboxService a OrgDataService použít odkazy na službu).|HiringRequestService|  
|Obsah na základě korelace|Na vlastnost ID náborovou žádosti o korelaci zprávy schválení:<br /><br /> – Když se spustí proces, popisovače korelace je inicializován s ID žádosti.<br />-Příchozí zprávy schválení je možné korelovat na jejich ID (ID požadavku je první parametr každé zprávy schválení).|HiringRequestService / ResumeRequestService|  
|Vlastní aktivity (deklarativní a na základě kódu)|Existuje několik vlastních aktivit v této ukázce:<br /><br /> -   `SaveActionTracking`: Tato aktivita vygeneruje vlastní <xref:System.Activities.Tracking.TrackingRecord> (pomocí <xref:System.Activities.NativeActivityContext.Track%2A>). Tato aktivita se vytvořila pomocí imperativního kódu rozšíření <xref:System.Activities.NativeActivity>.<br />-   `GetEmployeesByPositionTypes`: Tato aktivita přijímá seznam ID typu umístění a vrátí seznam lidí, kteří mají této pozici ve společnosti Contoso. Tato aktivita deklarativně vytvořila (použití návrháře aktivit).<br />-   `SaveHiringRequestInfo`: Tato aktivita uloží informace `HiringRequest` (pomocí `HiringRequestRepository.Save`). Tato aktivita se vytvořila pomocí imperativního kódu rozšíření <xref:System.Activities.CodeActivity>.|HiringRequestService|  
|Trvalost poskytované systémem SQL Server|<xref:System.ServiceModel.Activities.WorkflowServiceHost> Instanci, která hostuje definici vývojový diagram procesu je nakonfigurován na použití stálost poskytované systémem SQL Server.|HiringRequestService / ResumeRequestService|  
|Vlastní sledování|Ukázka zahrnuje vlastní sledování účastník, který ukládá historii `HiringRequestProcess` (to zaznamenává, jaké akce proběhla, kdo a kdy). Zdrojový kód je ve složce Sledování HiringRequestService.|HiringRequestService|  
|Sledování trasování událostí pro Windows|Poskytované systémem sledování ETW konfigurován v souboru App.config v HiringRequestService služby.|HiringRequestService|  
|Složení aktivit|Definice procesu používá bezplatný složení <xref:System.Activities.Activity>. Vývojový diagram obsahuje několik pořadí a paralelní aktivity, které současně obsahovat jiné aktivity (a tak dále).|HiringRequestService|  
|Paralelní aktivity.|-   <xref:System.Activities.Statements.ParallelForEach%601> slouží k registraci v doručené poště CEO a HR paralelně (čeká na dva HR správci krok schválení).<br />-   <xref:System.Activities.Statements.Parallel> Umožňuje provést některé úlohy čištění v krocích dokončeno a odmítnuto|HiringRequestService|  
|Zrušení modelu|Vývojový diagram používá <xref:System.Activities.Statements.CancellationScope> vytvořit zrušení chování (v tomto případě provádí některé čištění.)|HiringRequestService|  
|Zákazník trvalého účastníka|`HiringRequestPersistenceParticipant` uloží data z proměnné pracovního postupu do tabulky uložené v databázi Contoso HR.|HiringRequestService|  
|Služby pracovních postupů|`ResumeRequestService` je implementováno pomocí služeb pracovních postupů. Informace o definici a služby pracovních postupů jsou obsaženy v ResumeRequestService.xamlx. Služba je nakonfigurována používat trvalosti a sledování.|ResumeRequestService|  
|Trvalý časovače|`ResumeRequestService` používá k definování dobu trvání úlohy účtování trvalý časovače (po vypršení platnosti vypršení časového limitu odesílání úlohy je uzavřený).|ResumeRequestService|  
|Transakce|<xref:System.Activities.Statements.TransactionScope> slouží k zajištění konzistence dat v rámci provedení několik aktivit (při přijetí nového obnovit).|ResumeRequestService|  
|Transakce|Vlastní trvalého účastníka (`HiringRequestPersistenceParticipant`) a vlastní sledování účastník (`HistoryFileTrackingParticipant`) použít stejnou transakci.|HiringRequestService|  
|Pomocí [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v aplikacích technologie ASP.NET.|Pracovní postupy jsou přístupné ze dvou aplikací technologie ASP.NET.|InternalClient / CareersWebSite|  
  
## <a name="data-storage"></a>Úložiště dat  
 Data uložená v databázi serveru SQL Server s názvem `ContosoHR` (skript pro vytvoření této databáze se nachází v `DbSetup` složky). Instance pracovního postupu jsou uloženy v databázi serveru SQL Server s názvem `InstanceStore` (skriptů pro vytváření v úložišti instancí jsou součástí [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] distribuce).  
  
 Obě databáze jsou vytvořeny pomocí skriptu Setup.cmd na příkazovém řádku pro vývojáře pro sadu Visual Studio.  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
  
#### <a name="to-create-the-databases"></a>K vytvoření databáze  
  
1. Otevřete příkazový řádek pro vývojáře pro sadu Visual Studio.  
  
2. Přejděte do složky s ukázkou.  
  
3. Spusťte Setup.cmd.  
  
4. Ověřte, že dvě databáze `ContosoHR` a `InstanceStore` byly vytvořeny v rámci SQL serveru Express.  
  
#### <a name="to-set-up-the-solution-for-execution"></a>Nastavit řešení pro spouštění  
  
1. Spusťte sadu Visual Studio jako správce. Open HiringRequest.sln.  
  
2. Klikněte pravým tlačítkem na řešení v **Průzkumníka řešení** a vyberte **vlastnosti**.  
  
3. Vyberte možnost **více projektů po spuštění** a nastavit **CareersWebSite**, **InternalClient**, **HiringRequestService**, a **ResumeRequestService** k **Start**. Ponechte **ContosoHR**, **InboxService**, a **OrgService** jako None.  
  
4. Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B. Ověřte, že sestavení proběhlo úspěšně.  
  
#### <a name="to-run-the-solution"></a>Spuštění řešení  
  
1. Po sestavení řešení, stiskněte CTRL + F5 ke spuštění bez ladění. Ověřte, že všechny služby byly spuštěny.  
  
2. Klikněte pravým tlačítkem myši **InternalClient** v řešení a pak vyberte **zobrazit v prohlížeči**. Výchozí stránka pro `InternalClient` se zobrazí. Zkontrolujte, zda jsou spuštěny služby a klikněte na odkaz.  
  
3. **HiringRequest** modulu se zobrazí. Můžete postupovat podle scénáře pomocí zde podrobně.  
  
4. Jednou `HiringRequest` je dokončeno, můžete spustit `ResumeRequest`. Můžete postupovat podle scénáře pomocí zde podrobně.  
  
5. Když `ResumeRequest` je odesláno, je dostupná ve veřejné webové stránky (Contoso kariéru webové stránky). Chcete-li zobrazit odesílání úlohy (a použít pro umístění), přejděte na web kariéru.  
  
6. Klikněte pravým tlačítkem na **CareersWebSite** v řešení a vyberte **zobrazit v prohlížeči**.  
  
7. Přejděte zpět `InternalClient` kliknutím pravým tlačítkem myši **InternalClient** v řešení a vyberete **zobrazit v prohlížeči**.  
  
8. Přejděte na **JobPostings** část kliknutím **úlohy příspěvky** odkazu v horní nabídce doručené pošty. Můžete postupovat podle scénáře pomocí zde podrobně.  
  
## <a name="scenarios"></a>Scénáře  
  
### <a name="hiring-request"></a>Zařazení požadavku  
  
1. Michael Alexander (softwarový inženýr) chce požádat o novou pozici zařazení softwarový inženýr v testu (transformace rolí SDET) Engineering oddělení, který má alespoň 3 let zkušeností v jazyce C#.  
  
2. Po vytvoření se zobrazí žádosti v doručené poště od Michaela (klikněte na tlačítko **aktualizovat** Pokud nevidíte žádost) čeká na schválení Peter Brehm, který je od Michaela správce.  
  
3. Peter chce, aby mohly reagovat na žádosti od Michaela. Uzná za požadavky pozici 5 let zkušeností C# místo 3, takže posílá jeho komentáře zpět ke kontrole.  
  
4. Michael zobrazí zpráva ve své doručené poště od svého vedoucího a chce, aby se tak, aby fungoval. Michael historie pozice žádosti o vidí a souhlasí s Peter. Michael upraví popis, který vyžadují 5 let zkušeností s C# a přijímá úpravy.  
  
5. Peter pracuje na upravený požadavek od Michaela a přijme ji. Požadavek nyní musí schválit Director of Engineering, Tsvi Reiter.  
  
6. Tsvi Reiter chce, aby se ohledně urychlení jejich zpracování žádostí, aby mohl Vloží komentář říct, že žádost je důležitá a přijme ji.  
  
7. Požadavek nyní musí je schválit výbor dvě HR vedoucí nebo CEO. Generální ředitel, Brian Richard Goldstein, uvidí urgentní žádost Tsvi. Má funguje v požadavku tak, že přijímá, obejít schválení správci dvě HR.  
  
8. Žádost se odebere z Michael vaší doručené pošty a má teď zahájen proces náboru by.  
  
### <a name="start-resume-request"></a>Žádost o obnovení  
  
1. Nyní, pozice úloha čeká která se má zveřejnit na externí web, kde uživatelé mohou použít (uvidíte ho kliknutím **příspěvky úlohy** odkaz). V současné době pracovní zařazení nachází s personálního oddělení zástupce, který je zodpovědný za dokončování úlohy pozice a jejím zveřejněním.  
  
2. Personálního oddělení chce upravit tato pozice (kliknutím **upravit** odkaz) tak, že nastavíte časový limit 60 minut (v reálném životě, může to být dny nebo týdny). Časový limit umožňuje pozice mají být provedeny vypnout podle času určeného externí web.  
  
3. Po uložení upravených pozice, zobrazí se v **příjem obnoví** kartu (aktualizace webové stránky zobrazíte na nové pozici úlohu).  
  
### <a name="collecting-resumes"></a>Shromažďují se obnoví  
  
1. Umístění úlohy by se zobrazit na externí web. Jako osoba zájem o používání pro úlohu můžete použít pro tuto pozici a Odeslat životopis.  
  
2. Pokud přejdete zpět ke službě Job List příspěvky, můžete "Zobrazit obnoví", které jste zatím shromažďovat.  
  
3. HR taky můžete zastavit shromažďování obnoví (například když byl identifikován správný Release candidate).  
  
## <a name="troubleshooting"></a>Poradce při potížích  
  
1. Ujistěte se, že používáte Visual Studio s oprávněními správce.  
  
2. Pokud se sestavení nezdaří řešení, ověřte následující:  
  
    - Odkaz na `ContosoHR` není chybí `InternalClient` nebo `CareersWebSite` projekty.  
  
3. Pokud toto řešení se nepodaří spustit, ověřte následující:  
  
    1. Všechny služby spuštěné.  
  
    2. Aktualizují se odkazy na služby.  
  
        1. Otevřete složku App_WebReferences  
  
        2. Klikněte pravým tlačítkem na **Contoso** a vyberte **aktualizace Web/odkazy na služby**.  
  
        3. Znovu sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B v sadě Visual Studio.  
  
## <a name="uninstalling"></a>Odinstalace  
  
1. Odstraňte spuštěním Cleanup.bat, umístěný ve složce nástroj DbSetup v úložišti instancí systému SQL Server.  
  
2. Odstraňte ve formě zdrojového kódu pevném disku.
