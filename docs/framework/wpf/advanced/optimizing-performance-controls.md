---
title: Optimalizace výkonu ovládacího prvku
description: Windows Presentation Foundation obsahuje mnoho běžných součástí, které se používají ve většině aplikací pro Windows. Přečtěte si, jak vylepšit výkon uživatelského rozhraní.
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: de348dd93e5710b5b81af035ec7aa56e01dc4981
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168309"
---
# <a name="optimizing-performance-controls"></a>Optimalizace výkonu: ovládací prvky

Windows Presentation Foundation (WPF) zahrnuje mnoho běžných komponent uživatelského rozhraní (UI), které se používají ve většině aplikací pro Windows. Toto téma obsahuje techniky pro zlepšení výkonu uživatelského rozhraní.

## <a name="displaying-large-data-sets"></a>Zobrazení velkých datových sad

Ovládací prvky WPF, jako jsou <xref:System.Windows.Controls.ListView> a, <xref:System.Windows.Controls.ComboBox> slouží k zobrazení seznamu položek v aplikaci. Pokud je seznam pro zobrazení velký, může to mít vliv na výkon aplikace. Je to proto, že standardní systém rozložení vytvoří kontejner rozložení pro každou položku přidruženou k ovládacímu prvku seznam a vypočte velikost a polohu rozložení. Obvykle není nutné zobrazovat všechny položky současně. místo toho se zobrazí podmnožina a uživatel se posouvá seznamem. V takovém případě má smysl použít *virtualizaci*uživatelského rozhraní, což znamená, že je generování kontejneru položek a přidruženého rozložení pro položku odloženo, dokud je položka viditelná.

Virtualizace uživatelského rozhraní je důležitým aspektem ovládacích prvků seznam. Virtualizace uživatelského rozhraní by se neměla zaměňovat s virtualizací dat. Virtualizace uživatelského rozhraní ukládá jenom viditelné položky v paměti, ale v případě vázání dat ukládá celou datovou strukturu do paměti. Virtualizace dat naopak ukládá pouze datové položky, které jsou viditelné na obrazovce v paměti.

Ve výchozím nastavení je virtualizace uživatelského rozhraní povolena <xref:System.Windows.Controls.ListView> pro <xref:System.Windows.Controls.ListBox> ovládací prvky a, pokud jsou jejich položky seznamu vázány na data. <xref:System.Windows.Controls.TreeView>virtualizaci je možné povolit nastavením <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> připojené vlastnosti na `true` . Pokud chcete povolit virtualizaci uživatelského rozhraní pro vlastní ovládací prvky, které jsou odvozeny z <xref:System.Windows.Controls.ItemsControl> nebo existující ovládací prvky položek, které používají <xref:System.Windows.Controls.StackPanel> třídu, například <xref:System.Windows.Controls.ComboBox> , můžete nastavit na <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> <xref:System.Windows.Controls.VirtualizingStackPanel> a nastavit na <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> `true` . Pro tyto ovládací prvky ale můžete zakázat virtualizaci uživatelského rozhraní bez nutnosti jejich použití. Níže je seznam podmínek, které zakazují virtualizaci uživatelského rozhraní.

- Kontejnery položek jsou přidány přímo do <xref:System.Windows.Controls.ItemsControl> . Například pokud aplikace explicitně přidá <xref:System.Windows.Controls.ListBoxItem> objekty do <xref:System.Windows.Controls.ListBox> , <xref:System.Windows.Controls.ListBox> nevirtualizuje <xref:System.Windows.Controls.ListBoxItem> objekty.

- Kontejnery položek v <xref:System.Windows.Controls.ItemsControl> existují v různých typech. Například objekt <xref:System.Windows.Controls.Menu> , který používá <xref:System.Windows.Controls.Separator> objekty, nemůže implementovat recyklaci položky, protože <xref:System.Windows.Controls.Menu> obsahuje objekty typu <xref:System.Windows.Controls.Separator> a <xref:System.Windows.Controls.MenuItem> .

- Nastavení <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> na `false` .

- Nastavení <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> na `false` .

Důležitým aspektem při virtualizaci kontejnerů položek je, zda máte k dispozici další informace o stavu přidružené k kontejneru položek, který patří k položce. V takovém případě musíte uložit další stav. Například můžete mít položku obsaženou v <xref:System.Windows.Controls.Expander> ovládacím prvku a <xref:System.Windows.Controls.Expander.IsExpanded%2A> stav je vázán na kontejner položky, nikoli na samotné položky. Pokud je kontejner znovu použit pro novou položku, <xref:System.Windows.Controls.Expander.IsExpanded%2A> je pro novou položku použita aktuální hodnota. Původní položka navíc ztratí správnou <xref:System.Windows.Controls.Expander.IsExpanded%2A> hodnotu.

V současné době žádné ovládací prvky WPF nenabízejí integrovanou podporu pro virtualizaci dat.

## <a name="container-recycling"></a>Recyklace kontejneru

