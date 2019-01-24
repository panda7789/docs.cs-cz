---
title: 'Postupy: Zákaz přidávání a odstraňování položek DataRepeater (Visual Studio)'
ms.date: 07/20/2015
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, disabling delete
- DataRepeater, disabling add
ms.assetid: 298d8f60-ddfe-4361-ab66-cf76d0df5220
ms.openlocfilehash: 3a304132d0514da4c19811be2536c9516e2838f0
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54618539"
---
# <a name="how-to-disable-adding-and-deleting-datarepeater-items-visual-studio"></a><span data-ttu-id="468c6-102">Postupy: Zákaz přidávání a odstraňování položek DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="468c6-102">How to: Disable Adding and Deleting DataRepeater Items (Visual Studio)</span></span>
<span data-ttu-id="468c6-103">Ve výchozím nastavení, můžete přidávat a odstraňovat položky v uživatelů <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="468c6-103">By default, users can add and delete items in a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span> <span data-ttu-id="468c6-104">Uživatele můžete přidat novou položku stisknutím kombinace kláves CTRL + N při <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> má právě fokus, nebo kliknutím **AddNewItem** tlačítko <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="468c6-104">Users can add a new item by pressing CTRL+N when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **AddNewItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span> <span data-ttu-id="468c6-105">Uživatelé, mohou odstranit položku stisknutím kombinace kláves ODSTRANĚNY při <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> má právě fokus, nebo kliknutím **DeleteItem** tlačítko <xref:System.Windows.Forms.BindingNavigator> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="468c6-105">Users can delete an item by pressing DELETE when a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItemEventArgs.DataRepeaterItem%2A> has focus or by clicking the **DeleteItem** button on the <xref:System.Windows.Forms.BindingNavigator> control.</span></span>  
  
 <span data-ttu-id="468c6-106">Můžete zakázat přidávání nebo odstraňování v době návrhu nebo v době běhu.</span><span class="sxs-lookup"><span data-stu-id="468c6-106">You can disable adding and/or deleting at design time or at run time.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-design-time"></a><span data-ttu-id="468c6-107">Chcete-li zakázat přidávání a odstraňování v době návrhu</span><span class="sxs-lookup"><span data-stu-id="468c6-107">To disable adding and deleting at design time</span></span>  
  
1.  <span data-ttu-id="468c6-108">V Návrháři formulářů Windows, vyberte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="468c6-108">In the Windows Forms Designer, select the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="468c6-109">Musíte vybrat dolní části ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="468c6-109">You must select the lower section of the control.</span></span> <span data-ttu-id="468c6-110">Pokud jste vybrali v části šablony položky, zobrazí se různé sady vlastností.</span><span class="sxs-lookup"><span data-stu-id="468c6-110">If you select the item template section, a different set of properties will be displayed.</span></span>  
  
2.  <span data-ttu-id="468c6-111">V okně Vlastnosti nastavte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> vlastnost **False**.</span><span class="sxs-lookup"><span data-stu-id="468c6-111">In the Properties window, set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToAddItems%2A> property to **False**.</span></span>  
  
3.  <span data-ttu-id="468c6-112">Nastavte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> vlastnost **False**.</span><span class="sxs-lookup"><span data-stu-id="468c6-112">Set the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.AllowUserToDeleteItems%2A> property to **False**.</span></span>  
  
4.  <span data-ttu-id="468c6-113">V Návrháři formulářů Windows, vyberte <xref:System.Windows.Forms.BindingNavigator> ovládací prvek a potom klikněte na tlačítko **AddNewItem** (tlačítko se symbolem plus na něj).</span><span class="sxs-lookup"><span data-stu-id="468c6-113">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **AddNewItem** button (the button with a plus sign on it).</span></span>  
  
5.  <span data-ttu-id="468c6-114">V okně Vlastnosti nastavte <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> vlastnost **False**.</span><span class="sxs-lookup"><span data-stu-id="468c6-114">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
6.  <span data-ttu-id="468c6-115">V Návrháři formulářů Windows, vyberte <xref:System.Windows.Forms.BindingNavigator> ovládací prvek a potom klikněte na tlačítko **DeleteItem** (tlačítko s černým symbolem X na něj).</span><span class="sxs-lookup"><span data-stu-id="468c6-115">In the Windows Forms Designer, select the <xref:System.Windows.Forms.BindingNavigator> control, and then click the **DeleteItem** button (the button with a red X on it).</span></span>  
  
