---
title: Architektura ovládacího prvku ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: fd00fff6c745f5f7991c038dec305b5d45761656
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="toolstrip-control-architecture"></a>Architektura ovládacího prvku ToolStrip
<xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.ToolStripItem> třídy poskytují flexibilní a rozšiřitelný systém pro zobrazení položek panelu nástrojů, stavu a nabídky. Tyto třídy jsou obsaženy v <xref:System.Windows.Forms> obor názvů a že jsou všechny obvykle s názvem s předponou "ToolStrip" (například <xref:System.Windows.Forms.ToolStripOverflow>) nebo s příponou "Pruhu" (například <xref:System.Windows.Forms.MenuStrip>).  
  
## <a name="toolstrip"></a>ToolStrip  
 Následující témata popisují <xref:System.Windows.Forms.ToolStrip> a ovládací prvky, které jsou odvozeny od ho.  
  
 <xref:System.Windows.Forms.ToolStrip> je abstraktní základní třída pro <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, a <xref:System.Windows.Forms.ContextMenuStrip>. Tento objekt modelu ukazuje <xref:System.Windows.Forms.ToolStrip> hierarchie dědičnosti.  
  
 ![ToolStrip – objektový Model](../../../../docs/framework/winforms/controls/media/toolstripobjectmodel.gif "ToolStripObjectModel")  
ToolStrip – objektový model  
  
 Dostanete všechny položky v <xref:System.Windows.Forms.ToolStrip> prostřednictvím <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekce. Dostanete všechny položky v <xref:System.Windows.Forms.ToolStripDropDownItem> prostřednictvím <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> kolekce. V třídy odvozené od <xref:System.Windows.Forms.ToolStrip>, můžete použít také <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> vlastnost, která má přístup jen ty položky, které jsou aktuálně zobrazeny. Toto jsou položky, které nejsou aktuálně nabídky přetečení.  
  
 Následující položky jsou navrženy speciálně bezproblémově pracovat s oběma <xref:System.Windows.Forms.ToolStripSystemRenderer> a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> v všechny orientace. Jsou k dispozici ve výchozím nastavení v době návrhu pro <xref:System.Windows.Forms.ToolStrip> ovládacího prvku:  
  
-   <xref:System.Windows.Forms.ToolStripButton>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="menustrip"></a>MenuStrip  
 <xref:System.Windows.Forms.MenuStrip> je kontejner nejvyšší úrovně, která nahrazuje <xref:System.Windows.Forms.MainMenu>. Poskytuje také klíče zpracování a více dokumentů funkcí rozhraní (MDI). Funkčně <xref:System.Windows.Forms.ToolStripDropDownItem> a <xref:System.Windows.Forms.ToolStripMenuItem> pracovní spolu s <xref:System.Windows.Forms.MenuStrip>, i když jsou odvozeny od <xref:System.Windows.Forms.ToolStripItem>.  
  
 Následující položky jsou navrženy speciálně bezproblémově pracovat s oběma <xref:System.Windows.Forms.ToolStripSystemRenderer> a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> v všechny orientace. Jsou k dispozici ve výchozím nastavení v době návrhu pro <xref:System.Windows.Forms.MenuStrip> ovládacího prvku:  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="statusstrip"></a>StatusStrip  
 <xref:System.Windows.Forms.StatusStrip> nahradí <xref:System.Windows.Forms.StatusBar> ovládacího prvku. Speciální funkce <xref:System.Windows.Forms.StatusStrip> zahrnout vlastní tabulky rozložení, podporu pro formulář pro změnu velikosti a přesunutí grips a `Spring` vlastností, která umožňuje <xref:System.Windows.Forms.ToolStripStatusLabel> k vyplnění dostupné místo automaticky.  
  
 Následující položky jsou navrženy speciálně bezproblémově pracovat s oběma <xref:System.Windows.Forms.ToolStripSystemRenderer> a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> v všechny orientace. Jsou k dispozici ve výchozím nastavení v době návrhu pro <xref:System.Windows.Forms.StatusStrip> ovládacího prvku:  
  
-   <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### <a name="contextmenustrip"></a>ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenuStrip> nahradí <xref:System.Windows.Forms.ContextMenu>. Můžete přidružit <xref:System.Windows.Forms.ContextMenuStrip> s libovolný ovládací prvek a pravého tlačítka myši klikněte na tlačítko se automaticky zobrazí kontextové nabídky (nebo místní nabídky). Můžete zobrazit <xref:System.Windows.Forms.ContextMenuStrip> programově pomocí <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> metoda. <xref:System.Windows.Forms.ContextMenuStrip> podporuje možné zrušit <xref:System.Windows.Forms.ToolStripDropDown.Opening> a <xref:System.Windows.Forms.ToolStripDropDown.Closing> události pro zpracování více klávesou scénáře a dynamické naplnění. <xref:System.Windows.Forms.ContextMenuStrip> podporuje bitové kopie, zkontrolujte stav položky nabídky, text, přístupové klíče, zástupce a kaskádových nabídky.  
  
 Následující položky jsou navrženy speciálně bezproblémově pracovat s oběma <xref:System.Windows.Forms.ToolStripSystemRenderer> a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> v všechny orientace. Jsou k dispozici ve výchozím nastavení v době návrhu pro <xref:System.Windows.Forms.ContextMenuStrip> ovládacího prvku:  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="toolstrip-generic-features"></a>ToolStrip – obecné funkce  
 Následující témata popisují funkce a chování, které jsou obecné na <xref:System.Windows.Forms.ToolStrip> a odvozené ovládací prvky.  
  
