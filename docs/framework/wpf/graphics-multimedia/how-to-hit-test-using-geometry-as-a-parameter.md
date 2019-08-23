---
title: 'Postupy: Ověřování pozice pomocí objektu Geometry jako parametru'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
ms.openlocfilehash: 8bed7784b00f49178c9a87def74b62f7ce620ec7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923409"
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>Postupy: Ověřování pozice pomocí objektu Geometry jako parametru
Tento příklad ukazuje, jak provést test přístupů na vizuální objekt pomocí <xref:System.Windows.Media.Geometry> parametru jako parametr testu volání.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit test přístupů pomocí <xref:System.Windows.Media.GeometryHitTestParameters> <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metody. Hodnota, která je předána `OnMouseDown` metodě, slouží k vytvoření <xref:System.Windows.Media.Geometry> objektu, aby bylo možné rozšířit rozsah testu přístupů. <xref:System.Windows.Point>  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 Vlastnost poskytuje informace o výsledcích testu <xref:System.Windows.Media.Geometry> volání, který používá jako parametr testu volání. <xref:System.Windows.Media.GeometryHitTestResult> <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> Následující ilustrace znázorňuje vztah mezi geometrií testu přístupů (modrý kroužek) a vykresleným obsahem cílového vizuálního objektu (červené čtverce).  
  
 ![Diagram, který zobrazuje IntersectionDetail používaný při testování přístupů.](./media/how-to-hit-test-using-geometry-as-a-parameter/intersectiondetail-hit-test.png)  
  
 Následující příklad ukazuje, jak implementovat volání testu volání, když <xref:System.Windows.Media.Geometry> se používá jako parametr testu volání. Parametr je přetypování <xref:System.Windows.Media.GeometryHitTestResult> na hodnotu, aby se <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> načetla hodnota vlastnosti. `result` Hodnota vlastnosti umožňuje určit, zda <xref:System.Windows.Media.Geometry> je parametr testu volání plně nebo částečně obsažen v rámci vykresleného obsahu cíle testu volání. V tomto případě vzorový kód přidává pouze výsledky testů přístupů do seznamu pro vizuály, které jsou plně obsaženy v cílové hranici.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](~/samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
> Zpětné volání by nemělo být voláno, když je <xref:System.Windows.Media.IntersectionDetail.Empty>detail průniku. <xref:System.Windows.Media.HitTestResult>  
  
## <a name="see-also"></a>Viz také:

- [Ověřování pozice ve vizuální vrstvě](hit-testing-in-the-visual-layer.md)
- [Ověření pozice objektu Geometry ve vizuálním objektu](how-to-hit-test-geometry-in-a-visual.md)
