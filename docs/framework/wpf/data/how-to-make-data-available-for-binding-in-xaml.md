---
title: 'Postupy: Zpřístupnění dat pro připojení v jazyku XAML'
description: Seznamte se s různými způsoby, jak můžete data zpřístupnit v závislosti na potřebách vaší aplikace v Windows Presentation Foundation (WPF).
ms.date: 01/29/2018
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding [WPF], making data available for binding
- binding data [WPF], making data available for
ms.assetid: 7103c2e8-0e31-4a13-bf12-ca382221a8d5
ms.openlocfilehash: 16618ce8b19f5dd5854c4d126e7fc455f0428a28
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620791"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Postupy: Zpřístupnění dat pro připojení v jazyku XAML
Toto téma popisuje různé způsoby, jak můžete zpřístupnit data pro vazby v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] závislosti na potřebách vaší aplikace.  
  
## <a name="example"></a>Příklad  
 Pokud máte objekt modulu CLR (Common Language Runtime), na který chcete vytvořit vazbu [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , jedním ze způsobů, jak lze objekt zpřístupnit pro vazbu, je definovat jako prostředek a poskytnout mu `x:Key` . V následujícím příkladu máte `Person` objekt s vlastností řetězce s názvem `PersonName` . `Person`Objekt (v zobrazeném řádku, který obsahuje `<src>` element) je definován v oboru názvů s názvem `SDKSample` .  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Ovládací prvek lze následně navazovat <xref:System.Windows.Controls.TextBlock> na objekt v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , protože zvýrazněný řádek, který obsahuje prvek, se `<TextBlock>` zobrazí.
  
 Alternativně můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídu, jak je uvedeno v následujícím příkladu:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Vazbu lze definovat stejným způsobem jako zvýrazněný řádek, který obsahuje `<TextBlock>` prvek.  
  
 V tomto konkrétním příkladu je výsledek stejný: máte <xref:System.Windows.Controls.TextBlock> textový obsah `Joe` . <xref:System.Windows.Data.ObjectDataProvider>Třída však poskytuje funkce, jako je možnost svázání s výsledkem metody. Můžete použít <xref:System.Windows.Data.ObjectDataProvider> třídu, pokud potřebujete funkce, které poskytuje.  
  
 Pokud však vytváříte vazbu na objekt, který již byl vytvořen, je nutné nastavit `DataContext` v kódu, jak je uvedeno v následujícím příkladu.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Chcete-li získat přístup k datům XML pro vazbu pomocí <xref:System.Windows.Data.XmlDataProvider> třídy, přečtěte si téma [vazba na data XML pomocí dotazů XmlDataProvider a XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Chcete-li získat přístup k datům XML pro vazbu pomocí <xref:System.Windows.Data.ObjectDataProvider> třídy, přečtěte si téma [vazba na XDocument, XELEMENT nebo LINQ pro výsledky dotazu XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Informace o mnoha způsobech, kterými můžete zadat data, k jejichž vytváření vytváříte, najdete v tématu [určení zdroje vazby](how-to-specify-the-binding-source.md). Informace o tom, jaké typy dat můžete svázat nebo jak implementovat vlastní objekty modulu CLR (Common Language Runtime) pro vazbu, najdete v tématu [Přehled zdrojů vazby](binding-sources-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [– postupy](data-binding-how-to-topics.md)
