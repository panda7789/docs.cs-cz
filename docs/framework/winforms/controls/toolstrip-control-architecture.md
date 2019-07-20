---
title: Architektura ovládacího prvku ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: d0a1441e9bae8d2c1f938e7399c11e736708da4d
ms.sourcegitcommit: 30a83efb57c468da74e9e218de26cf88d3254597
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/20/2019
ms.locfileid: "68363822"
---
# <a name="toolstrip-control-architecture"></a>Architektura ovládacího prvku ToolStrip

Třídy <xref:System.Windows.Forms.ToolStrip> a<xref:System.Windows.Forms.ToolStripItem> poskytují flexibilní rozšiřitelný systém pro zobrazení položek panelu nástrojů, stav a nabídky. Tyto třídy jsou obsaženy v <xref:System.Windows.Forms> oboru názvů a jsou všechny obvykle pojmenovány s předponou "ToolStrip" ( <xref:System.Windows.Forms.ToolStripOverflow>například) nebo s příponou "proužek <xref:System.Windows.Forms.MenuStrip>" (například).

## <a name="toolstrip"></a>ToolStrip

Následující témata popisují <xref:System.Windows.Forms.ToolStrip> a ovládací prvky, které jsou z něho odvozené.

<xref:System.Windows.Forms.ToolStrip>je abstraktní základní třída pro <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>a <xref:System.Windows.Forms.ContextMenuStrip>. Následující objektový model znázorňuje <xref:System.Windows.Forms.ToolStrip> hierarchii dědičnosti.

![Diagram, který zobrazuje model objektu ToolStrip.](./media/toolstrip-control-architecture/toolstrip-object-model.gif)

Ke všem položkám <xref:System.Windows.Forms.ToolStrip> můžete přistupovat <xref:System.Windows.Forms.ToolStrip.Items%2A> přes kolekci. Ke všem položkám <xref:System.Windows.Forms.ToolStripDropDownItem> můžete přistupovat <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> přes kolekci. Ve třídě odvozené z <xref:System.Windows.Forms.ToolStrip>, můžete také <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> použít vlastnost pro přístup pouze k aktuálně zobrazeným položkám. Jedná se o položky, které nejsou momentálně v nabídce přetečení.

Následující položky jsou speciálně navržené pro bezproblémové fungování s oběma <xref:System.Windows.Forms.ToolStripSystemRenderer> i <xref:System.Windows.Forms.ToolStripProfessionalRenderer> ve všech orientací. Jsou k dispozici ve výchozím nastavení v době <xref:System.Windows.Forms.ToolStrip> návrhu ovládacího prvku:

- <xref:System.Windows.Forms.ToolStripButton>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="menustrip"></a>MenuStrip

<xref:System.Windows.Forms.MenuStrip>je kontejner nejvyšší úrovně, který nahrazuje <xref:System.Windows.Forms.MainMenu>. Poskytuje také funkce pro zpracování klíčů a rozhraní MDI (Multiple Document Interface). Functions <xref:System.Windows.Forms.ToolStripMenuItem> <xref:System.Windows.Forms.MenuStrip>a pracujte společně s, i když jsou odvozeny z <xref:System.Windows.Forms.ToolStripItem>. <xref:System.Windows.Forms.ToolStripDropDownItem>

Následující položky jsou speciálně navržené pro bezproblémové fungování s oběma <xref:System.Windows.Forms.ToolStripSystemRenderer> i <xref:System.Windows.Forms.ToolStripProfessionalRenderer> ve všech orientací. Jsou k dispozici ve výchozím nastavení v době <xref:System.Windows.Forms.MenuStrip> návrhu ovládacího prvku:

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="statusstrip"></a>StatusStrip

<xref:System.Windows.Forms.StatusStrip><xref:System.Windows.Forms.StatusBar> nahradí ovládací prvek. <xref:System.Windows.Forms.StatusStrip> Mezi speciální funkce patří vlastní rozložení tabulky, podpora velikosti a přesunutí formuláře `Spring` a <xref:System.Windows.Forms.ToolStripStatusLabel> vlastnost, která umožňuje automatické vyplňování dostupného místa.

Následující položky jsou speciálně navržené pro bezproblémové fungování s oběma <xref:System.Windows.Forms.ToolStripSystemRenderer> i <xref:System.Windows.Forms.ToolStripProfessionalRenderer> ve všech orientací. Jsou k dispozici ve výchozím nastavení v době <xref:System.Windows.Forms.StatusStrip> návrhu ovládacího prvku:

- <xref:System.Windows.Forms.ToolStripStatusLabel>

- <xref:System.Windows.Forms.ToolStripDropDownButton>

- <xref:System.Windows.Forms.ToolStripSplitButton>

- <xref:System.Windows.Forms.ToolStripProgressBar>

### <a name="contextmenustrip"></a>ContextMenuStrip

