---
title: 'Postupy: Hledání elementu podle názvu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
ms.openlocfilehash: e2d176c9334c0a1d4c10819e0dc9f2c408e41d5d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-find-an-element-by-its-name"></a>Postupy: Hledání elementu podle názvu
Tento příklad popisuje postup použití <xref:System.Windows.FrameworkElement.FindName%2A> metody k vyhledání element podle jeho <xref:System.Windows.FrameworkElement.Name%2A> hodnotu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se jako obslužné rutiny události tlačítka s zapíše metody k vyhledání konkrétní prvek jeho název. `stackPanel` je <xref:System.Windows.FrameworkElement.Name%2A> kořenové <xref:System.Windows.FrameworkElement> prohledávaný, a metodu příklad pak vizuálně označuje nalezen element podle přetypování jej jako <xref:System.Windows.Controls.TextBlock> a změna jednoho z <xref:System.Windows.Controls.TextBlock> viditelné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlastnosti.  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
