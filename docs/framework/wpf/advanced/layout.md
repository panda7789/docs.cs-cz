---
title: "Rozložení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WPF layout system [WPF]
- controls [WPF], layout system
- layout system [WPF]
ms.assetid: 3eecdced-3623-403a-a077-7595453a9221
caps.latest.revision: "31"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c9a5f33ab22779002e85d7a73b29ae74dac81c26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="layout"></a>Rozložení
Toto téma popisuje [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] rozložení systému. Pochopení, jak a kdy probíhá výpočet rozložení je nezbytné pro vytvoření uživatelského rozhraní v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)].  
  
 Toto téma obsahuje následující oddíly:  
  
-   [Element ohraničujícího polí](#LayoutSystem_BoundingBox)  
  
-   [Rozložení systému](#LayoutSystem_Overview)  
  
-   [Měření a uspořádání podřízených prvků](#LayoutSystem_Measure_Arrange)  
  
-   [Prvky panelů a chování vlastní rozložení](#LayoutSystem_PanelsCustom)  
  
-   [Faktory ovlivňující výkon rozložení](#LayoutSystem_Performance)  
  
-   [Vykreslování dílčí pixelů a zaokrouhlení rozložení](#LayoutSystem_LayoutRounding)  
  
-   [Co je další](#LayoutSystem_whatsnext)  
  
<a name="LayoutSystem_BoundingBox"></a>   
## <a name="element-bounding-boxes"></a>Element ohraničujícího polí  
 Pokud přemýšlíte o rozložení v [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)], je důležité si uvědomit, ohraničující pole, která obklopuje všechny elementy. Každý <xref:System.Windows.FrameworkElement> spotřebované podle rozložení systému lze považovat za obdélníku, která je s drážkou do rozložení. <xref:System.Windows.Controls.Primitives.LayoutInformation> Třída vrací hranice rozložení přidělení elementu nebo slot. Velikost rámeček je dáno výpočet místo k dispozici obrazovky, velikost žádná omezení, rozložení specifické vlastnosti (například okraj a odsazení) a jednotlivé chování nadřazené <xref:System.Windows.Controls.Panel> elementu. Zpracování těchto dat, systém rozložení je moct vypočítat pozici všechny podřízené objekty konkrétní <xref:System.Windows.Controls.Panel>. Je důležité si pamatovat, že změna velikosti vlastnosti definované na nadřazený element, například <xref:System.Windows.Controls.Border>, vliv na jeho podřízených položek.  
  
 Následující obrázek znázorňuje jednoduché rozložení.  
  
 ![Typické mřížky žádné ohraničující pole překrývat. ] (../../../../docs/framework/wpf/advanced/media/boundingbox1.png "boundingbox1")  
  
 Toto rozložení lze dosáhnout pomocí následujících [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[LayoutInformation#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml#1)]  
  
 Jediný <xref:System.Windows.Controls.TextBlock> element je hostovaným v rámci <xref:System.Windows.Controls.Grid>. Při doplní levého horního rohu prvního sloupce, přidělení místo pro text <xref:System.Windows.Controls.TextBlock> je ve skutečnosti mnohem větší. Pole ohraničující libovolného <xref:System.Windows.FrameworkElement> můžete načíst pomocí <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> metoda. Následující obrázek znázorňuje ohraničující políčka <xref:System.Windows.Controls.TextBlock> elementu.  
  
 ![Ohraničující pole objektu TextBlock je nyní viditelné. ] (../../../../docs/framework/wpf/advanced/media/boundingbox2.png "boundingbox2")  
  
 Jak je uvedeno žlutý obdélníku přidělení místo pro <xref:System.Windows.Controls.TextBlock> element je ve skutečnosti mnohem větší, než se zobrazí. Jako další prvky jsou přidány do <xref:System.Windows.Controls.Grid>, může tato přidělení zmenšit nebo rozšířit, v závislosti na typu a velikosti elementů, které jsou přidány.  
  
 Rozložení pozici <xref:System.Windows.Controls.TextBlock> je přeložit na <xref:System.Windows.Shapes.Path> pomocí <xref:System.Windows.Controls.Primitives.LayoutInformation.GetLayoutSlot%2A> metoda. Tento postup může být užitečná pro zobrazení ohraničující pole elementu.  
  
 [!code-csharp[LayoutInformation#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LayoutInformation/CSharp/Window1.xaml.cs#2)]
 [!code-vb[LayoutInformation#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/LayoutInformation/VisualBasic/Window1.xaml.vb#2)]  
  
<a name="LayoutSystem_Overview"></a>   
## <a name="the-layout-system"></a>Rozložení systému  
 V nejjednodušším rozložení je rekurzivní systém, který vede k se k elementu, velikost, umístěný a vykreslit. Přesněji řečeno, rozložení popisuje proces měření a uspořádání členů <xref:System.Windows.Controls.Panel> elementu <xref:System.Windows.Controls.Panel.Children%2A> kolekce. Rozložení je náročné proces. Čím vyšší <xref:System.Windows.Controls.Panel.Children%2A> kolekce, tím větší je počet výpočtů, které musí být provedeny. Složitost můžete zavedená také na základě chování rozložení definované <xref:System.Windows.Controls.Panel> element, který vlastní kolekce. Relativně jednoduché <xref:System.Windows.Controls.Panel>, jako například <xref:System.Windows.Controls.Canvas>, může mít výrazně lepší výkon než složitější <xref:System.Windows.Controls.Panel>, jako například <xref:System.Windows.Controls.Grid>.  
  
 Každý čas, který podřízenou <xref:System.Windows.UIElement> změní jeho pozice má potenciál k aktivaci nového průchodu systémem rozložení. Proto je důležité si uvědomit, události, které můžete vyvolat rozložení systému, jako nepotřebné volání může vést k aplikace snížený výkon. Následující část popisuje proces, který nastane, když je volána rozložení systému.  
  
1.  Podřízená <xref:System.Windows.UIElement> zahájí proces rozložení tak, že první jeho základní vlastnosti měří.  
  
2.  Změna velikosti vlastnosti definované na <xref:System.Windows.FrameworkElement> se vyhodnocují jako <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Height%2A>, a <xref:System.Windows.FrameworkElement.Margin%2A>.  
  
3.  <xref:System.Windows.Controls.Panel>-je použité určitou logiku, jako například <xref:System.Windows.Controls.Dock> směr nebo překrývání <xref:System.Windows.Controls.StackPanel.Orientation%2A>.  
  
4.  Obsah je uspořádané po měří všechny podřízené objekty.  
  
5.  <xref:System.Windows.Controls.Panel.Children%2A> Kolekce vykreslením na obrazovce.  
  
6.  Proces je volána znovu, pokud je to další <xref:System.Windows.Controls.Panel.Children%2A> jsou přidány do kolekce, <xref:System.Windows.FrameworkElement.LayoutTransform%2A> se použije, nebo <xref:System.Windows.UIElement.UpdateLayout%2A> metoda je volána.  
  
 Tento proces a jak je vyvolána jsou definovány podrobněji v následujících částech.  
  
<a name="LayoutSystem_Measure_Arrange"></a>   
## <a name="measuring-and-arranging-children"></a>Měření a uspořádání podřízených prvků  
 Rozložení systému dokončení dva předává pro každého člena <xref:System.Windows.Controls.Panel.Children%2A> kolekce, pass měr a předejte jí uspořádání. Všechny podřízené <xref:System.Windows.Controls.Panel> poskytuje svou vlastní <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> způsobů dosažení vlastní rozložení konkrétní chování.  
  
 Během průchodu měr každý člen <xref:System.Windows.Controls.Panel.Children%2A> vyhodnotí kolekce. Proces začíná volání <xref:System.Windows.UIElement.Measure%2A> metoda. Tato metoda je volána v rámci implementace nadřazené <xref:System.Windows.Controls.Panel> elementu a nemusí být explicitně volána pro rozložení proběhnout.  
  
 První, nativní velikost vlastnosti <xref:System.Windows.UIElement> se vyhodnocují jako <xref:System.Windows.UIElement.Clip%2A> a <xref:System.Windows.UIElement.Visibility%2A>. Tím se vygeneruje hodnotu s názvem `constraintSize` předá do <xref:System.Windows.FrameworkElement.MeasureCore%2A>.  
  
 Za druhé, framework vlastnosti definované na <xref:System.Windows.FrameworkElement> zpracovávají, jenž ovlivňuje hodnotu `constraintSize`. Tyto vlastnosti obecně popisují základní charakteristiky velikosti <xref:System.Windows.UIElement>, například jeho <xref:System.Windows.FrameworkElement.Height%2A>, <xref:System.Windows.FrameworkElement.Width%2A>, <xref:System.Windows.FrameworkElement.Margin%2A>, a <xref:System.Windows.FrameworkElement.Style%2A>. Každý z těchto vlastností, můžete změnit místo, které jsou nutné k zobrazení elementu. <xref:System.Windows.FrameworkElement.MeasureOverride%2A>pak je volán s `constraintSize` jako parametr.  
  
> [!NOTE]
>  Existuje rozdíl mezi vlastnosti <xref:System.Windows.FrameworkElement.Height%2A> a <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.ActualHeight%2A> a <xref:System.Windows.FrameworkElement.ActualWidth%2A>. Například <xref:System.Windows.FrameworkElement.ActualHeight%2A> vlastnost je vypočítaná hodnota na základě jiných vstupy výšky a rozložení systému. Hodnota se nastavuje pomocí rozložení systému samostatně, podle průchodu skutečné vykreslování a může proto funkce lag mírně za nastavte hodnotu vlastnosti, jako například <xref:System.Windows.FrameworkElement.Height%2A>, které jsou základem vstupní změny.  
>   
>  Protože <xref:System.Windows.FrameworkElement.ActualHeight%2A> je vypočítaná hodnota, je třeba si uvědomit, že může být více přírůstkové hlášené změní nebo k němu v důsledku různých operací systému rozložení. Rozložení systému může výpočet požadované měr místa pro podřízené prvky, omezení nadřazeného elementu a tak dále.  
  
 Konečným cílem míry průchodu je podřízená určit jeho <xref:System.Windows.UIElement.DesiredSize%2A>, která spadá <xref:System.Windows.FrameworkElement.MeasureCore%2A> volání. <xref:System.Windows.UIElement.DesiredSize%2A> Hodnota je uložena ve <xref:System.Windows.UIElement.Measure%2A> pro použití při průchodu uspořádání obsahu.  
  
 Uspořádat průchodu začíná volání <xref:System.Windows.UIElement.Arrange%2A> metoda. Během průchodu uspořádat nadřazené <xref:System.Windows.Controls.Panel> element generuje obdélníku, která představuje hranice podřízený objekt. Tato hodnota je předán <xref:System.Windows.FrameworkElement.ArrangeCore%2A> metody pro zpracování.  
  
 <xref:System.Windows.FrameworkElement.ArrangeCore%2A> Metoda vyhodnocuje <xref:System.Windows.UIElement.DesiredSize%2A> z podřízených a vyhodnocuje všechny další okraje, které může mít vliv na velikost vykreslené elementu. <xref:System.Windows.FrameworkElement.ArrangeCore%2A>generuje `arrangeSize`, který je předán <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metodu <xref:System.Windows.Controls.Panel> jako parametr. <xref:System.Windows.FrameworkElement.ArrangeOverride%2A>generuje `finalSize` podřízeného. Nakonec <xref:System.Windows.FrameworkElement.ArrangeCore%2A> metoda nemá posledním vyhodnocení posunutí vlastností, jako je například okraj a zarovnání a vloží podřízený objekt v rámci jeho rozložení slot. Podřízený objekt nemusí být (a často nemá) zadejte celý přidělené místo. Ovládací prvek je pak vrácen do nadřazené <xref:System.Windows.Controls.Panel> a dokončení procesu rozložení.  
  
<a name="LayoutSystem_PanelsCustom"></a>   
## <a name="panel-elements-and-custom-layout-behaviors"></a>Prvky panelů a chování vlastní rozložení  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]obsahuje skupinu elementů, které jsou odvozeny od <xref:System.Windows.Controls.Panel>. Tyto <xref:System.Windows.Controls.Panel> elementy povolit mnoho složitých rozložení. Například překrývání elementy lze snadno dosáhnout pomocí <xref:System.Windows.Controls.StackPanel> elementu, zatímco další komplexní a free průchodu rozložení je možné pomocí <xref:System.Windows.Controls.Canvas>.  
  
 Následující tabulka shrnuje dostupné rozložení <xref:System.Windows.Controls.Panel> elementy.  
  
|Název panelu|Popis|  
|----------------|-----------------|  
|<xref:System.Windows.Controls.Canvas>|Definuje oblast, ve kterém můžete explicitně umístit podřízené elementy souřadnicích vzhledem k <xref:System.Windows.Controls.Canvas> oblasti.|  
|<xref:System.Windows.Controls.DockPanel>|Definuje oblast, ve kterém můžete uspořádat podřízené elementy vodorovně nebo svisle, relativně k sobě navzájem.|  
|<xref:System.Windows.Controls.Grid>|Definuje oblast flexibilní mřížky, která se skládá z řádků a sloupců.|  
|<xref:System.Windows.Controls.StackPanel>|Podřízené elementy jsou uspořádány jeden řádek, který může být orientované vodorovně nebo svisle.|  
|<xref:System.Windows.Controls.VirtualizingPanel>|Poskytuje rozhraní pro <xref:System.Windows.Controls.Panel> prvky, které Virtualizovat jejich podřízené kolekce data. Toto je abstraktní třída.|  
|<xref:System.Windows.Controls.WrapPanel>|Pozice podřízených elementů v sekvenčních pozici od zleva doprava, narušující obsahu na další řádek na hranici obsahujícího pole. Následné řazení dochází postupně shora dolů nebo zprava doleva, v závislosti na hodnotě <xref:System.Windows.Controls.WrapPanel.Orientation%2A> vlastnost.|  
  
 Pro aplikace, které vyžadují rozložení, který není možné pomocí některé z předdefinovaných <xref:System.Windows.Controls.Panel> elementy, vlastní rozložení chování lze dosáhnout, která dědí z <xref:System.Windows.Controls.Panel> a přepsáním <xref:System.Windows.FrameworkElement.MeasureOverride%2A> a <xref:System.Windows.FrameworkElement.ArrangeOverride%2A> metody. Příklad, naleznete v části [vlastní paprskového panelu ukázkové](http://go.microsoft.com/fwlink/?LinkID=159982).  
  
<a name="LayoutSystem_Performance"></a>   
## <a name="layout-performance-considerations"></a>Faktory ovlivňující výkon rozložení  
 Rozložení je rekurzivní proces. Každý podřízený element v <xref:System.Windows.Controls.Panel.Children%2A> kolekce získá zpracovaných při každém volání systému rozložení. V důsledku toho spouštění systému rozložení je nutno při není nutné. Následující aspekty můžete dosáhnout lepšího výkonu.  
  
-   Pamatujte na které změn hodnot vlastností vynutí rekurzivní aktualizace systému rozložení.  
  
     Veřejné příznaky jsou označené vlastností závislostí, jejichž hodnoty může způsobit, že systém rozložení na inicializaci. <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A>a <xref:System.Windows.FrameworkPropertyMetadata.AffectsArrange%2A> poskytují užitečné různá vodítka, jehož vlastnost změny hodnot vynutí rekurzivního aktualizovat systém rozložení. Obecně platí, by měly mít jakákoli vlastnost, která může mít vliv na velikost pole ohraničující elementu <xref:System.Windows.FrameworkPropertyMetadata.AffectsMeasure%2A> příznak nastaven na hodnotu true. Další informace najdete v tématu [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
-   Pokud je to možné, používat <xref:System.Windows.UIElement.RenderTransform%2A> místo <xref:System.Windows.FrameworkElement.LayoutTransform%2A>.  
  
     A <xref:System.Windows.FrameworkElement.LayoutTransform%2A> může být velmi užitečný způsob, jak mít vliv na obsah [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)]. Ale pokud efekt transformace nemusí mít vliv na pozici další elementy, je nejvhodnější použít <xref:System.Windows.UIElement.RenderTransform%2A> místo, protože <xref:System.Windows.UIElement.RenderTransform%2A> nevyvolá rozložení systému. <xref:System.Windows.FrameworkElement.LayoutTransform%2A>použije jeho transformaci a vynutí se tak, že aktualizace rozložení rekurzivní účet pro nové pozice ovlivněný prvek.  
  
-   Zabránit zbytečných volání <xref:System.Windows.UIElement.UpdateLayout%2A>.  
  
     <xref:System.Windows.UIElement.UpdateLayout%2A> Metoda vynutí aktualizaci rozložení s rekurzivní a je často nezbytné. Pokud si nejste jistí, že je vyžadována úplná aktualizace, závisí na systému rozložení mohli volat tuto metodu za vás.  
  
-   Při práci s velkým <xref:System.Windows.Controls.Panel.Children%2A> kolekce, zvažte použití <xref:System.Windows.Controls.VirtualizingStackPanel> místo běžný <xref:System.Windows.Controls.StackPanel>.  
  
     Prostřednictvím virtualizace podřízené kolekce <xref:System.Windows.Controls.VirtualizingStackPanel> pouze ponechá objekty v paměti, které jsou aktuálně v rámci nadřazeného zobrazení. V důsledku toho podstatně vyšší výkon ve většině scénářů.  
  
<a name="LayoutSystem_LayoutRounding"></a>   
## <a name="sub-pixel-rendering-and-layout-rounding"></a>Vykreslování dílčí pixelů a zaokrouhlení rozložení  
 [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] Grafika systému používá jednotky nezávislé na zařízení, které nezávislost překlad IP adres a zařízení. Každé zařízení nezávislé pixelů automaticky škáluje s systému [!INCLUDE[TLA#tla_dpi](../../../../includes/tlasharptla-dpi-md.md)] nastavení. To poskytuje [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] správné škálování aplikací pro různé [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] nastavení a způsobí, že aplikace automaticky [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)]-vědět.  
  
 Ale to [!INCLUDE[TLA2#tla_dpi](../../../../includes/tla2sharptla-dpi-md.md)] nezávislost můžete vytvořit nestandardní edge vykreslování kvůli vyhlazení. Tyto artefakty, zpravidla se zobrazí jako rozmazaně nebo poloprůhledné hranami, může dojít, když umístění okraj spadá uprostřed pixelů zařízení místo mezi pixelů zařízení. Rozložení systém poskytuje způsob, jak nastavit pro tuto s zaokrouhlení rozložení. Rozložení zaokrouhlení je, kde systém rozložení zaokrouhlí žádné hodnoty bez integrální pixelů při průchodu rozložení.  
  
 Ve výchozím nastavení vypnutá zaokrouhlení rozložení. Chcete-li povolit zaokrouhlení rozložení, nastavte <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> vlastnost `true` na žádném <xref:System.Windows.FrameworkElement>. Protože je vlastnost závislosti, hodnota rozšíří na všechny podřízené objekty ve vizuálním stromu. Chcete-li povolit rozložení zaokrouhlení pro celý uživatelského rozhraní, nastavte <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A> k `true` na kořenový kontejner. Příklad naleznete v tématu <xref:System.Windows.FrameworkElement.UseLayoutRounding%2A>.  
  
<a name="LayoutSystem_whatsnext"></a>   
## <a name="whats-next"></a>Co je další  
 Pochopení, jak jsou elementy měří a uspořádané je prvním krokem při pochopení rozložení. Další informace o dostupných <xref:System.Windows.Controls.Panel> elementy, najdete v části [přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md). Chcete-li lépe pochopit různé umísťovací vlastnosti, které můžou ovlivnit rozložení, přečtěte si téma [zarovnání, okraje a odsazení přehled](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md). Příklad vlastní <xref:System.Windows.Controls.Panel> elementu, najdete v části [vlastní paprskového panelu ukázkové](http://go.microsoft.com/fwlink/?LinkID=159982). Až budete připraveni na všech součástí dohromady v šedé – aplikace, najdete v části [návod: Můj první desktopová aplikace WPF](../../../../docs/framework/wpf/getting-started/walkthrough-my-first-wpf-desktop-application.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.UIElement>  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Přehled zarovnání, okrajů a odsazení](../../../../docs/framework/wpf/advanced/alignment-margins-and-padding-overview.md)  
 [Rozložení a návrh](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)
