---
title: Co&#39;s nové v modelu Windows Workflow Foundation v rozhraní .NET 4.5
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
caps.latest.revision: 32
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: b57cf990f9fdf987f4cc414cb42db6cf9fe0da21
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="what39s-new-in-windows-workflow-foundation-in-net-45"></a>Co&#39;s nové v modelu Windows Workflow Foundation v rozhraní .NET 4.5
[!INCLUDE[wf](../../../includes/wf-md.md)] v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zavádí mnoha nových funkcí, jako je například nové aktivity, návrháře možnosti a modely vývoj pracovního postupu. Mnoho, ale ne všechny nové funkce pracovního postupu byla zavedená v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] jsou podporovány v Návrháři znovu hostovaných pracovních postupů. [!INCLUDE[crabout](../../../includes/crabout-md.md)] nové funkce, které jsou podporované, najdete v části [podporu pro nové funkce Workflow Foundation 4.5 v Návrháři pracovních postupů opětovné hostování nástroje](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md). [!INCLUDE[crabout](../../../includes/crabout-md.md)] migrace na rozhraní .NET 3.0 a rozhraní .NET 3.5 pracovního postupu aplikacím používat nejnovější verzi, najdete v části [migrace pokyny](../../../docs/framework/windows-workflow-foundation/migration-guidance.md). Toto téma poskytuje přehled nových funkcí pracovního postupu byla zavedená v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
> [!WARNING]
>  Nové [!INCLUDE[wf2](../../../includes/wf2-md.md)] funkce zavedená v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nejsou k dispozici pro projekty, které cílí na předchozích verzích rozhraní. Pokud projektu, jehož cílem [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] znovu cílí na předchozí verzi rozhraní framework situace může nastat několik problémů.  
>   
>  -   Výrazy jazyka C# se nahradí v návrháři se zprávou **v jazyce XAML byla nastavena hodnota**.  
> -   Dojde k chybám mnoho sestavení, včetně k následující chybě.  
>   
>  **Formát souboru není kompatibilní s aktuální cílení framework. Chcete-li převést do formátu souboru, prosím explicitně uložte soubor. Tato chybová zpráva zmizí po uložení souboru a znovu otevřete návrháře.**  
  
##  <a name="BKMK_Versioning"></a> Pracovní postup správy verzí  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zavedly několik nových funkcí správy verzí na základě kolem nové <xref:System.Activities.WorkflowIdentity> třídy. <xref:System.Activities.WorkflowIdentity> poskytuje mechanismus pro mapování trvalého pracovního postupu instance s jeho definice aplikace autoři pracovního postupu.  
  
