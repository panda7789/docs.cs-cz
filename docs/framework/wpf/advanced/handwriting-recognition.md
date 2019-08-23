---
title: Rozpoznávání textu psaného rukou
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- handwriting recognition [WPF]
- recognition of handwriting [WPF]
ms.assetid: f4e8576d-e731-4bac-9818-22e2ae636636
ms.openlocfilehash: d6c09f063b6bd0eef2cb9f6bb444eac980ad4832
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956534"
---
# <a name="handwriting-recognition"></a>Rozpoznávání textu psaného rukou
Tato část popisuje základy rozpoznávání, protože se týkají digitálního inkoustu v platformě WPF.  
  
## <a name="recognition-solutions"></a>Řešení pro rozpoznávání  
 Následující příklad ukazuje, jak rozpoznat rukopis pomocí třídy [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) .  
  
> [!NOTE]
> Tato ukázka vyžaduje, aby byly v systému nainstalovány nástroje pro rozpoznávání rukopisu.  
  
 Vytvořte nový projekt aplikace WPF v aplikaci Visual Studio s názvem **InkRecognition**. Obsah souboru Window1. xaml nahraďte následujícím kódem XAML. Tento kód vykreslí uživatelské rozhraní aplikace.  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 Přidat odkaz na sestavení Microsoft Ink, Microsoft. Ink. dll, které najdete v \Program Files\Common Files\Microsoft Shared\Ink. Obsah souboru kódu na pozadí nahraďte následujícím kódem.  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))
