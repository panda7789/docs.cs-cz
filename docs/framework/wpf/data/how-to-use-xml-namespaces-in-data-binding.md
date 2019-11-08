---
title: 'Postupy: Použití oborů názvů XML v datové vazbě'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: f6e6e042fa5583fcf91bd15c524537490fb6670c
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73740571"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Postupy: Použití oborů názvů XML v datové vazbě
## <a name="example"></a>Příklad
 Tento příklad ukazuje, jak zpracovat obory názvů zadané ve zdroji vazby XML.

 Pokud data XML mají následující definici oboru názvů XML:

 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`

 Můžete použít prvek <xref:System.Windows.Data.XmlNamespaceMapping> pro mapování oboru názvů na <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, jak je uvedeno v následujícím příkladu. Pak můžete použít <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> pro odkazování na obor názvů XML. <xref:System.Windows.Controls.ListBox> v tomto příkladu zobrazuje *název* a *DC: datum* každé *položky*.

 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]

 Všimněte si, že <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, které zadáte, se nemusí shodovat s tím, který se používá ve zdroji XML; Pokud se změní předpona ve zdroji XML, vaše mapování pořád funguje.

 V tomto konkrétním příkladu data XML přicházejí z webové služby, ale prvek <xref:System.Windows.Data.XmlNamespaceMapping> také funguje s vloženými daty XML nebo XML v vloženém souboru.

## <a name="see-also"></a>Viz také:

- [Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
