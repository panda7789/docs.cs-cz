---
title: "Postupy: Hledání elementu podle názvu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- elements [WPF], finding by name
ms.assetid: cfa7cf35-8aa2-4060-9454-872ed4af3f0e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7c51f22cb663b77ddcbbc280ab9d93c5e0eb7405
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-find-an-element-by-its-name"></a>Postupy: Hledání elementu podle názvu
Tento příklad popisuje postup použití <xref:System.Windows.FrameworkElement.FindName%2A> metody k vyhledání element podle jeho <xref:System.Windows.FrameworkElement.Name%2A> hodnotu.  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se jako obslužné rutiny události tlačítka s zapíše metody k vyhledání konkrétní prvek jeho název. `stackPanel`je <xref:System.Windows.FrameworkElement.Name%2A> kořenové <xref:System.Windows.FrameworkElement> prohledávaný, a metodu příklad pak vizuálně označuje nalezen element podle přetypování jej jako <xref:System.Windows.Controls.TextBlock> a změna jednoho z <xref:System.Windows.Controls.TextBlock> viditelné [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] vlastnosti.  
  
 [!code-csharp[FEFindName#Find](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEFindName/CSharp/default.xaml.cs#find)]
 [!code-vb[FEFindName#Find](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEFindName/VisualBasic/default.xaml.vb#find)]
