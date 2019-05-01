---
title: Vykreslení textu použitím piktogramů
ms.date: 03/30/2017
helpviewer_keywords:
- text [WPF], drawing with Glyphs objects
- Glyphs objects [WPF], drawing text
- typography [WPF], Glyphs objects
ms.assetid: 587ab17e-a419-4ad5-b6da-8933a8e83d97
ms.openlocfilehash: 55bbc50de519d6607a843fcd633f2c07db53109f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62010368"
---
# <a name="draw-text-using-glyphs"></a>Vykreslení textu použitím piktogramů
Toto téma vysvětluje, jak používat nízké úrovni <xref:System.Windows.Documents.Glyphs> objektu k zobrazení textu v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)].  
  
## <a name="example"></a>Příklad  
 Následující příklady ukazují, jak definovat vlastnosti <xref:System.Windows.Documents.Glyphs> objekt [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)]. <xref:System.Windows.Documents.Glyphs> Objekt představuje výstup <xref:System.Windows.Media.GlyphRun> v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)]. V příkladech se předpokládá, že Arial Kurýrní nové a časy New Roman písma jsou nainstalovány ve složce C:\WINDOWS\Fonts v místním počítači.  
  
 [!code-xaml[GlyphsOvwSample1#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSample1/CS/default.xaml#1)]  
  
 Tento příklad ukazuje, jak definovat další vlastnosti <xref:System.Windows.Documents.Glyphs> objekty v [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)].  
  
 [!code-xaml[GlyphsOvwSamp2#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GlyphsOvwSamp2/CS/default.xaml#1)]  
  
## <a name="see-also"></a>Viz také:

- [Typografie v rozhraní WPF](typography-in-wpf.md)
