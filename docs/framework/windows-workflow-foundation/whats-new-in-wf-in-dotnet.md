---
title: Co je nového ve Windows Workflow Foundation v rozhraní .NET 4.5
ms.date: 03/30/2017
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
ms.openlocfilehash: 6afdca70dacb97cda4f72d7a6b4114c09d46bee1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279133"
---
# <a name="whats-new-in-windows-workflow-foundation-in-net-45"></a>Co je nového ve Windows Workflow Foundation v rozhraní .NET 4.5
Windows Workflow Foundation (WF) v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] přináší mnoho nových funkcí, jako jsou nové aktivity, návrháře funkce a pracovní postup vývoje modelů. Mnoho, ale ne všechny nový pracovní postup funkcí představených v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] jsou podporovány v Návrháři znovu hostovaných pracovních postupů. Další informace o nových funkcích, které jsou podporovány, naleznete v tématu [podpora nových funkcí Workflow Foundation 4.5 v Návrháři postupu provádění se změněným hostováním](../../../docs/framework/windows-workflow-foundation/wf-features-in-the-rehosted-workflow-designer.md). Další informace o migraci .NET 3.0 a 3.5 rozhraní .NET aplikace pracovního postupu chcete používat nejnovější verzi najdete v tématu [pokyny k migraci](../../../docs/framework/windows-workflow-foundation/migration-guidance.md). Toto téma obsahuje přehled o nové funkce pracovního postupu v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)].  
  
> [!WARNING]
>  Nové funkce Windows Workflow Foundation v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nejsou k dispozici pro projekty, které cílí na předchozí verze rozhraní Framework. Pokud projekt, který cílí na [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] znovu cílí na předchozí verzi rozhraní framework, může nastat několik problémů.  
>   
>  -   Výrazy jazyka C# se nahradí v návrháři se zprávou **hodnota byla nastavená v XAML**.  
> -   Dojde k mnoha chyby sestavení, včetně následující chyba.  
>   
>  **Formát souboru není kompatibilní s aktuálním cílení rozhraní. Chcete-li převést formát souboru, explicitně uložte prosím soubor. Tato chybová zpráva přestane být zobrazována po uložení souboru a znovu otevřete návrháře.**  
  
##  <a name="BKMK_Versioning"></a> Správa verzí pracovního postupu  
 [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] zavedená několik nových funkcí správy verzí podle nového <xref:System.Activities.WorkflowIdentity> třídy. <xref:System.Activities.WorkflowIdentity> Autoři pracovního postupu aplikace poskytuje mechanismus pro mapování trvalé instance práce s jeho definicí.  
  
-   Vývojáři, kteří používají <xref:System.Activities.WorkflowApplication> hostování můžete použít <xref:System.Activities.WorkflowIdentity> k povolení hostování více verzí pracovní postup-souběžně. Instance trvalý pracovních postupů je možné načíst pomocí nového <xref:System.Activities.WorkflowApplicationInstance> třídy a pak <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> je možné zajistit správné verze definice pracovního postupu při vytváření instance hostitele <xref:System.Activities.WorkflowApplication>. Další informace najdete v tématu [použití WorkflowIdentity a správy verzí](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md) a [jak: Hostování několika verzí pracovní postup-souběžně](../../../docs/framework/windows-workflow-foundation/how-to-host-multiple-versions-of-a-workflow-side-by-side.md).  
  
-   <xref:System.ServiceModel.WorkflowServiceHost> je teď hostitelem více verzí. Když nasadíte novou verzi služby pracovního postupu, nové instance jsou vytvořeny pomocí nové služby, ale existující instance absolvovat s použitím předchozí verze. Další informace najdete v tématu [správy verzí vedle sebe ve třídě WorkflowServiceHost](../../../docs/framework/wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).  
  
-   Dynamická aktualizace byla zavedená, které poskytuje mechanismus pro aktualizaci definice trvalé instance práce. Další informace najdete v tématu [dynamická aktualizace](../../../docs/framework/windows-workflow-foundation/dynamic-update.md) a [jak: Aktualizace definice běžící Instance pracovního postupu](../../../docs/framework/windows-workflow-foundation/how-to-update-the-definition-of-a-running-workflow-instance.md).  
  
