---
title: Novinky ve Windows Workflow Foundation v rozhraní .NET 4.5
description: Programovací model Windows Workflow Foundation v .NET Framework 4,5 zavádí mnoho nových funkcí, jako jsou nové aktivity, možnosti návrháře a vývojové modely pracovního postupu.
ms.date: 03/30/2017
ms.assetid: 195c43a8-e0a8-43d9-aead-d65a9e6751ec
ms.openlocfilehash: 85555e48929885b6eef7fde6ac0c9017fa403d4d
ms.sourcegitcommit: 9a4488a3625866335e83a20da5e9c5286b1f034c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2020
ms.locfileid: "83419457"
---
# <a name="whats-new-in-windows-workflow-foundation-in-net-45"></a>Novinky ve Windows Workflow Foundation v rozhraní .NET 4.5

Programovací model Windows Workflow Foundation (WF) v .NET Framework 4,5 zavádí mnoho nových funkcí, jako jsou nové aktivity, možnosti návrháře a vývojové modely pracovního postupu. Mnohé, ale ne všechny nové funkce pracovního postupu, které jsou představené v .NET Framework 4,5, jsou podporované v Návrháři opětovného hostovaného pracovního postupu. Další informace o nových funkcích, které jsou podporovány, naleznete [v tématu Support for New Workflow Foundation 4,5 Features in the hosted Návrhář postupu provádění](wf-features-in-the-rehosted-workflow-designer.md). Další informace o migraci aplikací pro pracovní postup .NET 3,0 a .NET 3,5 na používání nejnovější verze najdete v tématu [pokyny k migraci](migration-guidance.md). V tomto tématu najdete přehled nových funkcí pracovního postupu, které jsou představené v .NET Framework 4,5.

> [!WARNING]
> Nové funkce programovací model Windows Workflow Foundation představené v .NET Framework 4,5 nejsou k dispozici pro projekty, které cílí na předchozí verze rozhraní .NET Framework. Pokud je projekt, který cílí na .NET Framework 4,5, znovu cílen na předchozí verzi rozhraní, může dojít k několika problémům.
>
> - Výrazy jazyka C# budou v Návrháři nahrazeny **hodnotou zprávy nastavenou v jazyce XAML**.
> - Dojde k mnoha chybám sestavení, včetně následující chyby.
>
> **Formát souboru není kompatibilní s aktuálním cílovým rozhraním. Chcete-li převést formát souboru, soubor prosím explicitně uložte. Tato chybová zpráva zmizí po uložení souboru a opětovném otevření návrháře.**

## <a name="workflow-versioning"></a><a name="BKMK_Versioning"></a>Správa verzí pracovních postupů

.NET Framework 4,5 zavedlo několik nových funkcí správy verzí založených na nové <xref:System.Activities.WorkflowIdentity> třídě. <xref:System.Activities.WorkflowIdentity>poskytuje autorům aplikace pracovního postupu mechanismus pro mapování trvalé instance pracovního postupu s její definicí.

- Vývojáři, kteří používají <xref:System.Activities.WorkflowApplication> hostování, můžou <xref:System.Activities.WorkflowIdentity> Povolit hostování více verzí pracovního postupu vedle sebe. Trvalé instance pracovního postupu mohou být načteny pomocí nové <xref:System.Activities.WorkflowApplicationInstance> třídy a poté <xref:System.Activities.WorkflowApplicationInstance.DefinitionIdentity%2A> mohou být použity hostitelem k poskytnutí správné verze definice pracovního postupu při vytváření instance <xref:System.Activities.WorkflowApplication> . Další informace najdete v tématu [použití identita WorkflowIdentity a správy verzí](using-workflowidentity-and-versioning.md) a [Postup: hostování více verzí pracovního postupu vedle](how-to-host-multiple-versions-of-a-workflow-side-by-side.md)sebe.

- <xref:System.ServiceModel.WorkflowServiceHost>je teď hostitel s více verzemi. Při nasazení nové verze služby pracovního postupu se nové instance vytvoří pomocí nové služby, ale existující instance se dokončí pomocí předchozí verze. Další informace najdete v tématu [Správa verzí vedle sebe v hostiteli WorkflowServiceHost](../wcf/feature-details/side-by-side-versioning-in-workflowservicehost.md).