<xref:System.Windows.Forms.ContextMenuStrip>nahrazuje <xref:System.Windows.Forms.ContextMenu>. Můžete přidružit <xref:System.Windows.Forms.ContextMenuStrip> k libovolnému ovládacímu prvku a kliknutím pravým tlačítkem myši se automaticky zobrazí místní nabídka (nebo místní nabídka). Můžete zobrazit <xref:System.Windows.Forms.ContextMenuStrip> programově <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> pomocí metody. <xref:System.Windows.Forms.ContextMenuStrip>podporuje zrušení <xref:System.Windows.Forms.ToolStripDropDown.Opening> a <xref:System.Windows.Forms.ToolStripDropDown.Closing> události pro zpracování dynamického naplnění a scénářů s vícenásobným kliknutím. <xref:System.Windows.Forms.ContextMenuStrip>podporuje obrázky, stav kontroly nabídky, text, přístupové klávesy, zástupce a kaskádové nabídky.

Následující položky jsou speciálně navržené pro bezproblémové fungování s oběma <xref:System.Windows.Forms.ToolStripSystemRenderer> i <xref:System.Windows.Forms.ToolStripProfessionalRenderer> ve všech orientací. Jsou k dispozici ve výchozím nastavení v době <xref:System.Windows.Forms.ContextMenuStrip> návrhu ovládacího prvku:

- <xref:System.Windows.Forms.ToolStripMenuItem>

- <xref:System.Windows.Forms.ToolStripSeparator>

- <xref:System.Windows.Forms.ToolStripTextBox>

- <xref:System.Windows.Forms.ToolStripComboBox>

### <a name="toolstrip-generic-features"></a>Obecné funkce ToolStrip

Následující témata popisují funkce a chování, které jsou obecné pro <xref:System.Windows.Forms.ToolStrip> a odvozené ovládací prvky.

#### <a name="painting"></a>Vykreslování

Vlastní Malování můžete provádět v <xref:System.Windows.Forms.ToolStrip> ovládacích prvcích několika způsoby. Stejně jako <xref:System.Windows.Forms.ToolStrip> u jiných ovládacích prvků <xref:System.Windows.Forms.ToolStripItem> model Windows Forms mají i obojí přepsatelné `OnPaint` metody a `Paint` události. Stejně jako při běžném Malování je souřadnicový systém relativní vzhledem ke klientské oblasti ovládacího prvku. To znamená, že levý horní roh ovládacího prvku je 0, 0. Událost a `OnPaint` Metoda<xref:System.Windows.Forms.ToolStripItem> se chová jako jiné události Malování ovládacích prvků. `Paint`

Ovládací prvky také poskytují jemnější přístup k vykreslování položek a kontejneru <xref:System.Windows.Forms.ToolStripRenderer> skrze třídu, která má přepsatelné metody pro vykreslování pozadí, pozadí položky, obrázku položky, šipky položky, textu položky a ohraničení <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.ToolStrip>. Argumenty události pro tyto metody zveřejňují několik vlastností, jako jsou obdélníky, barvy a textové formáty, které lze upravit podle potřeby.

Chcete-li upravit pouze několik aspektů, jak je položka vykreslena, obvykle přepište <xref:System.Windows.Forms.ToolStripRenderer>.

Pokud píšete novou položku a chcete ovládat všechny aspekty vykreslování, přepište `OnPaint` metodu. V rámci `OnPaint`můžete použít metody <xref:System.Windows.Forms.ToolStripRenderer>z.

Ve výchozím nastavení <xref:System.Windows.Forms.ToolStrip> je dvojité ukládání do vyrovnávací paměti s využitím <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> tohoto nastavení.

#### <a name="parenting"></a>Nadřazené vztahy

Koncept vlastnictví kontejneru a nadřazených objektů je složitější v <xref:System.Windows.Forms.ToolStrip> ovládacích prvcích než v jiných model Windows Formsch ovládacích prvcích kontejneru. To je nezbytné pro podporu dynamických scénářů, jako je přetečení, sdílení rozevíracích položek <xref:System.Windows.Forms.ToolStrip> napříč více položkami a pro podporu generování <xref:System.Windows.Forms.ContextMenuStrip> z ovládacího prvku.

Následující seznam popisuje členy související s nadřazenou a vysvětluje jejich použití.

- <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A>přistupuje k položce, která je zdrojem rozevírací nabídky. To je podobné <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>, ale místo vrácení ovládacího prvku <xref:System.Windows.Forms.ToolStripItem>vrátí.

- <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>Určuje, který ovládací prvek je zdrojem v <xref:System.Windows.Forms.ContextMenuStrip> případě, že více ovládacích prvků <xref:System.Windows.Forms.ContextMenuStrip>sdílí stejné.

- <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A>je přístup k <xref:System.Windows.Forms.ToolStripItem.Parent%2A> vlastnosti jen pro čtení. Nadřazený objekt se liší od vlastníka v tom, že nadřazená položka označuje vrácenou aktuální <xref:System.Windows.Forms.ToolStrip> hodnotu, která je zobrazena v oblasti přetečení.

- <xref:System.Windows.Forms.ToolStripItem.Owner%2A>Vrátí kolekci <xref:System.Windows.Forms.ToolStrip> , jejíž kolekce Items obsahuje <xref:System.Windows.Forms.ToolStripItem>aktuální. Toto je nejlepší způsob, jak odkazovat <xref:System.Windows.Forms.ToolStrip.ImageList%2A> nebo jiné vlastnosti v nejvyšší úrovni <xref:System.Windows.Forms.ToolStrip> bez psaní speciálního kódu pro zpracování přetečení.

#### <a name="behavior-of-inherited-controls"></a>Chování zděděných ovládacích prvků

Následující ovládací prvky jsou uzamčeny vždy, když jsou použity v dědičnosti:

