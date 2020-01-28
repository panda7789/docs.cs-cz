---
title: Optimalizace výkonu ovládacího prvku
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: d02fde7076cd6a24fdfb171ed54161b20f3d465e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746727"
---
# <a name="optimizing-performance-controls"></a>Optimalizace výkonu: ovládací prvky

Windows Presentation Foundation (WPF) zahrnuje mnoho běžných komponent uživatelského rozhraní (UI), které se používají ve většině aplikací pro Windows. Toto téma obsahuje techniky pro zlepšení výkonu uživatelského rozhraní.

## <a name="displaying-large-data-sets"></a>Zobrazení velkých datových sad

Ovládací prvky WPF, jako <xref:System.Windows.Controls.ListView> a <xref:System.Windows.Controls.ComboBox>, slouží k zobrazení seznamu položek v aplikaci. Pokud je seznam pro zobrazení velký, může to mít vliv na výkon aplikace. Je to proto, že standardní systém rozložení vytvoří kontejner rozložení pro každou položku přidruženou k ovládacímu prvku seznam a vypočte velikost a polohu rozložení. Obvykle není nutné zobrazovat všechny položky současně. místo toho se zobrazí podmnožina a uživatel se posouvá seznamem. V takovém případě má smysl použít *virtualizaci*uživatelského rozhraní, což znamená, že je generování kontejneru položek a přidruženého rozložení pro položku odloženo, dokud je položka viditelná.

Virtualizace uživatelského rozhraní je důležitým aspektem ovládacích prvků seznam. Virtualizace uživatelského rozhraní by se neměla zaměňovat s virtualizací dat. Virtualizace uživatelského rozhraní ukládá jenom viditelné položky v paměti, ale v případě vázání dat ukládá celou datovou strukturu do paměti. Virtualizace dat naopak ukládá pouze datové položky, které jsou viditelné na obrazovce v paměti.

Ve výchozím nastavení je virtualizace uživatelského rozhraní povolená pro <xref:System.Windows.Controls.ListView> a <xref:System.Windows.Controls.ListBox> ovládací prvky, když jsou jejich položky seznamu vázané na data. virtualizaci <xref:System.Windows.Controls.TreeView> lze povolit nastavením vlastnosti <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> připojené na `true`. Pokud chcete povolit virtualizaci uživatelského rozhraní pro vlastní ovládací prvky, které jsou odvozeny z <xref:System.Windows.Controls.ItemsControl> nebo existující ovládací prvky položek, které používají třídu <xref:System.Windows.Controls.StackPanel>, například <xref:System.Windows.Controls.ComboBox>, můžete <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> nastavit na <xref:System.Windows.Controls.VirtualizingStackPanel> a nastavit <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> na `true`. Pro tyto ovládací prvky ale můžete zakázat virtualizaci uživatelského rozhraní bez nutnosti jejich použití. Níže je seznam podmínek, které zakazují virtualizaci uživatelského rozhraní.

- Kontejnery položek jsou přidány přímo do <xref:System.Windows.Controls.ItemsControl>. Například pokud aplikace explicitně přidá <xref:System.Windows.Controls.ListBoxItem> objektů do <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListBox> nevirtualizuje objekty <xref:System.Windows.Controls.ListBoxItem>.

- Kontejnery položek v <xref:System.Windows.Controls.ItemsControl> jsou různých typů. Například <xref:System.Windows.Controls.Menu>, který používá <xref:System.Windows.Controls.Separator> objektů, nemůže implementovat recyklaci položek, protože <xref:System.Windows.Controls.Menu> obsahuje objekty typu <xref:System.Windows.Controls.Separator> a <xref:System.Windows.Controls.MenuItem>.

- Nastavení <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> na `false`.

- Nastavení <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> na `false`.

Důležitým aspektem při virtualizaci kontejnerů položek je, zda máte k dispozici další informace o stavu přidružené k kontejneru položek, který patří k položce. V takovém případě musíte uložit další stav. Například můžete mít položku obsaženou v ovládacím prvku <xref:System.Windows.Controls.Expander> a stav <xref:System.Windows.Controls.Expander.IsExpanded%2A> je vázán na kontejner položky, nikoli na samotné položky. Pokud je kontejner znovu použit pro novou položku, je pro novou položku použita aktuální hodnota <xref:System.Windows.Controls.Expander.IsExpanded%2A>. Původní položka navíc ztratí správnou hodnotu <xref:System.Windows.Controls.Expander.IsExpanded%2A>.

V současné době žádné ovládací prvky WPF nenabízejí integrovanou podporu pro virtualizaci dat.

## <a name="container-recycling"></a>Recyklace kontejneru