-   Upgrade databáze trvalosti vytvořené ve službě je poskytován skript databáze SqlWorkflowInstanceStoreSchemaUpgrade.sql [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] databázové skripty. Tento skript aktualizace [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] databáze trvalosti pro podporu nové možnosti správy verzí, počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Instance trvalá pracovního postupu v databázi jsou uvedeny výchozí hodnoty správy verzí a účastnit se spuštění vedle sebe a dynamické aktualizace. Další informace najdete v tématu [upgrade rozhraní .NET Framework 4 trvalost databází na podporu pracovních postupů správy verzí](../../../docs/framework/windows-workflow-foundation/using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).  
  
##  <a name="BKMK_NewActivities"></a> Aktivity  
 Knihovna předdefinovaných aktivit obsahuje nové aktivity a nové funkce pro existujících aktivit.  
  
###  <a name="BKMK_NoPersistScope"></a> A oboru  
 <xref:System.Activities.Statements.NoPersistScope> je nová aktivita kontejneru, který brání se jako trvalý, pokud jsou spuštěny NoPersistScope podřízené aktivity pracovního postupu. To je užitečné v situacích, kde není vhodné pro pracovní postup nastavit jako trvalý, například když pracovní postup používá prostředky specifické pro počítač, jako jsou popisovače souborů, nebo v průběhu transakce databáze. Dříve aby se zabránilo trvalost z vyskytovat se během provádění aktivity, vlastní <xref:System.Activities.NativeActivity> , který používá <xref:System.Activities.NoPersistHandle> nebyla nutná.  
  
###  <a name="BKMK_NewFlowchartCapabilities"></a> Nové funkce vývojového diagramu  
 Vývojové diagramy se aktualizují pro [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] a mají následující nové funkce:  
  
-   `DisplayName` Vlastnost <xref:System.Activities.Statements.FlowSwitch%601> nebo <xref:System.Activities.Statements.FlowDecision> aktivitu je možné upravovat. To vám umožní zobrazit další informace o účelu aktivity návrháře aktivit.  
  
-   Na vývojových diagramech mají novou vlastnost s názvem <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A>; výchozí hodnota této vlastnosti je `False`. Pokud je tato vlastnost nastavená na `True`, pak uzly nepřipojené vývojový diagram způsobí chyby ověření.  
  
## <a name="support-for-partial-trust"></a>Podpora pro částečné důvěryhodnosti  
 Pracovní postupy v [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] vyžaduje plně důvěryhodné aplikaci domény. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], pracovní postupy mohou pracovat v prostředí s částečnou důvěryhodností. V prostředí s částečným vztahem důvěryhodnosti je možné bez nutnosti přidělit jim úplný přístup k prostředkům hostitele komponenty třetích stran. Některé obavy o spouštění pracovních postupů v částečném vztahu důvěryhodnosti se takto:  
  
1.  Používání starší verze komponent (včetně pravidla) součástí <xref:System.Activities.Statements.Interop> aktivity není podporován v částečném vztahu důvěryhodnosti.  
  
2.  Spouštění pracovních postupů v částečném vztahu důvěryhodnosti v <xref:System.ServiceModel.WorkflowServiceHost> se nepodporuje.  
  
3.  Zachování výjimky v částečným vztahem důvěryhodnosti scénář je potenciální ohrožení zabezpečení. Zakázat uchování výjimek, rozšíření typu <xref:System.Activities.ExceptionPersistenceExtension> musí být přidaný do projektu, pokud chcete vyjádřit výslovný nesouhlas zachování výjimky. Následující příklad kódu ukazuje, jak implementovat tohoto typu.  
  
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
  
     Pokud není k serializaci jsou výjimky, ujistěte se, že výjimky se používají v rámci <xref:System.Activities.Statements.NoPersistScope>.  
  
4.  Aktivita autoři by měly přepsat <xref:System.Activities.Activity.CacheMetadata%2A> vyhnout modulu runtime pracovního postupu automaticky spustit reflexe proti typu. Argumenty a podřízené aktivity musí mít hodnotu null, a <xref:System.Activities.ActivityMetadata.Bind%2A> musí být explicitně volána. Další informace o přepsání <xref:System.Activities.Activity.CacheMetadata%2A>, naleznete v tématu [zveřejnění dat pomocí CacheMetadata](../../../docs/framework/windows-workflow-foundation/exposing-data-with-cachemetadata.md). Navíc instancí argumentů, které jsou typu, který je `internal` nebo **privátní** musí být explicitně vytvořeny v <xref:System.Activities.Activity.CacheMetadata%2A> , aby se vytvořil reflexe.  
  
