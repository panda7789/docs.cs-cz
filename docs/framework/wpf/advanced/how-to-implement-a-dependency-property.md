---
title: 'Postupy: Implementace vlastnosti závislosti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: e2f18cb3941be2ebf4315a844c05b91ff49c6aa2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59223798"
---
# <a name="how-to-implement-a-dependency-property"></a>Postupy: Implementace vlastnosti závislosti
Tento příklad ukazuje, jak zálohovat [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost s <xref:System.Windows.DependencyProperty> pole, proto definování vlastnost závislosti. Při definování vlastní vlastnosti a nechcete, aby podporují mnoho aspektů [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkce, včetně styly, vazby dat, dědičnost, animace a výchozí hodnoty, měli byste implementovat jako vlastnost závislosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad nejprve registruje vlastnost závislosti voláním <xref:System.Windows.DependencyProperty.Register%2A> metody. Název pole identifikátor, který použijete k uložení názvu a vlastnosti vlastnost závislosti musí být <xref:System.Windows.DependencyProperty.Name%2A> jste zvolili pro vlastnost závislosti v rámci <xref:System.Windows.DependencyProperty.Register%2A> volání připojí pomocí řetězcového literálu `Property`. Například když si zaregistrujete pomocí vlastnosti závislosti <xref:System.Windows.DependencyProperty.Name%2A> z `Location`, pak musí mít název na identifikátor pole, které definujete pro vlastnost závislosti `LocationProperty`.  
  
 V tomto příkladu, název vlastnosti závislostí a jeho [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] přístupový objekt není `State`; je pole identifikátor `StateProperty`; typ vlastnosti je <xref:System.Boolean>; a typ, který registruje vlastnost závislosti je `MyStateControl`.  
  
 Pokud chcete řídit tímto vzorem pojmenování, návrháři nemusí správně sestavu vaše vlastnost, a některé aspekty aplikaci ve stylu systému vlastnost nemusí chovat dle očekávání.  
  
 Můžete také určit výchozí metadat pro vlastnost závislosti. Tento příklad registruje výchozí hodnota `State` vlastnost závislosti bude `false`.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Další informace o tom, a proto implementace vlastnosti závislosti, na rozdíl od jenom zálohování [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost s privátní pole, naleznete v tématu [přehled vlastností závislosti](dependency-properties-overview.md).  
  
## <a name="see-also"></a>Viz také:

- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [Témata s postupy](properties-how-to-topics.md)
