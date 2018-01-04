---
title: "Postupy: Použití oborů názvů XML v datové vazbě"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- XML [WPF], namespaces
- data binding [WPF], XML namespaces
- namespaces [WPF], XML
ms.assetid: a47c832f-dc84-48f2-96d5-cde18fc4284b
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f23e041a1e6b283cfe5308d6aef861f1fc757a7d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-xml-namespaces-in-data-binding"></a>Postupy: Použití oborů názvů XML v datové vazbě
## <a name="example"></a>Příklad  
 Tento příklad ukazuje, jak pracovat s obory názvů zadaný ve vaší [!INCLUDE[TLA#tla_xml](../../../../includes/tlasharptla-xml-md.md)] vazby zdroje.  
  
 Pokud vaše [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data mají následující [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] definici oboru názvů:  
  
 `<rss version="2.0" xmlns:dc="http://purl.org/dc/elements/1.1/">`  
  
 Můžete použít <xref:System.Windows.Data.XmlNamespaceMapping> element k mapování oboru názvů <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A>, jako v následujícím příkladu. Pak můžete použít <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> k odkazování na [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] oboru názvů. <xref:System.Windows.Controls.ListBox> v tomto příkladu se zobrazí *název* a *dc:date* jednotlivých *položky*.  
  
 [!code-xaml[XmlnsBindSnippet#XmlNamespaceMapping](../../../../samples/snippets/csharp/VS_Snippets_Wpf/XmlnsBindSnippet/CS/Window1.xaml#xmlnamespacemapping)]  
  
 Všimněte si, že <xref:System.Windows.Data.XmlNamespaceMapping.Prefix%2A> zadáte tak, aby odpovídaly používaný v nemá [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] zdroje; Pokud se změní předponu v [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] zdroj vaší mapování pořád funguje.  
  
 V tomto konkrétním příkladu [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data pocházejí z webové služby, ale <xref:System.Windows.Data.XmlNamespaceMapping> element funguje taky s vložené [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] nebo [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat ve vloženém souboru.  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby k datům XML pomocí objektu XMLDataProvider a dotazů XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
