---
title: 'Postupy: Spuštění testu použitím geometrie jako parametru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 3d6f4190a5b5c8410a6be01d2645df9c123f9ac4
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/25/2019
ms.locfileid: "58410612"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>Postupy: Spuštění testu použitím geometrie jako parametru
Tento příklad ukazuje, jak provádět ověření pozice ve vizuální objekty pomocí <xref:System.Windows.Media.Geometry> jako nalezený testování parametru.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit ověření pozice pomocí <xref:System.Windows.Media.GeometryHitTestParameters> pro <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody. <xref:System.Windows.Point> Hodnotu, která je předána `OnMouseDown` metoda se používá k vytvoření <xref:System.Windows.Media.Geometry> objektu, aby bylo možné rozšířit rozsah průchodů testů.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> Vlastnost <xref:System.Windows.Media.GeometryHitTestResult> poskytuje informace o výsledcích přístupů test, který se používá <xref:System.Windows.Media.Geometry> jako nalezený testování parametru. Následující ilustrace znázorňuje vztah mezi geometrie ověření pozice (modré circle) a vykreslený obsah visual cílový objekt (červený čtvereček).  
  
 ![Diagram zobrazující průběh IntersectionDetail použitou v testování průchodu.](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 Následující příklad ukazuje, jak provádět ověření pozice zpětné volání při <xref:System.Windows.Media.Geometry> slouží jako parametr ověření pozice. `result` Parametr přetypováno na <xref:System.Windows.Media.GeometryHitTestResult> k načtení hodnoty <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> vlastnost. Hodnota vlastnosti umožňuje určit, jestli <xref:System.Windows.Media.Geometry> ověření pozice parametru je částečně nebo zcela obsažena v vykreslený obsah cíl ověření pozice. V takovém případě ukázkový kód je pouze přidáním výsledky ověření pozice do seznamu pro vizuály, které jsou plně obsaženy v rámci hranic cíl.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.HitTestResult> Zpětného volání by neměla být volána po průniku podrobností <xref:System.Windows.Media.IntersectionDetail.Empty>.  
  
## <a name="see-also"></a>Viz také:
- [Ověřování pozice ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
- [Ověření pozice objektu Geometry ve vizuálním objektu](how-to-hit-test-geometry-in-a-visual.md)
