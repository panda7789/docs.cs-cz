---
title: Vytvoření prohlížeče dokumentů HTML v aplikaci model Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 913bc86af034645b4b8cf3d69da4c9def58fc19c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76732842"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Postupy: Vytvoření prohlížeče dokumentu HTML v aplikaci Windows Forms
Pomocí ovládacího prvku <xref:System.Windows.Forms.WebBrowser> můžete zobrazovat a tisknout dokumenty HTML bez nutnosti poskytovat všechny funkce internetového webového prohlížeče. To je užitečné, pokud chcete využít možnosti formátování HTML, ale nechcete, aby uživatelé načetli libovolné webové stránky, které mohou obsahovat nedůvěryhodné webové ovládací prvky nebo potenciálně škodlivý kód skriptu. Můžete chtít omezit schopnost ovládacího prvku <xref:System.Windows.Forms.WebBrowser> tímto způsobem, například pro použití jako prohlížeč e-mailů HTML nebo k poskytnutí nápovědy ve formátu HTML ve vaší aplikaci.  
  
### <a name="to-create-an-html-document-viewer"></a>Vytvoření prohlížeče dokumentů HTML  
  
1. Nastavte vlastnost <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> na `false`, aby se zabránilo ovládacímu prvku <xref:System.Windows.Forms.WebBrowser> otevírat soubory, které se na něj přetáhly.  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2. Nastavte vlastnost <xref:System.Windows.Forms.WebBrowser.Url%2A> na umístění počátečního souboru, který se má zobrazit.  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.WebBrowser> ovládací prvek s názvem `webBrowser1`.  
  
- Odkazy na `System` a `System.Windows.Forms` sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [Přehled ovládacího prvku WebBrowser](webbrowser-control-overview.md)
- [WebBrowser – zabezpečení](webbrowser-security.md)
- [Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Postupy: Tisk pomocí ovládacího prvku WebBrowser](how-to-print-with-a-webbrowser-control.md)