- <xref:System.Windows.Forms.ToolStrip>

- <xref:System.Windows.Forms.MenuStrip>

- <xref:System.Windows.Forms.ContextMenuStrip>

- <xref:System.Windows.Forms.StatusStrip>

- <xref:System.Windows.Forms.ToolStripPanel>který obsahuje panely v <xref:System.Windows.Forms.ToolStripContainer> a také jednotlivé <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky.

Můžete například vytvořit novou aplikaci model Windows Forms pomocí jednoho nebo více ovládacích prvků v předchozím seznamu. Nastavte modifikátor přístupu jednoho nebo více ovládacích prvků na `public` nebo `protected`a pak Sestavte projekt. Přidejte formulář, který dědí z prvního formuláře, a pak vyberte Zděděný ovládací prvek. Ovládací prvek se zobrazí jako uzamčený, chová se, jako by `private`byl jeho modifikátor přístupu.

#### <a name="toolstripcontainer-support-of-inheritance"></a>Podpora prvku ToolStripContainer pro dědičnost

<xref:System.Windows.Forms.ToolStripContainer> Ovládací prvek podporuje omezené zděděné scénáře, podobně jako v následujícím příkladu:

1. Vytvořte novou model Windows Forms aplikaci.

2. <xref:System.Windows.Forms.ToolStripContainer> Přidejte do formuláře.

3. Nastavte modifikátor <xref:System.Windows.Forms.ToolStripContainer> přístupu pro `public` nebo `protected`.

4. <xref:System.Windows.Forms.ToolStrip>Přidejte libovolnou kombinaci prvků, <xref:System.Windows.Forms.MenuStrip>a <xref:System.Windows.Forms.ContextMenuStrip> ovládací prvky do <xref:System.Windows.Forms.ToolStripPanel> oblastí <xref:System.Windows.Forms.ToolStripContainer>.

5. Sestavte projekt.

6. Přidejte formulář, který dědí z prvního formuláře.

7. Vyberte zděděné <xref:System.Windows.Forms.ToolStripContainer> na formuláři.

#### <a name="inherited-behavior-of-child-controls"></a>Zděděné chování podřízených ovládacích prvků

Po dokončení předchozích kroků dojde k následujícímu zděděnému chování:

- V návrháři se ovládací prvek zobrazí s děděnou ikonou.

- <xref:System.Windows.Forms.ToolStripPanel> Ovládací prvky jsou zamčeny. obsah nelze vybrat ani změnit jejich uspořádání.

- Můžete přidat ovládací prvky do <xref:System.Windows.Forms.ToolStripContentPanel>, přesunout ovládací prvky a nastavit je podřízenými ovládacími prvky. <xref:System.Windows.Forms.ToolStripContentPanel>

- Změny zůstanou po sestavení formuláře zachované.

  > [!NOTE]
  > Odeberte modifikátory přístupu ze všech <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků, které jsou součástí. <xref:System.Windows.Forms.ToolStripContainer> Modifikátor přístupu se <xref:System.Windows.Forms.ToolStripContainer> řídí celým ovládacím prvkem.

#### <a name="partial-trust"></a>Částečná důvěryhodnost

Omezení s v `ToolStrip`případě částečné důvěryhodnosti jsou navržena tak, aby nedocházelo k neúmyslnému zadání osobních údajů, které by mohly být používány neautorizovanými osobami nebo službami. Ochranné míry jsou následující:

- `ToolStripDropDown`ovládací prvky <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> vyžadují zobrazení položek <xref:System.Windows.Forms.ToolStripControlHost>v. To platí pro vnitřní ovládací prvky <xref:System.Windows.Forms.ToolStripTextBox>, jako jsou, <xref:System.Windows.Forms.ToolStripComboBox>a <xref:System.Windows.Forms.ToolStripProgressBar> také pro uživatelem vytvořené ovládací prvky. Pokud tento požadavek není splněn, tyto položky se nezobrazí. Není vyvolána žádná výjimka.

- Nastavení vlastnosti na `false` není povoleno a parametr <xref:System.Windows.Forms.ToolStripDropDown.Closing> události Canceled je ignorován. <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> Díky tomu není možné zadat více než jednu klávesovou zkratku, aniž by se vypnula položka rozevíracího seznamu. Pokud tento požadavek není splněn, tyto položky se nezobrazí. Není vyvolána žádná výjimka.

- Mnohé události zpracování klávesových úhozů nebudou vyvolány v případě, že dojde v kontextech <xref:System.Security.Permissions.UIPermissionWindow.AllWindows>s částečným vztahem důvěryhodnosti, nikoli.

- Přístupové klíče nejsou zpracovány, pokud <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> není uděleno.

#### <a name="usage"></a>Použití

Následující vzorce používání mají vliv na <xref:System.Windows.Forms.ToolStrip> rozložení, interakci s klávesnicí a chování koncového uživatele:

- Připojeno v<xref:System.Windows.Forms.ToolStripPanel>

  Lze změnit umístění v <xref:System.Windows.Forms.ToolStripPanel> rámci a v rámci <xref:System.Windows.Forms.ToolStripPanel>s. <xref:System.Windows.Forms.ToolStrip> `false` <xref:System.Windows.Forms.ToolStrip.Stretch%2A> <xref:System.Windows.Forms.ToolStripPanel> <xref:System.Windows.Forms.ToolStrip> Vlastnost je ignorována a pokud je vlastnost nastavena na hodnotu, velikost se rozroste jako položky jsou přidány do. `Dock` Obvykle se <xref:System.Windows.Forms.ToolStrip> neúčastní v pořadí prvků.

