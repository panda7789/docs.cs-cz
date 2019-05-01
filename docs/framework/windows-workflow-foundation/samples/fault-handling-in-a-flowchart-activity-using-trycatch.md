---
title: Zpracování chyb v aktivitě FlowChart pomocí TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 81bfeb911658a6f363a9f0f95ecc7db68a02dbe2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005040"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>Zpracování chyb v aktivitě FlowChart pomocí TryCatch
Tato ukázka předvádí, jak <xref:System.Activities.Statements.TryCatch> aktivita se dá použít v rámci aktivity toku řízení komplexní.

 V této ukázce propagační kód, který a počet podřízených jsou předány jako proměnné <xref:System.Activities.Statements.Flowchart> aktivitu, která vypočítá a uplatnit tak slevu podle vzorce, které odpovídají propagační kód. Ukázka zahrnuje imperativního kódu pracovního postupu návrháře verze a ukázky.

 Následující tabulka obsahuje podrobnosti o proměnné pro `CreateFlowchartWithFaults` aktivity.

|Parametry|Popis|
|----------------|-----------------|
|promoCode|Propagační kód. Zadejte: String<br /><br /> Možné hodnoty s popisem v závorkách:<br /><br /> -Jednou (jednoduchý)<br />-MNK (vdaná s žádné děti.)<br />-MWK (vdaná s děti.)|
|numKids|Počet podřízených. Typ: int|

 `CreateFlowchartWithFaults` Používá aktivitu <xref:System.Activities.Statements.FlowSwitch%601> aktivitu, která se přepne na `promoCode` argument a vypočítá slevu pomocí tohoto vzorce.

|Hodnota `promoCode`|Slevy (%)|
|--------------------------|--------------------|
|Single|10|
|MNK|15|
|MWK|15 + (1 – 1 /`numberOfKids`)\*10 **Poznámka:**  Případně může vyvolat tento výpočet <xref:System.DivideByZeroException>. Ano, je výpočet slevy zabalené v <xref:System.Activities.Statements.TryCatch> aktivitu, která zachytává <xref:System.DivideByZeroException> výjimky a nastaví slevy na nulu.|

#### <a name="to-use-this-sample"></a>Pro fungování této ukázky

1. Pomocí sady Visual Studio 2010, otevřete soubor řešení FlowchartWithFaultHandling.sln.

2. Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Abyste mohli spustit řešení, stiskněte klávesu F5.

> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a>Viz také:

- [Pracovní postupy vývojového diagramu](../flowchart-workflows.md)
- [Výjimky](../exceptions.md)
