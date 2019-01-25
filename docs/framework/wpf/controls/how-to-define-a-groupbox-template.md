---
title: 'Postupy: Definice šablony GroupBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: 0e1b0487629bba3550a8b6b4a31c163a7ade6a87
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54743719"
---
# <a name="how-to-define-a-groupbox-template"></a>Postupy: Definice šablony GroupBox
Tento příklad ukazuje, jak vytvořit šablonu pro <xref:System.Windows.Controls.GroupBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje <xref:System.Windows.Controls.GroupBox> šablony ovládacího prvku pomocí <xref:System.Windows.Controls.Grid> ovládací prvek pro rozložení. Šablona používá <xref:System.Windows.Controls.BorderGapMaskConverter> definovat ohraničení <xref:System.Windows.Controls.GroupBox> tak, aby ohraničení není skryl <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> obsah.  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.GroupBox>
- [Groupbox – postupy](https://msdn.microsoft.com/library/7692e155-a4c6-428c-b7e0-64b3740daca7)
