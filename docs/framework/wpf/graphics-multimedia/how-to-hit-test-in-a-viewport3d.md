---
title: "Postupy: Spuštění testu v objektu Viewport3D"
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
- 3-D visuals [WPF], hit-testing for
- hit tests [WPF], for 3-D visuals
- Viewport3D [WPF]
ms.assetid: 42bfbd99-c7c6-43f1-940b-90448faa412e
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: efd8016e0169a258dbe7b6d9a54a81b1cda94ee4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-hit-test-in-a-viewport3d"></a>Postupy: Spuštění testu v objektu Viewport3D
Tento příklad ukazuje, jak zadat test pro 3D Vizuálů na <xref:System.Windows.Controls.Viewport3D>.  
  
 Protože <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> vrátí informace o vytváření 2D a 3D, je možné k iteraci v rámci výsledky testů číst pouze 3D výsledky.  
  
 [!code-csharp[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn4)]
 [!code-vb[HitTest3D#HitTest3D3DN4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn4)]  
  
 <xref:System.Windows.Media.HitTestResultBehavior> v následujícím kódu určuje, jak se zpracují výsledky testů přístupů.  `UpdateResultInfo`a `UpdateMaterial` místně definované způsoby.  
  
 [!code-csharp[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTest3D/CSharp/Window1.xaml.cs#hittest3d3dn5)]
 [!code-vb[HitTest3D#HitTest3D3DN5](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTest3D/visualbasic/window1.xaml.vb#hittest3d3dn5)]  
  
## <a name="see-also"></a>Viz také  
 [Ukázka testování průchodu 3D](http://go.microsoft.com/fwlink/?LinkID=159959)
