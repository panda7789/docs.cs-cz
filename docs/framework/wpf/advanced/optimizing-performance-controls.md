---
title: 'Optimalizace výkonu: Ovládací prvky – WPF'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: 1e291e1638864176913342d02acad092f561789c
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65645686"
---
# <a name="optimizing-performance-controls"></a>Optimalizace výkonu: Ovládací prvky

Windows Presentation Foundation (WPF) obsahuje mnoho běžných součásti uživatelského rozhraní (UI), které se používají ve většině aplikací Windows. Toto téma obsahuje postupy pro zlepšení výkonu uživatelského rozhraní.

## <a name="displaying-large-data-sets"></a>Zobrazování velkých sad dat

Například ovládací prvky WPF <xref:System.Windows.Controls.ListView> a <xref:System.Windows.Controls.ComboBox> slouží k zobrazení seznamu položek v aplikaci. Pokud k zobrazení seznamu je velká, může být ovlivněn výkon vaší aplikace. Toto je vzhledem k tomu, že systém standardní rozložení vytvoří kontejner rozložení pro každou položku přidružený k ovládacímu prvku seznam a vypočítá jeho velikost rozložení a umístění. Obvykle není nutné k zobrazení všech položek ve stejnou dobu; Místo toho zobrazí podmnožinu, a uživatel procházení seznamu. V takovém případě je vhodné použít uživatelské rozhraní *virtualizace*, což znamená, že generování položky kontejneru a související výpočet rozložení pro položku je odloženo, dokud je položka viditelná.

Virtualizace uživatelského rozhraní je důležitou součástí seznamu ovládacích prvků. Virtualizace uživatelského rozhraní, neměly by být zaměňovány s virtualizací data. Uživatelské rozhraní virtualizace úložiště jenom viditelné položky v paměti, ale v případě vázání dat ukládá celé datové struktury v paměti. Naproti tomu virtualizace dat ukládá pouze datové položky, které jsou viditelné na obrazovce v paměti.

Ve výchozím nastavení, je povolena virtualizace uživatelského rozhraní pro <xref:System.Windows.Controls.ListView> a <xref:System.Windows.Controls.ListBox> řídí, kdy jejich položky seznamu jsou vázány na data. <xref:System.Windows.Controls.TreeView> virtualizace se dá nastavit tak, že nastavíte <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> připojené vlastnosti `true`. Pokud chcete povolit virtualizaci uživatelského rozhraní pro vlastní ovládací prvky, které jsou odvozeny z <xref:System.Windows.Controls.ItemsControl> nebo existující položku Ovládací prvky, které používají <xref:System.Windows.Controls.StackPanel> třídy, jako například <xref:System.Windows.Controls.ComboBox>, můžete nastavit <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> k <xref:System.Windows.Controls.VirtualizingStackPanel> a nastavte <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> k `true`. Virtualizace uživatelského rozhraní pro tyto ovládací prvky můžete zakázat bohužel nevěděli ho. Následuje seznam podmínek, které zakázat uživatelské rozhraní virtualizace.

- Kontejnerů prvku se přidají přímo <xref:System.Windows.Controls.ItemsControl>. Například, pokud aplikace explicitně přidá <xref:System.Windows.Controls.ListBoxItem> objektů do <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListBox> nelze Virtualizovat <xref:System.Windows.Controls.ListBoxItem> objekty.

- Kontejnery v položce <xref:System.Windows.Controls.ItemsControl> jsou jiného typu. Například <xref:System.Windows.Controls.Menu> , která používá <xref:System.Windows.Controls.Separator> objektů nemůže implementovat položky recyklace, protože <xref:System.Windows.Controls.Menu> obsahuje objekty typu <xref:System.Windows.Controls.Separator> a <xref:System.Windows.Controls.MenuItem>.

- Nastavení <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> k `false`.

- Nastavení <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A> k `false`.

Což je důležité při virtualizaci kontejnerů prvku se, jestli máte informace o dalších stavu přidružené kontejner položek, které patří k položce. V takovém případě musíte uložit další stav. Například můžete mít položka obsažená v <xref:System.Windows.Controls.Expander> ovládacího prvku a <xref:System.Windows.Controls.Expander.IsExpanded%2A> stavu je vázán na položky kontejneru a nechcete přímo s příslušnou položkou. Když je kontejner znovu pro nové položky, aktuální hodnota <xref:System.Windows.Controls.Expander.IsExpanded%2A> se používá pro novou položku. Kromě toho ztratí správné staré položky <xref:System.Windows.Controls.Expander.IsExpanded%2A> hodnotu.

V současné době žádné ovládací prvky WPF nabízejí integrovanou podporu pro virtualizaci data.

## <a name="container-recycling"></a>Recyklace kontejneru

