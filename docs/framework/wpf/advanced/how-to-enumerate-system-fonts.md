---
title: 'Postupy: Vyčíslení systémových písem'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- typography [WPF], enumerating system fonts
- fonts [WPF], enumerating
- system fonts [WPF], enumerating
- enumerating [WPF], system fonts
ms.assetid: 36e37791-55b9-4f01-a496-5cc10335e6a6
ms.openlocfilehash: 7fc996a2d3ba7042fce70afc20be5d64042c2b63
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enumerate-system-fonts"></a>Postupy: Vyčíslení systémových písem
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit výčet písem v kolekci písma systému. Název rodiny písem jednotlivých <xref:System.Windows.Media.FontFamily> v rámci <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> je přidána do pole se seznamem jako položku.  
  
 [!code-csharp[TextOverview#100](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 Pokud více verzí stejné rodiny písem nacházet ve stejném adresáři [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] písma výčtu vrátí nejnovější verzi písma. Pokud informace o verzi neposkytuje řešení, je vrácena písma s nejnovější časové razítko. Pokud informace časového razítka jsou ekvivalentní, vrátí se soubor písma, který je první v abecedním pořadí.
