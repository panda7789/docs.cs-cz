---
title: "Postupy: Vytváření rozšíření pomocí prvku ScrollViewer"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- controls [WPF], Expander
- ScrollViewer control [WPF], with Expander control
- Expander control [WPF], creating
- controls [WPF], ScrollViewer
ms.assetid: 2ad124d2-2406-4157-aaf2-64e067298f01
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 817fb8d04e680335aff726db84cdfb9630b4cdf4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-expander-with-a-scrollviewer"></a>Postupy: Vytváření rozšíření pomocí prvku ScrollViewer
Tento příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Expander> ovládací prvek, který obsahuje komplexní obsah, například bitové kopie a text. Tento příklad také zvýrazněna obsah <xref:System.Windows.Controls.Expander> v <xref:System.Windows.Controls.ScrollViewer> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.Expander>. V příkladu se používá <xref:System.Windows.Controls.Primitives.BulletDecorator> ovládací prvek, který obsahuje bitovou kopii a text, aby bylo možné definovat <xref:System.Windows.Controls.HeaderedContentControl.Header%2A>. A <xref:System.Windows.Controls.ScrollViewer> řízení poskytuje metodu pro posouvání rozšířené obsah.  
  
 Všimněte si, že v příkladu je nastaven <xref:System.Windows.FrameworkElement.Height%2A> vlastnost <xref:System.Windows.Controls.ScrollViewer> místo na obsah. Pokud <xref:System.Windows.FrameworkElement.Height%2A> je nastavený na obsah, <xref:System.Windows.Controls.ScrollViewer> neumožňuje uživateli posuňte se k obsahu. <xref:System.Windows.FrameworkElement.Width%2A> Je nastavena na <xref:System.Windows.Controls.Expander> řízení a toto nastavení se vztahuje na <xref:System.Windows.Controls.HeaderedContentControl.Header%2A> a rozšířená obsah.  
  
 [!code-xaml[ExpanderRichContent#CreateExpander](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml#createexpander)]  
  
 [!code-csharp[ExpanderRichContent#CreateExpanderCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ExpanderRichContent/CSharp/Window1.xaml.cs#createexpandercode)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Expander>  
 [Přehled Expander](../../../../docs/framework/wpf/controls/expander-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/controls/expander-how-to-topics.md)
