---
title: Selhání zpracování v aktivitě sady vývojový diagram pomocí TryCatch
ms.date: 03/30/2017
ms.assetid: 50922964-bfe0-4ba8-9422-0e7220d514fd
ms.openlocfilehash: cc7630be868a5bdc1a07e8d935e5dd3269b4ae22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="fault-handling-in-a-flowchart-activity-using-trycatch"></a>Selhání zpracování v aktivitě sady vývojový diagram pomocí TryCatch
Tento příklad ukazuje, jak <xref:System.Activities.Statements.TryCatch> aktivitu je možné v rámci aktivitu toku řízení komplexní.  
  
 V této ukázce kódu povýšení a počet podřízených jsou předány jako proměnné, které chcete <xref:System.Activities.Statements.Flowchart> aktivity, která vypočítá slevu podle vzorce, které odpovídají propagační kód. Ukázka zahrnuje imperativní kódu a pracovní postup návrháře verze vzorku.  
  
 V následující tabulce jsou proměnné pro `CreateFlowchartWithFaults` aktivity.  
  
|Parametry|Popis|  
|----------------|-----------------|  
|promoCode|Propagační kód. Typ: řetězec<br /><br /> Možné hodnoty s Popis v závorkách:<br /><br /> -Jedním (jednoduchý)<br />-MNK (Ženatý s žádné dětí.)<br />-MWK (Ženatý s dětí.)|  
|numKids|Počet podřízených prvků. Typ: int|  
  
 `CreateFlowchartWithFaults` Používá aktivitu <xref:System.Activities.Statements.FlowSwitch%601> aktivity, která přepne na `promoCode` argument a vypočítá slevu pomocí následujícího vzorce.  
  
|Hodnota `promoCode`|Diskontní (%)|  
|--------------------------|--------------------|  
|Single|10|  
|MNK|15|  
|MWK|15 + (1 – 1 /`numberOfKids`)\*10 **Poznámka:** potenciálně, může tento výpočet throw <xref:System.DivideByZeroException>. Ano, je výpočet slevy uzavřen do <xref:System.Activities.Statements.TryCatch> aktivity, který zachytí <xref:System.DivideByZeroException> výjimky a nastaví sleva na nula.|  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení FlowchartWithFaultHandling.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Pokud chcete spustit řešení, stisknutím klávesy F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Built-InActivities\FlowChartWithFaultHandling`  
  
## <a name="see-also"></a>Viz také  
 [Pracovní postupy vývojového diagramu](../../../../docs/framework/windows-workflow-foundation/flowchart-workflows.md)  
 [Výjimky](../../../../docs/framework/windows-workflow-foundation/exceptions.md)
