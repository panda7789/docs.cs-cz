---
title: "Přehled automatického rozložení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
caps.latest.revision: "22"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2c9f5b9a6665778bc313febb039aeeeb2e484a6c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="use-automatic-layout-overview"></a>Přehled automatického rozložení
Toto téma představuje pokyny pro vývojáře na tom, jak psát [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikace s lokalizovatelný [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]. V minulosti, lokalizace [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] byl časově náročný proces. Každý jazyk, který [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] byla přizpůsobena pro požadované úpravy po jednotlivých bodech. Dnes s správné návrhu a pravé kódování standardy, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] konstruovat tak, aby překladatelům při lokalizaci menší změny velikosti a přemístění udělat. Přístup pro zápis aplikace, které může být snadněji změněnou a přemístěných se nazývá Automatické rozložení a dosáhnout pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] návrh aplikace.  
  
<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a>Výhody používání automatického rozložení  
 Protože [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prezentace systém je výkonný a flexibilní, poskytuje schopnost rozložení prvky v aplikaci, která lze upravit podle požadavků různých jazyků. V následujícím seznamu bodů některé z výhod automatického rozložení.  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]zobrazí správně v libovolném jazyce.  
  
-   Snižuje nutnost po převádějí text se znovu pozice a velikosti ovládacích prvků.  
  
-   Snižuje nutnost znovu nastavte velikost okna.  
  
-   [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]rozložení vykreslí správně v libovolném jazyce.  
  
-   Lokalizace může snížit do bodu, že se jedná o něco více než řetězec překlad.  
  
<a name="autolayout_controls"></a>   
## <a name="automatic-layout-and-controls"></a>Automatické rozložení a ovládací prvky  
 Automatické rozložení povolí aplikaci automaticky upravit velikost ovládacího prvku. Například můžete změnit ovládacího prvku podle délky řetězce. Tato funkce umožňuje překladatelům při lokalizaci přeložit řetězec; už nemusí ke změně velikosti ovládacího prvku podle přeložený textu. Následující příklad vytvoří tlačítko s obsah v angličtině.  
  
 [!code-xaml[LocalizationBtn_snip#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn_snip/CS/Pane1.xaml#1)]  
  
 V příkladu, které budete muset udělat, aby byly španělské tlačítko je změna textu. Například  
  
 [!code-xaml[LocalizationBtn#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationBtn/CS/Pane1.xaml#1)]  
  
 Následující obrázek ukazuje výstup ukázky kódu.  
  
 ![Tlačítko stejné s textem v různých jazycích](../../../../docs/framework/wpf/advanced/media/globalizationbutton.png "GlobalizationButton")  
Tlačítko automaticky s možností změny velikosti  
  
<a name="autolayout_coding"></a>   
## <a name="automatic-layout-and-coding-standards"></a>Automatické rozložení a kódování standardy  
 Použití automatického rozložení přístup vyžaduje sadu standardy kódování a návrhu a pravidla k vytvoření plně lokalizovatelný [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Následující pokyny se podpoře kódování automatického rozložení.  
  
|Kódování standardy|Popis|  
|----------------------|-----------------|  
|Nepoužívejte absolutní umístění.|-Nepoužívejte <xref:System.Windows.Controls.Canvas> protože umisťuje elementy absolutně.<br />-Použít <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.Grid> na pozici ovládací prvky.<br />-Informace o různých typech panelů, naleznete v [přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md).|  
|Nenastavujte s pevnou velikostí pro okno.|-Použít <xref:System.Windows.Window.SizeToContent%2A>.<br />-Například:<br /><br /> [!code-xaml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]|  
|Přidat <xref:System.Windows.FrameworkElement.FlowDirection%2A>.|<ul><li>Přidat <xref:System.Windows.FrameworkElement.FlowDirection%2A> pro kořenový element vaší aplikace.</li><li>[!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)]poskytuje pohodlný způsob pro podporu vodorovné, obousměrné a svislém rozložení. V presentation framework <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost lze použít k definování rozložení. Směr toku vzory jsou:<br /><br /> <ul><li><xref:System.Windows.FlowDirection.LeftToRight>(LrTb) – vodorovném rozložení pro Latin, východoasijské a tak dále.</li><li><xref:System.Windows.FlowDirection.RightToLeft>(RlTb) – obousměrné arabština, hebrejština a tak dále.</li></ul></li></ul>|  
|Místo fyzické písem používejte složená písma.|<ul><li>Pomocí složeného písem <xref:System.Windows.Controls.Control.FontFamily%2A> vlastnost nemusí lokalizovat.</li><li>Vývojářům můžete použít jednu z následujících písem nebo vytvořit vlastní.<br /><br /> <ul><li>Globální uživatelské rozhraní</li><li>Serif globální sítě San</li><li>Globální Serif</li></ul></li></ul>|  
|Přidejte XML: lang.|-Přidat `xml:lang` atribut v kořenovém elementu vaše [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)], například `xml:lang="en-US"` pro angličtinu aplikaci.<br />-Vzhledem k tomu použít složená písma `xml:lang` Pokud chcete zjistit, jaká písma používat, nastavte tuto vlastnost na podporu více jazyků scénářů.|  
  
<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a>Automatické rozložení a mřížky  
 <xref:System.Windows.Controls.Grid> Elementu, je užitečné pro automatické rozložení, protože umožňuje vývojář na pozici elementy. A <xref:System.Windows.Controls.Grid> ovládací prvek je schopen distribuci dostupné místo mezi její podřízené elementy pomocí sloupců a řádků uspořádání. [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] Elementy může mít rozsah více buněk a je možné, že mřížky v rámci mřížky. Mřížky jsou užitečné, protože ty umožňují vytvořit a umístit je komplexní [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)]. Následující příklad ukazuje použití tabulky na pozici některé tlačítka a text. Všimněte si, že výška a šířka buněk jsou nastaveny na <xref:System.Windows.GridUnitType.Auto>; proto buňku, která obsahuje tlačítko s bitovou kopií upraví podle bitovou kopii.  
  
 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Následující obrázek znázorňuje mřížky vyprodukované předchozí kód.  
  
 ![Příklad mřížky](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Mřížka  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>Automatické rozložení a pomocí vlastnosti IsSharedSizeScope mřížky  
 A <xref:System.Windows.Controls.Grid> element je užitečné v lokalizovatelný aplikacím vytvořit ovládací prvky, které velikost podle obsahu. V některých případech ale budete chtít ovládacích prvků k udržování určité velikosti bez ohledu na obsah. Například pokud máte "OK", tlačítko Storno"a"Vyhledat"pravděpodobně nechcete, aby tlačítka přizpůsobí obsahu tlačítka. V takovém případě <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> přidružená vlastnost je užitečná sdílení stejné nastavení velikosti mezi více elementů mřížky. Následující příklad ukazuje, jak sdílet data mezi několika Změna velikosti řádků a sloupců <xref:System.Windows.Controls.Grid> elementy.  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **Poznámka:** kompletní příklad naleznete v části [sdílené složky pro změnu velikosti vlastnosti mezi mřížky](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)  
  
## <a name="see-also"></a>Viz také  
 [Globalizace pro grafický subsystém WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)  
 [Použití automatického rozložení pro vytvoření tlačítka](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)  
 [Pomocí automatického rozložení mřížky](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
