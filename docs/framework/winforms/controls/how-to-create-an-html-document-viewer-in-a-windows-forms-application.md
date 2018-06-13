---
title: 'Postupy: Vytvoření prohlížeče dokumentu HTML ve formulářové aplikaci Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WebBrowser control [Windows Forms], creating an HTML document viewer
- document viewers
- Windows Forms, creating document viewers
ms.assetid: 6a6338fe-f7ee-4f5e-9d8f-0465c57e9039
ms.openlocfilehash: 1330e20cc4fe7df86e51bebca28e4a71e3108673
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530540"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Postupy: Vytvoření prohlížeče dokumentu HTML ve formulářové aplikaci Windows
Můžete použít <xref:System.Windows.Forms.WebBrowser> ovládací prvek zobrazit a tisk dokumentů HTML bez zadání všechny funkce prohlížeči Internet. To je užitečné, pokud chcete využít výhod možnosti formátování HTML, ale nechcete, aby vaši uživatelé načíst libovolné webové stránky, které mohou obsahovat nedůvěryhodné ovládací prvky webového nebo potenciálně škodlivý kód. Můžete chtít omezit schopnosti produktu <xref:System.Windows.Forms.WebBrowser> řídit tímto způsobem, například můžete použít jako prohlížeč formátu HTML e-mailu nebo k poskytnutí nápovědy ve formátu HTML v aplikaci.  
  
### <a name="to-create-an-html-document-viewer"></a>K vytvoření prohlížeče dokumentu HTML  
  
1.  Nastavit <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> vlastnost, která má `false` zabránit <xref:System.Windows.Forms.WebBrowser> ovládací prvek v otevírání souborů, které jsou umístěny na ho.  
  
     [!code-csharp[WebBrowserMisc#20](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  Nastavte <xref:System.Windows.Forms.WebBrowser.Url%2A> vlastnost do umístění souboru počáteční k zobrazení.  
  
     [!code-csharp[WebBrowserMisc#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.WebBrowser> ovládací prvek s názvem `webBrowser1`.  
  
-   Odkazuje na `System` a `System.Windows.Forms` sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.WebBrowser>  
 <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>  
 <xref:System.Windows.Forms.WebBrowser.Url%2A>  
 [Přehled ovládacího prvku WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)  
 [WebBrowser – zabezpečení](../../../../docs/framework/winforms/controls/webbrowser-security.md)  
 [Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser](../../../../docs/framework/winforms/controls/how-to-navigate-to-a-url-with-the-webbrowser-control.md)  
 [Postupy: Tisk pomocí ovládacího prvku WebBrowser](../../../../docs/framework/winforms/controls/how-to-print-with-a-webbrowser-control.md)
