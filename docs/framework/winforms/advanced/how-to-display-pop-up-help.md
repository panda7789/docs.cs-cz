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
ms.openlocfilehash: bf3bcbff0cd6f3bbf71e96e748cb170d5ce68dfc
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211404"
---
# <a name="how-to-display-pop-up-help"></a><span data-ttu-id="4cd20-102">Postupy: Zobrazení místní nápovědy</span><span class="sxs-lookup"><span data-stu-id="4cd20-102">How to: Display pop-up Help</span></span>

<span data-ttu-id="4cd20-103">Jedním ze způsobů pro zobrazení nápovědy v modelu Windows Forms je prostřednictvím **pomáhají** tlačítko, se nachází na pravé straně záhlaví, přístupné prostřednictvím <xref:System.Windows.Forms.Form.HelpButton%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4cd20-103">One way to display Help on Windows Forms is through the **Help** button, located on the right side of the title bar, accessible through the <xref:System.Windows.Forms.Form.HelpButton%2A> property.</span></span> <span data-ttu-id="4cd20-104">Tento typ zobrazení nápovědy je velmi vhodná pro použití s dialogových oknech.</span><span class="sxs-lookup"><span data-stu-id="4cd20-104">This type of Help display is well-suited for use with dialog boxes.</span></span> <span data-ttu-id="4cd20-105">Dialogová okna zobrazen modálně (s <xref:System.Windows.Forms.Form.ShowDialog%2A> metoda), nedaří spustit až externí Nápověda systémy, protože modálních dialogových oken muset zřejmě zavřít před fokus můžete přesunout do jiného okna.</span><span class="sxs-lookup"><span data-stu-id="4cd20-105">Dialog boxes shown modally (with the <xref:System.Windows.Forms.Form.ShowDialog%2A> method) have trouble bringing up external Help systems, because modal dialog boxes need to be closed before focus can shift to another window.</span></span> <span data-ttu-id="4cd20-106">Kromě toho používání **pomáhají** tlačítko vyžaduje, aby existovala žádné **minimalizovat** tlačítko nebo **Maximalizovat** tlačítka zobrazen v záhlaví.</span><span class="sxs-lookup"><span data-stu-id="4cd20-106">Additionally, using the **Help** button requires that there is no **Minimize** button or **Maximize** button shown in the title bar.</span></span> <span data-ttu-id="4cd20-107">Jedná se o standardní dialogové konvenci, zatímco formuláře mají obvykle **minimalizovat** a **Maximalizovat** tlačítka.</span><span class="sxs-lookup"><span data-stu-id="4cd20-107">This is a standard dialog-box convention, whereas forms usually have **Minimize** and **Maximize** buttons.</span></span>

<span data-ttu-id="4cd20-108">Můžete také použít <xref:System.Windows.Forms.HelpProvider> komponenty propojení ovládacích prvků do souborů v systému nápovědy, i v případě, že jste implementovali místní nápovědy.</span><span class="sxs-lookup"><span data-stu-id="4cd20-108">You can also use the <xref:System.Windows.Forms.HelpProvider> component to link controls to files in a Help system, even if you have implemented pop-up Help.</span></span> <span data-ttu-id="4cd20-109">Další informace najdete v tématu [poskytnutí nápovědy v aplikaci Windows](how-to-provide-help-in-a-windows-application.md).</span><span class="sxs-lookup"><span data-stu-id="4cd20-109">For more information, see [Providing Help in a Windows Application](how-to-provide-help-in-a-windows-application.md).</span></span>

## <a name="display-pop-up-help"></a><span data-ttu-id="4cd20-110">Zobrazení místní nápovědy</span><span class="sxs-lookup"><span data-stu-id="4cd20-110">Display pop-up Help</span></span>

1. <span data-ttu-id="4cd20-111">V sadě Visual Studio, přetáhněte [HelpProvider](../controls/helpprovider-component-windows-forms.md) komponentu z panelu nástrojů do formuláře.</span><span class="sxs-lookup"><span data-stu-id="4cd20-111">In Visual Studio, drag a [HelpProvider](../controls/helpprovider-component-windows-forms.md) component from the Toolbox to your form.</span></span>

   <span data-ttu-id="4cd20-112">Se nacházejí na hlavním panelu v dolní části Návrháře formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="4cd20-112">It will sit in the tray at the bottom of the Windows Forms Designer.</span></span>

