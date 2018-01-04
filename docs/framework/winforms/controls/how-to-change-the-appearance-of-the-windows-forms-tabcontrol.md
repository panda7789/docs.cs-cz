---
title: "Postupy: Změna vzhledu Windows Forms TabControl"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 61fb11b79459da14384af974dbc403024faa377f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-change-the-appearance-of-the-windows-forms-tabcontrol"></a><span data-ttu-id="f7545-102">Postupy: Změna vzhledu Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="f7545-102">How to: Change the Appearance of the Windows Forms TabControl</span></span>
<span data-ttu-id="f7545-103">Můžete změnit vzhled karet ve Windows Forms pomocí vlastnosti <xref:System.Windows.Forms.TabControl> a <xref:System.Windows.Forms.TabPage> objekty, které tvoří na jednotlivé karty na ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="f7545-103">You can change the appearance of tabs in Windows Forms by using properties of the <xref:System.Windows.Forms.TabControl> and the <xref:System.Windows.Forms.TabPage> objects that make up the individual tabs on the control.</span></span> <span data-ttu-id="f7545-104">Pomocí nastavení těchto vlastností, můžete zobrazení obrázků na karty, zobrazení karet svisle místo vodorovně, zobrazit více řádků karet a povolit nebo zakázat karty prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="f7545-104">By setting these properties, you can display images on tabs, display tabs vertically instead of horizontally, display multiple rows of tabs, and enable or disable tabs programmatically.</span></span>  
  
### <a name="to-display-an-icon-on-the-label-part-of-a-tab"></a><span data-ttu-id="f7545-105">Zobrazit ikonu na část popisek karty</span><span class="sxs-lookup"><span data-stu-id="f7545-105">To display an icon on the label part of a tab</span></span>  
  
1.  <span data-ttu-id="f7545-106">Přidat <xref:System.Windows.Forms.ImageList> ovládacího prvku do formuláře.</span><span class="sxs-lookup"><span data-stu-id="f7545-106">Add an <xref:System.Windows.Forms.ImageList> control to the form.</span></span>  
  
