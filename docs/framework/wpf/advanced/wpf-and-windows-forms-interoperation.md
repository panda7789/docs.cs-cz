---
title: "Vzájemná spolupráce subsystémů WPF a Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms [WPF], interoperability with
- nester interoperation [WPF]
- Windows Forms [WPF], WPF interoperation
- interoperability [WPF], Windows Forms
- hybrid control [WPF interoperability]
ms.assetid: 9e8aa6b6-112c-4579-98d1-c974917df499
caps.latest.revision: "23"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d713a03469edc5d4c950c75c8094386372657486
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="wpf-and-windows-forms-interoperation"></a>Vzájemná spolupráce subsystémů WPF a Windows Forms
[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] k dispozici dvě různé architektury pro vytváření aplikací rozhraní. <xref:System.Windows.Forms.Integration?displayProperty=nameWithType> Obor názvů obsahuje třídy, které umožňují součinnosti běžné scénáře. Jsou dva klíče třídy, které implementují součinnosti možnosti <xref:System.Windows.Forms.Integration.WindowsFormsHost> a <xref:System.Windows.Forms.Integration.ElementHost>. Toto téma popisuje, jaké součinnosti scénáře jsou podporovány a jaké scénáře nejsou podporované.  
  
> [!NOTE]
>  Obzvláštní pozornost je uveden *hybridní řízení* scénář. Ovládací prvek hybridní obsahuje ovládacího prvku z jedné technologie vnořené v ovládacím prvku z jiné technologie. To se označuje taky jako *vnořené vzájemná spolupráce*. A *víceúrovňové hybridní řízení* má více než jednu úroveň hybridní řízení vnoření. Je například víceúrovňové vnořené vzájemná spolupráce [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek, který obsahuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek, který obsahuje jiné [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku. Ovládací prvky víceúrovňové hybridní nejsou podporovány.  
  
  
<a name="Windows_Presentation_Foundation_Application_Hosting"></a>   
## <a name="hosting-windows-forms-controls-in-wpf"></a>Hostování Windows Forms – ovládací prvky v grafickém subsystému WPF  
 Podporovány jsou následující scénáře součinnosti při [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řídit, hostitele [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] ovládacího prvku:  
  
-   [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Řízení může hostovat jeden nebo více [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky pomocí XAML.  
  
-   Může hostovat, jeden nebo více [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky pomocí kódu.  
  
-   Může hostovat [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky kontejneru, které obsahují další [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky.  
  
-   Může být hostitelem hlavního a podrobného formuláře pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hlavní a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] podrobnosti.  
  
-   Může být hostitelem hlavního a podrobného formuláře pomocí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hlavní a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podrobnosti.  
  
-   Může hostovat, jeden nebo více [!INCLUDE[TLA2#tla_actx](../../../../includes/tla2sharptla-actx-md.md)] ovládací prvky.  
  
-   Jeden nebo více složené ovládací prvky se může hostovat.  
  
-   Ho může hostovat hybridní ovládacích prvků pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
-   Ho může hostovat hybridní ovládacích prvků pomocí kódu.  
  
### <a name="layout-support"></a>Podpora rozložení  
 Následující seznam popisuje známá omezení při <xref:System.Windows.Forms.Integration.WindowsFormsHost> element pokusí integrovat jeho hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení do [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] rozložení systému.  
  
-   V některých případech [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nelze změnit velikost nebo může být dimenzovány pouze pro konkrétní dimenze. Například [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] <xref:System.Windows.Forms.ComboBox> řízení podporuje pouze jeden výška, který je definovaný velikost písma ovládacího prvku. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] dynamické rozložení, který se předpokládá, že elementy lze roztáhnout ve svislém směru hostovaný <xref:System.Windows.Forms.ComboBox> řízení nebude stretch podle očekávání.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládací prvky nelze otáčet nebo nesouměrně rozdělí. Například při otočení uživatelské rozhraní o 90 stupňů, hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky se zachovávají původní pozice výšku.  
  
-   Ve většině případů [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nepodporují přímo úměrná škálování. I když bude škálovat celkové rozměry ovládacího prvku, podřízené ovládací prvky a součásti elementy ovládacího prvku nesmí změnit velikost podle očekávání. Toto omezení závisí na tom, jak dobře každý [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení podporuje škálování.  
  
-   V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uživatelské rozhraní, můžete změnit pořadí vykreslování elementů na ovládací prvek překrývání chování. Hostovaný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení se vykresluje v samostatných HWND, takže je vždy vykreslován na [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] elementy.  
  
-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládací prvky podporují automatické škálování podle velikost písma. V [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] uživatelské rozhraní, změny velikosti písma není změnit velikost celého rozložení, i když může dynamicky změnit velikost jednotlivých elementů.  
  
### <a name="ambient-properties"></a>Vedlejším vlastnostem  
 Některé vlastnosti prostředí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacích prvků mají [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ekvivalenty. Tyto vlastnosti prostředí rozšířeny do hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky a zveřejněné jako veřejné vlastnosti na <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku. <xref:System.Windows.Forms.Integration.WindowsFormsHost> Řízení překládá každý [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] vedlejším vlastnosti do její [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ekvivalentní.  
  
 Další informace najdete v tématu [Windows Forms a mapování vlastností WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Chování  
 Následující tabulka popisuje součinnosti chování.  
  
|Chování|Podporováno|Nepodporováno|  
|--------------|---------------|-------------------|  
|Průhlednost|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]vykreslování ovládacího prvku podporuje průhlednost. Na pozadí nadřazeného objektu [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řízení se může stát pozadí hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky.|Některé [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky nepodporují průhlednost. Například <xref:System.Windows.Forms.TextBox> a <xref:System.Windows.Forms.ComboBox> ovládací prvky nebudou transparentní, pokud je hostováno pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].|  
|Použití tabulátoru|Pořadí karet pro hostované [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky je stejný jako při tyto ovládací prvky jsou hostované v [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]– na základě aplikace.<br /><br /> Použití tabulátoru z [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řídit k [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řídit pomocí klávesy TAB a klávesy SHIFT + TAB funguje jako obvykle.<br /><br /> [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládací prvky, které mají <xref:System.Windows.Forms.Control.TabStop%2A> hodnota vlastnosti `false` ne stane aktivní, když uživatel karty prostřednictvím ovládací prvky.<br /><br /> -Každý <xref:System.Windows.Forms.Integration.WindowsFormsHost> má ovládací prvek <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A> hodnotu, která určuje, kdy které <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládací prvky, které jsou obsaženy v <xref:System.Windows.Forms.Integration.WindowsFormsHost> kontejneru podle pořadí zadaném <xref:System.Windows.Forms.Control.TabIndex%2A> vlastnost. Při příštím procházení tabulátorem z poslední pořadové číslo umístí fokus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řízení, pokud existuje. Pokud žádné jiné může získat fokus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řízení existuje, vrátí na první použití tabulátoru [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek v pořadí.<br />-   <xref:System.Windows.Forms.Integration.WindowsFormsHost.TabIndex%2A>hodnoty pro ovládací prvky uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost> jsou relativní vzhledem k na stejné úrovni [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvky, které jsou součástí <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.<br />-Použití tabulátoru ctí specifické pro řízení chování. Například stisknutím klávesy TAB v <xref:System.Windows.Forms.TextBox> ovládací prvek, který má <xref:System.Windows.Forms.TextBoxBase.AcceptsTab%2A> hodnota vlastnosti `true` vstoupí do textového pole místo přesunutím fokusu na kartě.|Nelze použít.|  
|Navigace pomocí klávesy se šipkami|– Navigace s šipkou klíče do <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládací prvek je stejné jako běžný [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku kontejneru: šipka nahoru nebo šipku vlevo vyberte předchozí ovládacího prvku a klávesy Šipka dolů a šipka vpravo vyberte na další ovládací prvek.<br />-Na až klíče šipku a šipka doleva z první ovládací prvek, který je součástí <xref:System.Windows.Forms.Integration.WindowsFormsHost> řízení provádět stejné akce jako kláves SHIFT + TAB. Pokud dojde může získat fokus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řízení, se aktivuje mimo <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku. Toto chování se liší od standardní <xref:System.Windows.Forms.ContainerControl> v tom, že žádné zabalení na poslední řízení chování. Pokud žádné jiné může získat fokus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řízení existuje, fokus vrátí na poslední [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek v pořadí.<br />-Na dolů šipka a šipka vpravo klíče z poslední ovládací prvek, který je součástí <xref:System.Windows.Forms.Integration.WindowsFormsHost> řízení provádět stejné akce jako klávesy TAB. Pokud dojde může získat fokus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řízení, se aktivuje mimo <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku. Toto chování se liší od standardní <xref:System.Windows.Forms.ContainerControl> chování v tom, že nastane obtékání na první ovládací prvek. Pokud žádné jiné může získat fokus [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] řízení existuje, fokus vrátí do první [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládací prvek v pořadí.|Nelze použít.|  
|Akcelerátorů|Akcelerátorů fungovat obvyklým způsobem, pokud není uvedeno ve sloupci "Nepodporuje" jinak.|Duplicitním akcelerátorům napříč technologie jako obyčejnou duplicitním akcelerátorům nefungují. Když je akcelerátor duplicitní v technologie s alespoň jedním na [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení a druhá v systému [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvek, [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení vždy obdrží akcelerátor. Fokus není přepínání mezi ovládacími prvky při stisknutí duplicitní akcelerátoru.|  
|Klávesové zkratky|Klávesové zkratky fungovat obvyklým způsobem, pokud není uvedeno ve sloupci "Nepodporuje" jinak.|-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]klávesové zkratky, které jsou zpracovávány ve fázi předběžného zpracování vždy mají přednost před [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] klávesové zkratky. Pokud máte například <xref:System.Windows.Forms.ToolStrip> řídit pomocí klávesové zkratky CTRL + S definovaný a je [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] příkaz vázána na CTRL + S <xref:System.Windows.Forms.ToolStrip> obslužná rutina ovládacího prvku je vždy nejdříve volána bez ohledu na fokus.<br />-   [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]klávesové zkratky, které jsou zpracovávány <xref:System.Windows.Forms.Control.KeyDown> v poslední zpracována událost [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]. Toto chování můžete zabránit přepsáním [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacího prvku <xref:System.Windows.Forms.Control.IsInputKey%2A> metoda nebo zpracování <xref:System.Windows.Forms.Control.PreviewKeyDown> událostí. Vrátí `true` z <xref:System.Windows.Forms.Control.IsInputKey%2A> metoda, nebo nastavte hodnotu <xref:System.Windows.Forms.PreviewKeyDownEventArgs.IsInputKey%2A?displayProperty=nameWithType> vlastnost `true` v vaší <xref:System.Windows.Forms.Control.PreviewKeyDown> obslužné rutiny události.|  
|AcceptsReturn, AcceptsTabs a dalších specifické pro řízení chování|Vlastnosti, které změnit výchozí chování klávesnice fungovat obvyklým způsobem, za předpokladu, který [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení přepsání <xref:System.Windows.Forms.Control.IsInputKey%2A> metoda vrátí `true`.|[!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)]ovládací prvky, které změní výchozí klávesové chování ve zpracování <xref:System.Windows.Forms.Control.KeyDown> události jsou zpracována jako poslední na hostiteli [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku. Protože tyto prvky se zpracovávají poslední, může vést k neočekávanému chování.|  
|Zadejte a nechte události|Pokud není fokus přejdete na obsahující <xref:System.Windows.Forms.Integration.ElementHost> řídit, zadejte a nechte události jsou vyvolány obvyklým při změně fokusu v jediném <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.|Zadejte a nechte události nejsou vyvolá, když dojde k následujícím změnám fokus:<br /><br /> -Z uvnitř k mimo <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.<br />-Z vnějšího k uvnitř <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.<br />-Mimo <xref:System.Windows.Forms.Integration.WindowsFormsHost> ovládacího prvku.<br />-Z [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení hostované v <xref:System.Windows.Forms.Integration.WindowsFormsHost> řídit k <xref:System.Windows.Forms.Integration.ElementHost> řízení hostovanou v rámci stejné <xref:System.Windows.Forms.Integration.WindowsFormsHost>.|  
|Více vláken|Všechny typy multithreading jsou podporovány.|Jak [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] technologie předpokládá modelu jednovláknové souběžnosti. Během ladění, volání framework objektů z jiných vláken vyvolá výjimku vynutit tento požadavek.|  
|Zabezpečení|Všechny součinnosti scénáře vyžadují úplný vztah důvěryhodnosti.|Žádné součinnosti scénáře jsou povoleny v částečné důvěryhodnosti.|  
|Usnadnění|Jsou podporovány ve všech scénářích usnadnění. Produktů využívajících technologie usnadnění fungovat správně, pokud se používá pro hybridní aplikace, které obsahují i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Nelze použít.|  
|Schránka|Všechny operace se schránkou fungovat obvyklým způsobem. To zahrnuje vyjímání a vkládání mezi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Nelze použít.|  
|Funkce a přetažení|Všechny operace přetažení myší fungovat obvyklým způsobem. To zahrnuje operace mezi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Nelze použít.|  
  
<a name="Windows_Forms_Application_Hosting_Windows"></a>   
## <a name="hosting-wpf-controls-in-windows-forms"></a>Hostování ovládacích prvků WPF v rozhraní Windows Forms  
 Podporovány jsou následující scénáře součinnosti při [!INCLUDE[TLA2#tla_winforms](../../../../includes/tla2sharptla-winforms-md.md)] řídit, hostitele [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládacího prvku:  
  
-   Hostující jednu nebo více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky pomocí kódu.  
  
-   Přidružení vlastnost listu s jedním nebo více hostovaných [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.  
  
-   Hostující jednu nebo více [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] stránky ve formuláři.  
  
-   Spuštění [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] okno.  
  
-   Hostování hlavního a podrobného formuláře pomocí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] hlavní a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] podrobnosti.  
  
-   Hostování hlavního a podrobného formuláře pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] hlavní a [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] podrobnosti.  
  
-   Vlastní hostování [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.  
  
-   Hostování ovládacích prvků hybridní.  
  
### <a name="ambient-properties"></a>Vedlejším vlastnostem  
 Některé vlastnosti prostředí [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] ovládacích prvků mají [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekvivalenty. Tyto vlastnosti prostředí rozšířeny do hostované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky a zveřejněné jako veřejné vlastnosti na <xref:System.Windows.Forms.Integration.ElementHost> ovládacího prvku. <xref:System.Windows.Forms.Integration.ElementHost> Řízení překládá každý [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] – vedlejší vlastnost k jeho [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ekvivalentní.  
  
 Další informace najdete v tématu [Windows Forms a mapování vlastností WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md).  
  
### <a name="behavior"></a>Chování  
 Následující tabulka popisuje součinnosti chování.  
  
|Chování|Podporováno|Nepodporováno|  
|--------------|---------------|-------------------|  
|Průhlednost|[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]vykreslování ovládacího prvku podporuje průhlednost. Na pozadí nadřazeného objektu [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] řízení se může stát pozadí hostované [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Nelze použít.|  
|Více vláken|Všechny typy multithreading jsou podporovány.|Jak [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] technologie předpokládá modelu jednovláknové souběžnosti. Během ladění, volání framework objektů z jiných vláken vyvolá výjimku vynutit tento požadavek.|  
|Zabezpečení|Všechny součinnosti scénáře vyžadují úplný vztah důvěryhodnosti.|Žádné součinnosti scénáře jsou povoleny v částečné důvěryhodnosti.|  
|Usnadnění|Jsou podporovány ve všech scénářích usnadnění. Produktů využívajících technologie usnadnění fungovat správně, pokud se používá pro hybridní aplikace, které obsahují i [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Nelze použít.|  
|Schránka|Všechny operace se schránkou fungovat obvyklým způsobem. To zahrnuje vyjímání a vkládání mezi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Nelze použít.|  
|Funkce a přetažení|Všechny operace přetažení myší fungovat obvyklým způsobem. To zahrnuje operace mezi [!INCLUDE[TLA#tla_winforms](../../../../includes/tlasharptla-winforms-md.md)] a [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] ovládací prvky.|Nelze použít.|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [Postupy: Hostování ovládacího prvku Windows Forms v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-control-in-wpf.md)  
 [Postupy: Hostování ovládacího prvku Windows Forms složené v grafickém subsystému WPF](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-windows-forms-composite-control-in-wpf.md)  
 [Postupy: Hostování složeného ovládacího prvku WPF ve Windows Forms](../../../../docs/framework/wpf/advanced/walkthrough-hosting-a-wpf-composite-control-in-windows-forms.md)  
 [Windows Forms a mapování vlastností WPF](../../../../docs/framework/wpf/advanced/windows-forms-and-wpf-property-mapping.md)
