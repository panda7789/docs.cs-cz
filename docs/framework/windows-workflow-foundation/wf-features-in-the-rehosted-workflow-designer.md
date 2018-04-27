---
title: Podpora nových funkcí Workflow Foundation 4.5 v Návrháři pracovních postupů opětovné hostování nástroje
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1a4a4038-d8e6-41dd-99ea-93bd76286772
caps.latest.revision: 3
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 999c18f20264a71cf73bbd5afd352ad3104a03e8
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="support-for-new-workflow-foundation-45-features-in-the-rehosted-workflow-designer"></a>Podpora nových funkcí Workflow Foundation 4.5 v Návrháři pracovních postupů opětovné hostování nástroje
[!INCLUDE[wf](../../../includes/wf-md.md)] v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zavedená mnoha nových funkcí, včetně několik vylepšení zkušeností Návrháře pracovního postupu. V tomto tématu jsou tyto funkce jsou podporované v Návrháři opětovné hostování nástroje, a ty, které nejsou aktuálně podporovány.  
  
> [!NOTE]
>  Seznam všech nové [!INCLUDE[wf](../../../includes/wf-md.md)] funkce zavedená v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], včetně těch, které se nevztahují ke návrháře opětovného hostování, najdete v tématu [co je nového v modelu Windows Workflow Foundation v rozhraní .NET 4.5](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).  
  
## <a name="activities"></a>Aktivity  
 Knihovna předdefinovaných aktivit obsahuje nové aktivity a nové funkce pro stávající aktivity. Všechny tyto nové aktivity jsou podporovány v Návrháři opětovné hostování nástroje. Další informace o těchto nových aktivit najdete v tématu [aktivity](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_NewActivities) části [co je nového v modelu Windows Workflow Foundation v rozhraní .NET 4.5](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md).  
  
## <a name="c-expressions"></a>Výrazy jazyka C#  
 Před verzí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], všechny výrazy v pracovních postupech může lze zapsat pouze v jazyce Visual Basic. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], výrazy jazyka Visual Basic se používají jenom pro projekty vytvořené pomocí jazyka Visual Basic. Projekty Visual C# teď použít C# pro výrazy. Při vytváření pracovních postupů v [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)], jaké funkce jako je například gramatika zvýrazňování a intellisense je k dispozici plně funkční editor výrazu jazyka C#. Pracovní postup projektů C# vytvořených v předchozích verzích, které používají výrazy jazyka Visual Basic budou nadále fungovat.  
  
> [!WARNING]
>  C# výrazy nejsou podporovány v Návrháři opětovné hostování nástroje.  
  
## <a name="new-designer-capabilities"></a>Nové funkce návrháře  
  
### <a name="designer-search"></a>Návrhář vyhledávání  
 [Rychlého hledání](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) a [hledání v souborech](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) funkce zavedené [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] opětovné hostování nástroje designer nepodporuje. `Toolbox` Vyhledávání je podporováno v Návrháři opětovné hostování nástroje. Další informace o těchto funkcích najdete v tématu [Návrhář vyhledávání](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_DesignerSearch).  
  