2.  <span data-ttu-id="f7545-107">Přidání bitové kopie do seznamu obrázků.</span><span class="sxs-lookup"><span data-stu-id="f7545-107">Add images to the image list.</span></span>  
  
     <span data-ttu-id="f7545-108">Další informace o seznamech obrázků najdete v tématu [ImageList – komponenta](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) a [postupy: Přidání nebo odebrání obrázků s komponentou Windows Forms ImageList](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span><span class="sxs-lookup"><span data-stu-id="f7545-108">For more information about image lists, see [ImageList Component](../../../../docs/framework/winforms/controls/imagelist-component-windows-forms.md) and [How to: Add or Remove Images with the Windows Forms ImageList Component](../../../../docs/framework/winforms/controls/how-to-add-or-remove-images-with-the-windows-forms-imagelist-component.md).</span></span>  
  
3.  <span data-ttu-id="f7545-109">Nastavte <xref:System.Windows.Forms.TabControl.ImageList%2A> vlastnost <xref:System.Windows.Forms.TabControl> k <xref:System.Windows.Forms.ImageList> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f7545-109">Set the <xref:System.Windows.Forms.TabControl.ImageList%2A> property of the <xref:System.Windows.Forms.TabControl> to the <xref:System.Windows.Forms.ImageList> control.</span></span>  
  
4.  <span data-ttu-id="f7545-110">Nastavte <xref:System.Windows.Forms.TabPage.ImageIndex%2A> vlastnost <xref:System.Windows.Forms.TabPage> indexu příslušné bitové kopie v seznamu.</span><span class="sxs-lookup"><span data-stu-id="f7545-110">Set the <xref:System.Windows.Forms.TabPage.ImageIndex%2A> property of the <xref:System.Windows.Forms.TabPage> to the index of an appropriate image in the list.</span></span>  
  
### <a name="to-create-multiple-rows-of-tabs"></a><span data-ttu-id="f7545-111">Chcete-li vytvořit více řádků karty</span><span class="sxs-lookup"><span data-stu-id="f7545-111">To create multiple rows of tabs</span></span>  
  
1.  <span data-ttu-id="f7545-112">Číslo stránky karet, které chcete přidáte.</span><span class="sxs-lookup"><span data-stu-id="f7545-112">Add the number of tab pages you want.</span></span>  
  
2.  <span data-ttu-id="f7545-113">Nastavte <xref:System.Windows.Forms.TabControl.Multiline%2A> vlastnost <xref:System.Windows.Forms.TabControl> k `true`.</span><span class="sxs-lookup"><span data-stu-id="f7545-113">Set the <xref:System.Windows.Forms.TabControl.Multiline%2A> property of the <xref:System.Windows.Forms.TabControl> to `true`.</span></span>  
  
3.  <span data-ttu-id="f7545-114">Pokud karty se již nezobrazují ve více řádků, nastavte <xref:System.Windows.Forms.Control.Width%2A> vlastnost <xref:System.Windows.Forms.TabControl> být užší než všechny karty.</span><span class="sxs-lookup"><span data-stu-id="f7545-114">If the tabs do not already appear in multiple rows, set the <xref:System.Windows.Forms.Control.Width%2A> property of the <xref:System.Windows.Forms.TabControl> to be narrower than all the tabs.</span></span>  
  
### <a name="to-arrange-tabs-on-the-side-of-the-control"></a><span data-ttu-id="f7545-115">Chcete-li uspořádat karty stranu ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="f7545-115">To arrange tabs on the side of the control</span></span>  
  
-   <span data-ttu-id="f7545-116">Nastavte <xref:System.Windows.Forms.TabControl.Alignment%2A> vlastnost <xref:System.Windows.Forms.TabControl> k <xref:System.Windows.Forms.TabAlignment.Left> nebo <xref:System.Windows.Forms.TabAlignment.Right>.</span><span class="sxs-lookup"><span data-stu-id="f7545-116">Set the <xref:System.Windows.Forms.TabControl.Alignment%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAlignment.Left> or <xref:System.Windows.Forms.TabAlignment.Right>.</span></span>  
  
### <a name="to-programmatically-enable-or-disable-all-controls-on-a-tab"></a><span data-ttu-id="f7545-117">Prostřednictvím kódu programu povolit nebo zakázat všechny ovládací prvky na kartě</span><span class="sxs-lookup"><span data-stu-id="f7545-117">To programmatically enable or disable all controls on a tab</span></span>  
  
1.  <span data-ttu-id="f7545-118">Nastavte <xref:System.Windows.Forms.TabPage.Enabled%2A> vlastnost <xref:System.Windows.Forms.TabPage> k `true` nebo `false`.</span><span class="sxs-lookup"><span data-stu-id="f7545-118">Set the <xref:System.Windows.Forms.TabPage.Enabled%2A> property of the <xref:System.Windows.Forms.TabPage> to `true` or `false`.</span></span>  
  
    ```vb  
    TabPage1.Enabled = False  
    ```  
  
    ```csharp  
    tabPage1.Enabled = false;  
    ```  
  
    ```cpp  
    tabPage1->Enabled = false;  
    ```  
  
### <a name="to-display-tabs-as-buttons"></a><span data-ttu-id="f7545-119">K zobrazení karet jako tlačítka</span><span class="sxs-lookup"><span data-stu-id="f7545-119">To display tabs as buttons</span></span>  
  
-   <span data-ttu-id="f7545-120">Nastavte <xref:System.Windows.Forms.TabControl.Appearance%2A> vlastnost <xref:System.Windows.Forms.TabControl> k <xref:System.Windows.Forms.TabAppearance.Buttons> nebo <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span><span class="sxs-lookup"><span data-stu-id="f7545-120">Set the <xref:System.Windows.Forms.TabControl.Appearance%2A> property of the <xref:System.Windows.Forms.TabControl> to <xref:System.Windows.Forms.TabAppearance.Buttons> or <xref:System.Windows.Forms.TabAppearance.FlatButtons>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7545-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7545-121">See Also</span></span>  
 [<span data-ttu-id="f7545-122">Ovládací prvek TabControl</span><span class="sxs-lookup"><span data-stu-id="f7545-122">TabControl Control</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-windows-forms.md)  
 [<span data-ttu-id="f7545-123">Přehled ovládacího prvku TabControl</span><span class="sxs-lookup"><span data-stu-id="f7545-123">TabControl Control Overview</span></span>](../../../../docs/framework/winforms/controls/tabcontrol-control-overview-windows-forms.md)  
 [<span data-ttu-id="f7545-124">Postupy: Přidání ovládacího prvku na kartu</span><span class="sxs-lookup"><span data-stu-id="f7545-124">How to: Add a Control to a Tab Page</span></span>](../../../../docs/framework/winforms/controls/how-to-add-a-control-to-a-tab-page.md)  
 [<span data-ttu-id="f7545-125">Postupy: Zákaz karet</span><span class="sxs-lookup"><span data-stu-id="f7545-125">How to: Disable Tab Pages</span></span>](../../../../docs/framework/winforms/controls/how-to-disable-tab-pages.md)  
 [<span data-ttu-id="f7545-126">Postupy: Přidání a odebrání karet pomocí ovládacího prvku Windows Forms TabControl</span><span class="sxs-lookup"><span data-stu-id="f7545-126">How to: Add and Remove Tabs with the Windows Forms TabControl</span></span>](../../../../docs/framework/winforms/controls/how-to-add-and-remove-tabs-with-the-windows-forms-tabcontrol.md)
