---
title: Architektura ovládacího prvku ToolStrip
ms.date: 03/30/2017
helpviewer_keywords:
- ToolStrip control [Windows Forms], architecture
ms.assetid: 71df2d18-862e-4701-9ff9-c1fe606f94f2
ms.openlocfilehash: bede247ca9e1c2c20ffc8fef9fd4fab89aa78453
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/29/2019
ms.locfileid: "58654767"
---
# <a name="toolstrip-control-architecture"></a>Architektura ovládacího prvku ToolStrip
<xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.ToolStripItem> třídy poskytují flexibilní a rozšiřitelný systém pro zobrazení položek panelu nástrojů, nabídek a stav. Tyto třídy jsou obsaženy v <xref:System.Windows.Forms> obor názvů a že jsou všechny obvykle s názvem s předponou "Ovládací prvek ToolStrip" (například <xref:System.Windows.Forms.ToolStripOverflow>) nebo s příponou "Odstranit" (například <xref:System.Windows.Forms.MenuStrip>).  
  
## <a name="toolstrip"></a>ToolStrip  
 Následující témata popisují <xref:System.Windows.Forms.ToolStrip> a ovládací prvky, které jsou odvozeny z něj.  
  
 <xref:System.Windows.Forms.ToolStrip> je abstraktní základní třída pro <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, a <xref:System.Windows.Forms.ContextMenuStrip>. Následující objekt modelu ukazuje <xref:System.Windows.Forms.ToolStrip> hierarchii dědičnosti.  
  
 ![Diagram, který je znázorněn objektový model prvku ToolStrip.](./media/toolstrip-control-architecture/toolstrip-object-model.gif)  
  
 Dostanete všechny položky v <xref:System.Windows.Forms.ToolStrip> prostřednictvím <xref:System.Windows.Forms.ToolStrip.Items%2A> kolekce. Dostanete všechny položky v <xref:System.Windows.Forms.ToolStripDropDownItem> prostřednictvím <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> kolekce. Ve třídě odvozené z <xref:System.Windows.Forms.ToolStrip>, můžete použít také <xref:System.Windows.Forms.ToolStrip.DisplayedItems%2A> vlastnosti pro přístup k pouze ty položky, které jsou aktuálně zobrazeny. Toto jsou položky, které nejsou aktuálně nabídky přetečení.  
  
 Následující položky jsou vytvořené speciálně navržený pro hladkou spolupráci s oběma <xref:System.Windows.Forms.ToolStripSystemRenderer> a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> v všechny orientace. Jsou k dispozici ve výchozím nastavení při návrhu pro <xref:System.Windows.Forms.ToolStrip> ovládacího prvku:  
  
-   <xref:System.Windows.Forms.ToolStripButton>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="menustrip"></a>MenuStrip  
 <xref:System.Windows.Forms.MenuStrip> je kontejner nejvyšší úrovně, který nahrazuje <xref:System.Windows.Forms.MainMenu>. Také poskytuje klíče zpracování a více dokumentů (MDI) interface funkce. Funkčně <xref:System.Windows.Forms.ToolStripDropDownItem> a <xref:System.Windows.Forms.ToolStripMenuItem> fungují společně s <xref:System.Windows.Forms.MenuStrip>, i když jsou odvozeny z <xref:System.Windows.Forms.ToolStripItem>.  
  
 Následující položky jsou vytvořené speciálně navržený pro hladkou spolupráci s oběma <xref:System.Windows.Forms.ToolStripSystemRenderer> a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> v všechny orientace. Jsou k dispozici ve výchozím nastavení při návrhu pro <xref:System.Windows.Forms.MenuStrip> ovládacího prvku:  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="statusstrip"></a>StatusStrip  
 <xref:System.Windows.Forms.StatusStrip> nahrazuje <xref:System.Windows.Forms.StatusBar> ovládacího prvku. Speciální funkce <xref:System.Windows.Forms.StatusStrip> zahrnout vlastní tabulkové rozložení, podporu pro formulář pro změnu velikosti a přesunutí grips a `Spring` vlastnost, která umožňuje <xref:System.Windows.Forms.ToolStripStatusLabel> tak, aby vyplnil dostupné místo automaticky.  
  
 Následující položky jsou vytvořené speciálně navržený pro hladkou spolupráci s oběma <xref:System.Windows.Forms.ToolStripSystemRenderer> a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> v všechny orientace. Jsou k dispozici ve výchozím nastavení při návrhu pro <xref:System.Windows.Forms.StatusStrip> ovládacího prvku:  
  
-   <xref:System.Windows.Forms.ToolStripStatusLabel>  
  
-   <xref:System.Windows.Forms.ToolStripDropDownButton>  
  
-   <xref:System.Windows.Forms.ToolStripSplitButton>  
  
-   <xref:System.Windows.Forms.ToolStripProgressBar>  
  
### <a name="contextmenustrip"></a>ContextMenuStrip  
 <xref:System.Windows.Forms.ContextMenuStrip> nahradí <xref:System.Windows.Forms.ContextMenu>. Můžete přiřadit <xref:System.Windows.Forms.ContextMenuStrip> pomocí libovolného ovládacího prvku a pravým tlačítkem myši klikněte na tlačítko automaticky zobrazí místní nabídky (nebo místní nabídky). Můžete zobrazit <xref:System.Windows.Forms.ContextMenuStrip> prostřednictvím kódu programu pomocí <xref:System.Windows.Forms.ToolStripDropDown.Show%2A> metody. <xref:System.Windows.Forms.ContextMenuStrip> podporuje zrušitelný <xref:System.Windows.Forms.ToolStripDropDown.Opening> a <xref:System.Windows.Forms.ToolStripDropDown.Closing> události pro zpracování více kliknutím scénáře a dynamické naplnění. <xref:System.Windows.Forms.ContextMenuStrip> podporuje Image, stavu zaškrtnutí položky nabídky, text, přístupové klíče, klávesové zkratky a podnabídky.  
  
 Následující položky jsou vytvořené speciálně navržený pro hladkou spolupráci s oběma <xref:System.Windows.Forms.ToolStripSystemRenderer> a <xref:System.Windows.Forms.ToolStripProfessionalRenderer> v všechny orientace. Jsou k dispozici ve výchozím nastavení při návrhu pro <xref:System.Windows.Forms.ContextMenuStrip> ovládacího prvku:  
  
