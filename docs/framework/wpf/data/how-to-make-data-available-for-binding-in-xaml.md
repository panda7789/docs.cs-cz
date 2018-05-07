---
title: 'Postupy: Zpřístupnění dat pro připojení v jazyku XAML'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: dd66fb2f96f8c42fea36afaeda0aaf35a2adbace
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Postupy: Zpřístupnění dat pro připojení v jazyku XAML
Toto téma popisuje různé způsoby můžete zpřístupnit data pro vazbu v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], v závislosti na potřebách vaší aplikace.  
  
## <a name="example"></a>Příklad  
 Pokud máte [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objektu, kterou chcete vytvořit vazbu k z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jedním ze způsobů, které můžete zpřístupnit objekt vazba je pro definování jako prostředek a pojmenujte ho `x:Key`. V následujícím příkladu, máte `Person` objekt s řetězec vlastnost s názvem `PersonName`. `Person` Objekt, který se zobrazí ve zvýrazněný řádek, který obsahuje `<src>` elementu je definován v oboru názvů názvem `SDKSample`.  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Pak můžete vázat <xref:System.Windows.Controls.TextBlock> ovládacího prvku do objektu v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jako zvýrazněný řádek, který obsahuje `<TextBlock>` ukazuje elementu. 
  
 Alternativně můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídy, jako v následujícím příkladu:  
  
 [!code-xaml[ObjectDataProvider}](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Můžete definovat vazby stejným způsobem jako zvýrazněný řádek, který obsahuje `<TextBlock>` element ukazuje.  
  
 V tomto konkrétním příkladu je výsledek stejný: máte <xref:System.Windows.Controls.TextBlock> s textového obsahu `Joe`. Ale <xref:System.Windows.Data.ObjectDataProvider> třída poskytuje funkce, jako je možnost vytvořit vazbu na výsledek metody. Můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídy, pokud potřebujete funkci poskytuje.  
  
 Ale pokud vytváříte vazbu na objekt, který byl vytvořen, budete muset nastavit `DataContext` v kódu, jako v následujícím příkladu.  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Pro přístup k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat pro použití vazby <xref:System.Windows.Data.XmlDataProvider> třídy najdete v tématu [vazby na Data XML pomocí služby XMLDataProvider a dotazy jazyka XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Pro přístup k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat pro použití vazby <xref:System.Windows.Data.ObjectDataProvider> třídy najdete v tématu [vytvořit vazbu na XDocument, XElement nebo LINQ na výsledky dotazu XML](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Informace o různých způsobech, můžete zadat data jsou vytvoření vazby na najdete v tématu [určit zdroj vazby](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md). Informace o jaké typy dat můžete vázat na nebo jak implementovat vlastní [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objekty pro vazbu, najdete v části [Přehled zdrojů vazby](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
