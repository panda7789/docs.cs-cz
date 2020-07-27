---
title: 'Postupy: Změna typu kurzoru'
description: Změní kurzor ukazatele myši u prvku a pro aplikaci v Windows Presentation Foundation. Tento příklad se skládá z XAML a souboru kódu na pozadí.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- mouse pointer [WPF], cursor type
- cursor (mouse pointer)
ms.assetid: 08c945a7-8ab0-4320-acf3-0b4955a344c2
ms.openlocfilehash: ce0bc290948a0e52e85f76ceb62a330b49fd87ea
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87165969"
---
# <a name="how-to-change-the-cursor-type"></a>Postupy: Změna typu kurzoru
Tento příklad ukazuje, jak změnit <xref:System.Windows.Input.Cursor> ukazatel myši pro určitý element a pro aplikaci.  
  
 Tento příklad se skládá ze [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] souboru a souboru kódu na pozadí.  
  
## <a name="example"></a>Příklad  
 Uživatelské rozhraní je vytvořeno, což se skládá z a <xref:System.Windows.Controls.ComboBox> vybrat požadovanou <xref:System.Windows.Input.Cursor> dvojici <xref:System.Windows.Controls.RadioButton> objektů k určení, zda se Změna kurzoru vztahuje pouze na jeden prvek nebo platí pro celou aplikaci, a <xref:System.Windows.Controls.Border> prvek, který je prvkem, na který je nový kurzor aplikován.  
  
 [!code-xaml[cursors#ChangeCursorsXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml#changecursorsxaml)]  
  
 Následující kód vytvoří <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> obslužnou rutinu události, která je volána při změně typu kurzoru v <xref:System.Windows.Controls.ComboBox> .  Příkaz přepíná filtry na název kurzoru a nastavuje vlastnost s <xref:System.Windows.FrameworkElement.Cursor%2A> <xref:System.Windows.Controls.Border> názvem *DisplayArea*.  
  
 Pokud je Změna kurzoru nastavena na "celá aplikace", <xref:System.Windows.Input.Mouse.OverrideCursor%2A> vlastnost je nastavena na <xref:System.Windows.FrameworkElement.Cursor%2A> vlastnost <xref:System.Windows.Controls.Border> ovládacího prvku.  To vynutí změnu kurzoru pro celou aplikaci.  
  
 [!code-csharp[cursors#ChangeCursorsSample](~/samples/snippets/csharp/VS_Snippets_Wpf/cursors/CSharp/Window1.xaml.cs#changecursorssample)]
 [!code-vb[cursors#ChangeCursorsSample](~/samples/snippets/visualbasic/VS_Snippets_Wpf/cursors/VisualBasic/Window1.xaml.vb#changecursorssample)]  
  
## <a name="see-also"></a>Viz také

- [Přehled vstupu](input-overview.md)
