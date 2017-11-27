---
title: "Postupy: Kódování a dekódování obrázku WDP"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 8b97f730da7e2a305ad26b56a6ccdc14851355b5
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-encode-and-decode-a-wdp-image"></a><span data-ttu-id="7c6d2-102">Postupy: Kódování a dekódování obrázku WDP</span><span class="sxs-lookup"><span data-stu-id="7c6d2-102">How to: Encode and Decode a WDP Image</span></span>
<span data-ttu-id="7c6d2-103">Následující příklady ukazují, jak kódování a dekódování [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)] bitovou kopii pomocí konkrétní <xref:System.Windows.Media.Imaging.WmpBitmapDecoder> a <xref:System.Windows.Media.Imaging.WmpBitmapEncoder> objekty.</span><span class="sxs-lookup"><span data-stu-id="7c6d2-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_wdp](../../../../includes/tlasharptla-wdp-md.md)] image using the specific <xref:System.Windows.Media.Imaging.WmpBitmapDecoder> and <xref:System.Windows.Media.Imaging.WmpBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7c6d2-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c6d2-104">Example</span></span>  
 <span data-ttu-id="7c6d2-105">Tento příklad ukazuje, jak k dekódování [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)] bitovou kopii pomocí <xref:System.Windows.Media.Imaging.WmpBitmapDecoder> z <xref:System.Uri>.</span><span class="sxs-lookup"><span data-stu-id="7c6d2-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)] image using a <xref:System.Windows.Media.Imaging.WmpBitmapDecoder> from a <xref:System.Uri>.</span></span>  
  
 [!code-cpp[WdpBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CPP/WDPEncoderDecoder.cpp#1)]
 [!code-csharp[WdpBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CSharp/WDPEncoderDecoder.cs#1)]
 [!code-vb[WdpBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/VB/WDPEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="7c6d2-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="7c6d2-106">Example</span></span>  
 <span data-ttu-id="7c6d2-107">Tento příklad ukazuje, jak ke kódování <xref:System.Windows.Media.Imaging.BitmapSource> do [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)] bitovou kopii pomocí <xref:System.Windows.Media.Imaging.WmpBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="7c6d2-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_wdp](../../../../includes/tla2sharptla-wdp-md.md)] image using a <xref:System.Windows.Media.Imaging.WmpBitmapEncoder>.</span></span>  
  
 [!code-cpp[WdpBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CPP/WDPEncoderDecoder.cpp#4)]
 [!code-csharp[WdpBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/CSharp/WDPEncoderDecoder.cs#4)]
 [!code-vb[WdpBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WdpBitmapDecoderEncoder/VB/WDPEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="7c6d2-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="7c6d2-108">See Also</span></span>  
 [<span data-ttu-id="7c6d2-109">Přehled vytvoření bitové kopie</span><span class="sxs-lookup"><span data-stu-id="7c6d2-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
