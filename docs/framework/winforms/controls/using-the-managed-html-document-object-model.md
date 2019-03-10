---
title: Použití modelu spravovaného objektu dokumentu HTML
ms.date: 03/30/2017
helpviewer_keywords:
- managed HTML DOM
ms.assetid: a017dd5c-cd7b-47e4-952c-f4f54cb48409
ms.openlocfilehash: c18c6df29f79e9bde8474fa38e45dea03d4e0020
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57721898"
---
# <a name="using-the-managed-html-document-object-model"></a><span data-ttu-id="4bad0-102">Použití modelu spravovaného objektu dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="4bad0-102">Using the Managed HTML Document Object Model</span></span>
<span data-ttu-id="4bad0-103">Spravovaný model (DOM) objektu dokumentu HTML poskytuje obálku na základě [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] pro třídy HTML vystavené aplikace Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="4bad0-103">The managed HTML document object model (DOM) provides a wrapper based on the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] for the HTML classes exposed by Internet Explorer.</span></span> <span data-ttu-id="4bad0-104">Použít tyto třídy manipulovat s HTML stránek hostovaných v <xref:System.Windows.Forms.WebBrowser> ovládacího prvku, nebo vytvářet nové stránky od začátku.</span><span class="sxs-lookup"><span data-stu-id="4bad0-104">Use these classes to manipulate HTML pages hosted in the <xref:System.Windows.Forms.WebBrowser> control, or to build new pages from the beginning.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="4bad0-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="4bad0-105">In This Section</span></span>  
 [<span data-ttu-id="4bad0-106">Postupy: Přístup k modelu objektu spravovaného dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="4bad0-106">How to: Access the Managed HTML Document Object Model</span></span>](how-to-access-the-managed-html-document-object-model.md)  
 <span data-ttu-id="4bad0-107">Popisuje, jak získat platnou instanci <xref:System.Windows.Forms.HtmlDocument> z aplikace Windows Forms nebo <xref:System.Windows.Forms.UserControl> hostované v aplikaci Internet Explorer.</span><span class="sxs-lookup"><span data-stu-id="4bad0-107">Describes how to obtain a valid instance of <xref:System.Windows.Forms.HtmlDocument> from either a Windows Forms application or a <xref:System.Windows.Forms.UserControl> hosted in Internet Explorer.</span></span>  
  
 [<span data-ttu-id="4bad0-108">Postupy: Přístup ke zdroji HTML v objektovém modelu spravovaného dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="4bad0-108">How to: Access the HTML Source in the Managed HTML Document Object Model</span></span>](how-to-access-the-html-source-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="4bad0-109">Popisuje, jak získat zdrojový kód HTML původní, bez úprav a tom, jak získat zdroje "živé", který odráží aktuální stav modelu DOM.</span><span class="sxs-lookup"><span data-stu-id="4bad0-109">Describes how to obtain the original, unmodified HTML source, and how to obtain the "live" source that reflects the current state of the DOM.</span></span>  
  
 [<span data-ttu-id="4bad0-110">Postupy: Změna stylů v elementu v modelu objektu spravovaného dokumentu HTML</span><span class="sxs-lookup"><span data-stu-id="4bad0-110">How to: Change Styles on an Element in the Managed HTML Document Object Model</span></span>](how-to-change-styles-on-an-element-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="4bad0-111">Popisuje, jak pracovat s styly, které se používají k řízení vizuální zobrazení elementů.</span><span class="sxs-lookup"><span data-stu-id="4bad0-111">Describes how to manipulate styles, which are used to control the visual display of elements.</span></span>  
  
 [<span data-ttu-id="4bad0-112">Přístup k rámcům ve spravovaném modelu DOM (Document Object Model) HTML</span><span class="sxs-lookup"><span data-stu-id="4bad0-112">Accessing Frames in the Managed HTML Document Object Model</span></span>](accessing-frames-in-the-managed-html-document-object-model.md)  
 <span data-ttu-id="4bad0-113">Popisuje, co jsou snímky a sady rámců a jak získat přístup k modelu DOM rámce.</span><span class="sxs-lookup"><span data-stu-id="4bad0-113">Describes what frames and framesets are, and how to access the DOM of a frame.</span></span>  
  
 [<span data-ttu-id="4bad0-114">Přístup k nevystaveným členům ve spravovaném modelu DOM (Document Object Model) HTML</span><span class="sxs-lookup"><span data-stu-id="4bad0-114">Accessing Unexposed Members on the Managed HTML Document Object Model</span></span>](accessing-unexposed-members-on-the-managed-html-document-object-model.md)  
 <span data-ttu-id="4bad0-115">Popisuje, jak pro přístup ke členům základní modelu DOM, které nemají ekvivalent spravované.</span><span class="sxs-lookup"><span data-stu-id="4bad0-115">Describes how to access members of the underlying DOM that do not have a managed equivalent.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="4bad0-116">Odkaz</span><span class="sxs-lookup"><span data-stu-id="4bad0-116">Reference</span></span>  
 <xref:System.Windows.Forms.HtmlDocument>  
  
 <xref:System.Windows.Forms.HtmlElement>  
  
 <xref:System.Windows.Forms.HtmlWindow>  
  
## <a name="related-sections"></a><span data-ttu-id="4bad0-117">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="4bad0-117">Related Sections</span></span>  
 [<span data-ttu-id="4bad0-118">Ovládací prvek WebBrowser</span><span class="sxs-lookup"><span data-stu-id="4bad0-118">WebBrowser Control</span></span>](webbrowser-control-windows-forms.md)  
