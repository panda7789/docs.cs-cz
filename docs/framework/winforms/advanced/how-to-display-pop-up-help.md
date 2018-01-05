---
title: "Postupy: Zobrazení místní nápovědy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- pop-up Help
- Help [Windows Forms], pop-up Help
- Windows Forms, displaying Help
- forms [Windows Forms], displaying Help
- modal dialog boxes [Windows Forms], pop-up Help
- F1 Help [Windows Forms], in dialog boxes
- HelpProvider component [Windows Forms]
- Help [Windows Forms], adding to dialog boxes
ms.assetid: 218aa81e-e87e-4d67-af05-11627bbdce3b
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4d139c283d002ac76005f22385d83190144c5082
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-display-pop-up-help"></a><span data-ttu-id="43f7c-102">Postupy: Zobrazení místní nápovědy</span><span class="sxs-lookup"><span data-stu-id="43f7c-102">How to: Display Pop-up Help</span></span>
<span data-ttu-id="43f7c-103">Je možné zobrazit nápovědu pro Windows Forms pomocí **pomoci** tlačítko, které se nachází na pravé straně záhlaví, přístupný prostřednictvím <xref:System.Windows.Forms.Form.HelpButton%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="43f7c-103">One way to display Help on Windows Forms is through the **Help** button, located on the right side of the title bar, accessible through the <xref:System.Windows.Forms.Form.HelpButton%2A> property.</span></span> <span data-ttu-id="43f7c-104">Tento typ zobrazení nápovědy je vhodné pro použití s dialogová okna.</span><span class="sxs-lookup"><span data-stu-id="43f7c-104">This type of Help display is well-suited for use with dialog boxes.</span></span> <span data-ttu-id="43f7c-105">Dialogová okna zobrazí modálně (s <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda) mít potíže při vyvolání externí nápovědy systémy, protože modálních dialogových oken, musí se napřed zavřít fokus můžete přesune na další okno.</span><span class="sxs-lookup"><span data-stu-id="43f7c-105">Dialog boxes shown modally (with the <xref:System.Windows.Forms.Form.ShowDialog%2A> method) have trouble bringing up external Help systems, because modal dialog boxes need to be closed before focus can shift to another window.</span></span> <span data-ttu-id="43f7c-106">Kromě toho používání **pomoci** tlačítko vyžaduje, aby byl žádné **minimalizaci** tlačítko nebo **Maximalizovat** tlačítko zobrazené v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="43f7c-106">Additionally, using the **Help** button requires that there is no **Minimize** button or **Maximize** button shown in the title bar.</span></span> <span data-ttu-id="43f7c-107">Jedná se o standardní dialogové konvenci, zatímco forms obvykle mají **minimalizaci** a **Maximalizovat** tlačítka.</span><span class="sxs-lookup"><span data-stu-id="43f7c-107">This is a standard dialog-box convention, whereas forms usually have **Minimize** and **Maximize** buttons.</span></span>  
  
 <span data-ttu-id="43f7c-108">Uvědomte si, že můžete také použít <xref:System.Windows.Forms.HelpProvider> součást propojení ovládacích prvků do souborů v systému nápovědy, i v případě, že jste implementovali automaticky otevírané okno nápovědy.</span><span class="sxs-lookup"><span data-stu-id="43f7c-108">Be aware that you can also use the <xref:System.Windows.Forms.HelpProvider> component to link controls to files in a Help system, even if you have implemented pop-up Help.</span></span> <span data-ttu-id="43f7c-109">Další informace najdete v tématu [poskytnutí nápovědy v aplikaci Windows](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).</span><span class="sxs-lookup"><span data-stu-id="43f7c-109">For more information, see [Providing Help in a Windows Application](../../../../docs/framework/winforms/advanced/how-to-provide-help-in-a-windows-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="43f7c-110">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="43f7c-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="43f7c-111">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="43f7c-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="43f7c-112">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="43f7c-112">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-display-pop-up-help"></a><span data-ttu-id="43f7c-113">K zobrazení místní nápovědy</span><span class="sxs-lookup"><span data-stu-id="43f7c-113">To display pop-up Help</span></span>  
  
1.  <span data-ttu-id="43f7c-114">Přetáhněte [HelpProvider –](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) součásti z panelu nástrojů do svého formuláře.</span><span class="sxs-lookup"><span data-stu-id="43f7c-114">Drag a [HelpProvider](../../../../docs/framework/winforms/controls/helpprovider-component-windows-forms.md) component from the Toolbox to your form.</span></span>  
  
     <span data-ttu-id="43f7c-115">Bude se nacházejí na hlavním panelu v dolní části Návrhář formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="43f7c-115">It will sit in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2.  <span data-ttu-id="43f7c-116">V okně vlastnosti nastavit <xref:System.Windows.Forms.Form.HelpButton%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="43f7c-116">In the Properties window, set the <xref:System.Windows.Forms.Form.HelpButton%2A> property to `true`.</span></span> <span data-ttu-id="43f7c-117">Tlačítko s otazníkem v ní bude se zobrazovat na pravé straně záhlaví formuláře.</span><span class="sxs-lookup"><span data-stu-id="43f7c-117">This will display a button with a question mark in it on the right side of the title bar of the form.</span></span>  
  
3.  <span data-ttu-id="43f7c-118">Aby <xref:System.Windows.Forms.Form.HelpButton%2A> k zobrazení, formuláře <xref:System.Windows.Forms.Form.MinimizeBox%2A> a <xref:System.Windows.Forms.Form.MaximizeBox%2A> vlastnosti musí být nastavena na `false`, <xref:System.Windows.Forms.Form.ControlBox%2A> vlastnost nastavena na hodnotu `true`a <xref:System.Windows.Forms.Form.FormBorderStyle%2A> vlastnost na jednu z následujících hodnot: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> nebo <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span><span class="sxs-lookup"><span data-stu-id="43f7c-118">In order for the <xref:System.Windows.Forms.Form.HelpButton%2A> to display, the form's <xref:System.Windows.Forms.Form.MinimizeBox%2A> and <xref:System.Windows.Forms.Form.MaximizeBox%2A> properties must be set to `false`, the <xref:System.Windows.Forms.Form.ControlBox%2A> property set to `true`, and the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to one of the following values: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle>, <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> or <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span></span>  
  
4.  <span data-ttu-id="43f7c-119">Vyberte ovládací prvek, pro který chcete zobrazit nápovědu ve formuláři a nastavte řetězec nápovědy v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="43f7c-119">Select the control for which you want to show help on your form and set the Help string in the Properties window.</span></span> <span data-ttu-id="43f7c-120">Toto je řetězec text, který se zobrazí v okně podobná [popisek](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="43f7c-120">This is the string of text that will be displayed in a window similar to a [ToolTip](../../../../docs/framework/winforms/controls/tooltip-component-windows-forms.md).</span></span>  
  
5.  <span data-ttu-id="43f7c-121">Stiskněte klávesu **F5**.</span><span class="sxs-lookup"><span data-stu-id="43f7c-121">Press **F5**.</span></span>  
  
6.  <span data-ttu-id="43f7c-122">Stiskněte **pomoci** tlačítko v záhlaví okna a klikněte na ovládací prvek, na které můžete určit řetězec nápovědy.</span><span class="sxs-lookup"><span data-stu-id="43f7c-122">Press the **Help** button on the title bar and click the control on which you set the Help string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="43f7c-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="43f7c-123">See Also</span></span>  
 [<span data-ttu-id="43f7c-124">Nápověda ovládacího prvku pomocí ToolTips</span><span class="sxs-lookup"><span data-stu-id="43f7c-124">Control Help Using ToolTips</span></span>](../../../../docs/framework/winforms/advanced/control-help-using-tooltips.md)  
 [<span data-ttu-id="43f7c-125">Integrace uživatelské nápovědy v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43f7c-125">Integrating User Help in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/integrating-user-help-in-windows-forms.md)  
 [<span data-ttu-id="43f7c-126">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="43f7c-126">Windows Forms</span></span>](../../../../docs/framework/winforms/index.md)
