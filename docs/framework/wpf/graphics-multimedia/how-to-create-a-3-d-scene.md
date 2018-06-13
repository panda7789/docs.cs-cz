---
title: 'Postupy: Vytvoření 3D scény'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3-D
- 3-D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: e3c2ea803961ca57606f8ea8bec21d50a38dbe1f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33559523"
---
# <a name="how-to-create-a-3-d-scene"></a>Postupy: Vytvoření 3D scény
Tento příklad ukazuje postup vytvoření 3D objekt, který vypadá jako plochý list dokumentu, který otočený. A <xref:System.Windows.Controls.Viewport3D> společně s následující součásti, které se používají k vytvoření tohoto jednoduchého 3D scény:  
  
-   Fotoaparátu je vytvořený pomocí <xref:System.Windows.Media.Media3D.PerspectiveCamera>. Kamera Určuje, jaká část 3D scény jsou viditelná.  
  
-   Vytvoření mřížku k určení obrazec 3D objekt (list papíru) pomocí <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
-   Materiálu, který je zadán zobrazený na povrchu objekt (lineárního přechodu v této ukázce) pomocí <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
-   Lehkým se vytvoří pro září na objekt pomocí <xref:System.Windows.Media.Media3D.DirectionalLight>.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak vytvořit 3D scény v jazyce XAML.  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak vytvořit stejné 3D scény v procedurální kódu.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
