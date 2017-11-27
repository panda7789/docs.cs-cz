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
ms.openlocfilehash: 5e498bc8e425198e479d7ce0b2328e0efa3ede70
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [Kreslení objekty – přehled](../../../../docs/framework/wpf/graphics-multimedia/drawing-objects-overview.md)  
 [Přehled vykreslování grafiky WPF](../../../../docs/framework/wpf/graphics-multimedia/wpf-graphics-rendering-overview.md)