- Ukotven

  <xref:System.Windows.Forms.ToolStrip> Je umístěn na jedné straně kontejneru na pevné pozici a jeho velikost se zvětšuje nad celou hranou, do které je ukotveno. Obvykle se <xref:System.Windows.Forms.ToolStrip> neúčastní v pořadí prvků.

- Absolutně umístěné

  Je podobně jako jiné ovládací prvky, v tom, že je umístěna <xref:System.Windows.Forms.Control.Location%2A> vlastností, má pevnou velikost a obvykle se účastní v pořadí prvků. <xref:System.Windows.Forms.ToolStrip>

#### <a name="keyboard-interaction"></a>Interakce klávesnice

##### <a name="access-keys"></a>Přístupové klíče

V kombinaci s nebo po stisknutí klávesy ALT jsou přístupové klíče jedním ze způsobů aktivace ovládacího prvku pomocí klávesnice. <xref:System.Windows.Forms.ToolStrip>podporuje explicitní i implicitní přístupové klíče. Explicitní definice používá znak ampersandu (&) před písmenem. Implicitní definice používá algoritmus, který se pokouší najít odpovídající položku na základě pořadí znaků v dané `Text` vlastnosti.

##### <a name="shortcut-keys"></a>Klávesové zkratky

Klávesové zkratky používané při <xref:System.Windows.Forms.MenuStrip> použití kombinace <xref:System.Windows.Forms.Keys> výčtu (která není specifická pro jednotlivé objednávky) k definování klávesových zkratek. <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> Vlastnost můžete použít také k zobrazení klávesové zkratky pouze s textem, jako je například "del" místo "Delete".

##### <a name="navigation"></a>Navigace

Klávesa ALT aktivuje <xref:System.Windows.Forms.MenuStrip> odkaz, na který odkazuje <xref:System.Windows.Forms.Form.MainMenuStrip%2A>. Odtud CTRL + TAB prochází mezi <xref:System.Windows.Forms.ToolStrip> ovládacími prvky v `ToolStripPanel`s. Klávesy TAB a klávesy se šipkami na numerické klávesnici pohybují mezi položkami v <xref:System.Windows.Forms.ToolStrip>. Speciální algoritmus zpracovává navigaci v oblasti přetečení. Mezerník vybere a <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>nebo <xref:System.Windows.Forms.ToolStripSplitButton>.

##### <a name="focus-and-validation"></a>Fokus a ověření

Když je aktivována klávesou Alt, <xref:System.Windows.Forms.MenuStrip> nebo <xref:System.Windows.Forms.ToolStrip> obvykle nebere ani neodebere fokus z ovládacího prvku, který aktuálně má fokus. Pokud je ovládací prvek hostovaný v <xref:System.Windows.Forms.MenuStrip> nebo v rozevíracím seznamu <xref:System.Windows.Forms.MenuStrip>, ovládací prvek získá fokus, když uživatel stiskne klávesu TAB. Obecně platí, že <xref:System.Windows.Forms.Control.GotFocus>události <xref:System.Windows.Forms.Control.LostFocus> <xref:System.Windows.Forms.Control.Enter> ,,<xref:System.Windows.Forms.Control.Leave> a nemusíbýtvyvolány,kdyžjsouaktivoványklávesnicí.<xref:System.Windows.Forms.MenuStrip> V takových případech použijte <xref:System.Windows.Forms.MenuStrip.MenuActivate> místo toho události a. <xref:System.Windows.Forms.MenuStrip.MenuDeactivate>

Ve výchozím nastavení <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> je `false`. Pro <xref:System.Windows.Forms.ContainerControl.Validate%2A> ověření proveďte explicitní volání na formuláři.

#### <a name="layout"></a>Rozložení

Rozložení můžete <xref:System.Windows.Forms.ToolStrip> řídit výběrem jednoho z <xref:System.Windows.Forms.ToolStripLayoutStyle> členů s <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> vlastností.

##### <a name="stack-layouts"></a>Rozložení zásobníku

Skládání je uspořádání položek vedle sebe na obou koncích <xref:System.Windows.Forms.ToolStrip>. Následující seznam popisuje rozložení zásobníku.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow>je výchozí hodnota. Toto nastavení způsobí, <xref:System.Windows.Forms.ToolStrip> že změní rozložení automaticky v souladu <xref:System.Windows.Forms.ToolStrip.Orientation%2A> s vlastností pro zpracování scénářů přetahování a ukotvení.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow><xref:System.Windows.Forms.ToolStrip> vykresluje položky vedle sebe svisle.

- <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow><xref:System.Windows.Forms.ToolStrip> vykresluje položky vedle sebe vodorovně.

##### <a name="other-features-of-stack-layouts"></a>Další funkce rozložení zásobníku

<xref:System.Windows.Forms.ToolStripItem.Alignment%2A>určuje konec, <xref:System.Windows.Forms.ToolStrip> na který je položka zarovnána.

