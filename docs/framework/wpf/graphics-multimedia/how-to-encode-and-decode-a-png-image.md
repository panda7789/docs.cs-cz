---
title: 'Postupy: Kódování a dekódování obrázku PNG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- PNG encoding [WPF]
- decoding PNG images [WPF]
- PNG decoding [WPF]
- encoding image formats [WPF]
- decoding image formats [WPF]
- encoding PNG images [WPF]
ms.assetid: 3d31d186-af73-47f0-b5a7-c26ae46409a6
ms.openlocfilehash: a22b0eae323c12f99ad5447eb27423bc0e5f9277
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33558828"
---
# <a name="how-to-encode-and-decode-a-png-image"></a><span data-ttu-id="e5161-102">Postupy: Kódování a dekódování obrázku PNG</span><span class="sxs-lookup"><span data-stu-id="e5161-102">How to: Encode and Decode a PNG Image</span></span>
<span data-ttu-id="e5161-103">Následující příklady ukazují, jak kódování a dekódování [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] bitovou kopii pomocí konkrétní <xref:System.Windows.Media.Imaging.PngBitmapDecoder> a <xref:System.Windows.Media.Imaging.PngBitmapEncoder> objekty.</span><span class="sxs-lookup"><span data-stu-id="e5161-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] image using the specific <xref:System.Windows.Media.Imaging.PngBitmapDecoder> and <xref:System.Windows.Media.Imaging.PngBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5161-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5161-104">Example</span></span>  
 <span data-ttu-id="e5161-105">Tento příklad ukazuje, jak k dekódování [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] bitovou kopii pomocí <xref:System.Windows.Media.Imaging.PngBitmapDecoder> z <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="e5161-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image using a <xref:System.Windows.Media.Imaging.PngBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#1)]
 [!code-csharp[PngBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#1)]
 [!code-vb[PngBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="e5161-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="e5161-106">Example</span></span>  
 <span data-ttu-id="e5161-107">Tento příklad ukazuje, jak ke kódování <xref:System.Windows.Media.Imaging.BitmapSource> do [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] bitovou kopii pomocí <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="e5161-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image using a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#4)]
 [!code-csharp[PngBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#4)]
 [!code-vb[PngBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="e5161-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="e5161-108">See Also</span></span>  
 [<span data-ttu-id="e5161-109">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="e5161-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