- Zavádí se dynamická aktualizace, která poskytuje mechanismus pro aktualizaci definice trvalé instance pracovního postupu. Další informace najdete v tématu [Dynamická aktualizace](dynamic-update.md) a [Postupy: aktualizace definice spuštěné instance pracovního postupu](how-to-update-the-definition-of-a-running-workflow-instance.md).

- K upgradu databáze trvalosti vytvořené pomocí databázových skriptů .NET Framework 4 se poskytuje skript databáze SqlWorkflowInstanceStoreSchemaUpgrade. SQL. Tento skript aktualizuje .NET Framework 4 databáze trvalosti tak, aby podporovaly nové možnosti správy verzí, které byly zavedeny v .NET Framework 4,5. Trvalé instance pracovního postupu v databázi mají nastavené výchozí hodnoty správy verzí a můžou se účastnit souběžného spouštění a dynamické aktualizace. Další informace najdete v tématu [upgrade databáze .NET Framework 4 Persistence pro podporu správy verzí pracovních postupů](using-workflowidentity-and-versioning.md#UpdatingWF4PersistenceDatabases).

## <a name="activities"></a><a name="BKMK_NewActivities"></a>Soutěž

Integrovaná knihovna aktivit obsahuje nové aktivity a nové funkce pro existující aktivity.

### <a name="nopersist-scope"></a><a name="BKMK_NoPersistScope"></a>Zachovat obor

<xref:System.Activities.Statements.NoPersistScope>je nová aktivita kontejneru, která brání trvalému uložení pracovního postupu při provádění podřízených aktivit oboru NoPersistScope. To je užitečné ve scénářích, kdy není vhodné pro pracovní postup, například když pracovní postup používá prostředky specifické pro počítač, jako jsou popisovače souborů nebo během transakcí databáze. Dříve, aby nedocházelo k trvalému výskytu během provádění aktivity, <xref:System.Activities.NativeActivity> <xref:System.Activities.NoPersistHandle> bylo nutné použít vlastní.

### <a name="new-flowchart-capabilities"></a><a name="BKMK_NewFlowchartCapabilities"></a>Nové možnosti vývojového diagramu

Vývojové diagramy jsou aktualizované pro .NET Framework 4,5 a mají následující nové funkce:

- `DisplayName`Vlastnost <xref:System.Activities.Statements.FlowSwitch%601> <xref:System.Activities.Statements.FlowDecision> aktivity nebo je upravitelná. To umožní návrháři aktivity Zobrazit další informace o účelu aktivity.

- Vývojové diagramy mají novou vlastnost nazvanou <xref:System.Activities.Statements.Flowchart.ValidateUnconnectedNodes%2A> ; Výchozí hodnota pro tuto vlastnost je `False` . Pokud je tato vlastnost nastavená na `True` , nepřipojené uzly vývojového diagramu vytvoří chyby ověřování.

## <a name="support-for-partial-trust"></a>Podpora částečné důvěryhodnosti

Pracovní postupy v .NET Framework 4 vyžadovaly plně důvěryhodnou doménu aplikace. V .NET Framework 4,5 mohou pracovní postupy fungovat v prostředí s částečným vztahem důvěryhodnosti. V prostředí s částečným vztahem důvěryhodnosti lze použít komponenty třetích stran bez udělení úplného přístupu k prostředkům hostitele. Mezi obavy týkající se spouštění pracovních postupů v částečném vztahu důvěryhodnosti patří následující:

1. Použití starších komponent (včetně pravidel) obsažených v <xref:System.Activities.Statements.Interop> aktivitě není v případě částečné důvěryhodnosti podporováno.

2. Spuštění pracovních postupů v částečném vztahu důvěryhodnosti v <xref:System.ServiceModel.WorkflowServiceHost> není podporováno.

3. Zachování výjimek v případě částečné důvěryhodnosti je potenciální bezpečnostní hrozba. Chcete-li zakázat zachování výjimek, je <xref:System.Activities.ExceptionPersistenceExtension> nutné do projektu přidat rozšíření typu, aby bylo možné odhlásit z trvalých výjimek. Následující příklad kódu ukazuje, jak implementovat tento typ.

    ```csharp
    public class ExceptionPersistenceExtension
    {
        public ExceptionPersistenceExtension()
        {
            this.PersistExceptions = false;
        }
        public bool PersistExceptions { get; set; }
    }
    ```

     Pokud výjimky nejsou serializován, zajistěte, aby byly výjimky použity v rámci <xref:System.Activities.Statements.NoPersistScope> .

4. Autoři aktivity by měli přepsat <xref:System.Activities.Activity.CacheMetadata%2A> , aby nedocházelo k automatickému spuštění reflexe modulu Workflow na typ. Argumenty a podřízené aktivity nesmí být null a <xref:System.Activities.ActivityMetadata.Bind%2A> musí být explicitně volány. Další informace o přepsání najdete <xref:System.Activities.Activity.CacheMetadata%2A> v tématu [vystavení dat pomocí voláním funkce CacheMetadata](exposing-data-with-cachemetadata.md). Instance argumentů, které jsou typu, které jsou `internal` nebo jsou **privátní** , musí být explicitně vytvořeny v, <xref:System.Activities.Activity.CacheMetadata%2A> aby nedocházelo k vytváření reflexe.

5. Typy nebudou použity <xref:System.Runtime.Serialization.ISerializable> ani <xref:System.SerializableAttribute> pro serializaci, typy, které mají být serializovány, musí podporovat <xref:System.Runtime.Serialization.DataContractSerializer> .

6. Výrazy, které <xref:System.Activities.Expressions.LambdaValue%601> vyžadují <xref:System.Security.Permissions.ReflectionPermissionAttribute.RestrictedMemberAccess%2A> , a proto nebudou fungovat s částečnou důvěryhodností. Pracovní postupy, které používají, <xref:System.Activities.Expressions.LambdaValue%601> by měly nahradit tyto výrazy aktivitami, které jsou odvozeny z <xref:System.Activities.CodeActivity%601> . .

7. Výrazy nelze zkompilovat pomocí <xref:System.Activities.XamlIntegration.TextExpressionCompiler> nebo Visual Basic hostovaného kompilátoru v částečném vztahu důvěryhodnosti, ale je možné spustit dříve zkompilované výrazy.

8. Jedno sestavení, které používá [transparentnost úrovně 2](https://aka.ms/Level2Transparency) , nelze použít v .NET Framework 4, [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v úplném vztahu důvěryhodnosti a [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] v částečném vztahu důvěryhodnosti.

## <a name="new-designer-capabilities"></a><a name="BKMK_NewDesignerCapabilites"></a>Nové možnosti návrháře

### <a name="designer-search"></a><a name="BKMK_DesignerSearch"></a>Hledání návrháře

Chcete-li zvýšit možnosti správy většího pracovního postupu, mohou být pracovní postupy nyní prohledávány pomocí klíčového slova. Tato funkce je k dispozici pouze v aplikaci Visual Studio; Tato funkce není k dispozici v přehostujícím návrháři. K dispozici jsou dva druhy hledání:

- Rychlé hledání iniciované pomocí **kombinace kláves CTRL + F** nebo **Úpravy**, **hledání a nahrazení**, **Rychlé hledání**.

- Najít v souborech, které byly zahájeny pomocí **kombinace kláves CTRL + SHIFT + F** nebo **Upravit**, **Najít a nahradit**, **najdete v souborech**.

Poznámka: nahrazení se nepodporuje.

#### <a name="quick-find"></a><a name="BKMK_QuickFind"></a>Rychlé hledání

Klíčová slova prohledaná v pracovních postupech budou odpovídat následujícím položkám návrháře:

- Vlastnosti <xref:System.Activities.Activity> objektů, <xref:System.Activities.Statements.FlowNode> objektů, <xref:System.Activities.Statements.State> objektů, <xref:System.Activities.Statements.Transition> objektů a dalších vlastních položek řízení toku.

- Proměnné

- Arguments

- Výrazy

Rychlé hledání se provádí ve <xref:System.Activities.Presentation.Model.ModelItem> stromové struktuře návrháře. Při rychlém hledání se obory názvů importované do definice pracovního postupu nehledají.

#### <a name="find-in-files"></a><a name="BKMK_FindInFiles"></a>Najít v souborech

Klíčová slova prohledaná v pracovních postupech budou odpovídat skutečnému obsahu souborů pracovního postupu. Výsledky hledání se zobrazí v podokně najít Výsledky sady Visual Studio. Dvojím kliknutím na výslednou položku přejdete na aktivitu, která obsahuje shodu v Návrháři pracovních postupů.

### <a name="delete-context-menu-item-in-variable-and-argument-designer"></a><a name="BKMK_VariableDeleteContextMenu"></a>Odstranit položku kontextové nabídky v Návrháři proměnných a argumentů

V .NET Framework 4 lze proměnné a argumenty odstranit pouze v Návrháři pomocí klávesnice. Počínaje .NET Framework 4,5 lze proměnné a argumenty odstranit pomocí místní nabídky.

Následující snímek obrazovky ukazuje kontextovou nabídku návrháře proměnných a argumentů.

![Kontextová nabídka návrháře proměnných a argumentů](./media/whats-new-in-wf-in-dotnet/designer-context-menu.png)

### <a name="auto-surround-with-sequence"></a><a name="BKMK_AutoSurround"></a>Automaticky uzavřít sekvencí

Vzhledem k tomu, že pracovní postup nebo určité aktivity kontejneru (například <xref:System.Activities.Statements.NoPersistScope> ) může obsahovat pouze jednu aktivitu těla, přidání druhé aktivity, která vývojář vyžádala odstranit první aktivitu, přidat <xref:System.Activities.Statements.Sequence> aktivitu a pak přidat obě aktivity do aktivity sekvence. Počínaje .NET Framework 4,5 se při přidávání druhé aktivity na plochu návrháře `Sequence` automaticky vytvoří aktivita, která zabalí obě aktivity.

Následující snímek obrazovky ukazuje `WriteLine` aktivitu v rámci `Body` `NoPersistScope` .

![Aktivita WriteLine v těle aktivity oboru NoPersistScope](./media/whats-new-in-wf-in-dotnet/auto-surround-write-line-activity.png)

Na následujícím snímku obrazovky se zobrazuje automaticky vytvořená `Sequence` aktivita v `Body` okamžiku, kdy `WriteLine` je druhý vyřazen pod první.

![Automaticky vytvořená sekvence v těle oboru nopersistscopeu.](./media/whats-new-in-wf-in-dotnet/auto-surround-sequence-activity.png)

### <a name="pan-mode"></a><a name="BKMK_PanMode"></a>Režim posouvání

Chcete-li snadněji procházet rozsáhlý pracovní postup v návrháři, můžete povolit režim posouvání, který vývojářům umožňuje kliknout a přetáhnout, aby přesunul viditelnou část pracovního postupu, místo aby bylo nutné používat posuvníky. Tlačítko pro aktivaci režimu posunu je v pravém dolním rohu návrháře.

Na následujícím snímku obrazovky vidíte tlačítko posouvání, které se nachází v pravém dolním rohu návrháře pracovních postupů.

![Tlačítko posouvání zvýrazněné v Návrháři postupu.](./media/whats-new-in-wf-in-dotnet/pan-button-workflow-designer.png)

K posouvání návrháře pracovních postupů můžete použít také prostřední tlačítko myši nebo MEZERNÍK.

### <a name="multi-select"></a><a name="BKMK_MultiSelect"></a>Vícenásobný výběr

Najednou lze vybrat více aktivit, buď přetažením obdélníku kolem nich (když režim posouvání není povolen), nebo podržením klávesy CTRL a kliknutím na požadované aktivity jednu po druhé.

V Návrháři lze také přetáhnout a vyřadit více výběrů aktivit a lze je také interagovat pomocí místní nabídky.

### <a name="outline-view-of-workflow-items"></a><a name="BKMK_DocumentOutline"></a>zobrazení Osnova položek pracovního postupu

Aby bylo možné hierarchické pracovní postupy snáze procházet, jsou komponenty pracovního postupu zobrazeny v zobrazení osnovy ve stylu stromu. Zobrazení Osnova se zobrazí v zobrazení **Osnova dokumentu** . Chcete-li otevřít toto zobrazení, vyberte v horní nabídce možnost **zobrazení**, **ostatní okna**, **Osnova dokumentu**nebo stiskněte klávesovou zkratku CTRL W, U. Kliknutím na uzel v zobrazení osnovy přejdete na odpovídající aktivitu v Návrháři pracovních postupů a zobrazení osnovy se aktualizuje tak, aby se zobrazily aktivity vybrané v návrháři.

Následující snímek obrazovky dokončeného pracovního postupu z [kurzu Začínáme](getting-started-tutorial.md) ukazuje zobrazení osnovy s sekvenčním pracovním postupem.

![Snímek obrazovky se zobrazením osnovy a sekvenčním pracovním postupem v aplikaci Visual Studio.](./media/whats-new-in-wf-in-dotnet/outline-view-in-workflow-designer.jpg)

### <a name="c-expressions"></a><a name="BKMK_CSharpExpressions"></a>Výrazy jazyka C#

Před .NET Framework 4,5 se všechny výrazy v pracovních postupech daly zapisovat jenom v Visual Basic. V .NET Framework 4,5 jsou výrazy Visual Basic používány pouze pro projekty vytvořené pomocí Visual Basic. Projekty Visual C# nyní používají jazyk C# pro výrazy. K dispozici je plně funkční editor výrazů jazyka C#, který nabízí funkce, jako je například zvýrazňování gramatiky a IntelliSense. Projekty pracovního postupu C# vytvořené v předchozích verzích, které používají Visual Basic výrazy budou fungovat i nadále.

Výrazy jazyka C# jsou ověřovány v době návrhu. Chyby ve výrazech jazyka C# budou označeny červeným podtržením.

Další informace o výrazech jazyka C# naleznete v tématu [výrazy jazyka c#](csharp-expressions.md).

### <a name="more-control-of-visibility-of-shell-bar-and-header-items"></a><a name="BKMK_Visibility"></a>Větší kontrola nad viditelností položek v panelu prostředí a v záhlaví

V přehostujícím Návrháři nemusí některé standardní ovládací prvky uživatelského rozhraní mít význam pro daný pracovní postup a mohou být vypnuty. V .NET Framework 4 se toto přizpůsobení podporuje jenom na panelu prostředí v dolní části návrháře. V .NET Framework 4,5 lze upravit viditelnost položek hlaviček prostředí v horní části návrháře nastavením <xref:System.Activities.Presentation.View.DesignerView.WorkflowShellHeaderItemsVisibility%2A> příslušné <xref:System.Activities.Presentation.View.ShellHeaderItemsVisibility> hodnoty.

### <a name="auto-connect-and-auto-insert-in-flowchart-and-state-machine-workflows"></a><a name="BKMK_AutoConnect"></a>Automatické připojení a automatické vkládání v pracovních postupech vývojových diagramů a stavových počítačů

V .NET Framework 4 bylo nutné přidat připojení mezi uzly v pracovním postupu vývojového diagramu ručně. V uzlech .NET Framework 4,5 mají uzly vývojového a stavového počítače automaticky propojené body, které se zobrazí při přetažení aktivity z panelu nástrojů na plochu návrháře. Vyřazení aktivity v jednom z těchto bodů automaticky přidá aktivitu spolu s potřebným připojením.

Následující snímek obrazovky ukazuje body připojení, které se zobrazí při přetažení aktivity ze sady nástrojů.

![Počáteční uzel vývojového diagramu znázorňující body automatického připojení](./media/whats-new-in-wf-in-dotnet/auto-connect-points-start-node.png)

Aktivity lze také přetáhnout na propojení mezi uzly vývojového diagramu a stavy a automaticky tak vkládat uzel mezi dva ostatní uzly. Na následujícím snímku obrazovky vidíte zvýrazněný spojovací řádek, kde je možné aktivity přetáhnout z panelu nástrojů a vyřadit.

![Automatický vložení popisovače pro vyřazování aktivit](./media/whats-new-in-wf-in-dotnet/auto-insert-connecting-line.png)

### <a name="designer-annotations"></a><a name="BKMK_Annotations"></a>Poznámky návrháře

Aby bylo možné vyvíjet větší pracovní postupy, Návrhář nyní podporuje přidávání poznámek, které pomáhají sledovat proces návrhu. Anotace lze přidat k aktivitám, stavům, uzlům vývojového diagramu, proměnným a argumentům. Následující snímek obrazovky ukazuje místní nabídku, která se používá k přidání poznámek do návrháře.

![Snímek obrazovky znázorňující nabídku pro přidání poznámek](./media/whats-new-in-wf-in-dotnet/designer-annotations-context-menu.png)

### <a name="debugging-states"></a>Stavy ladění

V .NET Framework 4 neaktivity prvky nemohou podporovat ladicí zarážky, protože nebyly jednotkami provádění. Tato verze poskytuje mechanismus pro přidání zarážek do <xref:System.Activities.Statements.State> objektů. Je-li zarážka nastavena na <xref:System.Activities.Statements.State> , spuštění bude přerušeno, když je stav převeden na, před tím, než se naplánují jeho aktivity nebo události vstupu.

### <a name="define-and-consume-activitydelegate-objects-in-the-designer"></a><a name="BKMK_ActivityDelegates"></a>Definování a využívání objektů ActivityDelegate v Návrháři

Aktivity v .NET Framework 4 používaly <xref:System.Activities.ActivityDelegate> objekty k vystavování bodů provádění, kde jiné části pracovního postupu mohou komunikovat s prováděním pracovního postupu, ale použití těchto bodů spuštění obvykle vyžaduje spravedlivé množství kódu. V této verzi můžou vývojáři definovat a využívat delegáty aktivity pomocí návrháře pracovních postupů. Další informace naleznete v tématu [How to: Define and spotřebovávají Delegates Activity Delegates in the Návrhář postupu provádění](/visualstudio/workflow-designer/how-to-define-and-consume-activity-delegates-in-the-workflow-designer).

### <a name="build-time-validation"></a><a name="BKMK_BuildTimeValidation"></a>Ověřování při sestavení

V .NET Framework 4 se chyby ověření pracovního postupu nepočítají jako chyby sestavení během sestavování projektu pracovního postupu. To znamenalo, že sestavení projektu pracovního postupu může být úspěšné i v případě, že došlo k chybám ověření pracovního postupu. V .NET Framework 4,5 způsobí chyby ověření pracovního postupu selhání sestavení.

### <a name="design-time-background-validation"></a><a name="BKMK_DesignTimeValidation"></a>Ověřování na pozadí v době návrhu

V .NET Framework 4 byly pracovní postupy ověřeny jako proces na popředí, což by mohlo potenciálně blokovat uživatelské rozhraní během složitých nebo časově náročných ověřovacích procesů. Ověření pracovního postupu teď probíhá na vlákně na pozadí, takže uživatelské rozhraní není blokované.

### <a name="view-state-located-in-a-separate-location-in-xaml-files"></a><a name="BKMK_ViewState"></a>Zobrazit stav umístěný v samostatném umístění v souborech XAML

V .NET Framework 4 jsou informace o stavu pracovního postupu uloženy v rámci souboru XAML v mnoha různých umístěních. To je nepraktické pro vývojáře, kteří chtějí přímo číst XAML, nebo psát kód pro odebrání informací o stavu zobrazení. V .NET Framework 4,5 jsou informace o stavu zobrazení v souboru XAML serializovány jako samostatný prvek v souboru XAML. Vývojáři můžou snadno vyhledat a upravit informace o stavu aktivity nebo stav zobrazení úplně odebrat.

### <a name="expression-extensibility"></a><a name="BKMK_ExpressionExtensibility"></a>Rozšiřitelnost výrazu

V .NET Framework 4,5 poskytujeme vývojářům možnost vytvářet vlastní výrazy a prostředí pro tvorbu výrazů, které je možné zapojit do návrháře pracovních postupů.

### <a name="opt-in-for-workflow-45-features-in-rehosted-designer"></a><a name="BKMK_BackwardCompatRehostedDesigner"></a>Výslovný souhlas s funkcemi pracovního postupu 4,5 v přehostovaném návrháři

Aby se zachovala zpětná kompatibilita, některé nové funkce, které jsou součástí .NET Framework 4,5, nejsou ve výchozím nastavení v přehostujícím návrháři povolené. K tomu je potřeba zajistit, aby existující aplikace používající znovu hostujícího návrháře nebyly přerušeny aktualizací na nejnovější verzi. Chcete-li povolit nové funkce v novém hostovaném návrháři, buď nastavte <xref:System.Activities.Presentation.DesignerConfigurationService.TargetFrameworkName%2A> na ".NET Framework 4,5", nebo nastavte jednotlivé členy <xref:System.Activities.Presentation.DesignerConfigurationService> pro povolení jednotlivých funkcí.

## <a name="new-workflow-development-models"></a><a name="BKMK_NewWFModels"></a>Nové modely vývoje pracovního postupu

Kromě vývojových a sekvenčních vývojových modelů pracovních postupů tato verze zahrnuje pracovní postupy stavového počítače a služby pracovního postupu pro první kontrakt.

### <a name="state-machine-workflows"></a><a name="BKMK_StateMachine"></a>Pracovní postupy stavového stroje

Pracovní postupy stavového počítače byly představeny jako součást .NET Framework 4, verze 4.0.1 v [Microsoft .NET Framework 4 Platform Update 1](https://docs.microsoft.com/archive/blogs/endpoint/microsoft-net-framework-4-platform-update-1). Tato aktualizace obsahuje několik nových tříd a aktivit, které vývojářům umožňují vytvářet pracovní postupy stavového počítače. Tyto třídy a aktivity byly aktualizovány pro .NET Framework 4,5. Aktualizace zahrnují:

1. Možnost nastavovat zarážky na stavech

2. Možnost Kopírovat a vkládat přechody v Návrháři pracovních postupů

3. Podpora návrháře pro vytvoření přechodu na sdílené triggery

4. Aktivity, které slouží k vytváření pracovních postupů stavového počítače, včetně: <xref:System.Activities.Statements.StateMachine> , <xref:System.Activities.Statements.State> a<xref:System.Activities.Statements.Transition>

Následující snímek obrazovky ukazuje pracovní postup dokončeného stavu počítače z kroku [Začínáme kurzu](getting-started-tutorial.md) [Postup: vytvoření pracovního postupu stavového stroje](how-to-create-a-state-machine-workflow.md).

![Obrázek zobrazující pracovní postup dokončeného stavového počítače.](./media/whats-new-in-wf-in-dotnet/complete-state-machine-workflow.jpg)

Další informace o vytváření pracovních postupů stavových počítačů najdete v tématu [pracovní postupy stavového stroje](state-machine-workflows.md).

### <a name="contract-first-workflow-development"></a><a name="BKMK_ContractFirst"></a>Vývoj pracovního postupu prvního kontraktu

Nástroj pro vývoj pracovního postupu první smlouvy umožňuje vývojářům nejprve navrhnout kontrakt v kódu a pak s několika kliknutími v sadě Visual Studio automaticky vygenerovat šablonu aktivity v sadě nástrojů reprezentující jednotlivé operace. Tyto aktivity se pak použijí k vytvoření pracovního postupu, který implementuje operace definované smlouvou. Návrhář pracovního postupu ověří službu pracovního postupu, aby se zajistilo, že tyto operace budou implementované a že signatura pracovního postupu odpovídá signatuře smlouvy. Vývojář může také přidružit službu pracovního postupu ke kolekci implementovaných smluv. Další informace o vývoji služeb pracovních postupů prvního kontraktu najdete v tématu [Postupy: vytvoření služby pracovního postupu, která využívá stávající kontrakt služby](how-to-create-a-workflow-service-that-consumes-an-existing-service-contract.md).
