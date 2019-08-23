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
# <a name="handwriting-recognition"></a><span data-ttu-id="d2030-102">Rozpoznávání textu psaného rukou</span><span class="sxs-lookup"><span data-stu-id="d2030-102">Handwriting Recognition</span></span>
<span data-ttu-id="d2030-103">Tato část popisuje základy rozpoznávání, protože se týkají digitálního inkoustu v platformě WPF.</span><span class="sxs-lookup"><span data-stu-id="d2030-103">This section discusses the fundamentals of recognition as it pertains to digital ink in the WPF platform.</span></span>  
  
## <a name="recognition-solutions"></a><span data-ttu-id="d2030-104">Řešení pro rozpoznávání</span><span class="sxs-lookup"><span data-stu-id="d2030-104">Recognition Solutions</span></span>  
 <span data-ttu-id="d2030-105">Následující příklad ukazuje, jak rozpoznat rukopis pomocí třídy [Microsoft. Ink. InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) .</span><span class="sxs-lookup"><span data-stu-id="d2030-105">The following example shows how to recognize ink using the [Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90)) class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d2030-106">Tato ukázka vyžaduje, aby byly v systému nainstalovány nástroje pro rozpoznávání rukopisu.</span><span class="sxs-lookup"><span data-stu-id="d2030-106">This sample requires that handwriting recognizers be installed on the system.</span></span>  
  
 <span data-ttu-id="d2030-107">Vytvořte nový projekt aplikace WPF v aplikaci Visual Studio s názvem **InkRecognition**.</span><span class="sxs-lookup"><span data-stu-id="d2030-107">Create a new WPF application project in Visual Studio called **InkRecognition**.</span></span> <span data-ttu-id="d2030-108">Obsah souboru Window1. xaml nahraďte následujícím kódem XAML.</span><span class="sxs-lookup"><span data-stu-id="d2030-108">Replace the contents of the Window1.xaml file with the following XAML code.</span></span> <span data-ttu-id="d2030-109">Tento kód vykreslí uživatelské rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2030-109">This code renders the application's user interface.</span></span>  
  
 [!code-xaml[InkRecognition#1](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml#1)]  
  
 <span data-ttu-id="d2030-110">Přidat odkaz na sestavení Microsoft Ink, Microsoft. Ink. dll, které najdete v \Program Files\Common Files\Microsoft Shared\Ink.</span><span class="sxs-lookup"><span data-stu-id="d2030-110">Add a reference to the Microsoft Ink assembly, Microsoft.Ink.dll, which can be found in \Program Files\Common Files\Microsoft Shared\Ink.</span></span> <span data-ttu-id="d2030-111">Obsah souboru kódu na pozadí nahraďte následujícím kódem.</span><span class="sxs-lookup"><span data-stu-id="d2030-111">Replace the contents of the code behind file with the following code.</span></span>  
  
 [!code-csharp[InkRecognition#2](~/samples/snippets/csharp/VS_Snippets_Wpf/InkRecognition/CSharp/Window1.xaml.cs#2)]
 [!code-vb[InkRecognition#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/InkRecognition/VisualBasic/Window1.xaml.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d2030-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d2030-112">See also</span></span>

- <span data-ttu-id="d2030-113">[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="d2030-113">[Microsoft.Ink.InkCollector](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms583683(v=vs.90))</span></span>
