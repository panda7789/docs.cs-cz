---
title: "Postupy: Vytvoření a použití objektu GridLengthConverter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: Grid control [WPF], creating [WPF], GridLengthConverter objects
ms.assetid: 5ab75911-e36a-4825-80e4-081c57e8e182
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 775d51a35f64f8736931dec32fb439bb9925be53
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-and-use-a-gridlengthconverter-object"></a>Postupy: Vytvoření a použití objektu GridLengthConverter
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit a použít instanci <xref:System.Windows.GridLengthConverter>. V příkladu definuje vlastní metodu s názvem `changeCol`, který předává <xref:System.Windows.Controls.ListBoxItem> k <xref:System.Windows.GridLengthConverter> , která převádí <xref:System.Windows.Controls.ContentControl.Content%2A> z <xref:System.Windows.Controls.ListBoxItem> na instanci <xref:System.Windows.GridLength>. Převedená hodnota se potom předá zpět jako hodnota <xref:System.Windows.Controls.ColumnDefinition.Width%2A> vlastnost <xref:System.Windows.Controls.ColumnDefinition> elementu.  
  
 V příkladu definuje také druhý vlastní metodu, s názvem `changeColVal`. Tato vlastní metoda převede <xref:System.Windows.Controls.Primitives.RangeBase.Value%2A> z <xref:System.Windows.Controls.Slider> k <xref:System.String> a potom předává, které hodnoty zpět do <xref:System.Windows.Controls.ColumnDefinition> jako <xref:System.Windows.Controls.ColumnDefinition.Width%2A> elementu.  
  
 Všimněte si, že samostatné [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] soubor definuje obsah <xref:System.Windows.Controls.ListBoxItem>.  
  
 [!code-csharp[gridlengthConverterGrid#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/gridlengthConverterGrid/CSharp/Window1.xaml.cs#1)]
 [!code-vb[gridlengthConverterGrid#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/gridlengthConverterGrid/VisualBasic/Window1.xaml.vb#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.GridLengthConverter>  
 <xref:System.Windows.GridLength>