2. <span data-ttu-id="4cd20-113">V okně Vlastnosti nastavte <xref:System.Windows.Forms.Form.HelpButton%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="4cd20-113">In the Properties window, set the <xref:System.Windows.Forms.Form.HelpButton%2A> property to `true`.</span></span> <span data-ttu-id="4cd20-114">Bude se zobrazovat tlačítko s otazníkem ho na pravé straně záhlaví formuláře.</span><span class="sxs-lookup"><span data-stu-id="4cd20-114">This will display a button with a question mark in it on the right side of the title bar of the form.</span></span>

3. <span data-ttu-id="4cd20-115">Aby <xref:System.Windows.Forms.Form.HelpButton%2A> k zobrazení formuláře <xref:System.Windows.Forms.Form.MinimizeBox%2A> a <xref:System.Windows.Forms.Form.MaximizeBox%2A> vlastnosti musí být nastavena na `false`, <xref:System.Windows.Forms.Form.ControlBox%2A> vlastnost nastavena na `true`a <xref:System.Windows.Forms.Form.FormBorderStyle%2A> vlastnost na jednu z následujících hodnot: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle> , <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> nebo <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span><span class="sxs-lookup"><span data-stu-id="4cd20-115">In order for the <xref:System.Windows.Forms.Form.HelpButton%2A> to display, the form's <xref:System.Windows.Forms.Form.MinimizeBox%2A> and <xref:System.Windows.Forms.Form.MaximizeBox%2A> properties must be set to `false`, the <xref:System.Windows.Forms.Form.ControlBox%2A> property set to `true`, and the <xref:System.Windows.Forms.Form.FormBorderStyle%2A> property to one of the following values: <xref:System.Windows.Forms.FormBorderStyle.FixedSingle>, <xref:System.Windows.Forms.FormBorderStyle.Fixed3D>, <xref:System.Windows.Forms.FormBorderStyle.FixedDialog> or <xref:System.Windows.Forms.FormBorderStyle.Sizable>.</span></span>

4. <span data-ttu-id="4cd20-116">Vyberte ovládací prvek, pro kterou chcete zobrazit nápovědu na formuláři a nastavit text nápovědy v okně Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4cd20-116">Select the control for which you want to show help on your form and set the Help string in the Properties window.</span></span> <span data-ttu-id="4cd20-117">Jedná se o řetězec textu, který se zobrazí v okně podobně jako [popisek](../controls/tooltip-component-windows-forms.md).</span><span class="sxs-lookup"><span data-stu-id="4cd20-117">This is the string of text that will be displayed in a window similar to a [ToolTip](../controls/tooltip-component-windows-forms.md).</span></span>

5. <span data-ttu-id="4cd20-118">Stisknutím klávesy **F5**.</span><span class="sxs-lookup"><span data-stu-id="4cd20-118">Press **F5**.</span></span>

6. <span data-ttu-id="4cd20-119">Stisknutím klávesy **pomáhají** tlačítko v záhlaví okna a klepněte na ovládací prvek, na kterém můžete nastavit text nápovědy.</span><span class="sxs-lookup"><span data-stu-id="4cd20-119">Press the **Help** button on the title bar and click the control on which you set the Help string.</span></span>

## <a name="see-also"></a><span data-ttu-id="4cd20-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4cd20-120">See also</span></span>

- [<span data-ttu-id="4cd20-121">Nápověda ovládacího prvku pomocí ToolTips</span><span class="sxs-lookup"><span data-stu-id="4cd20-121">Control Help Using ToolTips</span></span>](control-help-using-tooltips.md)
- [<span data-ttu-id="4cd20-122">Integrace uživatelské nápovědy v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4cd20-122">Integrating User Help in Windows Forms</span></span>](integrating-user-help-in-windows-forms.md)
- [<span data-ttu-id="4cd20-123">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4cd20-123">Windows Forms</span></span>](../index.md)
