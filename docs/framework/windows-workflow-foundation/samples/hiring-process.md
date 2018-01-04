---
title: "Náborové procesu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d5fcacbb-c884-4b37-a5d6-02b1b8eec7b4
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 30cad662a9cca679f7e8ce720cfde3d369b9ba60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="hiring-process"></a>Náborové procesu
Tento příklad ukazuje, jak implementovat obchodní proces, který používá aktivity zasílání zpráv a dvě pracovních hostované jako pracovní postup služby. Tyto pracovní postupy jsou součástí IT infrastruktury fiktivní společnosti nazývané Contoso, Inc.  
  
 `HiringRequest` Pracovní postup (implementovaný jako <xref:System.Activities.Statements.Flowchart>) požádá o autorizaci z několika správci v organizaci. K dosažení tohoto cíle, pracovní postup používá jiné existující služby v organizaci (v našem případě služby doručené pošty a k organizačním datům službě implementované jako prostý [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby).  
  
 `ResumeRequest` Pracovního postupu (implementovaný jako <xref:System.Activities.Statements.Sequence>) publikuje úlohu publikování ve společnosti Contoso externí přenašečích webové stránky a spravuje získání obnoví. Účtování projektu je k dispozici v externí Web lokality po stanovenou dobu (dokud platnost vyprší časový limit) nebo dokud se zaměstnanci ze společnosti Contoso rozhodne jeho odebrání.  
  
 Tento příklad znázorňuje následující funkce sady [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)]:  
  
-   <xref:System.Activities.Statements.Flowchart>a <xref:System.Activities.Statements.Sequence> pracovní postupy pro modelování obchodní procesy.  
  
-   Služby pracovních postupů.  
  
-   Aktivity zasílání zpráv.  
  
-   Korelace na základě obsahu.  
  
-   Vlastní aktivity (deklarativní a založené na kódu).  
  
-   Poskytované systémem SQL server trvalost.  
  
-   Vlastní <xref:System.Activities.Persistence.PersistenceParticipant>.  
  
-   Vlastní sledování.  
  
-   Sledování pro Windows (ETW) sledování událostí.  
  
-   Sestavení aktivit.  
  
-   <xref:System.Activities.Statements.Parallel>aktivity.  
  
-   <xref:System.Activities.Statements.CancellationScope>aktivita.  
  
-   Trvanlivý časovače (<xref:System.Activities.Statements.Delay> aktivity).  
  
-   Transakce.  
  
