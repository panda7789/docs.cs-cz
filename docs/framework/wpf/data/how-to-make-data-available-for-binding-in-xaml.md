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
ms.openlocfilehash: 91e89dbf36024c31f4afcd9b6d956944baf13576
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174183"
---
# <a name="how-to-make-data-available-for-binding-in-xaml"></a>Postupy: Zpřístupnění dat pro připojení v jazyku XAML
Toto téma popisuje různé způsoby, jak [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]můžete zpřístupnit data pro vazbu v aplikaci v závislosti na potřebách aplikace.  
  
## <a name="example"></a>Příklad  
 Pokud máte objekt CLR (COMMON Language runtime), na [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]který chcete vytvořit vazbu `x:Key`, jedním ze způsobů, jak objekt zpřístupnit pro vazbu, je definovat jej jako prostředek a poskytnout mu . V následujícím příkladu máte `Person` objekt s vlastností string s názvem `PersonName`. Objekt `Person` (v zobrazeném řádku, `<src>` který obsahuje prvek) je `SDKSample`definován v oboru názvů nazývaném .  
  
 [!code-xaml[SimpleBinding#Instantiation](~/samples/snippets/csharp/VS_Snippets_Wpf/SimpleBinding/CSharp/Page1.xaml?highlight=9,37)]  
  
 Potom můžete svázat <xref:System.Windows.Controls.TextBlock> ovládací prvek [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]s objektem v , `<TextBlock>` jak ukazuje zvýrazněný řádek, který obsahuje prvek.
  
 Případně můžete použít třídu, <xref:System.Windows.Data.ObjectDataProvider> jako v následujícím příkladu:  
  
 [!code-xaml[ObjectDataProvider}](~/samples/snippets/visualbasic/VS_Snippets_Wpf/SimpleBinding/VisualBasic/Page1.xaml?highlight=10-14,42)]  
  
 Vazbu definujete stejným způsobem, jako se zobrazí `<TextBlock>` zvýrazněný řádek, který obsahuje prvek.  
  
 V tomto konkrétním příkladu je výsledek stejný: máte <xref:System.Windows.Controls.TextBlock> `Joe`s textovým obsahem . Třída však <xref:System.Windows.Data.ObjectDataProvider> poskytuje funkce, jako je například schopnost vázat na výsledek metody. Třídu můžete použít, <xref:System.Windows.Data.ObjectDataProvider> pokud potřebujete funkce, které poskytuje.  
  
 Pokud však jste vazby na objekt, který již byl `DataContext` vytvořen, je třeba nastavit v kódu, jako v následujícím příkladu.  
  
 [!code-csharp[ADODataSet#1](~/samples/snippets/csharp/VS_Snippets_Wpf/ADODataSet/CSharp/Window1.xaml.cs#1)]
 [!code-vb[ADODataSet#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ADODataSet/VisualBasic/Window1.xaml.vb#1)]  
  
 Informace o přístupu k <xref:System.Windows.Data.XmlDataProvider> datům XML pro vazbu pomocí třídy naleznete [v tématu Vazba na data XML pomocí dotazů XMLDataProvider a XPath](how-to-bind-to-xml-data-using-an-xmldataprovider-and-xpath-queries.md). Informace o přístupu k <xref:System.Windows.Data.ObjectDataProvider> datům XML pro vazbu pomocí třídy naleznete v [tématu Vazba na XDocument, XElement nebo LINQ pro výsledky dotazů XML](how-to-bind-to-xdocument-xelement-or-linq-for-xml-query-results.md).  
  
 Informace o mnoha způsobech, jak můžete určit data, ke které jste vazby, naleznete [v tématu Určení zdroje vazby](how-to-specify-the-binding-source.md). Informace o tom, jaké typy dat můžete vázat nebo jak implementovat vlastní objekty CLR (COMMON Language runtime) pro vazbu, naleznete v [tématu Přehled zdrojů vazby](binding-sources-overview.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled datových vazeb](../../../desktop-wpf/data/data-binding-overview.md)
- [Témata s postupy](data-binding-how-to-topics.md)
