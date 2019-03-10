---
title: 'Postupy: Změna vzhledu ovládacího prvku Windows Forms TabControl'
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
ms.openlocfilehash: 642115eeb61649eb369058947e5347d4389182a0
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57702409"
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a><span data-ttu-id="323ba-102">Postupy: Změna vzhledu ovládacího prvku Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="323ba-102">How to: Change the Appearance of the Windows Forms TabControl</span></span>
<span data-ttu-id="323ba-103">Můžete změnit vzhled karty ve Windows Forms pomocí vlastnosti <xref:System.Windows.Forms.TabControl> a <xref:System.Windows.Forms.TabPage> objekty, které tvoří jednotlivé karty na ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="323ba-103">You can change the appearance of tabs in Windows Forms by using properties of the <xref:System.Windows.Forms.TabControl> and the <xref:System.Windows.Forms.TabPage> objects that make up the individual tabs on the control.</span></span> <span data-ttu-id="323ba-104">Nastavením těchto vlastností můžete zobrazit obrázky na karty, zobrazení karet svisle namísto vodorovně, zobrazit více řádků karet a povolit nebo zakázat karty prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="323ba-104">By setting these properties, you can display images on tabs, display tabs vertically instead of horizontally, display multiple rows of tabs, and enable or disable tabs programmatically.</span></span>  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a><span data-ttu-id="323ba-105">Chcete-li zobrazit ikonu v části popisek karty</span><span class="sxs-lookup"><span data-stu-id="323ba-105">To display an icon on the label part of a tab</span></span>  
  
1.  <span data-ttu-id="323ba-106">Přidat <xref:System.Windows.Forms.ImageList> ovládacího prvku na formuláři.</span><span class="sxs-lookup"><span data-stu-id="323ba-106">Add an <xref:System.Windows.Forms.ImageList> control to the form.</span></span>  
  
2.  <span data-ttu-id="323ba-107">Přidání obrázků do seznamu obrázků.</span><span class="sxs-lookup"><span data-stu-id="323ba-107">Add images to the image list.</span></span>  
  
     <span data-ttu-id="323ba-108">Další informace o seznamech image, najdete v části [komponenty ImageList](imagelist-component-windows-forms.md) a [jak: Přidání a odebrání obrázků se Windows Forms ImageList – komponenta](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="323ba-108">For more information about image lists, see [ImageList Component](imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
3.  <span data-ttu-id="323ba-109">Nastavte <xref:System.Windows.Forms.TabControl.ImageList%2A> vlastnost <xref:System.Windows.Forms.TabControl> k <xref:System.Windows.Forms.ImageList> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="323ba-109">Set the <xref:System.Windows.Forms.TabControl.ImageList%2A> property of the <xref:System.Windows.Forms.TabControl> to the <xref:System.Windows.Forms.ImageList> control.</span></span>  
  
4.  <span data-ttu-id="323ba-110">Nastavte <xref:System.Windows.Forms.TabPage.ImageIndex%2A> vlastnost <xref:System.Windows.Forms.TabPage> do indexu v seznamu odpovídající image.</span><span class="sxs-lookup"><span data-stu-id="323ba-110">Set the <xref:System.Windows.Forms.TabPage.ImageIndex%2A> property of the <xref:System.Windows.Forms.TabPage> to the index of an appropriate image in the list.</span></span>  
  
### <a name="to-create-multiple-rows-of-tabs"></a><span data-ttu-id="323ba-111">Chcete-li vytvořit více řádků karet</span><span class="sxs-lookup"><span data-stu-id="323ba-111">To create multiple rows of tabs</span></span>  
  
1.  <span data-ttu-id="323ba-112">Číslo stránky karet, které chcete přidáte.</span><span class="sxs-lookup"><span data-stu-id="323ba-112">Add the number of tab pages you want.</span></span>  
  
2.  <span data-ttu-id="323ba-113">Nastavte <xref:System.Windows.Forms.TabControl.Multiline%2A> vlastnost <xref:System.Windows.Forms.TabControl> k `true`.</span><span class="sxs-lookup"><span data-stu-id="323ba-113">Set the <xref:System.Windows.Forms.TabControl.Multiline%2A> property of the <xref:System.Windows.Forms.TabControl> to `true`.</span></span>  
  
3.  <span data-ttu-id="323ba-114">Pokud na kartách se už nezobrazují v více řádků, nastavte <xref:System.Windows.Forms.Control.Width%2A> vlastnost <xref:System.Windows.Forms.TabControl> bude užší než všechny karty.</span><span class="sxs-lookup"><span data-stu-id="323ba-114">If the tabs do not already appear in multiple rows, set the <xref:System.Windows.Forms.Control.Width%2A> property of the <xref:System.Windows.Forms.TabControl> to be narrower than all the tabs.</span></span>  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a><span data-ttu-id="323ba-115">Uspořádání karet Toolbar ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="323ba-115">To arrange tabs on the side of the control</span></span>  
  
-   <span data-ttu-id="323ba-116">Nastavte <xref:System.Windows.Forms.TabControl.Alignment%2A> vlastnost <xref:System.Windows.Forms.TabControl> k <xref:System.Windows.Forms.TabAlignment.Left> nebo <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="323ba-116">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAlignment.Left> or <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a><span data-ttu-id="323ba-117">Prostřednictvím kódu programu povolit nebo zakázat všechny ovládací prvky na kartě</span><span class="sxs-lookup"><span data-stu-id="323ba-117">To programmatically enable or disable all controls on a tab</span></span>  
  
1.  <span data-ttu-id="323ba-118">Nastavte <xref:System.Windows.Forms.TabPage.Enabled%2A> vlastnost <xref:System.Windows.Forms.TabPage> k `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="323ba-118">Set the <xref:System.Windows.Forms.TabPage.Enabled%2A> property of the <xref:System.Windows.Forms.TabPage> to `true` or `false`.</span></span>  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a><span data-ttu-id="323ba-119">Chcete-li zobrazit karty jako tlačítka</span><span class="sxs-lookup"><span data-stu-id="323ba-119">To display tabs as buttons</span></span>  
  
-   <span data-ttu-id="323ba-120">Nastavte <xref:System.Windows.Forms.TabControl.Appearance%2A> vlastnost <xref:System.Windows.Forms.TabControl> k <xref:System.Windows.Forms.TabAppearance.Buttons> nebo <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span><span class="sxs-lookup"><span data-stu-id="323ba-120">Set the <xref:System.Windows.Forms.TabControl.Appearance%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAppearance.Buttons> or <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="323ba-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="323ba-121">See also</span></span>
- [<span data-ttu-id="323ba-122">Ovládací prvek TabControl</span><span class="sxs-lookup"><span data-stu-id="323ba-122">TabControl Control</span></span>](tabcontrol-control-windows-forms.md)
- [<span data-ttu-id="323ba-123">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="323ba-123">TabControl Control Overview</span></span>](tabcontrol-control-overview-windows-forms.md)
- [<span data-ttu-id="323ba-124">Postupy: Přidání ovládacího prvku do stránky karty</span><span class="sxs-lookup"><span data-stu-id="323ba-124">How to: Add a Control to a Tab Page</span></span>](how-to-add-a-control-to-a-tab-page.md)
- [<span data-ttu-id="323ba-125">Postupy: Zákaz stránek karet</span><span class="sxs-lookup"><span data-stu-id="323ba-125">How to: Disable Tab Pages</span></span>](how-to-disable-tab-pages.md)
- [<span data-ttu-id="323ba-126">Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="323ba-126">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
