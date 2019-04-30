---
title: 'Postupy: Definice šablony GroupBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: dd53af87ec2d12b2ed0dcf2b23374d76e8f631a9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61910517"
---
# <a name="how-to-define-a-groupbox-template"></a>Postupy: Definice šablony GroupBox
Tento příklad ukazuje, jak vytvořit šablonu pro <xref:System.Windows.Controls.GroupBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje <xref:System.Windows.Controls.GroupBox> šablony ovládacího prvku pomocí <xref:System.Windows.Controls.Grid> ovládací prvek pro rozložení. Šablona používá <xref:System.Windows.Controls.BorderGapMaskConverter> definovat ohraničení <xref:System.Windows.Controls.GroupBox> tak, aby ohraničení není skryl <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> obsah.  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](~/samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.GroupBox>
- [Postupy: Vytvoření GroupBox](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms748321(v=vs.90))
