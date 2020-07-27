---
title: ListView – přehled
description: Seznamte se s ovládacím prvkem Windows Presentation Foundation ListView, který poskytuje infrastrukturu pro zobrazení datových položek v různých rozloženích nebo zobrazeních.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], ListView
- ListView controls [WPF], about ListView control
ms.assetid: 989e12b0-260e-4570-95c6-489284003ce2
ms.openlocfilehash: 419c6216f0af696ec71e7607c79c2db637caa785
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87164565"
---
# <a name="listview-overview"></a>ListView – přehled
<xref:System.Windows.Controls.ListView>Ovládací prvek poskytuje infrastrukturu pro zobrazení sady datových položek v různých rozloženích nebo zobrazeních. Uživatel například může chtít zobrazit datové položky v tabulce a také seřadit sloupce.  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a>Co je ListView?  
 <xref:System.Windows.Controls.ListView>Ovládací prvek je <xref:System.Windows.Controls.ItemsControl> odvozen z <xref:System.Windows.Controls.ListBox> . Obvykle jsou položky členy kolekce dat a jsou reprezentovány jako <xref:System.Windows.Controls.ListViewItem> objekty. <xref:System.Windows.Controls.ListViewItem> <xref:System.Windows.Controls.ContentControl> A je a může obsahovat pouze jeden podřízený element. Tento podřízený element však může být libovolného vizuálního prvku.  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a>Definování režimu zobrazení pro ListView  
 Chcete-li určit režim zobrazení pro obsah <xref:System.Windows.Controls.ListView> ovládacího prvku, nastavte <xref:System.Windows.Controls.ListView.View%2A> vlastnost. Jeden režim zobrazení, který [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] poskytuje <xref:System.Windows.Controls.GridView> , zobrazuje kolekci datových položek v tabulce, která má přizpůsobitelné sloupce.  
  
 Následující příklad ukazuje, jak definovat <xref:System.Windows.Controls.GridView> pro <xref:System.Windows.Controls.ListView> ovládací prvek, který zobrazuje informace o zaměstnancích.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Následující obrázek ukazuje, jak se data objeví pro předchozí příklad.  
  
 ![Snímek obrazovky zobrazující zobrazení ListView s výstupem prvku GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
 Můžete vytvořit vlastní režim zobrazení definováním třídy, která dědí z <xref:System.Windows.Controls.ViewBase> třídy. <xref:System.Windows.Controls.ViewBase>Třída poskytuje infrastrukturu, kterou potřebujete k vytvoření vlastního zobrazení. Další informace o tom, jak vytvořit vlastní zobrazení, najdete v tématu [Vytvoření vlastního režimu zobrazení pro zobrazení ListView](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a>Vázání dat na ListView  
 Pomocí <xref:System.Windows.Controls.ItemsControl.Items%2A> vlastností a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> Určete položky <xref:System.Windows.Controls.ListView> ovládacího prvku. Následující příklad nastaví <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost na kolekci dat, která je volána `EmployeeInfoDataSource` .  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 V vytvoří <xref:System.Windows.Controls.GridView> <xref:System.Windows.Controls.GridViewColumn> objekty vazby na zadaná datová pole. Následující příklad váže <xref:System.Windows.Controls.GridViewColumn> objekt k datovému poli zadáním <xref:System.Windows.Data.Binding> <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> vlastnosti pro vlastnost.  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Můžete také zadat <xref:System.Windows.Data.Binding> jako součást <xref:System.Windows.DataTemplate> definice, kterou použijete k vytvoření stylu buněk ve sloupci. V následujícím příkladu, <xref:System.Windows.DataTemplate> který je identifikován pomocí <xref:System.Windows.ResourceKey> sady <xref:System.Windows.Data.Binding> pro <xref:System.Windows.Controls.GridViewColumn> . Všimněte si, že tento příklad nedefinuje, <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> protože to provádí přepsání vazby, která je určena pomocí <xref:System.Windows.DataTemplate> .  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a>Stylování prvku ListView, který implementuje prvek GridView  
 <xref:System.Windows.Controls.ListView>Ovládací prvek obsahuje <xref:System.Windows.Controls.ListViewItem> objekty, které představují zobrazené datové položky. Pomocí následujících vlastností můžete definovat obsah a styl datových položek:  
  
- V <xref:System.Windows.Controls.ListView> ovládacím prvku použijte <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A> vlastnosti, a <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> .  
  
- V <xref:System.Windows.Controls.ListViewItem> ovládacím prvku použijte <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> vlastnosti a.  
  
 Aby nedocházelo k problémům se zarovnáním mezi buňkami v <xref:System.Windows.Controls.GridView> , nepoužívejte <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> k nastavení vlastností nebo přidání obsahu, který ovlivňuje šířku položky v <xref:System.Windows.Controls.ListView> . Například problém zarovnání může nastat při nastavení <xref:System.Windows.FrameworkElement.Margin%2A> vlastnosti v <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> . Chcete-li určit vlastnosti nebo definovat obsah, který má vliv na šířku položek v <xref:System.Windows.Controls.GridView> , použijte vlastnosti <xref:System.Windows.Controls.GridView> třídy a její související třídy, například <xref:System.Windows.Controls.GridViewColumn> .  
  
 Další informace o tom, jak používat <xref:System.Windows.Controls.GridView> a jeho podpůrné třídy, naleznete v tématu [Přehled prvku GridView](gridview-overview.md).  
  
 Pokud definujete <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pro <xref:System.Windows.Controls.ListView> ovládací prvek a také definujete <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> , musíte zahrnout do stylu, aby <xref:System.Windows.Controls.ContentPresenter> <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> správně fungovala.  
  
 Nepoužívejte <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> vlastnosti a pro <xref:System.Windows.Controls.ListView> obsah, který je zobrazen pomocí <xref:System.Windows.Controls.GridView> . Chcete-li určit zarovnání obsahu ve sloupci <xref:System.Windows.Controls.GridView> , definujte <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A> .  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a>Sdílení stejného režimu zobrazení  
 Dva <xref:System.Windows.Controls.ListView> ovládací prvky nemohou současně sdílet stejný režim zobrazení. Pokud se pokusíte použít stejný režim zobrazení s více než jedním <xref:System.Windows.Controls.ListView> ovládacím prvkem, dojde k výjimce.  
  
 Chcete-li určit režim zobrazení, který může být současně použit více než jedním <xref:System.Windows.Controls.ListView> , použijte šablony nebo styly.
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a>Vytvoření vlastního režimu zobrazení  
 Přizpůsobená zobrazení <xref:System.Windows.Controls.GridView> jsou odvozena z <xref:System.Windows.Controls.ViewBase> abstraktní třídy, která poskytuje nástroje pro zobrazení datových položek, které jsou reprezentovány jako <xref:System.Windows.Controls.ListViewItem> objekty.
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [GridView – přehled](gridview-overview.md)
- [– postupy](listview-how-to-topics.md)
- [Ovládací prvky](../advanced/optimizing-performance-controls.md)
