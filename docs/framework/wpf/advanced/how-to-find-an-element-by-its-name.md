---
title: 'Postupy: Hledání elementu podle názvu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
ms.openlocfilehash: 7405f9ba8db5d4db0ce35ca250f13e456685f39b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61757843"
---
# <a name="how-to-find-an-element-by-its-name"></a>Postupy: Hledání elementu podle názvu
Tento příklad popisuje způsob použití <xref:System.Windows.FrameworkElement.FindName%2A> způsob hledání elementu podle jeho <xref:System.Windows.FrameworkElement.Name%2A> hodnotu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu je zapsán metody k vyhledání konkrétní elementu podle názvu jako obslužná rutina události tlačítka. `stackPanel` je <xref:System.Windows.FrameworkElement.Name%2A> kořenové <xref:System.Windows.FrameworkElement> vyhledávaná, a příklad metody pak vizuálně označuje nalezeného prvku přetypováním jako <xref:System.Windows.Controls.TextBlock> a změnit jeden z <xref:System.Windows.Controls.TextBlock> viditelné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlastnosti.  
  
 [!code-csharp[FEFindName#Find](~/samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
