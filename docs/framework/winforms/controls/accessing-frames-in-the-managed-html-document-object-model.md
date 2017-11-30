---
title: "Přístup k rámcům v modelu spravovaného objektu dokumentu HTML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- HTML [Windows Forms], dOM
- managed HTML DOM
- HTML [Windows Forms], managed
- HTML DOM [Windows Forms], managed
- frames [Windows Forms], accessing
- DOM [Windows Forms], accessing frames in managed HTML
ms.assetid: cdeeaa22-0be4-4bbf-9a75-4ddc79199f8d
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: c8766e33f0fb253d532ff7161ed0a1e7842d0c50
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="accessing-frames-in-the-managed-html-document-object-model"></a><span data-ttu-id="40a65-102">Přístup k rámcům v modelu spravovaného objektu dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="40a65-102">Accessing Frames in the Managed HTML Document Object Model</span></span>
<span data-ttu-id="40a65-103">Některé dokumentů HTML se skládají z *rámce*, nebo okna, která může pojmout své vlastní dokumenty odlišné HTML.</span><span class="sxs-lookup"><span data-stu-id="40a65-103">Some HTML documents are composed out of *frames*, or windows that can hold their own distinct HTML documents.</span></span> <span data-ttu-id="40a65-104">Pomocí rámce usnadňuje vytvoření stránky HTML, ve kterých zůstat statický, jako je například navigační panel některé části stránky, zatímco jiné rámce neustále mění svůj obsah.</span><span class="sxs-lookup"><span data-stu-id="40a65-104">Using frames makes it easy to create HTML pages in which one or more pieces of the page remain static, such as a navigation bar, while other frames constantly change their content.</span></span>  
  
 <span data-ttu-id="40a65-105">Autoři HTML můžete vytvořit rámce v jednom ze dvou způsobů:</span><span class="sxs-lookup"><span data-stu-id="40a65-105">HTML authors can create frames in one of two ways:</span></span>  
  
-   <span data-ttu-id="40a65-106">Pomocí `FRAMESET` a `FRAME` značky, které pak vytvoří pevné windows.</span><span class="sxs-lookup"><span data-stu-id="40a65-106">Using the `FRAMESET` and `FRAME` tags, which create fixed windows.</span></span>  
  
 <span data-ttu-id="40a65-107">-nebo-</span><span class="sxs-lookup"><span data-stu-id="40a65-107">-or-</span></span>  
  
-   <span data-ttu-id="40a65-108">Pomocí `IFRAME` značku, která vytvoří plovoucího okna, které můžete změnit jejich umístění v době běhu.</span><span class="sxs-lookup"><span data-stu-id="40a65-108">Using the `IFRAME` tag, which creates a floating window that can be repositioned at run time.</span></span>  
  
1.  <span data-ttu-id="40a65-109">Protože snímky obsahují dokumenty ve formátu HTML, jsou reprezentovány jako prvků okna a rámce elementy v objektu modelu dokumentu (DOM).</span><span class="sxs-lookup"><span data-stu-id="40a65-109">Because frames contain HTML documents, they are represented in the Document Object Model (DOM) as both window elements and frame elements.</span></span>  
  
2.  <span data-ttu-id="40a65-110">Při přístupu `FRAME` nebo `IFRAME` značky pomocí kolekce rámce <xref:System.Windows.Forms.HtmlWindow>, jsou načítání prvku okno odpovídající rámečku.</span><span class="sxs-lookup"><span data-stu-id="40a65-110">When you access a `FRAME` or `IFRAME` tag by using the Frames collection of <xref:System.Windows.Forms.HtmlWindow>, you are retrieving the window element corresponding to the frame.</span></span> <span data-ttu-id="40a65-111">Reprezentuje všechny dynamických vlastností rámečku, například jeho aktuální adresu URL, dokumentů a velikost.</span><span class="sxs-lookup"><span data-stu-id="40a65-111">This represents all of the frame's dynamic properties, such as its current URL, document, and size.</span></span>  
  
3.  <span data-ttu-id="40a65-112">Při přístupu `FRAME` nebo `IFRAME` značky pomocí <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> vlastnost <xref:System.Windows.Forms.HtmlWindow>, <xref:System.Windows.Forms.HtmlElement.Children%2A> kolekce nebo metody, jako <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> nebo <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, jsou načítání rámce elementu.</span><span class="sxs-lookup"><span data-stu-id="40a65-112">When you access a `FRAME` or `IFRAME` tag by using the <xref:System.Windows.Forms.HtmlWindow.WindowFrameElement%2A> property of <xref:System.Windows.Forms.HtmlWindow>, the <xref:System.Windows.Forms.HtmlElement.Children%2A> collection, or methods such as <xref:System.Windows.Forms.HtmlElementCollection.GetElementsByName%2A> or <xref:System.Windows.Forms.HtmlDocument.GetElementById%2A>, you are retrieving the frame element.</span></span> <span data-ttu-id="40a65-113">To představuje statické vlastnosti rámečku, včetně adresa URL zadaná v původní soubor HTML.</span><span class="sxs-lookup"><span data-stu-id="40a65-113">This represents the static properties of the frame, including the URL specified in the original HTML file.</span></span>  
  