-   <xref:System.Windows.Forms.ToolStripMenuItem>  
  
-   <xref:System.Windows.Forms.ToolStripSeparator>  
  
-   <xref:System.Windows.Forms.ToolStripTextBox>  
  
-   <xref:System.Windows.Forms.ToolStripComboBox>  
  
### <a name="toolstrip-generic-features"></a>Funkce obecného prvku ToolStrip  
 Toto téma popisuje funkce a chování, které jsou obecné na <xref:System.Windows.Forms.ToolStrip> a odvozené ovládací prvky.  
  
#### <a name="painting"></a>Malování  
 Můžete provést vlastní vykreslování <xref:System.Windows.Forms.ToolStrip> ovládací prvky několika způsoby. Stejně jako u jiných ovládacích prvků Windows Forms <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.ToolStripItem> mají overridable `OnPaint` metody a `Paint` události. Stejně jako u pravidelné Malování souřadnicový systém je vzhledem ke klientské oblasti ovládacího prvku; levém horním rohu ovládacího prvku je 0, 0. `Paint` Událostí a `OnPaint` metodu <xref:System.Windows.Forms.ToolStripItem> chovají se jako další události ovládacího prvku programu Malování.  
  
 <xref:System.Windows.Forms.ToolStrip> Ovládací prvky také poskytovat lepší přístup k vykreslování položky a kontejneru, přistoupit přes <xref:System.Windows.Forms.ToolStripRenderer> třídu, která má přepisovatelné metody pro vykreslování na pozadí, pozadí položky, obrázek položky, položka šipku, text položky a ohraničení <xref:System.Windows.Forms.ToolStrip>. Argumenty událostí pro tyto metody vystavit několik vlastností, jako je například obdélníky, barvy a textových formátů, které můžete upravit podle potřeby.  
  
 Chcete-li upravit jen několik aspektů jak překreslit položku, je obvykle přepsat <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Pokud píšete nové položky a chcete řídit všechny aspekty Malování, má přednost před `OnPaint` metody. V rámci `OnPaint`, můžete použít metody z <xref:System.Windows.Forms.ToolStripRenderer>.  
  
 Ve výchozím nastavení <xref:System.Windows.Forms.ToolStrip> je dvojité vyrovnávací paměti, využití výhod <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> nastavení.  
  
#### <a name="parenting"></a>Správa nadřazených  
 Koncept kontejneru vlastnictví a vztahy k nadřazeným položkám je složitější v <xref:System.Windows.Forms.ToolStrip> ovládacích prvků než v jiných ovládacích prvků Windows Forms kontejneru. Který je nezbytný pro podporu dynamické scénářů, jako je přetečení, sdílení položek rozbalovací napříč více <xref:System.Windows.Forms.ToolStrip> položky a pro podporu generování <xref:System.Windows.Forms.ContextMenuStrip> z ovládacího prvku.  
  
 Následující seznam popisuje členy související s vztahy k nadřazeným položkám a vysvětluje jejich použití.  
  
-   <xref:System.Windows.Forms.ToolStripDropDown.OwnerItem%2A> přistupuje k položky, které je zdrojem položka rozevíracího seznamu. Je to podobné <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A>, ale místo vrácení ovládací prvek vrátí <xref:System.Windows.Forms.ToolStripItem>.  
  
-   <xref:System.Windows.Forms.ContextMenuStrip.SourceControl%2A> Určuje, který ovládací prvek je zdrojem z <xref:System.Windows.Forms.ContextMenuStrip> při více ovládacích prvků sdílet stejný <xref:System.Windows.Forms.ContextMenuStrip>.  
  
-   <xref:System.Windows.Forms.ToolStripItem.GetCurrentParent%2A> je jen pro čtení přistupující objekt, který chcete <xref:System.Windows.Forms.ToolStripItem.Parent%2A> vlastnost. Nadřazená se liší od vlastníka, v tom, že nadřazený označuje vrácené aktuální <xref:System.Windows.Forms.ToolStrip> v které položky se zobrazí, který může být v oblasti přetečení.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Owner%2A> Vrátí <xref:System.Windows.Forms.ToolStrip> jehož kolekce položek obsahuje aktuální <xref:System.Windows.Forms.ToolStripItem>. Toto je nejlepší způsob, jak odkazovat na <xref:System.Windows.Forms.ToolStrip.ImageList%2A> nebo jiné vlastnosti na nejvyšší úrovni <xref:System.Windows.Forms.ToolStrip> aniž byste museli napsat speciální kód pro zpracování přetečení.  
  
#### <a name="behavior-of-inherited-controls"></a>Chování zděděného ovládacích prvků  
 Následující ovládací prvky jsou zamknuté pokaždé, když se používají v dědičnosti:  
  
-   <xref:System.Windows.Forms.ToolStrip>  
  
-   <xref:System.Windows.Forms.MenuStrip>  
  
-   <xref:System.Windows.Forms.ContextMenuStrip>  
  
-   <xref:System.Windows.Forms.StatusStrip>  
  
