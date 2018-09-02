---
title: Dialogová okna ve Windows Forms
ms.date: 03/30/2017
helpviewer_keywords:
- dialog boxes [Windows Forms], Windows Forms
- Windows Forms dialog boxes
- dialogs [Windows Forms], using in Windows Forms
ms.assetid: d43d022b-451b-490d-9386-dc79d98fbf8a
ms.openlocfilehash: ef07c087ca43efaf99231453fcb56af0db24234a
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43387738"
---
# <a name="dialog-boxes-in-windows-forms"></a><span data-ttu-id="17464-102">Dialogová okna ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="17464-102">Dialog Boxes in Windows Forms</span></span>
<span data-ttu-id="17464-103">Dialogová okna se používají k interakci s uživatelem a načítání informací.</span><span class="sxs-lookup"><span data-stu-id="17464-103">Dialog boxes are used to interact with the user and retrieve information.</span></span> <span data-ttu-id="17464-104">Jednoduše řečeno, dialogové okno je formulář s jeho <xref:System.Windows.Forms.FormBorderStyle> výčet vlastností nastavenou na `FixedDialog`.</span><span class="sxs-lookup"><span data-stu-id="17464-104">In simple terms, a dialog box is a form with its <xref:System.Windows.Forms.FormBorderStyle> enumeration property set to `FixedDialog`.</span></span> <span data-ttu-id="17464-105">Můžete vytvořit vlastní vlastní dialogová okna pomocí Návrháře formulářů Windows v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="17464-105">You can construct your own custom dialog boxes by using the Windows Forms Designer in Visual Studio.</span></span> <span data-ttu-id="17464-106">Přidání ovládacích prvků, jako `Label`, `Textbox`, a `Button` přizpůsobení dialogových oknech vašim konkrétním potřebám.</span><span class="sxs-lookup"><span data-stu-id="17464-106">Add controls such as `Label`, `Textbox`, and `Button` to customize dialog boxes to your specific needs.</span></span> <span data-ttu-id="17464-107">[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Také obsahuje předdefinovaných dialogových oknech, jako například **otevřít soubor** a okna se zprávou, které můžete přizpůsobit pro vaše vlastní aplikace.</span><span class="sxs-lookup"><span data-stu-id="17464-107">The [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] also includes predefined dialog boxes, such as **File Open** and message boxes, which you can adapt for your own applications.</span></span> <span data-ttu-id="17464-108">Další informace najdete v tématu [dialogového okna ovládacích prvků a komponent](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="17464-108">For more information, see [Dialog-Box Controls and Components](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="17464-109">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="17464-109">In This Section</span></span>  
 [<span data-ttu-id="17464-110">Postupy: Zobrazování dialogových oken pro Windows Forms</span><span class="sxs-lookup"><span data-stu-id="17464-110">How to: Display Dialog Boxes for Windows Forms</span></span>](../../../docs/framework/winforms/how-to-display-dialog-boxes-for-windows-forms.md)  
 <span data-ttu-id="17464-111">Poskytuje pokyny pro zobrazování dialogových oknech.</span><span class="sxs-lookup"><span data-stu-id="17464-111">Gives directions for showing dialog boxes.</span></span>  
  
-   <span data-ttu-id="17464-112">[Postupy: načtení informací z dialogového okna selektivně pomocí více vlastností](https://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="17464-112">[How to: Retrieve Dialog Box Information Selectively Using Multiple Properties](https://msdn.microsoft.com/library/56taefba\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="17464-113">[Postupy: načtení informací z nadřízeného formuláře dialogového okna](https://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="17464-113">[How to: Retrieve Information from the Parent Form of a Dialog Box](https://msdn.microsoft.com/library/k70t19bb\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="17464-114">[Uživatelský vstup do dialogových oken](https://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="17464-114">[User Input to Dialog Boxes](https://msdn.microsoft.com/library/1s9ws53w\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="17464-115">[Postupy: načítání výsledku z dialogových oknech](https://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="17464-115">[How to: Retrieve the Result for Dialog Boxes](https://msdn.microsoft.com/library/40x40td1\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="17464-116">[Návod: Načtení informací z dialogového okna souhrnně pomocí objektů](https://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="17464-116">[Walkthrough: Retrieving Dialog Box Information Collectively Using Objects](https://msdn.microsoft.com/library/cakx2hdw\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="17464-117">[Postupy: Zavření dialogových oknech a zachování dat zadaných uživatelem](https://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="17464-117">[How to: Close Dialog Boxes and Retain User Input](https://msdn.microsoft.com/library/65ad5907\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="17464-118">[Postupy: vytváření dialogových oken během návrhu](https://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="17464-118">[How to: Create Dialog Boxes at Design Time](https://msdn.microsoft.com/library/55cz5x2c\(v=vs.110\))</span></span>  
  
-   <span data-ttu-id="17464-119">[Postupy: zobrazení okna se zprávou](https://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span><span class="sxs-lookup"><span data-stu-id="17464-119">[How to: Display Message Boxes](https://msdn.microsoft.com/library/3tt9e94f\(v=vs.110\))</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="17464-120">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="17464-120">Related Sections</span></span>  
 [<span data-ttu-id="17464-121">Ovládací prvky a součásti dialogového okna</span><span class="sxs-lookup"><span data-stu-id="17464-121">Dialog-Box Controls and Components</span></span>](../../../docs/framework/winforms/controls/dialog-box-controls-and-components-windows-forms.md)  
 <span data-ttu-id="17464-122">Obsahuje ovládací prvky předdefinované dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="17464-122">Lists the predefined dialog box controls.</span></span>  
  
 [<span data-ttu-id="17464-123">Změna vzhledu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="17464-123">Changing the Appearance of Windows Forms</span></span>](../../../docs/framework/winforms/changing-the-appearance-of-windows-forms.md)  
 <span data-ttu-id="17464-124">Obsahuje odkazy na témata, která popisují, jak změnit vzhled aplikace Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="17464-124">Contains links to topics that describe how to change the appearance of Windows Forms applications.</span></span>  
  
 [<span data-ttu-id="17464-125">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="17464-125">TabControl Control Overview</span></span>](../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 <span data-ttu-id="17464-126">Vysvětluje, jak začlenit kartu ovládacího prvku do dialogového okna.</span><span class="sxs-lookup"><span data-stu-id="17464-126">Explains how you incorporate the tab control into a dialog box.</span></span>
