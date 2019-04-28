---
title: Podpora nových funkcí Workflow Foundation 4.5 v Návrháři postupu provádění se změněným hostováním
ms.date: 03/30/2017
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
ms.openlocfilehash: a7b7ed6987320314ee3fdccf0e58a8c7314fe50d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669753"
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>Podpora nových funkcí Workflow Foundation 4.5 v Návrháři postupu provádění se změněným hostováním
Windows Workflow Foundation (WF) v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] přichází s mnoha novými funkcemi včetně několik vylepšení prostředí Návrháře pracovního postupu. Toto téma podrobně popisuje tyto funkce jsou podporované v návrháři se změněným hostováním, a ty, které nejsou aktuálně podporovány.

> [!NOTE]
>  Pro všechny nové funkce Windows Workflow Foundation (WF) v seznamu [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], včetně těch, které nesouvisí s změna hostování návrháře, najdete v tématu [co je nového ve Windows Workflow Foundation v rozhraní .NET 4.5](whats-new-in-wf-in-dotnet.md).

## <a name="activities"></a>Aktivity
 Knihovna předdefinovaných aktivit obsahuje nové aktivity a nové funkce pro existujících aktivit. Všechny tyto nové aktivity jsou podporované v návrháři se změněným hostováním. Další informace o těchto nových aktivit najdete v článku [aktivity](whats-new-in-wf-in-dotnet.md#BKMK_NewActivities) část [co je nového ve Windows Workflow Foundation v rozhraní .NET 4.5](whats-new-in-wf-in-dotnet.md).

## <a name="c-expressions"></a>Výrazy C#
 Před verzí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], všechny výrazy v pracovních postupech, může být pouze napsaná v jazyce Visual Basic. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], výrazy jazyka Visual Basic se používají pouze pro projekty vytvořené pomocí jazyka Visual Basic. Projekty Visual C# nyní pomocí C# pro výrazy. Při vytváření pracovních postupů v sadě Visual Studio 2012, plně funkční editor výrazů C# poskytuje jaké schopnosti zvýraznění gramatiky a technologie intellisense. Pracovní postup projekty jazyka C# vytvořené v předchozích verzích, které používají výrazy jazyka Visual Basic, budou nadále fungovat.

> [!WARNING]
>  V návrháři se změněným hostováním nepodporují výrazy jazyka C#.

## <a name="new-designer-capabilities"></a>Nové možnosti návrháře

### <a name="designer-search"></a>Návrháře vyhledávání
 [Rychlé hledání](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) a [najít v souborech](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) nepředchází funkce [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nejsou podporovány v návrháři se změněným hostováním. `Toolbox` Hledání je podporované v návrháři se změněným hostováním. Další informace o těchto funkcích najdete v tématu [návrháře hledání](whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch).

> [!WARNING]
>  [Rychlé hledání](whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) a [najít v souborech](whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) nejsou podporovány v návrháři se změněným hostováním.

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>Odstranit položky kontextové nabídky v Návrháři proměnných a argumentů
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], proměnné a argumenty může odstranit jenom v Návrháři pomocí klávesnice. Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], proměnné a argumenty je možné odstranit pomocí místní nabídky. Tato funkce je podporovaná v návrháři se změněným hostováním.

 Následující snímek obrazovky ukazuje návrháře kontextové nabídky proměnných a argumentů.

 ![Proměnné a Argument místní nabídka návrháře](./media/designercontextmenu.png "DesignerContextMenu")

