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
ms.openlocfilehash: 09a6fca48c06efca6f06b9e0617de9095197bd17
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2018
ms.locfileid: "46703486"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Postupy: Zpřístupnění dat pro připojení v jazyku XAML
Toto téma popisuje různé způsoby, jak můžete zpřístupnit data pro vazbu v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], v závislosti na potřebách vaší aplikace.  
  
## <a name="example"></a>Příklad  
 Pokud máte [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objektů chcete svázat z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jedním ze způsobů, které můžete zpřístupnit objekt pro vazbu, je definovat jako prostředek a přiřaďte mu `x:Key`. V následujícím příkladu je nutné `Person` objekt s řetězcovou vlastnost s názvem `PersonName`. `Person` Objekt (v řádku zobrazeném zvýrazněný, který obsahuje `<src>` element) je definován v oboru názvů volá `SDKSample`.  
  
 [!code-xaml[SimpleBinding#Instantiation](../../../../samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Potom můžete svázat <xref:System.Windows.Controls.TextBlock> ovládací prvek na objekt v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jak zvýrazněný řádek, který obsahuje `<TextBlock>` ukazuje element. 
  
 Alternativně můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídy, jako v následujícím příkladu:  
  
 [!code-xaml[ObjectDataProvider}](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Můžete definovat vazby stejným způsobem jako zvýrazněný řádek, který obsahuje `<TextBlock>` ukazuje element.  
  
 V tomto konkrétním příkladu je výsledek stejný: je nutné <xref:System.Windows.Controls.TextBlock> pomocí textového obsahu `Joe`. Ale <xref:System.Windows.Data.ObjectDataProvider> třída poskytuje funkce, třeba možnost vytvoření vazby mezi výsledkem metody. Můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídy, pokud potřebujete funkci poskytuje.  
  
 Nicméně, pokud vytváříte vazbu na objekt, který již byl vytvořen, je nutné nastavit `DataContext` v kódu, jako v následujícím příkladu.  
  
 [!code-csharp[ADODataSet#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Pro přístup k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data pomocí vazby <xref:System.Windows.Data.XmlDataProvider> najdete v tématu [svázání dat XML pomocí XMLDataProvider a dotazů XPath](../../../../docs/framework/wpf/data/how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Pro přístup k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] data pomocí vazby <xref:System.Windows.Data.ObjectDataProvider> najdete v tématu [připojení k XDocument, XElement nebo LINQ pro výsledky XML dotazu](../../../../docs/framework/wpf/data/how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Informace o mnoha způsoby, jak je možné určit data, vytváříte vazbu s najdete v tématu [určení zdroje připojení](../../../../docs/framework/wpf/data/how-to-specify-the-binding-source.md). Informace o tom, jaké typy dat lze svázat nebo jak implementovat vlastní [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] objekty pro vazbu, naleznete v tématu [Přehled zdrojů vazby](../../../../docs/framework/wpf/data/binding-sources-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
