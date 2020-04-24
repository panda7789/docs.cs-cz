---
title: 'Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7bbc7bad36b3b1f2c92065e5f5699e5a86ac6189
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646114"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView
Chcete-li zpracovat událost <xref:System.Windows.Controls.ListView>pro položku v aplikaci <xref:System.Windows.Controls.ListViewItem>, je třeba ke každé události přidat obslužnou rutinu . Pokud <xref:System.Windows.Controls.ListView> je a vázána na zdroj dat, <xref:System.Windows.Controls.ListViewItem>není explicitně vytvořit , ale můžete <xref:System.Windows.EventSetter> zpracovat událost <xref:System.Windows.Controls.ListViewItem>pro každou položku přidáním styl .  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří vazbu <xref:System.Windows.Controls.ListView> na <xref:System.Windows.Style> data a vytvoří pro <xref:System.Windows.Controls.ListViewItem>přidání obslužné rutiny události do každé z nich .  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Následující příklad zpracovává <xref:System.Windows.Controls.Control.MouseDoubleClick> událost.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> Přestože <xref:System.Windows.Controls.ListView> je nejběžnější svázat a se zdrojem dat, můžete použít styl <xref:System.Windows.Controls.ListViewItem> přidat obslužnou rutinu události do každého v non-data-bound <xref:System.Windows.Controls.ListView> bez ohledu na to, zda explicitně vytvořit <xref:System.Windows.Controls.ListViewItem>.  Další informace o explicitně <xref:System.Windows.Controls.ListViewItem> a implicitně vytvořených ovládacích prvcích naleznete v tématu <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Xml.XmlElement>
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vazba na data XML pomocí dotazů XMLDataProvider a XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView – přehled](listview-overview.md)
