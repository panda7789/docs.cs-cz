---
title: 'Postupy: Vytvoření připojeného ovládacího prvku a formátování zobrazených dat'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: f7f1ed2fbca4ab8892cb6c439ae8841fa8828bf0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59302540"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="daa8f-102">Postupy: Vytvoření připojeného ovládacího prvku a formátování zobrazených dat</span><span class="sxs-lookup"><span data-stu-id="daa8f-102">How to: Create a Bound Control and Format the Displayed Data</span></span>
<span data-ttu-id="daa8f-103">Pomocí Windows Forms – datová vazba, lze formátovat data zobrazená v ovládací prvek vázaný na data pomocí **formátování a rozšířené vazby** dialogové okno.</span><span class="sxs-lookup"><span data-stu-id="daa8f-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="daa8f-104">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="daa8f-104">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="daa8f-105">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="daa8f-105">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="daa8f-106">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="daa8f-106">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="daa8f-107">K vytvoření vazby ovládacího prvku a formátování zobrazených dat</span><span class="sxs-lookup"><span data-stu-id="daa8f-107">To bind a control and format the displayed data</span></span>  
  
1. <span data-ttu-id="daa8f-108">Připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="daa8f-108">Connect to a data source.</span></span>  
  
     <span data-ttu-id="daa8f-109">Další informace najdete v tématu [připojení ke zdroji dat](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="daa8f-109">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>  
  
2. <span data-ttu-id="daa8f-110">Ve formuláři vyberte ovládací prvek a potom otevřete okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="daa8f-110">In the form, select the control, and then open the Properties window.</span></span>  
  
3. <span data-ttu-id="daa8f-111">Rozbalte **(DataBindings)** vlastnost a potom v **(rozšířené)** klikněte na tlačítko se třemi tečkami (![snímek obrazovky VisualStudioEllipsesButton](./media/vbellipsesbutton.png " vbEllipsesButton")) zobrazíte **formátování a rozšířené vazby** dialogové okno, které obsahuje úplný seznam vlastností pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="daa8f-111">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![VisualStudioEllipsesButton screenshot](./media/vbellipsesbutton.png "vbEllipsesButton")) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>  
  
4. <span data-ttu-id="daa8f-112">Vyberte vlastnost, kterou chcete vytvořit vazbu a potom klikněte na **vazby** šipku.</span><span class="sxs-lookup"><span data-stu-id="daa8f-112">Select the property you want to bind, and then click the **Binding** arrow.</span></span>  
  
     <span data-ttu-id="daa8f-113">Zobrazí se seznam dostupných datových zdrojů.</span><span class="sxs-lookup"><span data-stu-id="daa8f-113">A list of available data sources is displayed.</span></span>  
  
5. <span data-ttu-id="daa8f-114">Rozbalení zdroje dat, kterou chcete svázat, dokud nenajdete jeden datový element, který chcete.</span><span class="sxs-lookup"><span data-stu-id="daa8f-114">Expand the data source you want to bind to until you find the single data element you want.</span></span>  
  
     <span data-ttu-id="daa8f-115">Pokud vytváříte vazbu na hodnotu sloupce v tabulce datové sady, rozbalte název datové sady a potom rozbalte název tabulky, chcete-li zobrazit názvy sloupců.</span><span class="sxs-lookup"><span data-stu-id="daa8f-115">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>  
  
6. <span data-ttu-id="daa8f-116">Klikněte na název elementu k vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="daa8f-116">Click the name of an element to bind to.</span></span>  
  