#### <a name="painting"></a>Malování  
 Můžete provést vlastní Malování <xref:System.Windows.Forms.ToolStrip> ovládacích prvků v několika způsoby. Stejně jako u jiných ovládacích prvků Windows Forms <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.ToolStripItem> mají přepisovatelné `OnPaint` metody a `Paint` události. Stejně jako u regulární Malování souřadnicový systém je relativní vzhledem k klientské oblasti ovládacího prvku; levém horním rohu ovládacího prvku je 0, 0. `Paint` Událostí a `OnPaint` metodu <xref:System.Windows.Forms.ToolStripItem> chovají jako ostatní události Malování ovládacího prvku.  
  
 <xref:System.Windows.Forms.ToolStrip> Ovládací prvky také poskytují lepší přístup k vykreslování položky a kontejneru, přistoupit přes <xref:System.Windows.Forms.ToolStripRenderer> třídy, která má přepisovatelné metody pro vykreslování pozadí, pozadí položky, obrázek položky, položka šipku, text položky a ohraničení <xref:System.Windows.Forms.ToolStrip>. Argumenty událostí pro tyto metody vystavit několik vlastností, jako je například obdélníků, barvy a textových formátů, které můžete upravit podle potřeby.  
  
 Chcete-li upravit pouze několik aspektů jak vykresluje položky, je obvykle přepsat <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Pokud jsou psaní novou položku a chcete spravovat všechny aspekty Malování, mají přednost před `OnPaint` metoda. V nástroji `OnPaint`, můžete použít metody z <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Ve výchozím nastavení <xref:System.Windows.Forms.ToolStrip> je dvojité vyrovnávací paměti, využívat výhod <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> nastavení.  
  
#### <a name="parenting"></a>Správa nadřazených  
 Základní informace o kontejneru vlastnictví a vztahy k nadřazeným položkám je složitější v <xref:System.Windows.Forms.ToolStrip> ovládacích prvků než do jiných ovládacích prvků Windows Forms kontejneru. Které je nezbytné pro podporu dynamické scénáře, jako je přetečení, sdílení rozevíracího seznamu položek napříč více <xref:System.Windows.Forms.ToolStrip> položky a k podpoře generování <xref:System.Windows.Forms.ContextMenuStrip> z ovládacího prvku.  
  
 Následující seznam popisuje členy související s vztahy k nadřazeným položkám a vysvětluje jejich použití.  
  
-   <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A> přístup k položce, který je zdrojem položky rozevíracího seznamu. Toto je podobná <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>, ale místo vrácení ovládacího prvku, vrátí <xref:System.Windows.Forms.ToolStripItem>.  
  
-   <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A> Určuje, který ovládací prvek je zdrojem z <xref:System.Windows.Forms.ContextMenuStrip> při více ovládacích prvků sdílet stejný <xref:System.Windows.Forms.ContextMenuStrip>.  
  
-   <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A> je jen pro čtení přistupující objekt k <xref:System.Windows.Forms.ToolStripItem.Parent%2A> vlastnost. Nadřazený se liší od vlastníka, v tom, že nadřazený označuje vrácený aktuální <xref:System.Windows.Forms.ToolStrip> ve kterém bude zobrazena, což může být v oblasti přetečení.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Owner%2A> Vrátí <xref:System.Windows.Forms.ToolStrip> jejichž položky kolekce obsahuje aktuální <xref:System.Windows.Forms.ToolStripItem>. Toto je nejlepší způsob, jak odkazovat na <xref:System.Windows.Forms.ToolStrip.ImageList%2A> nebo dalších vlastností v nejvyšší úrovně <xref:System.Windows.Forms.ToolStrip> bez nutnosti psaní kódu speciální zpracování přetečení.  
  
