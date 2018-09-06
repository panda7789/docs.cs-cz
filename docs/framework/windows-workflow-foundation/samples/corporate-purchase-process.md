---
title: Proces nákupu v podniku
ms.date: 03/30/2017
ms.assetid: a5e57336-4290-41ea-936d-435593d97055
ms.openlocfilehash: a5e0d6191967c592d5a32baa7eee3f1659a27e50
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43802908"
---
# <a name="corporate-purchase-process"></a>Proces nákupu v podniku
Tento příklad ukazuje, jak vytvořit velmi základní požadavek na proces nákupu návrhy (RFP) na základě s automatický výběr nejlepší návrh. Kombinuje <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.ParallelForEach%601>, a <xref:System.Activities.Statements.ForEach%601> a vlastní aktivitu pro vytvoření pracovního postupu, který představuje proces.  
  
 Tato ukázka obsahuje [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] klientskou aplikaci, která umožňuje komunikaci s procesem jako jiný účastníky (jako původní žadatel nebo konkrétního dodavatele).  
  
## <a name="requirements"></a>Požadavky  
  
-   [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)].  
  
-   [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].  
  
## <a name="demonstrates"></a>Demonstruje  
  
-   Vlastní aktivity.  
  
-   Složení aktivit.  
  
-   Záložky.  
  
-   Trvalost.  
  
-   Schematizovanými trvalosti.  
  
-   Trasování.  
  
-   Sledování.  
  
