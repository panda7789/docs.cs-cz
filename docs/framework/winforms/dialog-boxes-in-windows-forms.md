---
title: "Dialogová okna ve Windows Forms"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- dialog boxes [Windows Forms], Windows Forms
- Windows Forms dialog boxes
- dialogs [Windows Forms], using in Windows Forms
ms.assetid: d43d022b-451b-490d-9386-dc79d98fbf8a
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1660bf08f10a7d4e0db4b7ae8d58fd631986974c
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="dialog-boxes-in-windows-forms"></a><span data-ttu-id="3a439-102">Dialogová okna ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3a439-102">Dialog Boxes in Windows Forms</span></span>
<span data-ttu-id="3a439-103">Dialogová okna se používají k interakci s uživatelem a načíst informace.</span><span class="sxs-lookup"><span data-stu-id="3a439-103">Dialog boxes are used to interact with the user and retrieve information.</span></span> <span data-ttu-id="3a439-104">Jednoduše řečeno, dialogové okno je formulář se jeho <xref:System.Windows.Forms.FormBorderStyle> výčet vlastností nastavenou na `FixedDialog`.</span><span class="sxs-lookup"><span data-stu-id="3a439-104">In simple terms, a dialog box is a form with its <xref:System.Windows.Forms.FormBorderStyle> enumeration property set to `FixedDialog`.</span></span> <span data-ttu-id="3a439-105">Můžete vytvořit vlastní vlastní dialogových oken pomocí Windows Forms designerem v [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span><span class="sxs-lookup"><span data-stu-id="3a439-105">You can construct your own custom dialog boxes by using the Windows Forms Designer in [!INCLUDE[vsprvs](../../../includes/vsprvs-md.md)].</span></span> <span data-ttu-id="3a439-106">Přidání ovládacích prvků, jako `Label`, `Textbox`, a `Button` přizpůsobit dialogová okna vašim konkrétním potřebám.</span><span class="sxs-lookup"><span data-stu-id="3a439-106">Add controls such as `Label`, `Textbox`, and `Button` to customize dialog boxes to your specific needs.</span></span> <span data-ttu-id="3a439-107">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Také obsahuje předdefinovaných dialogových oken, jako například **otevřít soubor** a okna zpráv, které můžete přizpůsobit pro vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="3a439-107">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also includes predefined dialog boxes, such as **File Open** and message boxes, which you can adapt for your own applications.</span></span> <span data-ttu-id="3a439-108">Další informace najdete v tématu [– dialogové okno Ovládací prvky a součásti](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="3a439-108">For more information, see [Dialog-Box Controls and Components](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="3a439-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="3a439-109">In This Section</span></span>  
 [<span data-ttu-id="3a439-110">Postupy: zobrazování dialogových oken pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3a439-110">How to: Display Dialog Boxes for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-display-dialog-boxes-for-windows-forms.md)  
 <span data-ttu-id="3a439-111">Poskytuje pokyny pro zobrazení dialogových oken.</span><span class="sxs-lookup"><span data-stu-id="3a439-111">Gives directions for showing dialog boxes.</span></span>  
  
-   <span data-ttu-id="3a439-112">[Postupy: načtení informací o dialogové okno pole selektivně pomocí více vlastností](http://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3a439-112">[How to: Retrieve Dialog Box Information Selectively Using Multiple Properties](http://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3a439-113">[Postupy: načtení informací z nadřazené formuláře dialogového okna](http://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3a439-113">[How to: Retrieve Information from the Parent Form of a Dialog Box](http://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3a439-114">[Uživatelský vstup do dialogových oken](http://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3a439-114">[User Input to Dialog Boxes](http://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3a439-115">[Postupy: načtení výsledek pro dialogová okna](http://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3a439-115">[How to: Retrieve the Result for Dialog Boxes](http://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3a439-116">[Návod: Načtení informací dialogové okno pole souhrnně pomocí objektů](http://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3a439-116">[Walkthrough: Retrieving Dialog Box Information Collectively Using Objects](http://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3a439-117">[Postupy: zavřete dialogová okna a zachovat uživatelský vstup](http://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3a439-117">[How to: Close Dialog Boxes and Retain User Input](http://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3a439-118">[Postupy: vytvoření dialogová okna v době návrhu](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3a439-118">[How to: Create Dialog Boxes at Design Time](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="3a439-119">[Postupy: zobrazení oken zpráv](http://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="3a439-119">[How to: Display Message Boxes](http://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="3a439-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="3a439-120">Related Sections</span></span>  
 [<span data-ttu-id="3a439-121">Dialogové okno – Ovládací prvky a součásti</span><span class="sxs-lookup"><span data-stu-id="3a439-121">Dialog-Box Controls and Components</span></span>](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 <span data-ttu-id="3a439-122">Zobrazí ovládací prvky předdefinované dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="3a439-122">Lists the predefined dialog box controls.</span></span>  
  
 [<span data-ttu-id="3a439-123">Změna vzhledu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="3a439-123">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 <span data-ttu-id="3a439-124">Obsahuje odkazy na témata, které popisují, jak změnit vzhled v aplikacích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3a439-124">Contains links to topics that describe how to change the appearance of Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="3a439-125">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="3a439-125">TabControl Control Overview</span></span>](../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="3a439-126">Vysvětluje, jak začlenit ovládacího prvku karta do dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="3a439-126">Explains how you incorporate the tab control into a dialog box.</span></span>
