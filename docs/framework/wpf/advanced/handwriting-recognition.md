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
ms.openlocfilehash: 417af272514ac9ce68c8faa72339f2befc2dd7c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59170193"
---
# <a name="handwriting-recognition"></a><span data-ttu-id="5f4cb-102">Rozpoznávání textu psaného rukou</span><span class="sxs-lookup"><span data-stu-id="5f4cb-102">Handwriting Recognition</span></span>
<span data-ttu-id="5f4cb-103">Tato část popisuje základní informace o rozpoznávání, protože se týkají digitálních inkoust v platformě WPF.</span><span class="sxs-lookup"><span data-stu-id="5f4cb-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="5f4cb-104">Rozpoznávání řešení</span><span class="sxs-lookup"><span data-stu-id="5f4cb-104">Recognition Solutions</span></span>  
 <span data-ttu-id="5f4cb-105">Následující příklad ukazuje, jak rozpoznávání rukopisu pomocí [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) třídy.</span><span class="sxs-lookup"><span data-stu-id="5f4cb-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5f4cb-106">Tato ukázka vyžaduje nainstalované nástroje pro rozpoznávání rukopisu v systému.</span><span class="sxs-lookup"><span data-stu-id="5f4cb-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="5f4cb-107">Vytvoření nového projektu aplikace WPF v sadě Visual Studio volá **InkRecognition**.</span><span class="sxs-lookup"><span data-stu-id="5f4cb-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="5f4cb-108">Nahraďte obsah souboru Window1.xaml následující kód XAML.</span><span class="sxs-lookup"><span data-stu-id="5f4cb-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="5f4cb-109">Tento kód vykreslí uživatelské rozhraní vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="5f4cb-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="5f4cb-110">Přidáte odkaz na sestavení Microsoft Ink, Microsoft.Ink.dll, který se nachází v \Program Files\Microsoft Shared\Ink.</span><span class="sxs-lookup"><span data-stu-id="5f4cb-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="5f4cb-111">Nahraďte obsah souboru kódu na pozadí s následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="5f4cb-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="5f4cb-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5f4cb-112">See also</span></span>

- <span data-ttu-id="5f4cb-113">[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="5f4cb-113">[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))</span></span>