### <a name="auto-surround-with-sequence"></a>Automatické kulatých pořadí
 Od pracovního postupu nebo určité aktivity kontejneru (například <xref:System.Activities.Statements.NoPersistScope>) může obsahovat jenom jeden text aktivity, přidání druhé aktivity vyžaduje vývojářům první aktivita odstranění, přidání <xref:System.Activities.Statements.Sequence> aktivity a pak přidat obě aktivity k sekvenční aktivity. Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], při přidání druhé aktivity na plochu návrháře `Sequence` aktivity se automaticky vytvoří při zabalení obě aktivity. Tato funkce je podporovaná v návrháři se změněným hostováním.

 Následující snímek obrazovky ukazuje `WriteLine` aktivity v `Body` z `NoPersistScope`.

 ![Automatické&#45;před a za místo přetažení](./media/autosurround1.png "AutoSurround1")

 Následující snímek obrazovky ukazuje automaticky vytvořený `Sequence` aktivity v `Body` při sekundy `WriteLine` neklesla pod první.

 ![Automaticky vytvořit sekvenční aktivitu](./media/autosurround2.png "AutoSurround2")

### <a name="pan-mode"></a>Režim posouvání
 Velké pracovní postup v Návrháři snadněji přejít, je možné povolit režim posouvání umožňuje vývojářům klikněte a tažením přesuňte viditelnou část pracovního postupu, místo nutnosti použít posuvníky. Tlačítko aktivovat režim posouvání se v pravém dolním rohu návrháře. Tato funkce je podporovaná v návrháři se změněným hostováním.

 Následující snímek obrazovky ukazuje tlačítko posouvání, která se nachází v pravém dolním rohu návrháře postupu provádění.

 ![Tlačítko posouvání v Návrháři pracovních postupů](./media/panbutton.png "PanButton")

 Prostřední tlačítko myši nebo MEZERNÍK lze použít také k posouvání návrháře postupu provádění.

### <a name="multi-select"></a>Vícenásobný výběr
 Více aktivit můžete vybrat najednou, buď přetažením obdélníkem (když není povolen režim posouvání), nebo tím, že podržíte stisknutou klávesu Ctrl a klikněte na požadovaný aktivity jeden po druhém. Tato funkce je podporovaná v návrháři se změněným hostováním.

 Více výběrů aktivita může také být přetáhnout v návrháři a můžete také interakci s použitím místní nabídky.

### <a name="outline-view-of-workflow-items"></a>Zobrazení osnovy položky pracovního postupu
 Pokud chcete mít hierarchické pracovních postupů přehlednější a díky tomu, komponenty pracovního postupu se zobrazí v zobrazení stromové osnovy. Zobrazí se v zobrazení osnovy **Osnova dokumentu** zobrazení. Chcete-li toto zobrazení otevřít v sadě Visual Studio z hlavní nabídky, vyberte **zobrazení**, **ostatní Windows**, **Osnova dokumentu**, nebo stiskněte klávesy Ctrl W, U. Kliknutím na uzel v zobrazení osnovy přejdete na odpovídající aktivity v Návrháři pracovních postupů a zobrazení osnovy se aktualizuje a zobrazí aktivity, které jsou vybrány v návrháři. Tato funkce je podporovaná v návrháři se změněným hostováním.

 Na následujícím snímku obrazovky dokončené pracovní postup [kurz Začínáme](getting-started-tutorial.md) zobrazuje zobrazení osnovy s sekvenčního pracovního postupu.

 ![Zobrazení v Návrháři pracovních postupů osnovy](./media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>Větší míra kontroly viditelnost panelu prostředí a v záhlaví položek
 V návrháři se změněným hostováním některé standardní ovládací prvky uživatelského rozhraní nemůže mít význam pro daný pracovní postup a může být vypnuté. V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], tato přizpůsobení je podporována pouze na prostředí panelu v dolní části okna návrháře. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], viditelnost prostředí položek záhlaví v horní části okna návrháře je možné upravit tak, že nastavíte <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> příslušnou <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> hodnotu.

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>Automatické připojení a automatické vložení v pracovních postupech vývojový diagram a stavového stroje.
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], připojení mezi uzly v pracovním postupu vývojového diagramu musí přidat ručně. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], vývojový diagram a stavového stroje uzly mají automaticky připojit body, které pak bude viditelný, když je aktivita přetáhnout z panelu nástrojů na plochu návrháře. Přetažení aktivity v jednom z těchto bodů automaticky přidá aktivitu do aktivity spolu s nezbytné připojení.

 Následující snímek obrazovky ukazuje body přílohy, které pak bude viditelný, když je aktivita přetáhnout z panelu nástrojů.

 ![Počáteční uzel vývojový diagram zobrazuje body automatické připojení](./media/autoconnect1.png "Autoconnect1")

 Aktivity můžete také přetahovat do připojení mezi uzly vývojový diagram a stavy pro automatické vložení uzlu mezi dvou jiných uzlech. Následující snímek obrazovky ukazuje zvýrazněný řádek připojení, kde můžete přetáhnout z panelu nástrojů a vyřadit aktivity.

 ![Automatické&#45;vložit úchyt pro přetažení aktivity](./media/autoinsert.png "Autoinsert")

 Automaticky připojit a automaticky vkládat jsou podporovány v návrháři se změněným hostováním.

### <a name="designer-annotations"></a>Návrháře poznámky
 Usnadňuje vývoj větší pracovních postupů návrháře nyní podporuje přidávání poznámek k pomáhají udržovat přehled o procesu návrhu. Komentáře lze přidat do aktivity, státy, vývojový diagram uzly, proměnné a argumenty. Na následujícím snímku obrazovky se zobrazí místní nabídku pro přidání poznámky do návrháře.

 ![Poznámka kontextovou nabídku](./media/annotationdialog.png "annotationdialog")

 Návrháře poznámky jsou podporovány v návrháři se změněným hostováním.

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>Definice a používání objektu ActivityDelegate objektů v Návrháři
 Aktivity v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] použít <xref:System.Activities.ActivityDelegate> objekty k vystavení body provádění kde ostatní části pracovního postupu může pracovat s pracovní postup spouštění, ale obvykle pomocí těchto bodů provádění požadované množství kódu. V této verzi můžou vývojáři definice a používání delegátů aktivit pomocí návrháře postupu provádění. Další informace najdete v tématu [jak: Definice a používání delegátů aktivit v Návrháři postupu provádění](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).

 Delegátů aktivit jsou podporovány v návrháři se změněným hostováním.

