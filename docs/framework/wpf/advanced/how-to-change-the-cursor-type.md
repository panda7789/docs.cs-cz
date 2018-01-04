---
title: "Postupy: Změna typu kurzoru"
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
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 31c59f4c90eed00775fc9fceaf872391faa93784
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-cursor-type"></a>Postupy: Změna typu kurzoru
Tento příklad ukazuje, jak změnit <xref:System.Windows.Input.Cursor> ukazatele myši pro konkrétní element a pro aplikaci.  
  
 V tomto příkladu se skládá z [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru a souboru kódu.  
  
## <a name="example"></a>Příklad  
 Vytvoření uživatelského rozhraní, která se skládá z <xref:System.Windows.Controls.ComboBox> vyberte požadovanou <xref:System.Windows.Input.Cursor>, pár <xref:System.Windows.Controls.RadioButton> objekty, které chcete zjistit, zda změna kurzoru platí pro pouze jeden element či platí v celé aplikaci a <xref:System.Windows.Controls.Border> což je nový kurzor se použije pro element.  
  
 [!code-xaml[cursors#ChangeCursorsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 Následující kód za vytvoří <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> obslužná rutina události, která je volána, když typ kurzoru se změnilo v <xref:System.Windows.Controls.ComboBox>.  Příkaz switch filtry na název kurzoru a nastaví <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost <xref:System.Windows.Controls.Border> který s názvem *DisplayArea*.  
  
 Pokud změnu kurzor je nastavený na "Celou aplikaci", <xref:System.Windows.Input.Mouse.OverrideCursor%2A> je nastavena na <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost <xref:System.Windows.Controls.Border> ovládacího prvku.  Vynutí kurzor změnit pro celou aplikaci.  
  
 [!code-csharp[cursors#ChangeCursorsSample](../../../../samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled vstupu](../../../../docs/framework/wpf/advanced/input-overview.md)
