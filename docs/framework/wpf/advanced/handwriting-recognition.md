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
ms.openlocfilehash: d72d8b42a23205d8599b23a467677dd2f05d5cbc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542373"
---
# <a name="handwriting-recognition"></a>Rozpoznávání textu psaného rukou
Tato část popisuje základní informace o rozpoznávání, jak se vztahuje k digitální rukopisu v platformě WPF.  
  
## <a name="recognition-solutions"></a>Rozpoznávání řešení  
 Následující příklad ukazuje, jak rozpoznávat rukopisu pomocí [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) třídy.  
  
> [!NOTE]
>  Tato ukázka vyžaduje nainstalované nástroje pro rozpoznávání rukopisu v systému.  
  
 Vytvořte nový projekt aplikace WPF v sadě Visual Studio názvem **InkRecognition**. Nahraďte obsah souboru Window1.xaml následující kód XAML. Tento kód vykreslí uživatelské rozhraní aplikace.  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 Přidáte odkaz na sestavení Microsoft inkoustu, Microsoft.Ink.dll, které lze nalézt v \Program Files\Common Files\Microsoft Shared\Ink. Obsah souboru kódu nahraďte následujícím kódem.  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a>Viz také  
 [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)
