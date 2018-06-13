---
title: Podnikové nákupní proces
ms.date: 03/30/2017
ms.assetid: a5e57336-4290-41ea-936d-435593d97055
ms.openlocfilehash: 34d9280fb1d4009aa729cb2eba55b817db9fff56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520039"
---
# <a name="corporate-purchase-process"></a>Podnikové nákupní proces
Tento příklad ukazuje postup vytvoření velmi základní požadavek pro návrhy (RFP) na základě nákupní proces s automatické nejlepší výběru návrhu. Spojuje v sobě <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.ParallelForEach%601>, a <xref:System.Activities.Statements.ForEach%601> a vlastních aktivit k vytvoření pracovního postupu, který představuje proces.  
  
 Tato ukázka obsahuje [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] klientskou aplikaci, která umožňuje interakci s procesem jako jiný účastníky (jako původní žadatele nebo konkrétní dodavatele).  
  
## <a name="requirements"></a>Požadavky  
  
-   [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
-   [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
## <a name="demonstrates"></a>Demonstruje  
  
-   Vlastní aktivity.  
  
-   Sestavení aktivit.  
  
-   Záložky.  
  
-   Trvalost.  
  
-   Schematized trvalost.  
  
-   Trasování.  
  
-   Ke sledování.  
  
-   Hostování [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v různých klientů ([!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webové aplikace a aplikace, WinForms).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\PurchaseProcess`  
  
## <a name="description-of-the-process"></a>Popis procesu  
 Tento příklad ukazuje implementaci programu Windows Workflow Foundation (WF) získat návrhy od dodavatelů obecné společnosti.  
  
1.  Zaměstnanec společnosti X vytvoří žádost pro návrh (RFP).  
  
    1.  Typy zaměstnanec RFP nadpis a popis.  
  
    2.  Zaměstnanec vybere dodavatelů, které chce pozvat k odeslání návrhy.  
  
2.  Zaměstnanec odešle návrh.  
  
    1.  Je vytvořena instance pracovního postupu.  
  
    2.  Pracovní postup čeká pro všechny dodavatele odeslat své návrhy.  
  
3.  Po přijetí jsou všechny návrhy, pracovní postup iteruje všechny přijaté návrhy a vybere nejlepší.  
  
    1.  Jednotlivých dodavatelů má dobré jméno (Tato ukázka ukládá seznam ztrátou dobré pověsti VendorRepository.cs).  
  
    2.  Celkovou hodnotu návrhu je dáno (hodnota zadali od dodavatele) * (dodavatele je zaznamenávají ztrátou dobré pověsti) / 100.  
  
4.  Původní žadatele můžete zobrazit všechny odeslané návrhy. Nejlepší návrhu jsou poskytovány speciální oddíl v sestavě.  
  
## <a name="process-definition"></a>Definice procesu  
 Základní logika vzorku použije <xref:System.Activities.Statements.ParallelForEach%601> aktivity, která čeká na nabídky od jednotlivých dodavatelů (s použitím vlastní aktivitu, která vytvoří záložku), a zaregistruje návrh dodavatele jako RFP (pomocí <xref:System.Activities.Statements.InvokeMethod> aktivity).  
  
 Ukázka pak iteruje všechny přijaté návrhů uložené v `RfpRepository`, výpočet upravená hodnota (pomocí <xref:System.Activities.Statements.Assign> aktivity a <xref:System.Activities.Expressions> aktivity), a pokud upravená hodnota je lepší, než předchozí nejlepší nabídku, přiřadí novou hodnotu jako nejlepší nabídka (pomocí <xref:System.Activities.Statements.If> a <xref:System.Activities.Statements.Assign> aktivit).  
  
## <a name="projects-in-this-sample"></a>Projekty v této ukázce  
 Tato ukázka obsahuje následující projekty.  
  
|Projekt|Popis|  
|-------------|-----------------|  
|Běžné|Objekty entity v rámci procesu (žádost o návrhu, dodavatele a návrh dodavatele).|  
|WfDefinition|Definice procesu (jako [!INCLUDE[wf1](../../../../includes/wf1-md.md)] programu) a hostitele (`PurchaseProcessHost`) použít v klientských aplikacích pro vytváření a používání instancí pracovního postupu procesu nákupu.|  
|Webový klient|[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Klientskou aplikaci, která umožňuje uživatelům vytvářet a účastnit instancí procesu nákupu. Vytvořit vlastní hostitele používá k interakci se modul pracovních postupů.|  
|WinFormsClient|Klientská aplikace Windows Forms, který umožňuje uživatelům vytvářet a účastnit instancí procesu nákupu. Vytvořit vlastní hostitele používá k interakci se modul pracovních postupů.|  
  
### <a name="wfdefinition"></a>WfDefinition  
 Následující tabulka obsahuje popis nejdůležitější soubory v projektu WfDefinition.  
  
|Soubor|Popis|  
|----------|-----------------|  
|IPurchaseProcessHost.cs|Rozhraní pro hostitele pracovního postupu.|  
|PurchaseProcessHost.cs|Implementace hostitele pro pracovní postup. Hostitel abstrahuje podrobnosti o modulu runtime pracovního postupu a používá se v klientské aplikace k načítání, spuštění a interakci s `PurchaseProcess` instance pracovního postupu.|  
|PurchaseProcessWorkflow.cs|Aktivitu, která obsahuje definici pracovního postupu procesu nákupu (odvozená z <xref:System.Activities.Activity>).<br /><br /> Aktivity, které jsou odvozeny od <xref:System.Activities.Activity> tvoří sestavte existující vlastní funkce a aktivity z [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] knihovna aktivit. Ty se tyto aktivity je nejzákladnější způsob, jak vytvořit vlastní funkce.|  
|WaitForVendorProposal.cs|Tato vlastní aktivita je odvozena z <xref:System.Activities.NativeActivity> a vytvoří pojmenované záložka, která musí být obnoven, později dodavatelem při odesílání návrh.<br /><br /> Aktivity, které jsou odvozeny od <xref:System.Activities.NativeActivity>, jako jsou ty, které jsou odvozeny od <xref:System.Activities.CodeActivity>, vytvořit imperativní funkce přepsáním <xref:System.Activities.NativeActivity.Execute%2A>, ale také mají přístup ke všem funkci modulu runtime pracovního postupu prostřednictvím <xref:System.Activities.ActivityContext> , který získá předaný do `Execute` metoda. Tento kontext se podpora pro plánování a zrušení zachovat ne aktivity, nastavení podřízené zóny (bloky provádění během které modulu runtime není zachována dat pracovního postupu, například v rámci atomic transakcí), a <xref:System.Activities.Bookmark> objekty (obslužné rutiny pro obnovení pozastavených pracovních postupů).|  
|TrackingParticipant.cs|A <xref:System.Activities.Tracking.TrackingParticipant> který přijímá všechny události sledování a uloží je do textového souboru.<br /><br /> Sledování účastníků jsou přidány do instance pracovního postupu jako rozšíření.|  
|XmlWorkflowInstanceStore.cs|Vlastní <xref:System.Runtime.DurableInstancing.InstanceStore> , uloží pracovní postup aplikace do souborů XML.|  
|XmlPersistenceParticipant.cs|Vlastní <xref:System.Activities.Persistence.PersistenceParticipant> instance požadavku pro návrh, uloží do souboru XML.|  
|AsyncResult.cs / CompletedAsyncResult.cs|Pomocné třídy pro implementaci asynchronního vzoru v součásti trvalost.|  
  
### <a name="common"></a>Běžné  
 Následující tabulka obsahuje popis nejdůležitější tříd v běžné projektu.  
  
|Třída|Popis|  
|-----------|-----------------|  
|Dodavatele|Výrobce, který odešle návrhy v požadavku pro návrhy.|  
|RequestForProposal|Žádost o návrhy (RFP) je pozvánka dodavatelé odeslat návrhy na konkrétní komoditním nebo službě.|  
|VendorProposal|Návrh dodavatele a konkrétní RFP.|  
|VendorRepository|Úložiště dodavatelů. Tato implementace obsahuje kolekci v paměti instancí dodavatele a metody pro vystavení těchto instancí.|  
|RfpRepository|Úložiště požadavků pro návrhy. Tato implementace obsahuje používá technologie Linq to XML do souboru XML požadavků pro návrh vytvořený schematized trvalost dotazu. Tato třída implementuje [System.Runtime.Persistence.IDataViewMapper](https://msdn.microsoft.com/library/system.runtime.persistence.idataviewmapper(v=vs.110).aspx).|  
|IOHelper|Tato třída zpracovává všechny I/E problémy související s (složky, cesty a atd.)|  
  
### <a name="web-client"></a>Webový klient  
 Následující tabulka obsahuje popis nejdůležitější webových stránek v projektu webového klienta.  
  
|Soubor|Popis|  
|-|-|  
|CreateRfp.aspx|Vytvoří a odešle nová žádost o návrhy.|  
|Default.aspx|Zobrazí všechny aktivní a dokončené žádosti o návrhy.|  
|GetVendorProposal.aspx|Získá návrh od dodavatele v požadavku konkrétní pro návrhy. Tato stránka slouží jenom prodejci.|  
|ShowRfp.aspx|Zobrazit všechny informace o požadavku pro návrhy (přijaté návrhy, kalendářních dat, hodnoty a další informace). Tato stránka se používá pouze pomocí Tvůrce požadavku pro návrh.|  
  
### <a name="winforms-client"></a>WinForms klienta  
 Následující tabulka obsahuje popis nejdůležitější formuláře do projektu Win Forms.  
  
|Formulář|Popis|  
|-|-|  
|NewRfp|Vytvoří a odešle nová žádost o návrhy.|  
|ShowProposals|Zobrazit všechny aktivní a dokončení žádosti o návrhy. **Poznámka:** pravděpodobně třeba kliknout na **aktualizovat** tlačítko v uživatelském rozhraní a podívejte se změny na této obrazovce po vytvoření nebo úpravě žádost o návrhu.|  
|SubmitProposal|Návrh získáte od dodavatele v požadavku konkrétní pro návrhy. Toto okno se používá pouze prodejci.|  
|ViewRfp|Zobrazit všechny informace o požadavku pro návrhy (přijaté návrhy, kalendářních dat, hodnoty a další informace). Toto okno Tvůrce požadavek použít pouze pro návrhy.|  
  
### <a name="persistence-files"></a>Trvalé soubory  
 Následující tabulka uvádí soubory generované trvalost zprostředkovatele (`XmlPersistenceProvider`) jsou umístěné v cestě k dočasné složce v aktuálním systému (pomocí <xref:System.IO.Path.GetTempPath%2A>). Soubor trasování se vytvoří v aktuální cestě provádění.  
  
|Název souboru|Popis|Cesta|  
|-|-|-|  
|rfps.XML|Soubor XML s všechny aktivní a dokončení žádosti pro návrhy.|<xref:System.IO.Path.GetTempPath%2A>|  
|[identifikátor instanceid]|Tento soubor obsahuje všechny informace o instanci pracovního postupu.<br /><br /> Tento soubor je generován implementace schematized trvalost (PersistenceParticipant v XmlPersistenceProvider).|<xref:System.IO.Path.GetTempPath%2A>|  
|.tracking [identifikátor instanceId]|Textový soubor s všechny události, k nimž došlo v rámci konkrétní instance.<br /><br /> Tento soubor je generován TrackingParticipant.|<xref:System.IO.Path.GetTempPath%2A>|  
|PurchaseProcess.Tracing.TraceLog.txt|Soubor trasování, který byl vytvořen v tomto pracovním postupu, na základě parametrů konfigurace v souborech App.config nebo Web.config.|Aktuální cestě provádění|  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení PurchaseProcess.sln.  
  
2.  Chcete-li spustit projekt webového klienta, otevřete **Průzkumníku řešení** a klikněte pravým tlačítkem **webového klienta** projektu. Vyberte **nastavit jako spouštěný projekt**.  
  
3.  K provedení WinForms klientského projektu, otevřete **Průzkumníku řešení** a klikněte pravým tlačítkem **WinForms klienta** projektu. Vyberte **nastavit jako spouštěný projekt**.  
  
4.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
5.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
### <a name="web-client-options"></a>Možnosti webového klienta  
  
-   **Vytvořit nový RFP**: vytvoří novou žádost o pro návrhy (RFP) a spustí pracovní postup procesu nákupu.  
  
-   **Aktualizujte**: aktualizuje seznam aktivní a dokončení RFPs v hlavním okně.  
  
-   **Zobrazení**: Zobrazí obsah existující RFP. Dodavatelé mohou odesílat své návrhy (Pokud jste pozvánku, nebo nebylo dokončeno RFP).  
  
-   Zobrazení jako: Má uživatel přístup RFP pomocí různých identit výběrem požadované účastnit **zobrazit jako** – pole se seznamem v mřížce active RFPs.  
  
### <a name="winforms-client-options"></a>Možnosti WinForms klienta  
  
-   **Vytvoření RFP**: vytvoří novou žádost o pro návrhy (RFP) a spustí pracovní postup procesu nákupu.  
  
-   **Aktualizujte**: aktualizuje seznam aktivní a dokončení RFPs v hlavním okně.  
  
-   **Zobrazit RFP**: Zobrazí obsah existující RFP. Dodavatelé mohou odesílat své návrhy (Pokud jste pozvánku, nebo nebylo dokončeno RFP)  
  
-   **Připojit jako**: má uživatel přístup RFP pomocí různých identit výběrem požadované účastnit **zobrazit jako** – pole se seznamem v mřížce active RFPs.