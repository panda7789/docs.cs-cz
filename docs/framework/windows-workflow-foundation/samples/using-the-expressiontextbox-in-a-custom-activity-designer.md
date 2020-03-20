---
title: Použití ExpressionTextBox v návrháři vlastní aktivity
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6d3df9e18c7239f0e4695509d80edfd02e9a9d6f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182771"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Použití ExpressionTextBox v návrháři vlastní aktivity
Tato ukázka ukazuje, <xref:System.Activities.Presentation.View.ExpressionTextBox> jak používat v návrháři vlastní aktivity. Vlastní aktivita `MultiAssign`, přiřadí dvě řetězcové hodnoty dvěma řetězcovým proměnným. Některé <xref:System.Activities.Presentation.View.ExpressionTextBox> ovládací <xref:System.Activities.InArgument>prvky se <xref:System.Activities.OutArgument>vážou na s a některé se vážou na s.

## <a name="sample-details"></a>Podrobnosti ukázky
 Převaděč `ArgumentToExpressionConverter` typu se používá při vazby výrazy argumenty. Musí `ConverterParameter` být nastavena na `In` nebo `Out` podle potřeby. `InOut`není podporována.

 Atribut `UseLocationExpression` se používá `OutArgument`na s určit, že výraz by měl být l-hodnota ("levá hodnota" nebo "hodnota umístění") výraz. Ve většině případů je výraz hodnoty L platným identifikátorem jazyka `OutArgument` Visual Basic, který slouží k označení, že vrácená možnost je název proměnné nebo argumentu.

 Atribut `MaxLines` je nastaven na jeden `MinLines` v tomto příkladu a není nastaven. To znamená, <xref:System.Activities.Presentation.View.ExpressionTextBox> že je pevná velikost jednoho řádku bez ohledu na množství textu zadali uživatel. Chcete-li <xref:System.Activities.Presentation.View.ExpressionTextBox> povolit růst, aby `MaxLines` se `MinLines`vešly vstup uživatele, nastavte větší než .

 ExpressionTextBox může být vázán pouze na argumenty a nemůže být vázán na vlastnosti CLR.

#### <a name="to-use-this-sample"></a>Chcete-li použít tento vzorek

1. Pomocí sady Visual Studio 2010 otevřete soubor ExpressionTextBoxSample.sln.

2. Chcete-li vytvořit řešení, stiskněte kombinaci kláves CTRL+SHIFT+B.

#### <a name="to-run-this-sample"></a>Spuštění této ukázky

1. Přidejte do řešení novou konzolovou aplikaci pracovního postupu.

2. Přidejte odkaz na projekt **ExpressionTextBoxSample** z nového projektu konzoly pracovního postupu.

3. Sestavte řešení.

4. Přetáhněte aktivitu **MultiAssign** z panelu nástrojů a přetáhněte ji do pracovního postupu.

> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Viz také

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [Vývoj aplikací pomocí Návrháře postupu provádění](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