#### <a name="behavior-of-inherited-controls"></a>Chování zděděné ovládacích prvků  
 Ovládací prvky jsou zamčené vždy, když jsou použity v dědičnosti:  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.ToolStripPanel> panely v, který obsahuje <xref:System.Windows.Forms.ToolStripContainer> a také jednotlivé <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky.  
  
 Můžete například vytvořte novou aplikaci Windows Forms pomocí jednoho nebo více ovládacích prvků v předchozím seznamu. Nastavit – modifikátor přístupu jeden nebo více ovládacích prvků, aby `public` nebo `protected`a potom sestavte projekt. Přidejte formulář, který dědí z první formulář a potom vyberte zděděné ovládací prvek. Ovládací prvek se zobrazuje uzamčení, chovají, jako kdyby byla jeho – modifikátor přístupu `private`.  
  
#### <a name="toolstripcontainer-support-of-inheritance"></a>Podpora ToolStripContainer dědičnosti  
 <xref:System.Windows.Forms.ToolStripContainer> Řízení podporuje omezenou zděděné scénáře, podobně jako v následujícím příkladu:  
  
1.  Vytvořte novou aplikaci Windows Forms.  
  
2.  Přidat <xref:System.Windows.Forms.ToolStripContainer> do formuláře.  
  
3.  Nastavit modifikátor přístupu <xref:System.Windows.Forms.ToolStripContainer> k `public` nebo `protected`.  
  
4.  Přidat libovolnou kombinaci <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, a <xref:System.Windows.Forms.ContextMenuStrip> prvky <xref:System.Windows.Forms.ToolStripPanel> oblasti <xref:System.Windows.Forms.ToolStripContainer>.  
  
5.  Sestavte projekt.  
  
6.  Přidáte formulář, který dědí z první formulář.  
  
7.  Vyberte zděděné <xref:System.Windows.Forms.ToolStripContainer> na formuláři.  
  
#### <a name="inherited-behavior-of-child-controls"></a>Zděděné chování podřízených ovládacích prvků  
 Po dokončení předchozích kroků, očekávejte toto chování zděděné:  
  
-   Ovládací prvek zobrazí v návrháři se zděděné ikonou.  
  
-   <xref:System.Windows.Forms.ToolStripPanel> Ovládací prvky jsou zamčené; nelze vybrat nebo změna uspořádání jejich obsah.  
  
-   Můžete přidat ovládací prvky <xref:System.Windows.Forms.ToolStripContentPanel>, přesuňte ovládací prvky a proveďte je podřízených ovládacích prvků <xref:System.Windows.Forms.ToolStripContentPanel>.  
  
-   Zachová tak změny po sestavení formuláře.  
  
    > [!NOTE]
    >  Modifikátory přístupu odebrat ze všech <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky, které jsou součástí <xref:System.Windows.Forms.ToolStripContainer>. Modifikátor přístupu <xref:System.Windows.Forms.ToolStripContainer> řídí celý ovládací prvek.  
  
#### <a name="partial-trust"></a>Částečná důvěryhodnost  
 Omezení `ToolStrip`s v částečné důvěryhodnosti jsou navržené tak, aby se zabránilo nechtěnému položku osobní informace, které by mohly používat neoprávněné osoby nebo služby. Ochranná opatření, která jsou následující:  
  
-   `ToolStripDropDown` ovládací prvky vyžadují <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> zobrazíte položky ve <xref:System.Windows.Forms.ToolStripControlHost>. To platí pro obě vnitřní ovládací prvky, jako <xref:System.Windows.Forms.ToolStripTextBox>, <xref:System.Windows.Forms.ToolStripComboBox>, a <xref:System.Windows.Forms.ToolStripProgressBar> jako dobře, uživatelem vytvořené prvky. Pokud není tento požadavek splnit, tyto položky se nezobrazují. Nedojde k výjimce.  
  
-   Nastavení <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> vlastnost `false` není povolena a možné zrušit <xref:System.Windows.Forms.ToolStripDropDown.Closing> parametr událostí je ignorován. Díky tomu je možné zadat více než jedním stisknutím klávesy bez pracovní položka rozevíracího seznamu. Pokud není tento požadavek splnit, tyto položky se nezobrazují. Nedojde k výjimce.  
  
-   Mnoho klávesu zpracování událostí nebude vyvolá, když se vyskytují v částečné důvěryhodnosti kontexty jiné než <xref:System.Security.Permissions.UIPermissionWindow.AllWindows>.  
  
-   Přístupové klávesy nejsou zpracovány při <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> nebylo uděleno oprávnění.  
  
#### <a name="usage"></a>Použití  
 Následující vzorce používání mají vliv na <xref:System.Windows.Forms.ToolStrip> rozložení klávesnice interakce a chování koncových uživatelů:  
  
-   Připojený <xref:System.Windows.Forms.ToolStripPanel>  
  
     <xref:System.Windows.Forms.ToolStrip> Můžete změnit jejich umístění v rámci <xref:System.Windows.Forms.ToolStripPanel> a napříč <xref:System.Windows.Forms.ToolStripPanel>s. `Dock` Vlastnost je ignorována a pokud <xref:System.Windows.Forms.ToolStrip.Stretch%2A> vlastnost je `false`, velikost <xref:System.Windows.Forms.ToolStrip> narůstá položky budou přidány do <xref:System.Windows.Forms.ToolStripPanel>. Obvykle <xref:System.Windows.Forms.ToolStrip> neúčastní pořadí.  
  
