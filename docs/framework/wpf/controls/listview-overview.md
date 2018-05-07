---
title: ListView – přehled
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 5a7e640b7398c2034933688ea6356ef14692f8f2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="listview-overview"></a>ListView – přehled
<xref:System.Windows.Controls.ListView> Řízení poskytuje infrastrukturu pro zobrazení sadu datových položek v různých rozložení nebo zobrazení. Uživatel například může chtít, k zobrazení datových položek v tabulce a také řadit její sloupce.  
  
  
<a name="WhatisaListView"></a>   
## <a name="what-is-a-listview"></a>Co je prvku ListView?  
 <xref:System.Windows.Controls.ListView> Ovládacího prvku <xref:System.Windows.Controls.ItemsControl> je odvozena z <xref:System.Windows.Controls.ListBox>. Obvykle jeho položky jsou členy kolekce dat a jsou reprezentovány jako <xref:System.Windows.Controls.ListViewItem> objekty. A <xref:System.Windows.Controls.ListViewItem> je <xref:System.Windows.Controls.ContentControl> a může obsahovat pouze jeden podřízený element. Tento podřízený element však může být libovolný visual element.  
  
<a name="DefiningaListViewView"></a>   
## <a name="defining-a-view-mode-for-a-listview"></a>Definování režim zobrazení pro prvku ListView  
 K určení režimu zobrazení pro obsah <xref:System.Windows.Controls.ListView> řízení, nastavíte <xref:System.Windows.Controls.ListView.View%2A> vlastnost. Režim zobrazení, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje je <xref:System.Windows.Controls.GridView>, zobrazuje kolekce položek dat v tabulce, která má přizpůsobitelné sloupců.  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridView> pro <xref:System.Windows.Controls.ListView> ovládací prvek, který zobrazí informace o zaměstnancích.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Následující obrázek znázorňuje, jak se objeví data pro předchozí příklad.  
  
 ![ListView s výstupem GridView](../../../../docs/framework/wpf/controls/media/listviewgridview.JPG "ListViewGridView")  
  
 Můžete vytvořit vlastní zobrazení režimu definováním třídy, která dědí z <xref:System.Windows.Controls.ViewBase> třídy. <xref:System.Windows.Controls.ViewBase> Třída poskytuje infrastrukturu, která budete muset vytvořit vlastní zobrazení. Další informace o tom, jak vytvořit vlastní zobrazení najdete v tématu [vytvořit vlastní režim zobrazení pro prvku ListView](../../../../docs/framework/wpf/controls/how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>   
## <a name="binding-data-to-a-listview"></a>Vazba dat s prvku ListView  
 Použití <xref:System.Windows.Controls.ItemsControl.Items%2A> a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnosti, které chcete zadat položky pro <xref:System.Windows.Controls.ListView> ovládacího prvku. Následující příklad nastavuje <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost pro shromažďování dat, která je volána `EmployeeInfoDataSource`.  
  
 [!code-xaml[ListViewCode#ItemsSource](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 V <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn> objekty vytvořit vazbu na zadanou datová pole. Následující příklad vytvoří vazbu <xref:System.Windows.Controls.GridViewColumn> objektu do datové pole zadáním <xref:System.Windows.Data.Binding> pro <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> vlastnost.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Můžete také zadat <xref:System.Windows.Data.Binding> jako součást <xref:System.Windows.DataTemplate> definice, který používáte k úpravě stylu buněk ve sloupci. V následujícím příkladu <xref:System.Windows.DataTemplate> který je identifikován s <xref:System.Windows.ResourceKey> nastaví <xref:System.Windows.Data.Binding> pro <xref:System.Windows.Controls.GridViewColumn>. Všimněte si, že v tomto příkladu nedefinuje <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> vzhledem k tomu, že to tak přepsání vazby, která je zadána <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>   
## <a name="styling-a-listview-that-implements-a-gridview"></a>Styly prvku ListView, který implementuje GridView  
 <xref:System.Windows.Controls.ListView> Ovládací prvek obsahuje <xref:System.Windows.Controls.ListViewItem> objekty, které představují datových položek, které jsou zobrazeny. Zadat obsah a styl datových položek, můžete použít následující vlastnosti:  
  
-   Na <xref:System.Windows.Controls.ListView> řídit, použijte <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>, a <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> vlastnosti.  
  
-   Na <xref:System.Windows.Controls.ListViewItem> řídit, použijte <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> a <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> vlastnosti.  
  
 Abyste předešli problémům s zarovnání mezi buněk <xref:System.Windows.Controls.GridView>, nepoužívejte <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> nastavit vlastnosti nebo přidat obsah, který má vliv na šířku položky v <xref:System.Windows.Controls.ListView>. Například zarovnání problému může dojít, když nastavíte <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Zadejte vlastnosti nebo definovat obsah, který má vliv na šířku položky v <xref:System.Windows.Controls.GridView>, použijte vlastnosti <xref:System.Windows.Controls.GridView> třídy a jeho souvisejících tříd, jako <xref:System.Windows.Controls.GridViewColumn>.  
  
 Další informace o tom, jak používat <xref:System.Windows.Controls.GridView> a jeho podpůrné třídách naleznete v tématu [GridView přehled](../../../../docs/framework/wpf/controls/gridview-overview.md).  
  
 Pokud definujete <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pro <xref:System.Windows.Controls.ListView> řízení a také definovat <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, musí obsahovat <xref:System.Windows.Controls.ContentPresenter> ve stylu, aby <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> fungovala správně.  
  
 Nepoužívejte <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> a <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> vlastnosti <xref:System.Windows.Controls.ListView> obsah, který se zobrazí pomocí <xref:System.Windows.Controls.GridView>. K určení zarovnání obsahu ve sloupci <xref:System.Windows.Controls.GridView>, definovat <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>.  
  
<a name="UsingtheSameViewMoreThanOnce"></a>   
## <a name="sharing-the-same-view-mode"></a>Sdílení stejný režim zobrazení  
 Dva <xref:System.Windows.Controls.ListView> ovládací prvky nemohou sdílet stejný režim zobrazení ve stejnou dobu. Pokud se pokusíte používat stejný režim zobrazení s více než jeden <xref:System.Windows.Controls.ListView> řídit, dojde k výjimce.  
  
 Chcete-li určit režim zobrazení, který lze současně použít více než jedna <xref:System.Windows.Controls.ListView>, použít šablony nebo styly. Příklad toho, jak a určit tak zobrazení jako <xref:System.Windows.FrameworkElement.Resources%2A>, najdete v části [ListView s ukázkou více zobrazení](http://go.microsoft.com/fwlink/?LinkID=160013).  
  
<a name="CreatingaCustomView"></a>   
## <a name="creating-a-custom-view-mode"></a>Vytvoření vlastního zobrazení režimu  
 Přizpůsobit zobrazení jako <xref:System.Windows.Controls.GridView> jsou odvozeny od <xref:System.Windows.Controls.ViewBase> abstraktní třída, která poskytuje nástroje pro zobrazení datových položek, které jsou reprezentovány jako <xref:System.Windows.Controls.ListViewItem> objekty.  
  
 Příklad režimu vlastní zobrazení, naleznete v části [ListView s ukázkou více zobrazení](http://go.microsoft.com/fwlink/?LinkID=160013).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.GridView>  
 <xref:System.Windows.Controls.ListView>  
 <xref:System.Windows.Controls.ListViewItem>  
 <xref:System.Windows.Data.Binding>  
 [GridView – přehled](../../../../docs/framework/wpf/controls/gridview-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/controls/listview-how-to-topics.md)  
 [Ovládací prvky](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
