---
title: 'Postupy: kódování a dekódování ve formátu JPEG'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- encoding image formats [WPF]
- decoding JPEG images [WPF]
- encoding JPEG images [WPF]
- decoding image formats [WPF]
- JPEG decoding [WPF]
- JPEG encoding [WPF]
ms.assetid: b8cfde37-9f68-4911-a05e-51d8d7bdec7b
ms.openlocfilehash: 916eab63938100daf91e6c1a5af31648a99108d0
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027964"
---
# <a name="how-to-encode-and-decode-a-jpeg-image"></a><span data-ttu-id="5470c-102">Postupy: kódování a dekódování ve formátu JPEG</span><span class="sxs-lookup"><span data-stu-id="5470c-102">How to: Encode and decode a JPEG image</span></span>

<span data-ttu-id="5470c-103">Následující příklady ukazují, jak pro dekódování a kódování ve formátu JPEG pomocí konkrétní <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> a <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> objekty.</span><span class="sxs-lookup"><span data-stu-id="5470c-103">The following examples show how to decode and encode a JPEG image using the specific <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> and <xref:System.Windows.Media.Imaging.JpegBitmapEncoder> objects.</span></span>  
  
## <a name="example---decode-a-jpeg-image"></a><span data-ttu-id="5470c-104">Příklad: dekódování ve formátu JPEG</span><span class="sxs-lookup"><span data-stu-id="5470c-104">Example - Decode a JPEG image</span></span>

<span data-ttu-id="5470c-105">Tento příklad ukazuje, jak k dekódování pomocí bitové kopie JPEG <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> z <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="5470c-105">This example demonstrates how to decode a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#1)]
[!code-csharp[JpegBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#1)]
[!code-vb[JpegBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#1)]  
  
## <a name="example---encode-a-jpeg-image"></a><span data-ttu-id="5470c-106">Příklad: kódování ve formátu JPEG</span><span class="sxs-lookup"><span data-stu-id="5470c-106">Example - Encode a JPEG image</span></span>

<span data-ttu-id="5470c-107">Tento příklad ukazuje, jak ke kódování <xref:System.Windows.Media.Imaging.BitmapSource> do JPEG bitovou kopii pomocí <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="5470c-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a JPEG image using a <xref:System.Windows.Media.Imaging.JpegBitmapEncoder>.</span></span>  
  
[!code-cpp[JpegBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CPP/jpegencoderdecoder.cpp#4)]
[!code-csharp[JpegBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/CSharp/JpegEncoderDecoder.cs#4)]
[!code-vb[JpegBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/JpegBitmapDecoderEncoder/VB/JpegEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="5470c-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5470c-108">See also</span></span>

[<span data-ttu-id="5470c-109">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="5470c-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)