---
title: Vlastní aktivita vlastnost Vazba na ovládací prvek návrháře
ms.date: 03/30/2017
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
ms.openlocfilehash: 142a9eb273a98d3a2d83a1239d6d7c891d5cc305
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/06/2019
ms.locfileid: "57468569"
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a><span data-ttu-id="1fa18-102">Vlastní aktivita vlastnost Vazba na ovládací prvek návrháře</span><span class="sxs-lookup"><span data-stu-id="1fa18-102">Binding a custom activity property to a designer control</span></span>

<span data-ttu-id="1fa18-103">Vytvoření vazby návrhář ovládacího prvku textového pole na argument aktivity je celkem jasné; Vazba komplexního návrhář ovládacího prvku (například pole se seznamem) na argument aktivity příkaz může nést výzvy, ale.</span><span class="sxs-lookup"><span data-stu-id="1fa18-103">Binding a text box designer control to an activity argument is fairly straightforward; binding a complex designer control (such as a combo box) to an activity argument may present challenges, however.</span></span> <span data-ttu-id="1fa18-104">Toto téma popisuje, jak vytvořit vazbu argument aktivity do ovládacího prvku pole se seznamem v Návrháři vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="1fa18-104">This topic discusses how to bind an activity argument to a combo box control on a custom activity designer.</span></span>

## <a name="creating-the-combo-box-item-converter"></a><span data-ttu-id="1fa18-105">Vytváření převaděč položky pole se seznamem</span><span class="sxs-lookup"><span data-stu-id="1fa18-105">Creating the combo box item converter</span></span>

1. <span data-ttu-id="1fa18-106">Vytvoření nové prázdné řešení v sadě Visual Studio názvem vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1fa18-106">Create a new empty solution in Visual Studio called CustomProperty.</span></span>

2. <span data-ttu-id="1fa18-107">Vytvořte novou třídu s názvem ComboBoxItemConverter.</span><span class="sxs-lookup"><span data-stu-id="1fa18-107">Create a new class called ComboBoxItemConverter.</span></span> <span data-ttu-id="1fa18-108">Přidejte odkaz na System.Windows.Data a mají být odvozen od třídy <xref:System.Windows.Data.IValueConverter>.</span><span class="sxs-lookup"><span data-stu-id="1fa18-108">Add a reference to System.Windows.Data, and have the class derive from <xref:System.Windows.Data.IValueConverter>.</span></span> <span data-ttu-id="1fa18-109">Sada Visual Studio implementovat rozhraní za účelem generování zástupných procedur pro `Convert` a `ConvertBack`.</span><span class="sxs-lookup"><span data-stu-id="1fa18-109">Have Visual Studio implement the interface to generate stubs for `Convert` and `ConvertBack`.</span></span>

3. <span data-ttu-id="1fa18-110">Přidejte následující kód, který `Convert` metody.</span><span class="sxs-lookup"><span data-stu-id="1fa18-110">Add the following code to the `Convert` method.</span></span> <span data-ttu-id="1fa18-111">Tento kód převede aktivitu <xref:System.Activities.InArgument%601> typu <xref:System.String> k hodnota, která má být umístěn v návrháři.</span><span class="sxs-lookup"><span data-stu-id="1fa18-111">This code converts the activity's <xref:System.Activities.InArgument%601> of type <xref:System.String> to the value to be placed in the designer.</span></span>

    ```csharp
    ModelItem modelItem = value as ModelItem;
    if (value != null)
    {
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;

        if (inArgument != null)
        {
            Activity<string> expression = inArgument.Expression;
            VisualBasicValue<string> vbexpression = expression as VisualBasicValue<string>;
            Literal<string> literal = expression as Literal<string>;

            if (literal != null)
            {
                return "\"" + literal.Value + "\"";
            }
            else if (vbexpression != null)
            {
                return vbexpression.ExpressionText;
            }
        }
    }
    return null;
    ```

     <span data-ttu-id="1fa18-112">Výraz ve výše uvedeném fragmentu kódu můžete vytvořit také pomocí <xref:Microsoft.CSharp.Activities.CSharpValue%601> místo <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span><span class="sxs-lookup"><span data-stu-id="1fa18-112">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>

    ```csharp
    ModelItem modelItem = value as ModelItem;
    if (value != null)
    {
        InArgument<string> inArgument = modelItem.GetCurrentValue() as InArgument<string>;

        if (inArgument != null)
        {
            Activity<string> expression = inArgument.Expression;
            CSharpValue<string> csexpression = expression as CSharpValue<string>;
            Literal<string> literal = expression as Literal<string>;

            if (literal != null)
            {
                return "\"" + literal.Value + "\"";
            }
            else if (csexpression != null)
            {
                return csexpression.ExpressionText;
            }
        }
    }
    return null;
    ```

4. <span data-ttu-id="1fa18-113">Přidejte následující kód, který `ConvertBack` metody.</span><span class="sxs-lookup"><span data-stu-id="1fa18-113">Add the following code to the `ConvertBack` method.</span></span> <span data-ttu-id="1fa18-114">Tento kód převede příchozí položky pole se seznamem zpět do <xref:System.Activities.InArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="1fa18-114">This code converts the incoming combo box item back to an <xref:System.Activities.InArgument%601>.</span></span>

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(vbArgument);
                return inArgument;
    ```

     <span data-ttu-id="1fa18-115">Výraz ve výše uvedeném fragmentu kódu můžete vytvořit také pomocí <xref:Microsoft.CSharp.Activities.CSharpValue%601> místo <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span><span class="sxs-lookup"><span data-stu-id="1fa18-115">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(csArgument);
                return inArgument;
    ```