-   Hostování [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v různých klientů ([!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] webových aplikací a aplikací WinForms).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Application\PurchaseProcess`  
  
## <a name="description-of-the-process"></a>Popis procesu  
 Tento příklad ukazuje implementaci pro program Windows Workflow Foundation (WF) ke shromáždění návrhy od dodavatelů obecný společnosti.  
  
1.  Zaměstnanec společnosti X vytvoří žádost pro návrh (RFP).  
  
    1.  Typy zaměstnanců poptávku (RFP) název a popis.  
  
    2.  Zaměstnanec vybere dodavatelů, které chce odeslat návrhy pozvat.  
  
2.  Zaměstnanec odešle návrh.  
  
    1.  Je vytvořena instance pracovního postupu.  
  
    2.  Pracovní postup čeká všichni dodavatelé odesílat své návrhy.  
  
3.  Po přijetí jsou všechny návrhy, pracovní postup projde všechny přijaté návrhy a vybere ten nejvhodnější.  
  
    1.  Jednotlivých dodavatelů má pověst (Tato ukázka ukládá seznam pověst VendorRepository.cs).  
  
    2.  Celková hodnota návrh je určeno (hodnotu zadanou v dodavatelem) * (dodavatele uživatele zaznamenaná pověst) / 100.  
  
4.  Původní žadatel můžete zobrazit všechny odeslané návrhy. Nejlepší návrh se zobrazí v části speciální v sestavě.  
  
## <a name="process-definition"></a>Definice procesu  
 Používá základní logiku ukázky <xref:System.Activities.Statements.ParallelForEach%601> aktivitu, která čeká na nabídky od každého dodavatele (s použitím vlastní aktivitu, která vytvoří záložku), a registruje návrh dodavatele jako poptávku (RFP) (pomocí <xref:System.Activities.Statements.InvokeMethod> aktivit).  
  
 Ukázka pak Iteruje přes všechny přijaté návrhy uložené v `RfpRepository`, výpočtu upravená hodnota (pomocí <xref:System.Activities.Statements.Assign> aktivity a <xref:System.Activities.Expressions> aktivity), a pokud upravená hodnota je lepší než předchozí nejlepší nabídky přiřadí hodnotu nové doporučené nabídky (pomocí <xref:System.Activities.Statements.If> a <xref:System.Activities.Statements.Assign> aktivit).  
  
## <a name="projects-in-this-sample"></a>Projekty v této ukázce  
 Tato ukázka obsahuje následující projekty.  
  
|Projekt|Popis|  
|-------------|-----------------|  
|Běžné|Objekty entity používané v rámci procesu (žádost o návrh, výrobce a dodavatele návrh).|  
|WfDefinition|Definice procesu (jako [!INCLUDE[wf1](../../../../includes/wf1-md.md)] programu) a hostitele (`PurchaseProcessHost`) používají klientské aplikace pro vytváření a používání instancí pracovního procesu nákupu.|  
|Webový klient|[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] Klientskou aplikaci, která umožňuje uživatelům vytvořit a účast v instancích služby procesu nákupu. Vytvoření vlastního hostitele se používá k interakci s modul pracovních postupů.|  
|WinFormsClient|Klientská aplikace Windows Forms, který umožňuje uživatelům vytvořit a účast v instancích služby procesu nákupu. Vytvoření vlastního hostitele se používá k interakci s modul pracovních postupů.|  
  
### <a name="wfdefinition"></a>WfDefinition  
 Následující tabulka obsahuje popis nejdůležitější soubory v projektu WfDefinition.  
  
|Soubor|Popis|  
|----------|-----------------|  
|IPurchaseProcessHost.cs|Rozhraní pro hostitele pracovního postupu.|  
|PurchaseProcessHost.cs|Implementace hostitele pracovního postupu. Hostitel získává podrobnosti modulu runtime pracovního postupu a používá se v klientských aplikacích načíst, spuštění a interakci s `PurchaseProcess` instancí pracovních postupů.|  
|PurchaseProcessWorkflow.cs|Aktivita, která obsahuje definice pracovního procesu nákupu (je odvozena z <xref:System.Activities.Activity>).<br /><br /> Aktivity, které jsou odvozeny z <xref:System.Activities.Activity> compose funkce sloučením existující vlastní aktivity a aktivit [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] knihovny aktivit. Tyto aktivity sestavení je nejzákladnější možnost pro vytvoření vlastní funkce.|  
|WaitForVendorProposal.cs|Tato vlastní aktivita je odvozena z <xref:System.Activities.NativeActivity> a vytvoří pojmenovaný záložku, která musí být obnoveno později dodavatelem při odesílání návrh.<br /><br /> Aktivity, které jsou odvozeny z <xref:System.Activities.NativeActivity>, jako jsou ty, které jsou odvozeny z <xref:System.Activities.CodeActivity>, vytvořit imperativní funkce tak, že přepíšete <xref:System.Activities.NativeActivity.Execute%2A>, ale také mají přístup ke všem funkce modulu runtime pracovního postupu pomocí <xref:System.Activities.ActivityContext> , který získá předán `Execute` metody. Tento kontext zahrnuje podporu pro plánování a zrušení podřízené aktivity, nastavení bez zachování zóny (zablokuje spuštění během které modul runtime není zachována data pro pracovní postupy, jako například v rámci atomické transakce), a <xref:System.Activities.Bookmark> objekty (obslužné rutiny pro obnovení pozastavených pracovních postupů).|  
|TrackingParticipant.cs|A <xref:System.Activities.Tracking.TrackingParticipant> , který přijímá všechny události sledování a uloží je do textového souboru.<br /><br /> Sledování účastníci se přidají do instance pracovního postupu jako rozšíření.|  
|XmlWorkflowInstanceStore.cs|Vlastní <xref:System.Runtime.DurableInstancing.InstanceStore> , která ukládá aplikací pracovních postupů do souborů XML.|  
|XmlPersistenceParticipant.cs|Vlastní <xref:System.Activities.Persistence.PersistenceParticipant> instance žádosti pro návrh, který uloží do souboru XML.|  
|AsyncResult.cs / CompletedAsyncResult.cs|Pomocné třídy pro implementaci asynchronního vzoru v součástech trvalosti.|  
  
### <a name="common"></a>Běžné  
 Následující tabulka obsahuje popis nejdůležitější tříd v běžných projektu.  
  
|Třída|Popis|  
|-----------|-----------------|  
|Dodavatele|Dodavatel, který odešle návrhů v požadavku pro návrhy.|  
|RequestForProposal|Pozvánku pro dodavatele odeslat návrhy na konkrétní zboží nebo služeb je požadavek pro návrhy (RFP).|  
|VendorProposal|Návrh dodavatele a konkrétní poptávku (RFP).|  
|VendorRepository|Úložiště dodavatele. Tato implementace obsahuje kolekci v paměť instancí dodavatele a metody pro vystavení tyto instance.|  
|RfpRepository|Úložiště požadavky pro návrhy. Tato implementace obsahuje použití Linq to XML do souboru XML požadavků pro návrh vytvořený schematizovanými trvalost dotazu. Tato třída implementuje [System.Runtime.Persistence.IDataViewMapper](https://msdn.microsoft.com/library/system.runtime.persistence.idataviewmapper(v=vs.110).aspx).|  
|IOHelper|Tato třída zpracovává všechny můžu/O otázky související se (složky, cesty a atd.)|  
  
### <a name="web-client"></a>Webový klient  
 Následující tabulka obsahuje popis nejdůležitější webové stránky v projektu webového klienta.  
  
|Soubor|Popis|  
|-|-|  
|CreateRfp.aspx|Vytvoří a odešle novou žádost o návrhy.|  
|Default.aspx|Zobrazuje všechny aktivní a dokončené žádosti o návrhy.|  
|GetVendorProposal.aspx|Získá návrh od dodavatele v požadavku konkrétní pro návrhy. Tato stránka slouží jenom podle dodavatele.|  
|ShowRfp.aspx|Zobrazit všechny informace o požadavku pro návrhy (přijaté návrhy, data, hodnoty a další informace). Tato stránka slouží pouze tvůrcem požadavku pro návrh.|  
  
### <a name="winforms-client"></a>WinForms klienta  
 Následující tabulka obsahuje popis nejdůležitější formuláře v projektu Windows Forms.  
  
|Formulář|Popis|  
|-|-|  
|NewRfp|Vytvoří a odešle novou žádost o návrhy.|  
|ShowProposals|Zobrazit všechny aktivní a dokončení žádosti o návrhy. **Poznámka:** budete možná muset kliknout na **aktualizovat** tlačítko v uživatelském rozhraní pro zobrazení změn na této obrazovce, po vytvoření nebo úpravě žádost o návrhu.|  
|SubmitProposal|Návrh získáte od dodavatele v požadavku konkrétní pro návrhy. Toto okno se používá pouze podle dodavatele.|  
|ViewRfp|Zobrazit všechny informace o požadavku pro návrhy (přijaté návrhy, data, hodnoty a další informace). V tomto okně Tvůrce požadavku použít jenom pro návrhy.|  
  
### <a name="persistence-files"></a>Trvalé soubory  
 V následující tabulce jsou uvedeny soubory generované záznamem pro poskytovatele trvalého chování (`XmlPersistenceProvider`) jsou umístěny v cestě z aktuálního systému dočasné složky (pomocí <xref:System.IO.Path.GetTempPath%2A>). V aktuální cestě spuštění se vytvoří soubor trasování.  
  
|Název souboru|Popis|Cesta|  
|-|-|-|  
|rfps.XML|Soubor XML se všechny aktivní a dokončení žádosti pro návrhy.|<xref:System.IO.Path.GetTempPath%2A>|  
|[instanceid]|Tento soubor obsahuje všechny informace o instanci pracovního postupu.<br /><br /> Tento soubor vygenerovala sada implementace schematizovanými trvalého (PersistenceParticipant v XmlPersistenceProvider).|<xref:System.IO.Path.GetTempPath%2A>|  
|.tracking [instanceId]|Textový soubor s všechny události, ke kterým došlo v rámci konkrétní instance.<br /><br /> Tento soubor vygenerovala sada TrackingParticipant.|<xref:System.IO.Path.GetTempPath%2A>|  
|PurchaseProcess.Tracing.TraceLog.txt|Soubor trasování vygenerovaná pracovního postupu na základě parametrů konfigurace v souboru App.config nebo Web.config.|Aktuální cesta provedení|  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení PurchaseProcess.sln.  
  
2.  Chcete-li spustit projekt webového klienta, otevřete **Průzkumníku řešení** a klikněte pravým tlačítkem myši **webového klienta** projektu. Vyberte **nastavit jako spouštěný projekt**.  
  
3.  Chcete-li spustit WinForms klientský projekt, otevřete **Průzkumníka řešení** a klikněte pravým tlačítkem na **WinForms klienta** projektu. Vyberte **nastavit jako spouštěný projekt**.  
  
4.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
5.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
### <a name="web-client-options"></a>Možnosti webového klienta  
  
-   **Vytvořit nový poptávku (RFP)**: vytvoří novou žádost o, pro návrhy (RFP) a spustí pracovní postup procesu nákupu.  
  
-   **Aktualizovat**: aktualizuje seznam aktivních a dokončení RFPs v hlavním okně.  
  
-   **Zobrazení**: Zobrazí obsah existujícího poptávku (RFP). Dodavatelé mohou odesílat své návrhy (Pokud pozváni nebo není dokončen poptávku (RFP)).  
  
-   Zobrazit jako: Má uživatel přístup poptávku (RFP) pomocí jiné identity tak, že vyberete požadovaný účastník **zobrazit jako** – pole se seznamem v mřížce RFPs aktivní.  
  
### <a name="winforms-client-options"></a>Možnosti klienta WinForms  
  
-   **Vytvoření poptávku (RFP)**: vytvoří novou žádost o, pro návrhy (RFP) a spustí pracovní postup procesu nákupu.  
  
-   **Aktualizovat**: aktualizuje seznam aktivních a dokončení RFPs v hlavním okně.  
  
-   **Zobrazit poptávku (RFP)**: Zobrazí obsah existujícího poptávku (RFP). Dodavatelé mohou odesílat své návrhy (Pokud pozváni nebo není dokončen poptávku (RFP))  
  
-   **Připojit jako**: poptávku (RFP) pomocí jiné identity tak, že vyberete požadovaný účastník může uživatel **zobrazit jako** – pole se seznamem v mřížce RFPs aktivní.