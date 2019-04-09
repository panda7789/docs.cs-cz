---
title: 'Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- WebBrowser.Navigate
helpviewer_keywords:
- WebBrowser control [Windows Forms], examples
- URLs [Windows Forms], navigating to
- WebBrowser control [Windows Forms], navigating to URLs
- examples [Windows Forms], WebBrowser control
ms.assetid: b3ec38cb-f509-4d0b-bd79-9f3611259c62
ms.openlocfilehash: a174b6ae60f87e91e6f97e8fa7f8ad3892ef017a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59132935"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="8c896-102">Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="8c896-102">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="8c896-103">Následující příklad kódu ukazuje, jak se orientovat <xref:System.Windows.Forms.WebBrowser> ovládacího prvku na konkrétní adresu URL.</span><span class="sxs-lookup"><span data-stu-id="8c896-103">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>  
  
 <span data-ttu-id="8c896-104">Pokud chcete zjistit, kdy je nový dokument plně načten, zpracovat <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="8c896-104">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="8c896-105">Ukázku této události, naleznete v tématu [jak: Tisk pomocí ovládacího prvku WebBrowser](how-to-print-with-a-webbrowser-control.md).</span><span class="sxs-lookup"><span data-stu-id="8c896-105">For a demonstration of this event, see [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8c896-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8c896-106">Example</span></span>  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="8c896-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="8c896-107">Compiling the Code</span></span>  
 <span data-ttu-id="8c896-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="8c896-108">This example requires:</span></span>  
  
-   <span data-ttu-id="8c896-109">A <xref:System.Windows.Forms.WebBrowser> ovládací prvek s názvem `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="8c896-109">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="8c896-110">Odkazy `System` a `System.Windows.Forms` sestavení.</span><span class="sxs-lookup"><span data-stu-id="8c896-110">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8c896-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="8c896-111">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [<span data-ttu-id="8c896-112">WebBrowser – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="8c896-112">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
- [<span data-ttu-id="8c896-113">Postupy: Tisk pomocí ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="8c896-113">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