Optimalizace virtualizace uživatelského rozhraní přidaná v .NET Framework 3,5 SP1 pro ovládací prvky, které dědí z <xref:System.Windows.Controls.ItemsControl> je *recyklace kontejneru,* což může také zlepšit výkon při posouvání. Když je naplněna <xref:System.Windows.Controls.ItemsControl>, která používá virtualizaci uživatelského rozhraní, vytvoří kontejner položky pro každou položku, která se posune k zobrazení, a odstraní kontejner položek pro každou položku, která se posouvá mimo zobrazení. *Recyklace kontejneru* umožňuje ovládacímu prvku znovu použít existující kontejnery položek pro různé datové položky, aby se kontejnery položek nevytvářely trvale a nezničily, když uživatel posune <xref:System.Windows.Controls.ItemsControl>. Můžete zvolit povolení recyklace položek nastavením vlastnosti <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> připojeno na <xref:System.Windows.Controls.VirtualizationMode.Recycling>.

Všechny <xref:System.Windows.Controls.ItemsControl> podporující virtualizaci mohou použít recyklaci kontejneru. Příklad, jak povolit recyklaci kontejneru na <xref:System.Windows.Controls.ListBox>, najdete v tématu [zlepšení výkonu posouvání objektu ListBox](../controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).

## <a name="supporting-bidirectional-virtualization"></a>Podpora obousměrné virtualizace

<xref:System.Windows.Controls.VirtualizingStackPanel> nabízí integrovanou podporu pro virtualizaci uživatelského rozhraní v jednom směru, a to buď vodorovně nebo svisle. Pokud chcete pro ovládací prvky použít obousměrnou virtualizaci, je nutné implementovat vlastní panel, který rozšiřuje třídu <xref:System.Windows.Controls.VirtualizingStackPanel>. Třída <xref:System.Windows.Controls.VirtualizingStackPanel> zpřístupňuje virtuální metody, jako jsou <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>a <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>. Tyto virtuální metody umožňují detekovat změnu v viditelné části seznamu a odpovídajícím způsobem je zpracovat.

## <a name="optimizing-templates"></a>Optimalizace šablon

Vizuální strom obsahuje všechny vizuální prvky v aplikaci. Kromě objektů, které byly vytvořeny přímo, obsahuje také objekty z důvodu rozšíření šablony. Například při vytváření <xref:System.Windows.Controls.Button>získáte také objekty <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> a <xref:System.Windows.Controls.ContentPresenter> ve vizuálním stromu. Pokud jste neoptimalizované šablony ovládacích prvků, je možné, že ve vizuálním stromu vytvoříte hodně dalších zbytečných objektů. Další informace o vizuálním stromu naleznete v tématu [Přehled vykreslování grafiky WPF](../graphics-multimedia/wpf-graphics-rendering-overview.md).

## <a name="deferred-scrolling"></a>Odložené posouvání

Ve výchozím nastavení, když uživatel přetáhne jezdce na posuvník, zobrazení obsahu se průběžně aktualizuje. Pokud je posouvání v ovládacím prvku pomalé, zvažte použití odloženého posouvání. V odloženém posouvání se obsah aktualizuje pouze v případě, že uživatel uvolní palec.

K implementaci odloženého posouvání nastavte vlastnost <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> na `true`. <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> je připojená vlastnost a lze ji nastavit na <xref:System.Windows.Controls.ScrollViewer> a jakýkoli ovládací prvek, který má <xref:System.Windows.Controls.ScrollViewer> v šabloně ovládacího prvku.

## <a name="controls-that-implement-performance-features"></a>Ovládací prvky, které implementují funkce výkonu

V následující tabulce jsou uvedeny běžné ovládací prvky pro zobrazování dat a jejich podporu funkcí výkonu. V předchozích částech najdete informace o tom, jak tyto funkce povolit.

|Control|Virtualizace|Recyklace kontejneru|Odložené posouvání|
|-------------|--------------------|-------------------------|------------------------|
|<xref:System.Windows.Controls.ComboBox>|Dá se povolit|Dá se povolit|Dá se povolit|
|<xref:System.Windows.Controls.ContextMenu>|Dá se povolit|Dá se povolit|Dá se povolit|
|<xref:System.Windows.Controls.DocumentViewer>|Není k dispozici|Není k dispozici|Dá se povolit|
|<xref:System.Windows.Controls.ListBox>|Výchozí|Dá se povolit|Dá se povolit|
|<xref:System.Windows.Controls.ListView>|Výchozí|Dá se povolit|Dá se povolit|
|<xref:System.Windows.Controls.TreeView>|Dá se povolit|Dá se povolit|Dá se povolit|
|<xref:System.Windows.Controls.ToolBar>|Není k dispozici|Není k dispozici|Dá se povolit|

> [!NOTE]
> Příklad toho, jak povolit virtualizaci a recyklaci kontejneru na <xref:System.Windows.Controls.TreeView>, najdete v tématu [zlepšení výkonu prvku TreeView](../controls/how-to-improve-the-performance-of-a-treeview.md).

## <a name="see-also"></a>Viz také:

- [Rozložení](layout.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Ovládací prvky](../controls/index.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
