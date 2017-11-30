---
title: "Postupy: Přístup ke zdroji HTML ve spravovaném objektu modelu dokumentu HTML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- managed HTML DOM
- HTML [Windows Forms], accessing in Windows Forms
ms.assetid: 53db79fa-8a5e-448e-88c2-f54ace3860b6
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 7ef9839029e1c60cbc0d713e8982baa5708a281f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-access-the-html-source-in-the-managed-html-document-object-model"></a><span data-ttu-id="99b08-102">Postupy: Přístup ke zdroji HTML ve spravovaném objektu modelu dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="99b08-102">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="99b08-103"><xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> a <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> vlastnosti <xref:System.Windows.Forms.WebBrowser> řízení vrátit HTML aktuálního dokumentu, který existoval, když se napřed zobrazí.</span><span class="sxs-lookup"><span data-stu-id="99b08-103">The <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A> properties on the <xref:System.Windows.Forms.WebBrowser> control return the HTML of the current document as it existed when it was first displayed.</span></span> <span data-ttu-id="99b08-104">Nicméně pokud změníte stránce pomocí volání metod a vlastností, jako třeba <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> a <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, tyto změny se neprojeví při volání <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> a <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span><span class="sxs-lookup"><span data-stu-id="99b08-104">However, if you modify the page using method and property calls such as <xref:System.Windows.Forms.HtmlElement.AppendChild%2A> and <xref:System.Windows.Forms.HtmlElement.InnerHtml%2A>, these changes will not appear when you call <xref:System.Windows.Forms.WebBrowser.DocumentStream%2A> and <xref:System.Windows.Forms.WebBrowser.DocumentText%2A>.</span></span> <span data-ttu-id="99b08-105">Pokud chcete získat nejaktuálnější zdrojový kód HTML pro modelu DOM, musí volat <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> vlastnost v elementu HTML.</span><span class="sxs-lookup"><span data-stu-id="99b08-105">To obtain the most up-to-date HTML source for the DOM, you must call the <xref:System.Windows.Forms.HtmlElement.OuterHtml%2A> property on the HTML element.</span></span>  
  
 <span data-ttu-id="99b08-106">Následující postup ukazuje, jak načíst zdroji dynamické a zobrazit ji v samostatné místní nabídky.</span><span class="sxs-lookup"><span data-stu-id="99b08-106">The following procedure shows how to retrieve the dynamic source and display it in a separate shortcut menu.</span></span>  
  
### <a name="retrieving-the-dynamic-source-with-the-outerhtml-property"></a><span data-ttu-id="99b08-107">Načítání zdroji dynamické s vlastností OuterHtml</span><span class="sxs-lookup"><span data-stu-id="99b08-107">Retrieving the dynamic source with the OuterHtml property</span></span>  
  
1.  <span data-ttu-id="99b08-108">Vytvořte novou aplikaci Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="99b08-108">Create a new Windows Forms application.</span></span> <span data-ttu-id="99b08-109">Spustit s jedním <xref:System.Windows.Forms.Form>a pojmenujte ji `Form1`.</span><span class="sxs-lookup"><span data-stu-id="99b08-109">Start with a single <xref:System.Windows.Forms.Form>, and call it `Form1`.</span></span>  
  
