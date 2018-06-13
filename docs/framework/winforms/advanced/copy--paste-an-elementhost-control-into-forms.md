---
title: 'Návod: Zkopírování a vložení ovládacího prvku ElementHost do samostatného formuláře Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, content copying and pasting
- interoperability [WPF]
- ElementHost control [Windows Forms], copying and pasting at design time
- WPF user control [Windows Forms], hosting in Windows Forms
ms.assetid: 6e81bb13-577c-46c3-a1cf-8d15969fb83e
ms.openlocfilehash: 1cce981e4cb04ab6ed6ed41e0afac0121b242761
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520939"
---
# <a name="walkthrough-copying-and-pasting-an-elementhost-control-into-separate-windows-forms"></a><span data-ttu-id="33e92-102">Návod: Zkopírování a vložení ovládacího prvku ElementHost do samostatného formuláře Windows</span><span class="sxs-lookup"><span data-stu-id="33e92-102">Walkthrough: Copying and Pasting an ElementHost Control into Separate Windows Forms</span></span>
<span data-ttu-id="33e92-103">Tento návod ukazuje, jak kopírovat ovládacího prvku Windows Presentation Foundation (WPF) z jednoho formuláře Windows do jiného.</span><span class="sxs-lookup"><span data-stu-id="33e92-103">This walkthrough shows you how to copy a Windows Presentation Foundation (WPF) control from one Windows Form to another.</span></span>  
  
 <span data-ttu-id="33e92-104">V tomto návodu můžete provádět následující úlohy:</span><span class="sxs-lookup"><span data-stu-id="33e92-104">In this walkthrough, you perform the following tasks:</span></span>  
  
-   <span data-ttu-id="33e92-105">Vytvoření projektu.</span><span class="sxs-lookup"><span data-stu-id="33e92-105">Create the project.</span></span>  
  
-   <span data-ttu-id="33e92-106">Zkopírujte ovládací prvek WPF.</span><span class="sxs-lookup"><span data-stu-id="33e92-106">Copy a WPF Control.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33e92-107">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="33e92-107">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="33e92-108">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="33e92-108">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="33e92-109">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="33e92-109">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
## <a name="prerequisites"></a><span data-ttu-id="33e92-110">Požadavky</span><span class="sxs-lookup"><span data-stu-id="33e92-110">Prerequisites</span></span>  
 <span data-ttu-id="33e92-111">K dokončení tohoto návodu budete potřebovat následující komponenty:</span><span class="sxs-lookup"><span data-stu-id="33e92-111">You need the following components to complete this walkthrough:</span></span>  
  
-   [!INCLUDE[vs_dev11_long](../../../../includes/vs-dev11-long-md.md)]<span data-ttu-id="33e92-112">.</span><span class="sxs-lookup"><span data-stu-id="33e92-112">.</span></span>  
  
## <a name="creating-the-project"></a><span data-ttu-id="33e92-113">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="33e92-113">Creating the Project</span></span>  
 <span data-ttu-id="33e92-114">Prvním krokem je vytvoření projektu modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="33e92-114">The first step is to create the Windows Forms project.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="33e92-115">Pokud hostování obsahu subsystému WPF, jsou podporovány pouze projekty C# a Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="33e92-115">When hosting WPF content, only C# and Visual Basic projects are supported.</span></span>  
  
#### <a name="to-create-the-project"></a><span data-ttu-id="33e92-116">Vytvoření projektu</span><span class="sxs-lookup"><span data-stu-id="33e92-116">To create the project</span></span>  
  
-   <span data-ttu-id="33e92-117">Vytvořte nový projekt aplikace Windows Forms v jazyce Visual Basic a Visual C# s názvem `CopyElementHost`.</span><span class="sxs-lookup"><span data-stu-id="33e92-117">Create a new Windows Forms Application project in Visual Basic or Visual C# named `CopyElementHost`.</span></span>  
  
## <a name="copying-a-wpf-control"></a><span data-ttu-id="33e92-118">Kopírování ovládací prvek WPF</span><span class="sxs-lookup"><span data-stu-id="33e92-118">Copying a WPF Control</span></span>  
 <span data-ttu-id="33e92-119">Po přidání ovládací prvek WPF do projektu, zkopírujte jej do jiných formulářů v projektu.</span><span class="sxs-lookup"><span data-stu-id="33e92-119">After you add a WPF control to the project, you can copy it to other forms in the project.</span></span>  
  
#### <a name="to-copy-a-wpf-control"></a><span data-ttu-id="33e92-120">Kopírování ovládací prvek WPF</span><span class="sxs-lookup"><span data-stu-id="33e92-120">To copy a WPF control</span></span>  
  