-   Ukotveno  
  
     <xref:System.Windows.Forms.ToolStrip> Je umístěn na jedné straně kontejner na stabilní, a rozšíří jeho velikost na celý okraj, ke kterému je ukotven. Obvykle <xref:System.Windows.Forms.ToolStrip> neúčastní pořadí.  
  
-   Absolutně umístěný.  
  
     <xref:System.Windows.Forms.ToolStrip> Je jako další ovládací prvky v tom, že je umístěn ve <xref:System.Windows.Forms.Control.Location%2A> vlastnost, má pevnou velikost a obvykle účastní pořadí.  
  
#### <a name="keyboard-interaction"></a>Interakce klávesnice  
  
##### <a name="access-keys"></a>Přístupové klávesy  
 V kombinaci s nebo následující klávesu ALT, přístupové klíče jsou jedním ze způsobů k aktivaci ovládacího prvku pomocí klávesnice. <xref:System.Windows.Forms.ToolStrip> podporuje oba explicitní a implicitní přístupové klíče. Explicitní definice používá ampersand (&) znak předcházející písmeno. Implicitní definice používá algoritmus, který se pokusí najít odpovídající položku na základě pořadí znaků daný `Text` vlastnost.  
  
##### <a name="shortcut-keys"></a>Klávesové zkratky  
 Klávesové zkratky používané <xref:System.Windows.Forms.MenuStrip> použít kombinaci <xref:System.Windows.Forms.Keys> – výčet (která není konkrétní pořadí) k definování klávesovou zkratku. Můžete také <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> vlastnost zobrazíte klávesovou zkratku s textem, jako je například zobrazení "Del" místo "Odstranit."  
  
##### <a name="navigation"></a>Navigace  
 Klávesa ALT aktivuje <xref:System.Windows.Forms.MenuStrip> na kterou odkazuje <xref:System.Windows.Forms.Form.MainMenuStrip%2A>. Z tohoto místa CTRL + TAB přejde mezi <xref:System.Windows.Forms.ToolStrip> ovládací prvky v rámci `ToolStripPanel`s. Klávesy TAB a klávesy se šipkami na numerické klávesnici přecházet mezi položky v <xref:System.Windows.Forms.ToolStrip>. Speciální algoritmus zpracuje navigační v oblasti přetečení. Vybere MEZERNÍK <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, nebo <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
##### <a name="focus-and-validation"></a>Fokus a ověřování  
 Pokud je aktivován pomocí klávesy ALT <xref:System.Windows.Forms.MenuStrip> nebo <xref:System.Windows.Forms.ToolStrip> obvykle trvat ani odebrat fokus z ovládacího prvku, který je aktuálně aktivní. Pokud je ovládací prvek hostovaným v rámci <xref:System.Windows.Forms.MenuStrip> nebo rozevírací z <xref:System.Windows.Forms.MenuStrip>, ovládacího prvku získá fokus při stisknutí klávesy TAB. Obecně <xref:System.Windows.Forms.Control.GotFocus>, <xref:System.Windows.Forms.Control.LostFocus>, <xref:System.Windows.Forms.Control.Enter>, a <xref:System.Windows.Forms.Control.Leave> události <xref:System.Windows.Forms.MenuStrip> nemusí být vyvolá, když jsou aktivované pomocí klávesnice. V takových případech použít <xref:System.Windows.Forms.MenuStrip.MenuActivate> a <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> události místo.  
  
 Ve výchozím nastavení <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> je `false`. Volání <xref:System.Windows.Forms.ContainerControl.Validate%2A> explicitně ve formuláři pro provedení ověřování.  
  
#### <a name="layout"></a>Rozložení  
 Můžete řídit <xref:System.Windows.Forms.ToolStrip> rozložení pomocí jednoho z členů <xref:System.Windows.Forms.ToolStripLayoutStyle> s <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> vlastnost.  
  
##### <a name="stack-layouts"></a>Rozložení zásobníku  
 Překrývání je uspořádání položek vedle sebe na obou koncích <xref:System.Windows.Forms.ToolStrip>. Následující seznam popisuje rozložení zásobníku.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow> je výchozí. Toto nastavení způsobí, že <xref:System.Windows.Forms.ToolStrip> ke změně jeho rozložení automaticky v souladu s <xref:System.Windows.Forms.ToolStrip.Orientation%2A> vlastnost pro zpracování přetahování a dokování scénáře.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow> vykreslí <xref:System.Windows.Forms.ToolStrip> položky vedle sebe navzájem svisle.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow> vykreslí <xref:System.Windows.Forms.ToolStrip> vodorovně položky vedle sebe navzájem.  
  
