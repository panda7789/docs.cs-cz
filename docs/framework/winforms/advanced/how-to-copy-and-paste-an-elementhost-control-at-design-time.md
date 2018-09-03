---
title: 'Postupy: Zkopírování a vložení ovládacího prvku ElementHost během návrhu'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: e570375d-2a68-44ba-b4f7-c781af2d20e8
ms.openlocfilehash: 43ebe50497df97511925bd2e413ab5b5988b7f57
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43476141"
---
# <a name="how-to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="7e472-102">Postupy: Zkopírování a vložení ovládacího prvku ElementHost během návrhu</span><span class="sxs-lookup"><span data-stu-id="7e472-102">How to: Copy and Paste an ElementHost Control at Design Time</span></span>
<span data-ttu-id="7e472-103">Tento postup ukazuje, jak zkopírovat Windows Presentation Foundation (WPF) ovládací prvek na formuláři Windows.</span><span class="sxs-lookup"><span data-stu-id="7e472-103">This procedure shows you how to copy a Windows Presentation Foundation (WPF) control on a Windows Form.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e472-104">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="7e472-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="7e472-105">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="7e472-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="7e472-106">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="7e472-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-copy-and-paste-an-elementhost-control-at-design-time"></a><span data-ttu-id="7e472-107">Zkopírování a vložení ovládacího prvku ElementHost během návrhu</span><span class="sxs-lookup"><span data-stu-id="7e472-107">To copy and paste an ElementHost control at design time</span></span>  
  
1.  <span data-ttu-id="7e472-108">Přidat nový WPF <xref:System.Windows.Controls.UserControl> do projektu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="7e472-108">Add a new WPF <xref:System.Windows.Controls.UserControl> to your Windows Forms project.</span></span> <span data-ttu-id="7e472-109">Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="7e472-109">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="7e472-110">Další informace najdete v tématu [návod: vytváření nových WPF obsahu ve Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="7e472-110">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="7e472-111">V **vlastnosti** okno, nastavte hodnotu <xref:System.Windows.FrameworkElement.Width%2A> a <xref:System.Windows.FrameworkElement.Height%2A> vlastnosti `UserControl1` k `200`.</span><span class="sxs-lookup"><span data-stu-id="7e472-111">In the **Properties** window, set the value of the <xref:System.Windows.FrameworkElement.Width%2A> and <xref:System.Windows.FrameworkElement.Height%2A> properties of `UserControl1` to `200`.</span></span>  
  
3.  <span data-ttu-id="7e472-112">Nastavte hodnotu <xref:System.Windows.Controls.Control.Background%2A> vlastnost `Blue`.</span><span class="sxs-lookup"><span data-stu-id="7e472-112">Set the value of the <xref:System.Windows.Controls.Control.Background%2A> property to `Blue`.</span></span>  
  
4.  <span data-ttu-id="7e472-113">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="7e472-113">Build the project.</span></span>  
  
5.  <span data-ttu-id="7e472-114">Otevřít `Form1` v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="7e472-114">Open `Form1` in the Windows Forms Designer.</span></span>  
  
6.  <span data-ttu-id="7e472-115">Z **nástrojů**, přetáhněte instance `UserControl1` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="7e472-115">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="7e472-116">Instance `UserControl1` hostována v novém <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="7e472-116">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
7.  <span data-ttu-id="7e472-117">S `elementHost1` vybrána, stiskněte CTRL + C zkopírujte do schránky.</span><span class="sxs-lookup"><span data-stu-id="7e472-117">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
8.  <span data-ttu-id="7e472-118">Stisknutím kláves CTRL + V vložte zkopírovaný ovládací prvek na formuláři.</span><span class="sxs-lookup"><span data-stu-id="7e472-118">Press CTRL+V to paste the copied control onto the form.</span></span>  
  
     <span data-ttu-id="7e472-119">Nový <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost2` se vytvoří ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="7e472-119">A new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost2` is created on the form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e472-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="7e472-120">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="7e472-121">Návod: Zkopírování a vložení ovládacího prvku ElementHost do samostatného modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="7e472-121">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 [<span data-ttu-id="7e472-122">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="7e472-122">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="7e472-123">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="7e472-123">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="7e472-124">Návrh kódu XAML v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="7e472-124">Design XAML in Visual Studio</span></span>](/visualstudio/designers/designing-xaml-in-visual-studio)
