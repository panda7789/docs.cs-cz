---
title: "Postupy: Převod BitmapSource do jiného formátu PixelFormat"
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
helpviewer_keywords:
- BitmapSource objects [WPF], converting to indexed pixel format
- converting images [WPF]
- converting [WPF], BitmapSource objects to indexed pixel formats
- converting [WPF], BitmapSource objects to palettized pixel format
- BitmapSource objects [WPF], converting to palettized pixel format
ms.assetid: cd9df1e4-d5dc-4f57-b67b-4ec67e086b33
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 606499a57dbad3c812b57b4a3d598218c0565742
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-convert-a-bitmapsource-to-a-different-pixelformat"></a>Postupy: Převod BitmapSource do jiného formátu PixelFormat
Tento příklad ukazuje, jak převést <xref:System.Windows.Media.Imaging.BitmapSource> objektu (<xref:System.Windows.Media.Imaging.BitmapImage>) na jiný <xref:System.Windows.Media.PixelFormat> pomocí <xref:System.Windows.Media.Imaging.FormatConvertedBitmap>.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#PixelFormatConversion](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/PixelFormatsExample.cs#pixelformatconversion)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#PixelFormatConversion](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/PixelFormatsExample.vb#pixelformatconversion)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled obrázků](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
