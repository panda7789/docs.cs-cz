---
title: 'Postupy: Ukotvení ovládacích prvků ve Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- Anchor property [Windows Forms], enabling resizable forms
- Windows Forms controls, screen resolutions
- resizing forms [Windows Forms]
- Windows Forms controls, size
- screen resolution and control display
- controls [Windows Forms], anchoring
- forms [Windows Forms], resizing
- Windows Forms, resizing
- controls [Windows Forms], positioning
ms.assetid: 59ea914f-fbd3-427a-80fe-decd02f7ae6d
ms.openlocfilehash: d3dd413793c8a6da900acbf60cc5a20edf908906
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57720368"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="16ded-102">Postupy: Ukotvení ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="16ded-102">How to: Anchor Controls on Windows Forms</span></span>
<span data-ttu-id="16ded-103">Pokud navrhujete formulář, který uživatel může změnit velikost v době běhu, by měl ovládací prvky na formuláři změnit velikost a umístění správně.</span><span class="sxs-lookup"><span data-stu-id="16ded-103">If you are designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="16ded-104">Změna velikosti ovládacích prvků dynamicky pomocí formuláře, můžete použít <xref:System.Windows.Forms.Control.Anchor%2A> vlastností ovládacích prvků Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="16ded-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="16ded-105"><xref:System.Windows.Forms.Control.Anchor%2A> Definuje vlastnost pozice ukotvení pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="16ded-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="16ded-106">Když je ovládací prvek ukotven k formuláři a změně velikosti formuláře, ovládací prvek udržuje vzdálenost mezi ovládacím prvkem a pozice ukotvení.</span><span class="sxs-lookup"><span data-stu-id="16ded-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="16ded-107">Například, pokud máte <xref:System.Windows.Forms.TextBox> ovládací prvek, který je ukotven doleva, doprava a dolů ve formuláři, při změně velikosti formuláře <xref:System.Windows.Forms.TextBox> vodorovně řídit změní tak, aby udržuje stejnou vzdálenost od pravá a levá strana formuláře.</span><span class="sxs-lookup"><span data-stu-id="16ded-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="16ded-108">Kromě toho ovládací prvek umístí samotné svisle tak, aby jeho umístění je vždy stejnou vzdálenost od dolní části formuláře.</span><span class="sxs-lookup"><span data-stu-id="16ded-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="16ded-109">Pokud není ukotven ovládacího prvku a změně velikosti formuláře, dojde ke změně pozice ovládacího prvku vzhledem k okrajům formuláře.</span><span class="sxs-lookup"><span data-stu-id="16ded-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>  
  
 <span data-ttu-id="16ded-110"><xref:System.Windows.Forms.Control.Anchor%2A> Vlastnost komunikuje <xref:System.Windows.Forms.Control.AutoSize%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="16ded-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="16ded-111">Další informace najdete v tématu [přehled vlastnosti AutoSize](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="16ded-111">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16ded-112">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="16ded-112">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="16ded-113">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="16ded-113">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="16ded-114">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="16ded-114">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-anchor-a-control-on-a-form"></a><span data-ttu-id="16ded-115">Chcete-li ukotvit ovládací prvek ve formuláři</span><span class="sxs-lookup"><span data-stu-id="16ded-115">To anchor a control on a form</span></span>  
  
1.  <span data-ttu-id="16ded-116">Vyberte ovládací prvek, který chcete ukotvit.</span><span class="sxs-lookup"><span data-stu-id="16ded-116">Select the control you want to anchor.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="16ded-117">Můžete ukotvit více ovládacích prvků současně klávesy CTRL, kliknutím na každý ovládací prvek a vyberte ho a budete postupovat zbývající část tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="16ded-117">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>  
  
2.  <span data-ttu-id="16ded-118">V **vlastnosti** okna, klikněte na šipku vpravo od <xref:System.Windows.Forms.Control.Anchor%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="16ded-118">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>  
  
     <span data-ttu-id="16ded-119">Editoru se zobrazí, který ukazuje na křížek.</span><span class="sxs-lookup"><span data-stu-id="16ded-119">An editor is displayed that shows a cross.</span></span>  
  
3.  <span data-ttu-id="16ded-120">Pokud chcete nastavit anchor, klikněte na tlačítko vlevo nahoře, pravé nebo dolní část křížového.</span><span class="sxs-lookup"><span data-stu-id="16ded-120">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>  
  
     <span data-ttu-id="16ded-121">Ovládací prvky jsou ukotven k horní a levé ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="16ded-121">Controls are anchored to the top and left by default.</span></span>  
  
4.  <span data-ttu-id="16ded-122">Na straně ovládacího prvku, který není ukotven, klikněte na tento arm křížové.</span><span class="sxs-lookup"><span data-stu-id="16ded-122">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>  
  
5.  <span data-ttu-id="16ded-123">Zavřete <xref:System.Windows.Forms.Control.Anchor%2A> editoru vlastností klikněte <xref:System.Windows.Forms.Control.Anchor%2A> znovu název vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="16ded-123">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>  
  
 <span data-ttu-id="16ded-124">Při formuláři se zobrazí v době běhu, zůstane umístěné ve stejné vzdálenosti od levého okraje formuláře změní velikost ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="16ded-124">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="16ded-125">Vzdálenost od levého okraje ukotvené vždy zůstává definovaný vzdálenost, když je ovládací prvek umístěný v Návrháři formulářů Windows.</span><span class="sxs-lookup"><span data-stu-id="16ded-125">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="16ded-126">Některé ovládací prvky, jako například <xref:System.Windows.Forms.ComboBox> řídit, omezení jejich výšku.</span><span class="sxs-lookup"><span data-stu-id="16ded-126">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="16ded-127">Ukotvení ovládacího prvku do dolní části formuláře nebo kontejneru nelze vynutit překročí limit výšku ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="16ded-127">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>  
  
 <span data-ttu-id="16ded-128">Zděděný ovládací prvky musí být `Protected` mohli být ukotven.</span><span class="sxs-lookup"><span data-stu-id="16ded-128">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="16ded-129">Chcete-li změnit úroveň přístupu ovládacího prvku, nastavte jeho `Modifiers` vlastnost **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="16ded-129">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="16ded-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="16ded-130">See also</span></span>
- [<span data-ttu-id="16ded-131">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="16ded-131">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="16ded-132">Uspořádávání ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="16ded-132">Arranging Controls on Windows Forms</span></span>](arranging-controls-on-windows-forms.md)
- [<span data-ttu-id="16ded-133">Přehled vlastnosti AutoSize</span><span class="sxs-lookup"><span data-stu-id="16ded-133">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="16ded-134">Postupy: Ukotvování ovládacích prvků ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="16ded-134">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="16ded-135">Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="16ded-135">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="16ded-136">Návod: Uspořádání ovládacích prvků na formuláři Windows s použitím ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="16ded-136">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="16ded-137">Návod: Vytváření rozložení Windows Forms ovládací prvky s odsazením, okraji a s vlastností AutoSize</span><span class="sxs-lookup"><span data-stu-id="16ded-137">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
