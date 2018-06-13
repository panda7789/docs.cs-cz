---
title: 'Postupy: Kódování a dekódování obrázku WDP'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WDP encoding [WPF]
- WDP decoding [WPF]
- encoding image formats [WPF]
- decoding WDP images [WPF]
- decoding image formats [WPF]
- encoding WDP images [WPF]
ms.assetid: 911777d1-516b-49db-a87b-b54e31b18532
ms.openlocfilehash: d2da0daa389f30cd976f74f3451609defadf4942
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33560123"
---
# <a name="how-to-encode-and-decode-a-wdp-image"></a><span data-ttu-id="1d2dd-102">Postupy: Kódování a dekódování obrázku WDP</span><span class="sxs-lookup"><span data-stu-id="1d2dd-102">How to: Encode and Decode a WDP Image</span></span>
<span data-ttu-id="1d2dd-103">Následující příklady ukazují, jak kódování a dekódování [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)] bitovou kopii pomocí konkrétní <xref:System.Windows.Media.Imaging.WmpBitmapDecoder> a <xref:System.Windows.Media.Imaging.WmpBitmapEncoder> objekty.</span><span class="sxs-lookup"><span data-stu-id="1d2dd-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)] image using the specific <xref:System.Windows.Media.Imaging.WmpBitmapDecoder> and <xref:System.Windows.Media.Imaging.WmpBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1d2dd-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2dd-104">Example</span></span>  
 <span data-ttu-id="1d2dd-105">Tento příklad ukazuje, jak k dekódování [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)] bitovou kopii pomocí <xref:System.Windows.Media.Imaging.WmpBitmapDecoder> z <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="1d2dd-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)] image using a <xref:System.Windows.Media.Imaging.WmpBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[WdpBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CPP/WDPEncoderDecoder.cpp#1)]
 [!code-csharp[WdpBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CSharp/WDPEncoderDecoder.cs#1)]
 [!code-vb[WdpBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/VB/WDPEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="1d2dd-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="1d2dd-106">Example</span></span>  
 <span data-ttu-id="1d2dd-107">Tento příklad ukazuje, jak ke kódování <xref:System.Windows.Media.Imaging.BitmapSource> do [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)] bitovou kopii pomocí <xref:System.Windows.Media.Imaging.WmpBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="1d2dd-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)] image using a <xref:System.Windows.Media.Imaging.WmpBitmapEncoder>.</span></span>  
  
 [!code-cpp[WdpBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CPP/WDPEncoderDecoder.cpp#4)]
 [!code-csharp[WdpBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CSharp/WDPEncoderDecoder.cs#4)]
 [!code-vb[WdpBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/VB/WDPEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="1d2dd-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="1d2dd-108">See Also</span></span>  
 [<span data-ttu-id="1d2dd-109">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="1d2dd-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
