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
# <a name="how-to-navigate-to-a-url-with-the-webbrowser-control"></a>Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser
Následující příklad kódu ukazuje, jak navigovat <xref:System.Windows.Forms.WebBrowser> ovládací prvek na konkrétní adresu URL.

 Chcete-li zjistit, kdy je nový dokument zcela načten, zpracujte <xref:System.Windows.Forms.WebBrowser.DocumentCompleted> událost. Ukázku této události naleznete v tématu [How to: Print with a WebBrowser Control](how-to-print-with-a-webbrowser-control.md).

## <a name="example"></a>Příklad

```vb
Me.webBrowser1.Navigate("https://www.microsoft.com")
```

```csharp
this.webBrowser1.Navigate("https://www.microsoft.com");
```

## <a name="compiling-the-code"></a>Probíhá kompilace kódu
 Tento příklad vyžaduje:

- <xref:System.Windows.Forms.WebBrowser>Ovládací prvek s názvem `webBrowser1` .

- Odkazy na `System` sestavení a `System.Windows.Forms` .

## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.DocumentCompleted?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigating?displayProperty=nameWithType>
- <xref:System.Windows.Forms.WebBrowser.Navigated?displayProperty=nameWithType>
- [Ovládací prvek WebBrowser](webbrowser-control-windows-forms.md)
- [Postupy: Tisk pomocí ovládacího prvku WebBrowser](how-to-print-with-a-webbrowser-control.md)
