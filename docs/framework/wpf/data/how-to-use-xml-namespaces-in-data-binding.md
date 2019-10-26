---
title: 'Postupy: Použití oborů názvů XML v datové vazbě'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 9d8ddc5445bac28c68cd6cc99acf3313613a8c7f
ms.sourcegitcommit: 82f94a44ad5c64a399df2a03fa842db308185a76
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2019
ms.locfileid: "72919671"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Postupy: Použití oborů názvů XML v datové vazbě
## <a name="example"></a>Příklad
 Tento příklad ukazuje, jak zpracovat obory názvů zadané ve zdroji vazby [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)].

 Pokud [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data obsahují následující [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] definice oboru názvů:

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 Můžete použít prvek <xref:System.Windows.Data.XmlNamespaceMapping> pro mapování oboru názvů na <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, jak je uvedeno v následujícím příkladu. Pak můžete použít <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> pro odkazování na obor názvů [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]. <xref:System.Windows.Controls.ListBox> v tomto příkladu zobrazuje *název* a *DC: datum* každé *položky*.

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 Všimněte si, že <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, které zadáte, se nemusí shodovat s tím, který se používá ve zdroji [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]; Pokud se změní předpona ve zdroji [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)], vaše mapování pořád funguje.

 V tomto konkrétním příkladu [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data pocházejí z webové služby, ale element <xref:System.Windows.Data.XmlNamespaceMapping> funguje také s vloženými [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] nebo [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)]mi daty v vloženém souboru.

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