-   <xref:System.Windows.Forms.ToolStripPanel> který obsahuje panelů v <xref:System.Windows.Forms.ToolStripContainer> a také individuální <xref:System.Windows.Forms.ToolStripPanel> ovládacích prvků.  
  
 Například vytvořte novou aplikaci Windows Forms pomocí jednoho nebo více ovládacích prvků v předchozím seznamu. Nastavit modifikátor přístupu jednoho nebo více ovládacích prvků do `public` nebo `protected`a pak sestavte projekt. Přidat formulář, který dědí z první formulář a vyberte zděděný ovládací prvek. Ovládací prvek zobrazí uzamčené, chová jako kdyby byla její modifikátor přístupu `private`.  
  
#### <a name="toolstripcontainer-support-of-inheritance"></a>ToolStripContainer – podpora dědičnosti  
 <xref:System.Windows.Forms.ToolStripContainer> Ovládací prvek podporuje omezenou zděděné scénářů, podobně jako v následujícím příkladu:  
  
1.  Vytvoření nové aplikace Windows Forms.  
  
2.  Přidat <xref:System.Windows.Forms.ToolStripContainer> do formuláře.  
  
3.  Modifikátor přístupu nastaven <xref:System.Windows.Forms.ToolStripContainer> k `public` nebo `protected`.  
  
4.  Přidat libovolnou kombinaci <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, a <xref:System.Windows.Forms.ContextMenuStrip> ovládacích prvků <xref:System.Windows.Forms.ToolStripPanel> regionů <xref:System.Windows.Forms.ToolStripContainer>.  
  
5.  Sestavte projekt.  
  
6.  Přidání formuláře, která dědí z první formuláře.  
  
7.  Vyberte zděděnou <xref:System.Windows.Forms.ToolStripContainer> ve formuláři.  
  
#### <a name="inherited-behavior-of-child-controls"></a>Zděděné chování podřízených ovládacích prvků  
 Po dokončení předchozích kroků, očekávejte toto chování zděděného:  
  
-   V návrháři se ovládací prvek zobrazí s ikonou zděděná.  
  
-   <xref:System.Windows.Forms.ToolStripPanel> Ovládací prvky jsou zamknuté; nelze vybrat nebo změnit uspořádání jejich obsah.  
  
-   Můžete přidat ovládací prvky <xref:System.Windows.Forms.ToolStripContentPanel>, přesuňte ovládací prvky a aby byly podřízené ovládací prvky <xref:System.Windows.Forms.ToolStripContentPanel>.  
  
-   Změny přetrvávají po sestavení formuláře.  
  
    > [!NOTE]
    >  Odebere modifikátory přístupu ze všech <xref:System.Windows.Forms.ToolStripPanel> ovládací prvky, které jsou součástí <xref:System.Windows.Forms.ToolStripContainer>. Modifikátor přístupu <xref:System.Windows.Forms.ToolStripContainer> řídí celý ovládací prvek.  
  
#### <a name="partial-trust"></a>Částečná důvěryhodnost  
 Omezení `ToolStrip`s v částečném vztahu důvěryhodnosti jsou navržené tak, aby se zabránilo nechtěnému položku osobní informace, které by mohly používat neoprávněné osoby nebo služby. Ochranná opatření jsou následující:  
  
-   `ToolStripDropDown` ovládací prvky vyžadují <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> pro zobrazení položek v <xref:System.Windows.Forms.ToolStripControlHost>. To platí pro oba vnitřní ovládací prvky, jako <xref:System.Windows.Forms.ToolStripTextBox>, <xref:System.Windows.Forms.ToolStripComboBox>, a <xref:System.Windows.Forms.ToolStripProgressBar> jako také tak, aby uživatel vytvořil ovládací prvky. Pokud tento požadavek není splněn, tyto položky se nezobrazují. Není vyvolána žádná výjimka.  
  
-   Nastavení <xref:System.Windows.Forms.ToolStripDropDown.AutoClose%2A> vlastnost `false` není povolena a možné zrušit <xref:System.Windows.Forms.ToolStripDropDown.Closing> události parametr je ignorován. Díky tomu je možné zadat více než jedním stisknutím klávesy bez zavření položka rozevíracího seznamu. Pokud tento požadavek není splněn, tyto položky se nezobrazují. Není vyvolána žádná výjimka.  
  
-   Mnoho stisk klávesy zpracování událostí nebude vyvolána, když se vyskytují v částečném vztahu důvěryhodnosti kontextech jiné než <xref:System.Security.Permissions.UIPermissionWindow.AllWindows>.  
  
-   Přístupové klíče nejsou při zpracování <xref:System.Security.Permissions.UIPermissionWindow.AllWindows> nebylo uděleno.  
  
#### <a name="usage"></a>Použití  
 Následující vzory používání se mít vliv <xref:System.Windows.Forms.ToolStrip> rozložení, interakce klávesnice a chování koncových uživatelů:  
  
-   Připojené v <xref:System.Windows.Forms.ToolStripPanel>  
  
     <xref:System.Windows.Forms.ToolStrip> Můžete změnit umístění v rámci <xref:System.Windows.Forms.ToolStripPanel> a napříč <xref:System.Windows.Forms.ToolStripPanel>s. `Dock` Vlastnost se ignoruje a pokud <xref:System.Windows.Forms.ToolStrip.Stretch%2A> vlastnost `false`, velikost <xref:System.Windows.Forms.ToolStrip> narůstá položky budou přidány do <xref:System.Windows.Forms.ToolStripPanel>. Obvykle <xref:System.Windows.Forms.ToolStrip> není součástí pořadí ovládacích prvků.  
  
