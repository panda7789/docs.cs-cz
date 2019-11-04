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
ms.openlocfilehash: 2bfd9809a6ad487a7e706366dc6bce8fe951c940
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459758"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Postupy: Zpřístupnění dat pro připojení v jazyku XAML
Toto téma popisuje různé způsoby, jak můžete zpřístupnit data pro vazby v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]v závislosti na potřebách vaší aplikace.  
  
## <a name="example"></a>Příklad  
 Máte-li objekt modulu CLR (Common Language Runtime), na který chcete vytvořit vazbu z [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jeden ze způsobů, jak lze objekt zpřístupnit pro vazbu, je definovat jako prostředek a poskytnout mu `x:Key`. V následujícím příkladu máte objekt `Person` s vlastností řetězce s názvem `PersonName`. Objekt `Person` (zvýrazněný řádek, který obsahuje `<src>` element) je definován v oboru názvů s názvem `SDKSample`.  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Ovládací prvek <xref:System.Windows.Controls.TextBlock> lze navazovat na objekt v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], protože zvýrazněný řádek, který obsahuje prvek `<TextBlock>`, ukazuje. 
  
 Alternativně můžete použít třídu <xref:System.Windows.Data.ObjectDataProvider>, jak je uvedeno v následujícím příkladu:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Vazbu lze definovat stejným způsobem jako zvýrazněný řádek, který obsahuje prvek `<TextBlock>`.  
  
 V tomto konkrétním příkladu je výsledek stejný: máte <xref:System.Windows.Controls.TextBlock> s textovým obsahem `Joe`. Třída <xref:System.Windows.Data.ObjectDataProvider> však poskytuje funkce, jako je možnost svázání s výsledkem metody. Můžete použít třídu <xref:System.Windows.Data.ObjectDataProvider>, pokud potřebujete funkce, které poskytuje.  
  
 Pokud však vytváříte vazbu na objekt, který již byl vytvořen, je nutné nastavit `DataContext` v kódu, jak je uvedeno v následujícím příkladu.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Chcete-li získat přístup k datům [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] pro vazbu pomocí <xref:System.Windows.Data.XmlDataProvider> třídy, přečtěte si téma [vazba na data XML pomocí dotazů XmlDataProvider a XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Chcete-li získat přístup k [!INCLUDE[TLA2#tla_xml](../../../../includes/tla2sharptla-xml-md.md)] dat pro vazbu pomocí <xref:System.Windows.Data.ObjectDataProvider> třídy, přečtěte si téma [vazba na XDocument, XElement nebo LINQ pro výsledky dotazu XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Informace o mnoha způsobech, kterými můžete zadat data, k jejichž vytváření vytváříte, najdete v tématu [určení zdroje vazby](how-to-specify-the-binding-source.md). Informace o tom, jaké typy dat můžete svázat nebo jak implementovat vlastní objekty modulu CLR (Common Language Runtime) pro vazbu, najdete v tématu [Přehled zdrojů vazby](binding-sources-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
