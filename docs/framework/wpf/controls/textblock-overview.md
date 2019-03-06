---
title: TextBlock – přehled
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- controls [WPF], TextBlock
- TextBlock control [WPF]
ms.assetid: 24720bca-341a-4b03-8a6b-7a678023b10a
ms.openlocfilehash: a3ea656a902f8a112a700667b6e08cae7463f68d
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57374463"
---
# <a name="textblock-overview"></a><span data-ttu-id="2868b-102">TextBlock – přehled</span><span class="sxs-lookup"><span data-stu-id="2868b-102">TextBlock Overview</span></span>
<span data-ttu-id="2868b-103"><xref:System.Windows.Controls.TextBlock> Ovládacího prvku poskytuje text flexibilní podporu pro [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] aplikací.</span><span class="sxs-lookup"><span data-stu-id="2868b-103">The <xref:System.Windows.Controls.TextBlock> control provides flexible text support for [!INCLUDE[TLA2#tla_winclient](../../../../includes/tla2sharptla-winclient-md.md)] applications.</span></span> <span data-ttu-id="2868b-104">Cílí element primárně na basic [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scénáře, které nevyžadují více než jeden odstavec textu.</span><span class="sxs-lookup"><span data-stu-id="2868b-104">The element is targeted primarily toward basic [!INCLUDE[TLA2#tla_ui](../../../../includes/tla2sharptla-ui-md.md)] scenarios that do not require more than one paragraph of text.</span></span> <span data-ttu-id="2868b-105">Podporuje celou řadu vlastností, které umožňují přesnou kontrolu nad prezentaci, jako například počet <xref:System.Windows.Controls.TextBlock.FontFamily%2A>, <xref:System.Windows.Controls.TextBlock.FontSize%2A>, <xref:System.Windows.Controls.TextBlock.FontWeight%2A>, <xref:System.Windows.Controls.TextBlock.TextEffects%2A>, a <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>.</span><span class="sxs-lookup"><span data-stu-id="2868b-105">It supports a number of properties that enable precise control of presentation, such as <xref:System.Windows.Controls.TextBlock.FontFamily%2A>, <xref:System.Windows.Controls.TextBlock.FontSize%2A>, <xref:System.Windows.Controls.TextBlock.FontWeight%2A>, <xref:System.Windows.Controls.TextBlock.TextEffects%2A>, and <xref:System.Windows.Controls.TextBlock.TextWrapping%2A>.</span></span> <span data-ttu-id="2868b-106">Textový obsah můžete přidat pomocí <xref:System.Windows.Controls.TextBlock.Text%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2868b-106">Text content can be added using the <xref:System.Windows.Controls.TextBlock.Text%2A> property.</span></span> <span data-ttu-id="2868b-107">Při použití v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], jako text elementu, který je implicitně přidal obsah mezi otevřít a uzavírací značka.</span><span class="sxs-lookup"><span data-stu-id="2868b-107">When used in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)], content between the open and closing tag is implicitly added as the text of the element.</span></span>  
  
 <span data-ttu-id="2868b-108">A <xref:System.Windows.Controls.TextBlock> element může být vytvořena instance velmi jednoduše pomocí [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2868b-108">A <xref:System.Windows.Controls.TextBlock> element can be instantiated very simply using [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[TextBlockSnip_XAML#2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip_XAML/CS/default.xaml#2)]  
  
 <span data-ttu-id="2868b-109">Podobně použití <xref:System.Windows.Controls.TextBlock> elementu v kódu je poměrně jednoduché.</span><span class="sxs-lookup"><span data-stu-id="2868b-109">Similarly, usage of the <xref:System.Windows.Controls.TextBlock> element in code is relatively simple.</span></span>  
  
 [!code-csharp[TextBlockSnip#1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBlockSnip/CSharp/TextBlockSnips.cs#1)]
 [!code-vb[TextBlockSnip#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBlockSnip/VisualBasic/TextBlockSnips.vb#1)]  
  
## <a name="see-also"></a><span data-ttu-id="2868b-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2868b-110">See also</span></span>
- <xref:System.Windows.Controls.Label>
