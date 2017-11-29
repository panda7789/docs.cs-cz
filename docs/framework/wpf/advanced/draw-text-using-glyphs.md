---
title: "Vykreslení textu použitím piktogramů"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- text [WPF], drawing with Glyphs objects
- Glyphs objects [WPF], drawing text
- typography [WPF], Glyphs objects
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ebce286cd93355feac7e4675ef6b142862740a92
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="draw-text-using-glyphs"></a><span data-ttu-id="0043f-102">Vykreslení textu použitím piktogramů</span><span class="sxs-lookup"><span data-stu-id="0043f-102">Draw Text Using Glyphs</span></span>
<span data-ttu-id="0043f-103">Toto téma vysvětluje, jak používat nízké úrovně <xref:System.Windows.Documents.Glyphs> objekt, který chcete zobrazit text v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0043f-103">This topic explains how to use the low-level <xref:System.Windows.Documents.Glyphs> object to display text in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span>  
  
## <a name="example"></a><span data-ttu-id="0043f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0043f-104">Example</span></span>  
 <span data-ttu-id="0043f-105">Následující příklady ukazují, jak definovat vlastnosti <xref:System.Windows.Documents.Glyphs> objekt v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0043f-105">The following examples show how to define properties for a <xref:System.Windows.Documents.Glyphs> object in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].</span></span> <span data-ttu-id="0043f-106"><xref:System.Windows.Documents.Glyphs> Objekt představuje výstup <xref:System.Windows.Media.GlyphRun> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0043f-106">The <xref:System.Windows.Documents.Glyphs> object represents the output of a <xref:System.Windows.Media.GlyphRun> in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span> <span data-ttu-id="0043f-107">V příkladech se předpokládá, že písma Arial, Kurýrní nové a časy New Roman jsou nainstalována ve složce C:\WINDOWS\Fonts v místním počítači.</span><span class="sxs-lookup"><span data-stu-id="0043f-107">The examples assume that the Arial, Courier New, and Times New Roman fonts are installed in the C:\WINDOWS\Fonts folder on the local computer.</span></span>  
  
 [!code-xaml[GlyphsOvwSample1#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 <span data-ttu-id="0043f-108">Tento příklad ukazuje, jak definovat další vlastnosti <xref:System.Windows.Documents.Glyphs> objekty v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span><span class="sxs-lookup"><span data-stu-id="0043f-108">This example shows how to define other properties of <xref:System.Windows.Documents.Glyphs> objects in [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].</span></span>  
  
 [!code-xaml[GlyphsOvwSamp2#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a><span data-ttu-id="0043f-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="0043f-109">See Also</span></span>  
 [<span data-ttu-id="0043f-110">Typografii v grafickém subsystému WPF</span><span class="sxs-lookup"><span data-stu-id="0043f-110">Typography in WPF</span></span>](../../../../docs/framework/wpf/advanced/typography-in-wpf.md)