1.  <span data-ttu-id="33e92-121">Přidat nové WPF <xref:System.Windows.Controls.UserControl> projektu k řešení.</span><span class="sxs-lookup"><span data-stu-id="33e92-121">Add a new WPF <xref:System.Windows.Controls.UserControl> project to the solution.</span></span> <span data-ttu-id="33e92-122">Použití výchozího názvu pro typ ovládacího prvku `UserControl1.xaml`.</span><span class="sxs-lookup"><span data-stu-id="33e92-122">Use the default name for the control type, `UserControl1.xaml`.</span></span> <span data-ttu-id="33e92-123">Další informace najdete v tématu [návod: vytvoření nové WPF obsahu v aplikaci Windows Forms v době návrhu](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span><span class="sxs-lookup"><span data-stu-id="33e92-123">For more information, see [Walkthrough: Creating New WPF Content on Windows Forms at Design Time](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md).</span></span>  
  
2.  <span data-ttu-id="33e92-124">Sestavte projekt.</span><span class="sxs-lookup"><span data-stu-id="33e92-124">Build the project.</span></span>  
  
3.  <span data-ttu-id="33e92-125">Otevřete `Form1` v Návrháři formulářů.</span><span class="sxs-lookup"><span data-stu-id="33e92-125">Open `Form1` in the Windows Forms Designer.</span></span>  
  
4.  <span data-ttu-id="33e92-126">Z **sada nástrojů**, přetáhněte instanci `UserControl1` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="33e92-126">From the **Toolbox**, drag an instance of `UserControl1` onto the form.</span></span>  
  
     <span data-ttu-id="33e92-127">Instance `UserControl1` je hostován v nové <xref:System.Windows.Forms.Integration.ElementHost> ovládací prvek s názvem `elementHost1`.</span><span class="sxs-lookup"><span data-stu-id="33e92-127">An instance of `UserControl1` is hosted in a new <xref:System.Windows.Forms.Integration.ElementHost> control named `elementHost1`.</span></span>  
  
5.  <span data-ttu-id="33e92-128">S `elementHost1` vybrána, stiskněte CTRL + C zkopírujte jej do schránky.</span><span class="sxs-lookup"><span data-stu-id="33e92-128">With `elementHost1` selected, press CTRL+C to copy it to the clipboard.</span></span>  
  
6.  <span data-ttu-id="33e92-129">Přidání nového formuláře Windows Form do projektu.</span><span class="sxs-lookup"><span data-stu-id="33e92-129">Add a new Windows Form to the project.</span></span> <span data-ttu-id="33e92-130">Použití výchozího názvu pro typ formuláře `Form2`.</span><span class="sxs-lookup"><span data-stu-id="33e92-130">Use the default name for the form type, `Form2`.</span></span>  
  
7.  <span data-ttu-id="33e92-131">S `Form2` otevřít v Návrháři formulářů, stiskněte klávesy CTRL + V vložte kopii `elementHost1` do formuláře.</span><span class="sxs-lookup"><span data-stu-id="33e92-131">With `Form2` open in the Windows Forms Designer, press CTRL+V to paste a copy of `elementHost1` onto the form.</span></span>  
  
     <span data-ttu-id="33e92-132">Zkopírovaný ovládacího prvku se nazývá také `elementHost1`, protože je privátní pole `Form2` třídy.</span><span class="sxs-lookup"><span data-stu-id="33e92-132">The copied control is also named `elementHost1`, because it is a private field of the `Form2` class.</span></span> <span data-ttu-id="33e92-133">Neexistuje žádný název kolizí s `elementHost1` v `Form1` třídy.</span><span class="sxs-lookup"><span data-stu-id="33e92-133">There is no name collision with the `elementHost1` in the `Form1` class.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="33e92-134">Viz také</span><span class="sxs-lookup"><span data-stu-id="33e92-134">See Also</span></span>  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 [<span data-ttu-id="33e92-135">Migrace a interoperabilita</span><span class="sxs-lookup"><span data-stu-id="33e92-135">Migration and Interoperability</span></span>](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 [<span data-ttu-id="33e92-136">Používání ovládacích prvků WPF</span><span class="sxs-lookup"><span data-stu-id="33e92-136">Using WPF Controls</span></span>](../../../../docs/framework/winforms/advanced/using-wpf-controls.md)  
 [<span data-ttu-id="33e92-137">Návrhář WPF</span><span class="sxs-lookup"><span data-stu-id="33e92-137">WPF Designer</span></span>](http://msdn.microsoft.com/library/c6c65214-8411-4e16-b254-163ed4099c26)
