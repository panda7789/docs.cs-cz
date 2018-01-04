---
title: "Postupy: Přidání typu vlastníka pro vlastnost závislosti"
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
- classes [WPF], adding as owners of dependency properties
- dependency properties [WPF], adding classes as owners of
ms.assetid: edcce050-0576-4edb-a31a-3f909637b452
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: b93934c8f84a7257445b530e27896342bdd73aea
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-an-owner-type-for-a-dependency-property"></a>Postupy: Přidání typu vlastníka pro vlastnost závislosti
Tento příklad ukazuje, jak přidat třídu jako vlastníka vlastnosti závislosti registrován pro jiného typu. Tímto způsobem, [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] čtečky a vlastnost systému jsou obě rozpoznat třída jako vlastníka další vlastnosti. Přidání jako vlastník volitelně umožňuje přidání třídy zajistit metadata specifická pro typ.  
  
 V následujícím příkladu `StateProperty` vlastnost registrován `MyStateControl` třídy. Třída `UnrelatedStateControl` přidá sám sebe jako vlastníkem `StateProperty` pomocí <xref:System.Windows.DependencyProperty.AddOwner%2A> metodu, konkrétně pomocí podpisu, který umožňuje novými metadaty pro vlastnost závislosti uložených na přidání typu. Všimněte si, že by měl poskytovat [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] přístupových objektů pro vlastnost podobně jako v příkladu znázorněno [implementovat vlastnost závislosti](../../../../docs/framework/wpf/advanced/how-to-implement-a-dependency-property.md) příklad, jakož i znovu vystavit identifikátor vlastnosti závislosti na třídě, který chcete přidat jako vlastník.  
  
 Bez obálky, vlastnost závislosti by i nadále fungovat z perspektivy programový přístup pomocí <xref:System.Windows.DependencyObject.GetValue%2A> nebo <xref:System.Windows.DependencyObject.SetValue%2A>. Obvykle budete chtít paralelní s tímto chováním vlastnosti systému, ale [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] obálky vlastnost. Obálky usnadňují nastavit vlastnost závislosti prostřednictvím kódu programu a umožňují, a nastavte vlastnosti jako [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] atributy.  
  
 Chcete-li zjistit, jak lze přepsat výchozí metadata, přečtěte si téma [přepsat Metadata pro vlastnost závislosti](../../../../docs/framework/wpf/advanced/how-to-override-metadata-for-a-dependency-property.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
[!code-csharp[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#unrelatedstatecontrol)]
[!code-vb[PropertySystemEsoterics#UnrelatedStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#unrelatedstatecontrol)]  
  
## <a name="see-also"></a>Viz také  
 [Vlastní vlastnosti závislosti](../../../../docs/framework/wpf/advanced/custom-dependency-properties.md)  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)