-   Vývojáře, kteří používají <xref:System.Activities.WorkflowApplication> hostingu můžete použít <xref:System.Activities.WorkflowIdentity> povolit, hostování více verzí pracovní postup-souběžného. Instance pracovního postupu trvalou můžete načíst pomocí nové <xref:System.Activities.WorkflowApplicationInstance> třída a potom <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> lze použít pro hostitele zajistit správnou verzi definice pracovního postupu při vytvoření instance <xref:System.Activities.WorkflowApplication>. Další informace najdete v tématu [pomocí WorkflowIdentity a správa verzí](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md) a [postup: hostitele více verzí pracovní postup-souběžného](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
-   <xref:System.ServiceModel.WorkflowServiceHost> je nyní hostitelem více verzí. Při nasazení nové verze služby pracovního postupu nové instance služby se vytvoří pomocí nové služby, ale existující instance dokončit pomocí předchozí verze. Další informace najdete v tématu [správu verzí vedle sebe v hostitele služby pracovního postupu](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).  
  
-   Dynamická aktualizace uvádíme, který poskytuje mechanismus pro aktualizaci definice instance trvalou pracovního postupu. Další informace najdete v tématu [dynamická aktualizace](../../../docs/framework/windows-workflow-foundation/dynamic-update.md) a [postupy: aktualizovat definice instanci pracovního postupu spuštění](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).  
  
-   SqlWorkflowInstanceStoreSchemaUpgrade.sql databázového skriptu je zadán pro upgrade trvalost databází vytvořených přes [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] databáze skripty. Tento skript aktualizace [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] trvalost databáze podporují nové možnosti správy verzí, počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Instance pracovního postupu trvalý v databázi mají výchozí hodnoty verze a mohl účastnit spuštění vedle sebe a dynamické aktualizace. [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [Upgrade rozhraní .NET Framework 4 trvalost databáze podporující pracovní postup správy verzí](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).  
  
##  <a name="BKMK_NewActivities"></a> aktivity  
 Knihovna předdefinovaných aktivit obsahuje nové aktivity a nové funkce pro stávající aktivity.  
  
###  <a name="BKMK_NoPersistScope"></a> A obor  
 <xref:System.Activities.Statements.NoPersistScope> je nová aktivita kontejneru, který brání jako trvalý, když jsou prováděny NoPersistScope podřízené aktivity pracovního postupu. To je užitečné v situacích, kde není vhodné pro pracovní postup natrvalo, například když je pracovní postup pomocí specifické pro počítač prostředky, jako jsou popisovače souborů, nebo při databázové transakce. Dříve aby se zabránilo trvalost z ke kterým došlo během provádění aktivity, vlastní <xref:System.Activities.NativeActivity> kterého <xref:System.Activities.NoPersistHandle> nebyla nutná.  
  
###  <a name="BKMK_NewFlowchartCapabilities"></a> Nové funkce vývojový diagram  
 Na vývojových diagramech jsou aktualizované o [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a mají následující nové funkce:  
  
-   `DisplayName` Vlastnost <xref:System.Activities.Statements.FlowSwitch%601> nebo <xref:System.Activities.Statements.FlowDecision> aktivity se upravovat. To vám umožní Návrhář aktivity zobrazit další informace o účelu aktivity.  
  
-   Na vývojových diagramech mít novou vlastnost s názvem <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A>; výchozí hodnota pro tuto vlastnost je `False`. Pokud je tato vlastnost nastavena na `True`, pak bez připojení vývojový diagram uzly způsobí chyby ověření.  
  
## <a name="support-for-partial-trust"></a>Podpora pro částečné důvěryhodnosti  
 Pracovní postupy v [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] požadované domény plně důvěryhodný pro aplikace. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], pracovní postupy můžou fungovat v prostředí s částečnou důvěryhodností. V prostředí s částečnou důvěryhodností lze použít komponenty třetích stran bez toho, abyste je plný přístup k prostředkům hostitele. Některé aspekty spouštění pracovních postupů v částečné důvěryhodnosti jsou následující:  
  
1.  Pomocí starší verze součásti (včetně pravidel) součástí <xref:System.Activities.Statements.Interop> aktivita není podporován v rámci částečnou důvěryhodností.  
  
2.  Spouštění pracovních postupů v částečné důvěryhodnosti v <xref:System.ServiceModel.WorkflowServiceHost> není podporován.  
  
3.  Zachování výjimky v částečné důvěryhodnosti scénář je potenciální ohrožení zabezpečení. Zakázat uložením výjimek, rozšíření typu <xref:System.Activities.ExceptionPersistenceExtension> musí být přidaný do projektu, aby bylo možné vyjádření výslovného nesouhlasu zachování výjimky. Následující příklad kódu ukazuje, jak implementaci tohoto typu.  
  
    ```  
    public class ExceptionPersistenceExtension   
    {  
        public ExceptionPersistenceExtension()   
        {   
            this.PersistExceptions = false;   
        }   
        public bool PersistExceptions { get; set; }   
    }  
    ```  
  
     Pokud výjimky jsou tak, aby se Dal serializovat, ujistěte se, že se výjimky použijí v rámci <xref:System.Activities.Statements.NoPersistScope>.  
  
4.  Autoři aktivity by měly přepsat <xref:System.Activities.Activity.CacheMetadata%2A> -li se vyhnout modulu runtime pracovního postupu je automaticky spouštějí reflexe proti typu. Argumenty a podřízené aktivity musí mít hodnotu null, a <xref:System.Activities.ActivityMetadata.Bind%2A> musí být explicitně volána. Další informace o přepsání <xref:System.Activities.Activity.CacheMetadata%2A>, najdete v části [úniku dat s CacheMetadata](../../../docs/framework/windows-workflow-foundation/exposing-data-with-cachemetadata.md). Navíc instancí argumenty, které jsou typu, který je `internal` nebo **privátní** musí být explicitně vytvořené v <xref:System.Activities.Activity.CacheMetadata%2A> předejdete vytváří pomocí reflexe.  
  
5.  Typy nebude používat <xref:System.Runtime.Serialization.ISerializable> nebo <xref:System.SerializableAttribute> pro serializaci; musí podporovat typy, které jsou k serializaci <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
6.  Výrazy, které používají <xref:System.Activities.Expressions.LambdaValue%601> vyžadují <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A>a proto nebude fungovat v částečné důvěryhodnosti. Pracovní postupy, které používají <xref:System.Activities.Expressions.LambdaValue%601> měli nahradit aktivity, které jsou odvozeny od těchto výrazů <xref:System.Activities.CodeActivity%601>. .  
  
7.  Výrazy nelze kompilovat, pomocí <xref:System.Activities.XamlIntegration.TextExpressionCompiler> nebo Visual Basicu hostované kompilátoru v částečné důvěryhodnosti, ale lze spustit dříve kompilované výrazy.  
  
8.  Jediné sestavení, která používá [průhlednost úrovně 2](http://aka.ms/Level2Transparency) nelze použít v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v režimu plné důvěryhodnosti a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v částečné důvěryhodnosti.  
  
##  <a name="BKMK_NewDesignerCapabilites"></a> Nové funkce návrháře  
  
###  <a name="BKMK_DesignerSearch"></a> Návrhář vyhledávání  
 Chcete-li větší pracovních lepší správu bitlockeru, pracovní postupy mohou nyní vyhledat – klíčové slovo. Tato funkce je k dispozici v sadě Visual Studio; Tato funkce není k dispozici v opětovné hostování nástroje návrháře. Nejsou k dispozici dva druhy hledání:  
  
-   Rychle najít, iniciovala s buď **Ctrl + F** nebo **upravit**, **najít a nahradit**, **rychlého hledání**.  
  
-   Hledání v souborech, iniciovala s buď **Ctrl + Shift + F** nebo **upravit**, **najít a nahradit**, **hledání v souborech**.  
  
 Všimněte si, že nahradit není podporován.  
  
####  <a name="BKMK_QuickFind"></a> Rychle najít  
 Klíčová slova v pracovních postupech vyhledávat bude shodovat s návrháře následující položky:  
  
-   Vlastnosti <xref:System.Activities.Activity> objekty, <xref:System.Activities.Statements.FlowNode> objekty, <xref:System.Activities.Statements.State> objekty, <xref:System.Activities.Statements.Transition> objekty a dalším položkám vlastní řízení toku.  
  
-   Proměnné  
  
-   Arguments  
  
-   Výrazy  
  
 Rychle najít provádí na nástroje designer <xref:System.Activities.Presentation.Model.ModelItem> stromu. Rychle najít nebude najít obory názvů definice pracovního postupu byla naimportována.  
  
####  <a name="BKMK_FindInFiles"></a> Hledání v souborech  
 Klíčová slova v pracovních postupech vyhledávat bude odpovídat skutečný obsah soubory pracovního postupu. V podokně zobrazení výsledků najít Visual Studio zobrazí výsledky hledání. Dvakrát klikněte na položku výsledek bude přejděte do aktivity, který obsahuje shody v Návrháři pracovních postupů.  
  
###  <a name="BKMK_VariableDeleteContextMenu"></a> Odstranit položky kontextové nabídky v Návrháři proměnné a argument  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], proměnné a argumenty může odstranit pouze v Návrháři pomocí klávesnice. Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], proměnné a argumenty lze odstranit pomocí místní nabídky.  
  
 Následující snímek obrazovky ukazuje návrháře místní nabídky proměnné a argument.  
  
 ![Proměnné a Argument návrháře kontextovou nabídku](../../../docs/framework/windows-workflow-foundation/media/designercontextmenu.png "DesignerContextMenu")  
  
###  <a name="BKMK_AutoSurround"></a> Auto-příkazu Obklopit s pořadím  
 Od pracovní postup nebo některé aktivity kontejneru (například <xref:System.Activities.Statements.NoPersistScope>) může obsahovat pouze jeden text aktivity, přidání druhá aktivita vyžaduje vývojáři odstranit první aktivitu, přidejte <xref:System.Activities.Statements.Sequence> aktivity a poté přidejte i aktivity a pořadí aktivit. Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], při přidávání druhá aktivita na plochu návrháře `Sequence` aktivity se automaticky vytvoří při zabalení obou aktivity.  
  
 Následující snímek obrazovky ukazuje `WriteLine` aktivity v `Body` z `NoPersistScope`.  
  
 ![Automatické&#45;obklopit rozevírací umístění](../../../docs/framework/windows-workflow-foundation/media/autosurround1.png "AutoSurround1")  
  
 Následující snímek obrazovky ukazuje automaticky vytvořený `Sequence` aktivity v `Body` při druhý `WriteLine` se snížilo pod úroveň první.  
  
 ![Automaticky vytvoří aktivity pořadí](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
###  <a name="BKMK_PanMode"></a> Pan režimu  
 Usnadnit navigaci velké workflow v návrháři, můžete je povolen režim pan, umožňuje vývojáři klikněte a přetáhněte přesunout viditelnou část pracovního postupu, místo nutnosti použít posuvníky. Tlačítko pro aktivaci režimu posouvání je v pravém dolním rohu návrháře.  
  
 Následující snímek obrazovky ukazuje tlačítko posun, která se nachází v pravém dolním rohu návrháře pracovních postupů.  
  
 ![Tlačítko Posun v Návrháři pracovních postupů](../../../docs/framework/windows-workflow-foundation/media/panbutton.png "PanButton")  
  
 Střední tlačítko myši nebo MEZERNÍK lze také posunete zobrazení návrháře pracovních postupů.  
  
###  <a name="BKMK_MultiSelect"></a> Vícenásobný výběr v  
 Více aktivit lze vybrat najednou, tak, že přetáhnete obdélníkem (když není povolen režim panoramování) nebo podržte klávesu Ctrl a klikněte na požadované aktivity po jednom.  
  
 Více výběrů aktivitu můžete také přetahování v návrháři a můžete také zpracoval pomocí místní nabídky.  
  
###  <a name="BKMK_DocumentOutline"></a> Zobrazení osnovy položek pracovního postupu  
 Abyste snadněji přejděte hierarchické pracovní postupy, jsou součástí pracovního postupu uvedené v stromové zobrazení osnovy. Zobrazí se v zobrazení osnovy **Osnova dokumentu** zobrazení. Chcete-li toto zobrazení otevřít z hlavní nabídky, vyberte **zobrazení**, **ostatní okna**, **Osnova dokumentu**, nebo stiskněte klávesu Ctrl W, U. Kliknutím na uzel v zobrazení osnovy bude přejděte na odpovídající aktivity v Návrháři pracovních postupů a zobrazení osnovy budou aktualizovány na Zobrazit aktivity, které jsou vybrány v návrháři.  
  
 Následující snímek obrazovky dokončené pracovního postupu z [kurzu Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) zobrazení osnovy s sekvenční pracovní postup.  
  
 ![Zobrazení v Návrháři pracovních postupů osnovy](../../../docs/framework/windows-workflow-foundation/media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")  
  
###  <a name="BKMK_CSharpExpressions"></a> Výrazy jazyka C#  
 Před verzí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], všechny výrazy v pracovních postupech může lze zapsat pouze v jazyce Visual Basic. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], výrazy jazyka Visual Basic se používají jenom pro projekty vytvořené pomocí jazyka Visual Basic. Projekty Visual C# teď použít C# pro výrazy. Jaké funkce jako je například gramatika zvýrazňování a intellisense je k dispozici plně funkční editor výrazu jazyka C#. Pracovní postup projektů C# vytvořených v předchozích verzích, které používají výrazy jazyka Visual Basic budou nadále fungovat.  
  
 Výrazy jazyka C# se ověřují v době návrhu. Chyby ve výrazech jazyka C#, budou označeny červenou vlnovkou.  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)] C# výrazy, najdete v části [výrazy jazyka C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).  
  
###  <a name="BKMK_Visibility"></a> Další kontrolu nad viditelnost panelu prostředí a záhlaví položky  
 Opětovné hostování nástroje Designer některé standardní ovládací prvky uživatelského rozhraní nemusí mít význam pro daný pracovní postup a může být vypnutý. V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], tato přizpůsobení je podporovaná jenom rozhraním prostředí panelu v dolní části návrháře. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], viditelnost prostředí položky hlavičky v horní části návrháře lze upravit nastavením <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> s příslušnou <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> hodnotu.  
  
###  <a name="BKMK_AutoConnect"></a> Automaticky připojit a automatické vkládání v pracovních postupech vývojový diagram a stav počítače  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], připojení mezi uzly v pracovním postupu vývojový diagram museli přidat ručně. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], uzly vývojový diagram a stav počítače mají automaticky připojit body, které budou zobrazeny při přetažení aktivitu z panelu nástrojů na plochu návrháře. Vyřazení aktivitu na jeden z těchto bodů automaticky přidá aktivitu do aktivity společně s nezbytné připojení.  
  
 Následující snímek obrazovky znázorňuje body přílohy, které pak bude viditelný, když je aktivita přetažení z panelu nástrojů.  
  
 ![Počáteční uzel vývojový diagram znázorňující automatické připojení body](../../../docs/framework/windows-workflow-foundation/media/autoconnect1.png "Autoconnect1")  
  
 Aktivity lze také být přetáhli připojení mezi uzly vývojový diagram a stavy k automatické vložení uzlu mezi dvěma ostatní uzly. Následující snímek obrazovky ukazuje zvýrazněný řádek připojování, kde můžete aktivity přetažení z panelu nástrojů a vyřadit.  
  
 ![Automatické&#45;vložit popisovač pro vyřazení aktivity](../../../docs/framework/windows-workflow-foundation/media/autoinsert.png "Autoinsert")  
  
###  <a name="BKMK_Annotations"></a> Návrhář poznámky  
 Usnadňuje vývoj větší pracovních návrháře teď podporuje přidání poznámky do sleduje proces návrhu aplikace. Poznámky lze přidat do aktivity, stavy, vývojový diagram uzlů, proměnné a argumenty. Následující snímek obrazovky ukazuje v místní nabídce použít k přidání poznámky do návrháře.  
  
 ![Poznámky kontextovou nabídku](../../../docs/framework/windows-workflow-foundation/media/annotationdialog.png "annotationdialog")  
  
### <a name="debugging-states"></a>Ladění stavy  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], bez ohledu elementy nepodporuje ladicí zarážky vzhledem k tomu, že nebyly jednotky provádění. Tato verze poskytuje mechanismus pro přidání zarážky pro <xref:System.Activities.Statements.State> objekty. Pokud je zarážku nastavená na <xref:System.Activities.Statements.State>, provádění dojde k přerušení při stav převedena do, před vstupem jsou naplánované aktivity nebo aktivační události.  
  
###  <a name="BKMK_ActivityDelegates"></a> Definice a používání ActivityDelegate objektů v Návrháři  
 Aktivity v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] používá <xref:System.Activities.ActivityDelegate> objekty, které chcete zobrazit provádění body, kde dalších částí pracovního postupu může komunikovat s spuštění pracovního postupu, ale pomocí těchto bodů provádění obvykle vyžaduje správného množství kódu. V této verzi můžete vývojáři definice a používání delegátů aktivity pomocí návrháře pracovních postupů. Další informace najdete v tématu [postupy: definice a používání delegátů aktivity v Návrháři pracovních postupů](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).  
  
###  <a name="BKMK_BuildTimeValidation"></a> Ověření sestavení za běhu  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], pracovní postup ověření chyby nebyly počítají jako chyby sestavení během vytváření sestavení projektu pracovního postupu. Vynutila si vytvoření pracovního postupu projektu může být úspěšné i v případě, že se vyskytly chyby ověření pracovního postupu. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], způsobit chyby ověření pracovního postupu sestavení selhání.  
  
###  <a name="BKMK_DesignTimeValidation"></a> Ověření pozadí v době návrhu  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], pracovní postupy, které byly ověřeny jako proces na popředí, což může potenciálně zablokování uživatelského rozhraní během procesů ověřování složitý nebo časově náročná. Pracovní postup ověření nyní probíhá na vlákna na pozadí tak, aby nebyl blokován uživatelského rozhraní.  
  
###  <a name="BKMK_ViewState"></a> Stav zobrazení, které jsou umístěné v samostatné umístění v souborech XAML  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], informace o zobrazení stavu pro pracovní postup je ukládat v rámci souboru XAML v různých umístěních. Toto je nepohodlná pro vývojáře, kteří chtějí čtení XAML přímo, nebo napsat kód pro odebrat informace o stavu zobrazení. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zobrazení informací o stavu v souboru XAML serializován jako samostatný prvek v souboru XAML.  Vývojáře můžou snadno najít a upravit informace o zobrazení stavu aktivity nebo úplně odebrat stav zobrazení.  
  
###  <a name="BKMK_ExpressionExtensibility"></a> Rozšiřitelnost výraz  
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], nám umožňují vývojářům vytvářet své vlastní výraz a výraz pro tvorbu prostředí, které lze připojit do návrháře pracovních postupů.  
  
