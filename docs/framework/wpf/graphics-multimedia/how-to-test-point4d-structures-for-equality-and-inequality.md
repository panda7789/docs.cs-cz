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
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a><span data-ttu-id="bb040-102">Postupy: Testování struktur Point4D na rovnost a nerovnost</span><span class="sxs-lookup"><span data-stu-id="bb040-102">How to: Test Point4D structures for equality and inequality</span></span>
<span data-ttu-id="bb040-103">Tento příklad ukazuje postup testování <xref:System.Windows.Media.Media3D.Point4D> struktury rovnosti a nerovnosti.</span><span class="sxs-lookup"><span data-stu-id="bb040-103">This example shows how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality.</span></span>  
  
 <span data-ttu-id="bb040-104">Následující kód ukazuje, jak otestovat <xref:System.Windows.Media.Media3D.Point4D> struktury rovnosti a nerovnosti pomocí <xref:System.Windows.Media.Media3D.Point4D> metody rovnosti.</span><span class="sxs-lookup"><span data-stu-id="bb040-104">The following code illustrates how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality using the <xref:System.Windows.Media.Media3D.Point4D> equality methods.</span></span>  <span data-ttu-id="bb040-105"><xref:System.Windows.Media.Media3D.Point4D> Struktury jsou testovány rovnosti pomocí přetížené rovnosti (`==`) operátor pak nerovnost pomocí přetížené nerovnosti (`!=`) operátor a nakonec <xref:System.Windows.Media.Media3D.Point3D> struktura a <xref:System.Windows.Media.Media3D.Point4D> struktura jsou zaškrtnutá políčka rovnosti pomocí statické <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="bb040-105">The <xref:System.Windows.Media.Media3D.Point4D> structures are tested for equality using the overloaded equality (`==`) operator, then for inequality using the overloaded inequality (`!=`) operator, and finally a <xref:System.Windows.Media.Media3D.Point3D> structure and a <xref:System.Windows.Media.Media3D.Point4D> structure are checked for equality using the static <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb040-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="bb040-106">Example</span></span>  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a><span data-ttu-id="bb040-107">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb040-107">See Also</span></span>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>  
 <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
