---
title: 'Postupy: Vytvoření jednoduše vázaného ovládacího prvku na formuláři Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: 5c92b7bfd5026b0569397dc05cca216fbdab0753
ms.sourcegitcommit: d8ebe0ee198f5d38387a80ba50f395386779334f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/05/2019
ms.locfileid: "66689295"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="4c049-102">Postupy: Vytvoření jednoduše vázaného ovládacího prvku na formuláři Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4c049-102">How to: Create a Simple-Bound Control on a Windows Form</span></span>

<span data-ttu-id="4c049-103">S *jednoduchá vazba*, jeden datový prvek, jako je například hodnota sloupce z tabulky datovou sadu, můžete zobrazit v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="4c049-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="4c049-104">Vám může jednoduché bind nějaká vlastnost ovládacího prvku na hodnotu data.</span><span class="sxs-lookup"><span data-stu-id="4c049-104">You can simple-bind any property of a control to a data value.</span></span>

> [!NOTE]
> <span data-ttu-id="4c049-105">Dialogová okna a příkazy nabídek, které vidíte, se mohou lišit od těch popsaných v nápovědě v závislosti na aktivních nastaveních nebo edici.</span><span class="sxs-lookup"><span data-stu-id="4c049-105">The dialog boxes and menu commands you see might differ from those described in Help depending on your active settings or edition.</span></span> <span data-ttu-id="4c049-106">Chcete-li změnit nastavení, zvolte **nastavení importu a exportu** na **nástroje** nabídky.</span><span class="sxs-lookup"><span data-stu-id="4c049-106">To change your settings, choose **Import and Export Settings** on the **Tools** menu.</span></span> <span data-ttu-id="4c049-107">Další informace najdete v tématu [přizpůsobení integrovaného vývojového prostředí sady Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).</span><span class="sxs-lookup"><span data-stu-id="4c049-107">For more information, see [Personalize the Visual Studio IDE](/visualstudio/ide/personalizing-the-visual-studio-ide).</span></span>

### <a name="to-simple-bind-a-control"></a><span data-ttu-id="4c049-108">Ovládací prvek jednoduché metody Bind</span><span class="sxs-lookup"><span data-stu-id="4c049-108">To simple-bind a control</span></span>

1. <span data-ttu-id="4c049-109">Připojení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="4c049-109">Connect to a data source.</span></span> <span data-ttu-id="4c049-110">Další informace najdete v tématu [připojení ke zdroji dat](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="4c049-110">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="4c049-111">Ve formuláři, vyberte ovládací prvek a zobrazí **vlastnosti** okna.</span><span class="sxs-lookup"><span data-stu-id="4c049-111">In the form, select the control and display the **Properties** window.</span></span>

3. <span data-ttu-id="4c049-112">Rozbalte **(DataBindings)** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4c049-112">Expand the **(DataBindings)** property.</span></span>

     <span data-ttu-id="4c049-113">Zobrazí se vlastnosti nejčastěji vázané pod **(DataBindings)** vlastnost.</span><span class="sxs-lookup"><span data-stu-id="4c049-113">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="4c049-114">Například ve většině ovládacích prvků **Text** vlastnost nejčastěji vázána.</span><span class="sxs-lookup"><span data-stu-id="4c049-114">For example, in most controls, the **Text** property is most frequently bound.</span></span>

4. <span data-ttu-id="4c049-115">Pokud vlastnost, kterou chcete bind není jedním z nejčastěji vázané vlastnosti, klikněte na tlačítko **tlačítko se třemi tečkami** tlačítko (![The třemi tečkami (...) v okně Vlastnosti systému Visual Studio](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)) v **() Rozšířené)** pole zobrazíte **formátování a rozšířené vazby** dialogové okno s kompletní seznam vlastností pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="4c049-115">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>

5. <span data-ttu-id="4c049-116">Vyberte vlastnost, kterou chcete vytvořit vazbu a klikněte na šipku rozevíracího seznamu v části **vazby**.</span><span class="sxs-lookup"><span data-stu-id="4c049-116">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>

     <span data-ttu-id="4c049-117">Zobrazí se seznam dostupných datových zdrojů.</span><span class="sxs-lookup"><span data-stu-id="4c049-117">A list of available data sources is displayed.</span></span>

6. <span data-ttu-id="4c049-118">Rozbalení zdroje dat, kterou chcete svázat, dokud nenajdete jeden datový element, který chcete.</span><span class="sxs-lookup"><span data-stu-id="4c049-118">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="4c049-119">Pokud vytváříte vazbu na hodnotu sloupce v tabulce datové sady, rozbalte název datové sady a potom rozbalte název tabulky, chcete-li zobrazit názvy sloupců.</span><span class="sxs-lookup"><span data-stu-id="4c049-119">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

7. <span data-ttu-id="4c049-120">Klikněte na název elementu k vytvoření vazby.</span><span class="sxs-lookup"><span data-stu-id="4c049-120">Click the name of an element to bind to.</span></span>

8. <span data-ttu-id="4c049-121">Pokud jste pracovali **formátování a rozšířené vazby** dialogovém okně klikněte na tlačítko **OK** se vraťte do **vlastnosti** okno.</span><span class="sxs-lookup"><span data-stu-id="4c049-121">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>

9. <span data-ttu-id="4c049-122">Pokud chcete vytvořit vazbu další vlastnosti ovládacího prvku, opakujte kroky 3 až 7.</span><span class="sxs-lookup"><span data-stu-id="4c049-122">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>

    > [!NOTE]
    > <span data-ttu-id="4c049-123">Protože ovládacích prvků vázaných na jednoduchý zobrazit pouze jeden datový prvek, je velmi obvykle obsahují logiku navigace ve formuláři Windows pomocí ovládacích prvků vázaných na jednoduché.</span><span class="sxs-lookup"><span data-stu-id="4c049-123">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>

## <a name="see-also"></a><span data-ttu-id="4c049-124">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4c049-124">See also</span></span>

- <xref:System.Windows.Forms.Binding>
- [<span data-ttu-id="4c049-125">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="4c049-125">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="4c049-126">Datové vazby a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4c049-126">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
