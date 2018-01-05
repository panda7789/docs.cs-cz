---
title: "Postupy: Testování struktur Point4D na rovnost a nerovnost"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- inequality [WPF], testing Point4D structures for
- equality [WPF], testing Point4D structures for
- testing [WPF], Point4D structures for equality
- Point4D structures [WPF], testing for inequality
- testing [WPF], Point4D structures for inequality
- Point4D structures [WPF], testing for equality
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ac69ec232485ebd3097f2db3b31d3fd43d0ccc99
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a>Postupy: Testování struktur Point4D na rovnost a nerovnost
Tento příklad ukazuje postup testování <xref:System.Windows.Media.Media3D.Point4D> struktury rovnosti a nerovnosti.  
  
 Následující kód ukazuje, jak otestovat <xref:System.Windows.Media.Media3D.Point4D> struktury rovnosti a nerovnosti pomocí <xref:System.Windows.Media.Media3D.Point4D> metody rovnosti.  <xref:System.Windows.Media.Media3D.Point4D> Struktury jsou testovány rovnosti pomocí přetížené rovnosti (`==`) operátor pak nerovnost pomocí přetížené nerovnosti (`!=`) operátor a nakonec <xref:System.Windows.Media.Media3D.Point3D> struktura a <xref:System.Windows.Media.Media3D.Point4D> struktura jsou zaškrtnutá políčka rovnosti pomocí statické <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> metoda.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