> [!WARNING]
>  [Rychle najít](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_QuickFind) a [hledání v souborech](../../../docs/framework/windows-workflow-foundation/whats-new-in-wf-in-dotnet.md#BKMK_FindInFiles) opětovné hostování nástroje designer nepodporuje.  
  
### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a>Odstranit položky kontextové nabídky v Návrháři proměnné a argument  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], proměnné a argumenty může odstranit pouze v Návrháři pomocí klávesnice. Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], proměnné a argumenty lze odstranit pomocí místní nabídky. Tato funkce je podporovaná v Návrháři opětovné hostování nástroje.  
  
 Následující snímek obrazovky ukazuje návrháře místní nabídky proměnné a argument.  
  
 ![Proměnné a Argument návrháře kontextovou nabídku](../../../docs/framework/windows-workflow-foundation/media/designercontextmenu.png "DesignerContextMenu")  
  
### <a name="auto-surround-with-sequence"></a>Auto-příkazu Obklopit s pořadím  
 Od pracovní postup nebo některé aktivity kontejneru (například <xref:System.Activities.Statements.NoPersistScope>) může obsahovat pouze jeden text aktivity, přidání druhá aktivita vyžaduje vývojáři odstranit první aktivitu, přidejte <xref:System.Activities.Statements.Sequence> aktivity a poté přidejte i aktivity a pořadí aktivit. Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], při přidávání druhá aktivita na plochu návrháře `Sequence` aktivity se automaticky vytvoří při zabalení obou aktivity. Tato funkce je podporovaná v Návrháři opětovné hostování nástroje.  
  
 Následující snímek obrazovky ukazuje `WriteLine` aktivity v `Body` z `NoPersistScope`.  
  
 ![Automatické&#45;obklopit rozevírací umístění](../../../docs/framework/windows-workflow-foundation/media/autosurround1.png "AutoSurround1")  
  
 Následující snímek obrazovky ukazuje automaticky vytvořený `Sequence` aktivity v `Body` při druhý `WriteLine` se snížilo pod úroveň první.  
  
 ![Automaticky vytvoří aktivity pořadí](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
### <a name="pan-mode"></a>Pan režimu  
 Usnadnit navigaci velké workflow v návrháři, můžete je povolen režim pan, umožňuje vývojáři klikněte a přetáhněte přesunout viditelnou část pracovního postupu, místo nutnosti použít posuvníky. Tlačítko pro aktivaci režimu posouvání je v pravém dolním rohu návrháře. Tato funkce je podporovaná v Návrháři opětovné hostování nástroje.  
  
 Následující snímek obrazovky ukazuje tlačítko posun, která se nachází v pravém dolním rohu návrháře pracovních postupů.  
  
 ![Tlačítko Posun v Návrháři pracovních postupů](../../../docs/framework/windows-workflow-foundation/media/panbutton.png "PanButton")  
  
 Střední tlačítko myši nebo MEZERNÍK lze také posunete zobrazení návrháře pracovních postupů.  
  
### <a name="multi-select"></a>Vícenásobný výběr v  
 Více aktivit lze vybrat najednou, tak, že přetáhnete obdélníkem (když není povolen režim panoramování) nebo podržte klávesu Ctrl a klikněte na požadované aktivity po jednom. Tato funkce je podporovaná v Návrháři opětovné hostování nástroje.  
  
 Více výběrů aktivitu můžete také přetahování v návrháři a můžete také zpracoval pomocí místní nabídky.  
  
### <a name="outline-view-of-workflow-items"></a>Zobrazení osnovy položek pracovního postupu  
 Abyste snadněji přejděte hierarchické pracovní postupy, jsou součástí pracovního postupu uvedené v stromové zobrazení osnovy. Zobrazí se v zobrazení osnovy **Osnova dokumentu** zobrazení. Chcete-li toto zobrazení otevřít v sadě Visual Studio, z hlavní nabídky, vyberte **zobrazení**, **ostatní okna**, **Osnova dokumentu**, nebo stiskněte klávesu Ctrl W, U. Kliknutím na uzel v zobrazení osnovy bude přejděte na odpovídající aktivity v Návrháři pracovních postupů a zobrazení osnovy budou aktualizovány na Zobrazit aktivity, které jsou vybrány v návrháři. Tato funkce je podporovaná v Návrháři opětovné hostování nástroje.  
  
 Následující snímek obrazovky dokončené pracovního postupu z [kurzu Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) zobrazení osnovy s sekvenční pracovní postup.  
  
 ![Zobrazení v Návrháři pracovních postupů osnovy](../../../docs/framework/windows-workflow-foundation/media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")  
  
### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a>Další kontrolu nad viditelnost panelu prostředí a záhlaví položky  
 Opětovné hostování nástroje Designer některé standardní ovládací prvky uživatelského rozhraní nemusí mít význam pro daný pracovní postup a může být vypnutý. V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], tato přizpůsobení je podporovaná jenom rozhraním prostředí panelu v dolní části návrháře. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], viditelnost prostředí položky hlavičky v horní části návrháře lze upravit nastavením <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> s příslušnou <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> hodnotu.  
  
### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a>Automaticky připojit a automatické vkládání v pracovních postupech vývojový diagram a stav počítače  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], připojení mezi uzly v pracovním postupu vývojový diagram museli přidat ručně. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], uzly vývojový diagram a stav počítače mají automaticky připojit body, které budou zobrazeny při přetažení aktivitu z panelu nástrojů na plochu návrháře. Vyřazení aktivitu na jeden z těchto bodů automaticky přidá aktivitu do aktivity společně s nezbytné připojení.  
  
 Následující snímek obrazovky znázorňuje body přílohy, které pak bude viditelný, když je aktivita přetažení z panelu nástrojů.  
  
 ![Počáteční uzel vývojový diagram znázorňující automatické připojení body](../../../docs/framework/windows-workflow-foundation/media/autoconnect1.png "Autoconnect1")  
  
 Aktivity lze také být přetáhli připojení mezi uzly vývojový diagram a stavy k automatické vložení uzlu mezi dvěma ostatní uzly. Následující snímek obrazovky ukazuje zvýrazněný řádek připojování, kde můžete aktivity přetažení z panelu nástrojů a vyřadit.  
  
 ![Automatické&#45;vložit popisovač pro vyřazení aktivity](../../../docs/framework/windows-workflow-foundation/media/autoinsert.png "Autoinsert")  
  
 Automaticky připojit a automatické vkládání jsou podporovány v Návrháři opětovné hostování nástroje.  
  
### <a name="designer-annotations"></a>Návrhář poznámky  
 Usnadňuje vývoj větší pracovních návrháře teď podporuje přidání poznámky do sleduje proces návrhu aplikace. Poznámky lze přidat do aktivity, stavy, vývojový diagram uzlů, proměnné a argumenty. Následující snímek obrazovky ukazuje v místní nabídce použít k přidání poznámky do návrháře.  
  
 ![Poznámky kontextovou nabídku](../../../docs/framework/windows-workflow-foundation/media/annotationdialog.png "annotationdialog")  
  
 Návrhář poznámky jsou podporovány v Návrháři opětovné hostování nástroje.  
  
### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a>Definice a používání ActivityDelegate objektů v Návrháři  
 Aktivity v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] používá <xref:System.Activities.ActivityDelegate> objekty, které chcete zobrazit provádění body, kde dalších částí pracovního postupu může komunikovat s spuštění pracovního postupu, ale pomocí těchto bodů provádění obvykle vyžaduje správného množství kódu. V této verzi můžete vývojáři definice a používání delegátů aktivity pomocí návrháře pracovních postupů. Další informace najdete v tématu [postupy: definice a používání delegátů aktivity v Návrháři pracovních postupů](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).  
  
 Delegáti aktivity jsou podporovány v Návrháři opětovné hostování nástroje.  
  
### <a name="build-time-validation"></a>Ověření sestavení za běhu  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], pracovní postup ověření chyby nebyly počítají jako chyby sestavení během vytváření sestavení projektu pracovního postupu. Vynutila si vytvoření pracovního postupu projektu může být úspěšné i v případě, že se vyskytly chyby ověření pracovního postupu. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], způsobit chyby ověření pracovního postupu sestavení selhání.  
  
> [!WARNING]
>  Ověření čase vytvoření buildu není podporováno v Návrháři opětovné hostování nástroje.  
  
### <a name="design-time-background-validation"></a>Ověření pozadí v době návrhu  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], pracovní postupy, které byly ověřeny jako proces na popředí, což může potenciálně zablokování uživatelského rozhraní během procesů ověřování složitý nebo časově náročná. Pracovní postup ověření nyní probíhá na vlákna na pozadí tak, aby nebyl blokován uživatelského rozhraní.  
  
 Ověření návrhu pozadí je podporováno v Návrháři opětovné hostování nástroje.  
  
### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a>Stav zobrazení, které jsou umístěné v samostatné umístění v souborech XAML  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], informace o zobrazení stavu pro pracovní postup je ukládat v rámci souboru XAML v různých umístěních. Toto je nepohodlná pro vývojáře, kteří chtějí čtení XAML přímo, nebo napsat kód pro odebrat informace o stavu zobrazení. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zobrazení informací o stavu v souboru XAML serializován jako samostatný prvek v souboru XAML.  Vývojáře můžou snadno najít a upravit informace o zobrazení stavu aktivity nebo úplně odebrat stav zobrazení.  
  
 Tato funkce je podporovaná v Návrháři pracovních postupů opětovné hostování nástroje.  
  
### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a>Výslovný souhlas pro funkce Workflow 4.5 v Návrháři opětovné hostování nástroje  
 Zachování zpětné kompatibility, některé nové funkce zahrnuté v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nejsou povolené ve výchozím nastavení v Návrháři opětovné hostování nástroje. To je potřeba zajistit, aby existující aplikace, které používají návrháři opětovné hostování nástroje nejsou přerušený při aktualizaci na nejnovější verzi. Pokud chcete povolit nové funkce v Návrháři opětovné hostování nástroje, nastavte <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> k "rozhraní .net Framework 4.5", nebo nastavte jednotlivé členy <xref:System.Activities.Presentation.DesignerConfigurationService> k povolení jednotlivých funkcí.  
  
## <a name="new-workflow-development-models"></a>Nový pracovní postup vývoj modely  
 Kromě vývojový diagram a modely vývoj sekvenční pracovní postup tato verze zahrnuje stav stavového stroje pracovní postupy a pracovního postupu první kontrakt služby.  
  
### <a name="state-machine-workflows"></a>Pracovní postupy stavu počítače  
 Pracovní postupy stavu počítače byly zavedeny v rámci rozhraní .NET Framework 4.0.1 v [rozhraní Microsoft .NET Framework 4 Platform Update 1](http://go.microsoft.com/fwlink/?LinkID=215092). Tato aktualizace zahrnuta několik nové třídy a aktivity, které povolené vývojářům vytvářet pracovní postupy stav počítače. Tyto třídy a aktivity byly aktualizovány pro [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Aktualizace zahrnují:  
  
1.  Možnost nastavit zarážky na stavy  
  
2.  Možnost Kopírovat a vkládat přechody v Návrháři pracovních postupů  
  
3.  Podpora návrháře pro vytvoření přechodu sdílené aktivační události  
  
4.  Aktivity použít k vytvoření pracovních stavu počítače, včetně: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, a <xref:System.Activities.Statements.Transition>  
  
 Následující snímek obrazovky ukazuje stavu dokončení pracovního postupu počítače z [kurzu Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) krok [postupy: vytvoření pracovního postupu stavu počítače](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md).  
  
 ![Dokončit pracovní postup stavového stroje](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Další informace o vytváření pracovních postupů stavu počítače najdete v tématu [stavu počítače pracovních](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md). Pracovní postupy stavu počítače jsou podporovány v Návrháři opětovné hostování nástroje.  
  
### <a name="contract-first-workflow-development"></a>Vývoj pro první kontrakt pracovního postupu  
 Nástroj pro vývoj kontrakt první pracovní postup umožňuje vývojáři navrhnout první kontraktu v kódu a potom pomocí několika kliknutí v sadě Visual Studio automaticky generovat šablonu aktivit v sadě nástrojů představující jednotlivých operací. Tyto aktivity jsou poté použít k vytvoření pracovního postupu, který implementuje operace definované kontrakt. Návrhář postupu provádění vyhodnotí služby pracovního postupu zajistit, že tyto operace jsou implementované a podpis pracovního postupu odpovídá podpisu smlouvy. Vývojář můžete taky přidružit kolekce implementovaná kontraktů služby pracovních postupů. Další informace o vývoj pracovního postupu první kontraktu služby najdete v tématu [postupy: vytvoření služby pracovního postupu, který využívá existující smlouvy služby](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).  
  
> [!WARNING]
>  Vývoj kontrakt první pracovního postupu není podporováno v Návrháři pracovních postupů.
