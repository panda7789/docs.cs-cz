---
title: 'Postupy: Použití oborů názvů XML v datové vazbě'
ms.date: 03/30/2017
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
ms.openlocfilehash: 38bf6e8f88b0325193d49148cd6c33031f7b0a6d
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61931908"
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Postupy: Použití oborů názvů XML v datové vazbě
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak zpracovat obory názvů určen ve vaší [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] zdroj vazby.  
  
 Pokud vaše [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data má následující [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] definice oboru názvů:  
  
 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`  
  
 Můžete použít <xref:System.Windows.Data.XmlNamespaceMapping> – element pro mapování oboru názvů <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, jako v následujícím příkladu. Pak můžete použít <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> k odkazování [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] oboru názvů. <xref:System.Windows.Controls.ListBox> v tomto příkladu se zobrazí *title* a *dc:date* jednotlivých *položky*.  
  
 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](~/samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]  
  
 Všimněte si, že <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> zadáte nemusí odpovídat tomu použitému v [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] zdroje; pokud předpona, která se změnami [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] zdrojového mapování pracovního stále funguje.  
  
 V tomto konkrétním příkladu [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data pocházejí z webové služby, ale <xref:System.Windows.Data.XmlNamespaceMapping> element funguje taky s vložené [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] nebo [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat ve vloženém souboru.  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)
- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
