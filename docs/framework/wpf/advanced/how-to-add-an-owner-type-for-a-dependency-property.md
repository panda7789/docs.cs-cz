---
title: 'Postupy: Přidání typu vlastníka pro vlastnost závislosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
ms.openlocfilehash: 1b1f2b241868b02e430af82bac8e9f6a617e511b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217091"
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>Postupy: Přidání typu vlastníka pro vlastnost závislosti
Tento příklad ukazuje, jak přidat třídu jako vlastníka skupiny vlastnost závislosti registrován pro jiného typu. Sytém díky tomu, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] čtečky i vlastnost systému jsou rozpoznat jako další vlastník vlastnost třídy. Volitelně můžete přidat jako vlastníka umožňuje přidávání třídě poskytnout metadata specifická pro typ.  
  
 V následujícím příkladu `StateProperty` vlastnost registraci `MyStateControl` třídy. Třída `UnrelatedStateControl` samotný přidá jako vlastníka skupiny `StateProperty` pomocí <xref:System.Windows.DependencyProperty.AddOwner%2A> metodu, konkrétně pomocí podpisu, který umožňuje pro nová metadata pro vlastnost závislosti na přidávání typ existuje. Všimněte si, že by měly poskytnout [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] přistupující objekty vlastnosti podobně jako v příkladu je znázorněno [implementace vlastnosti závislosti](how-to-implement-a-dependency-property.md) příklad, jakož i znovu vystavit identifikátor vlastnosti závislostí ve třídě přidávaný jako vlastník.  
  
 Bez obálky, bude vlastnost závislostí i nadále fungovat z hlediska programový přístup pomocí <xref:System.Windows.DependencyObject.GetValue%2A> nebo <xref:System.Windows.DependencyObject.SetValue%2A>. Obvykle budete chtít paralelní toto chování systému vlastností s, ale [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost obálky. Obálkami usnadňují prostřednictvím kódu programu nastavit vlastnost závislosti a umožňuje nastavit vlastnosti jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributy.  
  
 Jak lze přepsat výchozí metadat najdete v tématu [přepsání metadat pro vlastnost závislosti](how-to-override-metadata-for-a-dependency-property.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>Viz také:

- [Vlastní vlastnosti závislosti](custom-dependency-properties.md)
- [Přehled vlastností závislosti](dependency-properties-overview.md)