## <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a><span data-ttu-id="1fa18-116">Přidávání ComboBoxItemConverter do vlastního návrháře aktivity</span><span class="sxs-lookup"><span data-stu-id="1fa18-116">Adding the ComboBoxItemConverter to the custom designer of an activity</span></span>

1. <span data-ttu-id="1fa18-117">Přidáte novou položku do projektu.</span><span class="sxs-lookup"><span data-stu-id="1fa18-117">Add a new item to the project.</span></span> <span data-ttu-id="1fa18-118">V dialogovém okně Nová položka vyberte uzel pracovní postup a vyberte Návrhář aktivity jako typ nová položka.</span><span class="sxs-lookup"><span data-stu-id="1fa18-118">In the New Item dialog, select the Workflow node and select Activity Designer as the type of the new item.</span></span> <span data-ttu-id="1fa18-119">Název položky CustomPropertyDesigner.</span><span class="sxs-lookup"><span data-stu-id="1fa18-119">Name the item CustomPropertyDesigner.</span></span>

2. <span data-ttu-id="1fa18-120">Přidáte pole se seznamem do nového návrháře.</span><span class="sxs-lookup"><span data-stu-id="1fa18-120">Add a Combo Box to the new designer.</span></span> <span data-ttu-id="1fa18-121">Ve vlastnosti Items přidejte několik položek k poli se seznamem obsahu hodnotami "Item1" a "item2 –".</span><span class="sxs-lookup"><span data-stu-id="1fa18-121">In the Items property, add a couple of items to the combo box, with Content values of "Item1" and 'Item2".</span></span>

3. <span data-ttu-id="1fa18-122">Upravte XAML pole se seznamem přidání nové položky převaděč jako převaděč položka má být použit pro pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="1fa18-122">Modify the XAML of the combo box to add the new item converter as the item converter to be used for the combo box.</span></span> <span data-ttu-id="1fa18-123">Převaděč se přidá jako prostředek v segmentu ActivityDesigner.Resources a určuje převaděč v atributu převaděč pro <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="1fa18-123">The converter is added as a resource in the ActivityDesigner.Resources segment, and specifies the converter in the Converter attribute for the <xref:System.Windows.Controls.ComboBox>.</span></span> <span data-ttu-id="1fa18-124">Všimněte si, že je obor názvů projektu určený v atributech obory názvů pro Návrhář aktivity; Pokud návrháře se má použít v jiném projektu, tento obor názvů se musí změnit.</span><span class="sxs-lookup"><span data-stu-id="1fa18-124">Note that the namespace of the project is specified in the namespaces attributes for the activity designer; if the designer is to be used in a different project, this namespace will need to be changed.</span></span>

    ```xaml
    <sap:ActivityDesigner x:Class="CustomProperty.CustomPropertyDesigner"
        xmlns="http://schemas.microsoft.com/winfx/2006/xaml/presentation"
        xmlns:x="http://schemas.microsoft.com/winfx/2006/xaml"
        xmlns:c="clr-namespace:CustomProperty"
        xmlns:sap="clr-namespace:System.Activities.Presentation;assembly=System.Activities.Presentation"
        xmlns:sapv="clr-namespace:System.Activities.Presentation.View;assembly=System.Activities.Presentation">

        <sap:ActivityDesigner.Resources>
            <ResourceDictionary>
                <c:ComboBoxItemConverter x:Key="comboBoxItemConverter"/>
            </ResourceDictionary>
        </sap:ActivityDesigner.Resources>
        <Grid>
            <ComboBox SelectedValue="{Binding Path=ModelItem.Text, Mode=TwoWay, Converter={StaticResource comboBoxItemConverter}}"  Height="23" HorizontalAlignment="Left" Margin="132,5,0,0" Name="comboBox1" VerticalAlignment="Top" Width="120" ItemsSource="{Binding}">
                <ComboBoxItem>item1</ComboBoxItem>
                <ComboBoxItem>item2</ComboBoxItem>
            </ComboBox>
        </Grid>
    </sap:ActivityDesigner>
    ```

4. <span data-ttu-id="1fa18-125">Vytvoření nové položky typu <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="1fa18-125">Create a new item of type <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="1fa18-126">V tomto příkladu bude stačit výchozí kód vytvořený pomocí rozhraní IDE pro aktivitu.</span><span class="sxs-lookup"><span data-stu-id="1fa18-126">The default code created by the IDE for the activity will be sufficient for this example.</span></span>

5. <span data-ttu-id="1fa18-127">Přidejte následující atribut pro definici třídy:</span><span class="sxs-lookup"><span data-stu-id="1fa18-127">Add the following attribute to the class definition:</span></span>

    ```csharp
    [Designer(typeof(CustomPropertyDesigner))]
    ```

     <span data-ttu-id="1fa18-128">Tento řádek přiřadí nový Návrhář novou třídu.</span><span class="sxs-lookup"><span data-stu-id="1fa18-128">This line associates the new designer with the new class.</span></span>

 <span data-ttu-id="1fa18-129">Nová aktivita by měly být nyní přidružené návrháře.</span><span class="sxs-lookup"><span data-stu-id="1fa18-129">The new activity should now be associated with the designer.</span></span> <span data-ttu-id="1fa18-130">Otestovat novou aktivitu, přidejte ji do pracovního postupu a nastavte pole se seznamem dvou hodnot.</span><span class="sxs-lookup"><span data-stu-id="1fa18-130">To test the new activity, add it to a workflow, and set the combo box to the two values.</span></span> <span data-ttu-id="1fa18-131">V okně Vlastnosti by měl aktualizovat tak, aby odrážely hodnota pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="1fa18-131">The properties window should update to reflect the combo box value.</span></span>
