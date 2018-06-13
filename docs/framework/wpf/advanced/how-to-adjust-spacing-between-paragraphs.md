---
title: 'Postupy: Úprava mezer mezi odstavci'
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: b232903054cf45b70ba99a9223352391498cf79b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542945"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a>Postupy: Úprava mezer mezi odstavci
Tento příklad ukazuje, jak upravit nebo odstranit mezery mezi odstavci v toku obsahu.  
  
 V toku obsahu místo navíc, který se zobrazí mezi odstavců je výsledkem okraje nastavit u těchto odstavců; Proto může být řízena mezery mezi odstavci nastavování okrajů na těchto odstavcích.  Zcela eliminovat mezera navíc mezi dva odstavce, nastavení okrajů pro odstavců na **0**.  K dosažení uniform mezery mezi odstavci v rámci celou <xref:System.Windows.Documents.FlowDocument>, můžete nastavit hodnotu uniform rozpětí pro všechny odstavce v pomocí stylů <xref:System.Windows.Documents.FlowDocument>.  
  
 Je důležité si uvědomit, že okraje pro dva odstavce přiléhající bude "sbalit" větší dva okraje, namísto prodloužily nahoru. Ano Pokud dva odstavce přiléhající okraje 20 pixelů a 40 pixelů v uvedeném pořadí, výsledná mezery mezi odstavců je 40 pixelů, větší hodnot dva okraje.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá stylů pro nastavení okraje pro všechny <xref:System.Windows.Documents.Paragraph> elementů v <xref:System.Windows.Documents.FlowDocument> k **0**, které efektivně eliminuje mezi odstavců v mezera navíc <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
