---
title: Dialogová okna ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- dialog boxes [Windows Forms], Windows Forms
- Windows Forms dialog boxes
- dialogs [Windows Forms], using in Windows Forms
ms.assetid: d43d022b-451b-490d-9386-dc79d98fbf8a
ms.openlocfilehash: 302e59c607f179869bcf3923c3092e73a1eddc91
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539900"
---
# <a name="dialog-boxes-in-windows-forms"></a><span data-ttu-id="0d25a-102">Dialogová okna ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d25a-102">Dialog Boxes in Windows Forms</span></span>
<span data-ttu-id="0d25a-103">Dialogová okna se používají k interakci s uživatelem a načíst informace.</span><span class="sxs-lookup"><span data-stu-id="0d25a-103">Dialog boxes are used to interact with the user and retrieve information.</span></span> <span data-ttu-id="0d25a-104">Jednoduše řečeno, dialogové okno je formulář se jeho <xref:System.Windows.Forms.FormBorderStyle> výčet vlastností nastavenou na `FixedDialog`.</span><span class="sxs-lookup"><span data-stu-id="0d25a-104">In simple terms, a dialog box is a form with its <xref:System.Windows.Forms.FormBorderStyle> enumeration property set to `FixedDialog`.</span></span> <span data-ttu-id="0d25a-105">Pomocí Windows Forms designerem v sadě Visual Studio můžete vytvořit vlastní vlastní dialogová okna.</span><span class="sxs-lookup"><span data-stu-id="0d25a-105">You can construct your own custom dialog boxes by using the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="0d25a-106">Přidání ovládacích prvků, jako `Label`, `Textbox`, a `Button` přizpůsobit dialogová okna vašim konkrétním potřebám.</span><span class="sxs-lookup"><span data-stu-id="0d25a-106">Add controls such as `Label`, `Textbox`, and `Button` to customize dialog boxes to your specific needs.</span></span> <span data-ttu-id="0d25a-107">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Také obsahuje předdefinovaných dialogových oken, jako například **otevřít soubor** a okna zpráv, které můžete přizpůsobit pro vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d25a-107">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also includes predefined dialog boxes, such as **File Open** and message boxes, which you can adapt for your own applications.</span></span> <span data-ttu-id="0d25a-108">Další informace najdete v tématu [– dialogové okno Ovládací prvky a součásti](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="0d25a-108">For more information, see [Dialog-Box Controls and Components](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="0d25a-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="0d25a-109">In This Section</span></span>  
 [<span data-ttu-id="0d25a-110">Postupy: Zobrazování dialogových oken pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d25a-110">How to: Display Dialog Boxes for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-display-dialog-boxes-for-windows-forms.md)  
 <span data-ttu-id="0d25a-111">Poskytuje pokyny pro zobrazení dialogových oken.</span><span class="sxs-lookup"><span data-stu-id="0d25a-111">Gives directions for showing dialog boxes.</span></span>  
  
-   <span data-ttu-id="0d25a-112">[Postupy: načtení informací o dialogové okno pole selektivně pomocí více vlastností](http://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0d25a-112">[How to: Retrieve Dialog Box Information Selectively Using Multiple Properties](http://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="0d25a-113">[Postupy: načtení informací z nadřazené formuláře dialogového okna](http://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0d25a-113">[How to: Retrieve Information from the Parent Form of a Dialog Box](http://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="0d25a-114">[Uživatelský vstup do dialogových oken](http://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0d25a-114">[User Input to Dialog Boxes](http://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="0d25a-115">[Postupy: načtení výsledek pro dialogová okna](http://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0d25a-115">[How to: Retrieve the Result for Dialog Boxes](http://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="0d25a-116">[Návod: Načtení informací dialogové okno pole souhrnně pomocí objektů](http://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0d25a-116">[Walkthrough: Retrieving Dialog Box Information Collectively Using Objects](http://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="0d25a-117">[Postupy: zavřete dialogová okna a zachovat uživatelský vstup](http://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0d25a-117">[How to: Close Dialog Boxes and Retain User Input](http://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="0d25a-118">[Postupy: vytvoření dialogová okna v době návrhu](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0d25a-118">[How to: Create Dialog Boxes at Design Time](http://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="0d25a-119">[Postupy: zobrazení oken zpráv](http://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="0d25a-119">[How to: Display Message Boxes](http://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="0d25a-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="0d25a-120">Related Sections</span></span>  
 [<span data-ttu-id="0d25a-121">Ovládací prvky a součásti dialogového okna</span><span class="sxs-lookup"><span data-stu-id="0d25a-121">Dialog-Box Controls and Components</span></span>](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 <span data-ttu-id="0d25a-122">Zobrazí ovládací prvky předdefinované dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="0d25a-122">Lists the predefined dialog box controls.</span></span>  
  
 [<span data-ttu-id="0d25a-123">Změna vzhledu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="0d25a-123">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 <span data-ttu-id="0d25a-124">Obsahuje odkazy na témata, které popisují, jak změnit vzhled v aplikacích Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="0d25a-124">Contains links to topics that describe how to change the appearance of Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="0d25a-125">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="0d25a-125">TabControl Control Overview</span></span>](../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="0d25a-126">Vysvětluje, jak začlenit ovládacího prvku karta do dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="0d25a-126">Explains how you incorporate the tab control into a dialog box.</span></span>
