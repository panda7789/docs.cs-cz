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
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a><span data-ttu-id="cfc9c-102">Postupy: Vytvoření prohlížeče dokumentu HTML ve formulářové aplikaci Windows</span><span class="sxs-lookup"><span data-stu-id="cfc9c-102">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>
<span data-ttu-id="cfc9c-103">Můžete použít <xref:System.Windows.Forms.WebBrowser> ovládací prvek pro zobrazení a tisk dokumentů HTML bez zadání plnou funkčnost prohlížeči Internet.</span><span class="sxs-lookup"><span data-stu-id="cfc9c-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to display and print HTML documents without providing the full functionality of an Internet Web browser.</span></span> <span data-ttu-id="cfc9c-104">To je užitečné, když chtějí využít nabídky možností formátování HTML, ale nechcete, aby vaši uživatelé k načtení libovolného webové stránky, které mohou obsahovat nedůvěryhodné webové ovládací prvky nebo potenciálně škodlivý kód.</span><span class="sxs-lookup"><span data-stu-id="cfc9c-104">This is useful when you want to take advantage of the formatting capabilities of HTML but do not want your users to load arbitrary Web pages that may contain untrusted Web controls or potentially malicious script code.</span></span> <span data-ttu-id="cfc9c-105">Můžete chtít omezit schopnost <xref:System.Windows.Forms.WebBrowser> řídit tímto způsobem, například pro použití jako e-mailu prohlížeč formátu HTML nebo poskytnutí nápovědy ve formátu HTML v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="cfc9c-105">You might want to restrict the capability of the <xref:System.Windows.Forms.WebBrowser> control in this manner, for example, to use it as an HTML email viewer or to provide HTML-formatted help in your application.</span></span>  
  
### <a name="to-create-an-html-document-viewer"></a><span data-ttu-id="cfc9c-106">K vytvoření prohlížeče dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="cfc9c-106">To create an HTML document viewer</span></span>  
  
1.  <span data-ttu-id="cfc9c-107">Nastavte <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> vlastnost `false` zabránit <xref:System.Windows.Forms.WebBrowser> ovládacího prvku z otevírání souborů vyřadit problém napravit.</span><span class="sxs-lookup"><span data-stu-id="cfc9c-107">Set the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2.  <span data-ttu-id="cfc9c-108">Nastavte <xref:System.Windows.Forms.WebBrowser.Url%2A> vlastnost do umístění souboru počáteční k zobrazení.</span><span class="sxs-lookup"><span data-stu-id="cfc9c-108">Set the <xref:System.Windows.Forms.WebBrowser.Url%2A> property to the location of the initial file to display.</span></span>  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="cfc9c-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="cfc9c-109">Compiling the Code</span></span>  
 <span data-ttu-id="cfc9c-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="cfc9c-110">This example requires:</span></span>  
  
-   <span data-ttu-id="cfc9c-111">A <xref:System.Windows.Forms.WebBrowser> ovládací prvek s názvem `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="cfc9c-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
-   <span data-ttu-id="cfc9c-112">Odkazy `System` a `System.Windows.Forms` sestavení.</span><span class="sxs-lookup"><span data-stu-id="cfc9c-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cfc9c-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cfc9c-113">See also</span></span>
- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [<span data-ttu-id="cfc9c-114">Přehled ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="cfc9c-114">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- [<span data-ttu-id="cfc9c-115">WebBrowser – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="cfc9c-115">WebBrowser Security</span></span>](webbrowser-security.md)
- [<span data-ttu-id="cfc9c-116">Postupy: Přejděte na adresu URL pomocí ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="cfc9c-116">How to: Navigate to a URL with the WebBrowser Control</span></span>](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [<span data-ttu-id="cfc9c-117">Postupy: Tisk pomocí ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="cfc9c-117">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