-   Ukotvení  
  
     <xref:System.Windows.Forms.ToolStrip> Je umístěn na jedné straně kontejner ve službě pevné umístění a rozšíří jeho velikost za celý edge, ke kterému je ukotven. Obvykle <xref:System.Windows.Forms.ToolStrip> není součástí pořadí ovládacích prvků.  
  
-   Absolutně umístěné  
  
     <xref:System.Windows.Forms.ToolStrip> Je stejně jako ostatní ovládací prvky v tom, že ji umístí <xref:System.Windows.Forms.Control.Location%2A> vlastnost, má pevnou velikost a obvykle podílí na pořadí.  
  
#### <a name="keyboard-interaction"></a>Interakce klávesnice  
  
##### <a name="access-keys"></a>Přístupové klíče  
 V kombinaci se nebo po klávesu ALT, přístupových klíčů jsou jednosměrné k aktivaci ovládacího prvku pomocí klávesnice. <xref:System.Windows.Forms.ToolStrip> podporuje oba explicitní a implicitní přístupové klíče. Explicitní definice používá ampersandem (&) znak předchází písmeno. Implicitní definice používá algoritmus, který se pokusí najít odpovídající položky na základě pořadí znaků danou `Text` vlastnost.  
  
##### <a name="shortcut-keys"></a>Klávesové zkratky  
 Klávesové zkratky používané <xref:System.Windows.Forms.MenuStrip> použít kombinaci <xref:System.Windows.Forms.Keys> výčet (což není konkrétní pořadí) k definování klávesovou zkratku. Můžete také použít <xref:System.Windows.Forms.ToolStripMenuItem.ShortcutKeyDisplayString%2A> vlastnost zobrazíte klávesové zkratky s textem, jako je například zobrazení "Del" místo "Odstranit".  
  
##### <a name="navigation"></a>Navigace  
 Aktivuje klávesu ALT <xref:System.Windows.Forms.MenuStrip> odkazované <xref:System.Windows.Forms.Form.MainMenuStrip%2A>. Odtud, CTRL + TAB přechází mezi <xref:System.Windows.Forms.ToolStrip> ovládací prvky v rámci `ToolStripPanel`s. Klávesu TAB a klávesy se šipkami na numerické klávesnici procházet mezi položkami v <xref:System.Windows.Forms.ToolStrip>. Speciální algoritmus zpracovává navigace v oblasti přetečení. Vybere MEZERNÍK <xref:System.Windows.Forms.ToolStripButton>, <xref:System.Windows.Forms.ToolStripDropDownButton>, nebo <xref:System.Windows.Forms.ToolStripSplitButton>.  
  
##### <a name="focus-and-validation"></a>Výběr a ověření  
 Když se aktivuje pomocí klávesy ALT <xref:System.Windows.Forms.MenuStrip> nebo <xref:System.Windows.Forms.ToolStrip> obvykle ani trvat ani odebrání ovládacího prvku, který má aktuálně fokus zaměření. Pokud je ovládací prvek, který je hostován v rámci <xref:System.Windows.Forms.MenuStrip> nebo rozevírací nabídku z <xref:System.Windows.Forms.MenuStrip>, ovládací prvek získá fokus, když uživatel stiskne klávesu TAB. Obecně platí <xref:System.Windows.Forms.Control.GotFocus>, <xref:System.Windows.Forms.Control.LostFocus>, <xref:System.Windows.Forms.Control.Enter>, a <xref:System.Windows.Forms.Control.Leave> události <xref:System.Windows.Forms.MenuStrip> nemusí být vyvolána, když jsou aktivované pomocí klávesnice. V takovém případě použijte <xref:System.Windows.Forms.MenuStrip.MenuActivate> a <xref:System.Windows.Forms.MenuStrip.MenuDeactivate> události místo.  
  
 Ve výchozím nastavení <xref:System.Windows.Forms.ToolStrip.CausesValidation%2A> je `false`. Volání <xref:System.Windows.Forms.ContainerControl.Validate%2A> explicitně na formuláři provést ověření.  
  
#### <a name="layout"></a>Rozložení  
 Můžete řídit <xref:System.Windows.Forms.ToolStrip> rozložení výběrem jedné z členů <xref:System.Windows.Forms.ToolStripLayoutStyle> s <xref:System.Windows.Forms.ToolStrip.LayoutStyle%2A> vlastnost.  
  
##### <a name="stack-layouts"></a>Rozložení zásobníku  
 Překrývání je uspořádání položek vedle sebe na obou koncích <xref:System.Windows.Forms.ToolStrip>. Následující seznam popisuje rozložení zásobníku.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.StackWithOverflow> je výchozí nastavení. Toto nastavení způsobí, že <xref:System.Windows.Forms.ToolStrip> ke změně rozložení automaticky v souladu s <xref:System.Windows.Forms.ToolStrip.Orientation%2A> vlastnost pro zpracování přetažení a dokování scénáře.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow> vykreslí <xref:System.Windows.Forms.ToolStrip> položky svisle vedle sebe.  
  
-   <xref:System.Windows.Forms.ToolStripLayoutStyle.HorizontalStackWithOverflow> vykreslí <xref:System.Windows.Forms.ToolStrip> položky vedle sebe ve vodorovném směru.  
  
