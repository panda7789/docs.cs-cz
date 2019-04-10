---
title: Použití ExpressionTextBox v návrháři vlastní aktivity
ms.date: 03/30/2017
ms.assetid: f82e73e7-a256-4a4d-82b7-c0d62f4ab5e7
ms.openlocfilehash: c85254f1ae7ba8a269568cf1a14acf367b595e33
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2019
ms.locfileid: "59344972"
---
# <a name="using-the-expressiontextbox-in-a-custom-activity-designer"></a>Použití ExpressionTextBox v návrháři vlastní aktivity
Tento příklad ukazuje způsob použití <xref:System.Activities.Presentation.View.ExpressionTextBox> v Návrháři vlastní aktivity. Vlastní aktivita `MultiAssign`, přiřadí dva řetězcové hodnoty dvou proměnných řetězce. Některé <xref:System.Activities.Presentation.View.ExpressionTextBox> svázat ovládací prvky <xref:System.Activities.InArgument>svázat s a některé <xref:System.Activities.OutArgument>s.

## <a name="sample-details"></a>Ukázka podrobnosti
 `ArgumentToExpressionConverter` Se používá při vytváření vazby výrazy na argumenty konvertor typu. `ConverterParameter` Musí být nastaveno na `In` nebo `Out` podle potřeby. `InOut` není podporováno.

 `UseLocationExpression` Atribut se používá na `OutArgument`s určit, že výraz musí být výraz L-value ("vlevo hodnota" nebo "umístění value"). Ve většině případů výraz L-hodnota je platným identifikátorem jazyka Visual Basic používá k označení, že `OutArgument` vracených je název proměnné nebo argumentu.

 `MaxLines` Atribut je nastaven na jednu v tomto příkladu a `MinLines` není nastaven. Znamená to, že <xref:System.Activities.Presentation.View.ExpressionTextBox> pevnou velikost jednoho řádku bez ohledu na to, jaká část textu zadaného uživatelem. Chcete-li povolit <xref:System.Activities.Presentation.View.ExpressionTextBox> růst podle uživatelského vstupu, nastavte `MaxLines` větší než `MinLines`.

 ExpressionTextBox může být vázaný jedině na argumenty a nemůže být vázaný na vlastnosti CLR.

#### <a name="to-use-this-sample"></a>Pro fungování této ukázky

1. Pomocí sady Visual Studio 2010, otevřete soubor ExpressionTextBoxSample.sln.

2. Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.

#### <a name="to-run-this-sample"></a>Tuto ukázku spustit

1. Přidáte novou konzolovou aplikaci pracovního postupu do řešení.

2. Přidejte odkaz na **ExpressionTextBoxSample** projekt z nový projekt konzolové aplikace pracovního postupu.

3. Sestavte řešení.

4. Přetáhněte **MultiAssign** aktivity ze sady nástrojů a umístěte ho do pracovního postupu.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\CustomActivities\CustomActivityDesigners\ExpressionTextBox`  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Activities.Presentation.View.ExpressionTextBox>
- [Vývoj aplikací pomocí návrháře postupu provádění](/visualstudio/workflow-designer/developing-applications-with-the-workflow-designer)
