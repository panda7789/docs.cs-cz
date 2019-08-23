---
title: 'Postupy: Ověření pozice objektu Geometry ve vizuálním objektu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects comprising Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], visual objects comprising
ms.assetid: 8bf2643f-d7f9-4cb4-9ea6-5b893c23200d
ms.openlocfilehash: 52b9b99b0af38d797e4a3c98dc0979211c930c1f
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923382"
---
# <a name="how-to-hit-test-geometry-in-a-visual"></a>Postupy: Ověření pozice objektu Geometry ve vizuálním objektu
Tento příklad ukazuje, jak provést test přístupů na vizuální objekt, který se skládá z jednoho nebo více <xref:System.Windows.Media.Geometry> objektů.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak načíst <xref:System.Windows.Media.DrawingGroup> z vizuálního objektu, který <xref:System.Windows.Media.VisualTreeHelper.GetDrawing%2A> používá metodu. Test volání se pak provede na vykresleném obsahu každého výkresu v <xref:System.Windows.Media.DrawingGroup> a určí, který geometrie se dosáhl.  
  
> [!NOTE]
> Ve většině případů byste použili <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metodu k určení, zda se v bodě protínají jakékoli vykreslené obsahy vizuálu.  
  
 [!code-csharp[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/csharp/VS_Snippets_Wpf/VisualsOverview/CSharp/Window1.xaml.cs#visualsoverviewsnippet4)]
 [!code-vb[VisualsOverview#VisualsOverviewSnippet4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/VisualsOverview/visualbasic/window1.xaml.vb#visualsoverviewsnippet4)]  
  
 Metoda je přetížená metoda, která umožňuje volání testu pomocí zadaného <xref:System.Windows.Point> nebo <xref:System.Windows.Media.Geometry>. <xref:System.Windows.Media.Geometry.FillContains%2A> Pokud je geometrie zatažena, tah lze zvětšit mimo hranice výplně. V takovém případě může být vhodné volat <xref:System.Windows.Media.Geometry.StrokeContains%2A> <xref:System.Windows.Media.Geometry.FillContains%2A>kromě.  
  
 Můžete také zadat <xref:System.Windows.Media.ToleranceType> , který se používá pro účely plochého navýšení Bézierových křivek.  
  
> [!NOTE]
> Tato ukázka nebere v úvahu žádné transformace nebo oříznutí, které mohou být pro geometrii aplikovány. Kromě toho tato ukázka nebude fungovat se stylem ovládacího prvku, protože nemá přímo přidružené kresby.  
  
## <a name="see-also"></a>Viz také:

- [Ověřování pozice ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
- [Ověřování pozice pomocí objektu Geometry jako parametru](how-to-hit-test-using-geometry-as-a-parameter.md)
