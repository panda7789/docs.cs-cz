---
title: "Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: a447d69eb6dafbff75ddd9d161abd4f78c607cdd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a><span data-ttu-id="22514-102">Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="22514-102">How to: Navigate to a URL with the WebBrowser Control</span></span>
<span data-ttu-id="22514-103">Následující příklad kódu ukazuje, jak se orientovat <xref:System.Windows.Forms.WebBrowser> řízení konkrétní adresy URL.</span><span class="sxs-lookup"><span data-stu-id="22514-103">The following code example demonstrates how to navigate the <xref:System.Windows.Forms.WebBrowser> control to a specific URL.</span></span>  
  
 <span data-ttu-id="22514-104">Pokud chcete zjistit, kdy je nový dokument úplným načtením, zpracování <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> událostí.</span><span class="sxs-lookup"><span data-stu-id="22514-104">To determine when the new document is fully loaded, handle the <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> event.</span></span> <span data-ttu-id="22514-105">Ukázka tuto událost, najdete v části [postupy: tisk pomocí ovládacího prvku WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md).</span><span class="sxs-lookup"><span data-stu-id="22514-105">For a demonstration of this event, see [How to: Print with a WebBrowser Control](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="22514-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="22514-106">Example</span></span>  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="22514-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="22514-107">Compiling the Code</span></span>  
 <span data-ttu-id="22514-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="22514-108">This example requires:</span></span>  
  
-   <span data-ttu-id="22514-109">A <xref:System.Windows.Forms.WebBrowser> ovládací prvek s názvem `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="22514-109">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="22514-110">Odkazuje na `System` a `System.Windows.Forms` sestavení.</span><span class="sxs-lookup"><span data-stu-id="22514-110">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="22514-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="22514-111">See Also</span></span>  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>  
 [<span data-ttu-id="22514-112">Ovládací prvek WebBrowser</span><span class="sxs-lookup"><span data-stu-id="22514-112">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
 [<span data-ttu-id="22514-113">Postupy: Tisk pomocí ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="22514-113">How to: Print with a WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
