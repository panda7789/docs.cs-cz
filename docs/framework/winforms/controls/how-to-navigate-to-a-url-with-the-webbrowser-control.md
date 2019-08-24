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
ms.openlocfilehash: b6c1255fa17d91daaa73001fea04f26e73dba0ae
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015832"
---
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser
Následující příklad kódu ukazuje, jak navigovat <xref:System.Windows.Forms.WebBrowser> ovládací prvek na konkrétní adresu URL.

 Chcete-li zjistit, kdy je nový dokument zcela načten, <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> zpracujte událost. Ukázku této události naleznete v tématu [How to: Tisk pomocí ovládacího prvku](how-to-print-with-a-webbrowser-control.md)WebBrowser

## <a name="example"></a>Příklad

```vb
Me.webBrowser1.Navigate("http://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("http://www.microsoft.com");
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu
 Tento příklad vyžaduje:

- Ovládací prvek s `webBrowser1`názvem. <xref:System.Windows.Forms.WebBrowser>

- Odkazy na `System` sestavení a `System.Windows.Forms` .

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [Ovládací prvek WebBrowser](webbrowser-control-windows-forms.md)
- [Postupy: Tisk pomocí ovládacího prvku WebBrowser](how-to-print-with-a-webbrowser-control.md)
