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
ms.openlocfilehash: 68c9653e616388374aad2ad33ac7dab68446241d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923418"
---
# <a name="how-to-build-a-standard-ui-dialog-box-by-using-grid"></a>Postupy: Sestavení standardního dialogového okna uživatelského rozhraní pomocí mřížky
Tento příklad ukazuje, jak vytvořit standardní [!INCLUDE[TLA#tla_ui](../../../../includes/tlasharptla-ui-md.md)] dialogové okno <xref:System.Windows.Controls.Grid> pomocí elementu.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dialogové okno, jako je dialogové okno **Spustit** v operačním systému Windows.  
  
 V příkladu se vytvoří <xref:System.Windows.Controls.Grid> a <xref:System.Windows.Controls.ColumnDefinition> pomocí tříd a <xref:System.Windows.Controls.RowDefinition> definuje pět sloupců a čtyři řádky.  
  
 Příklad následně přidá a umístí <xref:System.Windows.Controls.Image>do, `RunIcon.png`, aby představoval obrázek, který se nachází v dialogovém okně. Obrázek se umístí do prvního sloupce a řádku <xref:System.Windows.Controls.Grid> (v levém horním rohu).  
  
 Dále tento příklad přidá <xref:System.Windows.Controls.TextBlock> prvek do prvního sloupce, který zahrnuje zbývající sloupce prvního řádku. Přidá další <xref:System.Windows.Controls.TextBlock> prvek do druhého řádku v prvním sloupci, který představuje **otevřené** textové pole. <xref:System.Windows.Controls.TextBlock> Následuje, který představuje oblast pro zadávání dat.  
  
 Nakonec <xref:System.Windows.Controls.Button> příklad přidá tři prvky do finálního řádku, které reprezentují události **OK**, **Zrušit**a **Procházet** .  
  
 [!code-csharp[GridRunDialog#1](~/samples/snippets/csharp/VS_Snippets_Wpf/GridRunDialog/CSharp/window1.xaml.cs#1)]
 [!code-vb[GridRunDialog#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/GridRunDialog/VisualBasic/grid_vb.vb#1)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Grid>
- <xref:System.Windows.GridUnitType>
- [Přehled panelu](panels-overview.md)
- [Témata s postupy](grid-how-to-topics.md)
