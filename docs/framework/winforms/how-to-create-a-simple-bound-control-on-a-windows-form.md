---
title: 'Postupy: Vytvoření jednoduše vázaného ovládacího prvku na formuláři Windows Forms'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: ed1d0e423a3cdf77a242ec3214720f1466f65897
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039509"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a><span data-ttu-id="ea750-102">Postupy: Vytvoření jednoduše vázaného ovládacího prvku na formuláři Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ea750-102">How to: Create a Simple-Bound Control on a Windows Form</span></span>

<span data-ttu-id="ea750-103">S *jednoduchou vazbou*můžete v ovládacím prvku zobrazit jeden datový prvek, jako je například hodnota sloupce z tabulky DataSet.</span><span class="sxs-lookup"><span data-stu-id="ea750-103">With *simple binding*, you can display a single data element, such as a column value from a dataset table, in a control.</span></span> <span data-ttu-id="ea750-104">Můžete vytvořit jednoduchou datovou vlastnost ovládacího prvku s datovou hodnotou.</span><span class="sxs-lookup"><span data-stu-id="ea750-104">You can simple-bind any property of a control to a data value.</span></span>

### <a name="to-simple-bind-a-control"></a><span data-ttu-id="ea750-105">Jednoduché vázání ovládacího prvku</span><span class="sxs-lookup"><span data-stu-id="ea750-105">To simple-bind a control</span></span>

1. <span data-ttu-id="ea750-106">Připojte se ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="ea750-106">Connect to a data source.</span></span> <span data-ttu-id="ea750-107">Další informace najdete v tématu [připojení ke zdroji dat](../data/adonet/connecting-to-a-data-source.md).</span><span class="sxs-lookup"><span data-stu-id="ea750-107">For more information, see [Connecting to a Data Source](../data/adonet/connecting-to-a-data-source.md).</span></span>

2. <span data-ttu-id="ea750-108">Ve formuláři vyberte ovládací prvek a zobrazte okno **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="ea750-108">In the form, select the control and display the **Properties** window.</span></span>

3. <span data-ttu-id="ea750-109">Rozbalte vlastnost **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="ea750-109">Expand the **(DataBindings)** property.</span></span>

     <span data-ttu-id="ea750-110">Vlastnosti nejčastěji vázaných jsou zobrazeny pod vlastností **(DataBindings)** .</span><span class="sxs-lookup"><span data-stu-id="ea750-110">The properties most often bound are displayed underneath the **(DataBindings)** property.</span></span> <span data-ttu-id="ea750-111">Ve většině ovládacích prvků je například vlastnost **text** nejčastěji svázána.</span><span class="sxs-lookup"><span data-stu-id="ea750-111">For example, in most controls, the **Text** property is most frequently bound.</span></span>

4. <span data-ttu-id="ea750-112">Pokud vlastnost, kterou chcete svázat, není jednou z běžně vázaných vlastností, klikněte na tlačítko se **třemi tečkami** ![(na tlačítko se třemi tečkami (...) v okno vlastnosti](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)sady Visual Studio.) v poli **(rozšířeném)** zobrazte  **Dialogové okno formátování a rozšířené vazby** s úplným seznamem vlastností pro tento ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="ea750-112">If the property you want to bind is not one of the commonly bound properties, click the **Ellipsis** button (![The Ellipsis button (...) in the Properties window of Visual Studio.](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)) in the **(Advanced)** box to display the **Formatting and Advanced Binding** dialog box with a complete list of properties for that control.</span></span>

5. <span data-ttu-id="ea750-113">Vyberte vlastnost, kterou chcete svázat, a klikněte na šipku rozevíracího seznamu u položky **vazba**.</span><span class="sxs-lookup"><span data-stu-id="ea750-113">Select the property you want to bind and click the drop-down arrow under **Binding**.</span></span>

     <span data-ttu-id="ea750-114">Zobrazí se seznam dostupných zdrojů dat.</span><span class="sxs-lookup"><span data-stu-id="ea750-114">A list of available data sources is displayed.</span></span>

6. <span data-ttu-id="ea750-115">Rozbalte zdroj dat, ke kterému chcete vytvořit vazby, dokud nenajdete jeden datový prvek, který chcete.</span><span class="sxs-lookup"><span data-stu-id="ea750-115">Expand the data source you want to bind to until you find the single data element you want.</span></span> <span data-ttu-id="ea750-116">Pokud například vytváříte vazbu k hodnotě sloupce v tabulce datové sady, rozbalíte název datové sady a potom rozbalíte název tabulky pro zobrazení názvů sloupců.</span><span class="sxs-lookup"><span data-stu-id="ea750-116">For example, if you are binding to a column value in a dataset's table, expand the name of the dataset, and then expand the table name to display column names.</span></span>

7. <span data-ttu-id="ea750-117">Klikněte na název elementu, na který se má vytvořit vazba.</span><span class="sxs-lookup"><span data-stu-id="ea750-117">Click the name of an element to bind to.</span></span>

8. <span data-ttu-id="ea750-118">Pokud jste pracovali v dialogovém okně **formátování a rozšířené vazby** , kliknutím na tlačítko **OK** se vraťte do okna **vlastnosti** .</span><span class="sxs-lookup"><span data-stu-id="ea750-118">If you were working in the **Formatting and Advanced Binding** dialog box, click **OK** to return to the **Properties** window.</span></span>

9. <span data-ttu-id="ea750-119">Pokud chcete navazovat další vlastnosti ovládacího prvku, opakujte kroky 3 až 7.</span><span class="sxs-lookup"><span data-stu-id="ea750-119">If you want to bind additional properties of the control, repeat steps 3 through 7.</span></span>

    > [!NOTE]
    > <span data-ttu-id="ea750-120">Vzhledem k tomu, že jednoduché ovládací prvky jsou zobrazeny pouze s jedním datovým prvkem, je velmi typický zahrnout navigační logiku do formuláře Windows pomocí jednoduchých vázaných ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="ea750-120">Because simple-bound controls show only a single data element, it is very typical to include navigation logic in a Windows Form with simple-bound controls.</span></span>

## <a name="see-also"></a><span data-ttu-id="ea750-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea750-121">See also</span></span>

- <xref:System.Windows.Forms.Binding>
- [<span data-ttu-id="ea750-122">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="ea750-122">Windows Forms Data Binding</span></span>](windows-forms-data-binding.md)
- [<span data-ttu-id="ea750-123">Datové vazby a Windows Forms</span><span class="sxs-lookup"><span data-stu-id="ea750-123">Data Binding and Windows Forms</span></span>](data-binding-and-windows-forms.md)
