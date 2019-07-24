---
title: 'Postupy: Zpřístupnění dat pro vazbu v jazyku XAML'
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 3487a160cc49ab6b779a20157668915c2da33900
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2019
ms.locfileid: "68401492"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Postupy: Zpřístupnění dat pro vazbu v jazyku XAML
Toto téma popisuje různé způsoby, jak můžete zpřístupnit data pro vazby v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]závislosti na potřebách vaší aplikace.  
  
## <a name="example"></a>Příklad  
 Pokud máte objekt modulu CLR (Common Language Runtime), na který chcete vytvořit vazbu, jedním [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]ze způsobů, jak lze objekt zpřístupnit pro vazbu, je definovat jako prostředek a poskytnout `x:Key`mu. V následujícím příkladu máte `Person` objekt s vlastností řetězce s názvem. `PersonName` Objekt (v zobrazeném řádku, který `<src>` obsahuje element) je definován v oboru názvů s názvem `SDKSample`. `Person`  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 <xref:System.Windows.Controls.TextBlock> Ovládací prvek lze následně navazovat na objekt v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], protože `<TextBlock>` zvýrazněný řádek, který obsahuje prvek, se zobrazí. 
  
 Alternativně můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídu, jak je uvedeno v následujícím příkladu:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Vazbu lze definovat stejným způsobem jako zvýrazněný řádek, který obsahuje `<TextBlock>` prvek.  
  
 V tomto konkrétním příkladu je výsledek stejný: <xref:System.Windows.Controls.TextBlock> máte textový obsah. `Joe` <xref:System.Windows.Data.ObjectDataProvider> Třída však poskytuje funkce, jako je možnost svázání s výsledkem metody. Můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídu, pokud potřebujete funkce, které poskytuje.  
  
 Pokud však vytváříte vazbu na objekt, který již byl vytvořen, je nutné nastavit `DataContext` v kódu, jak je uvedeno v následujícím příkladu.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Chcete- [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] li získat přístup k datům <xref:System.Windows.Data.XmlDataProvider> pro vazbu pomocí třídy, přečtěte si téma [vazba na data XML pomocí dotazů XmlDataProvider a XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Chcete- [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] li získat přístup k datům <xref:System.Windows.Data.ObjectDataProvider> pro vazbu pomocí třídy, přečtěte si téma [vazba na XDocument, XElement nebo LINQ pro výsledky dotazu XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Informace o mnoha způsobech, kterými můžete zadat data, k jejichž vytváření vytváříte, najdete v tématu [určení zdroje vazby](how-to-specify-the-binding-source.md). Informace o tom, jaké typy dat můžete svázat nebo jak implementovat vlastní objekty modulu CLR (Common Language Runtime) pro vazbu, najdete v tématu [Přehled zdrojů vazby](binding-sources-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
