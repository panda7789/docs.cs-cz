---
title: "Postupy: Zpřístupnění dat pro připojení v jazyku XAML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0c342f0d635a9220a88a2af79c76e2c1580dee2f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Postupy: Zpřístupnění dat pro připojení v jazyku XAML
Toto téma popisuje různé způsoby můžete zpřístupnit data pro vazbu v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], v závislosti na potřebách vaší aplikace.  
  
## <a name="example"></a>Příklad  
 Pokud máte [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objektu, kterou chcete vytvořit vazbu k z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jedním ze způsobů, které můžete zpřístupnit objekt vazba je pro definování jako prostředek a pojmenujte ho `x:Key`. V následujícím příkladu, máte `Person` objekt s řetězec vlastnost s názvem `PersonName`. `Person` Objekt je definován v oboru názvů názvem `SDKSample`.  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#instantiation)]  
[!code-xaml[SimpleBinding#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#2)]  
  
 Potom můžete vázat na objekt v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jak je znázorněno v následujícím příkladu.  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 Alternativně můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídy, jako v následujícím příkladu.  
  
 [!code-xaml[SimpleBinding#ODPCP](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml#odpcp)]  
  
 Můžete definovat vazby stejným způsobem jako:  
  
 [!code-xaml[SimpleBinding#BDO1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml#bdo1)]  
  
 V tomto konkrétním příkladu je výsledek stejný: máte <xref:System.Windows.Controls.TextBlock> s textového obsahu `Joe`. Ale <xref:System.Windows.Data.ObjectDataProvider> třída poskytuje funkce, jako je možnost vytvořit vazbu na výsledek metody. Můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídy, pokud potřebujete funkci poskytuje.  
  
 Ale pokud vytváříte vazbu na objekt, který byl vytvořen, budete muset nastavit `DataContext` v kódu, jako v následujícím příkladu.  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Pro přístup k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat pro použití vazby <xref:System.Windows.Data.XmlDataProvider> třídy najdete v tématu [vazby na Data XML pomocí služby XMLDataProvider a dotazy jazyka XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Pro přístup k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat pro použití vazby <xref:System.Windows.Data.ObjectDataProvider> třídy najdete v tématu [vytvořit vazbu na XDocument, XElement nebo LINQ na výsledky dotazu XML](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Informace o různých způsobech, můžete zadat data jsou vytvoření vazby na najdete v tématu [určit zdroj vazby](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md). Informace o jaké typy dat můžete vázat na nebo jak implementovat vlastní [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objekty pro vazbu, najdete v části [Přehled zdrojů vazby](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
