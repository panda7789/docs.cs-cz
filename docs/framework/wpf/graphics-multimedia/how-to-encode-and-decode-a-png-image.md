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
ms.openlocfilehash: 0a0a2f2625901f7ee32ba9fe70e71681a1b9ccd3
ms.sourcegitcommit: 43761fcee10aeefcf851ea81cea3f3c691420856
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/16/2019
ms.locfileid: "69545284"
---
# <a name="how-to-encode-and-decode-a-png-image"></a><span data-ttu-id="5182e-102">Postupy: Kódování a dekódování obrázku PNG</span><span class="sxs-lookup"><span data-stu-id="5182e-102">How to: Encode and Decode a PNG Image</span></span>
<span data-ttu-id="5182e-103">Následující příklady ukazují, jak dekódovat a kódovat obrázek png (Portable Network Graphics) pomocí konkrétních <xref:System.Windows.Media.Imaging.PngBitmapDecoder> objektů a. <xref:System.Windows.Media.Imaging.PngBitmapEncoder></span><span class="sxs-lookup"><span data-stu-id="5182e-103">The following examples show how to decode and encode a Portable Network Graphics (PNG) image using the specific <xref:System.Windows.Media.Imaging.PngBitmapDecoder> and <xref:System.Windows.Media.Imaging.PngBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5182e-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5182e-104">Example</span></span>  
 <span data-ttu-id="5182e-105">Tento příklad ukazuje, jak dekódovat obrázek png pomocí <xref:System.Windows.Media.Imaging.PngBitmapDecoder> <xref:System.IO.FileStream>z.</span><span class="sxs-lookup"><span data-stu-id="5182e-105">This example demonstrates how to decode a PNG image using a <xref:System.Windows.Media.Imaging.PngBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#1)]
 [!code-csharp[PngBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#1)]
 [!code-vb[PngBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="5182e-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5182e-106">Example</span></span>  
 <span data-ttu-id="5182e-107">Tento příklad ukazuje, jak zakódovat <xref:System.Windows.Media.Imaging.BitmapSource> do obrázku PNG <xref:System.Windows.Media.Imaging.PngBitmapEncoder>pomocí.</span><span class="sxs-lookup"><span data-stu-id="5182e-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a PNG image using a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#4)]
 [!code-csharp[PngBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#4)]
 [!code-vb[PngBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5182e-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5182e-108">See also</span></span>

- [<span data-ttu-id="5182e-109">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="5182e-109">Imaging Overview</span></span>](imaging-overview.md)
