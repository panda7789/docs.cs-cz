---
title: Zpracování chyb v aktivitě FlowChart pomocí TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 42eb660aff01c7e29227c28a6ad0d47d4370eb91
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/24/2019
ms.locfileid: "70016020"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>Zpracování chyb v aktivitě FlowChart pomocí TryCatch

Tento příklad ukazuje, <xref:System.Activities.Statements.TryCatch> jak lze aktivitu použít v rámci složité aktivity toku řízení.

V této ukázce se propagační kód a počet podřízených položek předávají jako proměnné do <xref:System.Activities.Statements.Flowchart> aktivity, která vypočítá slevu na základě vzorců, které odpovídají kódu pro povýšení. Ukázka zahrnuje imperativní verze kódu a návrháře pracovních postupů v ukázce.

Následující tabulka popisuje proměnné pro `CreateFlowchartWithFaults` aktivitu.

|Parametry|Popis|
|----------------|-----------------|
|promoCode|Propagační kód. Zadejte: String<br /><br /> Možné hodnoty s popisem v závorkách:<br /><br /> -Single (jedna)<br />-MNK (svatba bez dětí.)<br />-MWK (svatba s dětskými děti)|
|numKids|Počet podřízených objektů. Typ: int|

`CreateFlowchartWithFaults` Aktivita používá`promoCode` aktivitu, která se přepíná na argument a vypočítá slevu pomocí následujícího vzorce. <xref:System.Activities.Statements.FlowSwitch%601>

|Hodnota`promoCode`|Sleva (%)|
|--------------------------|--------------------|
|Single|10|
|MNK|15|
|MWK|15 + (1 – 1/`numberOfKids`)\*10 **Poznámka:**  Tento výpočet může způsobit vyvolání <xref:System.DivideByZeroException>. Proto je výpočet slevy zabalen do <xref:System.Activities.Statements.TryCatch> aktivity, která <xref:System.DivideByZeroException> výjimku zachytí, a nastaví slevu na nulu.|

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2010 otevřete soubor řešení FlowchartWithFaultHandling. sln.

2. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Pokud chcete řešení spustit, stiskněte klávesu F5.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a>Viz také:

- [Pracovní postupy vývojového diagramu](../flowchart-workflows.md)
- [Výjimky](../exceptions.md)
