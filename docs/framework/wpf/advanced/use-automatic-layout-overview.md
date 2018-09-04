---
title: Přehled automatického rozložení
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: a43b3c0e008025171e3b1fdeba3bc514d01e28c8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43542621"
---
# <a name="use-automatic-layout-overview"></a>Přehled automatického rozložení
Toto téma popisuje pokyny pro vývojáře na tom, jak psát [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací s lokalizovatelné [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]. V minulosti, lokalizace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] bylo časově náročný proces. Každý jazyk, který [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] byl upraven pro požadované úpravy podle pixelů. Dnes s správný návrh a pravá standardy kódování, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] lze sestavit tak, aby Lokalizátoři menší změny velikosti a přemístění provést. Přístup k vytváření aplikací, které se dají snadno změněnou velikostí a přemístěných nazývá Automatické rozložení a lze dosáhnout pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] návrhu aplikace.  
  
<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a>Mezi výhody používání automatického rozložení  
 Vzhledem k tomu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prezentační systém je výkonná a flexibilní, poskytuje schopnost rozložení prvků v aplikaci, která je možné upravit podle požadavků různých jazycích. Následující seznam ukazuje některé z výhod automatické rozložení.  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Zobrazí také v jakémkoli jazyce.  
  
-   Snižuje nutnost znovu nastavte pozici a velikost ovládacích prvků po přeložený text.  
  
-   Snižuje nutnost přizpůsobit velikosti okna.  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] rozložení vykreslí správně v libovolném jazyce.  
  
-   Lokalizace lze snížit, že se jedná o něco více než řetězec překladu bodu.  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a>Automatické rozložení a ovládací prvky  
 Automatické rozložení umožňuje aplikaci automaticky upravte velikost ovládacího prvku. Například ovládací prvek můžete změnit tak, aby vyhovovaly délku řetězce. Tato možnost umožňuje Lokalizátoři převodu řetězec. už nepotřebujete pro změnu velikosti ovládacího prvku podle přeložený text. Následující příklad vytvoří tlačítko s anglickým obsahem.  
  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 V příkladu jediné, co musíte udělat, aby Španělština tlačítko se změní celý text. Například  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Následující obrázek ukazuje výstup z ukázek kódu.  
  
 ![Stejné tlačítko s textem v různých jazycích](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Tlačítko automaticky umožňující změnu velikosti  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a>Automatické rozložení a standardy kódování  
 Pomocí automatického rozložení přístup vyžaduje sadu standardy kódování a návrhu a pravidla, která vytvoří plně lokalizovatelné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Následující pokyny vám pomůže automatické rozložení psaní kódu.  
  
| Standardy kódování | Popis |
| ---------------------- | ----------------- |
| Nepoužívejte absolutní umístění. | <ul><li>Nepoužívejte <xref:System.Windows.Controls.Canvas> protože naprosto umístí prvky.</li><li>Použití <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.Grid> umístěte ovládací prvky.</li><li>Informace o různých typech panelů najdete v článku [přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md).</li></ul> |
| Nenastavujte pevně danou velikost okna. | – Použijte <xref:System.Windows.Window.SizeToContent%2A>.<br />Příklad:<br /><br /> [!code-xaml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)] |
| Přidat <xref:System.Windows.FrameworkElement.FlowDirection%2A>. | <ul><li>Přidat <xref:System.Windows.FrameworkElement.FlowDirection%2A> do kořenového elementu vaší aplikace.</li><li>WPF poskytuje pohodlný způsob, jak podporovat vodorovné, obousměrné a svislé rozložení. V rámci prezentace <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost lze použít k definování rozložení. Směr toku vzorky jsou:<br /><br /> <ul><li><xref:System.Windows.FlowDirection.LeftToRight> (LrTb) – vodorovné rozložení pro latinka, východní Asie a tak dále.</li><li><xref:System.Windows.FlowDirection.RightToLeft> (RlTb) – obousměrné pro arabština, hebrejština a tak dále.</li></ul></li></ul> |
| Místo fyzických písma používejte složená písma. | <ul><li>S složená písma <xref:System.Windows.Controls.Control.FontFamily%2A> vlastnost nemusí být lokalizována.</li><li>Vývojáře můžou použít jednu z následujících písma nebo vytvořit svoje vlastní.<br /><br /> <ul><li>Globální uživatelské rozhraní</li><li>Serif globální sítě San</li><li>Globální Serif</li></ul></li></ul> |
| Přidáte XML: lang. | <ul><li>Přidat `xml:lang` atribut do kořenového elementu vaše [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], například `xml:lang="en-US"` anglické aplikace.</li><li>Vzhledem k tomu použít složená písma `xml:lang` Pokud chcete zjistit, jaká písma používat, nastavte tuto vlastnost na podporu více jazyků scénářů.</li></ul> |
  
<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a>Automatické rozložení a mřížky  
 <xref:System.Windows.Controls.Grid> Elementu, je užitečná pro automatické rozložení, protože umožňuje vývojářům umístění prvků. A <xref:System.Windows.Controls.Grid> ovládací prvek je schopen distribuci k dispozici prostor mezi jeho podřízené prvky použitím uspořádání sloupců a řádků. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Prvků může zahrnovat více buněk, a je možné mít mřížky v rámci mřížky. Mřížky jsou užitečné, protože umožňují vytvářet a umístěte komplexní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Následující příklad ukazuje použití tabulky na pozici některá tlačítka a text. Všimněte si, že výšku a šířku buňky jsou nastaveny na <xref:System.Windows.GridUnitType.Auto>; proto se upraví na buňku, která obsahuje tlačítko s imagí podle obrázku.  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Následující obrázek znázorňuje mřížky vytvořený v předchozím kódu.  
  
 ![Grid – příklad](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Mřížka  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>Automatické rozložení a pomocí vlastnosti IsSharedSizeScope mřížky  
 A <xref:System.Windows.Controls.Grid> prvek je užitečný v lokalizovatelných aplikacích vytvořit ovládací prvky, které se přizpůsobí zobrazení celého obsahu. V některých případech ale budete chtít ovládacích prvků pro udržování určité velikosti, bez ohledu na obsah. Například pokud máte "OK", "Storno" a "Procházet" pravděpodobně nechcete, aby tlačítka velikosti podle obsahu tlačítka. V tomto případě <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> připojená vlastnost je užitečná pro sdílení stejné velikosti mezi mnohonásobné elementy mřížky. Následující příklad ukazuje, jak sdílet data mezi více změny velikosti řádků a sloupců <xref:System.Windows.Controls.Grid> elementy.  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **Poznámka:** kompletní vzorek kódu, naleznete v tématu [sdílené složky velikosti vlastnosti mezi mřížkami](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)  
  
## <a name="see-also"></a>Viz také  
 [Globalizace pro WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Vytvoření tlačítka pomocí automatického rozložení](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [Automatické rozložení použitím mřížky](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
