---
title: Rozložení
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
ms.openlocfilehash: 869780f2b6a625923ce869bcaafbbd2319f6cb23
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44064982"
---
# <a name="layout"></a>Rozložení
Toto téma popisuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] systém rozložení. Vysvětlení, jak a kdy probíhá výpočet rozložení je nezbytné pro vytváření uživatelských rozhraní v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Element ohraničující polí](#LayoutSystem_BoundingBox)  
  
-   [Systém rozložení](#LayoutSystem_Overview)  
  
-   [Měření a uspořádání podřízených](#LayoutSystem_Measure_Arrange)  
  
-   [Prvky panel a chování vlastní rozložení](#LayoutSystem_PanelsCustom)  
  
-   [Důležité informace o výkonu rozložení](#LayoutSystem_Performance)  
  
-   [Dílčí pixel vykreslování a rozložení zaokrouhlení](#LayoutSystem_LayoutRounding)  
  
-   [Co se chystá](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## <a name="element-bounding-boxes"></a>Element ohraničující polí  
 Pokud uvažujete o rozložení v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], je důležité pochopit ohraničujícího rámečku, který obklopuje všechny elementy. Každý <xref:System.Windows.FrameworkElement> spotřebované podle rozložení systému můžete představit jako obdélníku, který je s drážkou do požadovaného rozložení. <xref:System.Windows.Controls.Primitives.LayoutInformation> Třída vrací hranice přidělení rozložení elementu nebo slotu. Velikost obdélníku je určeno výpočet prostor obrazovku, velikost žádná omezení, vlastnosti specifické pro rozložení (například okraje a odsazení) a jednotlivé chování nadřazené <xref:System.Windows.Controls.Panel> elementu. Zpracování těchto dat, systém rozložení je schopný vypočítat pozice všech podřízených objektů konkrétní <xref:System.Windows.Controls.Panel>. Je dobré si uvědomit, že změny velikosti vlastnosti definované na nadřazený prvek, například <xref:System.Windows.Controls.Border>, vliv na jeho podřízené položky.  
  
 Následující obrázek znázorňuje jednoduché rozložení.  
  
 ![Typické mřížky žádné ohraničujícího rámečku, který bude zobrazen. ](../../../../docs/framework/wpf/advanced/media/boundingbox1.png "boundingbox1")  
  
 Toto rozložení lze dosáhnout pomocí následujících [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[LayoutInformation#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 Jediný <xref:System.Windows.Controls.TextBlock> element hostována v rámci <xref:System.Windows.Controls.Grid>. Zatímco vyplní pouze levém horním rohu prvního sloupce do přiděleného místa pro text <xref:System.Windows.Controls.TextBlock> je ve skutečnosti mnohem větší. Ohraničující rámeček žádné <xref:System.Windows.FrameworkElement> lze načíst s použitím <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> metody. Následující obrázek znázorňuje rámeček ohraničující konkrétní <xref:System.Windows.Controls.TextBlock> elementu.  
  
 ![Ohraničující rámeček ovládacím prvku TextBlock je nyní viditelné. ](../../../../docs/framework/wpf/advanced/media/boundingbox2.png "boundingbox2")  
  
 Jak je uvedeno žlutý obdélníku do přiděleného místa pro <xref:System.Windows.Controls.TextBlock> prvek je ve skutečnosti mnohem větší, než se zobrazí. Jako další prvky jsou přidány do <xref:System.Windows.Controls.Grid>, toto přidělení může zmenšit nebo zvětšit, v závislosti na typu a velikosti prvků, které jsou přidány.  
  
 Pozici rozložení <xref:System.Windows.Controls.TextBlock> je přeložit na <xref:System.Windows.Shapes.Path> pomocí <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> metody. Tato technika může být užitečné při zobrazování ohraničující rámeček elementu.  
  
 [!code-csharp[LayoutInformation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## <a name="the-layout-system"></a>Systém rozložení  
 V nejjednodušším rozložení je rekurzivní, která vede k elementu se velikost, umístěn a vykreslit. Přesněji řečeno, rozložení popisuje proces měření a uspořádání členů <xref:System.Windows.Controls.Panel> elementu <xref:System.Windows.Controls.Panel.Children%2A> kolekce. Rozložení je náročné na zpracování. Čím větší <xref:System.Windows.Controls.Panel.Children%2A> kolekce, tím větší počet výpočty, které je třeba. Složitost je také možné vytvářet na základě rozložení chování definované <xref:System.Windows.Controls.Panel> element, který vlastní kolekce. Poměrně jednoduchá <xref:System.Windows.Controls.Panel>, například <xref:System.Windows.Controls.Canvas>, mají výrazně lepší výkon než komplexnější <xref:System.Windows.Controls.Panel>, jako například <xref:System.Windows.Controls.Grid>.  
  
 Pokaždé, když, který podřízený <xref:System.Windows.UIElement> změní pozici, má potenciál pro aktivaci nové předáván systém rozložení. Proto je důležité pochopit, události, které můžete vyvolat rozložení systému, jak je zbytečné volání může mít za následek nízký výkon aplikace. Následující část popisuje proces, který nastane, pokud je vyvolána systém rozložení.  
  
1.  Podřízený <xref:System.Windows.UIElement> zahájí proces rozložení tak, že první jeho základní vlastnosti měří.  
  
2.  Velikost vlastnosti definované v <xref:System.Windows.FrameworkElement> jsou vyhodnoceny jako <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, a <xref:System.Windows.FrameworkElement.Margin%2A>.  
  
3.  <xref:System.Windows.Controls.Panel>– Logika specifická pro použití, jako například <xref:System.Windows.Controls.Dock> směr nebo překrývání <xref:System.Windows.Controls.StackPanel.Orientation%2A>.  
  
4.  Obsah je uspořádaná Po změření všechny podřízené objekty.  
  
5.  <xref:System.Windows.Controls.Panel.Children%2A> Kolekce je vykreslen na obrazovce.  
  
6.  Proces je znovu vyvolána, pokud další <xref:System.Windows.Controls.Panel.Children%2A> jsou přidána do kolekce, <xref:System.Windows.FrameworkElement.LayoutTransform%2A> se použije, nebo <xref:System.Windows.UIElement.UpdateLayout%2A> metoda je volána.  
  
 Tento proces a jak je vyvolán jsou definovány podrobněji v následujících částech.  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## <a name="measuring-and-arranging-children"></a>Měření a uspořádání podřízených  
 Systém rozložení dokončení dva průchody pro každého člena <xref:System.Windows.Controls.Panel.Children%2A> kolekce, míru pass a průchodu uspořádat. Jednotlivých podřízených <xref:System.Windows.Controls.Panel> poskytuje vlastní <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> způsobů dosažení chování specifické rozložení.  
  
 Při průchodu měr každý člen <xref:System.Windows.Controls.Panel.Children%2A> kolekce je vyhodnocen. Proces začíná volání <xref:System.Windows.UIElement.Measure%2A> metody. Tato metoda je volána v rámci implementace nadřazené <xref:System.Windows.Controls.Panel> elementu a není nutné explicitně volat pro rozložení dojde k.  
  
 První, nativní velikosti vlastnosti <xref:System.Windows.UIElement> jsou vyhodnoceny jako <xref:System.Windows.UIElement.Clip%2A> a <xref:System.Windows.UIElement.Visibility%2A>. Tím se vygeneruje hodnotu s názvem `constraintSize` , který je předán <xref:System.Windows.FrameworkElement.MeasureCore%2A>.  
  
 Za druhé, framework vlastnosti definované v <xref:System.Windows.FrameworkElement> zpracování, což má vliv na hodnotu `constraintSize`. Tyto vlastnosti obvykle popisují základní vlastnosti velikosti <xref:System.Windows.UIElement>, například jeho <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, a <xref:System.Windows.FrameworkElement.Style%2A>. Každá z těchto vlastností můžete změnit místo, které jsou nezbytné k zobrazení elementu. <xref:System.Windows.FrameworkElement.MeasureOverride%2A> následném zavolání s `constraintSize` jako parametr.  
  
> [!NOTE]
>  Existuje rozdíl mezi vlastností <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A> a <xref:System.Windows.FrameworkElement.ActualWidth%2A>. Například <xref:System.Windows.FrameworkElement.ActualHeight%2A> počítané hodnoty na základě ostatní vstupy výšku a systém rozložení je vlastnost. Hodnota je nastavena rozložení samotný systém, podle skutečný vykreslování pass a může proto bude tak hrozit mírně sadu hodnot vlastností, jako například <xref:System.Windows.FrameworkElement.Height%2A>, které jsou základem vstupní změnit.  
>   
>  Protože <xref:System.Windows.FrameworkElement.ActualHeight%2A> je vypočítaná hodnota, je třeba si uvědomit, že může být více přírůstkové hlášené změní nebo k ní v důsledku různých operací systém rozložení. Systém rozložení může výpočet požadovaná míra místo pro podřízené prvky, omezení nadřazeného elementu a tak dále.  
  
 Konečným cílem průchodu měr je podřízený k určení jeho <xref:System.Windows.UIElement.DesiredSize%2A>, která spadá <xref:System.Windows.FrameworkElement.MeasureCore%2A> volání. <xref:System.Windows.UIElement.DesiredSize%2A> Hodnota se ukládá pomocí <xref:System.Windows.UIElement.Measure%2A> pro používání průchodu obsahu uspořádat.  
  
 Průchod uspořádat začíná volání <xref:System.Windows.UIElement.Arrange%2A> metody. Při průchodu uspořádat nadřazené <xref:System.Windows.Controls.Panel> element generuje obdélník, který představuje hranice podřízené. Tato hodnota je předán <xref:System.Windows.FrameworkElement.ArrangeCore%2A> metody pro zpracování.  
  
 <xref:System.Windows.FrameworkElement.ArrangeCore%2A> Metoda vyhodnocuje <xref:System.Windows.UIElement.DesiredSize%2A> podřízené a vyhodnotí další okraje, které mohou ovlivnit vykreslené velikost prvku. <xref:System.Windows.FrameworkElement.ArrangeCore%2A> generuje `arrangeSize`, které se předává <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metodu <xref:System.Windows.Controls.Panel> jako parametr. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> generuje `finalSize` podřízeného. Nakonec <xref:System.Windows.FrameworkElement.ArrangeCore%2A> metoda nemá konečného hodnocení posunu vlastnosti, jako je například okraje a zarovnání a umístí podřízené ve slotu rozložení. Podřízený objekt není nutné (a často není) zadejte celý přidělené místo. Ovládací prvek se potom vrátí do nadřazeného <xref:System.Windows.Controls.Panel> a dokončení procesu rozložení.  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## <a name="panel-elements-and-custom-layout-behaviors"></a>Prvky panel a chování vlastní rozložení  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] obsahuje skupinu prvky, které jsou odvozeny z <xref:System.Windows.Controls.Panel>. Tyto <xref:System.Windows.Controls.Panel> prvky povolit mnoho složitá rozložení. Například ukládání elementů můžete snadno dosáhnout pomocí <xref:System.Windows.Controls.StackPanel> elementu, zatímco další složité a bez průchodu rozložení je možné pomocí <xref:System.Windows.Controls.Canvas>.  
  
 Následující tabulka shrnuje dostupné rozložení <xref:System.Windows.Controls.Panel> elementy.  
  
|Název panelu|Popis|  
|----------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Vymezuje oblast, ve kterém můžete explicitně umísťovat podřízené prvky podle souřadnic vzhledem k <xref:System.Windows.Controls.Canvas> oblasti.|  
|<xref:System.Windows.Controls.DockPanel>|Vymezuje oblast, ve kterém můžete uspořádat podřízené elementy vodorovně nebo svisle, relativně vůči sobě navzájem.|  
|<xref:System.Windows.Controls.Grid>|Definuje flexibilní oblast mřížky, která se skládá ze sloupců a řádků.|  
|<xref:System.Windows.Controls.StackPanel>|Uspořádává podřízené prvky do jednoho řádku, který může být orientovaný vodorovně nebo svisle.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Poskytuje rozhraní pro <xref:System.Windows.Controls.Panel> prvky, které virtualizují jejich podřízenou kolekci dat. Toto je abstraktní třída.|  
|<xref:System.Windows.Controls.WrapPanel>|Umísťuje podřízené prvky do sekvenční Pozice zleva doprava, rozdělení obsahu na další řádek na okraji obsahujícího pole. Následné řazení vyvolá sekvenčně shora dolů nebo zprava doleva v závislosti na hodnotu <xref:System.Windows.Controls.WrapPanel.Orientation%2A> vlastnost.|  
  
 Pro aplikace, které vyžadují rozložení, který není možné s použitím některých z předdefinovaných <xref:System.Windows.Controls.Panel> prvky, vlastní rozložení chování se dá dosáhnout dědění z <xref:System.Windows.Controls.Panel> a přepsáním <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody. Příklad najdete v tématu [vlastní kruhové panelu ukázkové](https://go.microsoft.com/fwlink/?LinkID=159982).  
  
<a name="LayoutSystem_Performance"></a>   
## <a name="layout-performance-considerations"></a>Důležité informace o výkonu rozložení  
 Rozložení je rekurzivní proces. Každý podřízený prvek <xref:System.Windows.Controls.Panel.Children%2A> zpracuje kolekce při každém vyvolání systém rozložení. V důsledku toho aktivuje systém rozložení mělo by se vyhnout při není nutné. Následující aspekty pomáhá dosahovat lepšího výkonu.  
  
-   Mějte které změně hodnoty vlastnosti rekurzivní aktualizace vynutí systém rozložení.  
  
     Vlastnosti závislostí, jejichž hodnoty může způsobit, že systém rozložení inicializovat jsou označené veřejné příznaky. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> a <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> poskytují užitečné příčiny, vlastností, které vynutí změny hodnot rekurzivního aktualizovat tak, že systém rozložení. Obecně platí, by měly mít jakákoli vlastnost, která mohou ovlivnit velikost elementu ohraničující rámeček <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> příznak nastaven na hodnotu true. Další informace najdete v tématu [přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
-   Pokud je to možné, používat <xref:System.Windows.UIElement.RenderTransform%2A> místo <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.  
  
     A <xref:System.Windows.FrameworkElement.LayoutTransform%2A> může být velmi užitečný způsob, jak ovlivnit obsah [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Pokud efekt transformace není nutné mít vliv na umístění dalších prvků, je však nejvhodnější použít <xref:System.Windows.UIElement.RenderTransform%2A> místo, protože <xref:System.Windows.UIElement.RenderTransform%2A> systém rozložení se nevyvolá. <xref:System.Windows.FrameworkElement.LayoutTransform%2A> použije vlastní transformaci a vynutí aktualizaci rozložení s rekurzivní pro novou pozici ovlivněný prvek.  
  
-   Vyhněte se volání zbytečných <xref:System.Windows.UIElement.UpdateLayout%2A>.  
  
     <xref:System.Windows.UIElement.UpdateLayout%2A> Metoda vynutí aktualizaci rozložení rekurzivní a není často nutné. Pokud si nejste jistí, že úplná aktualizace je vyžadována, využívají systém rozložení mohli volat tuto metodu za vás.  
  
-   Při práci s velkým <xref:System.Windows.Controls.Panel.Children%2A> kolekci, zvažte použití <xref:System.Windows.Controls.VirtualizingStackPanel> místo běžný <xref:System.Windows.Controls.StackPanel>.  
  
     Prostřednictvím virtualizace podřízené kolekce <xref:System.Windows.Controls.VirtualizingStackPanel> pouze objekty udržuje v paměti, které jsou aktuálně v rámci nadřazeného zobrazení. V důsledku toho se podstatně výkon ve většině scénářů.  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## <a name="sub-pixel-rendering-and-layout-rounding"></a>Dílčí pixel vykreslování a rozložení zaokrouhlení  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Grafiky systém využívá jednotkách nezávislých na zařízení k zajištění nezávislosti překlad IP adres a zařízení. Každý pixel nezávislé zařízení se automaticky škáluje s systému [!INCLUDE[TLA#tla_dpi](../../../../includes/tlasharptla-dpi-md.md)] nastavení. To poskytuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] správné škálování aplikací pro různé [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] nastavení a způsobí, že aplikace automaticky [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)]-vědět.  
  
 Nicméně to [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] nezávislost můžete vytvořit nestandardní edge vykreslování kvůli anti-aliasing. Tyto artefakty, které jsou obvykle zobrazena jako fuzzy nebo poloprůhledného hrany, může dojít, pokud umístění okraj spadá uprostřed pixelů zařízení místo mezi pixelů zařízení. Systém rozložení poskytuje způsob, jak nastavit pro tuto se zaokrouhlováním rozložení. Zaokrouhlení rozložení je, kde systém rozložení zaokrouhlí žádné pixelech – neintegrální průchodu rozložení.  
  
 Zaokrouhlení rozložení je ve výchozím nastavení zakázána. Chcete-li povolit zaokrouhlení rozložení, nastavte <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> vlastnost `true` na žádném <xref:System.Windows.FrameworkElement>. Protože je vlastnost závislosti, hodnota rozšíří na všechny podřízené objekty ve vizuálním stromu. Chcete-li povolit rozložení zaokrouhlení pro celé uživatelské rozhraní, nastavte <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> k `true` na kořenový kontejner. Příklad naleznete v tématu <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>.  
  
<a name="LayoutSystem_whatsnext"></a>   
## <a name="whats-next"></a>Co se chystá  
 Vysvětlení, jak prvky se měří a uspořádat je prvním krokem při Principy rozložení. Další informace o dostupných <xref:System.Windows.Controls.Panel> prvky, naleznete v tématu [přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md). Chcete-li lépe pochopit různé vlastnosti umístění, které můžou ovlivnit rozložení, naleznete v tématu [zarovnání, okrajů a odsazení přehled](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md). Příklad vlastní <xref:System.Windows.Controls.Panel> prvku, naleznete v tématu [paprskového ukázková Panel](https://go.microsoft.com/fwlink/?LinkID=159982). Až budete připravení na všech součástí dohromady v aplikaci s nižšími nároky, naleznete v tématu [návod: Moje první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.UIElement>  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Přehled zarovnání, okrajů a odsazení](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)  
 [Rozložení a návrh](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
