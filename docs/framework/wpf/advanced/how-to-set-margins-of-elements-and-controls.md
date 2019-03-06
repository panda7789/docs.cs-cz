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
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57356270"
---
# <a name="how-to-set-margins-of-elements-and-controls"></a><span data-ttu-id="d35cc-102">Postupy: Nastavení okrajů elementů a ovládacích prvků</span><span class="sxs-lookup"><span data-stu-id="d35cc-102">How to: Set Margins of Elements and Controls</span></span>
<span data-ttu-id="d35cc-103">Tento příklad popisuje, jak nastavit <xref:System.Windows.FrameworkElement.Margin%2A> vlastnost tak, že změníte hodnotu jakékoli existující vlastnosti okraje v modelu code-behind.</span><span class="sxs-lookup"><span data-stu-id="d35cc-103">This example describes how to set the <xref:System.Windows.FrameworkElement.Margin%2A> property, by changing any existing property value for the margin in code-behind.</span></span> <span data-ttu-id="d35cc-104"><xref:System.Windows.FrameworkElement.Margin%2A> Vlastností je vlastnost <xref:System.Windows.FrameworkElement> základní prvek a proto dědí celou řadu ovládacích prvků a dalších prvků.</span><span class="sxs-lookup"><span data-stu-id="d35cc-104">The <xref:System.Windows.FrameworkElement.Margin%2A> property is a property of the <xref:System.Windows.FrameworkElement> base element, and is thus inherited by a variety of controls and other elements.</span></span>  
  
 <span data-ttu-id="d35cc-105">V tomto příkladu je napsána v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], s kódem na pozadí souboru, který [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] odkazuje.</span><span class="sxs-lookup"><span data-stu-id="d35cc-105">This example is written in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)], with a code-behind file that the [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] refers to.</span></span> <span data-ttu-id="d35cc-106">V obou je zobrazena modelu code-behind C# a verze Microsoft Visual Basicu.</span><span class="sxs-lookup"><span data-stu-id="d35cc-106">The code-behind is shown in both a C# and a Microsoft Visual Basic version.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d35cc-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="d35cc-107">Example</span></span>  
 [!code-xaml[FEMarginProgrammatic#XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml#xaml)]  
  
 [!code-csharp[FEMarginProgrammatic#Handler](~/samples/snippets/csharp/VS_Snippets_Wpf/FEMarginProgrammatic/CSharp/default.xaml.cs#handler)]
 [!code-vb[FEMarginProgrammatic#Handler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/FEMarginProgrammatic/VisualBasic/default.xaml.vb#handler)]
