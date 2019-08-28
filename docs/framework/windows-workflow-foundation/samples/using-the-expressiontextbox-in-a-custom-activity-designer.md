---
title: Použití ExpressionTextBox v návrháři vlastní aktivity
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: bfac07d64cd5e30c3475d4e269c16597905ea829
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70045358"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Použití ExpressionTextBox v návrháři vlastní aktivity
<xref:System.Activities.Presentation.View.ExpressionTextBox> V této ukázce se dozvíte, jak používat v Návrháři vlastní aktivity. Vlastní aktivita `MultiAssign`přiřadí dvě řetězcové hodnoty dvěma řetězcovým proměnným. Některé <xref:System.Activities.Presentation.View.ExpressionTextBox> ovládací prvky přiváží k <xref:System.Activities.InArgument>s a některé <xref:System.Activities.OutArgument>vazby na s.

## <a name="sample-details"></a>Podrobnosti ukázky
 `ArgumentToExpressionConverter` Je konvertor typu, který se používá při vytváření výrazů vazby k argumentům. Musí být nastavené na `In` nebo `Out` podle potřeby. `ConverterParameter` `InOut`není podporováno.

 `UseLocationExpression` Atribut se `OutArgument`používá pro s k určení, že výraz by měl být výraz L-hodnoty ("levá hodnota" nebo "hodnota umístění"). Ve většině případů je výraz L-hodnoty platným Visual Basic identifikátor, který označuje, že `OutArgument` vracená je proměnná nebo název argumentu.

 Atribut je v tomto příkladu nastaven na jeden a `MinLines` není nastaven. `MaxLines` To znamená, že <xref:System.Activities.Presentation.View.ExpressionTextBox> je pevná velikost jednoho řádku bez ohledu na množství textu zadaného uživatelem. Aby bylo umožněno <xref:System.Activities.Presentation.View.ExpressionTextBox> zvětšení podle uživatelského vstupu, je nastavena `MaxLines` větší než `MinLines`.

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
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [Vývoj aplikací pomocí návrháře postupu provádění](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
