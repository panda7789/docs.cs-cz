---
title: Proces nákupu v podniku
ms.date: 03/30/2017
ms.assetid: a5e57336-4290-41ea-936d-435593d97055
ms.openlocfilehash: 93cfc3546fc312f046c4a5e1dd63dfb357f143c4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182875"
---
# <a name="corporate-purchase-process"></a>Proces nákupu v podniku
Tato ukázka ukazuje, jak vytvořit velmi základní proces nákupu založený na požadavku na návrhy (RFP) s automatickým výběrem nejlepšího návrhu. Kombinuje <xref:System.Activities.Statements.Parallel>, <xref:System.Activities.Statements.ParallelForEach%601>a <xref:System.Activities.Statements.ForEach%601> a vlastní aktivitu k vytvoření pracovního postupu, který představuje proces.

 Tato ukázka obsahuje ASP.NET klientské aplikace, která umožňuje interakci s procesem jako různí účastníci (jako původní žadatel nebo konkrétní dodavatel).

## <a name="requirements"></a>Požadavky

- Visual Studio 2012.

- [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)].

## <a name="demonstrates"></a>Demonstruje

- Vlastní aktivity.

- Složení činností.

- Záložky.

- Trvalosti.

- Schematizovaná trvalosti.

- Trasování.

- Sledování.

