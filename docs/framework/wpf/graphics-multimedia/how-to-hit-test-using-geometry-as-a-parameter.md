---
title: "Postupy: Spuštění testu použitím geometrie jako parametru"
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
- hit tests [WPF], on visual objects using Geometry objects [WPF]
- visual objects [WPF], hit tests on
- Geometry objects [WPF], hit tests on visual objects [WPF]
ms.assetid: 6c8bdbf2-19e0-4fbb-bf89-c1252b2ebc61
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 32feb70a3b7a44a5a48f57fc2ecee912de4d39ef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-hit-test-using-geometry-as-a-parameter"></a>Postupy: Spuštění testu použitím geometrie jako parametru
Tento příklad ukazuje, jak chcete provést test přístupů na visual objekt pomocí <xref:System.Windows.Media.Geometry> jako stiskněte klávesu testovací parametr.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak nastavit přístupů testu pomocí <xref:System.Windows.Media.GeometryHitTestParameters> pro <xref:System.Windows.Media.VisualTreeHelper.HitTest%2A> metoda. <xref:System.Windows.Point> Hodnotu, která je předána `OnMouseDown` metoda se používá k vytvoření <xref:System.Windows.Media.Geometry> objektu, aby bylo možné rozšířit rozsah přístupů testu.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet10)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet10](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet10)]  
  
 <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> Vlastnost <xref:System.Windows.Media.GeometryHitTestResult> poskytuje informace o výsledky testu přístupů, které používá <xref:System.Windows.Media.Geometry> jako stiskněte klávesu testovací parametr. Následující obrázek znázorňuje vztah mezi geometry ověření pozice (modré kruhu) a vykreslené obsah cílového objektu visual (červený čtvereček).  
  
 ![Testování průchodu diagram IntersectionDetail použít v](../../../../docs/framework/wpf/graphics-multimedia/media/intersectiondetail01.png "IntersectionDetail01")  
Průnik mezi přístupů geometrie a cíle visual objekt testu  
  
 Následující příklad ukazuje, jak implementovat přístupů test zpětné volání při <xref:System.Windows.Media.Geometry> slouží jako parametr přístupů testu. `result` Parametr přetypovat <xref:System.Windows.Media.GeometryHitTestResult> Chcete-li načíst hodnotu <xref:System.Windows.Media.GeometryHitTestResult.IntersectionDetail%2A> vlastnost. Hodnota vlastnosti umožňuje zjistit, jestli <xref:System.Windows.Media.Geometry> přístupů testovací parametr je úplně nebo částečně obsažené v vykreslené obsah cílového počtu testu. V takovém případě ukázkový kód je jenom přidávání výsledky ověření pozice v seznamu vizuální prvky, které jsou zcela zahrnutá v rámci hranice cíl.  
  
 [!code-csharp[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HitTestingOverview/CSharp/GeometryHitTest.cs#hittestingoverviewsnippet11)]
 [!code-vb[HitTestingOverview#HitTestingOverviewSnippet11](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HitTestingOverview/visualbasic/geometryhittest.vb#hittestingoverviewsnippet11)]  
  
> [!NOTE]
>  <xref:System.Windows.Media.HitTestResult> Zpětného volání by neměl být volán při průniku podrobností <xref:System.Windows.Media.IntersectionDetail.Empty>.  
  
## <a name="see-also"></a>Viz také  
 [Ve Visual vrstvě testování průchodu](../../../../docs/framework/wpf/graphics-multimedia/hit-testing-in-the-visual-layer.md)  
 [Stiskněte tlačítko Test geometrie v zobrazení](../../../../docs/framework/wpf/graphics-multimedia/how-to-hit-test-geometry-in-a-visual.md)