5.  Nebudeme používat typy <xref:System.Runtime.Serialization.ISerializable> nebo <xref:System.SerializableAttribute> pro serializaci; typy, které jsou k serializaci musí podporovat <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
6.  Výrazy, které používají <xref:System.Activities.Expressions.LambdaValue%601> vyžadují <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A>a proto nebude fungovat v částečném vztahu důvěryhodnosti. Pracovní postupy využívající <xref:System.Activities.Expressions.LambdaValue%601> měli nahradit aktivity, které jsou odvozeny z těchto výrazů <xref:System.Activities.CodeActivity%601>. .  
  
7.  Výrazy nemůže být kompilováno s použitím <xref:System.Activities.XamlIntegration.TextExpressionCompiler> nebo Visual Basic hostují kompilátoru v částečném vztahu důvěryhodnosti, ale je možné spustit dříve zkompilované výrazy.  
  
8.  Jediné sestavení, která používá [transparentnosti úrovně 2](https://aka.ms/Level2Transparency) nelze použít v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v režimu plné důvěryhodnosti a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v částečném vztahu důvěryhodnosti.  
  
##  <a name="BKMK_NewDesignerCapabilites"></a> Nové možnosti návrháře  
  
###  <a name="BKMK_DesignerSearch"></a> Návrháře vyhledávání  
 K udržitelnější správu větší pracovních postupů, pracovní postupy mohou nyní vyhledat – klíčové slovo. Tato funkce dostupná jenom v sadě Visual Studio; Tato funkce není k dispozici v návrháři se změněným hostováním. Nejsou k dispozici dva druhy hledání:  
  
-   Rychlé vyhledání iniciovala s buď **Ctrl + F** nebo **upravit**, **najít a nahradit**, **rychlé hledání**.  
  
-   Najít v souborech, iniciovala s buď **Ctrl + Shift + F** nebo **upravit**, **najít a nahradit**, **najít v souborech**.  
  
 Mějte na paměti, že nahradit nepodporuje.  
  
####  <a name="BKMK_QuickFind"></a> Rychlé hledání  
 Klíčová slova v pracovních postupech prohledána bude odpovídat návrháře následující položky:  
  
-   Vlastnosti <xref:System.Activities.Activity> objekty, <xref:System.Activities.Statements.FlowNode> objekty, <xref:System.Activities.Statements.State> objekty, <xref:System.Activities.Statements.Transition> objekty a další položky vlastní řízení toku.  
  
-   Proměnné  
  
-   Arguments  
  
-   Výrazy  
  
 Rychlé vyhledání se provádí na návrháře <xref:System.Activities.Presentation.Model.ModelItem> stromu. Rychlé vyhledání nelze vyhledat definice pracovního postupu byla naimportována obory názvů.  
  
####  <a name="BKMK_FindInFiles"></a> Najít v souborech  
 Klíčová slova v pracovních postupech prohledána bude odpovídat skutečné obsah souborů pracovního postupu. Výsledky hledání se zobrazí v podokně Výsledky hledání Visual Studio. Položka výsledků dvakrát klikněte na aktivitu, která obsahuje shodu v Návrháři pracovních postupů.  
  
###  <a name="BKMK_VariableDeleteContextMenu"></a> Odstranit položky kontextové nabídky v Návrháři proměnných a argumentů  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], proměnné a argumenty může odstranit jenom v Návrháři pomocí klávesnice. Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], proměnné a argumenty je možné odstranit pomocí místní nabídky.  
  
 Následující snímek obrazovky ukazuje návrháře kontextové nabídky proměnných a argumentů.  
  
 ![Proměnné a Argument místní nabídka návrháře](../../../docs/framework/windows-workflow-foundation/media/designercontextmenu.png "DesignerContextMenu")  
  
###  <a name="BKMK_AutoSurround"></a> Automatické kulatých pořadí  
 Od pracovního postupu nebo určité aktivity kontejneru (například <xref:System.Activities.Statements.NoPersistScope>) může obsahovat jenom jeden text aktivity, přidání druhé aktivity vyžaduje vývojářům první aktivita odstranění, přidání <xref:System.Activities.Statements.Sequence> aktivity a pak přidat obě aktivity k sekvenční aktivity. Počínaje [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], při přidání druhé aktivity na plochu návrháře `Sequence` aktivity se automaticky vytvoří při zabalení obě aktivity.  
  
 Následující snímek obrazovky ukazuje `WriteLine` aktivity v `Body` z `NoPersistScope`.  
  
 ![Automatické&#45;před a za místo přetažení](../../../docs/framework/windows-workflow-foundation/media/autosurround1.png "AutoSurround1")  
  
 Následující snímek obrazovky ukazuje automaticky vytvořený `Sequence` aktivity v `Body` při sekundy `WriteLine` neklesla pod první.  
  
 ![Automaticky vytvořit sekvenční aktivitu](../../../docs/framework/windows-workflow-foundation/media/autosurround2.png "AutoSurround2")  
  
###  <a name="BKMK_PanMode"></a> Režim posouvání  
 Velké pracovní postup v Návrháři snadněji přejít, je možné povolit režim posouvání umožňuje vývojářům klikněte a tažením přesuňte viditelnou část pracovního postupu, místo nutnosti použít posuvníky. Tlačítko aktivovat režim posouvání se v pravém dolním rohu návrháře.  
  
 Následující snímek obrazovky ukazuje tlačítko posouvání, která se nachází v pravém dolním rohu návrháře postupu provádění.  
  
 ![Tlačítko posouvání v Návrháři pracovních postupů](../../../docs/framework/windows-workflow-foundation/media/panbutton.png "PanButton")  
  
 Prostřední tlačítko myši nebo MEZERNÍK lze použít také k posouvání návrháře postupu provádění.  
  
###  <a name="BKMK_MultiSelect"></a> Vícenásobný výběr  
 Více aktivit můžete vybrat najednou, buď přetažením obdélníkem (když není povolen režim posouvání), nebo tím, že podržíte stisknutou klávesu Ctrl a klikněte na požadovaný aktivity jeden po druhém.  
  
 Více výběrů aktivita může také být přetáhnout v návrháři a můžete také interakci s použitím místní nabídky.  
  
###  <a name="BKMK_DocumentOutline"></a> Zobrazení osnovy položky pracovního postupu  
 Pokud chcete mít hierarchické pracovních postupů přehlednější a díky tomu, komponenty pracovního postupu se zobrazí v zobrazení stromové osnovy. Zobrazí se v zobrazení osnovy **Osnova dokumentu** zobrazení. Chcete-li otevřít toto zobrazení z hlavní nabídky, vyberte **zobrazení**, **ostatní Windows**, **Osnova dokumentu**, nebo stiskněte klávesy Ctrl W, U. Kliknutím na uzel v zobrazení osnovy přejdete na odpovídající aktivity v Návrháři pracovních postupů a zobrazení osnovy se aktualizuje a zobrazí aktivity, které jsou vybrány v návrháři.  
  
 Na následujícím snímku obrazovky dokončené pracovní postup [kurz Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) zobrazuje zobrazení osnovy s sekvenčního pracovního postupu.  
  
 ![Zobrazení v Návrháři pracovních postupů osnovy](../../../docs/framework/windows-workflow-foundation/media/outlineviewinworkflowdesigner.jpg "OutlineViewinWorkflowDesigner")  
  
###  <a name="BKMK_CSharpExpressions"></a> Výrazy jazyka C#  
 Před verzí [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], všechny výrazy v pracovních postupech, může být pouze napsaná v jazyce Visual Basic. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], výrazy jazyka Visual Basic se používají pouze pro projekty vytvořené pomocí jazyka Visual Basic. Projekty Visual C# nyní pomocí C# pro výrazy. Jaké schopnosti zvýraznění gramatiky a technologie intellisense je k dispozici plně funkční editor výrazů C#. Pracovní postup projekty jazyka C# vytvořené v předchozích verzích, které používají výrazy jazyka Visual Basic, budou nadále fungovat.  
  
 Výrazy jazyka C# se ověřují v době návrhu. Chyby ve výrazech jazyka C#, budou označeny červenou vlnovkou.  
  
 Další informace o výrazy jazyka C# najdete v tématu [výrazy jazyka C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md).  
  
###  <a name="BKMK_Visibility"></a> Větší míra kontroly viditelnost panelu prostředí a v záhlaví položek  
 V návrháři se změněným hostováním některé standardní ovládací prvky uživatelského rozhraní nemůže mít význam pro daný pracovní postup a může být vypnuté. V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], tato přizpůsobení je podporována pouze na prostředí panelu v dolní části okna návrháře. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], viditelnost prostředí položek záhlaví v horní části okna návrháře je možné upravit tak, že nastavíte <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> příslušnou <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> hodnotu.  
  
