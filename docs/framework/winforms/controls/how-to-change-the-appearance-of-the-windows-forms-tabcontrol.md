---
title: Změna vzhledu TabControl
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- icons [Windows Forms], displaying on tabs
- TabControl control [Windows Forms], changing page appearance
- tabs [Windows Forms], controlling appearance
- buttons [Windows Forms], displaying tabs as
ms.assetid: 7c6cc443-ed62-4d26-b94d-b8913b44f773
ms.openlocfilehash: 056070177e6bbaba0c93c7b94f5adfd7887be6a8
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746609"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a><span data-ttu-id="c98a4-102">Postupy: Změna vzhledu Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="c98a4-102">How to: Change the Appearance of the Windows Forms TabControl</span></span>
<span data-ttu-id="c98a4-103">Můžete změnit vzhled karet v model Windows Forms pomocí vlastností <xref:System.Windows.Forms.TabControl> a objektů <xref:System.Windows.Forms.TabPage>, které tvoří jednotlivé karty na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="c98a4-103">You can change the appearance of tabs in Windows Forms by using properties of the <xref:System.Windows.Forms.TabControl> and the <xref:System.Windows.Forms.TabPage> objects that make up the individual tabs on the control.</span></span> <span data-ttu-id="c98a4-104">Nastavením těchto vlastností můžete zobrazit obrázky na kartách, zobrazit karty svisle namísto horizontálně, Zobrazit více řádků karet a povolit nebo zakázat karty programově.</span><span class="sxs-lookup"><span data-stu-id="c98a4-104">By setting these properties, you can display images on tabs, display tabs vertically instead of horizontally, display multiple rows of tabs, and enable or disable tabs programmatically.</span></span>  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a><span data-ttu-id="c98a4-105">Zobrazení ikony v části popisku na kartě</span><span class="sxs-lookup"><span data-stu-id="c98a4-105">To display an icon on the label part of a tab</span></span>  
  
1. <span data-ttu-id="c98a4-106">Přidejte ovládací prvek <xref:System.Windows.Forms.ImageList> do formuláře.</span><span class="sxs-lookup"><span data-stu-id="c98a4-106">Add an <xref:System.Windows.Forms.ImageList> control to the form.</span></span>  
  
2. <span data-ttu-id="c98a4-107">Přidejte obrázky do seznamu obrázků.</span><span class="sxs-lookup"><span data-stu-id="c98a4-107">Add images to the image list.</span></span>  
  
     <span data-ttu-id="c98a4-108">Další informace o seznamech obrázků naleznete v tématu [Komponenta ImageList](imagelist-component-windows-forms.md) a [Postupy: Přidání nebo odebrání obrázků s komponentou model Windows Forms ImageList](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="c98a4-108">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
3. <span data-ttu-id="c98a4-109">Nastavte vlastnost <xref:System.Windows.Forms.TabControl.ImageList%2A> <xref:System.Windows.Forms.TabControl> na ovládací prvek <xref:System.Windows.Forms.ImageList>.</span><span class="sxs-lookup"><span data-stu-id="c98a4-109">Set the <xref:System.Windows.Forms.TabControl.ImageList%2A> property of the <xref:System.Windows.Forms.TabControl> to the <xref:System.Windows.Forms.ImageList> control.</span></span>  
  
4. <span data-ttu-id="c98a4-110">Nastavte vlastnost <xref:System.Windows.Forms.TabPage.ImageIndex%2A> <xref:System.Windows.Forms.TabPage> na index příslušného obrázku v seznamu.</span><span class="sxs-lookup"><span data-stu-id="c98a4-110">Set the <xref:System.Windows.Forms.TabPage.ImageIndex%2A> property of the <xref:System.Windows.Forms.TabPage> to the index of an appropriate image in the list.</span></span>  
  
### <a name="to-create-multiple-rows-of-tabs"></a><span data-ttu-id="c98a4-111">Vytvoření více řádků karet</span><span class="sxs-lookup"><span data-stu-id="c98a4-111">To create multiple rows of tabs</span></span>  
  
1. <span data-ttu-id="c98a4-112">Přidejte požadovaný počet stránek karty.</span><span class="sxs-lookup"><span data-stu-id="c98a4-112">Add the number of tab pages you want.</span></span>  
  
2. <span data-ttu-id="c98a4-113">Nastavte vlastnost <xref:System.Windows.Forms.TabControl.Multiline%2A> <xref:System.Windows.Forms.TabControl> na `true`.</span><span class="sxs-lookup"><span data-stu-id="c98a4-113">Set the <xref:System.Windows.Forms.TabControl.Multiline%2A> property of the <xref:System.Windows.Forms.TabControl> to `true`.</span></span>  
  
3. <span data-ttu-id="c98a4-114">Pokud se karty ještě neobjevují v několika řádcích, nastavte vlastnost <xref:System.Windows.Forms.Control.Width%2A> <xref:System.Windows.Forms.TabControl> tak, aby byla užší než všechny karty.</span><span class="sxs-lookup"><span data-stu-id="c98a4-114">If the tabs do not already appear in multiple rows, set the <xref:System.Windows.Forms.Control.Width%2A> property of the <xref:System.Windows.Forms.TabControl> to be narrower than all the tabs.</span></span>  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a><span data-ttu-id="c98a4-115">Uspořádání karet na straně ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="c98a4-115">To arrange tabs on the side of the control</span></span>  
  
- <span data-ttu-id="c98a4-116">Vlastnost <xref:System.Windows.Forms.TabControl.Alignment%2A> <xref:System.Windows.Forms.TabControl> nastavte na <xref:System.Windows.Forms.TabAlignment.Left> nebo <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="c98a4-116">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAlignment.Left> or <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a><span data-ttu-id="c98a4-117">Programové povolení nebo zakázání všech ovládacích prvků na kartě</span><span class="sxs-lookup"><span data-stu-id="c98a4-117">To programmatically enable or disable all controls on a tab</span></span>  
  
1. <span data-ttu-id="c98a4-118">Vlastnost <xref:System.Windows.Forms.TabPage.Enabled%2A> <xref:System.Windows.Forms.TabPage> nastavte na `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="c98a4-118">Set the <xref:System.Windows.Forms.TabPage.Enabled%2A> property of the <xref:System.Windows.Forms.TabPage> to `true` or `false`.</span></span>  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a><span data-ttu-id="c98a4-119">Zobrazení karet jako tlačítek</span><span class="sxs-lookup"><span data-stu-id="c98a4-119">To display tabs as buttons</span></span>  
  
- <span data-ttu-id="c98a4-120">Vlastnost <xref:System.Windows.Forms.TabControl.Appearance%2A> <xref:System.Windows.Forms.TabControl> nastavte na <xref:System.Windows.Forms.TabAppearance.Buttons> nebo <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span><span class="sxs-lookup"><span data-stu-id="c98a4-120">Set the <xref:System.Windows.Forms.TabControl.Appearance%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAppearance.Buttons> or <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c98a4-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c98a4-121">See also</span></span>

- [<span data-ttu-id="c98a4-122">Ovládací prvek TabControl</span><span class="sxs-lookup"><span data-stu-id="c98a4-122">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="c98a4-123">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="c98a4-123">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="c98a4-124">Postupy: Přidání ovládacího prvku na kartu</span><span class="sxs-lookup"><span data-stu-id="c98a4-124">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="c98a4-125">Postupy: Zákaz karet</span><span class="sxs-lookup"><span data-stu-id="c98a4-125">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="c98a4-126">Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="c98a4-126">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
