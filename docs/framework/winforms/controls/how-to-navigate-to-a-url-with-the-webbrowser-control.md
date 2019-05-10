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
ms.openlocfilehash: bee16a388d823f74bc9c88bc34b510d2a5907393
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64649226"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser
Následující příklad kódu ukazuje, jak se orientovat <xref:System.Windows.Forms.WebBrowser> ovládacího prvku na konkrétní adresu URL.  
  
 Pokud chcete zjistit, kdy je nový dokument plně načten, zpracovat <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> událostí. Ukázku této události, naleznete v tématu [jak: Tisk pomocí ovládacího prvku WebBrowser](how-to-print-with-a-webbrowser-control.md).  
  
## <a name="example"></a>Příklad  
  
```vb  
Me.webBrowser1.Navigate("http://www.microsoft.com")  
```  
  
```csharp  
this.webBrowser1.Navigate("http://www.microsoft.com");  
```  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- A <xref:System.Windows.Forms.WebBrowser> ovládací prvek s názvem `webBrowser1`.  
  
- Odkazy `System` a `System.Windows.Forms` sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [Ovládací prvek WebBrowser](webbrowser-control-windows-forms.md)
- [Postupy: Tisk pomocí ovládacího prvku WebBrowser](how-to-print-with-a-webbrowser-control.md)