##### <a name="other-features-of-stack-layouts"></a>Další funkce rozložení zásobníku  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Určuje konec <xref:System.Windows.Forms.ToolStrip> s nímž je zarovnán položky.  
  
 Pokud nebudou vyhovovat položky v rámci <xref:System.Windows.Forms.ToolStrip>, automaticky se zobrazí tlačítko přetečení. <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> Vlastnost nastavení určuje, zda položka je uvedena v oblasti přetečení, podle potřeby, nebo vždy.  
  
 V <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> událostí, si můžete prohlédnout <xref:System.Windows.Forms.ToolStripItem.Placement%2A> vlastnosti k určení, zda umístění položky na hlavní <xref:System.Windows.Forms.ToolStrip>, přetečení <xref:System.Windows.Forms.ToolStrip>, nebo pokud vůbec není aktuálně zobrazuje. Typické z důvodů, proč se nezobrazí položky jsou položky se nevejdou na hlavní <xref:System.Windows.Forms.ToolStrip> a jeho <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> byla nastavena na <xref:System.Windows.Forms.ToolStripItemOverflow.Never>.  
  
 Ujistěte se, <xref:System.Windows.Forms.ToolStrip> mobilní umístěním <xref:System.Windows.Forms.ToolStripPanel> a nastavení jeho <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> k <xref:System.Windows.Forms.ToolStripGripStyle.Visible>.  
  
##### <a name="other-layout-options"></a>Další možnosti rozložení  
 Další možnosti rozložení <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> a <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>.  
  
##### <a name="flow-layout"></a>Plovoucí rozložení  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> rozložení je výchozí pro <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, a <xref:System.Windows.Forms.ToolStripOverflow>. Je podobná <xref:System.Windows.Forms.FlowLayoutPanel>. Funkce <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> rozložení jsou následující:  
  
-   Všechny funkce <xref:System.Windows.Forms.FlowLayoutPanel> jsou vystavené <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> vlastnost. Musíte vysílat <xref:System.Windows.Forms.LayoutSettings> třídy k <xref:System.Windows.Forms.FlowLayoutSettings> třídy.  
  
-   Můžete použít <xref:System.Windows.Forms.ToolStripItem.Dock%2A> a <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> vlastností v kódu, chcete-li zarovnat položky v rámci řádku.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Vlastnost je ignorována.  
  
-   V <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> událostí, si můžete prohlédnout <xref:System.Windows.Forms.ToolStripItem.Placement%2A> vlastnosti k určení, zda umístění položky na hlavní <xref:System.Windows.Forms.ToolStrip> nebo nevejdou.  
  
-   Není vykreslen úchytu a proto <xref:System.Windows.Forms.ToolStrip> v <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> stylu rozložení v <xref:System.Windows.Forms.ToolStripPanel> nelze přesunout.  
  
-   <xref:System.Windows.Forms.ToolStrip> Tlačítko přetečení není vykreslen, a <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> je ignorována.  
  
##### <a name="table-layout"></a>Rozložení tabulky  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> rozložení je výchozí pro <xref:System.Windows.Forms.StatusStrip>. Je podobná <xref:System.Windows.Forms.TableLayoutPanel>. Funkce <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> rozložení jsou následující:  
  
-   Všechny funkce <xref:System.Windows.Forms.TableLayoutPanel> jsou vystavené <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> vlastnost. Musíte vysílat <xref:System.Windows.Forms.LayoutSettings> třídy k <xref:System.Windows.Forms.TableLayoutSettings> třídy.  
  
-   Můžete použít <xref:System.Windows.Forms.ToolStripItem.Dock%2A> a <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> vlastností v kódu, chcete-li zarovnat položky v rámci buňky tabulky.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Vlastnost je ignorována.  
  
-   V <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> událostí, si můžete prohlédnout <xref:System.Windows.Forms.ToolStripItem.Placement%2A> vlastnosti k určení, zda umístění položky na hlavní <xref:System.Windows.Forms.ToolStrip> nebo nevejdou.  
  
-   Není vykreslen úchytu a proto <xref:System.Windows.Forms.ToolStrip> v <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> stylu rozložení v <xref:System.Windows.Forms.ToolStripPanel> nelze přesunout.  
  
-   <xref:System.Windows.Forms.ToolStrip> Tlačítko přetečení není vykreslen, a <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> je ignorována.  
  
## <a name="toolstripitem"></a>ToolStripItem  
 Následující témata popisují <xref:System.Windows.Forms.ToolStripItem> a ovládací prvky, které jsou odvozeny od ho.  
  
 <xref:System.Windows.Forms.ToolStripItem> je abstraktní základní třída pro všechny položky, které patří do <xref:System.Windows.Forms.ToolStrip>. Tento objekt modelu ukazuje <xref:System.Windows.Forms.ToolStripItem> hierarchie dědičnosti.  
  
 ![Model objektu ToolStripItem](../../../../docs/framework/winforms/controls/media/toolstripitemobjectmodel.gif "ToolStripItemObjectModel")  
