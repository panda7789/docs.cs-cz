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
ms.openlocfilehash: 8f520b80970bfeebdfea01a6c722634efd99ffe7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725386"
---
# <a name="handwriting-recognition"></a>Rozpoznávání textu psaného rukou
Tato část popisuje základní informace o rozpoznávání, protože se týkají digitálních inkoust v platformě WPF.  
  
## <a name="recognition-solutions"></a>Rozpoznávání řešení  
 Následující příklad ukazuje, jak rozpoznávání rukopisu pomocí [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) třídy.  
  
> [!NOTE]
>  Tato ukázka vyžaduje nainstalované nástroje pro rozpoznávání rukopisu v systému.  
  
 Vytvoření nového projektu aplikace WPF v sadě Visual Studio volá **InkRecognition**. Nahraďte obsah souboru Window1.xaml následující kód XAML. Tento kód vykreslí uživatelské rozhraní vaší aplikace.  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 Přidáte odkaz na sestavení Microsoft Ink, Microsoft.Ink.dll, který se nachází v \Program Files\Microsoft Shared\Ink. Nahraďte obsah souboru kódu na pozadí s následujícím kódem.  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také:
- [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)
