---
title: 'Postupy: Vytvoření tlačítka s obrázkem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Button controls [WPF], creating
ms.assetid: 607a193c-4098-4dd8-8dc0-51256cec2020
ms.openlocfilehash: 5be928ac75ad727feabcde07ac0c6dc76ed130e6
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59120715"
---
# <a name="how-to-create-a-button-that-has-an-image"></a>Postupy: Vytvoření tlačítka s obrázkem
Tento příklad ukazuje, jak pro zahrnutí obrázku na <xref:System.Windows.Controls.Button>.  
  
## <a name="example"></a>Příklad  
 Následující příklad vytvoří dva <xref:System.Windows.Controls.Button> ovládacích prvků. Jeden <xref:System.Windows.Controls.Button> obsahuje text a druhý obsahuje bitovou kopii. Na obrázku je do složky s názvem data, která je podsložkou složky projektu v příkladu. Když uživatel klikne <xref:System.Windows.Controls.Button> , která má bitovou kopii, pozadí a textu druhé <xref:System.Windows.Controls.Button> změnit.  
  
 Tento příklad vytvoří <xref:System.Windows.Controls.Button> ovládací prvky s použitím značky, ale kód používá k zápisu <xref:System.Windows.Controls.Primitives.ButtonBase.Click> obslužných rutin událostí.  
  
 [!code-xaml[BtnColor#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml#4)]  
  
 [!code-csharp[BtnColor#6](~/samples/snippets/csharp/VS_Snippets_Wpf/BtnColor/CSharp/Pane1.xaml.cs#6)]
 [!code-vb[BtnColor#6](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BtnColor/VisualBasic/Pane1.xaml.vb#6)]  
  
## <a name="see-also"></a>Viz také:

- [Ovládací prvky](index.md)
- [Knihovna ovládacích prvků](control-library.md)
