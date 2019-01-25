---
title: 'Postupy: Změna typu kurzoru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: 2330cdd3be35dc4e4b555db6401dd55d9946ed1f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54745048"
---
# <a name="how-to-change-the-cursor-type"></a>Postupy: Změna typu kurzoru
Tento příklad ukazuje, jak změnit <xref:System.Windows.Input.Cursor> ukazatele myši pro konkrétní elementu a pro aplikaci.  
  
 Tento příklad se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor a soubor kódu.  
  
## <a name="example"></a>Příklad  
 Vytvoření uživatelského rozhraní, která se skládá z <xref:System.Windows.Controls.ComboBox> vyberte požadovaný <xref:System.Windows.Input.Cursor>, dvojici <xref:System.Windows.Controls.RadioButton> objekty určují, jestli změna kurzor platí pro pouze jeden element nebo platí pro celou aplikaci a <xref:System.Windows.Controls.Border> což je element, který se použije nový ukazatel na.  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 Následující kód vytvoří <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> obslužná rutina události, která je volána, když typ kurzoru se změní v <xref:System.Windows.Controls.ComboBox>.  Příkaz switch filtry na název kurzoru a nastaví <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost <xref:System.Windows.Controls.Border> který se nazývá *DisplayArea*.  
  
 Pokud změna kurzoru je nastavená na "Celou aplikaci" <xref:System.Windows.Input.Mouse.OverrideCursor%2A> je nastavena na <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost <xref:System.Windows.Controls.Border> ovládacího prvku.  To přinutí kurzor, chcete-li změnit pro celou aplikaci.  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled vstupu](../../../../docs/framework/wpf/advanced/input-overview.md)