2.  <span data-ttu-id="99b08-110">Hostitel <xref:System.Windows.Forms.WebBrowser> řízení v aplikaci Windows Forms a pojmenujte ji `WebBrowser1`.</span><span class="sxs-lookup"><span data-stu-id="99b08-110">Host the <xref:System.Windows.Forms.WebBrowser> control in your Windows Forms application, and name it `WebBrowser1`.</span></span> <span data-ttu-id="99b08-111">Další informace najdete v tématu [postupy: přidání schopností webového prohlížeče do formulářové aplikace Windows](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span><span class="sxs-lookup"><span data-stu-id="99b08-111">For more information, see [How to: Add Web Browser Capabilities to a Windows Forms Application](../../../../docs/framework/winforms/controls/how-to-add-web-browser-capabilities-to-a-windows-forms-application.md).</span></span>  
  
3.  <span data-ttu-id="99b08-112">Vytvořte druhý <xref:System.Windows.Forms.Form> ve vaší aplikaci s názvem `CodeForm`.</span><span class="sxs-lookup"><span data-stu-id="99b08-112">Create a second <xref:System.Windows.Forms.Form> in your application called `CodeForm`.</span></span>  
  
4.  <span data-ttu-id="99b08-113">Přidat <xref:System.Windows.Forms.RichTextBox> řídit k `CodeForm` a nastavit jeho <xref:System.Windows.Forms.Control.Dock%2A> vlastnost `Fill`.</span><span class="sxs-lookup"><span data-stu-id="99b08-113">Add a <xref:System.Windows.Forms.RichTextBox> control to `CodeForm` and set its <xref:System.Windows.Forms.Control.Dock%2A> property to `Fill`.</span></span>  
  
5.  <span data-ttu-id="99b08-114">Vytvoření veřejné vlastnosti na `CodeForm` názvem `Code`.</span><span class="sxs-lookup"><span data-stu-id="99b08-114">Create a public property on `CodeForm` called `Code`.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/CodeForm.cs#1)]
     [!code-vb[DisplayWebBrowserCode#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/CodeForm.vb#1)]  
  
6.  <span data-ttu-id="99b08-115">Přidat <xref:System.Windows.Forms.Button> ovládací prvek s názvem `Button1` k vaší <xref:System.Windows.Forms.Form>a sledování <xref:System.Windows.Forms.Control.Click> událostí.</span><span class="sxs-lookup"><span data-stu-id="99b08-115">Add a <xref:System.Windows.Forms.Button> control named `Button1` to your <xref:System.Windows.Forms.Form>, and monitor for the <xref:System.Windows.Forms.Control.Click> event.</span></span> <span data-ttu-id="99b08-116">Informace o sledování událostí najdete v tématu [události](../../../../docs/standard/events/index.md).</span><span class="sxs-lookup"><span data-stu-id="99b08-116">For details on monitoring events, see [Events](../../../../docs/standard/events/index.md).</span></span>  
  
7.  <span data-ttu-id="99b08-117">Přidejte následující kód, který <xref:System.Windows.Forms.Control.Click> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="99b08-117">Add the following code to the <xref:System.Windows.Forms.Control.Click> event handler.</span></span>  
  
     [!code-csharp[DisplayWebBrowserCode#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/DisplayWebBrowserCode/CS/Form1.cs#2)]
     [!code-vb[DisplayWebBrowserCode#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/DisplayWebBrowserCode/VB/Form1.vb#2)]  
  
## <a name="robust-programming"></a><span data-ttu-id="99b08-118">Robustní programování</span><span class="sxs-lookup"><span data-stu-id="99b08-118">Robust Programming</span></span>  
 <span data-ttu-id="99b08-119">Vždy otestovat hodnotu <xref:System.Windows.Forms.WebBrowser.Document%2A> před pokusem o jeho načtení.</span><span class="sxs-lookup"><span data-stu-id="99b08-119">Always test the value of <xref:System.Windows.Forms.WebBrowser.Document%2A> before attempting to retrieve it.</span></span> <span data-ttu-id="99b08-120">Pokud není aktuální stránku dokončení načítání, <xref:System.Windows.Forms.WebBrowser.Document%2A> nebo jeden nebo více jeho podřízených objektů nemusí být inicializován.</span><span class="sxs-lookup"><span data-stu-id="99b08-120">If the current page is not finished loading, <xref:System.Windows.Forms.WebBrowser.Document%2A> or one or more of its child objects may not be initialized.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99b08-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="99b08-121">See Also</span></span>  
 [<span data-ttu-id="99b08-122">Pomocí modelu objektu spravovaného dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="99b08-122">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)  
 [<span data-ttu-id="99b08-123">Přehled ovládacího prvku WebBrowser</span><span class="sxs-lookup"><span data-stu-id="99b08-123">WebBrowser Control Overview</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-overview.md)
