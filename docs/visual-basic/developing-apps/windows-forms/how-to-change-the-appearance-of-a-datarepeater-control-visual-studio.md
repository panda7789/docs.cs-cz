---
title: "Postupy: Změna vzhledu ovládacího prvku DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataRepeater, customizing
- DataRepeater, changing run time appearance
ms.assetid: 2af6dfce-760b-489e-b863-8da967f315c3
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 585ff4c942185f3199fe6e9e47a4ebd9f1f0a478
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-change-the-appearance-of-a-datarepeater-control-visual-studio"></a><span data-ttu-id="eb1f7-102">Postupy: Změna vzhledu ovládacího prvku DataRepeater (Visual Studio)</span><span class="sxs-lookup"><span data-stu-id="eb1f7-102">How to: Change the Appearance of a DataRepeater Control (Visual Studio)</span></span>
<span data-ttu-id="eb1f7-103">Můžete změnit vzhled <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku v době návrhu nastavením vlastnosti nebo v době běhu zpracování <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> událostí.</span><span class="sxs-lookup"><span data-stu-id="eb1f7-103">You can change the appearance of a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control at design time by setting properties or at run time by handling the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event.</span></span>  
  
 <span data-ttu-id="eb1f7-104">Vlastnosti, které můžete nastavit v době návrhu, když je vybrána sekce šablony ovládacího prvku bude opakovat pro každý <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> za běhu.</span><span class="sxs-lookup"><span data-stu-id="eb1f7-104">Properties that you set at design time when the item template section of the control is selected will be repeated for each <xref:Microsoft.VisualBasic.PowerPacks.DataRepeaterItem> at run time.</span></span> <span data-ttu-id="eb1f7-105">Vlastnosti týkající se vzhledu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> vlastní ovládací prvek se nebude zobrazovat v době běhu je ponechán pouze pokud je část kontejneru zjištěných (například pokud <xref:System.Windows.Forms.Control.Padding%2A> je nastavena na hodnotu velké).</span><span class="sxs-lookup"><span data-stu-id="eb1f7-105">Appearance-related properties of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control itself will be visible at run time only if a part of the container is left uncovered (for example, if the <xref:System.Windows.Forms.Control.Padding%2A> property is set to a large value).</span></span>  
  
 <span data-ttu-id="eb1f7-106">V době běhu vlastnosti týkající se vzhledu můžete nastavena na základě podmínky.</span><span class="sxs-lookup"><span data-stu-id="eb1f7-106">At run time, appearance-related properties can be set based on conditions.</span></span> <span data-ttu-id="eb1f7-107">Například v aplikaci pro plánování, můžete změnit barvu pozadí položky upozornit uživatele, pokud je položka po splatnosti.</span><span class="sxs-lookup"><span data-stu-id="eb1f7-107">For example, in a scheduling application, you might change the background color of an item to warn users when an item is past due.</span></span> <span data-ttu-id="eb1f7-108">V <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> obslužnou rutinu události, je-li například nastavení vlastnosti v podmíněného příkazu `If…Then`, je třeba použít také `Else` klauzule určit vzhled, když není splněna podmínka.</span><span class="sxs-lookup"><span data-stu-id="eb1f7-108">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, if you set a property in a conditional statement such as `If…Then`, you must also use an `Else` clause to specify the appearance when the condition is not met.</span></span>  
  
### <a name="to-change-the-appearance-at-design-time"></a><span data-ttu-id="eb1f7-109">Chcete-li změnit vzhled v době návrhu</span><span class="sxs-lookup"><span data-stu-id="eb1f7-109">To change the appearance at design time</span></span>  
  
1.  <span data-ttu-id="eb1f7-110">V Návrháři formulářů vyberte oblast šablony (velká) položky <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="eb1f7-110">In the Windows Forms Designer, select the item template (upper) region of the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control.</span></span>  
  
2.  <span data-ttu-id="eb1f7-111">V okně vlastností vyberte vlastnosti a změňte hodnotu.</span><span class="sxs-lookup"><span data-stu-id="eb1f7-111">In the Properties window, select a property and change the value.</span></span> <span data-ttu-id="eb1f7-112">Společné vlastnosti, které ovlivňují vzhled zahrnují <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, a <xref:System.Windows.Forms.Control.ForeColor%2A>.</span><span class="sxs-lookup"><span data-stu-id="eb1f7-112">Common properties that affect appearance include <xref:System.Windows.Forms.Control.BackColor%2A>, <xref:System.Windows.Forms.Control.BackgroundImage%2A>, <xref:System.Windows.Forms.Panel.BorderStyle%2A>, and <xref:System.Windows.Forms.Control.ForeColor%2A>.</span></span>  
  
