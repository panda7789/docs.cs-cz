---
title: "Postupy: Vzájemné zřetězení objektů BitmapSource"
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
- BitmapSource objects [WPF], chaining
- graphics [WPF], chaining BitmapSource objects
- chaining BitmapSource objects [WPF]
ms.assetid: 32d88853-395b-4855-9685-51a482a3b421
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d085e4e382727cc91aa82603d64d2f567afdd126
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-chain-bitmapsource-objects-together"></a>Postupy: Vzájemné zřetězení objektů BitmapSource
Tento příklad ukazuje, jak můžete použít různé efekty na zdroj bitové kopie s řetězení více <xref:System.Windows.Media.Imaging.BitmapSource> odvozené objekty společně.  
  
 Následující příklad používá řetězení překlopit a změnit Pixelový formát zdroje bitové kopie.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[ImagingSnippetGallery_snip#ChainedBitmapSourcesXamlExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_snip/CS/ChainedBitmapSourcesExample.xaml#chainedbitmapsourcesxamlexamplewholepage)]  
  
 [!code-csharp[ImagingSnippetGallery_procedural_snip#ChainedBitmapSourcesCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/CSharp/ChainedBitmapSourcesExample.cs#chainedbitmapsourcescodeexamplewholepage)]
 [!code-vb[ImagingSnippetGallery_procedural_snip#ChainedBitmapSourcesCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImagingSnippetGallery_procedural_snip/VB/ChainedBitmapSourcesExample.vb#chainedbitmapsourcescodeexamplewholepage)]
