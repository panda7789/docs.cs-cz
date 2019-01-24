---
title: Vykreslení textu použitím piktogramů
ms.date: 03/30/2017
helpviewer_keywords:
- text [WPF], drawing with Glyphs objects
- Glyphs objects [WPF], drawing text
- typography [WPF], Glyphs objects
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
ms.openlocfilehash: 7c7c4946d2c5cc2aa9001cf119b969dd375a1050
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680241"
---
# <a name="draw-text-using-glyphs"></a><span data-ttu-id="e5ad8-102">Vykreslení textu použitím piktogramů</span><span class="sxs-lookup"><span data-stu-id="e5ad8-102">Draw Text Using Glyphs</span></span>
<span data-ttu-id="e5ad8-103">Toto téma vysvětluje, jak používat nízké úrovni <xref:System.Windows.Documents.Glyphs> objektu k zobrazení textu v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5ad8-103">This topic explains how to use the low-level <xref:System.Windows.Documents.Glyphs> object to display text in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5ad8-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5ad8-104">Example</span></span>  
 <span data-ttu-id="e5ad8-105">Následující příklady ukazují, jak definovat vlastnosti <xref:System.Windows.Documents.Glyphs> objekt [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5ad8-105">The following examples show how to define properties for a <xref:System.Windows.Documents.Glyphs> object in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="e5ad8-106"><xref:System.Windows.Documents.Glyphs> Objekt představuje výstup <xref:System.Windows.Media.GlyphRun> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5ad8-106">The <xref:System.Windows.Documents.Glyphs> object represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="e5ad8-107">V příkladech se předpokládá, že Arial Kurýrní nové a časy New Roman písma jsou nainstalovány ve složce C:\WINDOWS\Fonts v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="e5ad8-107">The examples assume that the Arial, Courier New, and Times New Roman fonts are installed in the C:\WINDOWS\Fonts folder on the local computer.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="e5ad8-108">Tento příklad ukazuje, jak definovat další vlastnosti <xref:System.Windows.Documents.Glyphs> objekty v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="e5ad8-108">This example shows how to define other properties of <xref:System.Windows.Documents.Glyphs> objects in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="e5ad8-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e5ad8-109">See also</span></span>
- [<span data-ttu-id="e5ad8-110">Typografie v rozhraní WPF</span><span class="sxs-lookup"><span data-stu-id="e5ad8-110">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