##### <a name="other-features-of-stack-layouts"></a>Další funkce rozložení zásobníku  
 <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Určuje konec <xref:System.Windows.Forms.ToolStrip> k položce zarovnán.  
  
 Pokud nebudou vyhovovat položky v rámci <xref:System.Windows.Forms.ToolStrip>, se automaticky zobrazí tlačítku přetečení. <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> Vlastnost nastavení určuje, zda položka se zobrazí v oblasti přetečení, podle potřeby, nebo vždy.  
  
 V <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> události, si můžete prohlédnout <xref:System.Windows.Forms.ToolStripItem.Placement%2A> a určí, zda byl umístěn položky na hlavní <xref:System.Windows.Forms.ToolStrip>, přetečení <xref:System.Windows.Forms.ToolStrip>, nebo pokud se nezobrazuje aktuálně vůbec. Běžné důvody, proč se nezobrazí položka se, že položka nevejdou na hlavní <xref:System.Windows.Forms.ToolStrip> a jeho <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> nastavenou na <xref:System.Windows.Forms.ToolStripItemOverflow.Never>.  
  
 Ujistěte se, <xref:System.Windows.Forms.ToolStrip> přesouvatelný tak, že vložíte ho <xref:System.Windows.Forms.ToolStripPanel> a nastavení jeho <xref:System.Windows.Forms.ToolStrip.GripStyle%2A> k <xref:System.Windows.Forms.ToolStripGripStyle.Visible>.  
  
##### <a name="other-layout-options"></a>Další možnosti rozložení  
 Další možnosti rozložení jsou <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> a <xref:System.Windows.Forms.ToolStripLayoutStyle.Table>.  
  
##### <a name="flow-layout"></a>Plovoucí rozložení  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> rozložení je výchozí nastavení pro <xref:System.Windows.Forms.ContextMenuStrip>, <xref:System.Windows.Forms.ToolStripDropDownMenu>, a <xref:System.Windows.Forms.ToolStripOverflow>. Se podobá <xref:System.Windows.Forms.FlowLayoutPanel>. Funkce <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> rozložení jsou následující:  
  
-   Všechny funkce <xref:System.Windows.Forms.FlowLayoutPanel> vrstvou <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> vlastnost. Musíte přetypovat <xref:System.Windows.Forms.LayoutSettings> třídu <xref:System.Windows.Forms.FlowLayoutSettings> třídy.  
  
-   Můžete použít <xref:System.Windows.Forms.ToolStripItem.Dock%2A> a <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> vlastností v kódu pro zarovnání položky v daném řádku.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Vlastnost se ignoruje.  
  
-   V <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> události, si můžete prohlédnout <xref:System.Windows.Forms.ToolStripItem.Placement%2A> a určí, zda byl umístěn položky na hlavní <xref:System.Windows.Forms.ToolStrip> nebo nevejdou.  
  
-   Úchytu není vykresleno a proto <xref:System.Windows.Forms.ToolStrip> v <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> styl rozložení v <xref:System.Windows.Forms.ToolStripPanel> nelze přesunout.  
  
-   <xref:System.Windows.Forms.ToolStrip> Tlačítku přetečení není vykresleno, a <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> se ignoruje.  
  
##### <a name="table-layout"></a>Rozložení tabulky  
 <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> rozložení je výchozí nastavení pro <xref:System.Windows.Forms.StatusStrip>. Je to podobné <xref:System.Windows.Forms.TableLayoutPanel>. Funkce <xref:System.Windows.Forms.ToolStripLayoutStyle.Flow> rozložení jsou následující:  
  
-   Všechny funkce <xref:System.Windows.Forms.TableLayoutPanel> vrstvou <xref:System.Windows.Forms.ToolStrip.LayoutSettings%2A> vlastnost. Musíte přetypovat <xref:System.Windows.Forms.LayoutSettings> třídu <xref:System.Windows.Forms.TableLayoutSettings> třídy.  
  
-   Můžete použít <xref:System.Windows.Forms.ToolStripItem.Dock%2A> a <xref:System.Windows.Forms.ToolStripItem.Anchor%2A> vlastností v kódu pro zarovnání položek v rámci buňky tabulky.  
  
-   <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Vlastnost se ignoruje.  
  
-   V <xref:System.Windows.Forms.ToolStrip.LayoutCompleted> události, si můžete prohlédnout <xref:System.Windows.Forms.ToolStripItem.Placement%2A> a určí, zda byl umístěn položky na hlavní <xref:System.Windows.Forms.ToolStrip> nebo nevejdou.  
  
-   Úchytu není vykresleno a proto <xref:System.Windows.Forms.ToolStrip> v <xref:System.Windows.Forms.ToolStripLayoutStyle.Table> styl rozložení v <xref:System.Windows.Forms.ToolStripPanel> nelze přesunout.  
  
-   <xref:System.Windows.Forms.ToolStrip> Tlačítku přetečení není vykresleno, a <xref:System.Windows.Forms.ToolStripItem.Overflow%2A> se ignoruje.  
  
## <a name="toolstripitem"></a>ToolStripItem  
 Následující témata popisují <xref:System.Windows.Forms.ToolStripItem> a ovládací prvky, které jsou odvozeny z něj.  
  
 <xref:System.Windows.Forms.ToolStripItem> je abstraktní základní třída pro všechny položky, které <xref:System.Windows.Forms.ToolStrip>. Následující objekt modelu ukazuje <xref:System.Windows.Forms.ToolStripItem> hierarchii dědičnosti.  
  
 ![Diagram, který je znázorněn objektový model prvku ToolStripItem.](./media/toolstrip-control-architecture/toolstripitem-object-model.gif)  
  
 <xref:System.Windows.Forms.ToolStripItem> buď dědí přímo z třídy <xref:System.Windows.Forms.ToolStripItem>, nebo nepřímo dědí z <xref:System.Windows.Forms.ToolStripItem> prostřednictvím <xref:System.Windows.Forms.ToolStripControlHost> nebo <xref:System.Windows.Forms.ToolStripDropDownItem>.  
  
 <xref:System.Windows.Forms.ToolStripItem> musí být součástí ovládacích prvků <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, <xref:System.Windows.Forms.StatusStrip>, nebo <xref:System.Windows.Forms.ContextMenuStrip> a nelze jej přidat přímo do formuláře. Různé třídy kontejnerů jsou navržené tak, aby obsahovala příslušnou podmnožinu <xref:System.Windows.Forms.ToolStripItem> ovládacích prvků.  
  
 V následující tabulce jsou uvedeny skladě <xref:System.Windows.Forms.ToolStripItem> ovládací prvky a kontejnery, ve kterých vypadat nejlepší. I když některé <xref:System.Windows.Forms.ToolStrip> položky mohou být hostovány v libovolném <xref:System.Windows.Forms.ToolStrip>-odvozené kontejneru, tyto položky byly navrženy vás pod rouškou nejlepší v následujících kontejnerech:  
  
