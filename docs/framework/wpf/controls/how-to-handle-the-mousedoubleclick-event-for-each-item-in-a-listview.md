---
title: 'Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 2a201eefba6e2623cfd7f733b85e271ce1c4e177
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54576054"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView
Zpracování události pro položky v <xref:System.Windows.Controls.ListView>, budete muset přidat obslužnou rutinu události u každého <xref:System.Windows.Controls.ListViewItem>. Při <xref:System.Windows.Controls.ListView> je vázán ke zdroji dat nevytvoříte explicitně <xref:System.Windows.Controls.ListViewItem>, ale můžete zpracovat událost pro každou položku tak, že přidáte <xref:System.Windows.EventSetter> na styl <xref:System.Windows.Controls.ListViewItem>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří vázaný na data <xref:System.Windows.Controls.ListView> a vytvoří <xref:System.Windows.Style> přidat obslužnou rutinu události u každého <xref:System.Windows.Controls.ListViewItem>.  
  
 [!code-xaml[ListViewHowTos#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Následující příklad popisovače <xref:System.Windows.Controls.Control.MouseDoubleClick> událostí.  
  
 [!code-csharp[ListViewHowTos#6](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
>  I když se nejčastěji k vytvoření vazby <xref:System.Windows.Controls.ListView> ke zdroji dat, můžete použít styl pro přidání obslužné rutiny události u každého <xref:System.Windows.Controls.ListViewItem> v jiných vázaný na data <xref:System.Windows.Controls.ListView> bez ohledu na to, zda explicitně nevytvoříte <xref:System.Windows.Controls.ListViewItem>.  Další informace o explicitně a implicitně vytvoří <xref:System.Windows.Controls.ListViewItem> ovládacích prvků, naleznete v tématu <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Xml.XmlElement>
- [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)
- [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
- [Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView – přehled](../../../../docs/framework/wpf/controls/listview-overview.md)