###  <a name="BKMK_BackwardCompatRehostedDesigner"></a> Výslovný souhlas pro funkce Workflow 4.5 v Návrháři opětovné hostování nástroje  
 Zachování zpětné kompatibility, některé nové funkce zahrnuté v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nejsou povolené ve výchozím nastavení v Návrháři opětovné hostování nástroje. To je potřeba zajistit, aby existující aplikace, které používají návrháři opětovné hostování nástroje nejsou přerušený při aktualizaci na nejnovější verzi. Pokud chcete povolit nové funkce v Návrháři opětovné hostování nástroje, nastavte <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> "Rozhraní .NET Framework 4.5", nebo jednotlivé členy sady <xref:System.Activities.Presentation.DesignerConfigurationService> k povolení jednotlivých funkcí.  
  
##  <a name="BKMK_NewWFModels"></a> Nový pracovní postup vývoj modely  
 Kromě vývojový diagram a modely vývoj sekvenční pracovní postup tato verze zahrnuje stav stavového stroje pracovní postupy a pracovního postupu první kontrakt služby.  
  
###  <a name="BKMK_StateMachine"></a> Pracovní postupy stavu počítače  
 Pracovní postupy stavu počítače byly zavedeny v rámci rozhraní .NET Framework 4, verze 4.0.1 v [rozhraní Microsoft .NET Framework 4 Platform Update 1](http://go.microsoft.com/fwlink/?LinkID=215092). Tato aktualizace zahrnuta několik nové třídy a aktivity, které povolené vývojářům vytvářet pracovní postupy stav počítače. Tyto třídy a aktivity byly aktualizovány pro [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Aktualizace zahrnují:  
  
1.  Možnost nastavit zarážky na stavy  
  
2.  Možnost Kopírovat a vkládat přechody v Návrháři pracovních postupů  
  
3.  Podpora návrháře pro vytvoření přechodu sdílené aktivační události  
  
4.  Aktivity použít k vytvoření pracovních stavu počítače, včetně: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, a <xref:System.Activities.Statements.Transition>  
  
 Následující snímek obrazovky ukazuje stavu dokončení pracovního postupu počítače z [kurzu Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) krok [postupy: vytvoření pracovního postupu stavu počítače](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md).  
  
 ![Dokončit pracovní postup stavového stroje](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Další informace o vytváření pracovních postupů stavu počítače najdete v tématu [stavu počítače pracovních](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).  
  
###  <a name="BKMK_ContractFirst"></a> Vývoj pro první kontrakt pracovního postupu  
 Nástroj pro vývoj kontrakt první pracovní postup umožňuje vývojáři navrhnout první kontraktu v kódu a potom pomocí několika kliknutí v sadě Visual Studio automaticky generovat šablonu aktivit v sadě nástrojů představující jednotlivých operací. Tyto aktivity jsou poté použít k vytvoření pracovního postupu, který implementuje operace definované kontrakt. Návrhář postupu provádění vyhodnotí služby pracovního postupu zajistit, že tyto operace jsou implementované a podpis pracovního postupu odpovídá podpisu smlouvy. Vývojář můžete taky přidružit kolekce implementovaná kontraktů služby pracovních postupů. Další informace o vývoj pracovního postupu první kontraktu služby najdete v tématu [postupy: vytvoření služby pracovního postupu, který využívá existující smlouvy služby](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).
