---
title: "Postupy: Vyčíslení vykreslovaného vizuálního obsahu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- retrieving the DrawingGroup value of a Visual [WPF]
- enumerating the contents of a Visual [WPF]
ms.assetid: 2974ddb3-2997-4713-8fd2-e93d549c58a8
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5c97926286076149a6eedf34bb70bbc76b2e0d8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enumerate-drawing-content-of-a-visual"></a>Postupy: Vyčíslení vykreslovaného vizuálního obsahu
<xref:System.Windows.Media.Drawing> Objekt zadejte objektový model pro vytvoření výčtu obsah <xref:System.Windows.Media.Visual>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metoda pro načtení <xref:System.Windows.Media.DrawingGroup> hodnotu <xref:System.Windows.Media.Visual> a výčet ho.  
  
> [!NOTE]
>  Při vytváření obsahu vizuálu jsou výčtu, jsou načítání <xref:System.Windows.Media.Drawing> objekty a není základní znázornění dat, vykreslení jako seznam vektorové grafiky instrukcí. Další informace najdete v tématu [vykreslování přehled grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md).  
  
 [!code-csharp[DrawingMiscSnippets_snip#GraphicsMMRetrieveDrawings](../../../../samples/snippets/csharp/VS_Snippets_Wpf/DrawingMiscSnippets_snip/CSharp/EnumerateDrawingsExample.xaml.cs#graphicsmmretrievedrawings)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Drawing>  
 <xref:System.Windows.Media.DrawingGroup>  
 <xref:System.Windows.Media.VisualTreeHelper>  
 [Přehled nakreslených objektů](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
