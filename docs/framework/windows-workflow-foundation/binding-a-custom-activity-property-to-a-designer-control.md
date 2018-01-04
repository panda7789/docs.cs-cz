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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 79ceeb7406fdae9b4044053e12bec2aad926f26e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="binding-a-custom-activity-property-to-a-designer-control"></a>Vazba vlastnost vlastní aktivity do ovládacího prvku návrháře
Vytvoření vazby návrháře textové pole na argument aktivity je poměrně jednoduché; Vytvoření vazby ovládacího prvku složité návrháře (například pole se seznamem) na aktivity argument příkaz může nést výzvy, ale. Toto téma popisuje, jak vytvořit vazbu argument aktivity do ovládacího prvku pole se seznamem na Návrhář vlastní aktivity.  
  
#### <a name="creating-the-combo-box-item-converter"></a>Vytváření převaděč položky pole se seznamem  
  
1.  Vytvořte nový prázdný řešení v sadě Visual Studio názvem CustomProperty.  
  
2.  Vytvořte novou třídu s názvem ComboBoxItemConverter. Přidat odkaz na System.Windows.Data a mít odvozena od třídy <xref:System.Windows.Data.IValueConverter>. Mít Visual Studio, které implementují rozhraní ke generování zástupných procedur pro `Convert` a `ConvertBack`.  
  
3.  Přidejte následující kód, který `Convert` metoda. Tento kód převede aktivity <xref:System.Activities.InArgument%601> typu <xref:System.String> k hodnota, která má být umístěn v návrháři.  
  
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
  
     Výraz ve výše uvedeném fragmentu kódu můžete vytvořit také pomocí <xref:Microsoft.CSharp.Activities.CSharpValue%601> místo <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
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
  
4.  Přidejte následující kód, který `ConvertBack` metoda. Tento kód převede příchozí položky pole se seznamem zpět do <xref:System.Activities.InArgument%601>.  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                VisualBasicValue<string> vbArgument = new VisualBasicValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(vbArgument);  
                return inArgument;  
    ```  
  
     Výraz ve výše uvedeném fragmentu kódu můžete vytvořit také pomocí <xref:Microsoft.CSharp.Activities.CSharpValue%601> místo <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
    ```  
    // Convert combo box value to InArgument<string>  
                string itemContent = (string)((ComboBoxItem)value).Content;  
                CSharpValue<string> csArgument = new CSharpValue<string>(itemContent);  
                InArgument<string> inArgument = new InArgument<string>(csArgument);  
                return inArgument;  
    ```  
  
#### <a name="adding-the-comboboxitemconverter-to-the-custom-designer-of-an-activity"></a>Přidávání ComboBoxItemConverter do vlastní Návrhář aktivity  
  
1.  Přidáte novou položku do projektu. V dialogovém okně novou položku vyberte uzel pracovního postupu a vyberte Návrhář aktivity jako typ nové položky. Název položky CustomPropertyDesigner.  
  
2.  Pole se seznamem přidáte do nové návrháře. Ve vlastnosti položky, přidejte několik položek do pole se seznamem obsahu hodnotami "Item1" a "Item2".  
  
3.  Upravte XAML pole se seznamem pro přidání nové položky převaděč jako položka převaděč má být použit pro pole se seznamem. Převaděč je přidán jako prostředek v segmentu ActivityDesigner.Resources a určuje převaděč v atributu převaděč pro <xref:System.Windows.Controls.ComboBox>. Všimněte si, že je obor názvů projektu zadané v atributech obory názvů pro Návrhář aktivity; Pokud návrháře pro použití v na jiný projekt, tento obor názvů se musí změnit.  
  
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
  
4.  Vytvořit novou položku typu <xref:System.Activities.CodeActivity>. Ve výchozím kódu vytvořené IDE aktivity jsou dostatečné pro tento příklad.  
  
5.  V definici třídy, přidejte následující atribut:  
  
    ```  
    [Designer(typeof(CustomPropertyDesigner))]  
    ```  
  
     Tento řádek přidruží nový designer novou třídu.  
  
 Nová aktivita by teď měly být přidruženy návrháře. Otestovat novou aktivitu, přidejte ho do pracovního postupu a nastavit pole se seznamem na tyto dvě hodnoty. Okno vlastností by měl aktualizovat tak, aby odrážela hodnota pole se seznamem.
