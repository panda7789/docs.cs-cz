---
title: 'Postupy: Zkopírování a vložení ovládacího prvku ElementHost během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: dfe5244e0c5b61fdf6d940dd16d8c280f013b12c
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69666184"
---
# <a name="how-to-copy-and-paste-an-elementhost-control"></a><span data-ttu-id="b9e16-102">Postupy: Zkopírování a vložení ovládacího prvku ElementHost</span><span class="sxs-lookup"><span data-stu-id="b9e16-102">How to: Copy and paste an ElementHost control</span></span>

<span data-ttu-id="b9e16-103">Tento postup ukazuje, jak zkopírovat ovládací prvek Windows Presentation Foundation (WPF) do formuláře Windows v aplikaci Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="b9e16-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form in Visual Studio.</span></span>

1. <span data-ttu-id="b9e16-104">V aplikaci Visual Studio přidejte nový WPF <xref:System.Windows.Controls.UserControl> do projektu model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="b9e16-104">In Visual Studio, add a new WPF <xref:System.Windows.Controls.UserControl> to a Windows Forms project.</span></span> <span data-ttu-id="b9e16-105">Použijte výchozí název pro typ ovládacího prvku, `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="b9e16-105">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="b9e16-106">Další informace najdete v tématu [Návod: Vytváření nového obsahu WPF v model Windows Forms v době](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)návrhu.</span><span class="sxs-lookup"><span data-stu-id="b9e16-106">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>

2. <span data-ttu-id="b9e16-107">V okně **vlastnosti** nastavte hodnotu vlastností <xref:System.Windows.FrameworkElement.Width%2A> `UserControl1` a <xref:System.Windows.FrameworkElement.Height%2A> na hodnotu **200**.</span><span class="sxs-lookup"><span data-stu-id="b9e16-107">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to **200**.</span></span>

3. <span data-ttu-id="b9e16-108">Nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnosti na modrou.</span><span class="sxs-lookup"><span data-stu-id="b9e16-108">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to **Blue**.</span></span>

4. <span data-ttu-id="b9e16-109">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="b9e16-109">Build the project.</span></span>

5. <span data-ttu-id="b9e16-110">Otevřete `Form1` v Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="b9e16-110">Open `Form1` in the Windows Forms Designer.</span></span>

6. <span data-ttu-id="b9e16-111">Z **panelu nástrojů**přetáhněte instanci `UserControl1` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="b9e16-111">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>

   <span data-ttu-id="b9e16-112">Instance `UserControl1` je hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládacím prvku s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="b9e16-112">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>

7. <span data-ttu-id="b9e16-113">Když vyberete tuto možnost, zkopírujte ji do schránky stisknutím **kombinace kláves CTRL +** +**C.** `elementHost1`</span><span class="sxs-lookup"><span data-stu-id="b9e16-113">With `elementHost1` selected, press **Ctrl**+**C** to copy it to the clipboard.</span></span>

8. <span data-ttu-id="b9e16-114">Stisknutím klávesy **CTRL**+**V** vložte zkopírovaný ovládací prvek do formuláře.</span><span class="sxs-lookup"><span data-stu-id="b9e16-114">Press **Ctrl**+**V** to paste the copied control onto the form.</span></span>

   <span data-ttu-id="b9e16-115">Ve formuláři <xref:System.Windows.Forms.Integration.ElementHost> se vytvoří `elementHost2` nový ovládací prvek s názvem.</span><span class="sxs-lookup"><span data-stu-id="b9e16-115">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>

## <a name="see-also"></a><span data-ttu-id="b9e16-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b9e16-116">See also</span></span>

- <xref:System.Windows.Forms.Integration.ElementHost>
- <xref:System.Windows.Forms.Integration.WindowsFormsHost>
- [<span data-ttu-id="b9e16-117">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="b9e16-117">Migration and Interoperability</span></span>](../../wpf/advanced/migration-and-interoperability.md)
- [<span data-ttu-id="b9e16-118">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="b9e16-118">Using WPF Controls</span></span>](using-wpf-controls.md)
- [<span data-ttu-id="b9e16-119">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="b9e16-119">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