###  <a name="BKMK_AutoConnect"></a> Automatické připojení a automatické vložení v pracovních postupech vývojový diagram a stavového stroje.  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], připojení mezi uzly v pracovním postupu vývojového diagramu musí přidat ručně. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], vývojový diagram a stavového stroje uzly mají automaticky připojit body, které pak bude viditelný, když je aktivita přetáhnout z panelu nástrojů na plochu návrháře. Přetažení aktivity v jednom z těchto bodů automaticky přidá aktivitu do aktivity spolu s nezbytné připojení.  
  
 Následující snímek obrazovky ukazuje body přílohy, které pak bude viditelný, když je aktivita přetáhnout z panelu nástrojů.  
  
 ![Počáteční uzel vývojový diagram zobrazuje body automatické připojení](../../../docs/framework/windows-workflow-foundation/media/autoconnect1.png "Autoconnect1")  
  
 Aktivity můžete také přetahovat do připojení mezi uzly vývojový diagram a stavy pro automatické vložení uzlu mezi dvou jiných uzlech. Následující snímek obrazovky ukazuje zvýrazněný řádek připojení, kde můžete přetáhnout z panelu nástrojů a vyřadit aktivity.  
  
 ![Automatické&#45;vložit úchyt pro přetažení aktivity](../../../docs/framework/windows-workflow-foundation/media/autoinsert.png "Autoinsert")  
  
###  <a name="BKMK_Annotations"></a> Návrháře poznámky  
 Usnadňuje vývoj větší pracovních postupů návrháře nyní podporuje přidávání poznámek k pomáhají udržovat přehled o procesu návrhu. Komentáře lze přidat do aktivity, státy, vývojový diagram uzly, proměnné a argumenty. Na následujícím snímku obrazovky se zobrazí místní nabídku pro přidání poznámky do návrháře.  
  
 ![Poznámka kontextovou nabídku](../../../docs/framework/windows-workflow-foundation/media/annotationdialog.png "annotationdialog")  
  
### <a name="debugging-states"></a>Ladění stavy  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], elementy bez ohledu nelze podporu ladění zarážek, protože nebyly jednotky spuštění. Tato verze poskytuje mechanismus pro přidání zarážky pro <xref:System.Activities.Statements.State> objekty. Pokud byla nastavena zarážka na <xref:System.Activities.Statements.State>, spuštění se přeruší, když se stav postoupí, před vstupem jsou naplánované aktivity nebo aktivační události.  
  
###  <a name="BKMK_ActivityDelegates"></a> Definice a používání objektu ActivityDelegate objektů v Návrháři  
 Aktivity v [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] použít <xref:System.Activities.ActivityDelegate> objekty k vystavení body provádění kde ostatní části pracovního postupu může pracovat s pracovní postup spouštění, ale obvykle pomocí těchto bodů provádění požadované množství kódu. V této verzi můžou vývojáři definice a používání delegátů aktivit pomocí návrháře postupu provádění. Další informace najdete v tématu [jak: Definice a používání delegátů aktivit v Návrháři postupu provádění](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).  
  
###  <a name="BKMK_BuildTimeValidation"></a> Ověření při sestavení  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], chyby ověření pracovního postupu se přitom počítá jako chyby sestavení během sestavování projektu pracovního postupu. To znamená, že tento pracovní postup sestavení projektu může úspěšné i v případě, že došlo k chybě ověření pracovního postupu. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], aby sestavení selhalo, způsobit chyby ověření pracovního postupu.  
  
###  <a name="BKMK_DesignTimeValidation"></a> Ověřování na pozadí v době návrhu  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], pracovní postupy, které byly ověřeny jako proces na popředí, která by mohla potenciálně přestane reagovat uživatelské rozhraní během procesů ověřování složité a časově náročné. Ověření pracovního postupu nyní probíhá na vlákně na pozadí, tak, aby uživatelského rozhraní není blokován.  
  
###  <a name="BKMK_ViewState"></a> Stav zobrazení, které jsou umístěné v samostatném umístění v souborech XAML  
 V [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], informace o zobrazení stavu pracovního postupu je uložen v souboru XAML v mnoha různých umístěních. Toto je vhodná pro vývojáře, kteří chtějí XAML přímo číst nebo napsat kód, který odebrat informace o stavu zobrazení. V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], zobrazit informace o stavu v souboru XAML je serializován jako samostatný prvek v souboru XAML.  Vývojáře můžou snadno najít a upravit informace o zobrazení stavu aktivity nebo zcela odebrat stav zobrazení.  
  