ToolStripItem objektový model  
  
 <xref:System.Windows.Forms.ToolStripItem> třídy buď dědit přímo z <xref:System.Windows.Forms.ToolStripItem>, nebo když nepřímo dědí z <xref:System.Windows.Forms.ToolStripItem> prostřednictvím <xref:System.Windows.Forms.ToolStripControlHost> nebo <xref:System.Windows.Forms.ToolStripDropDownItem>.  
  
 <xref:System.Windows.Forms.ToolStripItem> ovládací prvky, musí být obsažená v <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, nebo <xref:System.Windows.Forms.ContextMenuStrip> a nelze ji přidat přímo do formuláře. Různé třídy kontejnerů jsou navrženy tak, aby obsahovala odpovídající podmnožinu <xref:System.Windows.Forms.ToolStripItem> ovládací prvky.  
  
 V následující tabulce jsou uvedeny stock <xref:System.Windows.Forms.ToolStripItem> ovládací prvky a kontejnerů, ve kterých oblast nejvhodnější. I když některé <xref:System.Windows.Forms.ToolStrip> položka může být hostovaný v žádném <xref:System.Windows.Forms.ToolStrip>-odvozené kontejneru, tyto položky byly navrženy pro oblast nejvhodnější v následujících kontejnerech:  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripDropDown> v panelu nástrojů návrháře nezobrazí.  
  
|Obsažený položky|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|Prvku ToolStripDropDown|  
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
  
### <a name="toolstripbutton"></a>Ovládací prvek ToolStripButton  
 <xref:System.Windows.Forms.ToolStripButton> je položka tlačítka pro <xref:System.Windows.Forms.ToolStrip>. Můžete ji zobrazit s různými styly ohraničení a slouží k představují a aktivaci provozní stavy. Můžete také definovat ji tak, aby měl fokus ve výchozím nastavení.  
  
### <a name="toolstriplabel"></a>ToolStripLabel  
 <xref:System.Windows.Forms.ToolStripLabel> Poskytuje funkce popisek v <xref:System.Windows.Forms.ToolStrip> ovládací prvky. <xref:System.Windows.Forms.ToolStripLabel> Je stejná jako <xref:System.Windows.Forms.ToolStripButton> který ve výchozím nastavení nezíská fokus a který nevykresluje jako stisknutí nebo zvýrazněné.  
  
 <xref:System.Windows.Forms.ToolStripLabel> jako položku hostované podporuje přístupové klíče.  
  
 Použití <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>, a <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> vlastnosti <xref:System.Windows.Forms.ToolStripLabel> pro podporu řízení propojení v <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel> verze <xref:System.Windows.Forms.ToolStripLabel> určený speciálně pro použití v <xref:System.Windows.Forms.StatusStrip>. Speciální funkce zahrnují <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>, a <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.  
  
### <a name="toolstripseparator"></a>Třídu ToolStripSeparator  
 <xref:System.Windows.Forms.ToolStripSeparator> Přidá svislé nebo vodorovné čáry na panelu nástrojů nebo nabídky, v závislosti na orientaci. Poskytuje seskupení nebo rozdíl mezi položky, jako jsou ty, v nabídce.  
  
 Můžete přidat <xref:System.Windows.Forms.ToolStripSeparator> v době návrhu výběrem z rozevíracího seznamu. Ale můžete také automaticky vytvořit <xref:System.Windows.Forms.ToolStripSeparator> zadáním pomlčku (-) v uzlu návrháře šablony nebo v <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> metoda.  
  
### <a name="toolstripcontrolhost"></a>ToolStripControlHost  
 <xref:System.Windows.Forms.ToolStripControlHost> je abstraktní základní třída pro <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, a <xref:System.Windows.Forms.ToolStripProgressBar>. <xref:System.Windows.Forms.ToolStripControlHost> může být hostitelem jiných ovládacích prvků, včetně vlastní ovládací prvky, dvěma způsoby:  
  
-   Vytvořit <xref:System.Windows.Forms.ToolStripControlHost> s třídou, která je odvozena z <xref:System.Windows.Forms.Control>. K úplnému přístupu k hostované řízení a vlastnosti, musíte vysílat <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> vlastnost zpět na skutečnou třídy představuje.  
  
