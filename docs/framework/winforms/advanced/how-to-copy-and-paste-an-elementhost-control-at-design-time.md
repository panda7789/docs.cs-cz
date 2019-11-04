---
title: 'Postupy: Zkopírování a vložení ovládacího prvku ElementHost během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: e89510558274558e560bf810afe746e250ff26a4
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459227"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a><span data-ttu-id="3b7e4-102">Postupy: zkopírování a vložení ovládacího prvku ElementHost</span><span class="sxs-lookup"><span data-stu-id="3b7e4-102">How to: Copy and paste an ElementHost control</span></span>

<span data-ttu-id="3b7e4-103">Tento postup ukazuje, jak zkopírovat ovládací prvek Windows Presentation Foundation (WPF) do formuláře Windows v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="3b7e4-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form in Visual Studio.</span></span>

1. <span data-ttu-id="3b7e4-104">V aplikaci Visual Studio přidejte novou <xref:System.Windows.Controls.UserControl> WPF do projektu model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="3b7e4-104">In Visual Studio, add a new WPF <xref:System.Windows.Controls.UserControl> to a Windows Forms project.</span></span> <span data-ttu-id="3b7e4-105">Použijte výchozí název pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="3b7e4-105">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="3b7e4-106">Další informace najdete v tématu [Návod: vytvoření nového obsahu WPF na model Windows Forms v době návrhu](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="3b7e4-106">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="3b7e4-107">V okně **vlastnosti** nastavte hodnotu vlastnosti <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> `UserControl1` na **200**.</span><span class="sxs-lookup"><span data-stu-id="3b7e4-107">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to **200**.</span></span>

3. <span data-ttu-id="3b7e4-108">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span><span class="sxs-lookup"><span data-stu-id="3b7e4-108">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

4. <span data-ttu-id="3b7e4-109">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="3b7e4-109">Build the project.</span></span>

5. <span data-ttu-id="3b7e4-110">Open `Form1` in the Windows Forms Designer.</span><span class="sxs-lookup"><span data-stu-id="3b7e4-110">Open `Form1` in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="3b7e4-111">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span><span class="sxs-lookup"><span data-stu-id="3b7e4-111">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>

   <span data-ttu-id="3b7e4-112">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="3b7e4-112">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

7. <span data-ttu-id="3b7e4-113">With `elementHost1` selected, press **Ctrl**+**C** to copy it to the clipboard.</span><span class="sxs-lookup"><span data-stu-id="3b7e4-113">With `elementHost1` selected, press **Ctrl**+**C** to copy it to the clipboard.</span></span>

8. <span data-ttu-id="3b7e4-114">Press **Ctrl**+**V** to paste the copied control onto the form.</span><span class="sxs-lookup"><span data-stu-id="3b7e4-114">Press **Ctrl**+**V** to paste the copied control onto the form.</span></span>

   <span data-ttu-id="3b7e4-115">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span><span class="sxs-lookup"><span data-stu-id="3b7e4-115">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>

## <a name="see-also"></a><span data-ttu-id="3b7e4-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="3b7e4-116">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="3b7e4-117">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="3b7e4-117">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="3b7e4-118">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="3b7e4-118">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="3b7e4-119">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="3b7e4-119">Design XAML in Visual Studio</span></span>](/visualstudio/xaml-tools/designing-xaml-in-visual-studio)
