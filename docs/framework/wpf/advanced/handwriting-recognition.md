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
# <a name="handwriting-recognition"></a><span data-ttu-id="f63e6-102">Rozpoznávání textu psaného rukou</span><span class="sxs-lookup"><span data-stu-id="f63e6-102">Handwriting Recognition</span></span>
<span data-ttu-id="f63e6-103">Tato část popisuje základní informace o rozpoznávání, protože se týkají digitálních inkoust v platformě WPF.</span><span class="sxs-lookup"><span data-stu-id="f63e6-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="f63e6-104">Rozpoznávání řešení</span><span class="sxs-lookup"><span data-stu-id="f63e6-104">Recognition Solutions</span></span>  
 <span data-ttu-id="f63e6-105">Následující příklad ukazuje, jak rozpoznávání rukopisu pomocí [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) třídy.</span><span class="sxs-lookup"><span data-stu-id="f63e6-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx) class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f63e6-106">Tato ukázka vyžaduje nainstalované nástroje pro rozpoznávání rukopisu v systému.</span><span class="sxs-lookup"><span data-stu-id="f63e6-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="f63e6-107">Vytvoření nového projektu aplikace WPF v sadě Visual Studio volá **InkRecognition**.</span><span class="sxs-lookup"><span data-stu-id="f63e6-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="f63e6-108">Nahraďte obsah souboru Window1.xaml následující kód XAML.</span><span class="sxs-lookup"><span data-stu-id="f63e6-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="f63e6-109">Tento kód vykreslí uživatelské rozhraní vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="f63e6-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="f63e6-110">Přidáte odkaz na sestavení Microsoft Ink, Microsoft.Ink.dll, který se nachází v \Program Files\Microsoft Shared\Ink.</span><span class="sxs-lookup"><span data-stu-id="f63e6-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="f63e6-111">Nahraďte obsah souboru kódu na pozadí s následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="f63e6-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="f63e6-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f63e6-112">See also</span></span>
- <span data-ttu-id="f63e6-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span><span class="sxs-lookup"><span data-stu-id="f63e6-113">[Microsoft.Ink.InkCollector](https://msdn.microsoft.com/library/microsoft.ink.inkcollector\(v=vs.90\).aspx)</span></span>
