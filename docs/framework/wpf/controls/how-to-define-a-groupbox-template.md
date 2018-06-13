---
title: 'Postupy: Definice šablony GroupBox'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [WPF], GroupBox
- GroupBox control [WPF], creating templates
ms.assetid: 85a4d1a7-4753-4f4a-b26d-14fa10c1ddb5
ms.openlocfilehash: ed66d51e87a25f74e646d0d535ac9e4ee9c8a056
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33551133"
---
# <a name="how-to-define-a-groupbox-template"></a>Postupy: Definice šablony GroupBox
Tento příklad ukazuje, jak vytvořit šablonu pro <xref:System.Windows.Controls.GroupBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje <xref:System.Windows.Controls.GroupBox> šablony ovládacího prvku pomocí <xref:System.Windows.Controls.Grid> řízení rozložení. Šablona používá <xref:System.Windows.Controls.BorderGapMaskConverter> k definování ohraničení <xref:System.Windows.Controls.GroupBox> tak, aby ohraničení není skrývat <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> obsah.  
  
 [!code-xaml[GroupBoxSnippet#GroupBoxTemplate](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GroupBoxSnippet/CS/Window1.xaml#groupboxtemplate)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.GroupBox>  
 [Groupbox – postupy témata](http://msdn.microsoft.com/library/7692e155-a4c6-428c-b7e0-64b3740daca7)