> [!NOTE]
>  <xref:System.Windows.Forms.ToolStripDropDown> nezobrazí se na panelu nástrojů návrháře.  
  
|Obsažené položky|ToolStrip|MenuStrip|ContextMenuStrip|StatusStrip|ToolStripDropDown|  
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
  
### <a name="toolstripbutton"></a>ToolStripButton  
 <xref:System.Windows.Forms.ToolStripButton> je položka tlačítka pro <xref:System.Windows.Forms.ToolStrip>. Které můžete zobrazit pomocí různých stylů ohraničení a slouží k reprezentaci a aktivaci provozní stavy. Můžete také definovat tam chcete mít fokus ve výchozím nastavení.  
  
### <a name="toolstriplabel"></a>ToolStripLabel  
 <xref:System.Windows.Forms.ToolStripLabel> Poskytuje funkce popisek v <xref:System.Windows.Forms.ToolStrip> ovládací prvky. <xref:System.Windows.Forms.ToolStripLabel> Je stejná jako <xref:System.Windows.Forms.ToolStripButton> , která ve výchozím nastavení nezíská fokus a není vykreslí jako vložené nebo zvýrazněné.  
  
 <xref:System.Windows.Forms.ToolStripLabel> jako hostovaná položka podporuje přístupové klíče.  
  
 Použití <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.LinkVisited%2A>, a <xref:System.Windows.Forms.LinkLabel.LinkBehavior%2A> vlastnosti <xref:System.Windows.Forms.ToolStripLabel> pro podporu ovládací prvek odkazu v <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripstatuslabel"></a>ToolStripStatusLabel  
 <xref:System.Windows.Forms.ToolStripStatusLabel> verze <xref:System.Windows.Forms.ToolStripLabel> určený speciálně pro použití v <xref:System.Windows.Forms.StatusStrip>. Speciální funkce zahrnují <xref:System.Windows.Forms.ToolStripStatusLabel.BorderStyle%2A>, <xref:System.Windows.Forms.ToolStripStatusLabel.BorderSides%2A>, a <xref:System.Windows.Forms.ToolStripStatusLabel.Spring%2A>.  
  
### <a name="toolstripseparator"></a>ToolStripSeparator  
 <xref:System.Windows.Forms.ToolStripSeparator> Přidá nový řádek svislý nebo vodorovný do panelu nástrojů nebo nabídky, v závislosti na orientaci. Poskytuje seskupení nebo rozdíl mezi položkami, jako jsou ty v nabídce.  
  
 Můžete přidat <xref:System.Windows.Forms.ToolStripSeparator> v době návrhu výběrem z rozevíracího seznamu. Ale můžete také automaticky vytvořit <xref:System.Windows.Forms.ToolStripSeparator> zadáním pomlčkou (-) v návrháře šablony uzlu nebo v <xref:System.Windows.Forms.ToolStripItemCollection.Add%2A> metoda.  
  
### <a name="toolstripcontrolhost"></a>ToolStripControlHost  
 <xref:System.Windows.Forms.ToolStripControlHost> je abstraktní základní třída pro <xref:System.Windows.Forms.ToolStripComboBox>, <xref:System.Windows.Forms.ToolStripTextBox>, a <xref:System.Windows.Forms.ToolStripProgressBar>. <xref:System.Windows.Forms.ToolStripControlHost> Můžete hostovat další ovládací prvky, včetně vlastních ovládacích prvků, dvěma způsoby:  
  
-   Vytvoření <xref:System.Windows.Forms.ToolStripControlHost> s třídou, která je odvozena z <xref:System.Windows.Forms.Control>. K úplnému přístupu k vlastnosti hostovaného ovládacího prvku a, musíte přetypovat <xref:System.Windows.Forms.ToolStripControlHost.Control%2A> vlastnost zpět na skutečné třídě představuje.  
  
-   Rozšíření <xref:System.Windows.Forms.ToolStripControlHost>a ve zděděné třídě výchozí konstruktor, volání konstruktoru základní třídy, které jsou předávání, která je odvozena z třídy <xref:System.Windows.Forms.Control>. Tato možnost umožňuje zabalit běžné ovládací prvek metody a vlastnosti pro usnadnění přístupu v <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripcombobox"></a>ToolStripComboBox  
 <xref:System.Windows.Forms.ToolStripComboBox> je <xref:System.Windows.Forms.ComboBox> optimalizována pro hostování v <xref:System.Windows.Forms.ToolStrip>. Podmnožinu hostovaného ovládacího prvku vlastnosti a události jsou vystaveny na <xref:System.Windows.Forms.ToolStripComboBox> úroveň, ale základní <xref:System.Windows.Forms.ComboBox> ovládací prvek je plně přístupné prostřednictvím <xref:System.Windows.Forms.ToolStripComboBox.ComboBox%2A> vlastnost.  
  
