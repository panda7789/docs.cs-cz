---
title: Použití ExpressionTextBox v návrháři vlastní aktivity
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: 6b581b42c882c12425a17b9a518f8957ca10898a
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74715539"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Použití ExpressionTextBox v návrháři vlastní aktivity
V této ukázce se dozvíte, jak používat <xref:System.Activities.Presentation.View.ExpressionTextBox> v Návrháři vlastní aktivity. Vlastní aktivita `MultiAssign`přiřadí dvě řetězcové hodnoty dvěma řetězcovým proměnným. Některé ovládací prvky <xref:System.Activities.Presentation.View.ExpressionTextBox> vážou <xref:System.Activities.InArgument>s a některá vazba na <xref:System.Activities.OutArgument>s.

## <a name="sample-details"></a>Podrobnosti ukázky
 `ArgumentToExpressionConverter` je konvertor typu, který se používá při vytváření výrazů vazby k argumentům. `ConverterParameter` musí být nastavená na `In` nebo `Out` podle potřeby. `InOut` se nepodporuje.

 Atribut `UseLocationExpression` se používá v `OutArgument`s k určení, že výraz by měl být výraz L-hodnota ("levá hodnota" nebo "hodnota umístění"). Ve většině případů je výraz L-hodnoty platným Visual Basicm identifikátorem, který označuje, že `OutArgument` vracená je proměnná nebo název argumentu.

 Atribut `MaxLines` je v tomto příkladu nastaven na jeden a `MinLines` není nastaven. To znamená, že <xref:System.Activities.Presentation.View.ExpressionTextBox> je pevná velikost jednoho řádku bez ohledu na množství textu zadaného uživatelem. Aby bylo možné <xref:System.Activities.Presentation.View.ExpressionTextBox> zvětšit tak, aby odpovídaly vstupu uživatele, nastavte `MaxLines` větší než `MinLines`.

 ExpressionTextBox může být svázána pouze s argumenty a nelze jej svázat s vlastnostmi CLR.

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2010 otevřete soubor ExpressionTextBoxSample. sln.

2. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

#### <a name="to-run-this-sample"></a>Spuštění této ukázky

1. Přidejte do řešení novou konzolovou aplikaci pracovního postupu.

2. Do projektu **ExpressionTextBoxSample** přidejte odkaz z projektu konzolové aplikace nového pracovního postupu.

3. Sestavte řešení.

4. Přetáhněte aktivitu více **přiřazení** z panelu nástrojů a přetáhněte ji do pracovního postupu.

> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [Vývoj aplikací pomocí návrháře postupu provádění](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