Optimalizace virtualizace uživatelského rozhraní přidaná v .NET Framework 3,5 SP1 pro ovládací prvky, které dědí z <xref:System.Windows.Controls.ItemsControl> je *recyklace kontejneru,* což může také zlepšit výkon při posouvání. Když <xref:System.Windows.Controls.ItemsControl> je naplněna aplikace, která používá virtualizaci uživatelského rozhraní, vytvoří kontejner položky pro každou položku, která se posune k zobrazení, a odstraní kontejner položek pro každou položku, která se posouvá mimo zobrazení. *Recyklace kontejneru* umožňuje ovládacímu prvku znovu použít existující kontejnery položek pro různé datové položky, aby se kontejnery položek nevytvářely trvale a nezničily, když uživatel posune <xref:System.Windows.Controls.ItemsControl> . Můžete zvolit povolení recyklace položek nastavením <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> připojené vlastnosti na <xref:System.Windows.Controls.VirtualizationMode.Recycling> .

Každý <xref:System.Windows.Controls.ItemsControl> , který podporuje virtualizaci, může použít recyklaci kontejneru. Příklad, jak povolit recyklaci kontejneru v <xref:System.Windows.Controls.ListBox> , naleznete v tématu [zlepšení výkonu posouvání objektu ListBox](../controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).

## <a name="supporting-bidirectional-virtualization"></a>Podpora obousměrné virtualizace

<xref:System.Windows.Controls.VirtualizingStackPanel>nabízí integrovanou podporu pro virtualizaci uživatelského rozhraní v jednom směru, a to buď vodorovně, nebo svisle. Pokud chcete pro ovládací prvky použít obousměrnou virtualizaci, je nutné implementovat vlastní panel, který rozšiřuje <xref:System.Windows.Controls.VirtualizingStackPanel> třídu. <xref:System.Windows.Controls.VirtualizingStackPanel>Třída zveřejňuje virtuální metody, jako <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A> jsou, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A> , <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A> a <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A> . Tyto virtuální metody umožňují detekovat změnu v viditelné části seznamu a odpovídajícím způsobem je zpracovat.

## <a name="optimizing-templates"></a>Optimalizace šablon

Vizuální strom obsahuje všechny vizuální prvky v aplikaci. Kromě objektů, které byly vytvořeny přímo, obsahuje také objekty z důvodu rozšíření šablony. Například při vytváření <xref:System.Windows.Controls.Button> můžete také získat <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> a <xref:System.Windows.Controls.ContentPresenter> objekty ve vizuálním stromu. Pokud jste neoptimalizované šablony ovládacích prvků, je možné, že ve vizuálním stromu vytvoříte hodně dalších zbytečných objektů. Další informace o vizuálním stromu naleznete v tématu [Přehled vykreslování grafiky WPF](../graphics-multimedia/wpf-graphics-rendering-overview.md).

## <a name="deferred-scrolling"></a>Odložené posouvání

Ve výchozím nastavení, když uživatel přetáhne jezdce na posuvník, zobrazení obsahu se průběžně aktualizuje. Pokud je posouvání v ovládacím prvku pomalé, zvažte použití odloženého posouvání. V odloženém posouvání se obsah aktualizuje pouze v případě, že uživatel uvolní palec.

Pro implementaci odloženého posouvání nastavte <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> vlastnost na hodnotu `true` . <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A>je připojená vlastnost, kterou lze nastavit na <xref:System.Windows.Controls.ScrollViewer> a všechny ovládací prvky, které mají <xref:System.Windows.Controls.ScrollViewer> v šabloně ovládacího prvku.

## <a name="controls-that-implement-performance-features"></a>Ovládací prvky, které implementují funkce výkonu

V následující tabulce jsou uvedeny běžné ovládací prvky pro zobrazování dat a jejich podporu funkcí výkonu. V předchozích částech najdete informace o tom, jak tyto funkce povolit.

|Řízení|Virtualizace|Recyklace kontejneru|Odložené posouvání|
|-------------|--------------------|-------------------------|------------------------|
|<xref:System.Windows.Controls.ComboBox>|Dá se povolit|Dá se povolit|Dá se povolit|
|<xref:System.Windows.Controls.ContextMenu>|Dá se povolit|Dá se povolit|Dá se povolit|
|<xref:System.Windows.Controls.DocumentViewer>|Není k dispozici|Není k dispozici|Dá se povolit|
|<xref:System.Windows.Controls.ListBox>|Výchozí|Dá se povolit|Dá se povolit|
|<xref:System.Windows.Controls.ListView>|Výchozí|Dá se povolit|Dá se povolit|
|<xref:System.Windows.Controls.TreeView>|Dá se povolit|Dá se povolit|Dá se povolit|
|<xref:System.Windows.Controls.ToolBar>|Není k dispozici|Není k dispozici|Dá se povolit|

> [!NOTE]
> Příklad toho, jak povolit virtualizaci a recyklaci kontejneru na <xref:System.Windows.Controls.TreeView> , najdete v tématu [zlepšení výkonu prvku TreeView](../controls/how-to-improve-the-performance-of-a-treeview.md).

## <a name="see-also"></a>Viz také

- [Rozložení](layout.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Ovládací prvky](../controls/index.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
