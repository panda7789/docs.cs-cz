---
title: "Postupy: Vytvoření připojeného ovládacího prvku a formátování zobrazených dat"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 6088048ed27b2021e297494275f4e80f7c0cb681
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="cc96d-102">Postupy: Vytvoření připojeného ovládacího prvku a formátování zobrazených dat</span><span class="sxs-lookup"><span data-stu-id="cc96d-102">How to: Create a Bound Control and Format the Displayed Data</span></span>
<span data-ttu-id="cc96d-103">S Windows Forms – datová vazba, můžete ho naformátovat data zobrazená v ovládacím prvku vázané na data pomocí **formátování a rozšířené vazby** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="cc96d-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="cc96d-104">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="cc96d-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="cc96d-105">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="cc96d-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="cc96d-106">Další informace najdete v tématu [přizpůsobení nastavení pro vývoj v sadě Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span><span class="sxs-lookup"><span data-stu-id="cc96d-106">For more information, see [Customizing Development Settings in Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).</span></span>  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="cc96d-107">Chcete-li vytvořit vazbu ovládacího prvku a formátování zobrazených dat</span><span class="sxs-lookup"><span data-stu-id="cc96d-107">To bind a control and format the displayed data</span></span>  
  
1.  <span data-ttu-id="cc96d-108">Připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="cc96d-108">Connect to a data source.</span></span>  
  
     <span data-ttu-id="cc96d-109">Další informace najdete v tématu [připojení ke zdroji dat](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="cc96d-109">For more information, see [Connecting to a Data Source](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2.  <span data-ttu-id="cc96d-110">Ve formuláři vyberte ovládací prvek a potom otevřete okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="cc96d-110">In the form, select the control, and then open the Properties window.</span></span>  
  
3.  <span data-ttu-id="cc96d-111">Rozbalte **(datové vazby)** vlastnost a potom v **(rozšířené)** pole, klikněte na tlačítko se třemi tečkami (![– snímek obrazovky VisualStudioEllipsesButton] (../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) k zobrazení **formátování a rozšířené vazby** dialogové okno, který má úplný seznam vlastností pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="cc96d-111">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![VisualStudioEllipsesButton screenshot](../../../docs/framework/winforms/media/vbellipsesbutton.png "vbEllipsesButton")) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>  
  
4.  <span data-ttu-id="cc96d-112">Vyberte vlastnost, kterou chcete vytvořit vazbu a potom klikněte na **vazby** šipku.</span><span class="sxs-lookup"><span data-stu-id="cc96d-112">Select the property you want to bind, and then click the **Binding** arrow.</span></span>  
  
     <span data-ttu-id="cc96d-113">Zobrazí se seznam dostupných zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="cc96d-113">A list of available data sources is displayed.</span></span>  
  
5.  <span data-ttu-id="cc96d-114">Rozbalení zdroje dat, které chcete vytvořit vazbu, dokud nebude nalezen jeden datový prvek, který má být.</span><span class="sxs-lookup"><span data-stu-id="cc96d-114">Expand the data source you want to bind to until you find the single data element you want.</span></span>  
  
     <span data-ttu-id="cc96d-115">Pokud vytváříte vazbu na hodnotu sloupce v tabulce datové sady, rozbalte název datové sady a potom rozbalte název tabulky k zobrazení názvů sloupců.</span><span class="sxs-lookup"><span data-stu-id="cc96d-115">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
6.  <span data-ttu-id="cc96d-116">Klikněte na název elementu k vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="cc96d-116">Click the name of an element to bind to.</span></span>  
  
7.  <span data-ttu-id="cc96d-117">V **typ** pole, klikněte na formát, který chcete použít pro data zobrazená v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="cc96d-117">In the **Format type** box, click the format you want to apply to the data displayed in the control.</span></span>  
  
     <span data-ttu-id="cc96d-118">V každém případě můžete zadat hodnotu, pokud obsahuje zdroj dat, zobrazí v ovládacím prvku <xref:System.DBNull>.</span><span class="sxs-lookup"><span data-stu-id="cc96d-118">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="cc96d-119">Jinak hodnota možnosti mírně lišit v závislosti na typu formátu, který zvolíte.</span><span class="sxs-lookup"><span data-stu-id="cc96d-119">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="cc96d-120">V následující tabulce jsou uvedeny typy formátu a možnosti.</span><span class="sxs-lookup"><span data-stu-id="cc96d-120">The following table shows the format types and options.</span></span>  
  
    |<span data-ttu-id="cc96d-121">Typ formátu</span><span class="sxs-lookup"><span data-stu-id="cc96d-121">Format type</span></span>|<span data-ttu-id="cc96d-122">Možnost formátování</span><span class="sxs-lookup"><span data-stu-id="cc96d-122">Formatting option</span></span>|  
    |-----------------|-----------------------|  
    |<span data-ttu-id="cc96d-123">Žádné formátování</span><span class="sxs-lookup"><span data-stu-id="cc96d-123">No Formatting</span></span>|<span data-ttu-id="cc96d-124">Žádné možnosti.</span><span class="sxs-lookup"><span data-stu-id="cc96d-124">No options.</span></span>|  
    |<span data-ttu-id="cc96d-125">číselné</span><span class="sxs-lookup"><span data-stu-id="cc96d-125">Numeric</span></span>|<span data-ttu-id="cc96d-126">Zadejte počet desetinných míst pomocí **desetinných míst** dolů.</span><span class="sxs-lookup"><span data-stu-id="cc96d-126">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="cc96d-127">Měna</span><span class="sxs-lookup"><span data-stu-id="cc96d-127">Currency</span></span>|<span data-ttu-id="cc96d-128">Zadejte počet desetinných míst pomocí **desetinných míst** dolů.</span><span class="sxs-lookup"><span data-stu-id="cc96d-128">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="cc96d-129">Datum a čas</span><span class="sxs-lookup"><span data-stu-id="cc96d-129">Date Time</span></span>|<span data-ttu-id="cc96d-130">Vyberte, jak datum a čas mají být zobrazeny výběrem jedné z položek v **typ** výběr pole.</span><span class="sxs-lookup"><span data-stu-id="cc96d-130">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|  
    |<span data-ttu-id="cc96d-131">Scientific</span><span class="sxs-lookup"><span data-stu-id="cc96d-131">Scientific</span></span>|<span data-ttu-id="cc96d-132">Zadejte počet desetinných míst pomocí **desetinných míst** dolů.</span><span class="sxs-lookup"><span data-stu-id="cc96d-132">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="cc96d-133">Vlastní</span><span class="sxs-lookup"><span data-stu-id="cc96d-133">Custom</span></span>|<span data-ttu-id="cc96d-134">Zadejte řetězec vlastní formát pomocí.</span><span class="sxs-lookup"><span data-stu-id="cc96d-134">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="cc96d-135">Další informace najdete v tématu [typy formátování](../../../docs/standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="cc96d-135">For more information, see [Formatting Types](../../../docs/standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="cc96d-136">**Poznámka:** vlastní řetězce formátu není zaručena bezpečnost pro úspěšně odezvy mezi zdrojem dat a připojeného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="cc96d-136">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="cc96d-137">Místo toho zpracovat <xref:System.Windows.Forms.Binding.Parse> nebo <xref:System.Windows.Forms.Binding.Format> událostí pro vazbu a použít vlastní formátování v kódu zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="cc96d-137">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|  
  
8.  <span data-ttu-id="cc96d-138">Klikněte na tlačítko **OK** zavřete **formátování a rozšířené vazby** dialogové okno a vraťte se do okna vlastností.</span><span class="sxs-lookup"><span data-stu-id="cc96d-138">Click **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc96d-139">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc96d-139">See Also</span></span>  
 [<span data-ttu-id="cc96d-140">Postupy: Vytvoření jednoduše vázaného ovládacího prvku na formuláři Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc96d-140">How to: Create a Simple-Bound Control on a Windows Form</span></span>](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [<span data-ttu-id="cc96d-141">Ověřování uživatelského vstupu ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc96d-141">User Input Validation in Windows Forms</span></span>](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 [<span data-ttu-id="cc96d-142">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="cc96d-142">Windows Forms Data Binding</span></span>](../../../docs/framework/winforms/windows-forms-data-binding.md)