###  <a name="BKMK_ExpressionExtensibility"></a> Rozšiřitelnost výraz  
 V [!INCLUDE[net_v45](../../../includes/net-v45-md.md)], poskytujeme způsob, jak mohou vývojáři vytvářet vlastní výrazem a výraz zážitky, které může být připojeno v Návrháři postupu provádění.  
  
###  <a name="BKMK_BackwardCompatRehostedDesigner"></a> Vyjádřit výslovný souhlas pro funkce pracovního postupu 4.5 v návrháři se změněným hostováním  
 Pro zachování zpětné kompatibility, některé nové funkce zahrnuté v [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] nejsou povolené ve výchozím nastavení v návrháři se změněným hostováním. Tím je zajištěno, že existující aplikace, které používají návrháři se změněným hostováním negativně neovlivní aktualizace na nejnovější verzi. Chcete-li povolit nové funkce v návrháři se změněným hostováním, buď nastavte <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> "Rozhraní .NET Framework 4.5", nebo nastavení jednotlivých členů <xref:System.Activities.Presentation.DesignerConfigurationService> povolení jednotlivých funkcí.  
  
##  <a name="BKMK_NewWFModels"></a> Pracovní postup vývoje modelů  
 Kromě vývojový diagram a sekvenční pracovní postup vývoje modelů tato verze zahrnuje pracovní postupy stavu počítače a služby stavící do pracovního postupu.  
  
