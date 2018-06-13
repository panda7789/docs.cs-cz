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
ms.openlocfilehash: f34577d45ddfbd2445fd4558c5694facf3f1aa29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33531882"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser
Následující příklad kódu ukazuje, jak se orientovat <xref:System.Windows.Forms.WebBrowser> řízení konkrétní adresy URL.  
  
 Pokud chcete zjistit, kdy je nový dokument úplným načtením, zpracování <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> událostí. Ukázka tuto událost, najdete v části [postupy: tisk pomocí ovládacího prvku WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md).  
  
## <a name="example"></a>Příklad  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.WebBrowser> ovládací prvek s názvem `webBrowser1`.  
  
-   Odkazuje na `System` a `System.Windows.Forms` sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>  
 [Ovládací prvek WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
 [Postupy: Tisk pomocí ovládacího prvku WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