Pokud se položky nevejdou <xref:System.Windows.Forms.ToolStrip>do, zobrazí se automaticky tlačítko přetečení. Nastavení <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> vlastnosti určuje, zda se položka v oblasti přetečení zobrazuje vždy, podle potřeby, nebo nikdy.

V případě potřeby můžete <xref:System.Windows.Forms.ToolStripItem.Placement%2A> zkontrolovat vlastnost a určit, zda byla položka umístěna na hlavní <xref:System.Windows.Forms.ToolStrip>, přetečení <xref:System.Windows.Forms.ToolStrip>, nebo pokud není aktuálně zobrazena vůbec. <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> Typickými důvody, proč se položka nezobrazuje, je, že se položka nevešla do <xref:System.Windows.Forms.ToolStrip> hlavní a <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> její vlastnost byla nastavena <xref:System.Windows.Forms.ToolStripItemOverflow.Never>na.

Vytvořte objekt <xref:System.Windows.Forms.ToolStrip> movitého tak, že ho <xref:System.Windows.Forms.ToolStripPanel> umístíte do a <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> nastavíte na <xref:System.Windows.Forms.ToolStripGripStyle.Visible>.

##### <a name="other-layout-options"></a>Další možnosti rozložení

Další možnosti rozložení jsou <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> a. <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>

##### <a name="flow-layout"></a>Plovoucí rozložení

<xref:System.Windows.Forms.ToolStripLayoutStyle.Flow>rozložení je výchozím nastavením pro <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>a <xref:System.Windows.Forms.ToolStripOverflow>. Je podobný <xref:System.Windows.Forms.FlowLayoutPanel>. Funkce <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> rozložení jsou následující:

- Všechny funkce <xref:System.Windows.Forms.FlowLayoutPanel> nástroje jsou zpřístupněny <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> vlastností. Je nutné přetypovat <xref:System.Windows.Forms.LayoutSettings> třídu <xref:System.Windows.Forms.FlowLayoutSettings> na třídu.

- Pomocí <xref:System.Windows.Forms.ToolStripItem.Dock%2A> vlastností a <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> v kódu můžete zarovnat položky v rámci řádku.

- <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Vlastnost je ignorována.

- V takovém případě můžete <xref:System.Windows.Forms.ToolStripItem.Placement%2A> vlastnost zkontrolovat a zjistit, zda byla položka umístěna do hlavního <xref:System.Windows.Forms.ToolStrip> nebo nevyhovující. <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>

- Úchyt není vykreslen, a proto <xref:System.Windows.Forms.ToolStrip> nelze přesunout ve <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> stylu rozložení v rámci <xref:System.Windows.Forms.ToolStripPanel> .

- Tlačítko přetečení není vykresleno a <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> je ignorováno. <xref:System.Windows.Forms.ToolStrip>

##### <a name="table-layout"></a>Rozložení tabulky

<xref:System.Windows.Forms.ToolStripLayoutStyle.Table>pro <xref:System.Windows.Forms.StatusStrip>je výchozí rozložení. Je podobný <xref:System.Windows.Forms.TableLayoutPanel>. Funkce <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> rozložení jsou následující:

- Všechny funkce <xref:System.Windows.Forms.TableLayoutPanel> nástroje jsou zpřístupněny <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> vlastností. Je nutné přetypovat <xref:System.Windows.Forms.LayoutSettings> třídu <xref:System.Windows.Forms.TableLayoutSettings> na třídu.

- Pomocí <xref:System.Windows.Forms.ToolStripItem.Dock%2A> vlastností a <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> v kódu lze zarovnat položky v rámci buňky tabulky.

- <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Vlastnost je ignorována.

- V takovém případě můžete <xref:System.Windows.Forms.ToolStripItem.Placement%2A> vlastnost zkontrolovat a zjistit, zda byla položka umístěna do hlavního <xref:System.Windows.Forms.ToolStrip> nebo nevyhovující. <xref:System.Windows.Forms.ToolStrip.LayoutCompleted>

- Úchyt není vykreslen, a proto <xref:System.Windows.Forms.ToolStrip> nelze přesunout ve <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> stylu rozložení v rámci <xref:System.Windows.Forms.ToolStripPanel> .

- Tlačítko přetečení není vykresleno a <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> je ignorováno. <xref:System.Windows.Forms.ToolStrip>

## <a name="toolstripitem"></a>ToolStripItem

Následující témata popisují <xref:System.Windows.Forms.ToolStripItem> a ovládací prvky, které jsou z něho odvozené.

<xref:System.Windows.Forms.ToolStripItem>je abstraktní základní třída pro všechny položky, které <xref:System.Windows.Forms.ToolStrip>se nacházejí v. Následující objektový model znázorňuje <xref:System.Windows.Forms.ToolStripItem> hierarchii dědičnosti.

![Diagram, který zobrazuje model objektu ToolStripItem](./media/toolstrip-control-architecture/toolstripitem-object-model.gif)

<xref:System.Windows.Forms.ToolStripItem>třídy <xref:System.Windows.Forms.ToolStripItem>dědí přímo z, nebo dědí nepřímo z <xref:System.Windows.Forms.ToolStripItem> prostřednictvím <xref:System.Windows.Forms.ToolStripControlHost> nebo <xref:System.Windows.Forms.ToolStripDropDownItem>.

