---
title: 'Postupy: Sestavení standardního dialogového okna uživatelského rozhraní pomocí mřížky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- dialog boxes [WPF], creating
- Grid control [WPF], creating [WPF], dialog box
ms.assetid: d6ac3d51-844b-4d29-96d8-81a696a7b960
ms.openlocfilehash: d0b24e320c2a341b069e1c9c3e8b6d5e93076733
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551879"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>Postupy: Sestavení standardního dialogového okna uživatelského rozhraní pomocí mřížky
Tento příklad ukazuje, jak vytvořit standard [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialogové okno pomocí <xref:System.Windows.Controls.Grid> elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dialogové okno podobné **spustit** dialogovém okně [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operačního systému.  
  
 V příkladu se vytváří <xref:System.Windows.Controls.Grid> a používá <xref:System.Windows.Controls.ColumnDefinition> a <xref:System.Windows.Controls.RowDefinition> třídy k definování pět sloupců a řádků čtyři.  
  
 V příkladu se pak přidá a umisťuje <xref:System.Windows.Controls.Image>, `RunIcon.png`, účelem zastoupení obrázku, která se nachází v dialogovém okně. Obrázek je umístěn v první sloupec a řádek <xref:System.Windows.Controls.Grid> (levého horního rohu).  
  
 V dalším kroku v příkladu přidáme <xref:System.Windows.Controls.TextBlock> element první sloupec, který zahrnuje zbývající sloupce prvního řádku. Přidá další <xref:System.Windows.Controls.TextBlock> element na druhý řádek v první sloupec, aby reprezentoval **otevřete** textové pole. A <xref:System.Windows.Controls.TextBlock> způsobem, která představuje vstupní data oblast.  
  
 Nakonec v příkladu přidáme tři <xref:System.Windows.Controls.Button> elementy poslední řádek, které představují **OK**, **zrušit**, a **Procházet** události.  
  
 [!code-csharp[GridRunDialog#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Grid>  
 <xref:System.Windows.GridUnitType>  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/controls/grid-how-to-topics.md)
