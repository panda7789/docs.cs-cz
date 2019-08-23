---
title: 'Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 7e51c810a2e1e4bf4157aa1311255c5547021b60
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962064"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView
Chcete-li zpracovat událost pro položku v <xref:System.Windows.Controls.ListView>, je nutné přidat obslužnou rutinu <xref:System.Windows.Controls.ListViewItem>události. Je- <xref:System.Windows.Controls.ListView> li objekt svázán se zdrojem dat, <xref:System.Windows.Controls.ListViewItem>nevytvoříte explicitně, ale můžete zpracovat událost pro <xref:System.Windows.EventSetter> každou položku přidáním do stylu <xref:System.Windows.Controls.ListViewItem>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří datovou vazbu <xref:System.Windows.Controls.ListView> a <xref:System.Windows.Style> vytvoří pro přidání obslužné rutiny události do každého <xref:System.Windows.Controls.ListViewItem>.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Následující příklad zpracovává <xref:System.Windows.Controls.Control.MouseDoubleClick> událost.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> I když je <xref:System.Windows.Controls.ListView> nejběžnější vytvořit vazbu na zdroj dat, můžete použít styl k přidání obslužné rutiny události do každého <xref:System.Windows.Controls.ListViewItem> nevázaného <xref:System.Windows.Controls.ListView> data <xref:System.Windows.Controls.ListViewItem>bez ohledu na to, zda explicitně vytvoříte.  Další informace o explicitních a implicitně vytvořených <xref:System.Windows.Controls.ListViewItem> ovládacích prvcích naleznete <xref:System.Windows.Controls.ItemsControl>v tématu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlElement>
- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Styly a šablony](styling-and-templating.md)
- [Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView – přehled](listview-overview.md)
