---
title: 'Postupy: Implementace vlastnosti závislosti'
description: Definujte vlastnost závislosti v Windows Presentation Foundation tím, že zadáte zálohu vlastnosti modulu CLR (Common Language Runtime) s polem DependencyProperty.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dependency properties [WPF], backing properties with
- properties [WPF], backing with dependency properties
ms.assetid: 855fd6d7-19ac-493c-bf5e-2f40b57cdc92
ms.openlocfilehash: 673f653a9b02627efcccdfe08c4812ca0834217c
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165092"
---
# <a name="how-to-implement-a-dependency-property"></a>Postupy: Implementace vlastnosti závislosti
Tento příklad ukazuje, jak zálohovat vlastnost modulu CLR (Common Language Runtime) s <xref:System.Windows.DependencyProperty> polem a definovat tak vlastnost závislosti. Pokud definujete vlastní vlastnosti a chcete, aby podporovaly spoustu [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] funkcí, včetně stylů, datových vazeb, dědičnosti, animace a výchozích hodnot, měli byste je implementovat jako vlastnost závislosti.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je nejprve registrována vlastnost závislosti voláním <xref:System.Windows.DependencyProperty.Register%2A> metody. Název pole identifikátor, který použijete k uložení názvu a vlastností závislosti, musí být <xref:System.Windows.DependencyProperty.Name%2A> zvolen pro vlastnost závislosti jako součást <xref:System.Windows.DependencyProperty.Register%2A> volání, která je připojena pomocí řetězcového literálu `Property` . Pokud například zaregistrujete vlastnost závislosti s parametrem <xref:System.Windows.DependencyProperty.Name%2A> `Location` , musí být pole identifikátor, které definujete pro vlastnost Dependency, pojmenováno `LocationProperty` .  
  
 V tomto příkladu je název vlastnosti závislosti a jejího přístupového objektu CLR `State` ; pole identifikátoru je `StateProperty` ; typ vlastnosti je <xref:System.Boolean> ; a typ, který zaregistruje vlastnost závislosti, je `MyStateControl` .  
  
 Pokud se nedaří postupovat podle tohoto vzoru pojmenování, Návrháři nemusí správně nahlásit vlastnost a některé aspekty aplikace stylu systému vlastností se nemusí chovat podle očekávání.  
  
 Můžete také zadat výchozí metadata pro vlastnost závislosti. Tento příklad registruje výchozí hodnotu `State` vlastnosti závislosti, která má být `false` .  
  
 [!code-csharp[PropertySystemEsoterics#MyStateControl](~/samples/snippets/csharp/VS_Snippets_Wpf/PropertySystemEsoterics/CSharp/SDKSampleLibrary/class1.cs#mystatecontrol)]
 [!code-vb[PropertySystemEsoterics#MyStateControl](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PropertySystemEsoterics/visualbasic/sdksamplelibrary/class1.vb#mystatecontrol)]  
  
 Další informace o tom, jak a proč implementovat vlastnost závislosti, na rozdíl od pouhého zálohování vlastnosti CLR s privátním polem, najdete v tématu [Přehled vlastností závislosti](dependency-properties-overview.md).  
  
## <a name="see-also"></a>Viz také

- [Přehled vlastností závislosti](dependency-properties-overview.md)
- [– postupy](properties-how-to-topics.md)
