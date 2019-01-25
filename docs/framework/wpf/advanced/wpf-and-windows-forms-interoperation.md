---
title: Vzájemná spolupráce subsystémů WPF a Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
ms.openlocfilehash: e6bbf6aea1a98b7e1497101ea6a6121525f1c87f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54732021"
---
# <a name="wpf-and-windows-forms-interoperation"></a>Vzájemná spolupráce subsystémů WPF a Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] představovat dvě různé architektury pro vytvoření rozhraní aplikací. <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> Obor názvů obsahuje třídy, které umožňují běžné scénáře vzájemné spolupráce. Jsou dvě klíčové třídy, které implementují součinnosti možnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost>. Toto téma popisuje, jaké součinnosti scénáře jsou podporovány a jaké scénáře nejsou podporovány.  
  
> [!NOTE]
>  Zvláštní ohledy na *hybridní ovládací prvek* scénář. Hybridní ovládací prvek má ovládací prvek z jedné technologie vnořen do ovládacího prvku z jiné technologie. To se také nazývá *vnořené vzájemná spolupráce grafického subsystému*. A *víceúrovňové hybridní ovládací prvek* má více než jednu úroveň hybridní ovládací prvek vnoření. Je například víceúrovňové vnořené vzájemná spolupráce [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek, který obsahuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek, který obsahuje další [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku. Víceúrovňové hybridní ovládací prvky nejsou podporovány.  
  
  
<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>Ovládací prvky hostování Windows Forms v subsystému WPF  
 Jsou podporovány následující scénáře vzájemné spolupráce při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek hostuje ovládací prvek formuláře Windows:  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Ovládací prvek může hostovat jeden nebo více [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky pomocí XAML.  
  
-   Může hostovat jeden nebo více [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky pomocí kódu.  
  
-   Může hostovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky kontejneru, které obsahují jiné [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků.  
  
-   To může být hostitelem hlavního/podrobného formuláře pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hlavní a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] podrobnosti.  
  
-   To může být hostitelem hlavního/podrobného formuláře pomocí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hlavní a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podrobnosti.  
  
-   Může hostovat jeden nebo více [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] ovládacích prvků.  
  
-   To může hostovat jeden nebo více složených ovládacích prvků.  
  
-   To může být hostitelem hybridní ovládacích prvků pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
-   To může být hostitelem hybridní ovládacích prvků pomocí kódu.  
  
### <a name="layout-support"></a>Podpora rozložení  
 Následující seznam popisuje známých omezeních při <xref:System.Windows.Forms.Integration.WindowsFormsHost> element pokusí integrovat své prostředí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] systém rozložení.  
  
-   V některých případech [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nelze změnit velikost nebo můžou mít velikost pouze na určité dimenze. Například [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> ovládací prvek podporuje pouze jeden výšku, které jsou definovány pomocí ovládacího prvku velikost písma. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dynamického rozložení, který předpokládá, že prvky můžete roztáhnout svisle, hostovaný <xref:System.Windows.Forms.ComboBox> ovládací prvek nebude roztáhnout podle očekávání.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nelze otáčet nebo zešikmená. Například pokud vaše uživatelské rozhraní otočíte o 90 stupňů, hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky se zachovávají původní pozice vzhůru.  
  
-   Ve většině případů [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků nepodporují proporcionální škálování. I když bude možné škálovat celkové rozměry ovládacího prvku podřízených ovládacích prvků a komponent ovládacího prvku nemusí měnit velikost podle očekávání. Toto omezení závisí na tom, jak dobře se každý [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek podporuje škálování.  
  
-   V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uživatelského rozhraní, můžete změnit pořadí vykreslování prvků překrývající se chování ovládacího prvku. Hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek vykreslen v samostatných HWND, takže je vždy vykreslován nad [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řídí podporu automatického škálování na základě velikosti písma. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uživatelské rozhraní, změna velikosti písma se velikost celé rozložení, i když může dynamicky velikost jednotlivých prvků.  
  
### <a name="ambient-properties"></a>Vedlejším vlastnostem  
 Některé vlastnosti prostředí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky mají [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ekvivalenty. Tyto vlastnosti prostředí se rozšíří na hostovanou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky a vystavený jako veřejné vlastnosti na <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Ovládací prvek přeloží každý [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vedlejší vlastnost do jeho [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ekvivalentní.  
  
 Další informace najdete v tématu [Windows Forms a WPF vlastnost mapování](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Chování  
 Následující tabulka popisuje součinnosti chování.  
  
|Chování|Podporováno|Nepodporováno|  
|--------------|---------------|-------------------|  
|Průhlednost|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vykreslování ovládacího prvku podporuje průhlednost. Na pozadí nadřazeného objektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek se může stát na pozadí hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků.|Některé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků nepodporují průhlednost. Například <xref:System.Windows.Forms.TextBox> a <xref:System.Windows.Forms.ComboBox> ovládacích prvků nesmí být transparentní, když jsou hostované ve [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Procházení tabulátorem|Pořadí pro hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků je stejný jako při tyto ovládací prvky hostují v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]– aplikace založené na.<br /><br /> Procházení tabulátorem z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] mít pod kontrolou [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacím prvkem klávesu TAB a klávesy SHIFT + TAB funguje jako obvykle.<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, které mají <xref:System.Windows.Forms.Control.TabStop%2A> hodnotou vlastnosti `false` neobdrží fokus, když uživatel karty prostřednictvím ovládacích prvků.<br /><br /> -Každá <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek má <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> hodnotu, která určuje, zda, který <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, které jsou obsaženy v <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontejneru podle pořadí zadaném <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost. Procházení tabulátorem z poslední pořadové umístí fokus na další [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek, pokud existuje. Pokud žádné jiné focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek existuje, vrátí první tabulátor [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek v pořadí karet.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> hodnoty pro ovládací prvky uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost> jsou relativní vzhledem k na stejné úrovni [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, které jsou součástí <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.<br />-Tabulátor respektuje chování specifické pro ovládací prvek. Například stisknutím klávesy TAB v <xref:System.Windows.Forms.TextBox> ovládací prvek, který má <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> hodnotou vlastnosti `true` zadá na kartě v textovém poli namísto Přesun fokusu.|Nelze použít.|  
|Navigace pomocí kláves se šipkami|– Navigace s šipkou klíče do <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek je stejný jako běžný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku kontejneru: Šipka nahoru a šipka vlevo vyberte předchozí ovládací prvek a vyberte klávesy Šipka dolů a šipka vpravo na další ovládací prvek.<br />– NAHORU kláves ŠIPKA a šipka doleva z první ovládací prvek, který je součástí <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek provést stejnou akci, jako klávesovou zkratku SHIFT + TAB. Pokud je focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek fokus přesunete mimo <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku. Toto chování se liší od standardu <xref:System.Windows.Forms.ContainerControl> v dané žádné obtékání poslední ovládací prvek chování. Pokud žádné jiné focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existuje ovládací prvek fokus vrátí poslední [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek v pořadí karet.<br />– DOLŮ kláves ŠIPKA a šipka doprava z poslední ovládací prvek, který je součástí <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek provést stejnou akci jako klávesu TAB. Pokud je focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek fokus přesunete mimo <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku. Toto chování se liší od standardu <xref:System.Windows.Forms.ContainerControl> v dané Nezalamovat první ovládací prvek chování. Pokud žádné jiné focusable [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] existuje ovládací prvek fokus vrátí do první [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek v pořadí karet.|Nelze použít.|  
|Akcelerátory|Akcelerátory fungovat obvyklým způsobem, není uvedeno ve sloupci "Nepodporuje".|Duplicitním akcelerátorům napříč technologie jako běžný duplicitním akcelerátorům nefungují. Když akcelerátoru je duplicitní v rámci technologie s alespoň jednou na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku a druhá v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek dostane vždy akcelerátoru. Fokus není přepínat mezi ovládacími prvky, když se stiskne duplicitní akcelerátoru.|  
|Klávesové zkratky|Klávesové zkratky fungují jako obvykle není uvedeno ve sloupci "Nepodporuje".|-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] klávesové zkratky, které jsou zpracovávány ve fázi předběžného zpracování vždy přednost před [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klávesových zkratek. Například, pokud máte <xref:System.Windows.Forms.ToolStrip> ovládacím prvkem klávesové zkratky CTRL + S definována a je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] příkaz vázán na kombinaci kláves CTRL + S, <xref:System.Windows.Forms.ToolStrip> obslužná rutina ovládacího prvku je vždy vyvolán první, bez ohledu na to fokus.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] klávesové zkratky, které jsou zpracovávány <xref:System.Windows.Forms.Control.KeyDown> události jsou zpracována jako poslední v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Toto chování můžete zabránit tak, že přepíšete [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku <xref:System.Windows.Forms.Control.IsInputKey%2A> metody nebo zpracování <xref:System.Windows.Forms.Control.PreviewKeyDown> událostí. Vrátí `true` z <xref:System.Windows.Forms.Control.IsInputKey%2A> metodu, nebo nastavte hodnotu <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> vlastnost `true` v vaše <xref:System.Windows.Forms.Control.PreviewKeyDown> obslužné rutiny události.|  
|AcceptsReturn AcceptsTabs a jiné chování specifické pro ovládací prvek|Vlastnosti, které se mění výchozí chování klávesnice fungovat obvyklým způsobem, za předpokladu, že [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řídit přepsání <xref:System.Windows.Forms.Control.IsInputKey%2A> metoda vrátí `true`.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, které se mění výchozí chování klávesnice pomocí manipulace <xref:System.Windows.Forms.Control.KeyDown> události jsou zpracována jako poslední v hostitelském [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku. Protože tyto ovládací prvky jsou zpracována jako poslední, může vést k neočekávanému chování.|  
|O vstupu a opuštění události|Kdy se chystá obsahující fokus <xref:System.Windows.Forms.Integration.ElementHost> řídit, zadejte a nechte události jsou vyvolány jako obvykle při změně fokusu v jediném <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.|Zadejte a nechte události nejsou započteny, když dojde k následujícím změnám zaměření:<br /><br /> -Od vnitřní mimo <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.<br />-Od mimo k uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.<br />-Mimo <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.<br />-Z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek hostované v <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek je hostován uvnitř stejné <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|  
|Multithreading|Všechny typy prvků multithreading jsou podporovány.|Jak [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] technologie předpokládají modelu s jedním vláknem souběžnosti. Volání rozhraní framework objekty z jiných vláken během ladění, vyvolá výjimku k vynucení tento požadavek.|  
|Zabezpečení|Všechny vzájemné spolupráce scénáře vyžadují úplný vztah důvěryhodnosti.|Žádné vzájemné spolupráce scénáře jsou povoleny v částečném vztahu důvěryhodnosti.|  
|Usnadnění|Podporují se všechny scénáře usnadnění přístupu. Produkty technologií usnadnění fungovat správně při použití pro hybridní aplikace, které obsahují [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Nelze použít.|  
|Schránka|Všechny operace se schránkou fungovat obvyklým způsobem. To zahrnuje vyjímání a vkládání mezi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Nelze použít.|  
|Funkce přetažení myší|Všechny operace přetažení myší fungovat obvyklým způsobem. Patří sem operace mezi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Nelze použít.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hostování ovládacích prvků WPF v modelu Windows Forms  
 Při hostitele ovládacího prvku Windows Forms jsou podporovány následující scénáře vzájemné spolupráce [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku:  
  
-   Hostující jednu nebo více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky pomocí kódu.  
  
-   Přiřazení vlastnosti list s jedním nebo více hostovaných [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků.  
  
-   Hostující jednu nebo více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky ve formuláři.  
  
-   Spouští se [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okna.  
  
-   Hostování hlavního/podrobného formuláře pomocí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hlavní a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podrobnosti.  
  
-   Hostování hlavního/podrobného formuláře pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hlavní a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] podrobnosti.  
  
-   Vlastní hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků.  
  
-   Hostování ovládacích prvků hybridní.  
  
### <a name="ambient-properties"></a>Vedlejším vlastnostem  
 Některé vlastnosti prostředí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky mají [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekvivalenty. Tyto vlastnosti prostředí se rozšíří na hostovanou [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky a vystavený jako veřejné vlastnosti na <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku. <xref:System.Windows.Forms.Integration.ElementHost> Ovládací prvek přeloží každý [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] vedlejší vlastnost k jeho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekvivalentní.  
  
 Další informace najdete v tématu [Windows Forms a WPF vlastnost mapování](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Chování  
 Následující tabulka popisuje součinnosti chování.  
  
|Chování|Podporováno|Nepodporováno|  
|--------------|---------------|-------------------|  
|Průhlednost|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vykreslování ovládacího prvku podporuje průhlednost. Na pozadí nadřazeného objektu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek se může stát na pozadí hostované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků.|Nelze použít.|  
|Multithreading|Všechny typy prvků multithreading jsou podporovány.|Jak [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] technologie předpokládají modelu s jedním vláknem souběžnosti. Volání rozhraní framework objekty z jiných vláken během ladění, vyvolá výjimku k vynucení tento požadavek.|  
|Zabezpečení|Všechny vzájemné spolupráce scénáře vyžadují úplný vztah důvěryhodnosti.|Žádné vzájemné spolupráce scénáře jsou povoleny v částečném vztahu důvěryhodnosti.|  
|Usnadnění|Podporují se všechny scénáře usnadnění přístupu. Produkty technologií usnadnění fungovat správně při použití pro hybridní aplikace, které obsahují [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Nelze použít.|  
|Schránka|Všechny operace se schránkou fungovat obvyklým způsobem. To zahrnuje vyjímání a vkládání mezi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Nelze použít.|  
|Funkce přetažení myší|Všechny operace přetažení myší fungovat obvyklým způsobem. Patří sem operace mezi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Nelze použít.|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [Návod: Hostování ovládacího prvku Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího Windows Forms v subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)
- [Návod: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)
- [Mapování vlastnosti Windows Forms a WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