Optimalizace pro uživatelské rozhraní virtualizace přidáno v rozhraní .NET Framework 3.5 SP1 pro ovládací prvky, které dědí z <xref:System.Windows.Controls.ItemsControl> je *recyklace kontejneru* které může také zvýšit výkon posouvání. Když <xref:System.Windows.Controls.ItemsControl> , že vyplní virtualizace uživatelského rozhraní využívá, vytvoří kontejner položek pro každou položku, která se posune do zobrazení a odstraní kontejner položek pro každou položku, umožňuje posouvání mimo zobrazení. *Recyklace kontejneru* umožňuje znovu použít existující položka kontejnery pro různé datové položky tak, aby kontejnerů prvku není neustále vytvořeno a zničeno při jako uživatel posune ovládací prvek <xref:System.Windows.Controls.ItemsControl>. Můžete také povolit recyklace tak, že nastavíte položku <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> připojené vlastnosti <xref:System.Windows.Controls.VirtualizationMode.Recycling>.

Žádné <xref:System.Windows.Controls.ItemsControl> podporujících virtualizace, můžete použít recyklace kontejneru. Příklad toho, jak povolit recyklace kontejneru na <xref:System.Windows.Controls.ListBox>, naleznete v tématu [zvýšení výkonu posunování prvku ListBox](../controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).

## <a name="supporting-bidirectional-virtualization"></a>Podpora obousměrných virtualizace

<xref:System.Windows.Controls.VirtualizingStackPanel> nabízí vestavěnou podporu pro virtualizaci uživatelského rozhraní v jednom směru, buď vodorovně nebo svisle. Pokud chcete použít obousměrné virtualizace pro vaše ovládací prvky, musí implementovat vlastní panel, který rozšiřuje <xref:System.Windows.Controls.VirtualizingStackPanel> třídy. <xref:System.Windows.Controls.VirtualizingStackPanel> Třída zveřejňuje virtuální metody, jako <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>, a <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>. Tyto virtuální metody umožňují snadno zjistí změnu v viditelnou část seznamu a odpovídajícím způsobem ji zpracovat.

## <a name="optimizing-templates"></a>Optimalizace šablony

Vizuální strom obsahuje všechny vizuální prvky v aplikaci. Kromě objektů přímo vytvořil také obsahuje objekty z důvodu rozšíření šablon. Například při vytváření <xref:System.Windows.Controls.Button>, budete mít také <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> a <xref:System.Windows.Controls.ContentPresenter> objekty ve vizuálním stromu. Pokud nebyly optimalizovány šablony ovládacího prvku, můžete vytvářet spoustu dalších zbytečné objekty ve vizuálním stromu. Další informace o vizuálním stromu, naleznete v tématu [přehled vykreslování grafiky WPF](../graphics-multimedia/wpf-graphics-rendering-overview.md).

## <a name="deferred-scrolling"></a>Odložené posouvání.

Ve výchozím nastavení když uživatel přetáhne jezdce v objektu scrollbar, zobrazení obsahu průběžně aktualizuje. Pokud se posouvání je pomalý v ovládacím prvku, zvažte použití odložené posouvání. Odložené posouvání obsahu je aktualizováno pouze v případě, že uživatel uvolní jezdce.

Chcete-li implementovat odložené posouvání, nastavte <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> vlastnost `true`. <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> připojené vlastnosti a můžete ji nastavit na <xref:System.Windows.Controls.ScrollViewer> a libovolný ovládací prvek, který má <xref:System.Windows.Controls.ScrollViewer> v šabloně ovládacího prvku.

## <a name="controls-that-implement-performance-features"></a>Ovládací prvky, které implementují funkce výkonu

V následující tabulce jsou uvedeny běžné ovládací prvky pro zobrazení dat a jejich podpora funkce výkonu. Naleznete v předchozích částech informace o tom, jak tyto funkce povolit.

|Control|Virtualizace|Recyklace kontejneru|Odložené posouvání.|
|-------------|--------------------|-------------------------|------------------------|
|<xref:System.Windows.Controls.ComboBox>|Je možné povolit|Je možné povolit|Je možné povolit|
|<xref:System.Windows.Controls.ContextMenu>|Je možné povolit|Je možné povolit|Je možné povolit|
|<xref:System.Windows.Controls.DocumentViewer>|Není k dispozici|Není k dispozici|Je možné povolit|
|<xref:System.Windows.Controls.ListBox>|Výchozí|Je možné povolit|Je možné povolit|
|<xref:System.Windows.Controls.ListView>|Výchozí|Je možné povolit|Je možné povolit|
|<xref:System.Windows.Controls.TreeView>|Je možné povolit|Je možné povolit|Je možné povolit|
|<xref:System.Windows.Controls.ToolBar>|Není k dispozici|Není k dispozici|Je možné povolit|

> [!NOTE]
> Příklad toho, jak povolit virtualizaci a recyklace v kontejneru <xref:System.Windows.Controls.TreeView>, naleznete v tématu [zvýšení výkonu TreeView](../controls/how-to-improve-the-performance-of-a-treeview.md).

## <a name="see-also"></a>Viz také:

- [Rozložení](layout.md)
- [Rozložení a návrh](optimizing-performance-layout-and-design.md)
- [Datová vazba](optimizing-performance-data-binding.md)
- [Ovládací prvky](../controls/index.md)
- [Styly a šablony](../controls/styling-and-templating.md)
- [Návod: Ukládání dat aplikací v aplikaci WPF](walkthrough-caching-application-data-in-a-wpf-application.md)