###  <a name="BKMK_StateMachine"></a> Pracovní postupy stavového stroje  
 Pracovní postupy stavového stroje byly představeny jako součást rozhraní .NET Framework 4, verze 4.0.1 [rozhraní Microsoft .NET Framework 4 aktualizace platformy 1](https://go.microsoft.com/fwlink/?LinkID=215092). Tato aktualizace je zahrnuta několik nových třídách a činnostech, které mohou vývojáři vytvářet pracovní postupy stavu počítače povolené. Tyto třídy a činnosti byly aktualizovány [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Aktualizace zahrnují:  
  
1.  Možnost nastavit zarážky na stavy  
  
2.  Možnost kopírování a vkládání přechodů v Návrháři postupu provádění  
  
3.  Podpora návrhářů pro sdílené vytváření aktivačních přechodů  
  
4.  Aktivity použít k vytváření pracovních postupů stavového stroje, včetně: <xref:System.Activities.Statements.StateMachine>, <xref:System.Activities.Statements.State>, a <xref:System.Activities.Statements.Transition>  
  
 Následující snímek obrazovky ukazuje pracovní postup dokončený stav stroje ze [kurz Začínáme](../../../docs/framework/windows-workflow-foundation/getting-started-tutorial.md) krok [jak: Vytvoření pracovního postupu stavového stroje](../../../docs/framework/windows-workflow-foundation/how-to-create-a-state-machine-workflow.md).  
  
 ![Dokončení pracovního postupu stavového stroje](../../../docs/framework/windows-workflow-foundation/media/wfstatemachinegettingstartedtutorialcomplete.JPG "WFStateMachineGettingStartedTutorialComplete")  
  
 Další informace o vytváření pracovní postupy stavu počítače, naleznete v tématu [pracovní postupy stavu počítače](../../../docs/framework/windows-workflow-foundation/state-machine-workflows.md).  
  
###  <a name="BKMK_ContractFirst"></a> Vývoj stavící do pracovního postupu  
 Pracovní postup kontraktem vývojový nástroj umožňuje vývojářům navrhovat smlouvy v kódu a potom pomocí několika kliknutí v sadě Visual Studio automaticky vygenerovat šablonu aktivit v sadě nástrojů představující každé operace. Tyto aktivity se pak používají k vytvoření pracovního postupu, který implementuje operace definované ve smlouvě. Návrháře postupu provádění se ověří pracovní postup služby zajistíte, že tyto operace jsou implementovány a podpis pracovního postupu odpovídá podpisu smlouvu. Vývojář můžete taky přidružit kolekce implementované kontrakty služby pracovního postupu. Další informace o vývoj služby stavící do pracovního postupu najdete v tématu [jak: Vytvoření služby pracovního postupu, která využívá existující kontrakt služby](../../../docs/framework/windows-workflow-foundation/how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).
