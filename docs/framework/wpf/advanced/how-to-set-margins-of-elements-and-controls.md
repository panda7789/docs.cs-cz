---
title: 'Postupy: Nastavení okrajů elementů a ovládacích prvků'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- setting [WPF], Margin property
- properties [WPF], Margin property
- Margin property [WPF], setting
ms.assetid: 70ebee01-6f87-4352-8dd4-402c65eaaed6
ms.openlocfilehash: 41a0f1d025061cc7c1472a831fbbd5ed2f01b043
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-set-margins-of-elements-and-controls"></a>Postupy: Nastavení okrajů elementů a ovládacích prvků
Tento příklad popisuje postup nastavení <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost změnou žádnou existující hodnotu vlastnosti okraje v kódu. <xref:System.Windows.FrameworkElement.Margin%2A> Vlastnost je vlastnost <xref:System.Windows.FrameworkElement> základní element a proto dědí celou řadu ovládacích prvků a dalších prvků.  
  
 V tomto příkladu je napsána v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], s kódu na pozadí souboru, který [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] odkazuje. Kódu se zobrazí v C# i na verzi Microsoft Visual Basic.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[FEMarginProgrammatic#XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