-   Více než jeden pracovní postup ve stejném řešení.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\HiringProcess`  
  
## <a name="description-of-the-process"></a>Popis procesu  
 Contoso, Inc. chce mít Zavřít kontrolu nad zaměstnanců ve všech jeho oddělení. Proto můžete kdykoli spustit nový proces náborové chce, aby každý zaměstnanec, musí projít náborové schválení proces žádost předtím, než o přijetí může dojít ve skutečnosti. Tento proces se nazývá náborové žádost o proces (definovanou v projektu HiringRequestService) a se skládá z následujících kroků:  
  
1.  Zaměstnanec (žadateli) spustí náborové žádost o proces.  
  
2.  Žadatele správce musí schválit žádost:  
  
    1.  Správce může odmítnout žádosti.  
  
    2.  Správce může vrátit požadavek na žadatele o další informace:  
  
        1.  Žadatel zkontroluje a odešle žádost zpět na správce.  
  
    3.  Můžete schválit správce.  
  
3.  Po žadatele manager schválí, musíte tuto žádost schválit vlastník oddělení:  
  
    1.  Vlastník oddělení zamítnout.  
  
    2.  Vlastník oddělení můžete schválit.  
  
4.  Po vlastník oddělení schválí, proces vyžaduje schválení správce 2 HR nebo generálního:  
  
    1.  Proces můžete přechod do stavu přijetí nebo odmítnutí.  
  
    2.  Pokud je proces přijata, novou instanci třídy `ResumeRequest` spuštění pracovního postupu (`ResumeRequest` souvisí HiringRequest.csproj prostřednictvím odkazu na službu.)  
  
 Jakmile vybraných manažerů schválit nábor nových zaměstnanců, musí HR najít odpovídající candidate. Tento proces provádí druhý pracovního postupu (`ResumeRequest`, definované v ResumeRequestService.csproj). Tento pracovní postup definuje proces odesílání úlohy publikování s kariérní příležitost k externí přenašečích webové stránky společnosti Contoso, obdrží obnoví od žadatelů a sleduje stav účtování projektu. Pozice jsou k dispozici pro pevné časové období (než čas vyprší) nebo dokud se zaměstnanci ze společnosti Contoso rozhodne jeho odebrání. `ResumeRequest` Pracovní postup se skládá z následujících kroků:  
  
1.  Zaměstnanec společnosti Contoso typy v informace o umístění a dobu trvání časového limitu. Jakmile zaměstnanci typy v tyto informace, pozice odeslání Kariéra webu.  
  
2.  Po publikování informací můžete odeslat zúčastněným stranám jejich obnoví. Při odeslání obnovit je uložený v záznamu propojené s úvodní úlohy.  
  
3.  Žadatel můžete odeslat obnoví, dokud vyprší časový limit nebo někdo z oddělení lidských zdrojů Contoso rozhodne odeberte účtování ukončení procesu.  
  
## <a name="projects-in-the-sample"></a>Projekty v ukázce  
 V následující tabulce jsou projektů v ukázkové řešení.  
  
|Projekt|Popis|  
|-------------|-----------------|  
|ContosoHR|Obsahuje kontrakty dat, obchodní objekty a třídy úložiště.|  
|HiringRequestService|Obsahuje definici pracovního postupu proces žádosti o zařazení.<br /><br /> Tento projekt je implementovaný jako konzolovou aplikaci, která svým hostitelem pracovního postupu (souboru xaml) jako služba.|  
|ResumeRequestService|Služby pracovního postupu, který shromažďuje obnoví z kandidáty, dokud nevyprší časový limit, nebo někoho rozhodne, že proces musí být zastaven.<br /><br /> Tento projekt je implementovaný jako služby deklarativní pracovního procesu (xamlx).|  
|OrgService|Služba, která zveřejňuje organizační údaje (zaměstnanci, pozice, PositionTypes a oddělení). Tato služba si lze představit jako modulu společnosti organizace z prostředek plánování ERP (Enterprise).<br /><br /> Tento projekt je implementovaný jako konzolovou aplikaci, která zveřejňuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] služby.|  
|InboxService|Doručené pošty obsahující úkoly pro zaměstnance.<br /><br /> Tento projekt je implementovaný jako konzolovou aplikaci, která zveřejňuje služby WCF.|  
|InternalClient|Webovou aplikaci pro interakci s procesem. Uživatelé spustit, zúčastnit a zobrazit jejich HiringProcess pracovních postupů. Pomocí této aplikace, mohou také spustit a monitorovat ResumeRequest procesy.<br /><br /> Tento web je implementováno interní do intranetu společnosti Contoso. Tento projekt je implementovaný jako webu technologie ASP.NET.|  
|CareersWebSite|Externí web, který zveřejňuje otevřené pozice ve společnosti Contoso. Všechny potenciální candidate můžete přejděte na tento web a odesílání obnovení.|  
  
## <a name="feature-summary"></a>Souhrn funkcí  
 Následující tabulka popisuje použití jednotlivých funkcí v této ukázce.  
  
|Funkce|Popis|Projekt|  
|-------------|-----------------|-------------|  
|Vývojový diagram|Vývojový diagram představuje obchodní proces. Tento popis vývojový diagram představuje proces stejným způsobem, ve kterém firma by mít vykresluje ho v tabuli.|HiringRequestService|  
|Služby pracovních postupů|Vývojový diagram s definicí proces je hostovaná v službě (v tomto příkladu je služba hostována v konzolové aplikaci).|HiringRequestService|  
|Aktivity zasílání zpráv|Vývojový diagram aktivity zasílání zpráv používá dvěma způsoby:<br /><br /> – Chcete-li získat informace z (k přijímání rozhodnutí a související informace v jednotlivých kroků schválení).<br />– Chcete-li komunikovat s jinými existující službami (InboxService a OrgDataService, používá prostřednictvím odkazů na služby).|HiringRequestService|  
|Obsahu na základě korelace|Schválení zprávy korelovat na vlastnost ID náborové žádosti:<br /><br /> – V případě, že proces běží, je popisovač korelace inicializován s ID žádosti.<br />-Příchozí zprávy schválení korelovat na jejich ID (ID hledaného požadavku je první parametr každé zprávy schválení).|HiringRequestService / ResumeRequestService|  
|Vlastní aktivity (deklarativní a kódu na základě)|Existuje několik vlastních aktivit v této ukázce:<br /><br /> -   `SaveActionTracking`: Tato aktivita vysílá vlastní <xref:System.Activities.Tracking.TrackingRecord> (pomocí <xref:System.Activities.NativeActivityContext.Track%2A>). Tato aktivita byla napsána pomocí rozšíření imperativní kód <xref:System.Activities.NativeActivity>.<br />-   `GetEmployeesByPositionTypes`: Tato aktivita přijímá seznam ID typu pozice a vrátí seznam lidí, kteří mají tento pozice ve společnosti Contoso. Tato aktivita byla napsána deklarativně (použití návrháře aktivit).<br />-   `SaveHiringRequestInfo`: Tato aktivita se uloží informace `HiringRequest` (pomocí `HiringRequestRepository.Save`). Tato aktivita byla napsána pomocí rozšíření imperativní kód <xref:System.Activities.CodeActivity>.|HiringRequestService|  
|Trvalost poskytované systémem SQL Server|<xref:System.ServiceModel.Activities.WorkflowServiceHost> Instance, který je hostitelem definici vývojový diagram procesu je nakonfigurovaný na použití systému SQL Server trvalost poskytované systémem.|HiringRequestService / ResumeRequestService|  
|Vlastní sledování|Ukázka obsahuje vlastní sledování člena, který ukládá historii `HiringRequestProcess` (to zaznamenává provést akce, kdo a kdy). Zdrojový kód je ve složce Sledování HiringRequestService.|HiringRequestService|  
|Trasování událostí pro Windows Sledování|Poskytované systémem trasování událostí pro Windows Sledování je v souboru App.config v rámci služby HiringRequestService nakonfigurován.|HiringRequestService|  
|Sestavení aktivit|Definice proces používá volné složení <xref:System.Activities.Activity>. Vývojový diagram obsahuje několik pořadí a paralelní aktivity, které současně obsahovat jiné aktivity (a tak dále).|HiringRequestService|  
|Paralelní aktivity.|-   <xref:System.Activities.Statements.ParallelForEach%601>slouží k registraci v doručené poště CEO a správci oddělení lidských zdrojů paralelně (čeká na schválení krok dva HR správci).<br />-   <xref:System.Activities.Statements.Parallel>Umožňuje provést některé úlohy čištění v krocích dokončeno a byl odmítnut|HiringRequestService|  
|Zrušení modelu|Vývojový diagram používá <xref:System.Activities.Statements.CancellationScope> vytvořit zrušení chování (v tomto případě dělá některé vyčištění.)|HiringRequestService|  
|Zákaznickou stálost účastník|`HiringRequestPersistenceParticipant`ukládá data z proměnné pracovního postupu do tabulky uloženy v databázi personálního oddělení společnosti Contoso.|HiringRequestService|  
|Služby pracovních postupů|`ResumeRequestService`je implementovaná pomocí služeb pracovních postupů. Informace o pracovním postupu definice a služby je obsažený v ResumeRequestService.xamlx. Služba je nakonfigurována pro použití trvalosti a sledování.|ResumeRequestService|  
|Trvanlivý časovače|`ResumeRequestService`používá k definování dobu trvání úlohy publikování trvanlivý časovače (po vypršení časového limitu vyprší, publikování úlohy je uzavřený).|ResumeRequestService|  
|Transakce|<xref:System.Activities.Statements.TransactionScope>slouží k zajištění konzistence dat v rámci provedení několik aktivit (při přijetí nové obnovit).|ResumeRequestService|  
|Transakce|Vlastní trvalost účastník (`HiringRequestPersistenceParticipant`) a vlastní sledování účastník (`HistoryFileTrackingParticipant`) použít stejné transakci.|HiringRequestService|  
|Pomocí [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace.|Pracovní postupy jsou přístupné ze dvou [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikace.|InternalClient / CareersWebSite|  
  
## <a name="data-storage"></a>Úložiště dat  
 Data uložena v databázi systému SQL Server volá `ContosoHR` (skript pro vytvoření této databáze se nachází v `DbSetup` složku). Instance pracovního postupu jsou uložené v databázi systému SQL Server volá `InstanceStore` (skripty pro vytvoření instance úložiště jsou součástí [!INCLUDE[netfx_current_short](../../../../includes/netfx-current-short-md.md)] distribuční).  
  
 Obě databáze jsou vytvořeny pomocí skriptu Setup.cmd z [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] příkazového řádku.  
  
## <a name="running-the-sample"></a>Spuštění ukázky  
  
#### <a name="to-create-the-databases"></a>K vytvoření databáze  
  
1.  Otevřete [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] příkazového řádku.  
  
2.  Přejděte do složky ukázka.  
  
3.  Spusťte Setup.cmd.  
  
4.  Ověřte, že jsou obě databáze `ContosoHR` a `InstanceStore` byly vytvořeny v SQL Express.  
  
#### <a name="to-set-up-the-solution-for-execution"></a>Nastavit řešení pro spuštění  
  
1.  Spustit [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] jako správce. Otevřete HiringRequest.sln.  
  
2.  Pravým tlačítkem na řešení v **Průzkumníku řešení** a vyberte **vlastnosti**.  
  
3.  Vyberte možnost **více projektů po spuštění** a nastavte **CareersWebSite**, **InternalClient**, **HiringRequestService**, a **ResumeRequestService** k **spustit**. Nechte **ContosoHR**, **InboxService**, a **OrgService** jako None.  
  
4.  Sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B. Ověřte, zda sestavení proběhla úspěšně.  
  
#### <a name="to-run-the-solution"></a>Ke spuštění řešení  
  
1.  Po sestavení řešení, stiskněte CTRL + F5 a spusťte bez ladění. Ověřte, že spuštění všech služeb.  
  
2.  Klikněte pravým tlačítkem na **InternalClient** v řešení a potom vyberte **zobrazit v prohlížeči**. Výchozí stránku pro `InternalClient` se zobrazí. Ujistěte se, zda jsou spuštěny služby a klikněte na odkaz.  
  
3.  **HiringRequest** modulu se zobrazí. Můžete postupovat podle zde popsané scénáře.  
  
4.  Jednou `HiringRequest` je dokončena, můžete spustit `ResumeRequest`. Můžete postupovat podle zde popsané scénáře.  
  
5.  Když `ResumeRequest` je odesláno, je k dispozici v veřejného webu (webová stránka společnosti Contoso přenašečích). Chcete-li najdete v části publikování úlohy (a použít pro umístění), přejděte na web přenašečích.  
  
6.  Klikněte pravým tlačítkem na **CareersWebSite** v řešení a vyberte **zobrazit v prohlížeči**.  
  
7.  Přejděte zpět `InternalClient` kliknutím pravým tlačítkem na **InternalClient** v řešení a výběrem **zobrazit v prohlížeči**.  
  
8.  Přejděte na **JobPostings** část kliknutím **úlohy účtování** odkaz v horní nabídce doručené pošty. Můžete postupovat podle zde popsané scénáře.  
  
## <a name="scenarios"></a>Scénáře  
  
### <a name="hiring-request"></a>Náborové požadavku  
  
1.  Michael Alexander (pracovník softwaru) se chce požádat o nový pozice zařazení softwaru Engineer v testu (SDET) v inženýrství oddělení, který má aspoň 3 roky prostředí v jazyce C#.  
  
2.  Po vytvoření žádosti se zobrazí v doručené poště na Michael (klikněte na tlačítko **aktualizovat** Pokud nevidíte žádost) čeká na schválení Petr Brehm, který je Michael na správce.  
  
3.  Petr chce, aby se tak, aby fungoval s požadavkem na Michael. Pozice požadavky prostředí C# místo 3, 5 let uzná za tak posílá jeho komentáře zpět ke kontrole.  
  
4.  Michael ze svého správce se zobrazí zpráva v jeho doručené pošty a chce, aby se tak, aby fungoval. Michael vidí historii pozice žádosti a souhlasí s Petr. Michael popis tak, aby vyžadovala 5 let prostředí C# a přijímá úpravy.  
  
5.  Petr funguje na upravený požadavek na Michael a přijímá ho. Požadavek nyní musí schválit ředitel z technikům, Tsvi Reiter.  
  
6.  Tsvi Reiter chce urychlit žádost, proto mu převádí na komentář to znamená, že požadavek je důležitá a je přijímá ho.  
  
7.  Žádost se teď má schválení správce dvě HR nebo generálního. Generálního Brian Richard Goldstein, uvidí naléhavé požadavku pomocí Tsvi. Mu funguje u požadavku přijetím, proto obcházení schválení správci dvě oddělení lidských zdrojů.  
  
8.  Žádost se odebere ze složky Doručená pošta na Michael a nyní byl zahájen proces nástupu SDET.  
  
### <a name="start-resume-request"></a>Spuštění obnovení požadavku  
  
1.  Nyní se pozice úloha čeká na Odeslat na externí web kde uživatelé mohou použít (zobrazí se kliknutím na **úlohy účtování** odkaz). Pozice úlohy je v současné době uložený s HR zástupce, který je zodpovědný za dokončení úlohy pozice a jeho publikování.  
  
2.  HR chce upravit této pozice úlohy (kliknutím **upravit** odkaz) nastavením vypršení časového limitu 60 minut (v reálného života, může to být dny nebo týdny). Časový limit umožňuje úlohy pozici mají být provedeny mimo podle času určeného externího webu.  
  
3.  Po uložení upravených úlohy pozici, zobrazí se v **přijetí obnoví** karta (aktualizace webové stránky zobrazíte nové úlohy pozice).  
  
### <a name="collecting-resumes"></a>Shromažďování obnoví  
  
1.  Úlohy pozice se mají zobrazit na externí webovou stránku. Jako uživatel zájem o použití pro úlohu můžete použít pro tuto pozici a odeslání vašeho obnovit.  
  
2.  Pokud přejdete zpět ke službě účtování seznam úloh, můžete "Zobrazit obnoví" které byly shromážděny dosavadní práce.  
  
3.  Oddělení lidských zdrojů mohou také zastavit shromažďování obnoví (například po pravé candidate byla zjištěna).  
  
## <a name="troubleshooting"></a>Poradce při potížích  
  
1.  Ujistěte se, že používáte [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] s oprávněními správce.  
  
2.  Pokud se nepodaří řešení je sestavení, ověřte následující:  
  
    -   Odkaz na `ContosoHR` není chybí `InternalClient` nebo `CareersWebSite` projekty.  
  
3.  Pokud řešení se nepodaří spustit, ověřte následující:  
  
    1.  Všechny služby běží.  
  
    2.  Odkazy na službu jsou aktualizovány.  
  
        1.  Otevřete složku App_WebReferences  
  
        2.  Klikněte pravým tlačítkem na **Contoso** a vyberte **aktualizace nebo webové odkazy**.  
  
        3.  Znovu sestavte řešení stisknutím kombinace kláves CTRL + SHIFT + B v [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)].  
  
## <a name="uninstalling"></a>Probíhá odinstalace  
  
1.  Spuštěním Cleanup.bat, umístěný ve složce nástroj DbSetup odstraňte ukládání instance systému SQL Server.  
  
2.  Odstraňte zdrojový kód formuláře pevném disku.