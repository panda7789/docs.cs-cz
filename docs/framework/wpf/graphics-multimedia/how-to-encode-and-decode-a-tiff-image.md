---
title: 'Postupy: Kódování a dekódování obrázku TIFF'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TIFF encoding [WPF]
- encoding TIFF images [WPF]
- encoding image formats [WPF]
- decoding TIFF images [WPF]
- decoding image formats [WPF]
- TIFF decoding [WPF]
ms.assetid: 1dfe3209-fc73-40e6-ad1c-71c1c58b3364
ms.openlocfilehash: 0b1d5f19583e0a0014903ef6ace01bc164b70d0b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54696162"
---
# <a name="how-to-encode-and-decode-a-tiff-image"></a><span data-ttu-id="febea-102">Postupy: Kódování a dekódování obrázku TIFF</span><span class="sxs-lookup"><span data-stu-id="febea-102">How to: Encode and Decode a TIFF Image</span></span>
<span data-ttu-id="febea-103">Následující příklady ukazují, jak kódovat a dekódovat [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] image pomocí konkrétní <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> a <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> objekty.</span><span class="sxs-lookup"><span data-stu-id="febea-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_tiff](../../../../includes/tlasharptla-tiff-md.md)] image using the specific <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> and <xref:System.Windows.Media.Imaging.TiffBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="febea-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="febea-104">Example</span></span>  
 <span data-ttu-id="febea-105">Tento příklad ukazuje, jak se dekódovat [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image pomocí <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> z <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="febea-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image using a <xref:System.Windows.Media.Imaging.TiffBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#1)]
 [!code-csharp[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#1)]
 [!code-vb[TiffBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="febea-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="febea-106">Example</span></span>  
 <span data-ttu-id="febea-107">Tento příklad ukazuje, jak kódovat <xref:System.Windows.Media.Imaging.BitmapSource> do [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image pomocí <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="febea-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_tiff](../../../../includes/tla2sharptla-tiff-md.md)] image using a <xref:System.Windows.Media.Imaging.TiffBitmapEncoder>.</span></span>  
  
 [!code-cpp[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CPP/TiffEncoderDecoder.cpp#4)]
 [!code-csharp[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/CSharp/TiffEncoderDecoder.cs#4)]
 [!code-vb[TiffBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TiffBitmapDecoderEncoder/VB/TiffEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="febea-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="febea-108">See also</span></span>
- [<span data-ttu-id="febea-109">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="febea-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
