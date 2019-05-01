---
title: 'Postupy: Výčet systémových písem'
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
ms.openlocfilehash: c7e81b5d1b70ba911a0b505219f7977e019038cf
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62001595"
---
# <a name="how-to-enumerate-system-fonts"></a>Postupy: Výčet systémových písem
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit výčet písma v kolekci písma systému. Název rodiny písem pro každou z <xref:System.Windows.Media.FontFamily> v rámci <xref:System.Windows.Media.Fonts.SystemFontFamilies%2A> se přidá jako položky na pole se seznamem.  
  
 [!code-csharp[TextOverview#100](~/samples/snippets/csharp/VS_Snippets_Wpf/TextOverview/CSharp/Window1.xaml.cs#100)]
 [!code-vb[TextOverview#100](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextOverview/visualbasic/window1.xaml.vb#100)]  
  
 Pokud se více verzí stejného rodiny písem nachází ve stejném adresáři, [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)] písma výčet vrátí nejnovější verzi písmo. Pokud informace o verzi neposkytuje řešení, je vrácena písma s poslední časové razítko. Pokud informace o časové razítko je ekvivalentní, je vrácena písma souboru, který je první v abecedním pořadí.
