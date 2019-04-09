---
title: 'Postupy: Testování struktur Point4D na rovnost a nerovnost'
ms.date: 03/30/2017
helpviewer_keywords:
- inequality [WPF], testing Point4D structures for
- equality [WPF], testing Point4D structures for
- testing [WPF], Point4D structures for equality
- Point4D structures [WPF], testing for inequality
- testing [WPF], Point4D structures for inequality
- Point4D structures [WPF], testing for equality
ms.assetid: e004a67e-db7f-4af8-a31f-e6b2a44ccf34
ms.openlocfilehash: ce1188e99ef2b0682427cc2e227aaccd27f7c4f4
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59198436"
---
# <a name="how-to-test-point4d-structures-for-equality-and-inequality"></a><span data-ttu-id="278f2-102">Postupy: Testování struktur Point4D na rovnost a nerovnost</span><span class="sxs-lookup"><span data-stu-id="278f2-102">How to: Test Point4D structures for equality and inequality</span></span>
<span data-ttu-id="278f2-103">Tento příklad ukazuje, jak otestovat <xref:System.Windows.Media.Media3D.Point4D> struktury rovnost a nerovnost.</span><span class="sxs-lookup"><span data-stu-id="278f2-103">This example shows how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality.</span></span>  
  
 <span data-ttu-id="278f2-104">Následující kód ukazuje, jak otestovat <xref:System.Windows.Media.Media3D.Point4D> struktur rovnost a nerovnost pomocí <xref:System.Windows.Media.Media3D.Point4D> rovnosti metody.</span><span class="sxs-lookup"><span data-stu-id="278f2-104">The following code illustrates how to test <xref:System.Windows.Media.Media3D.Point4D> structures for equality and inequality using the <xref:System.Windows.Media.Media3D.Point4D> equality methods.</span></span>  <span data-ttu-id="278f2-105"><xref:System.Windows.Media.Media3D.Point4D> Struktury jsou testovány z hlediska rovnosti pomocí přetížených rovnosti (`==`) operátor, pak pro nerovnost pomocí přetížených nerovnosti (`!=`) operátor a nakonec <xref:System.Windows.Media.Media3D.Point3D> strukturu a <xref:System.Windows.Media.Media3D.Point4D> Struktura nebyly zvoleny na rovnost pomocí statické <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="278f2-105">The <xref:System.Windows.Media.Media3D.Point4D> structures are tested for equality using the overloaded equality (`==`) operator, then for inequality using the overloaded inequality (`!=`) operator, and finally a <xref:System.Windows.Media.Media3D.Point3D> structure and a <xref:System.Windows.Media.Media3D.Point4D> structure are checked for equality using the static <xref:System.Windows.Media.Media3D.Point4D.Equals%2A> method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="278f2-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="278f2-106">Example</span></span>  
 [!code-csharp[3DGallery_procedural_snip#Point4DEqualityExample_csharp](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_procedural_snip/CSharp/Misc3DOperationsExample.cs#point4dequalityexample_csharp)]  
  
## <a name="see-also"></a><span data-ttu-id="278f2-107">Viz také:</span><span class="sxs-lookup"><span data-stu-id="278f2-107">See also</span></span>

- <xref:System.Windows.Media.Media3D.Point4D.op_Equality%2A>
- <xref:System.Windows.Media.Media3D.Point4D.op_Inequality%2A>
- <xref:System.Windows.Media.Media3D.Point4D.Equals%2A>
