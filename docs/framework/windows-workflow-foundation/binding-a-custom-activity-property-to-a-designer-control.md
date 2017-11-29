---
title: "Vazba vlastnost vlastní aktivity do ovládacího prvku návrháře"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e9edc168dc6e4111e5f2d58a62c2b0341f74aa04
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a><span data-ttu-id="1c178-102">Vazba vlastnost vlastní aktivity do ovládacího prvku návrháře</span><span class="sxs-lookup"><span data-stu-id="1c178-102">Binding a custom activity property to a designer control</span></span>
<span data-ttu-id="1c178-103">Vytvoření vazby návrháře textové pole na argument aktivity je poměrně jednoduché; Vytvoření vazby ovládacího prvku složité návrháře (například pole se seznamem) na aktivity argument příkaz může nést výzvy, ale.</span><span class="sxs-lookup"><span data-stu-id="1c178-103">Binding a text box designer control to an activity argument is fairly straightforward; binding a complex designer control (such as a combo box) to an activity argument may present challenges, however.</span></span> <span data-ttu-id="1c178-104">Toto téma popisuje, jak vytvořit vazbu argument aktivity do ovládacího prvku pole se seznamem na Návrhář vlastní aktivity.</span><span class="sxs-lookup"><span data-stu-id="1c178-104">This topic discusses how to bind an activity argument to a combo box control on a custom activity designer.</span></span>  
  
#### <a name="creating-the-combo-box-item-converter"></a><span data-ttu-id="1c178-105">Vytváření převaděč položky pole se seznamem</span><span class="sxs-lookup"><span data-stu-id="1c178-105">Creating the combo box item converter</span></span>  
  
1.  <span data-ttu-id="1c178-106">Vytvořte nový prázdný řešení v sadě Visual Studio názvem CustomProperty.</span><span class="sxs-lookup"><span data-stu-id="1c178-106">Create a new empty solution in Visual Studio called CustomProperty.</span></span>  
  
2.  <span data-ttu-id="1c178-107">Vytvořte novou třídu s názvem ComboBoxItemConverter.</span><span class="sxs-lookup"><span data-stu-id="1c178-107">Create a new class called ComboBoxItemConverter.</span></span> <span data-ttu-id="1c178-108">Přidat odkaz na System.Windows.Data a mít odvozena od třídy <xref:System.Windows.Data.IValueConverter>.</span><span class="sxs-lookup"><span data-stu-id="1c178-108">Add a reference to System.Windows.Data, and have the class derive from <xref:System.Windows.Data.IValueConverter>.</span></span> <span data-ttu-id="1c178-109">Mít Visual Studio, které implementují rozhraní ke generování zástupných procedur pro `Convert` a `ConvertBack`.</span><span class="sxs-lookup"><span data-stu-id="1c178-109">Have Visual Studio implement the interface to generate stubs for `Convert` and `ConvertBack`.</span></span>  
  
3.  <span data-ttu-id="1c178-110">Přidejte následující kód, který `Convert` metoda.</span><span class="sxs-lookup"><span data-stu-id="1c178-110">Add the following code to the `Convert` method.</span></span> <span data-ttu-id="1c178-111">Tento kód převede aktivity <xref:System.Activities.InArgument%601> typu <xref:System.String> k hodnota, která má být umístěn v návrháři.</span><span class="sxs-lookup"><span data-stu-id="1c178-111">This code converts the activity's <xref:System.Activities.InArgument%601> of type <xref:System.String> to the value to be placed in the designer.</span></span>  
  
    ```  
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
  
     <span data-ttu-id="1c178-112">Výraz ve výše uvedeném fragmentu kódu můžete vytvořit také pomocí <xref:Microsoft.CSharp.Activities.CSharpValue%601> místo <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span><span class="sxs-lookup"><span data-stu-id="1c178-112">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>  
  
    ```  
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
  
4.  <span data-ttu-id="1c178-113">Přidejte následující kód, který `ConvertBack` metoda.</span><span class="sxs-lookup"><span data-stu-id="1c178-113">Add the following code to the `ConvertBack` method.</span></span> <span data-ttu-id="1c178-114">Tento kód převede příchozí položky pole se seznamem zpět do <xref:System.Activities.InArgument%601>.</span><span class="sxs-lookup"><span data-stu-id="1c178-114">This code converts the incoming combo box item back to an <xref:System.Activities.InArgument%601>.</span></span>  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(vbArgument);  
                return inArgument;  
    ```  
  
     <span data-ttu-id="1c178-115">Výraz ve výše uvedeném fragmentu kódu můžete vytvořit také pomocí <xref:Microsoft.CSharp.Activities.CSharpValue%601> místo <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span><span class="sxs-lookup"><span data-stu-id="1c178-115">The expression in the above code snippet can also be created using <xref:Microsoft.CSharp.Activities.CSharpValue%601> instead of <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.</span></span>  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(csArgument);  
                return inArgument;  
    ```  
  
