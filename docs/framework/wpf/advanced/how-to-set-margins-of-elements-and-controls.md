---
title: "Postupy: Nastavení okrajů elementů a ovládacích prvků"
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
- setting [WPF], Margin property
- properties [WPF], Margin property
- Margin property [WPF], setting
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 49bc3ac8c57e95e597d6b9aa505a931a6204b3f6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-margins-of-elements-and-controls"></a>Postupy: Nastavení okrajů elementů a ovládacích prvků
Tento příklad popisuje postup nastavení <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost změnou žádnou existující hodnotu vlastnosti okraje v kódu. <xref:System.Windows.FrameworkElement.Margin%2A> Vlastnost je vlastnost <xref:System.Windows.FrameworkElement> základní element a proto dědí celou řadu ovládacích prvků a dalších prvků.  
  
 V tomto příkladu je napsána v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], s kódu na pozadí souboru, který [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] odkazuje. Kódu se zobrazí v obou [!INCLUDE[TLA#tla_cshrp](../../../../includes/tlasharptla-cshrp-md.md)] a [!INCLUDE[TLA#tla_visualb](../../../../includes/tlasharptla-visualb-md.md)] verze.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[FEMarginProgrammatic#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