### <a name="toolstriptextbox"></a>ToolStripTextBox  
 <xref:System.Windows.Forms.ToolStripTextBox> je <xref:System.Windows.Forms.TextBox> optimalizována pro hostování v <xref:System.Windows.Forms.ToolStrip>. Podmnožinu hostovaného ovládacího prvku vlastnosti a události jsou vystaveny na <xref:System.Windows.Forms.ToolStripTextBox> úroveň, ale základní <xref:System.Windows.Forms.TextBox> ovládací prvek je plně přístupné prostřednictvím <xref:System.Windows.Forms.ToolStripTextBox.TextBox%2A> vlastnost.  
  
### <a name="toolstripprogressbar"></a>ToolStripProgressBar  
 <xref:System.Windows.Forms.ToolStripProgressBar> je <xref:System.Windows.Forms.ProgressBar> optimalizována pro hostování v <xref:System.Windows.Forms.ToolStrip>. Podmnožinu hostovaného ovládacího prvku vlastnosti a události jsou vystaveny na <xref:System.Windows.Forms.ToolStripProgressBar> úroveň, ale základní <xref:System.Windows.Forms.ProgressBar> ovládací prvek je plně přístupné prostřednictvím <xref:System.Windows.Forms.ToolStripProgressBar.ProgressBar%2A> vlastnost.  
  
### <a name="toolstripdropdownitem"></a>ToolStripDropDownItem  
 <xref:System.Windows.Forms.ToolStripDropDownItem> je abstraktní základní třída pro <xref:System.Windows.Forms.ToolStripMenuItem>, <xref:System.Windows.Forms.ToolStripDropDownButton>, a <xref:System.Windows.Forms.ToolStripSplitButton>, což může být hostitelem položek přímo nebo hostitele dalších položek v rozevíracím seznamu kontejneru. To provedete tak, že nastavíte <xref:System.Windows.Forms.ToolStripDropDownItem.DropDown%2A> vlastnost <xref:System.Windows.Forms.ToolStripDropDown> a nastavení <xref:System.Windows.Forms.ToolStrip.Items%2A> vlastnost <xref:System.Windows.Forms.ToolStripDropDown>. Přístup k těchto přímo pomocí rozevíracího seznamu položek <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItems%2A> vlastnost.  
  
### <a name="toolstripmenuitem"></a>ToolStripMenuItem  
 <xref:System.Windows.Forms.ToolStripMenuItem> je <xref:System.Windows.Forms.ToolStripDropDownItem> , který funguje s <xref:System.Windows.Forms.ToolStripDropDownMenu> a <xref:System.Windows.Forms.ContextMenuStrip> zpracovat speciální uspořádání zvýrazňování, rozložení a sloupec pro nabídky.  
  
### <a name="toolstripdropdownbutton"></a>ToolStripDropDownButton  
 <xref:System.Windows.Forms.ToolStripDropDownButton> vypadá podobně jako <xref:System.Windows.Forms.ToolStripButton>, ale zobrazuje oblasti rozevíracího seznamu, když na něj uživatel klikne. Skrytí nebo zobrazení tak, že nastavíte na šipku rozevíracího seznamu <xref:System.Windows.Forms.ToolStripDropDownButton.ShowDropDownArrow%2A> vlastnost. <xref:System.Windows.Forms.ToolStripDropDownButton> hostitelé <xref:System.Windows.Forms.ToolStripOverflowButton> , který zobrazí položky, které přetečení <xref:System.Windows.Forms.ToolStrip>.  
  
### <a name="toolstripsplitbutton"></a>Prvku ToolStripSplitButton  
 <xref:System.Windows.Forms.ToolStripSplitButton> kombinuje funkcí tlačítko rozevíracího seznamu a tlačítko.  
  
 Použití <xref:System.Windows.Forms.ToolStripSplitButton.DefaultItem%2A> vlastnost synchronizovat <xref:System.Windows.Forms.Control.Click> událostí vybraná položka rozevírací seznam s položkou zobrazovaný na tlačítku.  
  
### <a name="toolstripitem-generic-features"></a>Funkce obecného prvku ToolStripItem  
 <xref:System.Windows.Forms.ToolStripItem> poskytuje následující obecné funkce a možnosti pro dědění ovládacích prvků:  
  
-   Základní události  
  
-   Zpracování obrázků  
  
-   Zarovnání  
  
-   Textové a obrázkové vztah  
  
-   Styl zobrazení  
  
#### <a name="core-events"></a>Základní události  
 <xref:System.Windows.Forms.ToolStripItem> ovládací prvky zobrazí vlastní malířského událostí, myši a klikněte na tlačítko a můžete provádět některé klávesnice předzpracování také.  
  
#### <a name="image-handling"></a>Zpracování obrázků  
 <xref:System.Windows.Forms.ToolStripItem.Image%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageAlign%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageIndex%2A>, <xref:System.Windows.Forms.ToolStripItem.ImageKey%2A>, A <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> vlastnosti se vztahují na různé aspekty zpracování obrázku. Použití imagí v <xref:System.Windows.Forms.ToolStrip> ovládacích prvků tak, že nastavíte tyto vlastnosti přímo nebo nastavením na spuštění čas – jen <xref:System.Windows.Forms.ToolStrip.ImageList%2A> vlastnost.  
  
 Změna měřítka obrázku se určuje podle interakce vlastnosti v obou <xref:System.Windows.Forms.ToolStrip> a <xref:System.Windows.Forms.ToolStripItem>, následujícím způsobem:  
  
