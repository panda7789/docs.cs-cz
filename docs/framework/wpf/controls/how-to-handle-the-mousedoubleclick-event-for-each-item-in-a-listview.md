---
title: 'Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ListView controls [WPF], MouseDoubleClick event
ms.assetid: 81b39369-655a-4585-ac58-4640e5bb8fed
ms.openlocfilehash: 25308ee87fb387787e20c8a8887ae8e4e60742b9
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73460227"
---
# <a name="how-to-handle-the-mousedoubleclick-event-for-each-item-in-a-listview"></a>Postupy: Zpracování události MouseDoubleClick pro jednotlivé položky v objektu ListView
Chcete-li zpracovat událost pro položku v <xref:System.Windows.Controls.ListView>, je nutné přidat obslužnou rutinu události do každého <xref:System.Windows.Controls.ListViewItem>. Pokud je <xref:System.Windows.Controls.ListView> svázán se zdrojem dat, nevytvoříte explicitně <xref:System.Windows.Controls.ListViewItem>, ale můžete zpracovat událost pro každou položku přidáním <xref:System.Windows.EventSetter> do stylu <xref:System.Windows.Controls.ListViewItem>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří datově vázaný <xref:System.Windows.Controls.ListView> a vytvoří <xref:System.Windows.Style> pro přidání obslužné rutiny události do každého <xref:System.Windows.Controls.ListViewItem>.  
  
 [!code-xaml[ListViewHowTos#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#1)]  
[!code-xaml[ListViewHowTos#5](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#5)]  
[!code-xaml[ListViewHowTos#2](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml#2)]  
  
 Následující příklad zpracovává událost <xref:System.Windows.Controls.Control.MouseDoubleClick>.  
  
 [!code-csharp[ListViewHowTos#6](~/samples/snippets/csharp/VS_Snippets_Wpf/ListViewHowTos/CSharp/Window1.xaml.cs#6)]
 [!code-vb[ListViewHowTos#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ListViewHowTos/VisualBasic/Window1.xaml.vb#6)]  
  
> [!NOTE]
> I když je nejběžnější vytvořit vazbu <xref:System.Windows.Controls.ListView> ke zdroji dat, můžete použít styl k přidání obslužné rutiny události do každého <xref:System.Windows.Controls.ListViewItem> v nevázané <xref:System.Windows.Controls.ListView> dat bez ohledu na to, zda explicitně vytvoříte <xref:System.Windows.Controls.ListViewItem>.  Další informace o explicitním a implicitně vytvořeném ovládacím prvku <xref:System.Windows.Controls.ListViewItem> naleznete v tématu <xref:System.Windows.Controls.ItemsControl>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Xml.XmlElement>
- [Přehled datových vazeb](../data/data-binding-overview.md)
- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
- [Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath](../data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [ListView – přehled](listview-overview.md)
