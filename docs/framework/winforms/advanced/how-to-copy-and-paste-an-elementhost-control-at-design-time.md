---
title: 'Postupy: Zkopírování a vložení ovládacího prvku ElementHost během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 0f3367deaaec04744a3f812d7f2d08047d7eb588
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211371"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="45553-102">Postupy: Zkopírování a vložení ovládacího prvku ElementHost během návrhu</span><span class="sxs-lookup"><span data-stu-id="45553-102">How to: Copy and Paste an ElementHost Control at Design Time</span></span>

<span data-ttu-id="45553-103">Tento postup ukazuje, jak zkopírovat Windows Presentation Foundation (WPF) ovládací prvek na formuláři Windows v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="45553-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form in Visual Studio.</span></span>

## <a name="copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="45553-104">Kopírování a vložení ovládacího prvku ElementHost během návrhu</span><span class="sxs-lookup"><span data-stu-id="45553-104">Copy and paste an ElementHost control at design time</span></span>

1. <span data-ttu-id="45553-105">Přidat nový WPF <xref:System.Windows.Controls.UserControl> do projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="45553-105">Add a new WPF <xref:System.Windows.Controls.UserControl> to your Windows Forms project.</span></span> <span data-ttu-id="45553-106">Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="45553-106">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="45553-107">Další informace najdete v tématu [názorný postup: Vytvoření nového obsahu WPF ve Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="45553-107">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="45553-108">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti `UserControl1` k `200`.</span><span class="sxs-lookup"><span data-stu-id="45553-108">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to `200`.</span></span>

3. <span data-ttu-id="45553-109">Nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Blue`.</span><span class="sxs-lookup"><span data-stu-id="45553-109">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>

4. <span data-ttu-id="45553-110">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="45553-110">Build the project.</span></span>

5. <span data-ttu-id="45553-111">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="45553-111">Open `Form1` in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="45553-112">Z **nástrojů**, přetáhněte instance `UserControl1` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="45553-112">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>

   <span data-ttu-id="45553-113">Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="45553-113">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

7. <span data-ttu-id="45553-114">S `elementHost1` vybrána, stiskněte CTRL + C zkopírujte do schránky.</span><span class="sxs-lookup"><span data-stu-id="45553-114">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>

8. <span data-ttu-id="45553-115">Stisknutím kláves CTRL + V vložte zkopírovaný ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="45553-115">Press CTRL+V to paste the copied control onto the form.</span></span>

   <span data-ttu-id="45553-116">Nový <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost2` se vytvoří ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="45553-116">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>

## <a name="see-also"></a><span data-ttu-id="45553-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="45553-117">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="45553-118">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="45553-118">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="45553-119">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="45553-119">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="45553-120">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="45553-120">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
