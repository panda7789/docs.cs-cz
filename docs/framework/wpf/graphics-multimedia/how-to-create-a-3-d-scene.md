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
ms.openlocfilehash: a431b78993d197dac99f0b6e365823acb295f0b8
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64611637"
---
# <a name="how-to-create-a-3-d-scene"></a>Postupy: Vytvoření 3D scény
Tento příklad ukazuje postup vytvoření 3D objekt, který vypadá jako seznam bez stromové struktury papíru, které byly otočen. A <xref:System.Windows.Controls.Viewport3D> spolu s následující součásti, které se používají k vytvoření tohoto jednoduchého 3D scény:  
  
- Fotoaparát je vytvořený pomocí <xref:System.Windows.Media.Media3D.PerspectiveCamera>. Fotoaparátu/kamery Určuje, jaká část 3D Scéna je zobrazit.  
  
- Vytvoření sítě určit tvar 3D objekt (list papíru) pomocí <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
- Je zadán materiál zobrazený na povrchu objektu (lineárního přechodu v této ukázce) pomocí <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
- Světla vytvářen do září na objekt pomocí <xref:System.Windows.Media.Media3D.DirectionalLight>.  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje postup vytvoření 3D scény v XAML.  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje, jak vytvořit stejnou 3D scénu v kódu procedury.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:

- [Přehled 3D grafiky](3-d-graphics-overview.md)
