---
title: 'Postupy: Přístup ke zdroji HTML v objektovém modelu spravovaného dokumentu HTML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
ms.openlocfilehash: b9122e2c5bebdde2e04507973ccfeb924d0ad23e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57723644"
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a><span data-ttu-id="d3654-102">Postupy: Přístup ke zdroji HTML v objektovém modelu spravovaného dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="d3654-102">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="d3654-103"><xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> a <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnosti <xref:System.Windows.Forms.WebBrowser> ovládací prvek vrátí kód HTML aktuálního dokumentu jako existovala při prvním zobrazení.</span><span class="sxs-lookup"><span data-stu-id="d3654-103">The <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> properties on the <xref:System.Windows.Forms.WebBrowser> control return the HTML of the current document as it existed when it was first displayed.</span></span> <span data-ttu-id="d3654-104">Ale při úpravě stránky pomocí volání metody a vlastnosti, například <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> a <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, tyto změny se nezobrazí při volání <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> a <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span><span class="sxs-lookup"><span data-stu-id="d3654-104">However, if you modify the page using method and property calls such as <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> and <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, these changes will not appear when you call <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span></span> <span data-ttu-id="d3654-105">Chcete-li získat nejnovější zdrojový kód HTML pro modelu DOM, musíte volat <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> vlastnosti elementu HTML.</span><span class="sxs-lookup"><span data-stu-id="d3654-105">To obtain the most up-to-date HTML source for the DOM, you must call the <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> property on the HTML element.</span></span>  
  
 <span data-ttu-id="d3654-106">Následující postup ukazuje, jak načíst dynamické zdroje a zobrazí v samostatném nabídku.</span><span class="sxs-lookup"><span data-stu-id="d3654-106">The following procedure shows how to retrieve the dynamic source and display it in a separate shortcut menu.</span></span>  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a><span data-ttu-id="d3654-107">Načítání dynamické zdroje pomocí vlastnosti vnější HTML</span><span class="sxs-lookup"><span data-stu-id="d3654-107">Retrieving the dynamic source with the OuterHtml property</span></span>  
  
1.  <span data-ttu-id="d3654-108">Vytvoření nové aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="d3654-108">Create a new Windows Forms application.</span></span> <span data-ttu-id="d3654-109">Začněte s jedním <xref:System.Windows.Forms.Form>a jeho volání `Form1`.</span><span class="sxs-lookup"><span data-stu-id="d3654-109">Start with a single <xref:System.Windows.Forms.Form>, and call it `Form1`.</span></span>  
  
2.  <span data-ttu-id="d3654-110">Hostitel <xref:System.Windows.Forms.WebBrowser> ovládací prvek v aplikaci Windows Forms a pojmenujte ho `WebBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="d3654-110">Host the <xref:System.Windows.Forms.WebBrowser> control in your Windows Forms application, and name it `WebBrowser1`.</span></span> <span data-ttu-id="d3654-111">Další informace najdete v tématu [jak: Přidání schopností webového prohlížeče do formulářové aplikaci Windows](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="d3654-111">For more information, see [How to: Add Web Browser Capabilities to a Windows Forms Application](how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span></span>  
  
3.  <span data-ttu-id="d3654-112">Vytvořte druhý <xref:System.Windows.Forms.Form> ve vaší aplikaci s názvem `CodeForm`.</span><span class="sxs-lookup"><span data-stu-id="d3654-112">Create a second <xref:System.Windows.Forms.Form> in your application called `CodeForm`.</span></span>  
  
4.  <span data-ttu-id="d3654-113">Přidat <xref:System.Windows.Forms.RichTextBox> mít pod kontrolou `CodeForm` a nastavte jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost `Fill`.</span><span class="sxs-lookup"><span data-stu-id="d3654-113">Add a <xref:System.Windows.Forms.RichTextBox> control to `CodeForm` and set its <xref:System.Windows.Forms.Control.Dock%2A> property to `Fill`.</span></span>  
  
5.  <span data-ttu-id="d3654-114">Vytvoření veřejné vlastnosti na `CodeForm` volá `Code`.</span><span class="sxs-lookup"><span data-stu-id="d3654-114">Create a public property on `CodeForm` called `Code`.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#1](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  <span data-ttu-id="d3654-115">Přidat <xref:System.Windows.Forms.Button> ovládací prvek s názvem `Button1` k vaší <xref:System.Windows.Forms.Form>a monitorovat <xref:System.Windows.Forms.Control.Click> událostí.</span><span class="sxs-lookup"><span data-stu-id="d3654-115">Add a <xref:System.Windows.Forms.Button> control named `Button1` to your <xref:System.Windows.Forms.Form>, and monitor for the <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="d3654-116">Podrobnosti o sledování událostí najdete v tématu [události](../../../standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="d3654-116">For details on monitoring events, see [Events](../../../standard/events/index.md).</span></span>  
  
7.  <span data-ttu-id="d3654-117">Přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="d3654-117">Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#2](~/samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="d3654-118">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="d3654-118">Robust Programming</span></span>  
 <span data-ttu-id="d3654-119">Vždy testování hodnot <xref:System.Windows.Forms.WebBrowser.Document%2A> před pokusem o jeho načtení.</span><span class="sxs-lookup"><span data-stu-id="d3654-119">Always test the value of <xref:System.Windows.Forms.WebBrowser.Document%2A> before attempting to retrieve it.</span></span> <span data-ttu-id="d3654-120">Pokud není aktuální stránky dokončeno načítání, <xref:System.Windows.Forms.WebBrowser.Document%2A> nebo jeden nebo více jeho podřízených objektů nemusí být inicializovány.</span><span class="sxs-lookup"><span data-stu-id="d3654-120">If the current page is not finished loading, <xref:System.Windows.Forms.WebBrowser.Document%2A> or one or more of its child objects may not be initialized.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3654-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3654-121">See also</span></span>
- [<span data-ttu-id="d3654-122">Použití spravovaného modelu DOM (Document Object Model) HTML</span><span class="sxs-lookup"><span data-stu-id="d3654-122">Using the Managed HTML Document Object Model</span></span>](using-the-managed-html-document-object-model.md)
- [<span data-ttu-id="d3654-123">Přehled ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="d3654-123">WebBrowser Control Overview</span></span>](webbrowser-control-overview.md)
