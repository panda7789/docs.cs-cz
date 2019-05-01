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
ms.openlocfilehash: 3263810806b6b4bbec15eadfd1f1da3a57d12698
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62052362"
---
# <a name="how-to-set-margins-of-elements-and-controls"></a>Postupy: Nastavení okrajů elementů a ovládacích prvků
Tento příklad popisuje, jak nastavit <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost tak, že změníte hodnotu jakékoli existující vlastnosti okraje v modelu code-behind. <xref:System.Windows.FrameworkElement.Margin%2A> Vlastností je vlastnost <xref:System.Windows.FrameworkElement> základní prvek a proto dědí celou řadu ovládacích prvků a dalších prvků.  
  
 V tomto příkladu je napsána v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], s kódem na pozadí souboru, který [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] odkazuje. V obou je zobrazena modelu code-behind C# a verze Microsoft Visual Basicu.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[FEMarginProgrammatic#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
