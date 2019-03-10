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
ms.openlocfilehash: a25d8bf413614ae71676335c0c8e672caadbf885
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717749"
---
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a>Postupy: Vytvoření prohlížeče dokumentu HTML ve formulářové aplikaci Windows
Můžete použít <xref:System.Windows.Forms.WebBrowser> ovládací prvek pro zobrazení a tisk dokumentů HTML bez zadání plnou funkčnost prohlížeči Internet. To je užitečné, když chtějí využít nabídky možností formátování HTML, ale nechcete, aby vaši uživatelé k načtení libovolného webové stránky, které mohou obsahovat nedůvěryhodné webové ovládací prvky nebo potenciálně škodlivý kód. Můžete chtít omezit schopnost <xref:System.Windows.Forms.WebBrowser> řídit tímto způsobem, například pro použití jako e-mailu prohlížeč formátu HTML nebo poskytnutí nápovědy ve formátu HTML v aplikaci.  
  
### <a name="to-create-an-html-document-viewer"></a>K vytvoření prohlížeče dokumentu HTML  
  
1.  Nastavte <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> vlastnost `false` zabránit <xref:System.Windows.Forms.WebBrowser> ovládacího prvku z otevírání souborů vyřadit problém napravit.  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  Nastavte <xref:System.Windows.Forms.WebBrowser.Url%2A> vlastnost do umístění souboru počáteční k zobrazení.  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.WebBrowser> ovládací prvek s názvem `webBrowser1`.  
  
-   Odkazy `System` a `System.Windows.Forms` sestavení.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [Přehled ovládacího prvku WebBrowser](webbrowser-control-overview.md)
- [WebBrowser – zabezpečení](webbrowser-security.md)
- [Postupy: Přejděte na adresu URL pomocí ovládacího prvku WebBrowser](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [Postupy: Tisk pomocí ovládacího prvku WebBrowser](how-to-print-with-a-webbrowser-control.md)
