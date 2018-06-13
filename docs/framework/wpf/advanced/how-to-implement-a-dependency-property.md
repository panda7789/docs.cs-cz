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
ms.openlocfilehash: b0c5b33d841f43249f9559bd31f1ef8fe66ff05e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544645"
---
# <a name="how-to-implement-a-dependency-property"></a>Postupy: Implementace vlastnosti závislosti
Tento příklad ukazuje, jak zálohovat [!INCLUDE[TLA#tla_clr](../../../../includes/tlasharptla-clr-md.md)] vlastnost s <xref:System.Windows.DependencyProperty> pole, proto definování vlastnost závislosti. Když definovat vlastní vlastnosti a mají podporovat mnoho aspektů [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcí, včetně styly, vazby dat, dědičnosti, animace a výchozí hodnoty, měli byste implementovat jako vlastnost závislosti.  
  
## <a name="example"></a>Příklad  
 Následující příklad poprvé registruje vlastnost závislosti voláním <xref:System.Windows.DependencyProperty.Register%2A> metoda. Název pole identifikátor, který použijete k uložení názvu a vlastnosti vlastnost závislosti musí být <xref:System.Windows.DependencyProperty.Name%2A> jste zvolili pro vlastnost závislosti v rámci <xref:System.Windows.DependencyProperty.Register%2A> volání, která se připojí pomocí řetězcového literálu `Property`. Například Pokud zaregistrujete vlastnost závislosti s <xref:System.Windows.DependencyProperty.Name%2A> z `Location`, pak musí mít název pole identifikátor, který určíte pro vlastnost závislosti `LocationProperty`.  
  
 V tomto příkladu, název vlastnosti závislosti a jeho [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] přistupujícího objektu je `State`; je pole identifikátor `StateProperty`; je typ vlastnosti <xref:System.Boolean>; a typ, který registruje vlastnost závislosti je `MyStateControl`.  
  
 Pokud nedodržíte postupujte podle tohoto vzoru pro pojmenovávání, Designer nemusí správně sestavy vaší vlastností a některé aspekty vlastnost systému styl aplikace nemusí chovat podle očekávání.  
  
 Můžete také zadat výchozí metadata pro vlastnost závislosti. Tento příklad zaregistruje výchozí hodnota `State` vlastnost závislosti být `false`.  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Další informace o tom, a důvod, proč k implementaci vlastnost závislosti, oproti právě zálohování [!INCLUDE[TLA2#tla_clr](../../../../includes/tla2sharptla-clr-md.md)] vlastnost s soukromé pole, najdete v části [přehled vlastností závislostí](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md).  
  
## <a name="see-also"></a>Viz také  
 [Přehled vlastností závislosti](../../../../docs/framework/wpf/advanced/dependency-properties-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/advanced/properties-how-to-topics.md)
