---
title: 'Postupy: Úprava mezer mezi odstavci'
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: e2a6ba34e3ab15eb316671fef7c11bea03d53c73
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367476"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a>Postupy: Úprava mezer mezi odstavci
Tento příklad ukazuje, jak upravit nebo odstranit mezer mezi odstavci v plovoucího obsahu.  
  
 V toku obsahu místo navíc, který se zobrazí mezi odstavci je výsledkem okraje nastavit na těchto odstavcích; Proto mohou být řízena mezer mezi odstavci nastavování okrajů v těchto odstavcích.  Úplně eliminovat nadbytečné mezery mezi dva odstavce, nastavit okraje pro odstavce na **0**.  K dosažení jednotné mezer mezi odstavci v celém celý <xref:System.Windows.Documents.FlowDocument>, použití stylu pro nastavení jednotné okraj hodnoty pro všechny odstavce v <xref:System.Windows.Documents.FlowDocument>.  
  
 Je důležité si uvědomit, že okraje pro dva odstavce sousedící bude "sbalit" větší z dva okraje, a nemuseli zdvojovací nahoru. Takže pokud dva odstavce sousedící okrajů 20 pixelů a 40 pixelů v uvedeném pořadí, je výsledný mezeru mezi odstavců 40 pixelů, větší z hodnoty dvě vlastnosti okraj.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá používání stylů pro nastavení okraje pro všechny <xref:System.Windows.Documents.Paragraph> prvků v <xref:System.Windows.Documents.FlowDocument> k **0**, což účinně eliminuje nadbytečné mezery mezi odstavci v <xref:System.Windows.Documents.FlowDocument>.  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
