---
title: Rozložení
description: Naučte se, jak a kdy dochází k výpočtům rozložení v systému Windows Presentation Foundationho rozložení.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
ms.openlocfilehash: 0db3f2a6cbabc610362435d64de3fc970f01a73c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164764"
---
# <a name="layout"></a>Rozložení

Toto téma popisuje systém rozložení Windows Presentation Foundation (WPF). Porozumění tomu, jak a kdy dochází k výpočtům rozložení, je zásadní pro vytváření uživatelských rozhraní v WPF.

Toto téma obsahuje následující oddíly:

- [Prvky ohraničující pole](#LayoutSystem_BoundingBox)

- [Systém rozložení](#LayoutSystem_Overview)

- [Měření a uspořádání podřízených objektů](#LayoutSystem_Measure_Arrange)

- [Prvky panelu a chování vlastního rozložení](#LayoutSystem_PanelsCustom)

- [Požadavky na výkon rozložení](#LayoutSystem_Performance)

- [Vykreslování dílčích pixelů a zaoblení rozložení](#LayoutSystem_LayoutRounding)

- [Co dál](#LayoutSystem_whatsnext)

<a name="LayoutSystem_BoundingBox"></a>

## <a name="element-bounding-boxes"></a>Prvky ohraničující pole

Při seznámení s rozložením v WPF je důležité pochopit ohraničující rámeček, který obklopuje všechny prvky. <xref:System.Windows.FrameworkElement>Z každého spotřebovaného systémem pro rozložení si můžete představit jako obdélník, který je v rozložení drážký. <xref:System.Windows.Controls.Primitives.LayoutInformation>Třída vrací hranice rozvržení rozložení prvku nebo slot. Velikost obdélníku je určena výpočtem dostupného místa na obrazovce, velikosti všech omezení, vlastností specifických pro rozložení (například okraje a odsazení) a jednotlivého chování nadřazeného <xref:System.Windows.Controls.Panel> prvku. Zpracování těchto dat, systém rozložení dokáže vypočítat pozici všech podřízených objektů konkrétního <xref:System.Windows.Controls.Panel> . Je důležité si uvědomit, že charakteristiky změny velikosti definované v nadřazeném elementu, například a <xref:System.Windows.Controls.Border> , ovlivňují jeho podřízené objekty.

Na následujícím obrázku je znázorněno jednoduché rozložení.

![Snímek obrazovky, který zobrazuje typickou mřížku bez ohraničujícího pole.](./media/layout/grid-no-bounding-box-superimpose.png)

Toto rozložení lze dosáhnout pomocí následujícího [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] .

[!code-xaml[LayoutInformation#1](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]

Jeden <xref:System.Windows.Controls.TextBlock> element je hostován v rámci <xref:System.Windows.Controls.Grid> . I když text vyplní pouze levý horní roh prvního sloupce, je přidělený prostor pro, který <xref:System.Windows.Controls.TextBlock> je ve skutečnosti mnohem větší. Ohraničující rámeček Any <xref:System.Windows.FrameworkElement> lze načíst pomocí <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> metody. Následující ilustrace znázorňuje ohraničující rámeček pro <xref:System.Windows.Controls.TextBlock> element.

![Snímek obrazovky, který ukazuje, že se teď zobrazuje ohraničovací rámeček TextBlock](./media/layout/visible-textblock-bounding-box.png)

Jak je znázorněno žlutým obdélníkem, přidělený prostor pro <xref:System.Windows.Controls.TextBlock> element je skutečně mnohem větší, než se zobrazí. Stejně jako další prvky jsou přidány do <xref:System.Windows.Controls.Grid> , toto přidělení může zmenšit nebo rozšířit v závislosti na typu a velikosti přidaných prvků.

Pozice rozložení <xref:System.Windows.Controls.TextBlock> je přeložena do a <xref:System.Windows.Shapes.Path> pomocí <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> metody. Tato technika může být užitečná pro zobrazení ohraničovacího rámečku prvku.

[!code-csharp[LayoutInformation#2](~/samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
[!code-vb[LayoutInformation#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]

<a name="LayoutSystem_Overview"></a>

## <a name="the-layout-system"></a>Systém rozložení

V nejjednodušším případě je rozložení rekurzivní systém, který vede na velikost, umístění a vykreslení prvku. Přesněji řečeno, rozložení popisuje proces měření a uspořádání členů <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Panel.Children%2A> kolekce prvků. Rozložení je náročný proces. Čím větší je <xref:System.Windows.Controls.Panel.Children%2A> kolekce, tím větší je počet výpočtů, které je třeba provést. Složitost je také možné začlenit na základě chování rozložení definovaného <xref:System.Windows.Controls.Panel> prvkem, který je vlastníkem kolekce. Relativně jednoduché <xref:System.Windows.Controls.Panel> , například <xref:System.Windows.Controls.Canvas> , může mít výrazně lepší výkon než složitější, jako je například <xref:System.Windows.Controls.Panel> <xref:System.Windows.Controls.Grid> .

Pokaždé, když dítě <xref:System.Windows.UIElement> změní svou pozici, má potenciál aktivovat nové průchod systémem rozložení. Proto je důležité pochopit události, které mohou vyvolat systém rozložení, protože zbytečné vyvolání může vést k špatnému výkonu aplikace. Následující článek popisuje proces, který nastane, když je vyvolán systém rozložení.

1. Podřízená položka <xref:System.Windows.UIElement> zahájí proces rozložení, protože nejprve má měřené základní vlastnosti.

2. Vlastnosti změny velikosti definované v <xref:System.Windows.FrameworkElement> jsou vyhodnocovány, například, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Margin%2A> .

3. <xref:System.Windows.Controls.Panel>-používá se specifická logika, jako je například <xref:System.Windows.Controls.Dock> směr nebo skládání <xref:System.Windows.Controls.StackPanel.Orientation%2A> .

4. Obsah je uspořádán po měření všech podřízených objektů.

5. <xref:System.Windows.Controls.Panel.Children%2A>Kolekce se vykresluje na obrazovce.

6. Proces je znovu vyvolán, pokud je <xref:System.Windows.Controls.Panel.Children%2A> přidána další do kolekce, <xref:System.Windows.FrameworkElement.LayoutTransform%2A> je použita nebo je <xref:System.Windows.UIElement.UpdateLayout%2A> volána metoda.

Tento proces a jeho vyvolání jsou podrobněji definovány v následujících oddílech.

<a name="LayoutSystem_Measure_Arrange"></a>

## <a name="measuring-and-arranging-children"></a>Měření a uspořádání podřízených objektů

Systém rozložení dokončí dvě průchody pro každého člena <xref:System.Windows.Controls.Panel.Children%2A> kolekce, míra je úspěšná a uspořádání bude úspěšné. Každý podřízený objekt <xref:System.Windows.Controls.Panel> poskytuje vlastní <xref:System.Windows.FrameworkElement.MeasureOverride%2A> metody a, <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> aby bylo možné dosáhnout vlastního chování rozložení.

Během úspěšnosti míry <xref:System.Windows.Controls.Panel.Children%2A> se vyhodnotí každý člen kolekce. Proces začíná voláním <xref:System.Windows.UIElement.Measure%2A> metody. Tato metoda je volána v rámci implementace nadřazeného <xref:System.Windows.Controls.Panel> elementu a není nutné ji explicitně volat, aby bylo možné rozložení provést.

Nejprve <xref:System.Windows.UIElement> jsou vyhodnoceny vlastnosti nativní velikosti, například <xref:System.Windows.UIElement.Clip%2A> a <xref:System.Windows.UIElement.Visibility%2A> . Tím se vygeneruje hodnota s názvem `constraintSize` , která je předána do <xref:System.Windows.FrameworkElement.MeasureCore%2A> .

Druhý, vlastnosti rozhraní definované na <xref:System.Windows.FrameworkElement> jsou zpracovávány, což má vliv na hodnotu `constraintSize` . Tyto vlastnosti obecně popisují charakteristiky velikosti základního <xref:System.Windows.UIElement> , jako je například <xref:System.Windows.FrameworkElement.Height%2A> ,, <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.Margin%2A> a <xref:System.Windows.FrameworkElement.Style%2A> . Každá z těchto vlastností může změnit prostor, který je nezbytný k zobrazení elementu. <xref:System.Windows.FrameworkElement.MeasureOverride%2A>je pak volána s `constraintSize` parametrem.

> [!NOTE]
> Existuje rozdíl mezi vlastnostmi <xref:System.Windows.FrameworkElement.Height%2A> a a <xref:System.Windows.FrameworkElement.Width%2A> <xref:System.Windows.FrameworkElement.ActualHeight%2A> a <xref:System.Windows.FrameworkElement.ActualWidth%2A> . Například <xref:System.Windows.FrameworkElement.ActualHeight%2A> vlastnost je vypočtená hodnota založená na dalších vstupech výšky a v systému rozložení. Hodnota je nastavena samotným systémem rozložení na základě skutečného průchodu vykreslování a může proto mírně prodleva za nastavenou hodnotou vlastností, například <xref:System.Windows.FrameworkElement.Height%2A> , které jsou základem změny vstupu.
>
> Vzhledem k tomu <xref:System.Windows.FrameworkElement.ActualHeight%2A> , že je vypočtená hodnota, měli byste si uvědomit, že v důsledku různých operací se systémem rozložení může dojít k několika nebo přírůstkovým změnám. Systém rozložení může vypočítat požadované místo měření pro podřízené elementy, omezení nadřazeného elementu atd.

Konečný cíl míry úspěšnosti je pro podřízený element k určení <xref:System.Windows.UIElement.DesiredSize%2A> , ke kterému dojde během <xref:System.Windows.FrameworkElement.MeasureCore%2A> volání. <xref:System.Windows.UIElement.DesiredSize%2A>Hodnota je uložena v <xref:System.Windows.UIElement.Measure%2A> pro použití během uspořádání obsahu.

Průchod uspořádání začíná voláním <xref:System.Windows.UIElement.Arrange%2A> metody. Během uspořádání je nadřazený <xref:System.Windows.Controls.Panel> prvek vygenerován obdélník, který představuje hranice podřízeného objektu. Tato hodnota je předána <xref:System.Windows.FrameworkElement.ArrangeCore%2A> metodě pro zpracování.

<xref:System.Windows.FrameworkElement.ArrangeCore%2A>Metoda vyhodnocuje <xref:System.Windows.UIElement.DesiredSize%2A> podřízenou položku a vyhodnotí další okraje, které mohou ovlivnit vykreslenou velikost elementu. <xref:System.Windows.FrameworkElement.ArrangeCore%2A>vygeneruje objekt `arrangeSize` , který je předán <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metodě <xref:System.Windows.Controls.Panel> jako parametru. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>vygeneruje `finalSize` podřízenou položku. Nakonec <xref:System.Windows.FrameworkElement.ArrangeCore%2A> Metoda provede konečné vyhodnocení vlastností posunutí, jako je například marže a zarovnání, a umístí podřízenou položku do jejího slotu rozložení. Podřízená položka nemusí (a často neumožňuje) vyplnit celé přidělené místo. Ovládací prvek se pak vrátí nadřazenému <xref:System.Windows.Controls.Panel> procesu a proces rozložení je dokončený.

<a name="LayoutSystem_PanelsCustom"></a>

## <a name="panel-elements-and-custom-layout-behaviors"></a>Prvky panelu a chování vlastního rozložení

WPF obsahuje skupinu prvků, které jsou odvozeny z <xref:System.Windows.Controls.Panel> . Tyto <xref:System.Windows.Controls.Panel> prvky umožňují mnoho složitých rozložení. Například prvky Stack lze snadno dosáhnout pomocí <xref:System.Windows.Controls.StackPanel> elementu, zatímco složitější a bezplatná rozložení toků jsou možné pomocí <xref:System.Windows.Controls.Canvas> .

Následující tabulka shrnuje dostupné <xref:System.Windows.Controls.Panel> prvky rozložení.

|Název panelu|Popis|
|----------------|-----------------|
|<xref:System.Windows.Controls.Canvas>|Definuje oblast, ve které můžete explicitně umístit podřízené prvky souřadnicemi relativními k <xref:System.Windows.Controls.Canvas> oblasti.|
|<xref:System.Windows.Controls.DockPanel>|Definuje oblast, ve které můžete uspořádat podřízené prvky buď vodorovně, nebo svisle, relativně k sobě navzájem.|
|<xref:System.Windows.Controls.Grid>|Definuje flexibilní oblast mřížky, která se skládá ze sloupců a řádků.|
|<xref:System.Windows.Controls.StackPanel>|Uspořádá podřízené prvky na jeden řádek, který může být orientovaný vodorovně nebo svisle.|
|<xref:System.Windows.Controls.VirtualizingPanel>|Poskytuje rozhraní pro <xref:System.Windows.Controls.Panel> prvky, které virtualizují jejich podřízenou kolekci dat. Toto je abstraktní třída.|
|<xref:System.Windows.Controls.WrapPanel>|Umístí podřízené prvky v sekvenčním umístění zleva doprava a oddělí obsah na další řádek na okraji obsahujícího pole. Následné řazení probíhá postupně shora dolů nebo zprava doleva v závislosti na hodnotě <xref:System.Windows.Controls.WrapPanel.Orientation%2A> Vlastnosti.|

Pro aplikace, které vyžadují rozložení, které není možné pomocí některého z předdefinovaných <xref:System.Windows.Controls.Panel> prvků, lze chování vlastního rozložení dosáhnout děděním z <xref:System.Windows.Controls.Panel> a přepsáním <xref:System.Windows.FrameworkElement.MeasureOverride%2A> <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metod a.

<a name="LayoutSystem_Performance"></a>

## <a name="layout-performance-considerations"></a>Požadavky na výkon rozložení

Rozložení je rekurzivní proces. Každý podřízený element v <xref:System.Windows.Controls.Panel.Children%2A> kolekci se zpracuje během každého vyvolání systému rozložení. V důsledku toho by se měl spustit systém rozložení, pokud není potřeba. Následující požadavky vám pomůžou dosáhnout lepšího výkonu.

- Mějte na paměti, které změny hodnot vlastností vynutí rekurzivní aktualizaci systémem rozložení.

  Vlastnosti závislosti, jejichž hodnoty mohou způsobit inicializaci systému rozložení, jsou označeny veřejnými příznaky. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>a <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> poskytují užitečné ovládací předpisy, kterými se změny hodnot vlastností vynutí rekurzivní aktualizace systémem rozložení. Obecně platí, že jakákoli vlastnost, která může ovlivnit velikost ohraničujícího pole prvku, by měla mít <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> příznak nastaven na hodnotu true. Další informace najdete v tématu [Přehled vlastností závislosti](dependency-properties-overview.md).

- Pokud je to možné, použijte <xref:System.Windows.UIElement.RenderTransform%2A> místo a <xref:System.Windows.FrameworkElement.LayoutTransform%2A> .

  <xref:System.Windows.FrameworkElement.LayoutTransform%2A>Může být velmi užitečný způsob, jak ovlivnit obsah [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] . Nicméně pokud efekt transformace nemá vliv na pozici jiných prvků, je nejvhodnější použít <xref:System.Windows.UIElement.RenderTransform%2A> místo toho, protože <xref:System.Windows.UIElement.RenderTransform%2A> nevyvolává systém rozložení. <xref:System.Windows.FrameworkElement.LayoutTransform%2A>Použije transformaci a vynutí aktualizaci rekurzivního rozložení na účet pro novou pozici ovlivněného prvku.

- Vyhněte se zbytečnému volání <xref:System.Windows.UIElement.UpdateLayout%2A> .

  <xref:System.Windows.UIElement.UpdateLayout%2A>Metoda vynutí aktualizaci rekurzivního rozložení a často není nutná. Pokud si nejste jistí, jestli je nutná úplná aktualizace, spoléhá na to, že systém rozložení volá tuto metodu za vás.

- Při práci s velkou <xref:System.Windows.Controls.Panel.Children%2A> kolekcí zvažte použití <xref:System.Windows.Controls.VirtualizingStackPanel> namísto obyčejného <xref:System.Windows.Controls.StackPanel> .

  Virtualizací podřízené kolekce <xref:System.Windows.Controls.VirtualizingStackPanel> zachovává pouze objekty v paměti, které jsou aktuálně v zobrazení nadřazeného objektu. V důsledku toho se ve většině scénářů výrazně vylepšuje výkon.

<a name="LayoutSystem_LayoutRounding"></a>

## <a name="sub-pixel-rendering-and-layout-rounding"></a>Vykreslování dílčích pixelů a zaoblení rozložení

Grafický systém WPF používá jednotky nezávislé na zařízení k umožnění rozlišení a nezávislosti zařízení. Každé zařízení nezávislé na pixelech se automaticky škáluje s nastavením počet bodů na palec (dpi) v systému. To umožňuje aplikacím WPF správné škálování pro různá nastavení dpi a aplikace automaticky zohledňuje rozlišení DPI.

Tato nezávislost v DPI však může vytvořit nepravidelné vykreslování z důvodu vyhlazení. Tyto artefakty, které se obvykle zobrazují jako rozostřené nebo částečně transparentní okraje, mohou nastat, pokud umístění okraje spadá do středu zařízení v pixelu místo mezi pixely zařízení. Systém rozložení poskytuje způsob, jak ho upravit pomocí zaokrouhlování rozložení. Zaoblení rozložení je místo, kde systém rozložení zaokrouhlí jakékoli Neceločíselné hodnoty pixelů během průchodu rozložení.

Zaoblení rozložení je ve výchozím nastavení zakázáno. Chcete-li povolit zaokrouhlování rozložení, nastavte vlastnost na hodnotu <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> `true` on <xref:System.Windows.FrameworkElement> . Vzhledem k tomu, že se jedná o vlastnost závislosti, bude hodnota rozšířena do všech podřízených prvků ve vizuálním stromu. Chcete-li povolit zaokrouhlování rozložení pro celé uživatelské rozhraní, nastavte <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> na `true` kořenovém kontejneru. Příklad naleznete v tématu <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>.

<a name="LayoutSystem_whatsnext"></a>

## <a name="whats-next"></a>Jak dál?

Porozumění způsobu měření a uspořádání prvků je prvním krokem při porozumění rozložení. Další informace o dostupných <xref:System.Windows.Controls.Panel> prvcích najdete v tématu [Přehled panelů](../controls/panels-overview.md). Chcete-li lépe porozumět různým vlastnostem umístění, které mohou ovlivnit rozložení, přečtěte si téma [zarovnání, okraje a přehled odsazení](alignment-margins-and-padding-overview.md). Až budete připraveni ho umístit do zjednodušené aplikace, přečtěte si [Návod: Moje první desktopová aplikace WPF](../getting-started/walkthrough-my-first-wpf-desktop-application.md).

## <a name="see-also"></a>Viz také

- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.UIElement>
- [Přehled panelů](../controls/panels-overview.md)
- [Přehled zarovnání, okrajů a odsazení](alignment-margins-and-padding-overview.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
