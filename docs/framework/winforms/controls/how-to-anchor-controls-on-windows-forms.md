---
title: Ukotvení ovládacích prvků
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7c307d8c5b3bc32e15e6de048c434854ef1bbc65
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747178"
---
# <a name="how-to-anchor-controls-on-windows-forms"></a><span data-ttu-id="f1cf6-102">Postupy: ukotvení ovládacích prvků na model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="f1cf6-102">How to: Anchor controls on Windows Forms</span></span>

<span data-ttu-id="f1cf6-103">Pokud navrhujete formulář, který může uživatel změnit na velikost v době běhu, ovládací prvky ve formuláři by měly správně změnit velikost a změnit jejich polohu.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-103">If you're designing a form that the user can resize at run time, the controls on your form should resize and reposition properly.</span></span> <span data-ttu-id="f1cf6-104">Chcete-li změnit velikost ovládacích prvků dynamicky pomocí formuláře, můžete použít vlastnost <xref:System.Windows.Forms.Control.Anchor%2A> ovládacího prvku model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-104">To resize controls dynamically with the form, you can use the <xref:System.Windows.Forms.Control.Anchor%2A> property of Windows Forms controls.</span></span> <span data-ttu-id="f1cf6-105">Vlastnost <xref:System.Windows.Forms.Control.Anchor%2A> definuje pozici ukotvení ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-105">The <xref:System.Windows.Forms.Control.Anchor%2A> property defines an anchor position for the control.</span></span> <span data-ttu-id="f1cf6-106">Když je ovládací prvek ukotven do formuláře a změní se velikost formuláře, ovládací prvek zachovává vzdálenost mezi ovládacím prvkem a polohou kotvy.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-106">When a control is anchored to a form and the form is resized, the control maintains the distance between the control and the anchor positions.</span></span> <span data-ttu-id="f1cf6-107">Například pokud máte ovládací prvek <xref:System.Windows.Forms.TextBox>, který je ukotven k levému, pravému a dolnímu okraji formuláře, při změně velikosti formuláře <xref:System.Windows.Forms.TextBox> ovládací prvek změní velikost vodorovně tak, aby se zachovala stejná vzdálenost od pravé a levé strany formuláře.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-107">For example, if you have a <xref:System.Windows.Forms.TextBox> control that is anchored to the left, right, and bottom edges of the form, as the form is resized, the <xref:System.Windows.Forms.TextBox> control resizes horizontally so that it maintains the same distance from the right and left sides of the form.</span></span> <span data-ttu-id="f1cf6-108">Kromě toho se ovládací prvek umístí svisle přímo tak, aby jeho poloha byla vždy stejná jako vzdálenost od spodního okraje ve formuláři.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-108">In addition, the control positions itself vertically so that its location is always the same distance from the bottom edge of the form.</span></span> <span data-ttu-id="f1cf6-109">Pokud ovládací prvek není ukotven a dojde ke změně velikosti formuláře, poloha ovládacího prvku vztažena k okrajům formuláře je změněna.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-109">If a control is not anchored and the form is resized, the position of the control relative to the edges of the form is changed.</span></span>

<span data-ttu-id="f1cf6-110">Vlastnost <xref:System.Windows.Forms.Control.Anchor%2A> komunikuje s vlastností <xref:System.Windows.Forms.Control.AutoSize%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-110">The <xref:System.Windows.Forms.Control.Anchor%2A> property interacts with the <xref:System.Windows.Forms.Control.AutoSize%2A> property.</span></span> <span data-ttu-id="f1cf6-111">Další informace naleznete v tématu [Přehled vlastností AutoSize](autosize-property-overview.md).</span><span class="sxs-lookup"><span data-stu-id="f1cf6-111">For more information, see [AutoSize Property Overview](autosize-property-overview.md).</span></span>

## <a name="anchor-a-control-on-a-form"></a><span data-ttu-id="f1cf6-112">Ukotvení ovládacího prvku na formuláři</span><span class="sxs-lookup"><span data-stu-id="f1cf6-112">Anchor a control on a form</span></span>

1. <span data-ttu-id="f1cf6-113">V aplikaci Visual Studio vyberte ovládací prvek, který chcete ukotvit.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-113">In Visual Studio, select the control you want to anchor.</span></span>

    > [!NOTE]
    > <span data-ttu-id="f1cf6-114">Můžete ukotvit více ovládacích prvků současně stisknutím klávesy CTRL, kliknutím na každý ovládací prvek ho vybrat a potom podle zbytku tohoto postupu.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-114">You can anchor multiple controls simultaneously by pressing the CTRL key, clicking each control to select it, and then following the rest of this procedure.</span></span>

2. <span data-ttu-id="f1cf6-115">V okně **vlastnosti** klikněte na šipku napravo od vlastnosti <xref:System.Windows.Forms.Control.Anchor%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-115">In the **Properties** window, click the arrow to the right of the <xref:System.Windows.Forms.Control.Anchor%2A> property.</span></span>

     <span data-ttu-id="f1cf6-116">Zobrazí se editor, který zobrazuje více.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-116">An editor is displayed that shows a cross.</span></span>

