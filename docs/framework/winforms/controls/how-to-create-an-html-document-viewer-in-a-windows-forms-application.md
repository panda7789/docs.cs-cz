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
# <a name="how-to-create-an-html-document-viewer-in-a-windows-forms-application"></a><span data-ttu-id="4225a-102">Postupy: Vytvoření prohlížeče dokumentu HTML v aplikaci Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4225a-102">How to: Create an HTML Document Viewer in a Windows Forms Application</span></span>
<span data-ttu-id="4225a-103">Pomocí ovládacího prvku <xref:System.Windows.Forms.WebBrowser> můžete zobrazovat a tisknout dokumenty HTML bez nutnosti poskytovat všechny funkce internetového webového prohlížeče.</span><span class="sxs-lookup"><span data-stu-id="4225a-103">You can use the <xref:System.Windows.Forms.WebBrowser> control to display and print HTML documents without providing the full functionality of an Internet Web browser.</span></span> <span data-ttu-id="4225a-104">To je užitečné, pokud chcete využít možnosti formátování HTML, ale nechcete, aby uživatelé načetli libovolné webové stránky, které mohou obsahovat nedůvěryhodné webové ovládací prvky nebo potenciálně škodlivý kód skriptu.</span><span class="sxs-lookup"><span data-stu-id="4225a-104">This is useful when you want to take advantage of the formatting capabilities of HTML but do not want your users to load arbitrary Web pages that may contain untrusted Web controls or potentially malicious script code.</span></span> <span data-ttu-id="4225a-105">Můžete chtít omezit schopnost ovládacího prvku <xref:System.Windows.Forms.WebBrowser> tímto způsobem, například pro použití jako prohlížeč e-mailů HTML nebo k poskytnutí nápovědy ve formátu HTML ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="4225a-105">You might want to restrict the capability of the <xref:System.Windows.Forms.WebBrowser> control in this manner, for example, to use it as an HTML email viewer or to provide HTML-formatted help in your application.</span></span>  
  
### <a name="to-create-an-html-document-viewer"></a><span data-ttu-id="4225a-106">Vytvoření prohlížeče dokumentů HTML</span><span class="sxs-lookup"><span data-stu-id="4225a-106">To create an HTML document viewer</span></span>  
  
1. <span data-ttu-id="4225a-107">Nastavte vlastnost <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> na `false`, aby se zabránilo ovládacímu prvku <xref:System.Windows.Forms.WebBrowser> otevírat soubory, které se na něj přetáhly.</span><span class="sxs-lookup"><span data-stu-id="4225a-107">Set the <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A> property to `false` to prevent the <xref:System.Windows.Forms.WebBrowser> control from opening files dropped onto it.</span></span>  
  
     [!code-csharp[WebBrowserMisc#20](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#20)]
     [!code-vb[WebBrowserMisc#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#20)]  
  
2. <span data-ttu-id="4225a-108">Nastavte vlastnost <xref:System.Windows.Forms.WebBrowser.Url%2A> na umístění počátečního souboru, který se má zobrazit.</span><span class="sxs-lookup"><span data-stu-id="4225a-108">Set the <xref:System.Windows.Forms.WebBrowser.Url%2A> property to the location of the initial file to display.</span></span>  
  
     [!code-csharp[WebBrowserMisc#21](~/samples/snippets/csharp/VS_Snippets_Winforms/WebBrowserMisc/CS/WebBrowserMisc.cs#21)]
     [!code-vb[WebBrowserMisc#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WebBrowserMisc/vb/WebBrowserMisc.vb#21)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4225a-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4225a-109">Compiling the Code</span></span>  
 <span data-ttu-id="4225a-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="4225a-110">This example requires:</span></span>  
  
- <span data-ttu-id="4225a-111"><xref:System.Windows.Forms.WebBrowser> ovládací prvek s názvem `webBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="4225a-111">A <xref:System.Windows.Forms.WebBrowser> control named `webBrowser1`.</span></span>  
  
- <span data-ttu-id="4225a-112">Odkazy na `System` a `System.Windows.Forms` sestavení.</span><span class="sxs-lookup"><span data-stu-id="4225a-112">References to the `System` and `System.Windows.Forms` assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4225a-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="4225a-113">See also</span></span>

- <xref:System.Windows.Forms.WebBrowser>
- <xref:System.Windows.Forms.WebBrowser.AllowWebBrowserDrop%2A>
- <xref:System.Windows.Forms.WebBrowser.Url%2A>
- [<span data-ttu-id="4225a-114">Přehled ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="4225a-114">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
- [<span data-ttu-id="4225a-115">WebBrowser – zabezpečení</span><span class="sxs-lookup"><span data-stu-id="4225a-115">WebBrowser Security</span></span>](webbrowser-security.md)
- [<span data-ttu-id="4225a-116">Postupy: Přechod na adresu URL pomocí ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="4225a-116">How to: Navigate to a URL with the WebBrowser Control</span></span>](how-to-navigate-to-a-url-with-the-webbrowser-control.md)
- [<span data-ttu-id="4225a-117">Postupy: Tisk pomocí ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="4225a-117">How to: Print with a WebBrowser Control</span></span>](how-to-print-with-a-webbrowser-control.md)
