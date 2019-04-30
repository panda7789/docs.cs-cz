---
title: Vazba vlastní vlastnosti aktivity s ovládacím prvkem návrháře
ms.date: 03/30/2017
ms.assetid: 2e8061ea-10f5-407c-a31f-d0d74ce12f27
ms.openlocfilehash: 142a9eb273a98d3a2d83a1239d6d7c891d5cc305
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945896"
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a>Vazba vlastní vlastnosti aktivity s ovládacím prvkem návrháře

Vytvoření vazby návrhář ovládacího prvku textového pole na argument aktivity je celkem jasné; Vazba komplexního návrhář ovládacího prvku (například pole se seznamem) na argument aktivity příkaz může nést výzvy, ale. Toto téma popisuje, jak vytvořit vazbu argument aktivity do ovládacího prvku pole se seznamem v Návrháři vlastní aktivity.

## <a name="creating-the-combo-box-item-converter"></a>Vytváření převaděč položky pole se seznamem

1. Vytvoření nové prázdné řešení v sadě Visual Studio názvem vlastnosti.

2. Vytvořte novou třídu s názvem ComboBoxItemConverter. Přidejte odkaz na System.Windows.Data a mají být odvozen od třídy <xref:System.Windows.Data.IValueConverter>. Sada Visual Studio implementovat rozhraní za účelem generování zástupných procedur pro `Convert` a `ConvertBack`.

3. Přidejte následující kód, který `Convert` metody. Tento kód převede aktivitu <xref:System.Activities.InArgument%601> typu <xref:System.String> k hodnota, která má být umístěn v návrháři.

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

     Výraz ve výše uvedeném fragmentu kódu můžete vytvořit také pomocí <xref:Microsoft.CSharp.Activities.CSharpValue%601> místo <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.

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

4. Přidejte následující kód, který `ConvertBack` metody. Tento kód převede příchozí položky pole se seznamem zpět do <xref:System.Activities.InArgument%601>.

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(vbArgument);
                return inArgument;
    ```

     Výraz ve výše uvedeném fragmentu kódu můžete vytvořit také pomocí <xref:Microsoft.CSharp.Activities.CSharpValue%601> místo <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.

    ```csharp
    // Convert combo box value to InArgument<string>
                string itemContent = (string)((ComboBoxItem)value).Content;
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);
                InArgument<string> inArgument = new InArgument<string>(csArgument);
                return inArgument;
    ```

## <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a>Přidávání ComboBoxItemConverter do vlastního návrháře aktivity

1. Přidáte novou položku do projektu. V dialogovém okně Nová položka vyberte uzel pracovní postup a vyberte Návrhář aktivity jako typ nová položka. Název položky CustomPropertyDesigner.

2. Přidáte pole se seznamem do nového návrháře. Ve vlastnosti Items přidejte několik položek k poli se seznamem obsahu hodnotami "Item1" a "item2 –".

3. Upravte XAML pole se seznamem přidání nové položky převaděč jako převaděč položka má být použit pro pole se seznamem. Převaděč se přidá jako prostředek v segmentu ActivityDesigner.Resources a určuje převaděč v atributu převaděč pro <xref:System.Windows.Controls.ComboBox>. Všimněte si, že je obor názvů projektu určený v atributech obory názvů pro Návrhář aktivity; Pokud návrháře se má použít v jiném projektu, tento obor názvů se musí změnit.

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

4. Vytvoření nové položky typu <xref:System.Activities.CodeActivity>. V tomto příkladu bude stačit výchozí kód vytvořený pomocí rozhraní IDE pro aktivitu.

5. Přidejte následující atribut pro definici třídy:

    ```csharp
    [Designer(typeof(CustomPropertyDesigner))]
    ```

     Tento řádek přiřadí nový Návrhář novou třídu.

 Nová aktivita by měly být nyní přidružené návrháře. Otestovat novou aktivitu, přidejte ji do pracovního postupu a nastavte pole se seznamem dvou hodnot. V okně Vlastnosti by měl aktualizovat tak, aby odrážely hodnota pole se seznamem.
