---
title: 'Postupy: Kódování a dekódování obrázku BMP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding BMP images [WPF]
- BMP encoding [WPF]
- decoding BMP images [WPF]
- encoding image formats [WPF]
- BMP decoding [WPF]
- decoding image formats [WPF]
ms.assetid: feb5ef27-28ac-40ab-bfc2-e0456990d32c
ms.openlocfilehash: 7d3520a1b1913fe68fedb0ea9d76cc138ed661c4
ms.sourcegitcommit: 09d699aca28ae9723399bbd9d3d44aa0cbd3848d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/19/2019
ms.locfileid: "68331727"
---
# <a name="how-to-encode-and-decode-a-bmp-image"></a><span data-ttu-id="3cd31-102">Postupy: Kódování a dekódování obrázku BMP</span><span class="sxs-lookup"><span data-stu-id="3cd31-102">How to: Encode and Decode a BMP Image</span></span>
<span data-ttu-id="3cd31-103">Následující příklady znázorňují, jak dekódovat a kódovat rastrovou obrázek (BMP) pomocí konkrétních <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> objektů <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> a.</span><span class="sxs-lookup"><span data-stu-id="3cd31-103">The following examples show how to decode and encode a bitmap (BMP) image using the specific <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> and <xref:System.Windows.Media.Imaging.BmpBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3cd31-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="3cd31-104">Example</span></span>  
 <span data-ttu-id="3cd31-105">Tento příklad ukazuje, jak dekódovat obrázek bmp pomocí typu <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> <xref:System.Uri>z.</span><span class="sxs-lookup"><span data-stu-id="3cd31-105">This example demonstrates how to decode a BMP image using a <xref:System.Windows.Media.Imaging.BmpBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[BmpBitmapDecoderEncoder#5](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#5)]
 [!code-csharp[BmpBitmapDecoderEncoder#5](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#5)]
 [!code-vb[BmpBitmapDecoderEncoder#5](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#5)]  
  
## <a name="example"></a><span data-ttu-id="3cd31-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="3cd31-106">Example</span></span>  
 <span data-ttu-id="3cd31-107">Tento příklad ukazuje, jak zakódovat <xref:System.Windows.Media.Imaging.BitmapSource> do obrázku BMP <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>pomocí.</span><span class="sxs-lookup"><span data-stu-id="3cd31-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a BMP image using a <xref:System.Windows.Media.Imaging.BmpBitmapEncoder>.</span></span>  
  
 [!code-cpp[BmpBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CPP/anotherfile.cpp#4)]
 [!code-csharp[BmpBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/CSharp/BitmapFrame.cs#4)]
 [!code-vb[BmpBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/BmpBitmapDecoderEncoder/VB/BitmapFrame.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="3cd31-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3cd31-108">See also</span></span>

- [<span data-ttu-id="3cd31-109">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="3cd31-109">Imaging Overview</span></span>](imaging-overview.md)
