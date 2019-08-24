---
title: 'Postupy: Vytvoření připojeného ovládacího prvku a formátování zobrazených dat'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 543775894994c518d6069f697b145cedaa7af5b0
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015651"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a><span data-ttu-id="9c665-102">Postupy: Vytvoření připojeného ovládacího prvku a formátování zobrazených dat</span><span class="sxs-lookup"><span data-stu-id="9c665-102">How to: Create a Bound Control and Format the Displayed Data</span></span>

<span data-ttu-id="9c665-103">Pomocí model Windows Forms datové vazby můžete naformátovat data zobrazená v ovládacím prvku vázaného na data pomocí dialogového okna **formátování a rozšířené vazby** .</span><span class="sxs-lookup"><span data-stu-id="9c665-103">With Windows Forms data binding, you can format the data displayed in a data-bound control by using the **Formatting and Advanced Binding** dialog box.</span></span>

## <a name="to-bind-a-control-and-format-the-displayed-data"></a><span data-ttu-id="9c665-104">Navázání ovládacího prvku a formátování zobrazených dat</span><span class="sxs-lookup"><span data-stu-id="9c665-104">To bind a control and format the displayed data</span></span>

1. <span data-ttu-id="9c665-105">Připojte se ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="9c665-105">Connect to a data source.</span></span> <span data-ttu-id="9c665-106">Další informace najdete v tématu [připojení ke zdroji dat](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="9c665-106">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="9c665-107">V aplikaci Visual Studio vyberte ovládací prvek ve formuláři a poté otevřete okno **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="9c665-107">In Visual Studio, select the control on the form, and then open the **Properties** window.</span></span>

3. <span data-ttu-id="9c665-108">Rozbalte vlastnost **(DataBindings)** a pak v poli **(rozšířeném)** klikněte na tlačítko se třemi tečkami (![tlačítko se třemi tečkami (...) v okno Vlastnosti sady Visual](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)Studio) a zobrazte **formátování a rozšířené možnosti.** Dialogové okno vazby, které obsahuje úplný seznam vlastností pro tento ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="9c665-108">Expand the **(DataBindings)** property, and then in the **(Advanced)** box, click the ellipsis button (![The Ellipsis button (...) in the Properties window of Visual Studio](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)) to display the **Formatting and Advanced Binding** dialog box, which has a complete list of properties for that control.</span></span>

4. <span data-ttu-id="9c665-109">Vyberte vlastnost, kterou chcete svázat, a pak vyberte šipku **vazby** .</span><span class="sxs-lookup"><span data-stu-id="9c665-109">Select the property you want to bind, and then select the **Binding** arrow.</span></span>

     <span data-ttu-id="9c665-110">Zobrazí se seznam dostupných zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="9c665-110">A list of available data sources is displayed.</span></span>

5. <span data-ttu-id="9c665-111">Rozbalte zdroj dat, ke kterému chcete vytvořit vazby, dokud nenajdete jeden datový prvek, který chcete.</span><span class="sxs-lookup"><span data-stu-id="9c665-111">Expand the data source you want to bind to until you find the single data element you want.</span></span>

     <span data-ttu-id="9c665-112">Pokud například vytváříte vazbu k hodnotě sloupce v tabulce datové sady, rozbalíte název datové sady a potom rozbalíte název tabulky pro zobrazení názvů sloupců.</span><span class="sxs-lookup"><span data-stu-id="9c665-112">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

6. <span data-ttu-id="9c665-113">Vyberte název prvku, ke kterému se má vytvořit vazba.</span><span class="sxs-lookup"><span data-stu-id="9c665-113">Select the name of an element to bind to.</span></span>

7. <span data-ttu-id="9c665-114">V poli **typ formátu** vyberte formát, který chcete použít pro data zobrazená v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="9c665-114">In the **Format type** box, select the format you want to apply to the data displayed in the control.</span></span>

     <span data-ttu-id="9c665-115">V každém případě můžete zadat hodnotu zobrazenou v ovládacím prvku, pokud zdroj dat obsahuje <xref:System.DBNull>.</span><span class="sxs-lookup"><span data-stu-id="9c665-115">In every case, you can specify the value displayed in the control if the data source contains <xref:System.DBNull>.</span></span> <span data-ttu-id="9c665-116">V opačném případě se možnosti mírně liší v závislosti na zvoleném typu formátu.</span><span class="sxs-lookup"><span data-stu-id="9c665-116">Otherwise, the options vary slightly, depending on the format type you choose.</span></span> <span data-ttu-id="9c665-117">V následující tabulce jsou uvedeny typy a možnosti formátu.</span><span class="sxs-lookup"><span data-stu-id="9c665-117">The following table shows the format types and options.</span></span>

    |<span data-ttu-id="9c665-118">Typ formátu</span><span class="sxs-lookup"><span data-stu-id="9c665-118">Format type</span></span>|<span data-ttu-id="9c665-119">Možnost formátování</span><span class="sxs-lookup"><span data-stu-id="9c665-119">Formatting option</span></span>|
    |-----------------|-----------------------|
    |<span data-ttu-id="9c665-120">Žádné formátování</span><span class="sxs-lookup"><span data-stu-id="9c665-120">No Formatting</span></span>|<span data-ttu-id="9c665-121">Žádné možnosti.</span><span class="sxs-lookup"><span data-stu-id="9c665-121">No options.</span></span>|
    |<span data-ttu-id="9c665-122">Numeric</span><span class="sxs-lookup"><span data-stu-id="9c665-122">Numeric</span></span>|<span data-ttu-id="9c665-123">Určete počet desetinných míst pomocí ovládacího prvku **desetinná místa** .</span><span class="sxs-lookup"><span data-stu-id="9c665-123">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="9c665-124">Měna</span><span class="sxs-lookup"><span data-stu-id="9c665-124">Currency</span></span>|<span data-ttu-id="9c665-125">Určete počet desetinných míst pomocí ovládacího prvku **desetinná místa** .</span><span class="sxs-lookup"><span data-stu-id="9c665-125">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="9c665-126">Datum a čas</span><span class="sxs-lookup"><span data-stu-id="9c665-126">Date Time</span></span>|<span data-ttu-id="9c665-127">Vyberte, jak se má datum a čas zobrazit výběrem jedné z položek v poli Výběr **typu** .</span><span class="sxs-lookup"><span data-stu-id="9c665-127">Select how the date and time should be displayed by selecting one of the items in the **Type** selection box.</span></span>|
    |<span data-ttu-id="9c665-128">Odbornou</span><span class="sxs-lookup"><span data-stu-id="9c665-128">Scientific</span></span>|<span data-ttu-id="9c665-129">Určete počet desetinných míst pomocí ovládacího prvku **desetinná místa** .</span><span class="sxs-lookup"><span data-stu-id="9c665-129">Specify number of decimal places by using **Decimal places** up-down control.</span></span>|
    |<span data-ttu-id="9c665-130">Vlastní</span><span class="sxs-lookup"><span data-stu-id="9c665-130">Custom</span></span>|<span data-ttu-id="9c665-131">Zadejte řetězec vlastního formátu pomocí.</span><span class="sxs-lookup"><span data-stu-id="9c665-131">Specify a custom format string using.</span></span><br /><br /> <span data-ttu-id="9c665-132">Další informace najdete v tématu [formátování typů](../../standard/base-types/formatting-types.md).</span><span class="sxs-lookup"><span data-stu-id="9c665-132">For more information, see [Formatting Types](../../standard/base-types/formatting-types.md).</span></span> <span data-ttu-id="9c665-133">**Poznámka:**  Řetězce vlastního formátu nejsou zaručené k úspěšnému zacyklení cest mezi zdrojem dat a vázaným ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="9c665-133">**Note:**  Custom format strings are not guaranteed to successfully round trip between the data source and bound control.</span></span> <span data-ttu-id="9c665-134">Místo toho zpracujte <xref:System.Windows.Forms.Binding.Parse> událost <xref:System.Windows.Forms.Binding.Format> nebo pro vazbu a použijte vlastní formátování v kódu pro zpracování událostí.</span><span class="sxs-lookup"><span data-stu-id="9c665-134">Instead handle the <xref:System.Windows.Forms.Binding.Parse> or <xref:System.Windows.Forms.Binding.Format> event for the binding and apply custom formatting in the event-handling code.</span></span>|

8. <span data-ttu-id="9c665-135">Kliknutím na **tlačítko OK** zavřete dialogové okno **formátování a rozšířené vazby** a vraťte se do okno Vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="9c665-135">Select **OK** to close the **Formatting and Advanced Binding** dialog box and return to the Properties window.</span></span>

## <a name="see-also"></a><span data-ttu-id="9c665-136">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9c665-136">See also</span></span>

- [<span data-ttu-id="9c665-137">Postupy: Vytvoření jednoduchého ovládacího prvku vázaného na formuláři Windows</span><span class="sxs-lookup"><span data-stu-id="9c665-137">How to: Create a Simple-Bound Control on a Windows Form</span></span>](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [<span data-ttu-id="9c665-138">Ověřování uživatelského vstupu ve Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9c665-138">User Input Validation in Windows Forms</span></span>](user-input-validation-in-windows-forms.md)
- [<span data-ttu-id="9c665-139">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="9c665-139">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