<xref:System.Windows.Forms.ToolStripItem>ovládací prvky musí být obsaženy v <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>nebo <xref:System.Windows.Forms.ContextMenuStrip> a nelze je přidat přímo do formuláře. Různé třídy kontejneru jsou navrženy tak, aby obsahovaly vhodnou podmnožinu <xref:System.Windows.Forms.ToolStripItem> ovládacích prvků.

V následující tabulce jsou uvedeny burzovní <xref:System.Windows.Forms.ToolStripItem> ovládací prvky a kontejnery, ve kterých vypadají nejlépe. I když <xref:System.Windows.Forms.ToolStrip> může být libovolná položka hostována v jakémkoli <xref:System.Windows.Forms.ToolStrip>kontejneru odvozeném, byly tyto položky navrženy tak, aby vypadaly nejlépe v následujících kontejnerech:

> [!NOTE]
> <xref:System.Windows.Forms.ToolStripDropDown>se nezobrazí v sadě nástrojů návrháře.

|Obsažená položka|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|
|--------------------|---------------|---------------|----------------------|-----------------|-----------------------|
|<xref:System.Windows.Forms.ToolStripButton>|Ano|Ne|Ne|Ne|Ano|
|<xref:System.Windows.Forms.ToolStripComboBox>|Ano|Ano|Ano|Ne|Ano|
|<xref:System.Windows.Forms.ToolStripSplitButton>|Ano|Ne|Ne|Ano|Ano|
|<xref:System.Windows.Forms.ToolStripLabel>|Ano|Ne|Ne|Ano|Ano|
|<xref:System.Windows.Forms.ToolStripSeparator>|Ano|Ano|Ano|Ne|Ano|
|<xref:System.Windows.Forms.ToolStripDropDownButton>|Ano|Ne|Ne|Ano|Ano|
|<xref:System.Windows.Forms.ToolStripTextBox>|Ano|Ano|Ano|Ne|Ano|
|<xref:System.Windows.Forms.ToolStripMenuItem>|Ne|Ano|Ano|Ne|Ne|
|<xref:System.Windows.Forms.ToolStripStatusLabel>|Ne|Ne|Ne|Ano|Ne|
|<xref:System.Windows.Forms.ToolStripProgressBar>|Ano|Ne|Ne|Ano|Ne|
|<xref:System.Windows.Forms.ToolStripControlHost>|Ano|Ano|Ne|Ano|Ano|

### <a name="toolstripbutton"></a>Prvek ToolStripButton

<xref:System.Windows.Forms.ToolStripButton>je položka tlačítka pro <xref:System.Windows.Forms.ToolStrip>. Můžete ji zobrazit s různými styly ohraničení a můžete ji použít k reprezentaci a aktivaci provozních stavů. Můžete ho také definovat tak, aby ve výchozím nastavení byl fokus.

### <a name="toolstriplabel"></a>ToolStripLabel

Poskytuje funkce popisku v <xref:System.Windows.Forms.ToolStrip> ovládacích prvcích. <xref:System.Windows.Forms.ToolStripLabel> <xref:System.Windows.Forms.ToolStripLabel> Je podobnýjako,kterývevýchozímnastavenínezískáfokusakterýsenevykreslíjakonabízený<xref:System.Windows.Forms.ToolStripButton> nebo zvýrazněný.

<xref:System.Windows.Forms.ToolStripLabel>jako hostovaná položka podporuje přístupové klíče.

<xref:System.Windows.Forms.LinkLabel.LinkColor%2A>Použijte vlastnosti, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>a <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> vpřípadě<xref:System.Windows.Forms.ToolStripLabel> pro podporu ovládacího prvku odkazu v. <xref:System.Windows.Forms.ToolStrip>

### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel

<xref:System.Windows.Forms.ToolStripStatusLabel>je verze <xref:System.Windows.Forms.ToolStripLabel> navržená speciálně pro použití v <xref:System.Windows.Forms.StatusStrip>. Mezi speciální funkce patří <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>a <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.

### <a name="toolstripseparator"></a>ToolStripSeparator

<xref:System.Windows.Forms.ToolStripSeparator> Přidá svislou nebo vodorovnou čáru na panel nástrojů nebo nabídku v závislosti na orientaci. Poskytuje seskupení nebo rozlišení mezi položkami, jako jsou ty v nabídce.

Můžete přidat v době <xref:System.Windows.Forms.ToolStripSeparator> návrhu, a to výběrem z rozevíracího seznamu. Můžete však také automaticky vytvořit <xref:System.Windows.Forms.ToolStripSeparator> zadáním spojovníku (-) buď v uzlu šablony návrháře, nebo <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> v metodě.

### <a name="toolstripcontrolhost"></a>ToolStripControlHost

<xref:System.Windows.Forms.ToolStripControlHost>je abstraktní základní třída pro <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>a <xref:System.Windows.Forms.ToolStripProgressBar>. <xref:System.Windows.Forms.ToolStripControlHost>může hostovat jiné ovládací prvky, včetně vlastních ovládacích prvků, dvěma způsoby:

- Vytvořte třídu, která je odvozena z <xref:System.Windows.Forms.Control>. <xref:System.Windows.Forms.ToolStripControlHost> Chcete-li mít úplný přístup k hostovanému řízení a vlastnostem <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> , je nutné přetypovat vlastnost zpět na skutečnou třídu, kterou představuje.

