---
title: Přehled automatického rozložení
ms.date: 03/30/2017
helpviewer_keywords:
- layout [WPF], automatic
- automatic layout [WPF]
ms.assetid: 6fed9264-18bb-4d05-8867-1fe356c6f687
ms.openlocfilehash: 4cb351b0db83bd83c17aa4aca004b310dc957437
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54609600"
---
# <a name="use-automatic-layout-overview"></a>Přehled automatického rozložení
Toto téma popisuje pokyny pro vývojáře na tom, jak psát [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] aplikací s lokalizovatelné [!INCLUDE[TLA#tla_ui#plural](../../../../includes/tlasharptla-uisharpplural-md.md)]. Lokalizace uživatelského rozhraní v minulosti bylo časově náročný proces. Každý jazyk, který byl přizpůsobit uživatelské rozhraní pro požadované úpravy podle pixelů. Dnes s správný návrh a pravá standardy kódování, [!INCLUDE[TLA2#tla_ui#plural](../../../../includes/tla2sharptla-uisharpplural-md.md)] lze sestavit tak, aby Lokalizátoři menší změny velikosti a přemístění provést. Přístup k vytváření aplikací, které se dají snadno změněnou velikostí a přemístěných nazývá Automatické rozložení a lze dosáhnout pomocí [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] návrhu aplikace.  

<a name="advantages_of_autolayout"></a>   
## <a name="advantages-of-using-automatic-layout"></a>Mezi výhody používání automatického rozložení  
 Vzhledem k tomu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] prezentační systém je výkonná a flexibilní, poskytuje schopnost rozložení prvků v aplikaci, která je možné upravit podle požadavků různých jazycích. Následující seznam ukazuje některé z výhod automatické rozložení.  

-   Uživatelské rozhraní zobrazí také v jakémkoli jazyce.  

-   Snižuje nutnost znovu nastavte pozici a velikost ovládacích prvků po přeložený text.  
  
-   Snižuje nutnost přizpůsobit velikosti okna.  

-   Uživatelské rozhraní rozložení vykreslí správně v libovolném jazyce.  

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
 Pomocí automatického rozložení přístup vyžaduje sadu psaní kódu a návrhu normy a pravidla, která vytvoří plně lokalizovatelné uživatelského rozhraní. Následující pokyny vám pomůže automatické rozložení psaní kódu.  

**Nepoužívejte absolutní umístění**

- Nepoužívejte <xref:System.Windows.Controls.Canvas> protože naprosto umístí prvky.

- Použití <xref:System.Windows.Controls.DockPanel>, <xref:System.Windows.Controls.StackPanel>, a <xref:System.Windows.Controls.Grid> umístěte ovládací prvky.

Informace o různých typech panelů najdete v článku [přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md).

**Nenastavujte pevně danou velikost okna**

- Použití <xref:System.Windows.Window.SizeToContent%2A?displayProperty=nameWithType>. Příklad:

   [!code-xaml[LocalizationGrid#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#2)]

**Přidat <xref:System.Windows.FrameworkElement.FlowDirection%2A>**

- Přidat <xref:System.Windows.FrameworkElement.FlowDirection%2A> do kořenového elementu vaší aplikace.

   WPF poskytuje pohodlný způsob, jak podporovat vodorovné, obousměrné a svislé rozložení. V rámci prezentace <xref:System.Windows.FrameworkElement.FlowDirection%2A> vlastnost lze použít k definování rozložení. Směr toku vzorky jsou:
   
     - <xref:System.Windows.FlowDirection.LeftToRight?displayProperty=nameWithType> (LrTb) – vodorovné rozložení pro latinka, východní Asie a tak dále.
     
     - <xref:System.Windows.FlowDirection.RightToLeft?displayProperty=nameWithType> (RlTb) – obousměrné pro arabština, hebrejština a tak dále.

**Složená písma nahrazujícím fyzické písma**

- S složená písma <xref:System.Windows.Controls.Control.FontFamily%2A> vlastnost nemusí být lokalizována.

- Vývojáře můžou použít jednu z následujících písma nebo vytvořit svoje vlastní.

   - Globální uživatelské rozhraní
   - Global San Serif
   - Globální Serif

**XML: lang – přidat**

- Přidat `xml:lang` atribut v kořenovém prvku uživatelského rozhraní, jako například `xml:lang="en-US"` anglické aplikace.

- Vzhledem k tomu použít složená písma `xml:lang` Pokud chcete zjistit, jaká písma používat, nastavte tuto vlastnost na podporu více jazyků scénářů.

<a name="autolay_grids"></a>   
## <a name="automatic-layout-and-grids"></a>Automatické rozložení a mřížky  
 <xref:System.Windows.Controls.Grid> Elementu, je užitečná pro automatické rozložení, protože umožňuje vývojářům umístění prvků. A <xref:System.Windows.Controls.Grid> ovládací prvek je schopen distribuci k dispozici prostor mezi jeho podřízené prvky použitím uspořádání sloupců a řádků. Prvky uživatelského rozhraní může zahrnovat více buněk, a je možné mít mřížky v rámci mřížky. Mřížky jsou užitečné, protože umožňují vytvářet a umístěte komplexní uživatelského rozhraní. Následující příklad ukazuje použití tabulky na pozici některá tlačítka a text. Všimněte si, že výšku a šířku buňky jsou nastaveny na <xref:System.Windows.GridUnitType.Auto>; proto se upraví na buňku, která obsahuje tlačítko s imagí podle obrázku.  

 [!code-xaml[LocalizationGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/LocalizationGrid/CS/Pane1.xaml#1)]  
  
 Následující obrázek znázorňuje mřížky vytvořený v předchozím kódu.  
  
 ![Grid – příklad](../../../../docs/framework/wpf/advanced/media/glob-grid.png "glob_grid")  
Mřížka  
  
<a name="autolay_grids_issharedsizescope"></a>   
## <a name="automatic-layout-and-grids-using-the-issharedsizescope-property"></a>Automatické rozložení a pomocí vlastnosti IsSharedSizeScope mřížky  
 A <xref:System.Windows.Controls.Grid> prvek je užitečný v lokalizovatelných aplikacích vytvořit ovládací prvky, které se přizpůsobí zobrazení celého obsahu. V některých případech ale budete chtít ovládacích prvků pro udržování určité velikosti, bez ohledu na obsah. Například pokud máte "OK", "Storno" a "Procházet" pravděpodobně nechcete, aby tlačítka velikosti podle obsahu tlačítka. V tomto případě <xref:System.Windows.Controls.Grid.IsSharedSizeScope%2A?displayProperty=nameWithType> připojená vlastnost je užitečná pro sdílení stejné velikosti mezi mnohonásobné elementy mřížky. Následující příklad ukazuje, jak sdílet data mezi více změny velikosti řádků a sloupců <xref:System.Windows.Controls.Grid> elementy.  
  
 [!code-xaml[gridIssharedsizescopeProp#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridIssharedsizescopeProp/CSharp/Window1.xaml#2)]  
  
 **Poznámka:** kompletní vzorek kódu, naleznete v tématu [sdílené složky velikosti vlastnosti mezi mřížkami](../../../../docs/framework/wpf/controls/how-to-share-sizing-properties-between-grids.md)  
  
## <a name="see-also"></a>Viz také:
- [Globalizace pro WPF](../../../../docs/framework/wpf/advanced/globalization-for-wpf.md)
- [Vytvoření tlačítka pomocí automatického rozložení](../../../../docs/framework/wpf/advanced/how-to-use-automatic-layout-to-create-a-button.md)
- [Automatické rozložení použitím mřížky](../../../../docs/framework/wpf/advanced/how-to-use-a-grid-for-automatic-layout.md)
