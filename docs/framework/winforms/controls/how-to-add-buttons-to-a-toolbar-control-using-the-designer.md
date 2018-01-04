---
title: "Postupy: Přidávání tlačítek do ovládacího prvku ToolBar pomocí Návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- toolbars [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding buttons
- ToolBar control [Windows Forms], adding separators
- examples [Windows Forms], toolbars
- ToolBar control [Windows Forms], adding drop-down menus
ms.assetid: d9ce3040-3e21-4e2d-80ae-b430982b2db8
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ccd63cb88661db7601b87eec6bdf3a959afb8bbf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-add-buttons-to-a-toolbar-control-using-the-designer"></a><span data-ttu-id="85cc1-102">Postupy: Přidávání tlačítek do ovládacího prvku ToolBar pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="85cc1-102">How to: Add Buttons to a ToolBar Control Using the Designer</span></span>
> [!NOTE]
>  <span data-ttu-id="85cc1-103"><xref:System.Windows.Forms.ToolStrip> Řízení nahrazuje a přidá funkce <xref:System.Windows.Forms.ToolBar> řízení; však <xref:System.Windows.Forms.ToolBar> řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="85cc1-103">The <xref:System.Windows.Forms.ToolStrip> control replaces and adds functionality to the <xref:System.Windows.Forms.ToolBar> control; however, the <xref:System.Windows.Forms.ToolBar> control is retained for both backward compatibility and future use, if you choose.</span></span>  
  
 <span data-ttu-id="85cc1-104">Nedílnou součástí <xref:System.Windows.Forms.ToolBar> ovládací prvek je přidejte do ní tlačítek.</span><span class="sxs-lookup"><span data-stu-id="85cc1-104">An integral part of the <xref:System.Windows.Forms.ToolBar> control is the buttons you add to it.</span></span> <span data-ttu-id="85cc1-105">To slouží k poskytování snadného přístupu k příkazům nabídky nebo Alternativně můžete umístit v jiné oblasti uživatelského rozhraní pro vaší aplikace, která zveřejňuje příkazy pro vaše uživatele, kteří nejsou k dispozici ve struktuře nabídky.</span><span class="sxs-lookup"><span data-stu-id="85cc1-105">These can be used to provide easy access to menu commands or, alternately, they can be placed in another area of the user interface of your application to expose commands to your users that are not available in the menu structure.</span></span>  
  
 <span data-ttu-id="85cc1-106">Následující postup vyžaduje **aplikace Windows** projekt pomocí formuláře obsahující <xref:System.Windows.Forms.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="85cc1-106">The following procedure requires a **Windows Application** project with a form containing a <xref:System.Windows.Forms.ToolBar> control.</span></span> <span data-ttu-id="85cc1-107">Informace o nastavení tohoto projektu najdete v tématu [postupy: vytvoření projektu aplikace Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) a [postupy: Přidání ovládacích prvků do formulářů Windows](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="85cc1-107">For information about setting up such a project, see [How to: Create a Windows Application Project](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa) and [How to: Add Controls to Windows Forms](../../../../docs/framework/winforms/controls/how-to-add-controls-to-windows-forms.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="85cc1-108">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="85cc1-108">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="85cc1-109">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="85cc1-109">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="85cc1-110">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="85cc1-110">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-add-buttons-at-design-time"></a><span data-ttu-id="85cc1-111">Přidání tlačítka v době návrhu</span><span class="sxs-lookup"><span data-stu-id="85cc1-111">To add buttons at design time</span></span>  
  
1.  <span data-ttu-id="85cc1-112">Vyberte <xref:System.Windows.Forms.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="85cc1-112">Select the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
2.  <span data-ttu-id="85cc1-113">V **vlastnosti** okně klikněte na tlačítko <xref:System.Windows.Forms.ToolBar.Buttons%2A> vlastnost vyberte ho a klikněte na tlačítko **třemi tečkami** (![VisualStudioEllipsesButton snímek] (../../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) tlačítko Otevřít **Editor kolekce ToolBarButton**.</span><span class="sxs-lookup"><span data-stu-id="85cc1-113">In the **Properties** window, click the <xref:System.Windows.Forms.ToolBar.Buttons%2A> property to select it and click the **Ellipsis** (![VisualStudioEllipsesButton screenshot](../../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) button to open the **ToolBarButton Collection Editor**.</span></span>  
  
3.  <span data-ttu-id="85cc1-114">Použití **přidat** a **odebrat** tlačítka přidávat a odebírat tlačítka z <xref:System.Windows.Forms.ToolBar> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="85cc1-114">Use the **Add** and **Remove** buttons to add and remove buttons from the <xref:System.Windows.Forms.ToolBar> control.</span></span>  
  
4.  <span data-ttu-id="85cc1-115">Konfigurovat vlastnosti jednotlivých tlačítka v **vlastnosti** okno, které se zobrazí v podokně na pravé straně editoru.</span><span class="sxs-lookup"><span data-stu-id="85cc1-115">Configure the properties of the individual buttons in the **Properties** window that appears in the pane on the right side of the editor.</span></span> <span data-ttu-id="85cc1-116">V následující tabulce jsou uvedeny některé důležité vlastnosti vzít v úvahu.</span><span class="sxs-lookup"><span data-stu-id="85cc1-116">The following table shows some important properties to consider.</span></span>  
  
    |<span data-ttu-id="85cc1-117">Vlastnost</span><span class="sxs-lookup"><span data-stu-id="85cc1-117">Property</span></span>|<span data-ttu-id="85cc1-118">Popis</span><span class="sxs-lookup"><span data-stu-id="85cc1-118">Description</span></span>|  
    |--------------|-----------------|  
    |<xref:System.Windows.Forms.ToolBarButton.DropDownMenu%2A>|<span data-ttu-id="85cc1-119">Nastaví v nabídce Zobrazit v tlačítko panelu nástrojů rozevíracího seznamu.</span><span class="sxs-lookup"><span data-stu-id="85cc1-119">Sets the menu to be displayed in the drop-down toolbar button.</span></span> <span data-ttu-id="85cc1-120">Tlačítka panelu nástrojů <xref:System.Windows.Forms.ToolBarButton.Style%2A> musí být nastavena na <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>.</span><span class="sxs-lookup"><span data-stu-id="85cc1-120">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.DropDownButton>.</span></span> <span data-ttu-id="85cc1-121">Tato vlastnost přijímá instanci <xref:System.Windows.Forms.ContextMenu> třída jako odkaz.</span><span class="sxs-lookup"><span data-stu-id="85cc1-121">This property takes an instance of the <xref:System.Windows.Forms.ContextMenu> class as a reference.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.PartialPush%2A>|<span data-ttu-id="85cc1-122">Nastaví, zda je částečně nabídnutých Přepnout styl tlačítka panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="85cc1-122">Sets whether a toggle-style toolbar button is partially pushed.</span></span> <span data-ttu-id="85cc1-123">Tlačítka panelu nástrojů <xref:System.Windows.Forms.ToolBarButton.Style%2A> musí být nastavena na <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.</span><span class="sxs-lookup"><span data-stu-id="85cc1-123">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton>.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Pushed%2A>|<span data-ttu-id="85cc1-124">Nastaví, zda tlačítka panelu nástrojů Přepnout styl je momentálně v stisknutí stavu.</span><span class="sxs-lookup"><span data-stu-id="85cc1-124">Sets whether a toggle-style toolbar button is currently in the pushed state.</span></span> <span data-ttu-id="85cc1-125">Tlačítka panelu nástrojů <xref:System.Windows.Forms.ToolBarButton.Style%2A> musí být nastavena na <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> nebo <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.</span><span class="sxs-lookup"><span data-stu-id="85cc1-125">The toolbar button's <xref:System.Windows.Forms.ToolBarButton.Style%2A> property must be set to <xref:System.Windows.Forms.ToolBarButtonStyle.ToggleButton> or <xref:System.Windows.Forms.ToolBarButtonStyle.PushButton>.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Style%2A>|<span data-ttu-id="85cc1-126">Nastavuje styl tlačítka panelu nástrojů.</span><span class="sxs-lookup"><span data-stu-id="85cc1-126">Sets the style of the toolbar button.</span></span> <span data-ttu-id="85cc1-127">Musí být jedna z hodnot v <xref:System.Windows.Forms.ToolBarButtonStyle> výčtu.</span><span class="sxs-lookup"><span data-stu-id="85cc1-127">Must be one of the values in the <xref:System.Windows.Forms.ToolBarButtonStyle> enumeration.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.Text%2A>|<span data-ttu-id="85cc1-128">Textový řetězec zobrazí tlačítko.</span><span class="sxs-lookup"><span data-stu-id="85cc1-128">The text string displayed by the button.</span></span>|  
    |<xref:System.Windows.Forms.ToolBarButton.ToolTipText%2A>|<span data-ttu-id="85cc1-129">Text, který se zobrazí jako popisek pro tlačítko.</span><span class="sxs-lookup"><span data-stu-id="85cc1-129">The text that appears as a ToolTip for the button.</span></span>|  
  
5.  <span data-ttu-id="85cc1-130">Klikněte na tlačítko **OK** a zavřete dialogové okno Vytvořit panelů jste zadali.</span><span class="sxs-lookup"><span data-stu-id="85cc1-130">Click **OK** to close the dialog box and create the panels you specified.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="85cc1-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="85cc1-131">See Also</span></span>  
 <xref:System.Windows.Forms.ToolBar>  
 [<span data-ttu-id="85cc1-132">Postupy: Definování ikony pro tlačítko ToolBar</span><span class="sxs-lookup"><span data-stu-id="85cc1-132">How to: Define an Icon for a ToolBar Button</span></span>](../../../../docs/framework/winforms/controls/how-to-define-an-icon-for-a-toolbar-button.md)  
 [<span data-ttu-id="85cc1-133">Postupy: Spouštění událostí nabídky pro tlačítka panelu nástrojů</span><span class="sxs-lookup"><span data-stu-id="85cc1-133">How to: Trigger Menu Events for Toolbar Buttons</span></span>](../../../../docs/framework/winforms/controls/how-to-trigger-menu-events-for-toolbar-buttons.md)  
 [<span data-ttu-id="85cc1-134">Přehled ovládacího prvku ToolBar</span><span class="sxs-lookup"><span data-stu-id="85cc1-134">ToolBar Control Overview</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-overview-windows-forms.md)  
 [<span data-ttu-id="85cc1-135">Ovládací prvek ToolBar</span><span class="sxs-lookup"><span data-stu-id="85cc1-135">ToolBar Control</span></span>](../../../../docs/framework/winforms/controls/toolbar-control-windows-forms.md)
