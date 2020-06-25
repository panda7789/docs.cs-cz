---
title: 'Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser'
description: Naučte se používat model Windows Forms WebBrowser. navigace ovládacího prvku pro přechod na konkrétní adresu URL. Naučíte se také, jak určit, kdy se má nový dokument načíst.
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
ms.openlocfilehash: e6ad360cc73a84ca040869832bb59d354cb78bd5
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325573"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="49c82-104">Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="49c82-104">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="49c82-105">Následující příklad kódu ukazuje, jak navigovat <xref:System.Windows.Forms.WebBrowser> ovládací prvek na konkrétní adresu URL.</span><span class="sxs-lookup"><span data-stu-id="49c82-105">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>

 <span data-ttu-id="49c82-106">Chcete-li zjistit, kdy je nový dokument zcela načten, zpracujte <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> událost.</span><span class="sxs-lookup"><span data-stu-id="49c82-106">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="49c82-107">Ukázku této události naleznete v tématu [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span><span class="sxs-lookup"><span data-stu-id="49c82-107">For a demonstration of this event, see [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).</span></span>

## <a name="example"></a><span data-ttu-id="49c82-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="49c82-108">Example</span></span>

```vb
Me.webBrowser1.Navigate("https://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("https://www.microsoft.com");
```

## <a name="compiling-the-code"></a><span data-ttu-id="49c82-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="49c82-109">Compiling the Code</span></span>
 <span data-ttu-id="49c82-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="49c82-110">This example requires:</span></span>

- <span data-ttu-id="49c82-111"><xref:System.Windows.Forms.WebBrowser>Ovládací prvek s názvem `webBrowser1` .</span><span class="sxs-lookup"><span data-stu-id="49c82-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>

- <span data-ttu-id="49c82-112">Odkazy na `System` sestavení a `System.Windows.Forms` .</span><span class="sxs-lookup"><span data-stu-id="49c82-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>

## <a name="see-also"></a><span data-ttu-id="49c82-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="49c82-113">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [<span data-ttu-id="49c82-114">Ovládací prvek WebBrowser</span><span class="sxs-lookup"><span data-stu-id="49c82-114">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)
- [<span data-ttu-id="49c82-115">Postupy: Tisk pomocí ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="49c82-115">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
