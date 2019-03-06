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
ms.openlocfilehash: 132ccc2fca4b1b3984c88f1e75d3fd1934d8bf24
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358090"
---
# <a name="how-to-encode-and-decode-a-png-image"></a><span data-ttu-id="a0389-102">Postupy: Kódování a dekódování obrázku PNG</span><span class="sxs-lookup"><span data-stu-id="a0389-102">How to: Encode and Decode a PNG Image</span></span>
<span data-ttu-id="a0389-103">Následující příklady ukazují, jak kódovat a dekódovat [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] image pomocí konkrétní <xref:System.Windows.Media.Imaging.PngBitmapDecoder> a <xref:System.Windows.Media.Imaging.PngBitmapEncoder> objekty.</span><span class="sxs-lookup"><span data-stu-id="a0389-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_png](../../../../includes/tlasharptla-png-md.md)] image using the specific <xref:System.Windows.Media.Imaging.PngBitmapDecoder> and <xref:System.Windows.Media.Imaging.PngBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0389-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0389-104">Example</span></span>  
 <span data-ttu-id="a0389-105">Tento příklad ukazuje, jak se dekódovat [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image pomocí <xref:System.Windows.Media.Imaging.PngBitmapDecoder> z <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="a0389-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image using a <xref:System.Windows.Media.Imaging.PngBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#1](~/samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#1)]
 [!code-csharp[PngBitmapDecoderEncoder#1](~/samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#1)]
 [!code-vb[PngBitmapDecoderEncoder#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="a0389-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="a0389-106">Example</span></span>  
 <span data-ttu-id="a0389-107">Tento příklad ukazuje, jak kódovat <xref:System.Windows.Media.Imaging.BitmapSource> do [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image pomocí <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="a0389-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_png](../../../../includes/tla2sharptla-png-md.md)] image using a <xref:System.Windows.Media.Imaging.PngBitmapEncoder>.</span></span>  
  
 [!code-cpp[PngBitmapDecoderEncoder#4](~/samples/snippets/cpp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CPP/PngEncoderDecoder.cpp#4)]
 [!code-csharp[PngBitmapDecoderEncoder#4](~/samples/snippets/csharp/VS_Snippets_Wpf/PngBitmapDecoderEncoder/CSharp/PngEncoderDecoder.cs#4)]
 [!code-vb[PngBitmapDecoderEncoder#4](~/samples/snippets/visualbasic/VS_Snippets_Wpf/PngBitmapDecoderEncoder/VB/PngEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="a0389-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0389-108">See also</span></span>
- [<span data-ttu-id="a0389-109">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="a0389-109">Imaging Overview</span></span>](imaging-overview.md)