## <a name="frames-and-security"></a><span data-ttu-id="40a65-114">Rámce a zabezpečení</span><span class="sxs-lookup"><span data-stu-id="40a65-114">Frames and Security</span></span>  
 <span data-ttu-id="40a65-115">Přístup k rámce ztěžuje fakt, že spravovaný model HTML DOM implementuje bezpečnostní opatření známé jako *mezi rámci skriptování zabezpečení*.</span><span class="sxs-lookup"><span data-stu-id="40a65-115">Access to frames is complicated by the fact that the managed HTML DOM implements a security measure known as *cross-frame scripting security*.</span></span> <span data-ttu-id="40a65-116">Pokud dokument obsahuje `FRAMESET` s dvěma nebo více `FRAME`s v různých doménách, tyto `FRAME`nemůžou komunikovat s sebou.</span><span class="sxs-lookup"><span data-stu-id="40a65-116">If a document contains a `FRAMESET` with two or more `FRAME`s in different domains, these `FRAME`s cannot interact with one another.</span></span> <span data-ttu-id="40a65-117">Jinými slovy `FRAME` , zobrazí obsah webového serveru nelze přistupovat k informacím v `FRAME` , který hostuje server třetí strany, jako je například http://www.adatum.com/.</span><span class="sxs-lookup"><span data-stu-id="40a65-117">In other words, a `FRAME` that displays content from your Web site cannot access information in a `FRAME` that hosts a third-party site such as http://www.adatum.com/.</span></span> <span data-ttu-id="40a65-118">Je implementována tato zabezpečení na úrovni <xref:System.Windows.Forms.HtmlWindow> třídy.</span><span class="sxs-lookup"><span data-stu-id="40a65-118">This security is implemented at the level of the <xref:System.Windows.Forms.HtmlWindow> class.</span></span> <span data-ttu-id="40a65-119">Můžete získat obecné informace o `FRAME` hostování jiný web, jako je například jeho adresa URL, ale bude mít přístup k jeho <xref:System.Windows.Forms.HtmlWindow.Document%2A> nebo změna velikosti či umístění jeho hostování `FRAME` nebo `IFRAME`.</span><span class="sxs-lookup"><span data-stu-id="40a65-119">You can obtain general information about a `FRAME` hosting another Web site, such as its URL, but you will be unable to access its <xref:System.Windows.Forms.HtmlWindow.Document%2A> or change the size or location of its hosting `FRAME` or `IFRAME`.</span></span>  
  
 <span data-ttu-id="40a65-120">Toto pravidlo platí také pro windows, které můžete otevřít pomocí <xref:System.Windows.Forms.HtmlWindow.Open%2A> a <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="40a65-120">This rule also applies to windows that you open using the <xref:System.Windows.Forms.HtmlWindow.Open%2A> and <xref:System.Windows.Forms.HtmlWindow.OpenNew%2A> methods.</span></span> <span data-ttu-id="40a65-121">Pokud je okno otevření v jiné doméně ze stránky hostované v <xref:System.Windows.Forms.WebBrowser> řízení, nebudete moct přesouvat toto okno a zkontrolujte jeho obsah.</span><span class="sxs-lookup"><span data-stu-id="40a65-121">If the window you open is in a different domain from the page hosted in the <xref:System.Windows.Forms.WebBrowser> control, you will not be able to move that window or examine its contents.</span></span> <span data-ttu-id="40a65-122">Tyto vynutí se omezení taky Pokud použijete <xref:System.Windows.Forms.WebBrowser> ovládací prvek zobrazí web, který se liší od webu použít k nasazení aplikace na základě formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="40a65-122">These restrictions are also enforced if you use the <xref:System.Windows.Forms.WebBrowser> control to display a Web site that is different from the Web site used to deploy your Windows Forms-based application.</span></span> <span data-ttu-id="40a65-123">Pokud používáte [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] použít technologii nasazení k instalaci aplikace z webu A a <xref:System.Windows.Forms.WebBrowser> zobrazíte webový server B, nebude možné k datům přístup k webu pro B.</span><span class="sxs-lookup"><span data-stu-id="40a65-123">If you use [!INCLUDE[ndptecclick](../../../../includes/ndptecclick-md.md)] deployment technology to install your application from Web site A, and you use the <xref:System.Windows.Forms.WebBrowser> to display Web site B, you will not be able to access Web site B's data.</span></span>  
  
 <span data-ttu-id="40a65-124">Další informace o skriptování najdete v tématu[o skriptování mezi rámci a zabezpečení](http://msdn.microsoft.com/library/ms533028.aspx).</span><span class="sxs-lookup"><span data-stu-id="40a65-124">For more information about cross-site scripting, see[About Cross-Frame Scripting and Security](http://msdn.microsoft.com/library/ms533028.aspx).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="40a65-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="40a65-125">See Also</span></span>  
 [<span data-ttu-id="40a65-126">Element rámce &#124; Objekt s rámečkem</span><span class="sxs-lookup"><span data-stu-id="40a65-126">FRAME Element &#124; frame Object</span></span>](http://msdn.microsoft.com/library/ms535250.aspx)  
 [<span data-ttu-id="40a65-127">Pomocí modelu objektu spravovaného dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="40a65-127">Using the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/using-the-managed-html-document-object-model.md)
