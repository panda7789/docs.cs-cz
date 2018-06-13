---
title: Použití modelu spravovaného objektu dokumentu HTML
ms.date: 03/30/2017
helpviewer_keywords:
- managed HTML DOM
ms.assetid: a017dd5c-cd7b-47e4-952c-f4f54cb48409
ms.openlocfilehash: 95b14ae455ef8fcd0a81decec21b8305f2573643
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33535948"
---
# <a name="using-the-managed-html-document-object-model"></a><span data-ttu-id="3af85-102">Použití modelu spravovaného objektu dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="3af85-102">Using the Managed HTML Document Object Model</span></span>
<span data-ttu-id="3af85-103">Spravovaný model objektu dokumentu HTML (DOM) poskytuje obálku na základě [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pro třídy HTML vystavené Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="3af85-103">The managed HTML document object model (DOM) provides a wrapper based on the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] for the HTML classes exposed by Internet Explorer.</span></span> <span data-ttu-id="3af85-104">Použít k manipulaci s stránky HTML, které jsou hostované v těchto tříd <xref:System.Windows.Forms.WebBrowser> ovládací prvek, nebo vytvářet nové stránky od začátku.</span><span class="sxs-lookup"><span data-stu-id="3af85-104">Use these classes to manipulate HTML pages hosted in the <xref:System.Windows.Forms.WebBrowser> control, or to build new pages from the beginning.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3af85-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3af85-105">In This Section</span></span>  
 [<span data-ttu-id="3af85-106">Postupy: Přístup ke spravovanému modelu DOM (Document Object Model) HTML</span><span class="sxs-lookup"><span data-stu-id="3af85-106">How to: Access the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-access-the-managed-html-document-object-model.md)  
 <span data-ttu-id="3af85-107">Popisuje, jak získat platnou instanci systému <xref:System.Windows.Forms.HtmlDocument> z aplikace Windows Forms nebo <xref:System.Windows.Forms.UserControl> hostované v aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="3af85-107">Describes how to obtain a valid instance of <xref:System.Windows.Forms.HtmlDocument> from either a Windows Forms application or a <xref:System.Windows.Forms.UserControl> hosted in Internet Explorer.</span></span>  
  
 [<span data-ttu-id="3af85-108">Postupy: Přístup ke zdroji HTML ve spravovaném modelu DOM (Document Object Model) HTML</span><span class="sxs-lookup"><span data-stu-id="3af85-108">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-access-the-html-source-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="3af85-109">Popisuje, jak získat zdroji HTML původní, beze změny a jak získat zdroji "živé", která odráží aktuální stav modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="3af85-109">Describes how to obtain the original, unmodified HTML source, and how to obtain the "live" source that reflects the current state of the DOM.</span></span>  
  
 [<span data-ttu-id="3af85-110">Postupy: Změna stylů v elementu ve spravovaném modelu DOM (Document Object Model) HTML</span><span class="sxs-lookup"><span data-stu-id="3af85-110">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/how-to-change-styles-on-an-element-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="3af85-111">Popisuje, jak k manipulaci se styly, které jsou používány k ovládání visual zobrazení prvků.</span><span class="sxs-lookup"><span data-stu-id="3af85-111">Describes how to manipulate styles, which are used to control the visual display of elements.</span></span>  
  
 [<span data-ttu-id="3af85-112">Přístup k rámcům ve spravovaném modelu DOM (Document Object Model) HTML</span><span class="sxs-lookup"><span data-stu-id="3af85-112">Accessing Frames in the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/accessing-frames-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="3af85-113">Popisuje, co jsou rámce a sady rámců a jak přistupovat k modelu DOM rámečku.</span><span class="sxs-lookup"><span data-stu-id="3af85-113">Describes what frames and framesets are, and how to access the DOM of a frame.</span></span>  
  
 [<span data-ttu-id="3af85-114">Přístup k nevystaveným členům ve spravovaném modelu DOM (Document Object Model) HTML</span><span class="sxs-lookup"><span data-stu-id="3af85-114">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>](../../../../docs/framework/winforms/controls/accessing-unexposed-members-on-the-managed-html-document-object-model.md)  
 <span data-ttu-id="3af85-115">Popisuje, jak přístup ke členům základní DOM, které nemají spravované ekvivalent.</span><span class="sxs-lookup"><span data-stu-id="3af85-115">Describes how to access members of the underlying DOM that do not have a managed equivalent.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="3af85-116">Odkaz</span><span class="sxs-lookup"><span data-stu-id="3af85-116">Reference</span></span>  
 <xref:System.Windows.Forms.HtmlDocument>  
  
 <xref:System.Windows.Forms.HtmlElement>  
  
 <xref:System.Windows.Forms.HtmlWindow>  
  
## <a name="related-sections"></a><span data-ttu-id="3af85-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3af85-117">Related Sections</span></span>  
 [<span data-ttu-id="3af85-118">Ovládací prvek WebBrowser</span><span class="sxs-lookup"><span data-stu-id="3af85-118">WebBrowser Control</span></span>](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)  
  
## <a name="see-also"></a><span data-ttu-id="3af85-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="3af85-119">See Also</span></span>  
 [<span data-ttu-id="3af85-120">O objektový Model DHTML</span><span class="sxs-lookup"><span data-stu-id="3af85-120">About the DHTML Object Model</span></span>](http://msdn.microsoft.com/library/default.asp?url=/workshop/author/om/doc_object.asp)