-   Rozšíření <xref:System.Windows.Forms.ToolStripControlHost>a v zděděné třídy výchozí konstruktor, volat konstruktor základní třídy předávání třídu odvozenou z <xref:System.Windows.Forms.Control>. Tato možnost umožňuje zabalení běžné řízení metod a vlastností pro usnadnění přístupu v <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripcombobox"></a>ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox> je <xref:System.Windows.Forms.ComboBox> optimalizována pro hostování v <xref:System.Windows.Forms.ToolStrip>. Podmnožinu vlastností a událostí hostované ovládacího prvku jsou zveřejněné na <xref:System.Windows.Forms.ToolStripComboBox> úroveň, ale základní <xref:System.Windows.Forms.ComboBox> je plně přístupné prostřednictvím řízení <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> vlastnost.  
  
### <a name="toolstriptextbox"></a>ToolStripTextBox  
 <xref:System.Windows.Forms.ToolStripTextBox> je <xref:System.Windows.Forms.TextBox> optimalizována pro hostování v <xref:System.Windows.Forms.ToolStrip>. Podmnožinu vlastností a událostí hostované ovládacího prvku jsou zveřejněné na <xref:System.Windows.Forms.ToolStripTextBox> úroveň, ale základní <xref:System.Windows.Forms.TextBox> je plně přístupné prostřednictvím řízení <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> vlastnost.  
  
### <a name="toolstripprogressbar"></a>ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar> je <xref:System.Windows.Forms.ProgressBar> optimalizována pro hostování v <xref:System.Windows.Forms.ToolStrip>. Podmnožinu vlastností a událostí hostované ovládacího prvku jsou zveřejněné na <xref:System.Windows.Forms.ToolStripProgressBar> úroveň, ale základní <xref:System.Windows.Forms.ProgressBar> je plně přístupné prostřednictvím řízení <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> vlastnost.  
  
### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem> je abstraktní základní třída pro <xref:System.Windows.Forms.ToolStripMenuItem>, <xref:System.Windows.Forms.ToolStripDropDownButton>, a <xref:System.Windows.Forms.ToolStripSplitButton>, který může hostovat položky přímo nebo další položky hostitele v kontejneru rozevíracího seznamu. To provedete nastavením <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> vlastnosti <xref:System.Windows.Forms.ToolStripDropDown> a nastavení <xref:System.Windows.Forms.ToolStrip.Items%2A> vlastnost <xref:System.Windows.Forms.ToolStripDropDown>. Přístupu k těmto položkám rozevíracího seznamu přímo pomocí <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> vlastnost.  
  
### <a name="toolstripmenuitem"></a>ToolStripMenuItem  
 <xref:System.Windows.Forms.ToolStripMenuItem> je <xref:System.Windows.Forms.ToolStripDropDownItem> to funguje s <xref:System.Windows.Forms.ToolStripDropDownMenu> a <xref:System.Windows.Forms.ContextMenuStrip> pro zpracování speciální zvýraznění, rozložení a sloupcem uspořádání pro nabídky.  
  
### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton> vypadá jako <xref:System.Windows.Forms.ToolStripButton>, ale zobrazuje oblasti rozevíracího seznamu, když uživatel klikne ho. Skrytí nebo zobrazení na šipku rozevíracího seznamu nastavením <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> vlastnost. <xref:System.Windows.Forms.ToolStripDropDownButton> hostitelé <xref:System.Windows.Forms.ToolStripOverflowButton> který zobrazí položky, které přetečení <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripsplitbutton"></a>Prvku ToolStripSplitButton  
 <xref:System.Windows.Forms.ToolStripSplitButton> tlačítko kombinuje a rozevírací tlačítko funkcí.  
  
 Použití <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> vlastnost k synchronizaci <xref:System.Windows.Forms.Control.Click> událostí zvolené položky rozevírací seznam s položky zobrazené na tlačítko.  
  
### <a name="toolstripitem-generic-features"></a>ToolStripItem obecné funkce  
 <xref:System.Windows.Forms.ToolStripItem> poskytuje následující obecné funkce a možnosti pro dědění ovládací prvky:  
  
-   Základní události  
  
-   Zpracování obrázku  
  
-   Zarovnání  
  
-   Textové a obrázkové relace  
  
-   Styl zobrazení  
  
#### <a name="core-events"></a>Základní události  
 <xref:System.Windows.Forms.ToolStripItem> ovládací prvky obdrží vlastních událostí Malování, myši a klikněte na tlačítko a můžete provést některé klávesnice předzpracování také.  
  
#### <a name="image-handling"></a>Zpracování obrázku  
 <xref:System.Windows.Forms.ToolStripItem.Image%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>, A <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> vlastnosti se týkají různých aspektů zpracování obrázku. Použití obrázků v <xref:System.Windows.Forms.ToolStrip> ovládací prvky podle nastavení těchto vlastností přímo, nebo nastavením je spustit čas – jen <xref:System.Windows.Forms.ToolStrip.ImageList%2A> vlastnost.  
  
 Změna měřítka obrázku je dáno interakci vlastnosti v obou <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.ToolStripItem>, a to takto:  
  
