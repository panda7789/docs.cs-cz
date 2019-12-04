---
title: Zpracování chyb v aktivitě FlowChart pomocí TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: 8e3ca59bc9743300a230877a6fbcbed5468a1589
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74710827"
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>Zpracování chyb v aktivitě FlowChart pomocí TryCatch

Tento příklad ukazuje, jak lze použít aktivitu <xref:System.Activities.Statements.TryCatch> v rámci složité aktivity toku řízení.

V této ukázce se propagační kód a počet podřízených položek předávají jako proměnné do aktivity <xref:System.Activities.Statements.Flowchart>, která vypočítá slevu na základě vzorců, které odpovídají kódu pro povýšení. Ukázka zahrnuje imperativní verze kódu a návrháře pracovních postupů v ukázce.

Následující tabulka popisuje proměnné pro aktivitu `CreateFlowchartWithFaults`.

|Parametry|Popis|
|----------------|-----------------|
|promoCode|Propagační kód. Typ: řetězec<br /><br /> Možné hodnoty s popisem v závorkách:<br /><br /> -Single (jedna)<br />-MNK (svatba bez dětí.)<br />-MWK (svatba s dětskými děti)|
|numKids|Počet podřízených objektů. Typ: int|

Aktivita `CreateFlowchartWithFaults` používá <xref:System.Activities.Statements.FlowSwitch%601> aktivity, která se přepíná na argument `promoCode` a vypočítá slevu pomocí následujícího vzorce.

|Hodnota `promoCode`|Sleva (%)|
|--------------------------|--------------------|
|Jednoduché|10|
|MNK|15|
|MWK|15 + (1 – 1/`numberOfKids`)\*10 **Poznámka:** potenciálně může tento výpočet vyvolat <xref:System.DivideByZeroException>. Proto je výpočet slevy zabalen do <xref:System.Activities.Statements.TryCatch> aktivity, která zachytává výjimku <xref:System.DivideByZeroException> a nastaví slevu na nulu.|

#### <a name="to-use-this-sample"></a>Použití této ukázky

1. Pomocí sady Visual Studio 2010 otevřete soubor řešení FlowchartWithFaultHandling. sln.

2. Pro sestavení řešení stiskněte kombinaci kláves CTRL + SHIFT + B.

3. Pokud chcete řešení spustit, stiskněte klávesu F5.

> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.
>
> `<InstallDrive>:\WF_WCF_Samples`
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`

## <a name="see-also"></a>Viz také:

- [Pracovní postupy vývojového diagramu](../flowchart-workflows.md)
- [Výjimky](../exceptions.md)