### <a name="to-change-the-appearance-at-run-time"></a><span data-ttu-id="eb1f7-113">Změna vzhledu za běhu</span><span class="sxs-lookup"><span data-stu-id="eb1f7-113">To change the appearance at run time</span></span>  
  
1.  <span data-ttu-id="eb1f7-114">V editoru kódu, události rozevíracího seznamu, klikněte na tlačítko **DrawItem**.</span><span class="sxs-lookup"><span data-stu-id="eb1f7-114">In the Code Editor, in the Event drop-down list, click **DrawItem**.</span></span>  
  
2.  <span data-ttu-id="eb1f7-115">V <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> obslužné rutiny události, přidat kód pro nastavení vlastností:</span><span class="sxs-lookup"><span data-stu-id="eb1f7-115">In the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem> event handler, add code to set the properties:</span></span>  
  
     [!code-csharp[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.cs)]
     [!code-vb[VbPowerPacksDataRepeaterAppearance#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="eb1f7-116">Příklad</span><span class="sxs-lookup"><span data-stu-id="eb1f7-116">Example</span></span>  
 <span data-ttu-id="eb1f7-117">Pro některé běžné úpravy <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> řízení obsahují zobrazení řádků v střídavých barvy a změna barvy pole na základě podmínky.</span><span class="sxs-lookup"><span data-stu-id="eb1f7-117">Some common customizations for the <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control include displaying the rows in alternating colors and changing the color of a field based on a condition.</span></span> <span data-ttu-id="eb1f7-118">Následující příklad ukazuje, jak provést tyto úpravy.</span><span class="sxs-lookup"><span data-stu-id="eb1f7-118">The following example shows how to perform these customizations.</span></span> <span data-ttu-id="eb1f7-119">Tento příklad předpokládá, že máte <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> ovládací prvek, který je vázána k tabulce produktů v databázi Northwind.</span><span class="sxs-lookup"><span data-stu-id="eb1f7-119">This example assumes that you have a <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> control that is bound to the Products table in the Northwind database.</span></span>  
  
 [!code-vb[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/VisualBasic/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.vb)]
 [!code-csharp[VbPowerPacksDataRepeaterAlternateBackColor#1](../../../visual-basic/developing-apps/windows-forms/codesnippet/CSharp/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio_2.cs)]  
  
 <span data-ttu-id="eb1f7-120">Všimněte si, že pro obě tyto úpravy, je nutné zadat kód pro nastavení vlastností pro obě strany podmínky.</span><span class="sxs-lookup"><span data-stu-id="eb1f7-120">Note that for both of these customizations, you must provide code to set the properties for both sides of the condition.</span></span> <span data-ttu-id="eb1f7-121">Pokud nezadáte `Else` podmínky, zobrazí se neočekávaným výsledkům v době běhu.</span><span class="sxs-lookup"><span data-stu-id="eb1f7-121">If you do not specify the `Else` condition, you will see unexpected results at run time.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="eb1f7-122">Viz také</span><span class="sxs-lookup"><span data-stu-id="eb1f7-122">See Also</span></span>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DrawItem>  
 [<span data-ttu-id="eb1f7-123">Úvod do ovládacího prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="eb1f7-123">Introduction to the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="eb1f7-124">Řešení potíží s ovládacím prvkem DataRepeater</span><span class="sxs-lookup"><span data-stu-id="eb1f7-124">Troubleshooting the DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="eb1f7-125">Postupy: zobrazení vázaných dat v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="eb1f7-125">How to: Display Bound Data in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-bound-data-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="eb1f7-126">Postupy: zobrazení nevázaných ovládacích prvků v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="eb1f7-126">How to: Display Unbound Controls in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [<span data-ttu-id="eb1f7-127">Postupy: zobrazení položek záhlaví v ovládacím prvku DataRepeater</span><span class="sxs-lookup"><span data-stu-id="eb1f7-127">How to: Display Item Headers in a DataRepeater Control</span></span>](../../../visual-basic/developing-apps/windows-forms/how-to-display-item-headers-in-a-datarepeater-control-visual-studio.md)
