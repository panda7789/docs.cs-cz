---
title: 'Postupy: Zobrazení místní nápovědy'
ms.date: 03/30/2017
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
ms.openlocfilehash: f805840ea3b1a8aef6a289dba064c468a4da0cb0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62004338"
---
# <a name="how-to-display-pop-up-help"></a><span data-ttu-id="df036-102">Postupy: Zobrazení místní nápovědy</span><span class="sxs-lookup"><span data-stu-id="df036-102">How to: Display Pop-up Help</span></span>
<span data-ttu-id="df036-103">Jedním ze způsobů pro zobrazení nápovědy v modelu Windows Forms je prostřednictvím **pomáhají** tlačítko, se nachází na pravé straně záhlaví, přístupné prostřednictvím <xref:System.Windows.Forms.Form.HelpButton%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="df036-103">One way to display Help on Windows Forms is through the **Help** button, located on the right side of the title bar, accessible through the <xref:System.Windows.Forms.Form.HelpButton%2A> property.</span></span> <span data-ttu-id="df036-104">Tento typ zobrazení nápovědy je velmi vhodná pro použití s dialogových oknech.</span><span class="sxs-lookup"><span data-stu-id="df036-104">This type of Help display is well-suited for use with dialog boxes.</span></span> <span data-ttu-id="df036-105">Dialogová okna zobrazen modálně (s <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda), nedaří spustit až externí Nápověda systémy, protože modálních dialogových oken muset zřejmě zavřít před fokus můžete přesunout do jiného okna.</span><span class="sxs-lookup"><span data-stu-id="df036-105">Dialog boxes shown modally (with the <xref:System.Windows.Forms.Form.ShowDialog%2A> method) have trouble bringing up external Help systems, because modal dialog boxes need to be closed before focus can shift to another window.</span></span> <span data-ttu-id="df036-106">Kromě toho používání **pomáhají** tlačítko vyžaduje, aby existovala žádné **minimalizovat** tlačítko nebo **Maximalizovat** tlačítka zobrazen v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="df036-106">Additionally, using the **Help** button requires that there is no **Minimize** button or **Maximize** button shown in the title bar.</span></span> <span data-ttu-id="df036-107">Jedná se o standardní dialogové konvenci, zatímco formuláře mají obvykle **minimalizovat** a **Maximalizovat** tlačítka.</span><span class="sxs-lookup"><span data-stu-id="df036-107">This is a standard dialog-box convention, whereas forms usually have **Minimize** and **Maximize** buttons.</span></span>  
  
 <span data-ttu-id="df036-108">Mějte na paměti, že můžete použít také <xref:System.Windows.Forms.HelpProvider> komponenty propojení ovládacích prvků do souborů v systému nápovědy, i v případě, že jste implementovali místní nápovědy.</span><span class="sxs-lookup"><span data-stu-id="df036-108">Be aware that you can also use the <xref:System.Windows.Forms.HelpProvider> component to link controls to files in a Help system, even if you have implemented pop-up Help.</span></span> <span data-ttu-id="df036-109">Další informace najdete v tématu [poskytnutí nápovědy v aplikaci Windows](how-to-provide-help-in-a-windows-application.md).</span><span class="sxs-lookup"><span data-stu-id="df036-109">For more information, see [Providing Help in a Windows Application](how-to-provide-help-in-a-windows-application.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="df036-110">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="df036-110">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="df036-111">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="df036-111">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="df036-112">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="df036-112">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-display-pop-up-help"></a><span data-ttu-id="df036-113">K zobrazení místní nápovědy</span><span class="sxs-lookup"><span data-stu-id="df036-113">To display pop-up Help</span></span>  
  
1. <span data-ttu-id="df036-114">Přetáhněte [HelpProvider](../controls/helpprovider-component-windows-forms.md) komponentu z panelu nástrojů do formuláře.</span><span class="sxs-lookup"><span data-stu-id="df036-114">Drag a [HelpProvider](../controls/helpprovider-component-windows-forms.md) component from the Toolbox to your form.</span></span>  
  
     <span data-ttu-id="df036-115">Se nacházejí na hlavním panelu v dolní části Návrháře formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="df036-115">It will sit in the tray at the bottom of the Windows Forms Designer.</span></span>  
  
2. <span data-ttu-id="df036-116">V okně Vlastnosti nastavte <xref:System.Windows.Forms.Form.HelpButton%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="df036-116">In the Properties window, set the <xref:System.Windows.Forms.Form.HelpButton%2A> property to `true`.</span></span> <span data-ttu-id="df036-117">Bude se zobrazovat tlačítko s otazníkem ho na pravé straně záhlaví formuláře.</span><span class="sxs-lookup"><span data-stu-id="df036-117">This will display a button with a question mark in it on the right side of the title bar of the form.</span></span>  
  
3. <span data-ttu-id="df036-118">Aby <xref:System.Windows.Forms.Form.HelpButton%2A> k zobrazení formuláře <xref:System.Windows.Forms.Form.MinimizeBox%2A> a <xref:System.Windows.Forms.Form.MaximizeBox%2A> vlastnosti musí být nastavena na `false`, <xref:System.Windows.Forms.Form.ControlBox%2A> vlastnost nastavena na `true`a <xref:System.Windows.Forms.Form.FormBorderStyle%2A> vlastnost na jednu z následujících hodnot: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> nebo <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span><span class="sxs-lookup"><span data-stu-id="df036-118">In order for the <xref:System.Windows.Forms.Form.HelpButton%2A> to display, the form's <xref:System.Windows.Forms.Form.MinimizeBox%2A> and <xref:System.Windows.Forms.Form.MaximizeBox%2A> properties must be set to `false`, the <xref:System.Windows.Forms.Form.ControlBox%2A> property set to `true`, and the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to one of the following values: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle>, <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> or <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span></span>  
  
4. <span data-ttu-id="df036-119">Vyberte ovládací prvek, pro kterou chcete zobrazit nápovědu na formuláři a nastavit text nápovědy v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="df036-119">Select the control for which you want to show help on your form and set the Help string in the Properties window.</span></span> <span data-ttu-id="df036-120">Jedná se o řetězec textu, který se zobrazí v okně podobně jako [popisek](../controls/tooltip-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="df036-120">This is the string of text that will be displayed in a window similar to a [ToolTip](../controls/tooltip-component-windows-forms.md).</span></span>  
  
5. <span data-ttu-id="df036-121">Stisknutím klávesy **F5**.</span><span class="sxs-lookup"><span data-stu-id="df036-121">Press **F5**.</span></span>  
  
6. <span data-ttu-id="df036-122">Stisknutím klávesy **pomáhají** tlačítko v záhlaví okna a klepněte na ovládací prvek, na kterém můžete nastavit text nápovědy.</span><span class="sxs-lookup"><span data-stu-id="df036-122">Press the **Help** button on the title bar and click the control on which you set the Help string.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df036-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df036-123">See also</span></span>

- [<span data-ttu-id="df036-124">Nápověda ovládacího prvku pomocí ToolTips</span><span class="sxs-lookup"><span data-stu-id="df036-124">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)
- [<span data-ttu-id="df036-125">Integrace uživatelské nápovědy v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="df036-125">Integrating User Help in Windows Forms</span></span>](integrating-user-help-in-windows-forms.md)
- [<span data-ttu-id="df036-126">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="df036-126">Windows Forms</span></span>](../index.md)