- Hostování [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v různých klientech (ASP.NET webových aplikací a aplikací WinForms).

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Application\PurchaseProcess`  
  
## <a name="description-of-the-process"></a>Popis procesu  
 Tato ukázka ukazuje implementaci programu Windows Workflow Foundation (WF) shromažďovat návrhy od dodavatelů pro obecnou společnost.  
  
1. Zaměstnanec společnosti X vytvoří požadavek na návrh (RFP).  
  
    1. Typy zaměstnanců v názvu a popisu RFP.  
  
    2. Zaměstnanec vybere dodavatele, které chce pozvat k odeslání návrhů.  
  
2. Zaměstnanec předloží návrh.  
  
    1. Je vytvořena instance pracovního postupu.  
  
    2. Pracovní postup čeká na všechny dodavatele, aby předložili své návrhy.  
  
3. Po přijetí všech návrhů pracovní postup pronese všechny přijaté návrhy a vybere ten nejlepší.  
  
    1. Každý dodavatel má pověst (tato ukázka ukládá seznam reputace v VendorRepository.cs).  
  
    2. Celková hodnota návrhu je určena (Hodnota zapsaná dodavatelem) * (Zaznamenaná reputace dodavatele) / 100.  
  
4. Původní žadatel může zobrazit všechny předložené návrhy. Nejlepší návrh je předložen ve zvláštní části zprávy.  
  
## <a name="process-definition"></a>Definice procesu  
 Základní logika ukázky <xref:System.Activities.Statements.ParallelForEach%601> používá aktivitu, která čeká na nabídky od každého dodavatele (pomocí vlastní aktivity, která vytvoří záložku) a zaregistruje návrh dodavatele jako RFP (pomocí <xref:System.Activities.Statements.InvokeMethod> aktivity).  
  
 Vzorek pak itetuje všechny přijaté návrhy `RfpRepository`uložené v , výpočet upravené <xref:System.Activities.Statements.Assign> hodnoty <xref:System.Activities.Expressions> (pomocí aktivity a činnosti), a pokud upravená hodnota je lepší než <xref:System.Activities.Statements.If> předchozí <xref:System.Activities.Statements.Assign> nejlepší nabídka, přiřadí novou hodnotu jako nejlepší nabídku (použití a činnosti).  
  
## <a name="projects-in-this-sample"></a>Projekty v této ukázce  
 Tato ukázka obsahuje následující projekty.  
  
|Project|Popis|  
|-------------|-----------------|  
|Společné|Objekty entity použité v rámci procesu (Požadavek na návrh, Dodavatel a Návrh dodavatele).|  
|Definice Wf|Definice procesu (jako [!INCLUDE[wf1](../../../../includes/wf1-md.md)] programu) a`PurchaseProcessHost`hostitele ( ) používaná klientskými aplikacemi pro vytváření a používání instancí pracovního postupu nákupního procesu.|  
|Webclient|Klientská aplikace ASP.NET, která umožňuje uživatelům vytvářet a účastnit se instancí procesu nákupu. Používá vlastní vytvořený hostitel pro interakci s motorem pracovního postupu.|  
|Klient WinFormsClient|Klientská aplikace Windows Forms, která umožňuje uživatelům vytvářet a účastnit se instancí procesu nákupu. Používá vlastní vytvořený hostitel pro interakci s motorem pracovního postupu.|  
  
### <a name="wfdefinition"></a>Definice Wf  
 Následující tabulka obsahuje popis nejdůležitějších souborů v projektu WfDefinition.  
  
|File|Popis|  
|----------|-----------------|  
|IPurchaseProcessHost.cs|Rozhraní pro hostitele pracovního postupu.|  
|PurchaseProcessHost.cs|Implementace hostitele pro pracovní postup. Hostitel abstrahuje podrobnosti o běhu pracovního postupu a používá se ve `PurchaseProcess` všech klientských aplikacích k načtení, spuštění a interakci s instancemi pracovního postupu.|  
|PurchaseProcessWorkflow.cs|Aktivita, která obsahuje definici pracovního postupu <xref:System.Activities.Activity>Nákupní proces (odvozená z).<br /><br /> Aktivity, <xref:System.Activities.Activity> které jsou odvozeny z skládání funkce sestavením existující vlastní aktivity a aktivity z knihovny [!INCLUDE[netfx_current_long](../../../../includes/netfx-current-long-md.md)] aktivit. Sestavení těchto aktivit je nejzákladnější způsob, jak vytvořit vlastní funkce.|  
|WaitForVendorProposal.cs|Tato vlastní aktivita <xref:System.Activities.NativeActivity> je odvozena od a vytvoří pojmenovanou záložku, kterou musí dodavatel při odesílání návrhu obnovit později.<br /><br /> Aktivity, <xref:System.Activities.NativeActivity>které jsou odvozeny <xref:System.Activities.CodeActivity>z , jako jsou <xref:System.Activities.NativeActivity.Execute%2A>ty, které jsou odvozeny z , vytvořit imperativní funkce přepsáním , ale také mají přístup ke všem funkcím runtime pracovního postupu prostřednictvím <xref:System.Activities.ActivityContext> který získá předán do `Execute` metody. Tento kontext má podporu pro plánování a rušení podřízených aktivit, nastavení bez trvalé zóny (bloky spuštění, během kterého modul <xref:System.Activities.Bookmark> runtime nepřetrvává data pracovního postupu, například v rámci atomických transakcí) a objekty (popisovače pro obnovení pozastavené pracovní postupy).|  
|TrackingParticipant.cs|A, <xref:System.Activities.Tracking.TrackingParticipant> který obdrží všechny události sledování a uloží je do textového souboru.<br /><br /> Sledování účastníků jsou přidány do instance pracovního postupu jako rozšíření.|  
|XmlWorkflowInstanceStore.cs|Vlastní, <xref:System.Runtime.DurableInstancing.InstanceStore> který ukládá aplikace pracovního postupu do souborů XML.|  
|XmlPersistenceParticipant.cs|Vlastní, <xref:System.Activities.Persistence.PersistenceParticipant> který ukládá instanci požadavku na návrh do souboru XML.|  
|AsyncResult.cs / CompletedAsyncResult.cs|Pomocné třídy pro implementaci asynchronní vzor v součásti trvalosti.|  
  
### <a name="common"></a>Společné  
 Následující tabulka obsahuje popis nejdůležitějších tříd v projektu Common.  
  
|Třída|Popis|  
|-----------|-----------------|  
|Dodavatel|Dodavatel, který předkládá návrhy v žádosti o návrhy.|  
|RequestforProposal|Žádost o návrhy (RFP) je výzva pro dodavatele, aby předložili návrhy na konkrétní komoditu nebo službu.|  
|Návrh dodavatele|Návrh předložený dodavatelem konkrétnímu rfp.|  
|VendorRepository|Úložiště dodavatelů. Tato implementace obsahuje kolekci instanci instancí Vendor a metody pro vystavení těchto instancí.|  
|RfpRepository|Úložiště žádostí o návrhy. Tato implementace obsahuje používá Linq na XML k dotazování souboru XML požadavků na návrh generovaných schematizovanou trvalost. |  
|IOHelper|Tato třída zpracovává všechny problémy související s vstupně-va (složky, cesty a tak dále.)|  
  
### <a name="web-client"></a>Webový klient  
 Následující tabulka obsahuje popis nejdůležitějších webových stránek v projektu webového klienta.  
  
|File|Popis|  
|-|-|  
|VytvořitRfp.aspx|Vytvoří a odešle novou žádost o návrhy.|  
|Default.aspx|Zobrazí všechny aktivní a dokončené žádosti o návrhy.|  
|GetVendorProposal.aspx|Získá návrh od dodavatele v konkrétní požadavek na návrhy. Tuto stránku používají pouze dodavatelé.|  
|ZobrazitRfp.aspx|Zobrazí všechny informace o žádosti o návrhy (přijaté návrhy, data, hodnoty a další informace). Tuto stránku používá pouze tvůrce žádosti o návrh.|  
  
### <a name="winforms-client"></a>Klient WinForms  
 Následující tabulka obsahuje popis nejdůležitějších formulářů v projektu Win Forms.  
  
|Formulář|Popis|  
|-|-|  
|NewRfp|Vytvoří a odešle novou žádost o návrhy.|  
|Zobrazit návrhy|Zobrazí všechny aktivní a dokončené požadavky na návrhy. **Poznámka:**  Možná budete muset klepnout na tlačítko **Aktualizovat** v unovém uzem, abyste viděli změny na této obrazovce po vytvoření nebo úpravě požadavku na návrh.|  
|Odeslatnávrh|Získejte návrh od dodavatele v konkrétní žádosti o návrhy. Toto okno používají pouze dodavatelé.|  
|Zobrazitrfp|Zobrazí všechny informace o žádosti o návrhy (přijaté návrhy, data, hodnoty a další informace). Toto okno používá pouze tvůrce žádosti o návrhy.|  
  
### <a name="persistence-files"></a>Soubory trvalosti  
 V následující tabulce jsou uvedeny soubory generované`XmlPersistenceProvider`zprostředkovatelem trvalosti ( ) jsou umístěny <xref:System.IO.Path.GetTempPath%2A>v cestě dočasné složky aktuálního systému (pomocí ). Trasovací soubor je vytvořen v aktuální cestě spuštění.  
  
|Název souboru|Popis|Cesta|  
|-|-|-|  
|rfps.xml|Soubor XML se všemi aktivními a dokončenými požadavky na návrhy.|<xref:System.IO.Path.GetTempPath%2A>|  
|[instanceid]|Tento soubor obsahuje všechny informace o instanci pracovního postupu.<br /><br /> Tento soubor je generován schematizovanou implementací trvalosti (PersistenceParticipant v XmlPersistenceProvider).|<xref:System.IO.Path.GetTempPath%2A>|  
|[instanceId].sledování|Textový soubor se všemi událostmi, ke kterým došlo v rámci konkrétní instance.<br /><br /> Tento soubor je generován TrackingParticipant.|<xref:System.IO.Path.GetTempPath%2A>|  
|PurchaseProcess.Tracing.TraceLog.txt|Trasovací soubor generovaný pracovním postupem na základě konfiguračních parametrů v souborech App.config nebo Web.config.|Aktuální cesta spuštění|  
  
#### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek  
  
1. Pomocí sady Visual Studio 2010 otevřete soubor řešení PurchaseProcess.sln.  
  
2. Chcete-li spustit projekt webového klienta, otevřete **Průzkumníka řešení** a klepněte pravým tlačítkem myši na projekt **webového klienta.** Vyberte **možnost Nastavit jako spouštěcí projekt**.  
  
3. Chcete-li spustit projekt klienta WinForms, otevřete **Průzkumníka řešení** a klepněte pravým tlačítkem myši na projekt **klienta WinForms.** Vyberte **možnost Nastavit jako spouštěcí projekt**.  
  
4. Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.  
  
5. Chcete-li řešení spustit, stiskněte kombinaci kláves CTRL+F5.  
  
### <a name="web-client-options"></a>Možnosti webového klienta  
  
- **Vytvoření nového rfp:** Vytvoří nový požadavek na návrhy (RFP) a spustí pracovní postup procesu nákupu.  
  
- **Aktualizace**: Aktualizuje seznam aktivních a dokončených programů RFP v hlavním okně.  
  
- **Zobrazení**: Zobrazuje obsah existujícího rfp. Dodavatelé mohou předložit své návrhy (pokud jsou pozváni nebo RFP není dokončen).  
  
- Zobrazit jako: Uživatel může přistupovat k RFP pomocí různých identit výběrem požadovaného účastníka v poli **Zobrazit jako** se seznamem v aktivní mřížce rfps.  
  
### <a name="winforms-client-options"></a>Možnosti klienta WinForms  
  
- **Vytvořit RFP**: Vytvoří nový požadavek na návrhy (RFP) a spustí pracovní postup procesu nákupu.  
  
- **Aktualizace**: Aktualizuje seznam aktivních a dokončených programů RFP v hlavním okně.  
  
- **Zobrazit RFP**: Zobrazuje obsah existujícího rfp. Dodavatelé mohou předložit své návrhy (pokud jsou pozváni nebo RFP není dokončen)  
  
- **Připojit jako**: Uživatel může přistupovat k RFP pomocí různých identit výběrem požadovaného účastníka v poli **Zobrazit jako** se seznamem v aktivní mřížce rfps.
