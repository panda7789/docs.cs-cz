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
ms.openlocfilehash: 2f336d1eb8dcdfec3c3c8059ba865147c6b6c825
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79187517"
---
# <a name="listview-overview"></a>ListView – přehled
Ovládací <xref:System.Windows.Controls.ListView> prvek poskytuje infrastrukturu pro zobrazení sady datových položek v různých rozloženích nebo zobrazeních. Uživatel může například chtít zobrazit datové položky v tabulce a také seřadit jejich sloupce.  

<a name="WhatisaListView"></a>
## <a name="what-is-a-listview"></a>Co je ListView?  
 Ovládací <xref:System.Windows.Controls.ListView> prvek <xref:System.Windows.Controls.ItemsControl> je odvozen od <xref:System.Windows.Controls.ListBox>. Jeho položky jsou obvykle členy kolekce dat <xref:System.Windows.Controls.ListViewItem> a jsou reprezentovány jako objekty. A <xref:System.Windows.Controls.ListViewItem> je <xref:System.Windows.Controls.ContentControl> a může obsahovat pouze jeden podřízený prvek. Tento podřízený prvek však může být libovolný vizuální prvek.  
  
<a name="DefiningaListViewView"></a>
## <a name="defining-a-view-mode-for-a-listview"></a>Definování režimu zobrazení pro listview  
 Chcete-li určit režim zobrazení <xref:System.Windows.Controls.ListView> pro obsah ovládacího prvku, nastavte <xref:System.Windows.Controls.ListView.View%2A> vlastnost. Jeden režim [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] zobrazení, <xref:System.Windows.Controls.GridView>který poskytuje, je , který zobrazuje kolekci datových položek v tabulce, která má přizpůsobitelné sloupce.  
  
 Následující příklad ukazuje, jak <xref:System.Windows.Controls.GridView> definovat <xref:System.Windows.Controls.ListView> pro ovládací prvek, který zobrazuje informace o zaměstnancích.  
  
 [!code-xaml[ListViewCode#ListViewEmployee](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#listviewemployee)]  
  
 Následující obrázek znázorňuje, jak se zobrazí data pro předchozí příklad.  
  
 ![Snímek obrazovky, který zobrazuje ListView s výstupem GridView.](./media/gridview-overview/listview-gridview-output.jpg)  
  
 Vlastní režim zobrazení můžete vytvořit definováním třídy, <xref:System.Windows.Controls.ViewBase> která dědí z třídy. Třída <xref:System.Windows.Controls.ViewBase> poskytuje infrastrukturu, kterou potřebujete k vytvoření vlastního zobrazení. Další informace o vytvoření vlastního zobrazení naleznete v [tématu Vytvoření vlastního režimu zobrazení pro listview](how-to-create-a-custom-view-mode-for-a-listview.md).  
  
<a name="BindingDatatoaListView"></a>
## <a name="binding-data-to-a-listview"></a>Vazby dat listView  
 Pomocí <xref:System.Windows.Controls.ItemsControl.Items%2A> vlastností a <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> určete <xref:System.Windows.Controls.ListView> položky ovládacího prvku. Následující příklad nastaví <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost na kolekci `EmployeeInfoDataSource`dat, která se nazývá .  
  
 [!code-xaml[ListViewCode#ItemsSource](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#itemssource)]  
  
 V <xref:System.Windows.Controls.GridView>oblasti <xref:System.Windows.Controls.GridViewColumn> se objekty vážou k zadaným datovým polím. Následující příklad sváže <xref:System.Windows.Controls.GridViewColumn> objekt s datovým polem zadáním <xref:System.Windows.Data.Binding> vlastnosti. <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A>  
  
 [!code-csharp[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml.cs#gridviewcolumnproperties)]
 [!code-vb[ListViewCode#GridViewColumnProperties](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewCode/visualbasic/window1.xaml.vb#gridviewcolumnproperties)]
 [!code-xaml[ListViewCode#GridViewColumnProperties](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewCode/CSharp/Window1.xaml#gridviewcolumnproperties)]  
  
 Můžete také určit <xref:System.Windows.Data.Binding> jako součást <xref:System.Windows.DataTemplate> definice, kterou používáte k stylové mušce buněk ve sloupci. V následujícím <xref:System.Windows.DataTemplate> příkladu, který je <xref:System.Windows.ResourceKey> identifikován <xref:System.Windows.Data.Binding> s <xref:System.Windows.Controls.GridViewColumn>nastaví pro . Všimněte si, že <xref:System.Windows.Controls.GridViewColumn.DisplayMemberBinding%2A> tento příklad nedefinuje, protože tím <xref:System.Windows.DataTemplate>přepíše vazbu, která je určena .  
  
 [!code-xaml[ListViewTemplate#GridViewCellTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#gridviewcelltemplate)]  
  
 [!code-xaml[ListViewTemplate#CellTemplateProperty](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewTemplate/CS/window1.xaml#celltemplateproperty)]  
  
<a name="StylingaListView"></a>
## <a name="styling-a-listview-that-implements-a-gridview"></a>Stylování ListView, který implementuje GridView  
 Ovládací <xref:System.Windows.Controls.ListView> prvek <xref:System.Windows.Controls.ListViewItem> obsahuje objekty, které představují datové položky, které jsou zobrazeny. K definování obsahu a stylu datových položek můžete použít následující vlastnosti:  
  
- V <xref:System.Windows.Controls.ListView> ovládacím prvku <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> <xref:System.Windows.Controls.ItemsControl.ItemTemplateSelector%2A>použijte <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> vlastnosti , a vlastnosti.  
  
- V <xref:System.Windows.Controls.ListViewItem> ovládacím prvku <xref:System.Windows.Controls.ContentControl.ContentTemplate%2A> <xref:System.Windows.Controls.ContentControl.ContentTemplateSelector%2A> použijte vlastnosti a.  
  
 Chcete-li se vyhnout <xref:System.Windows.Controls.GridView>problémům se zarovnáním mezi buňkami v aplikaci , nepoužívejte <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> k nastavení vlastností ani nepřidávejte obsah, který ovlivňuje šířku položky v aplikaci <xref:System.Windows.Controls.ListView>. Například zarovnání problém může dojít <xref:System.Windows.FrameworkElement.Margin%2A> při <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A>nastavení vlastnostv . Chcete-li určit vlastnosti nebo definovat obsah, který ovlivňuje šířku položek v <xref:System.Windows.Controls.GridView>, použijte vlastnosti <xref:System.Windows.Controls.GridView> třídy a jejích souvisejících tříd, například <xref:System.Windows.Controls.GridViewColumn>.  
  
 Další informace o použití <xref:System.Windows.Controls.GridView> a jeho podpůrné třídy naleznete v tématu [GridView Přehled](gridview-overview.md).  
  
 Pokud definujete <xref:System.Windows.Controls.ItemsControl.ItemContainerStyle%2A> pro <xref:System.Windows.Controls.ListView> ovládací prvek <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A>a také definujete , musíte zahrnout a <xref:System.Windows.Controls.ContentPresenter> ve stylu, <xref:System.Windows.Controls.ItemsControl.ItemTemplate%2A> aby fungoval správně.  
  
 Nepoužívejte <xref:System.Windows.Controls.Control.HorizontalContentAlignment%2A> vlastnosti <xref:System.Windows.Controls.Control.VerticalContentAlignment%2A> a <xref:System.Windows.Controls.ListView> pro obsah, který <xref:System.Windows.Controls.GridView>je zobrazen pomocí rozhraní . Chcete-li určit zarovnání obsahu <xref:System.Windows.Controls.GridView>ve <xref:System.Windows.Controls.GridViewColumn.CellTemplate%2A>sloupci , definujte .  
  
<a name="UsingtheSameViewMoreThanOnce"></a>
## <a name="sharing-the-same-view-mode"></a>Sdílení stejného režimu zobrazení  
 Dva <xref:System.Windows.Controls.ListView> ovládací prvky nemohou sdílet stejný režim zobrazení současně. Pokud se pokusíte použít stejný režim <xref:System.Windows.Controls.ListView> zobrazení s více než jedním ovládacím prvkem, dojde k výjimce.  
  
 Chcete-li určit režim zobrazení, který může <xref:System.Windows.Controls.ListView>současně používat více než jeden , použijte šablony nebo styly.
  
<a name="CreatingaCustomView"></a>
## <a name="creating-a-custom-view-mode"></a>Vytvoření vlastního režimu zobrazení  
 Přizpůsobená zobrazení <xref:System.Windows.Controls.GridView> jako jsou <xref:System.Windows.Controls.ViewBase> odvozena z abstraktní třídy, která poskytuje <xref:System.Windows.Controls.ListViewItem> nástroje pro zobrazení datových položek, které jsou reprezentovány jako objekty.
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.GridView>
- <xref:System.Windows.Controls.ListView>
- <xref:System.Windows.Controls.ListViewItem>
- <xref:System.Windows.Data.Binding>
- [GridView – přehled](gridview-overview.md)
- [Témata s postupy](listview-how-to-topics.md)
- [Ovládací prvky](../advanced/optimizing-performance-controls.md)
