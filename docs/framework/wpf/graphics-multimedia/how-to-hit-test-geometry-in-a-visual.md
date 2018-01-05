---
title: "Postupy: Spuštění geometrie testu ve vizuálním objektu"
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
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a990a43853e375c1c97f88dc6792932ad64c8d37
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a>Postupy: Spuštění geometrie testu ve vizuálním objektu
Tento příklad ukazuje, jak chcete provést test přístupů na vizuální objekt, který se skládá z jedné nebo více <xref:System.Windows.Media.Geometry> objekty.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst <xref:System.Windows.Media.DrawingGroup> z visual objektu, který používá <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> metoda. Ověření pozice pak provádí na vykreslovaných obsah jednotlivých kreslení v <xref:System.Windows.Media.DrawingGroup> k určení, které geometrie byl vybrán.  
  
> [!NOTE]
>  Ve většině případů byste použili <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda k určení, zda bod protíná některé z vykreslené obsah vizuál.  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 <xref:System.Windows.Media.Geometry.FillContains%2A> Metoda je přetížené metody, která umožňuje průchodu testu s použitím zadané <xref:System.Windows.Point> nebo <xref:System.Windows.Media.Geometry>. Pokud je vytažený geometry, tahu rozšířit mimo hranice výplně. V takovém případě můžete chtít volání <xref:System.Windows.Media.Geometry.StrokeContains%2A> kromě <xref:System.Windows.Media.Geometry.FillContains%2A>.  
  
 Můžete zadat taky <xref:System.Windows.Media.ToleranceType> používané pro účely Bézierovy sloučení.  
  
> [!NOTE]
>  Tato ukázka není vzít v úvahu žádné transformace nebo výstřižek, které mohou být použity u geometrie. Kromě toho tato ukázka nebude fungovat s ovládacím prvkem stylem, vzhledem k tomu, že nemá žádné výkresy přímo s ním spojená.  
  
## <a name="see-also"></a>Viz také  
 [Ověřování pozice ve vizuální vrstvě](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [Ověřování pozice pomocí objektu Geometry jako parametru](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-using-geometry-as-a-parameter.md)
