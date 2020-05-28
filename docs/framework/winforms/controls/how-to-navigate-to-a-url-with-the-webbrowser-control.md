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
ms.openlocfilehash: f6cb26ff247bba75cc351d453314bade2d38d9f5
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144835"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="528ad-102">Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="528ad-102">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="528ad-103">Následující příklad kódu ukazuje, jak navigovat <xref:System.Windows.Forms.WebBrowser> ovládací prvek na konkrétní adresu URL.</span><span class="sxs-lookup"><span data-stu-id="528ad-103">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>

 <span data-ttu-id="528ad-104">Chcete-li zjistit, kdy je nový dokument zcela načten, zpracujte <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> událost.</span><span class="sxs-lookup"><span data-stu-id="528ad-104">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="528ad-105">Ukázku této události naleznete v tématu [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span><span class="sxs-lookup"><span data-stu-id="528ad-105">For a demonstration of this event, see [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span></span>

## <a name="example"></a><span data-ttu-id="528ad-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="528ad-106">Example</span></span>

```vb
Me.webBrowser1.Navigate("https://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("https://www.microsoft.com");
```

## <a name="compiling-the-code"></a><span data-ttu-id="528ad-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="528ad-107">Compiling the Code</span></span>
 <span data-ttu-id="528ad-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="528ad-108">This example requires:</span></span>

- <span data-ttu-id="528ad-109"><xref:System.Windows.Forms.WebBrowser>Ovládací prvek s názvem `webBrowser1` .</span><span class="sxs-lookup"><span data-stu-id="528ad-109">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>

- <span data-ttu-id="528ad-110">Odkazy na `System` sestavení a `System.Windows.Forms` .</span><span class="sxs-lookup"><span data-stu-id="528ad-110">References to the `System` and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="528ad-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="528ad-111">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [<span data-ttu-id="528ad-112">Ovládací prvek WebBrowser</span><span class="sxs-lookup"><span data-stu-id="528ad-112">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
- [<span data-ttu-id="528ad-113">Postupy: Tisk pomocí ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="528ad-113">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
