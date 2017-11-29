---
title: "Postupy: Připojení doplňku k elementu"
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
helpviewer_keywords:
- UIElements [WPF], binding adorners to
- adorners [WPF], binding to specified UIElements
ms.assetid: b2101611-a0ee-4137-bdb8-9b3673d2e6b9
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b1da3216ce6d3507c304ff957728d33ba1b9bd9
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-bind-an-adorner-to-an-element"></a>Postupy: Připojení doplňku k elementu
Tento příklad ukazuje, jak se prostřednictvím kódu programu vytvořit vazbu adorner do určeného <xref:System.Windows.UIElement>.  
  
## <a name="example"></a>Příklad  
 K vytvoření vazby adorner konkrétní <xref:System.Windows.UIElement>, postupujte takto:  
  
1.  Volání `static` metoda <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A> získat <xref:System.Windows.Documents.AdornerLayer> objekt pro <xref:System.Windows.UIElement> k být ozdobené. <xref:System.Windows.Documents.AdornerLayer.GetAdornerLayer%2A>provede až vizuálním stromu, začínající v zadaném **prvků uživatelského rozhraní**a vrátí první vrstvu adorner najde. (Pokud se nenajdou žádné adorner vrstvy, metoda vrátí hodnotu null.)  
  
2.  Volání <xref:System.Windows.Documents.AdornerLayer.Add%2A> metoda pro vazbu adorner k cíli **prvků uživatelského rozhraní**.  
  
 Následující příklad vytvoří vazbu SimpleCircleAdorner (viz výše) k <xref:System.Windows.Controls.TextBox> s názvem *hodnotu myTextBox*.  
  
 [!code-csharp[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/CSharp/Window1.xaml.cs#_adornsingleelement)]
 [!code-vb[Adorners_SimpleCircleAdorner#_AdornSingleElement](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Adorners_SimpleCircleAdorner/VisualBasic/Window1.xaml.vb#_adornsingleelement)]  
  
> [!NOTE]
>  Pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] vytvořit vazbu adorner jiný element se aktuálně nepodporuje.  
  
## <a name="see-also"></a>Viz také  
 [Přehled ozdobného prvku](../../../../docs/framework/wpf/controls/adorners-overview.md)
