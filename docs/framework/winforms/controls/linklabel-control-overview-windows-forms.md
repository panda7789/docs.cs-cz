---
title: "LinkLabel – přehled ovládacího prvku (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: LinkLabel
helpviewer_keywords:
- links [Windows Forms], LinkLabel control
- Label control [Windows Forms], about Label control
- LinkLabel control [Windows Forms], about LinkLabel control
ms.assetid: 9e248549-10ca-43a3-bb5e-60f583d369f1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0cb01c0fc5503a5bf16e1f191d87ae90907ec816
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="linklabel-control-overview-windows-forms"></a><span data-ttu-id="a0a4e-102">LinkLabel – přehled ovládacího prvku (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="a0a4e-102">LinkLabel Control Overview (Windows Forms)</span></span>
<span data-ttu-id="a0a4e-103">Windows Forms <xref:System.Windows.Forms.LinkLabel> řízení umožňuje přidat webových odkazů do formulářové aplikace Windows.</span><span class="sxs-lookup"><span data-stu-id="a0a4e-103">The Windows Forms <xref:System.Windows.Forms.LinkLabel> control allows you to add Web-style links to Windows Forms applications.</span></span> <span data-ttu-id="a0a4e-104">Můžete použít <xref:System.Windows.Forms.LinkLabel> řízení pro všechno, který můžete použít <xref:System.Windows.Forms.Label> řízení pro; můžete také nastavit část textu jako odkaz na soubor, složku nebo webové stránky.</span><span class="sxs-lookup"><span data-stu-id="a0a4e-104">You can use the <xref:System.Windows.Forms.LinkLabel> control for everything that you can use the <xref:System.Windows.Forms.Label> control for; you also can set part of the text as a link to a file, folder, or Web page.</span></span>  
  
## <a name="what-you-can-do-with-the-linklabel-control"></a><span data-ttu-id="a0a4e-105">Co můžete dělat s linklabel – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="a0a4e-105">What You Can Do with the LinkLabel Control</span></span>  
 <span data-ttu-id="a0a4e-106">Kromě všech vlastností, metod a události <xref:System.Windows.Forms.Label> ovládací prvek, <xref:System.Windows.Forms.LinkLabel> ovládací prvek má vlastnosti hypertextových odkazů a barvy propojení.</span><span class="sxs-lookup"><span data-stu-id="a0a4e-106">In addition to all the properties, methods, and events of the <xref:System.Windows.Forms.Label> control, the <xref:System.Windows.Forms.LinkLabel> control has properties for hyperlinks and link colors.</span></span> <span data-ttu-id="a0a4e-107"><xref:System.Windows.Forms.LinkLabel.LinkArea%2A> Vlastnost nastaví oblasti text, který aktivuje odkaz.</span><span class="sxs-lookup"><span data-stu-id="a0a4e-107">The <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property sets the area of the text that activates the link.</span></span> <span data-ttu-id="a0a4e-108"><xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, A <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> vlastnosti nastavit barvy propojení.</span><span class="sxs-lookup"><span data-stu-id="a0a4e-108">The <xref:System.Windows.Forms.LinkLabel.LinkColor%2A>, <xref:System.Windows.Forms.LinkLabel.VisitedLinkColor%2A>, and <xref:System.Windows.Forms.LinkLabel.ActiveLinkColor%2A> properties set the colors of the link.</span></span> <span data-ttu-id="a0a4e-109"><xref:System.Windows.Forms.LinkLabel.LinkClicked> Událostí určuje, co se stane, když je vybraný text odkazu.</span><span class="sxs-lookup"><span data-stu-id="a0a4e-109">The <xref:System.Windows.Forms.LinkLabel.LinkClicked> event determines what happens when the link text is selected.</span></span>  
  
 <span data-ttu-id="a0a4e-110">Nejjednodušší použití <xref:System.Windows.Forms.LinkLabel> ovládací prvek, je zobrazit odkaz pomocí <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> vlastnost, ale můžete také zobrazit více hypertextových odkazů pomocí <xref:System.Windows.Forms.LinkLabel.Links%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="a0a4e-110">The simplest use of the <xref:System.Windows.Forms.LinkLabel> control is to display a single link using the <xref:System.Windows.Forms.LinkLabel.LinkArea%2A> property, but you can also display multiple hyperlinks using the <xref:System.Windows.Forms.LinkLabel.Links%2A> property.</span></span> <span data-ttu-id="a0a4e-111"><xref:System.Windows.Forms.LinkLabel.Links%2A> Vlastnost umožňuje přístup ke kolekci odkazů.</span><span class="sxs-lookup"><span data-stu-id="a0a4e-111">The <xref:System.Windows.Forms.LinkLabel.Links%2A> property enables you to access a collection of links.</span></span> <span data-ttu-id="a0a4e-112">Můžete také zadat data <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> vlastnosti každého uživatele <xref:System.Windows.Forms.LinkLabel.Link> objektu.</span><span class="sxs-lookup"><span data-stu-id="a0a4e-112">You can also specify data in the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property of each individual <xref:System.Windows.Forms.LinkLabel.Link> object.</span></span> <span data-ttu-id="a0a4e-113">Hodnota <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> vlastnost lze použít k uložení umístění souboru k zobrazení nebo adresu webu.</span><span class="sxs-lookup"><span data-stu-id="a0a4e-113">The value of the <xref:System.Windows.Forms.LinkLabel.Link.LinkData%2A> property can be used to store the location of a file to display or the address of a Web site.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0a4e-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="a0a4e-114">See Also</span></span>  
 <xref:System.Windows.Forms.LinkLabel>  
 [<span data-ttu-id="a0a4e-115">Přehled ovládacího prvku popisek</span><span class="sxs-lookup"><span data-stu-id="a0a4e-115">Label Control Overview</span></span>](../../../../docs/framework/winforms/controls/label-control-overview-windows-forms.md)  
 [<span data-ttu-id="a0a4e-116">Postupy: odkaz na objekt nebo webovou stránku pomocí ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="a0a4e-116">How to: Link to an Object or Web Page with the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/link-to-an-object-or-web-page-with-wf-linklabel-control.md)  
 [<span data-ttu-id="a0a4e-117">Postupy: Změna vzhledu ovládacího prvku Windows Forms LinkLabel</span><span class="sxs-lookup"><span data-stu-id="a0a4e-117">How to: Change the Appearance of the Windows Forms LinkLabel Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-appearance-of-the-windows-forms-linklabel-control.md)