-   <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A> je škále finální image určené kombinací obrázku <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> nastavení a kontejneru <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> nastavení.  
  
    -   Pokud <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> je `true` (výchozí) a <xref:System.Windows.Forms.ToolStripItemImageScaling> je <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>, žádná změna velikosti obrázku dojde a <xref:System.Windows.Forms.ToolStrip> velikost je, že nebo předepsané minimální velikost největší položky.  
  
    -   Pokud <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> je `false` a <xref:System.Windows.Forms.ToolStripItemImageScaling> je <xref:System.Windows.Forms.ToolStripItemImageScaling.None>, ani image ani <xref:System.Windows.Forms.ToolStrip> škálování dojde.  
  
#### <a name="alignment"></a>Zarovnání  
 Hodnota <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> vlastnost určuje konec <xref:System.Windows.Forms.ToolStrip> na které se vyskytuje položku. <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Funguje pouze tehdy, když vlastnost stylu rozložení <xref:System.Windows.Forms.ToolStrip> je nastaven na jednu z hodnot přetečení zásobníku.  
  
 Položky, které jsou umístěny na <xref:System.Windows.Forms.ToolStrip> v pořadí, ve kterém zobrazí položky v kolekci položek. Můžete změnit prostřednictvím kódu programu, kde je rozložená položku, <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> metoda přesunout položku v kolekci. Tato metoda přesune položku, ale není duplicitní.  
  
#### <a name="text-and-image-relationship"></a>Text a vztah bitové kopie  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> Vlastnost definuje relativní umístění bitové kopie s ohledem na text na <xref:System.Windows.Forms.ToolStripItem>. Položky, které nemají obrázek, text nebo obě jsou považovány za zvláštní případy tak, aby <xref:System.Windows.Forms.ToolStripItem> nezobrazí na prázdné místo pro chybí element nebo elementy.  
  
#### <a name="display-style"></a>Styl zobrazení  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> Umožňuje nastavit hodnoty vlastnosti textových a obrázkových položky při zobrazování pouze to, co chcete. To se obvykle používá při zobrazující stejnou položku v jiném kontextu změnit styl zobrazení.  
  
## <a name="accessory-classes"></a>Příslušenství třídy  
 Třídy, které poskytují různé další funkce zahrnují:  
  
-   <xref:System.Windows.Forms.ToolStripManager> podporuje <xref:System.Windows.Forms.ToolStrip>-související úlohy pro celý aplikace, jako je například slučování, nastavení a zobrazovací jednotky možnosti.  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> umožňuje používat konkrétní styl nebo motiv se <xref:System.Windows.Forms.ToolStrip> snadno.  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> Vytvoří pera a štětce založené na tabulce replaceable barev (<xref:System.Windows.Forms.ProfessionalColorTable>).  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> platí systému barvy a nestrukturované vizuální styl pro <xref:System.Windows.Forms.ToolStrip> aplikace.  
  
-   <xref:System.Windows.Forms.ToolStripContainer> je podobná <xref:System.Windows.Forms.SplitContainer>. Používá čtyři ukotveného straně panelů (instance <xref:System.Windows.Forms.ToolStripPanel>) a jednu centrální panel (instance <xref:System.Windows.Forms.ToolStripContentPanel>) k vytvoření typické uspořádání. Nelze odebrat panelů straně, ale můžete je skrýt. Nelze odebrat ani skrýt středovém panelu. Můžete uspořádat jednu nebo více <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, nebo <xref:System.Windows.Forms.StatusStrip> ovládacích prvků na panely straně a centrální panel můžete použít pro další ovládací prvky. <xref:System.Windows.Forms.ToolStripContentPanel> Také poskytuje způsob, jak získat podporu pro vykreslení do těla formuláře pro konzistentní vzhled. <xref:System.Windows.Forms.ToolStripContainer> nepodporuje rozhraní více dokumentů (MDI).  
  
-   <xref:System.Windows.Forms.ToolStripPanel> Poskytuje místo pro přesunutí a uspořádání <xref:System.Windows.Forms.ToolStrip> ovládací prvky. Pokud se tak rozhodnete, můžete použít pouze jeden panely a <xref:System.Windows.Forms.ToolStripPanel> dobře funguje v MDI scénáře.  
  
## <a name="see-also"></a>Viz také  
 [Přehled ovládacího prvku ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-overview-windows-forms.md)  
 [Shrnutí technologie ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-technology-summary.md)  
 [Ovládací prvek ToolStrip](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [Ovládací prvek MenuStrip](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)  
 [Ovládací prvek StatusStrip](../../../../docs/framework/winforms/controls/statusstrip-control.md)  
 [Ovládací prvek ContextMenuStrip](../../../../docs/framework/winforms/controls/contextmenustrip-control.md)  
 [Ovládací prvek BindingNavigator](../../../../docs/framework/winforms/controls/bindingnavigator-control-windows-forms.md)
