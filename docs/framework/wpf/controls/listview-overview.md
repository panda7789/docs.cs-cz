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
ms.openlocfilehash: 07328a83e431bab02a72c3f252299e4b6b919b82
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57379143"
---
# <a name="listview-overview"></a>ListView – přehled
<xref:System.Windows.Controls.ListView> Ovládacího prvku poskytuje infrastrukturu pro zobrazení množinou datových položek v zobrazení nebo různá rozložení. Uživatel může být vhodné například pro zobrazení položek dat v tabulce a také k seřazení její sloupce.  
  
  
<a name="WhatisaListView"></a>   
## <a name="what-is-a-listview"></a>Co je ListView?  
 <xref:System.Windows.Controls.ListView> Je ovládací prvek <xref:System.Windows.Controls.ItemsControl> , která je odvozena od <xref:System.Windows.Controls.ListBox>. Obvykle jeho položky jsou členy kolekce dat a jsou reprezentovány ve formě <xref:System.Windows.Controls.ListViewItem> objekty. A <xref:System.Windows.Controls.ListViewItem> je <xref:System.Windows.Controls.ContentControl> a může obsahovat pouze jeden podřízený prvek. Tento podřízený element však může být libovolný element visual.  
  
<a name="DefiningaListViewView"></a>   
## <a name="defining-a-view-mode-for-a-listview"></a>Definování režimu zobrazení pro ListView  
 Pro určení režimu zobrazení pro obsah <xref:System.Windows.Controls.ListView> ovládacího prvku, je nastavit <xref:System.Windows.Controls.ListView.View%2A> vlastnost. Režim jedno zobrazení, která [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje je <xref:System.Windows.Controls.GridView>, který zobrazuje kolekci položek dat v tabulce, která má sloupce, přizpůsobitelné.  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridView> pro <xref:System.Windows.Controls.ListView> ovládací prvek, který se zobrazí informace o zaměstnancích.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Následující obrázek znázorňuje, jak se zobrazí data pro předchozí příklad.  
  
 ![ListView s výstupem GridView](./media/listviewgridview.JPG "ListViewGridView")  
  
 Můžete vytvořit tak, že definujete třídu, která dědí z vlastního režimu zobrazení <xref:System.Windows.Controls.ViewBase> třídy. <xref:System.Windows.Controls.ViewBase> Třída poskytuje infrastrukturu, která je potřeba vytvořit vlastní zobrazení. Další informace o tom, jak vytvořit vlastní zobrazení najdete v tématu [vytvoření vlastního režimu zobrazení pro ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>   
## <a name="binding-data-to-a-listview"></a>Vazba dat ListView  
 Použití <xref:System.Windows.Controls.ItemsControl.Items%2A> a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnosti, které chcete zadat položky pro <xref:System.Windows.Controls.ListView> ovládacího prvku. Následující příklad nastaví <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> na kolekci dat, která je volána `EmployeeInfoDataSource`.  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 V <xref:System.Windows.Controls.GridView>, <xref:System.Windows.Controls.GridViewColumn> objekty svázat zadaná datová pole. Následující příklad vytvoří vazbu <xref:System.Windows.Controls.GridViewColumn> objektu do datové pole tak, že zadáte <xref:System.Windows.Data.Binding> pro <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> vlastnost.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Můžete také určit <xref:System.Windows.Data.Binding> jako součást <xref:System.Windows.DataTemplate> definici, kterou použijete k úpravě stylu buňky ve sloupci. V následujícím příkladu <xref:System.Windows.DataTemplate> , který je označen <xref:System.Windows.ResourceKey> nastaví <xref:System.Windows.Data.Binding> pro <xref:System.Windows.Controls.GridViewColumn>. Všimněte si, že není definován v tomto příkladu <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> vzhledem k tomu, že to tedy přepíše vazbu, která je určená <xref:System.Windows.DataTemplate>.  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>   
## <a name="styling-a-listview-that-implements-a-gridview"></a>Práce se styly ListView, který s implementací GridView  
 <xref:System.Windows.Controls.ListView> Ovládací prvek obsahuje <xref:System.Windows.Controls.ListViewItem> objekty, které představují datové položky, které jsou zobrazeny. K definování obsah a styl položek dat můžete použít následující vlastnosti:  
  
-   Na <xref:System.Windows.Controls.ListView> řídit, použijte <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>, a <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> vlastnosti.  
  
-   Na <xref:System.Windows.Controls.ListViewItem> řídit, použijte <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> a <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> vlastnosti.  
  
 Abyste předešli problémům s zarovnání mezi buňkami v <xref:System.Windows.Controls.GridView>, nepoužívejte <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> nastavit vlastnosti nebo přidat obsah, který má vliv na šířku položky v <xref:System.Windows.Controls.ListView>. Například zarovnání problému může dojít, když jste nastavili <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>. Zadejte vlastnosti nebo definovat obsah, který má vliv na šířku položky v <xref:System.Windows.Controls.GridView>, použijte vlastnosti <xref:System.Windows.Controls.GridView> třídy a jejich souvisejícími třídami, jako <xref:System.Windows.Controls.GridViewColumn>.  
  
 Další informace o tom, jak používat <xref:System.Windows.Controls.GridView> a podpůrných tříd, naleznete v tématu [GridView – přehled](gridview-overview.md).  
  
 Při definování <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pro <xref:System.Windows.Controls.ListView> řízení a také definovat <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>, musí obsahovat <xref:System.Windows.Controls.ContentPresenter> ve stylu mohl <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> fungovat správně.  
  
 Nepoužívejte <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> a <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> vlastnosti <xref:System.Windows.Controls.ListView> obsah, který se zobrazí při použití <xref:System.Windows.Controls.GridView>. K určení zarovnání obsahu ve sloupci <xref:System.Windows.Controls.GridView>, definovat <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>.  
  
<a name="UsingtheSameViewMoreThanOnce"></a>   
## <a name="sharing-the-same-view-mode"></a>Sdílení stejný režim zobrazení  
 Dvě <xref:System.Windows.Controls.ListView> ovládací prvky nelze sdílet stejný režim zobrazení ve stejnou dobu. Pokud se pokusíte použít stejný režim zobrazení s více než jednou <xref:System.Windows.Controls.ListView> řídit, dojde k výjimce.  
  
 Chcete-li určit režim zobrazení, kterého lze současně ve více než jeden <xref:System.Windows.Controls.ListView>, použijte šablony stylů.
  
<a name="CreatingaCustomView"></a>   
## <a name="creating-a-custom-view-mode"></a>Vytvoření vlastního režimu zobrazení  
 Přizpůsobit zobrazení jako <xref:System.Windows.Controls.GridView> jsou odvozeny z <xref:System.Windows.Controls.ViewBase> abstraktní třídu, která poskytuje nástroje k zobrazení datových položek, které jsou reprezentovány ve formě <xref:System.Windows.Controls.ListViewItem> objekty.    
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [GridView – přehled](gridview-overview.md)
- [Témata s postupy](listview-how-to-topics.md)
- [Ovládací prvky](../advanced/optimizing-performance-controls.md)