7. <span data-ttu-id="daa8f-117">V **typ** klikněte na formát, který chcete použít pro data zobrazí v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="daa8f-117">In the **Format type** box, click the format you want to apply to the data displayed in the control.</span></span>  
  
     <span data-ttu-id="daa8f-118">V každém případě můžete zadat hodnotu, pokud obsahuje zdroj dat se zobrazí v ovládacím prvku <xref:System.DBNull>.</span><span class="sxs-lookup"><span data-stu-id="daa8f-118">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="daa8f-119">V opačném případě možnosti mírně lišit v závislosti na zvoleném typu formátu.</span><span class="sxs-lookup"><span data-stu-id="daa8f-119">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="daa8f-120">V následující tabulce jsou uvedeny typy formátů a možnosti.</span><span class="sxs-lookup"><span data-stu-id="daa8f-120">The following table shows the format types and options.</span></span>  
  
    |<span data-ttu-id="daa8f-121">Typ formátu</span><span class="sxs-lookup"><span data-stu-id="daa8f-121">Format type</span></span>|<span data-ttu-id="daa8f-122">Možnost formátování</span><span class="sxs-lookup"><span data-stu-id="daa8f-122">Formatting option</span></span>|  
    |-----------------|-----------------------|  
    |<span data-ttu-id="daa8f-123">Žádné formátování</span><span class="sxs-lookup"><span data-stu-id="daa8f-123">No Formatting</span></span>|<span data-ttu-id="daa8f-124">Žádné možnosti.</span><span class="sxs-lookup"><span data-stu-id="daa8f-124">No options.</span></span>|  
    |<span data-ttu-id="daa8f-125">Čísla</span><span class="sxs-lookup"><span data-stu-id="daa8f-125">Numeric</span></span>|<span data-ttu-id="daa8f-126">Zadejte počet desetinných míst s použitím **desetinných míst** číselníku.</span><span class="sxs-lookup"><span data-stu-id="daa8f-126">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="daa8f-127">Měna</span><span class="sxs-lookup"><span data-stu-id="daa8f-127">Currency</span></span>|<span data-ttu-id="daa8f-128">Zadejte počet desetinných míst s použitím **desetinných míst** číselníku.</span><span class="sxs-lookup"><span data-stu-id="daa8f-128">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="daa8f-129">Datum a čas</span><span class="sxs-lookup"><span data-stu-id="daa8f-129">Date Time</span></span>|<span data-ttu-id="daa8f-130">Vyberte datum a čas by měl být zobrazení tak, že vyberete jednu z položek v **typ** výběru.</span><span class="sxs-lookup"><span data-stu-id="daa8f-130">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|  
    |<span data-ttu-id="daa8f-131">vědecké</span><span class="sxs-lookup"><span data-stu-id="daa8f-131">Scientific</span></span>|<span data-ttu-id="daa8f-132">Zadejte počet desetinných míst s použitím **desetinných míst** číselníku.</span><span class="sxs-lookup"><span data-stu-id="daa8f-132">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|  
    |<span data-ttu-id="daa8f-133">Vlastní</span><span class="sxs-lookup"><span data-stu-id="daa8f-133">Custom</span></span>|<span data-ttu-id="daa8f-134">Zadejte řetězec vlastního formátu pomocí.</span><span class="sxs-lookup"><span data-stu-id="daa8f-134">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="daa8f-135">Další informace najdete v tématu [Formatting Types](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="daa8f-135">For more information, see [Formatting Types](../../standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="daa8f-136">**Poznámka:**  Vlastních formátovacích řetězců není zaručeno úspěšně odezvy komunikace mezi zdrojem dat a vázaného ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="daa8f-136">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="daa8f-137">Místo toho zpracovat <xref:System.Windows.Forms.Binding.Parse> nebo <xref:System.Windows.Forms.Binding.Format> události pro vazbu a použití vlastního formátování v kódu pro zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="daa8f-137">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|  
  
8. <span data-ttu-id="daa8f-138">Klikněte na tlačítko **OK** zavřete **formátování a rozšířené vazby** dialogové okno a vraťte se do okna Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="daa8f-138">Click **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="daa8f-139">Viz také:</span><span class="sxs-lookup"><span data-stu-id="daa8f-139">See also</span></span>

- [<span data-ttu-id="daa8f-140">Postupy: Vytvoření jednoduše vázaného ovládacího prvku ve formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="daa8f-140">How to: Create a Simple-Bound Control on a Windows Form</span></span>](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [<span data-ttu-id="daa8f-141">Ověřování uživatelského vstupu ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="daa8f-141">User Input Validation in Windows Forms</span></span>](user-input-validation-in-windows-forms.md)
- [<span data-ttu-id="daa8f-142">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="daa8f-142">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