#### <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a><span data-ttu-id="1c178-116">Přidávání ComboBoxItemConverter do vlastní Návrhář aktivity</span><span class="sxs-lookup"><span data-stu-id="1c178-116">Adding the ComboBoxItemConverter to the custom designer of an activity</span></span>  
  
1.  <span data-ttu-id="1c178-117">Přidáte novou položku do projektu.</span><span class="sxs-lookup"><span data-stu-id="1c178-117">Add a new item to the project.</span></span> <span data-ttu-id="1c178-118">V dialogovém okně novou položku vyberte uzel pracovního postupu a vyberte Návrhář aktivity jako typ nové položky.</span><span class="sxs-lookup"><span data-stu-id="1c178-118">In the New Item dialog, select the Workflow node and select Activity Designer as the type of the new item.</span></span> <span data-ttu-id="1c178-119">Název položky CustomPropertyDesigner.</span><span class="sxs-lookup"><span data-stu-id="1c178-119">Name the item CustomPropertyDesigner.</span></span>  
  
2.  <span data-ttu-id="1c178-120">Pole se seznamem přidáte do nové návrháře.</span><span class="sxs-lookup"><span data-stu-id="1c178-120">Add a Combo Box to the new designer.</span></span> <span data-ttu-id="1c178-121">Ve vlastnosti položky, přidejte několik položek do pole se seznamem obsahu hodnotami "Item1" a "Item2".</span><span class="sxs-lookup"><span data-stu-id="1c178-121">In the Items property, add a couple of items to the combo box, with Content values of "Item1" and 'Item2".</span></span>  
  
3.  <span data-ttu-id="1c178-122">Upravte XAML pole se seznamem pro přidání nové položky převaděč jako položka převaděč má být použit pro pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="1c178-122">Modify the XAML of the combo box to add the new item converter as the item converter to be used for the combo box.</span></span> <span data-ttu-id="1c178-123">Převaděč je přidán jako prostředek v segmentu ActivityDesigner.Resources a určuje převaděč v atributu převaděč pro <xref:System.Windows.Controls.ComboBox>.</span><span class="sxs-lookup"><span data-stu-id="1c178-123">The converter is added as a resource in the ActivityDesigner.Resources segment, and specifies the converter in the Converter attribute for the <xref:System.Windows.Controls.ComboBox>.</span></span> <span data-ttu-id="1c178-124">Všimněte si, že je obor názvů projektu zadané v atributech obory názvů pro Návrhář aktivity; Pokud návrháře pro použití v na jiný projekt, tento obor názvů se musí změnit.</span><span class="sxs-lookup"><span data-stu-id="1c178-124">Note that the namespace of the project is specified in the namespaces attributes for the activity designer; if the designer is to be used in a different project, this namespace will need to be changed.</span></span>  
  
    ```  
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
  
4.  <span data-ttu-id="1c178-125">Vytvořit novou položku typu <xref:System.Activities.CodeActivity>.</span><span class="sxs-lookup"><span data-stu-id="1c178-125">Create a new item of type <xref:System.Activities.CodeActivity>.</span></span> <span data-ttu-id="1c178-126">Ve výchozím kódu vytvořené IDE aktivity jsou dostatečné pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="1c178-126">The default code created by the IDE for the activity will be sufficient for this example.</span></span>  
  
5.  <span data-ttu-id="1c178-127">V definici třídy, přidejte následující atribut:</span><span class="sxs-lookup"><span data-stu-id="1c178-127">Add the following attribute to the class definition:</span></span>  
  
    ```  
    [Designer(typeof(CustomPropertyDesigner))]  
    ```  
  
     <span data-ttu-id="1c178-128">Tento řádek přidruží nový designer novou třídu.</span><span class="sxs-lookup"><span data-stu-id="1c178-128">This line associates the new designer with the new class.</span></span>  
  
 <span data-ttu-id="1c178-129">Nová aktivita by teď měly být přidruženy návrháře.</span><span class="sxs-lookup"><span data-stu-id="1c178-129">The new activity should now be associated with the designer.</span></span> <span data-ttu-id="1c178-130">Otestovat novou aktivitu, přidejte ho do pracovního postupu a nastavit pole se seznamem na tyto dvě hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1c178-130">To test the new activity, add it to a workflow, and set the combo box to the two values.</span></span> <span data-ttu-id="1c178-131">Okno vlastností by měl aktualizovat tak, aby odrážela hodnota pole se seznamem.</span><span class="sxs-lookup"><span data-stu-id="1c178-131">The properties window should update to reflect the combo box value.</span></span>