-   <xref:System.Windows.Forms.ToolStrip.ImageScalingSize%2A> škálování finální image určené kombinací na obrázku je <xref:System.Windows.Forms.ToolStripItem.ImageScaling%2A> nastavení a kontejneru <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> nastavení.  
  
    -   Pokud <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> je `true` (výchozí) a <xref:System.Windows.Forms.ToolStripItemImageScaling> je <xref:System.Windows.Forms.ToolStripItemImageScaling.SizeToFit>, dojde k žádné image škálování a <xref:System.Windows.Forms.ToolStrip> velikost je největší položky nebo předepsané minimální velikost.  
  
    -   Pokud <xref:System.Windows.Forms.ToolStrip.AutoSize%2A> je `false` a <xref:System.Windows.Forms.ToolStripItemImageScaling> je <xref:System.Windows.Forms.ToolStripItemImageScaling.None>, ani image ani <xref:System.Windows.Forms.ToolStrip> škálování nastane.  
  
#### <a name="alignment"></a>Zarovnání  
 Hodnota <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> vlastnost určuje konec <xref:System.Windows.Forms.ToolStrip> na které položky se vyskytuje. <xref:System.Windows.Forms.ToolStripItem.Alignment%2A> Vlastnost funguje pouze tehdy, když stylu rozložení ovládacího prvku <xref:System.Windows.Forms.ToolStrip> je nastavena na jednu z hodnot přetečení zásobníku.  
  
 Položky jsou umístěny na <xref:System.Windows.Forms.ToolStrip> v pořadí, ve kterém se zobrazí položky v kolekci položek. Chcete-li programově změnit, kde je rozloží položku, použijte <xref:System.Windows.Forms.ToolStripItemCollection.Insert%2A> metoda přesunout položku v kolekci. Tato metoda přesune položku, ale není duplicitní.  
  
#### <a name="text-and-image-relationship"></a>Text a obrázek vztahů  
 <xref:System.Windows.Forms.ToolStripItem.TextImageRelation%2A> Vlastnost definuje relativní umístění obrázku vzhledem k textu na <xref:System.Windows.Forms.ToolStripItem>. Položky, které nemají bitovou kopii, text nebo obě jsou považovány za zvláštní případy tak, aby <xref:System.Windows.Forms.ToolStripItem> nejsou zobrazeny na prázdné místo pro chybějící prvek nebo prvky.  
  
#### <a name="display-style"></a>Styl zobrazení  
 <xref:System.Windows.Forms.ToolStripItem.DisplayStyle%2A> Umožňuje nastavit hodnoty vlastností textových a obrázkových položky při zobrazení pouze to, co chcete. To se obvykle používá při zobrazování jedné položce v jiném kontextu změnit styl zobrazení.  
  
## <a name="accessory-classes"></a>Příslušenství třídy  
 Třídy, které poskytují různé další funkce patří:  
  
-   <xref:System.Windows.Forms.ToolStripManager> podporuje <xref:System.Windows.Forms.ToolStrip>-související úkoly pro celé aplikace, jako jsou možnosti sloučení, nastavení a nástroj pro vykreslování.  
  
-   <xref:System.Windows.Forms.ToolStripRenderer> umožňuje použití konkrétního stylu nebo motivu <xref:System.Windows.Forms.ToolStrip> snadno.  
  
-   <xref:System.Windows.Forms.ToolStripProfessionalRenderer> Vytvoří pera a na základě tabulky replaceable barvy štětce (<xref:System.Windows.Forms.ProfessionalColorTable>).  
  
-   <xref:System.Windows.Forms.ToolStripSystemRenderer> systémové barvy a fixní vizuální styl, který se vztahuje <xref:System.Windows.Forms.ToolStrip> aplikací.  
  
-   <xref:System.Windows.Forms.ToolStripContainer> je podobný <xref:System.Windows.Forms.SplitContainer>. Používá čtyři ukotvených boční panely (instance <xref:System.Windows.Forms.ToolStripPanel>) a jeden středovém panelu (instance <xref:System.Windows.Forms.ToolStripContentPanel>) k vytvoření typické uspořádání. Boční panely nelze odebrat, ale je můžete skrýt. Nelze odebrat ani skrýt středovém panelu. Můžete uspořádat jeden nebo více <xref:System.Windows.Forms.ToolStrip>, <xref:System.Windows.Forms.MenuStrip>, nebo <xref:System.Windows.Forms.StatusStrip> ovládacích prvků v boční panely kde můžete použít středovém panelu. pro další ovládací prvky. <xref:System.Windows.Forms.ToolStripContentPanel> Také poskytuje způsob, jak získat podporu nástroj pro vykreslování do těla formuláře pro jednotný vzhled. <xref:System.Windows.Forms.ToolStripContainer> nepodporuje rozhraní více dokumentů (MDI).  
  
-   <xref:System.Windows.Forms.ToolStripPanel> poskytuje prostor pro přesun a uspořádání <xref:System.Windows.Forms.ToolStrip> ovládacích prvků. Pokud se tak rozhodnete, můžete použít pouze jeden panel a <xref:System.Windows.Forms.ToolStripPanel> funguje dobře ve scénářích MDI.  
  
## <a name="see-also"></a>Viz také:
- [Přehled ovládacího prvku ToolStrip](toolstrip-control-overview-windows-forms.md)
- [Shrnutí technologie ToolStrip](toolstrip-technology-summary.md)
- [Ovládací prvek ToolStrip](toolstrip-control-windows-forms.md)
- [Ovládací prvek MenuStrip](menustrip-control-windows-forms.md)
- [Ovládací prvek StatusStrip](statusstrip-control.md)
- [Ovládací prvek ContextMenuStrip](contextmenustrip-control.md)
- [Ovládací prvek BindingNavigator](bindingnavigator-control-windows-forms.md)