### <a name="build-time-validation"></a>Ověření při sestavení
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], chyby ověření pracovního postupu se přitom počítá jako chyby sestavení během sestavování projektu pracovního postupu. To znamená, že tento pracovní postup sestavení projektu může úspěšné i v případě, že došlo k chybě ověření pracovního postupu. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], aby sestavení selhalo, způsobit chyby ověření pracovního postupu.

> [!WARNING]
>  Ověření při sestavení není v návrháři se změněným hostováním podporována.  
  
### <a name="design-time-background-validation"></a>Ověřování na pozadí v době návrhu  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], pracovní postupy, které byly ověřeny jako proces na popředí, která by mohla potenciálně přestane reagovat uživatelské rozhraní během procesů ověřování složité a časově náročné. Ověření pracovního postupu nyní probíhá na vlákně na pozadí, tak, aby uživatelského rozhraní není blokován.  
  
 Pozadí návrhové ověření je podporováno v návrháři se změněným hostováním.  
  
### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>Stav zobrazení, které jsou umístěné v samostatném umístění v souborech XAML  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], informace o zobrazení stavu pracovního postupu je uložen v souboru XAML v mnoha různých umístěních. Toto je vhodná pro vývojáře, kteří chtějí XAML přímo číst nebo napsat kód, který odebrat informace o stavu zobrazení. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zobrazit informace o stavu v souboru XAML je serializován jako samostatný prvek v souboru XAML.  Vývojáře můžou snadno najít a upravit informace o zobrazení stavu aktivity nebo zcela odebrat stav zobrazení.  
  
 Tato funkce je podporovaná v Návrháři postupu provádění se změněným hostováním.  
  
### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>Vyjádřit výslovný souhlas pro funkce pracovního postupu 4.5 v návrháři se změněným hostováním  
 Pro zachování zpětné kompatibility, některé nové funkce zahrnuté v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nejsou povolené ve výchozím nastavení v návrháři se změněným hostováním. Tím je zajištěno, že existující aplikace, které používají návrháři se změněným hostováním negativně neovlivní aktualizace na nejnovější verzi. Chcete-li povolit nové funkce v návrháři se změněným hostováním, buď nastavte <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> na ".Net Framework 4.5", nebo nastavit jednotlivé členy <xref:System.Activities.Presentation.DesignerConfigurationService> povolení jednotlivých funkcí.  
  
## <a name="new-workflow-development-models"></a>Pracovní postup vývoje modelů  
 Kromě vývojový diagram a sekvenční pracovní postup vývoje modelů tato verze zahrnuje pracovní postupy stavu počítače a služby stavící do pracovního postupu.  
  
### <a name="state-machine-workflows"></a>Pracovní postupy stavového stroje  
 Pracovní postupy stavového stroje byly představeny jako součást rozhraní .NET Framework 4.0.1 v [rozhraní Microsoft .NET Framework 4 aktualizace platformy 1](https://go.microsoft.com/fwlink/?LinkID=215092). Tato aktualizace je zahrnuta několik nových třídách a činnostech, které mohou vývojáři vytvářet pracovní postupy stavu počítače povolené. Tyto třídy a činnosti byly aktualizovány [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Aktualizace zahrnují:  
  
1. Možnost nastavit zarážky na stavy  
  
2. Možnost kopírování a vkládání přechodů v Návrháři postupu provádění  
  
3. Podpora návrhářů pro sdílené vytváření aktivačních přechodů  
  
4. Aktivity použít k vytváření pracovních postupů stavového stroje, včetně: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, a <xref:System.Activities.Statements.Transition>  
  
 Následující snímek obrazovky ukazuje pracovní postup dokončený stav stroje ze [kurz Začínáme](getting-started-tutorial.md) krok [jak: Vytvoření pracovního postupu stavového stroje](how-to-create-a-state-machine-workflow.md).  
  
 ![Dokončení pracovního postupu stavového stroje](./media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Další informace o vytváření pracovní postupy stavu počítače, naleznete v tématu [pracovní postupy stavu počítače](state-machine-workflows.md). V návrháři se změněným hostováním jsou podporovány pracovních postupů stavového stroje.  
  
### <a name="contract-first-workflow-development"></a>Vývoj stavící do pracovního postupu  
 Pracovní postup kontraktem vývojový nástroj umožňuje vývojářům navrhovat smlouvy v kódu a potom pomocí několika kliknutí v sadě Visual Studio automaticky vygenerovat šablonu aktivit v sadě nástrojů představující každé operace. Tyto aktivity se pak používají k vytvoření pracovního postupu, který implementuje operace definované ve smlouvě. Návrháře postupu provádění se ověří pracovní postup služby zajistíte, že tyto operace jsou implementovány a podpis pracovního postupu odpovídá podpisu smlouvu. Vývojář můžete taky přidružit kolekce implementované kontrakty služby pracovního postupu. Další informace o vývoj služby stavící do pracovního postupu najdete v tématu [jak: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
> [!WARNING]
>  Vývoj stavící do pracovního postupu není podporován v Návrháři pracovních postupů.
