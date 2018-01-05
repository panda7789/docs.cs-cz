---
title: "Postupy: Kódování a dekódování obrázku GIF"
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
- encoding GIF images [WPF]
- encoding image formats [WPF]
- decoding GIF images [WPF]
- decoding image formats [WPF]
- GIF decoding [WPF]
- GIF encoding [WPF]
ms.assetid: 9cdd9ec7-71eb-444b-b9e3-991958461163
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 9d098faf45edade4a37a4d8a6004d1e7b8acbd86
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-encode-and-decode-a-gif-image"></a><span data-ttu-id="180b0-102">Postupy: Kódování a dekódování obrázku GIF</span><span class="sxs-lookup"><span data-stu-id="180b0-102">How to: Encode and Decode a GIF Image</span></span>
<span data-ttu-id="180b0-103">Následující příklady ukazují, jak kódování a dekódování [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] bitovou kopii pomocí konkrétní <xref:System.Windows.Media.Imaging.GifBitmapDecoder> a <xref:System.Windows.Media.Imaging.GifBitmapEncoder> objekty.</span><span class="sxs-lookup"><span data-stu-id="180b0-103">The following examples show how to decode and encode a [!INCLUDE[TLA#tla_gif](../../../../includes/tlasharptla-gif-md.md)] image using the specific <xref:System.Windows.Media.Imaging.GifBitmapDecoder> and <xref:System.Windows.Media.Imaging.GifBitmapEncoder> objects.</span></span>  
  
## <a name="example"></a><span data-ttu-id="180b0-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="180b0-104">Example</span></span>  
 <span data-ttu-id="180b0-105">Tento příklad ukazuje, jak k dekódování [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] bitovou kopii pomocí <xref:System.Windows.Media.Imaging.GifBitmapDecoder> z <xref:System.IO.FileStream>.</span><span class="sxs-lookup"><span data-stu-id="180b0-105">This example demonstrates how to decode a [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] image using a <xref:System.Windows.Media.Imaging.GifBitmapDecoder> from a <xref:System.IO.FileStream>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#1)]
 [!code-csharp[GifBitmapDecoderEncoder#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#1)]
 [!code-vb[GifBitmapDecoderEncoder#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#1)]  
  
## <a name="example"></a><span data-ttu-id="180b0-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="180b0-106">Example</span></span>  
 <span data-ttu-id="180b0-107">Tento příklad ukazuje, jak ke kódování <xref:System.Windows.Media.Imaging.BitmapSource> do [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] bitovou kopii pomocí <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span><span class="sxs-lookup"><span data-stu-id="180b0-107">This example demonstrates how to encode a <xref:System.Windows.Media.Imaging.BitmapSource> into a [!INCLUDE[TLA2#tla_gif](../../../../includes/tla2sharptla-gif-md.md)] image using a <xref:System.Windows.Media.Imaging.GifBitmapEncoder>.</span></span>  
  
 [!code-cpp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/cpp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CPP/GifEncoderDecoder.cpp#4)]
 [!code-csharp[GifBitmapDecoderEncoder#4](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GifBitmapDecoderEncoder/CSharp/GifEncoderDecoder.cs#4)]
 [!code-vb[GifBitmapDecoderEncoder#4](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/GifBitmapDecoderEncoder/VB/GifEncoderDecoder.vb#4)]  
  
## <a name="see-also"></a><span data-ttu-id="180b0-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="180b0-108">See Also</span></span>  
 [<span data-ttu-id="180b0-109">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="180b0-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