7.  <span data-ttu-id="468c6-116">V okně Vlastnosti nastavte <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> vlastnost **False**.</span><span class="sxs-lookup"><span data-stu-id="468c6-116">In the Properties window, set the <xref:System.Windows.Forms.ToolBarButton.Enabled%2A> property to **False**.</span></span>  
  
8.  <span data-ttu-id="468c6-117">V panelu komponent, vyberte <xref:System.Windows.Forms.BindingSource> ke kterému <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> je vázán.</span><span class="sxs-lookup"><span data-stu-id="468c6-117">In the Component Tray, select the <xref:System.Windows.Forms.BindingSource> to which the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> is bound.</span></span>  
  
9. <span data-ttu-id="468c6-118">V okně Vlastnosti nastavte <xref:System.Windows.Forms.BindingSource.AllowNew%2A> vlastnost **False**.</span><span class="sxs-lookup"><span data-stu-id="468c6-118">In the Properties window, set the <xref:System.Windows.Forms.BindingSource.AllowNew%2A> property to **False**.</span></span>  
  
10. <span data-ttu-id="468c6-119">V Návrháři formulářů Windows, dvakrát klikněte **DeleteItem** tlačítko k otevření editoru kódu.</span><span class="sxs-lookup"><span data-stu-id="468c6-119">In the Windows Forms Designer, double-click the **DeleteItem** button to open the Code Editor.</span></span>  
  
11. <span data-ttu-id="468c6-120">V rozevíracím seznamu událostí vyberte `BindingNavigatorDeleteItem_EnabledChanged` událostí.</span><span class="sxs-lookup"><span data-stu-id="468c6-120">In the Events drop-down list, select the `BindingNavigatorDeleteItem_EnabledChanged` event.</span></span>  
  
12. <span data-ttu-id="468c6-121">Přidejte následující kód, který `BindingNavigatorDeleteItem_EnabledChanged` obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="468c6-121">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="468c6-122">Tento krok je nezbytný, protože <xref:System.Windows.Forms.BindingSource> vám umožní **DeleteItem** tlačítko pokaždé, když se změní aktuální záznam.</span><span class="sxs-lookup"><span data-stu-id="468c6-122">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
### <a name="to-disable-adding-and-deleting-at-run-time"></a><span data-ttu-id="468c6-123">Chcete-li zakázat přidávání a odstraňování v době běhu</span><span class="sxs-lookup"><span data-stu-id="468c6-123">To disable adding and deleting at run time</span></span>  
  
1.  <span data-ttu-id="468c6-124">V Návrháři formulářů Windows klikněte dvakrát na formuláři se otevřít Editor kódu.</span><span class="sxs-lookup"><span data-stu-id="468c6-124">In the Windows Forms Designer, double-click the form to open the Code Editor.</span></span>  
  
2.  <span data-ttu-id="468c6-125">Přidejte následující kód, který `Form_Load` události:</span><span class="sxs-lookup"><span data-stu-id="468c6-125">Add the following code to the `Form_Load` event:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#2](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_2.vb)]  
  
3.  <span data-ttu-id="468c6-126">Přidejte následující kód, který `BindingNavigatorDeleteItem_EnabledChanged` obslužné rutiny události:</span><span class="sxs-lookup"><span data-stu-id="468c6-126">Add the following code to the `BindingNavigatorDeleteItem_EnabledChanged` event handler:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterDisableAddDelete#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-disable-adding-and-deleting-datarepeater-items-visual-studio_1.vb)]  
  
    > [!NOTE]
    >  <span data-ttu-id="468c6-127">Tento krok je nezbytný, protože <xref:System.Windows.Forms.BindingSource> vám umožní **DeleteItem** tlačítko pokaždé, když se změní aktuální záznam.</span><span class="sxs-lookup"><span data-stu-id="468c6-127">This step is necessary because the <xref:System.Windows.Forms.BindingSource> will enable the **DeleteItem** button every time that the current record changes.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="468c6-128">Viz také:</span><span class="sxs-lookup"><span data-stu-id="468c6-128">See also</span></span>
- <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>
- [<span data-ttu-id="468c6-129">Úvod do ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="468c6-129">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)
- [<span data-ttu-id="468c6-130">Řešení potíží s ovládacím prvkem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="468c6-130">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
