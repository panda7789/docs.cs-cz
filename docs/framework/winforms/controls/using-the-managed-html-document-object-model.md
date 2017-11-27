---
title: "Použití modelu spravovaného objektu dokumentu HTML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: managed HTML DOM
ms.assetid: a017dd5c-cd7b-47e4-952c-f4f54cb48409
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ff1004248e709b4b4913b90eb81f0726ab390c54
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-the-managed-html-document-object-model"></a><span data-ttu-id="f1069-102">Použití modelu spravovaného objektu dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="f1069-102">Using the Managed HTML Document Object Model</span></span>
<span data-ttu-id="f1069-103">Spravovaný model objektu dokumentu HTML (DOM) poskytuje obálku na základě [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pro třídy HTML vystavené Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f1069-103">The managed HTML document object model (DOM) provides a wrapper based on the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] for the HTML classes exposed by Internet Explorer.</span></span> <span data-ttu-id="f1069-104">Použít k manipulaci s stránky HTML, které jsou hostované v těchto tříd <xref:System.Windows.Forms.WebBrowser> ovládací prvek, nebo vytvářet nové stránky od začátku.</span><span class="sxs-lookup"><span data-stu-id="f1069-104">Use these classes to manipulate HTML pages hosted in the <xref:System.Windows.Forms.WebBrowser> control, or to build new pages from the beginning.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="f1069-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f1069-105">In This Section</span></span>  
 [<span data-ttu-id="f1069-106">Postupy: přístup k modelu objektu spravovaného dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="f1069-106">How to: Access the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-access-the-managed-html-document-object-model.md)  
 <span data-ttu-id="f1069-107">Popisuje, jak získat platnou instanci systému <xref:System.Windows.Forms.HtmlDocument> z aplikace Windows Forms nebo <xref:System.Windows.Forms.UserControl> hostované v aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="f1069-107">Describes how to obtain a valid instance of <xref:System.Windows.Forms.HtmlDocument> from either a Windows Forms application or a <xref:System.Windows.Forms.UserControl> hosted in Internet Explorer.</span></span>  
  
 [<span data-ttu-id="f1069-108">Postupy: přístup ke zdroji HTML v modelu objektu spravovaného dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="f1069-108">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-access-the-html-source-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="f1069-109">Popisuje, jak získat zdroji HTML původní, beze změny a jak získat zdroji "živé", která odráží aktuální stav modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="f1069-109">Describes how to obtain the original, unmodified HTML source, and how to obtain the "live" source that reflects the current state of the DOM.</span></span>  
  
 [<span data-ttu-id="f1069-110">Postupy: Změna stylů v elementu v modelu objektu spravovaného dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="f1069-110">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-change-styles-on-an-element-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="f1069-111">Popisuje, jak k manipulaci se styly, které jsou používány k ovládání visual zobrazení prvků.</span><span class="sxs-lookup"><span data-stu-id="f1069-111">Describes how to manipulate styles, which are used to control the visual display of elements.</span></span>  
  
 [<span data-ttu-id="f1069-112">Přístup k rámcům v modelu objektu spravovaného dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="f1069-112">Accessing Frames in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/accessing-frames-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="f1069-113">Popisuje, co jsou rámce a sady rámců a jak přistupovat k modelu DOM rámečku.</span><span class="sxs-lookup"><span data-stu-id="f1069-113">Describes what frames and framesets are, and how to access the DOM of a frame.</span></span>  
  
 [<span data-ttu-id="f1069-114">Přístup k Nevystaveným členům v modelu objektu spravovaného dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="f1069-114">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/accessing-unexposed-members-on-the-managed-html-document-object-model.md)  
 <span data-ttu-id="f1069-115">Popisuje, jak přístup ke členům základní DOM, které nemají spravované ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="f1069-115">Describes how to access members of the underlying DOM that do not have a managed equivalent.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="f1069-116">Odkaz</span><span class="sxs-lookup"><span data-stu-id="f1069-116">Reference</span></span>  
 <xref:System.Windows.Forms.HtmlDocument>  
  
 <xref:System.Windows.Forms.HtmlElement>  
  
 <xref:System.Windows.Forms.HtmlWindow>  
  
## <a name="related-sections"></a><span data-ttu-id="f1069-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="f1069-117">Related Sections</span></span>  
 [<span data-ttu-id="f1069-118">WebBrowser – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="f1069-118">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
  
## <a name="see-also"></a><span data-ttu-id="f1069-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1069-119">See Also</span></span>  
 [<span data-ttu-id="f1069-120">O objektový Model DHTML</span><span class="sxs-lookup"><span data-stu-id="f1069-120">About the DHTML Object Model</span></span>](http://msdn.microsoft.com/library/default.asp?url=/workshop/author/om/doc_object.asp)
