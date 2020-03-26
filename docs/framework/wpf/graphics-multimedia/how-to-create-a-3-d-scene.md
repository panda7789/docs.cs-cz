---
title: 'Postup: Vytvoření 3D scény'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- scenes [WPF], 3D
- 3D scenes
ms.assetid: adb4a598-71a2-4dd5-b677-ea3fc11b78b2
ms.openlocfilehash: 36453894e06e7b59f339c21713449140c17f6851
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112099"
---
# <a name="how-to-create-a-3d-scene"></a>Postup: Vytvoření 3D scény
Tento příklad ukazuje, jak vytvořit 3D objekt, který vypadá jako plochý list papíru, který byl otočen. A <xref:System.Windows.Controls.Viewport3D> spolu s následujícími součástmi se používají k vytvoření této jednoduché 3D scény:  
  
- Kamera je vytvořena <xref:System.Windows.Media.Media3D.PerspectiveCamera>pomocí . Kamera určuje, která část 3D scény je zobrazitelná.  
  
- Síť je vytvořena pro určení tvaru 3D objektu (listu <xref:System.Windows.Media.Media3D.GeometryModel3D>papíru) pomocí vlastnosti <xref:System.Windows.Media.Media3D.GeometryModel3D.Geometry%2A> .  
  
- Materiál je určen k zobrazení na povrchu objektu (lineární gradient <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> v <xref:System.Windows.Media.Media3D.GeometryModel3D>tomto vzorku) pomocí vlastnosti .  
  
- Světlo je vytvořeno tak, aby <xref:System.Windows.Media.Media3D.DirectionalLight>svítilo na objekt pomocí .  
  
## <a name="example"></a>Příklad  
 Níže uvedený kód ukazuje, jak vytvořit 3D scénu v XAML.  
  
 [!code-xaml[3DGallery_snip#Basic3DShapeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/Basic3DShapeExample.xaml#basic3dshapeexamplewholepage)]  
  
## <a name="example"></a>Příklad  
 Níže uvedený kód ukazuje, jak vytvořit stejnou 3D scénu v procedurálním kódu.  
  
 [!code-csharp[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Basic3DShapeExample.cs#basic3dshapecodeexamplewholepage)]
 [!code-vb[3DGallery_procedural_snip#Basic3DShapeCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/3DGallery_procedural_snip/visualbasic/basic3dshapeexample.vb#basic3dshapecodeexamplewholepage)]  
  
## <a name="see-also"></a>Viz také

- [Přehled 3D grafiky](3-d-graphics-overview.md)