3. <span data-ttu-id="f1cf6-117">Chcete-li nastavit kotvu, klikněte na horní, levou, pravou nebo dolní část křížení.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-117">To set an anchor, click the top, left, right, or bottom section of the cross.</span></span>

     <span data-ttu-id="f1cf6-118">Ovládací prvky jsou ukotveny ve výchozím nastavení směrem nahoru a doleva.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-118">Controls are anchored to the top and left by default.</span></span>

4. <span data-ttu-id="f1cf6-119">Chcete-li vymazat stranu ovládacího prvku, který je ukotven, klikněte na něj ve vzájemném ramene.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-119">To clear a side of the control that has been anchored, click that arm of the cross.</span></span>

5. <span data-ttu-id="f1cf6-120">Chcete-li zavřít editor vlastností <xref:System.Windows.Forms.Control.Anchor%2A>, klikněte znovu na název vlastnosti <xref:System.Windows.Forms.Control.Anchor%2A>.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-120">To close the <xref:System.Windows.Forms.Control.Anchor%2A> property editor, click the <xref:System.Windows.Forms.Control.Anchor%2A> property name again.</span></span>

<span data-ttu-id="f1cf6-121">Když je formulář zobrazen v době běhu, změní se velikost ovládacího prvku tak, aby zůstala umístěná ve stejné vzdálenosti od okraje formuláře.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-121">When your form is displayed at run time, the control resizes to remain positioned at the same distance from the edge of the form.</span></span> <span data-ttu-id="f1cf6-122">Vzdálenost od ukotveného okraje vždy zůstane stejná jako vzdálenost definovaná při umístění ovládacího prvku do Návrhář formulářů.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-122">The distance from the anchored edge always remains the same as the distance defined when the control is positioned in the Windows Forms Designer.</span></span>

> [!NOTE]
> <span data-ttu-id="f1cf6-123">Některé ovládací prvky, například ovládací prvek <xref:System.Windows.Forms.ComboBox>, mají omezení na jejich výšku.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-123">Certain controls, such as the <xref:System.Windows.Forms.ComboBox> control, have a limit to their height.</span></span> <span data-ttu-id="f1cf6-124">Ukotvení ovládacího prvku do dolní části jeho formuláře nebo kontejneru nemůže vynutit, aby ovládací prvek překročil limit výšky.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-124">Anchoring the control to the bottom of its form or container cannot force the control to exceed its height limit.</span></span>

<span data-ttu-id="f1cf6-125">Zděděné ovládací prvky musí být `Protected`, aby je bylo možné ukotvit.</span><span class="sxs-lookup"><span data-stu-id="f1cf6-125">Inherited controls must be `Protected` to be able to be anchored.</span></span> <span data-ttu-id="f1cf6-126">Chcete-li změnit úroveň přístupu ovládacího prvku, nastavte jeho vlastnost `Modifiers` v okně **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="f1cf6-126">To change the access level of a control, set its `Modifiers` property in the **Properties** window.</span></span>

## <a name="see-also"></a><span data-ttu-id="f1cf6-127">Viz také</span><span class="sxs-lookup"><span data-stu-id="f1cf6-127">See also</span></span>

- [<span data-ttu-id="f1cf6-128">Windows Forms – ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="f1cf6-128">Windows Forms Controls</span></span>](index.md)
- [<span data-ttu-id="f1cf6-129">Přehled vlastnosti AutoSize</span><span class="sxs-lookup"><span data-stu-id="f1cf6-129">AutoSize Property Overview</span></span>](autosize-property-overview.md)
- [<span data-ttu-id="f1cf6-130">Postupy: Vložení ovládacích prvků ve Windows Forms do doku</span><span class="sxs-lookup"><span data-stu-id="f1cf6-130">How to: Dock Controls on Windows Forms</span></span>](how-to-dock-controls-on-windows-forms.md)
- [<span data-ttu-id="f1cf6-131">Postupy: Uspořádání ovládacích prvků na formuláři Windows Forms s použitím ovládacího prvku FlowLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f1cf6-131">Walkthrough: Arranging Controls on Windows Forms Using a FlowLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-flowlayoutpanel.md)
- [<span data-ttu-id="f1cf6-132">Postupy: Uspořádání ovládacích prvků na Windows Forms s použitím ovládacího prvku TableLayoutPanel</span><span class="sxs-lookup"><span data-stu-id="f1cf6-132">Walkthrough: Arranging Controls on Windows Forms Using a TableLayoutPanel</span></span>](walkthrough-arranging-controls-on-windows-forms-using-a-tablelayoutpanel.md)
- [<span data-ttu-id="f1cf6-133">Návod: Rozvrhování ovládacích prvků Windows Forms s odsazením, okraji a s vlastností AutoSize</span><span class="sxs-lookup"><span data-stu-id="f1cf6-133">Walkthrough: Laying Out Windows Forms Controls with Padding, Margins, and the AutoSize Property</span></span>](windows-forms-controls-padding-autosize.md)
