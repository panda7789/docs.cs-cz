---
title: 'Optimalizace výkonu: Ovládací prvky'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], improving performance
- container recycling [WPF]
- user interface virtualization [WPF]
ms.assetid: 45a31c43-ea8a-4546-96c8-0631b9934179
ms.openlocfilehash: 9e4ceee26263a1d047aeda0881b955070de4326d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33549260"
---
# <a name="optimizing-performance-controls"></a>Optimalizace výkonu: Ovládací prvky
[!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zahrnuje celou řadu běžných součásti uživatelského rozhraní (UI), které se používají v většina aplikací systému Windows. Toto téma obsahuje postupy pro zvýšení výkonu uživatelské rozhraní.  
  
 
  
<a name="Displaying"></a>   
## <a name="displaying-large-data-sets"></a>Zobrazení velkých datových sad  
 WPF ovládací prvky, jako <xref:System.Windows.Controls.ListView> a <xref:System.Windows.Controls.ComboBox> slouží k zobrazení seznamy položek v aplikaci. Pokud v seznamu zobrazíte velká, může mít vliv výkon aplikace. Toto je vzhledem k tomu, že systém standardní rozložení vytvoří kontejner rozložení pro každou položku přidruženého k ovládacímu prvku seznam a vypočítá jeho velikost rozložení a pozice. Obvykle nemáte zobrazíte všechny položky ve stejnou dobu; Místo toho můžete zobrazit podmnožinu a uživatel posune pomocí seznamu. V takovém případě má smysl použijte uživatelské rozhraní *virtualizace*, což znamená generování položky kontejneru a související výpočetní rozložení pro položku je odložení, dokud se nezobrazí položky.  
  
 Virtualizace uživatelského rozhraní je důležitým aspektem ovládací prvky seznamu. Virtualizace uživatelského rozhraní Nezaměňovat s virtualizací datových. Uživatelského rozhraní virtualizace úložiště viditelné položky v paměti, ale v případě vazby dat ukládá celé datové struktury v paměti. Naproti tomu virtualizací datových ukládá jenom datové položky, které jsou zobrazeny na obrazovce v paměti.  
  
 Ve výchozím nastavení, je povolena virtualizace uživatelského rozhraní pro <xref:System.Windows.Controls.ListView> a <xref:System.Windows.Controls.ListBox> prvky, když jsou jejich položky seznamu vázané na data. <xref:System.Windows.Controls.TreeView> může být povolena virtualizace nastavením <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A?displayProperty=nameWithType> --> `IsVirtualizing` přidružená vlastnost k `true`. Pokud chcete povolit virtualizaci uživatelského rozhraní pro vlastní ovládací prvky, které jsou odvozeny od <xref:System.Windows.Controls.ItemsControl> nebo existující položka prvky, které používají <xref:System.Windows.Controls.StackPanel> třídy, jako například <xref:System.Windows.Controls.ComboBox>, můžete nastavit <xref:System.Windows.Controls.ItemsControl.ItemsPanel%2A> k <xref:System.Windows.Controls.VirtualizingStackPanel> a nastavte <xref:System.Windows.Controls.VirtualizingPanel.IsVirtualizing%2A> k `true`. Virtualizace uživatelského rozhraní pro tyto ovládací prvky můžete zakázat bohužel bez porozumění ho. Následuje seznam podmínek, které zakázat virtualizace uživatelského rozhraní.  
  
-   Kontejnery položek přidají přímo na <xref:System.Windows.Controls.ItemsControl>. Například pokud aplikace explicitně přidá <xref:System.Windows.Controls.ListBoxItem> objekty do <xref:System.Windows.Controls.ListBox>, <xref:System.Windows.Controls.ListBox> není Virtualizovat <xref:System.Windows.Controls.ListBoxItem> objekty.  
  
-   Položka kontejnery v <xref:System.Windows.Controls.ItemsControl> jsou různého typu. Například <xref:System.Windows.Controls.Menu> používající <xref:System.Windows.Controls.Separator> objekty nelze implementovat, položka recyklaci, protože <xref:System.Windows.Controls.Menu> obsahuje objekty typu <xref:System.Windows.Controls.Separator> a <xref:System.Windows.Controls.MenuItem>.  
  
-   Nastavení <xref:System.Windows.Controls.ScrollViewer.CanContentScroll%2A> k `false`.  
  
-   Nastavení <!--zz <xref:System.Windows.Controls.VirtualizingStackPanel.IsVirtualizing%2A>--> `IsVirtualizing` k `false`.  
  
 Důležitá poznámka při virtualizaci kontejnery položek je, jestli máte další stav informace spojené s kontejner položek, které patří k položce. V takovém případě je nutné uložit další stav. Například můžete mít položka obsažená v <xref:System.Windows.Controls.Expander> řízení a <xref:System.Windows.Controls.Expander.IsExpanded%2A> stavu je vázán položky kontejneru a nikoli samotnou položku. Když se znovu použije kontejneru pro novou položku, aktuální hodnota <xref:System.Windows.Controls.Expander.IsExpanded%2A> se používá pro novou položku. Kromě toho ztratí správný starou položku <xref:System.Windows.Controls.Expander.IsExpanded%2A> hodnotu.  
  
 V současné době žádné ovládacích prvků WPF nabízí integrovanou podporu pro virtualizaci data.  
  
<a name="Container"></a>   
## <a name="container-recycling"></a>Kontejner recyklace  
 Optimalizace do uživatelského rozhraní virtualizace přidali v rozhraní .NET Framework 3.5 SP1 pro ovládací prvky, které dědí od <xref:System.Windows.Controls.ItemsControl> je *kontejneru recyklace,* které mohou rovněž zlepšit výkon posouvání.  Když <xref:System.Windows.Controls.ItemsControl> , používá uživatelského rozhraní virtualizace je vyplněný, vytvoří kontejner položku pro každou položku, která posune do zobrazení a zničí kontejner položek pro každou položku, která posune mimo zobrazení. *Kontejner recyklace* umožňuje kontrolu znova využít existující položka kontejnery pro různé datové položky, tak, aby položka kontejnery není neustále vytvořen a zničen jako viditelné pro uživatele <xref:System.Windows.Controls.ItemsControl>. Můžete povolit položky recyklace nastavením <xref:System.Windows.Controls.VirtualizingPanel.VirtualizationMode%2A> přidružená vlastnost k <xref:System.Windows.Controls.VirtualizationMode.Recycling>.  
  
 Všechny <xref:System.Windows.Controls.ItemsControl> této podporuje virtualizace můžete použít kontejner recyklace.  Příklad toho, jak povolit kontejneru recyklace na <xref:System.Windows.Controls.ListBox>, najdete v části [zlepšit výkon posouvání ListBox](../../../../docs/framework/wpf/controls/how-to-improve-the-scrolling-performance-of-a-listbox.md).  
  
<a name="Supporting"></a>   
## <a name="supporting-bidirectional-virtualization"></a>Podpora obousměrného virtualizace  
 <xref:System.Windows.Controls.VirtualizingStackPanel> má integrovanou podporu pro virtualizaci uživatelského rozhraní v jednom směru, vodorovně nebo svisle. Pokud chcete používat virtualizaci obousměrného pro vaše ovládací prvky, musí implementovat vlastní panel, který rozšiřuje <xref:System.Windows.Controls.VirtualizingStackPanel> třídy. <xref:System.Windows.Controls.VirtualizingStackPanel> Třída zpřístupňuje virtuální metody, jako <xref:System.Windows.Controls.VirtualizingStackPanel.OnViewportSizeChanged%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.LineUp%2A>, <xref:System.Windows.Controls.VirtualizingStackPanel.PageUp%2A>, a <xref:System.Windows.Controls.VirtualizingStackPanel.MouseWheelUp%2A>. Tyto virtuální metody umožňují zjistí změnu v viditelné části seznamu a odpovídajícím způsobem ji zpracovat.  
  
<a name="Optimizing"></a>   
## <a name="optimizing-templates"></a>Optimalizace šablony  
 Vizuální strojové struktuře obsahuje všechny vizuální prvky v aplikaci.  Kromě objekty přímo vytvořené také obsahuje objekty z důvodu rozšíření šablony.  Například při vytváření <xref:System.Windows.Controls.Button>, můžete také získat <xref:Microsoft.Windows.Themes.ClassicBorderDecorator> a <xref:System.Windows.Controls.ContentPresenter> objekty ve vizuálním stromu.  Pokud vaše šablony ovládacího prvku nebyly optimalizována, můžete vytvářet velké množství velmi nepotřebné objekty ve vizuálním stromu.   Další informace o vizuální strojové struktuře najdete v tématu [vykreslování přehled grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
<a name="Deferred"></a>   
## <a name="deferred-scrolling"></a>Odložení posouvání  
 Ve výchozím nastavení když uživatel nastavuje tažením úchytu na scrollbar, zobrazení obsahu průběžně aktualizuje.  Pokud posouvání pomalá v vlastního ovládacího prvku, zvažte použití odložení posouvání.  V odložené posouvání, je obsah aktualizován pouze v případě, že uživatel uvolní jezdce.  
  
 Chcete-li implementovat odložené posouvání, nastavte <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> vlastnost `true`.  <xref:System.Windows.Controls.ScrollViewer.IsDeferredScrollingEnabled%2A> je přidružená vlastnost a lze nastavit u <xref:System.Windows.Controls.ScrollViewer> a libovolný ovládací prvek, který má <xref:System.Windows.Controls.ScrollViewer> v šabloně jeho ovládacího prvku.  
  
<a name="Controls"></a>   
## <a name="controls-that-implement-performance-features"></a>Ovládací prvky, které implementují funkce výkonu  
 V následující tabulce jsou uvedeny běžné ovládací prvky pro zobrazení dat a jejich podpora funkce výkonu.  Naleznete v předchozích částech informace o tom, jak tyto funkce povolit.  
  
|Ovládací prvek|Virtualizace|Kontejner recyklace|Odložení posouvání|  
|-------------|--------------------|-------------------------|------------------------|  
|<xref:System.Windows.Controls.ComboBox>|Můžete povolit|Můžete povolit|Můžete povolit|  
|<xref:System.Windows.Controls.ContextMenu>|Můžete povolit|Můžete povolit|Můžete povolit|  
|<xref:System.Windows.Controls.DocumentViewer>|Není k dispozici|Není k dispozici|Můžete povolit|  
|<xref:System.Windows.Controls.ListBox>|Výchozí|Můžete povolit|Můžete povolit|  
|<xref:System.Windows.Controls.ListView>|Výchozí|Můžete povolit|Můžete povolit|  
|<xref:System.Windows.Controls.TreeView>|Můžete povolit|Můžete povolit|Můžete povolit|  
|<xref:System.Windows.Controls.ToolBar>|Není k dispozici|Není k dispozici|Můžete povolit|  
  
> [!NOTE]
>  Příklad toho, jak povolit virtualizaci a kontejner recyklace na <xref:System.Windows.Controls.TreeView>, najdete v části [zlepšit výkon elementu TreeView](../../../../docs/framework/wpf/controls/how-to-improve-the-performance-of-a-treeview.md).  
  
## <a name="see-also"></a>Viz také  
 [Rozložení](../../../../docs/framework/wpf/advanced/layout.md)  
 [Rozložení a návrh](../../../../docs/framework/wpf/advanced/optimizing-performance-layout-and-design.md)  
 [Datová vazba](../../../../docs/framework/wpf/advanced/optimizing-performance-data-binding.md)  
 [Ovládací prvky](../../../../docs/framework/wpf/controls/index.md)  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)  
 [Návod: Ukládání aplikačních dat do mezipaměti v aplikaci WPF](../../../../docs/framework/wpf/advanced/walkthrough-caching-application-data-in-a-wpf-application.md)