- Rozšiřuje <xref:System.Windows.Forms.ToolStripControlHost>a v konstruktoru bez parametrů zděděné třídy volejte konstruktor základní třídy, který předává třídu, která je odvozena z <xref:System.Windows.Forms.Control>. Tato možnost umožňuje zabalit společné metody a vlastnosti ovládacích prvků pro snadný přístup <xref:System.Windows.Forms.ToolStrip>v.

### <a name="toolstripcombobox"></a>ToolStripComboBox

<xref:System.Windows.Forms.ToolStripComboBox>je optimalizován pro hostování <xref:System.Windows.Forms.ToolStrip>v. <xref:System.Windows.Forms.ComboBox> Podmnožina vlastností a událostí hostovaného ovládacího prvku je vystavena na <xref:System.Windows.Forms.ToolStripComboBox> úrovni, ale podkladový <xref:System.Windows.Forms.ComboBox> ovládací prvek <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> je plně přístupný prostřednictvím vlastnosti.

### <a name="toolstriptextbox"></a>ToolStripTextBox

<xref:System.Windows.Forms.ToolStripTextBox>je optimalizován pro hostování <xref:System.Windows.Forms.ToolStrip>v. <xref:System.Windows.Forms.TextBox> Podmnožina vlastností a událostí hostovaného ovládacího prvku je vystavena na <xref:System.Windows.Forms.ToolStripTextBox> úrovni, ale podkladový <xref:System.Windows.Forms.TextBox> ovládací prvek <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> je plně přístupný prostřednictvím vlastnosti.

### <a name="toolstripprogressbar"></a>ToolStripProgressBar

<xref:System.Windows.Forms.ToolStripProgressBar>je optimalizován pro hostování <xref:System.Windows.Forms.ToolStrip>v. <xref:System.Windows.Forms.ProgressBar> Podmnožina vlastností a událostí hostovaného ovládacího prvku je vystavena na <xref:System.Windows.Forms.ToolStripProgressBar> úrovni, ale podkladový <xref:System.Windows.Forms.ProgressBar> ovládací prvek <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> je plně přístupný prostřednictvím vlastnosti.

### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem

<xref:System.Windows.Forms.ToolStripDropDownItem>je abstraktní základní třída pro <xref:System.Windows.Forms.ToolStripMenuItem>, <xref:System.Windows.Forms.ToolStripDropDownButton>, a <xref:System.Windows.Forms.ToolStripSplitButton>, která může hostovat položky přímo nebo hostovat další položky v rozevíracím kontejneru. To provedete nastavením <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> vlastnosti <xref:System.Windows.Forms.ToolStripDropDown> na a a <xref:System.Windows.Forms.ToolStripDropDown>nastavením <xref:System.Windows.Forms.ToolStrip.Items%2A> vlastnosti. Přístup k těmto rozevíracím položkám přímo prostřednictvím <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> vlastnosti.

### <a name="toolstripmenuitem"></a>ToolStripMenuItem

<xref:System.Windows.Forms.ToolStripMenuItem>je a <xref:System.Windows.Forms.ToolStripDropDownMenu> <xref:System.Windows.Forms.ContextMenuStrip> , který pracuje s a pro zpracování speciálního zvýraznění, rozložení a uspořádání sloupců pro nabídky. <xref:System.Windows.Forms.ToolStripDropDownItem>

### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton

<xref:System.Windows.Forms.ToolStripDropDownButton>Vypadá to <xref:System.Windows.Forms.ToolStripButton>, že se zobrazí rozevírací oblast, když na ni uživatel klikne. Umožňuje skrýt nebo zobrazit šipku rozevíracího seznamu nastavením <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> vlastnosti. <xref:System.Windows.Forms.ToolStripDropDownButton><xref:System.Windows.Forms.ToolStrip>hostitelé <xref:System.Windows.Forms.ToolStripOverflowButton> , který zobrazuje položky přetečení.

### <a name="toolstripsplitbutton"></a>ToolStripSplitButton

<xref:System.Windows.Forms.ToolStripSplitButton>kombinuje funkce tlačítek a tlačítek rozevíracího seznamu.

Použijte vlastnost k <xref:System.Windows.Forms.Control.Click> synchronizaci události zvolené rozevírací nabídky s položkou zobrazenou na tlačítku. <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A>

### <a name="toolstripitem-generic-features"></a>Obecné funkce ToolStripItem

<xref:System.Windows.Forms.ToolStripItem>poskytuje následující obecné funkce a možnosti pro dědění ovládacích prvků:

- Základní události

- Zpracování obrázků

- Zarovnání

- Vztah textu a obrázku

- Zobrazit styl

#### <a name="core-events"></a>Základní události

<xref:System.Windows.Forms.ToolStripItem>ovládací prvky přijímají vlastní události kliknutí, myši a malování a mohou také provádět některé předzpracování klávesnice.

#### <a name="image-handling"></a>Zpracování obrázků

<xref:System.Windows.Forms.ToolStripItem.Image%2A>Vlastnosti, <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>, ,<xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A> ase<xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> vztahují k různým aspektům zpracování obrázku. <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A> Použijte obrázky v <xref:System.Windows.Forms.ToolStrip> ovládacích prvcích nastavením těchto vlastností přímo nebo nastavením vlastnosti pouze <xref:System.Windows.Forms.ToolStrip.ImageList%2A> run-time.

