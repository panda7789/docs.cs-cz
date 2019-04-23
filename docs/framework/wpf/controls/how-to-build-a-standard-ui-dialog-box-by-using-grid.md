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
ms.openlocfilehash: 0ade908e92e552017acb9ba242ccba2c28c3c995
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59149523"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>Postupy: Sestavení standardního dialogového okna uživatelského rozhraní pomocí mřížky
Tento příklad ukazuje, jak vytvořit standardní [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialogové okno s použitím <xref:System.Windows.Controls.Grid> elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dialogové okno podobné **spustit** dialogovém [!INCLUDE[TLA#tla_mswin](../../../../includes/tlasharptla-mswin-md.md)] operačního systému.  
  
 V příkladu se vytvoří <xref:System.Windows.Controls.Grid> a používá <xref:System.Windows.Controls.ColumnDefinition> a <xref:System.Windows.Controls.RowDefinition> tříd k definování pět sloupců a čtyři řádky.  
  
 V příkladu se pak přidá a umístí <xref:System.Windows.Controls.Image>, `RunIcon.png`, představující obrázek, který se nachází v dialogovém okně. Na obrázku je umístěn v prvním sloupci a řádku <xref:System.Windows.Controls.Grid> (levý horní roh).  
  
 V dalším kroku příklad přidá <xref:System.Windows.Controls.TextBlock> element na první sloupec, který zahrnuje zbývající sloupce na prvním řádku. Přidá další <xref:System.Windows.Controls.TextBlock> element na druhém řádku v prvním sloupci znázornit **otevřít** textového pole. A <xref:System.Windows.Controls.TextBlock> způsobem, která představuje vstupní datové oblasti.  
  
 Nakonec příklad přidá tři <xref:System.Windows.Controls.Button> elementy na posledním řádku, které představují **OK**, **zrušit**, a **Procházet** události.  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [Přehled panelu](panels-overview.md)
- [Témata s postupy](grid-how-to-topics.md)