Měřítko obrázku je určeno interakcí vlastností v obou <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.ToolStripItem>, jak je znázorněno níže:

- <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A>je měřítko finálního obrázku, který je určen kombinací <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> nastavení obrázku a <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> nastavení kontejneru.

  - Pokud <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> <xref:System.Windows.Forms.ToolStripItemImageScaling> je `true` (výchozí) a není <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>k dispozici žádné škálování obrázku a <xref:System.Windows.Forms.ToolStrip> velikost největší položky nebo předepsané minimální velikosti.

  - Pokud <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> je `false` a není<xref:System.Windows.Forms.ToolStripItemImageScaling> <xref:System.Windows.Forms.ToolStrip> , nedojde k žádnému obrázku ani škálování. <xref:System.Windows.Forms.ToolStripItemImageScaling.None>

#### <a name="alignment"></a>Zarovnání

Hodnota <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> vlastnosti určuje konec, <xref:System.Windows.Forms.ToolStrip> ve kterém se položka zobrazuje. Vlastnost funguje pouze v případě, že styl <xref:System.Windows.Forms.ToolStrip> rozložení je nastaven na jednu z hodnot přetečení zásobníku. <xref:System.Windows.Forms.ToolStripItem.Alignment%2A>

Položky jsou umístěny <xref:System.Windows.Forms.ToolStrip> v pořadí, ve kterém se položky zobrazí v kolekci Items (položky). Chcete-li programově změnit umístění položky, použijte <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> metodu pro přesunutí položky v kolekci. Tato metoda přesune položku, ale neduplikuje ji.

#### <a name="text-and-image-relationship"></a>Vztah textu a obrázku

Vlastnost definuje relativní umístění obrázku s ohledem na text <xref:System.Windows.Forms.ToolStripItem>na. <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> Položky, které neobsahují obrázek, text nebo obojí, se považují za zvláštní případy <xref:System.Windows.Forms.ToolStripItem> , takže se nezobrazí prázdné místo pro chybějící prvky nebo elementy.

#### <a name="display-style"></a>Zobrazit styl

<xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A>umožňuje nastavit hodnoty vlastností textu a obrázku položky při zobrazení pouze těch, které chcete. Obvykle se používá ke změně stylu zobrazení pouze při zobrazení stejné položky v jiném kontextu.

## <a name="accessory-classes"></a>Třídy příslušenství

Mezi třídy, které poskytují různé další funkce, patří:

- <xref:System.Windows.Forms.ToolStripManager>podporuje <xref:System.Windows.Forms.ToolStrip>úlohy pro celé aplikace, jako je například sloučení, nastavení a možnosti zobrazovací jednotky.

- <xref:System.Windows.Forms.ToolStripRenderer>umožňuje <xref:System.Windows.Forms.ToolStrip> snadno aplikovat konkrétní styl nebo motiv.

- <xref:System.Windows.Forms.ToolStripProfessionalRenderer>Vytvoří pera a štětce založené na nahraditelných barevných tabulkách (<xref:System.Windows.Forms.ProfessionalColorTable>).

- <xref:System.Windows.Forms.ToolStripSystemRenderer>aplikuje systémové barvy a plochý vizuální styl <xref:System.Windows.Forms.ToolStrip> na aplikace.

- <xref:System.Windows.Forms.ToolStripContainer>je podobný <xref:System.Windows.Forms.SplitContainer>. K vytvoření typického uspořádání používá čtyři ukotvené postranní <xref:System.Windows.Forms.ToolStripPanel>panely (instance) a jeden centrální panel ( <xref:System.Windows.Forms.ToolStripContentPanel>instance). Boční panely nemůžete odebrat, ale můžete je skrýt. Centrální panel není možné odebrat ani skrýt. Jeden nebo více <xref:System.Windows.Forms.ToolStrip> <xref:System.Windows.Forms.MenuStrip> ovládacíchprvkůlzeuspořádatdobočníchpanelůamůžetepoužítcentrálnípanelprojinéovládacíprvky.<xref:System.Windows.Forms.StatusStrip> Poskytuje <xref:System.Windows.Forms.ToolStripContentPanel> také způsob, jak získat podporu pro vykreslování do těla formuláře pro zajištění konzistentního vzhledu. <xref:System.Windows.Forms.ToolStripContainer>nepodporuje rozhraní MDI (Multiple Document Interface).

- <xref:System.Windows.Forms.ToolStripPanel>poskytuje prostor pro přesun a uspořádání <xref:System.Windows.Forms.ToolStrip> ovládacích prvků. Pokud si zvolíte možnost a <xref:System.Windows.Forms.ToolStripPanel> funguje dobře ve scénářích MDI, můžete použít pouze jeden panel.

## <a name="see-also"></a>Viz také:

- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Shrnutí technologie ToolStrip](toolstrip-technology-summary.md)
- [Ovládací prvek ToolStrip](toolstrip-control-windows-forms.md)
- [Ovládací prvek MenuStrip](menustrip-control-windows-forms.md)
- [Ovládací prvek StatusStrip](statusstrip-control.md)
- [Ovládací prvek ContextMenuStrip](contextmenustrip-control.md)
- [Ovládací prvek BindingNavigator](bindingnavigator-control-windows-forms.md)
