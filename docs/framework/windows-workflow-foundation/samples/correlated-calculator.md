---
title: Korelační kalkulačky
ms.date: 03/30/2017
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
ms.openlocfilehash: 77e13b3ca913d2432cfe5d4a95e83764effbb109
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="correlated-calculator"></a>Korelační kalkulačky
Tento příklad znázorňuje způsob použití zasílání zpráv aktivity (<xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>) v návrháři se korelace na základě obsahu na základě parametru ve zprávě. V tomto scénáři jsou operace kalkulačky v paralelní convoy. Instance a existuje korelace (na základě `CalculatorId`) se vytvoří, když je první zpráva odeslána do pracovního postupu a dalších zpráv se stejným `CalculatorId` se odesílají do této instance, dokud operace resetování, se nazývá. Klient je implementovaný jako WPF aplikace, která používá proxy server založené na kódu klienta ke komunikaci se službou.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] v zvýšenými oprávněními, otevřete soubor řešení For.sln.  
  
    1.  Přejděte do složky, která obsahuje [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Klikněte pravým tlačítkem na Devenv.exe a vyberte **spustit jako správce**.  
  
2.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení CorrelatedCalculator.sln.  
  
3.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
4.  Chcete-li spustit projekt služby, stiskněte CTRL + F5.  
  
5.  Jakmile služba je připravena a naslouchání pro zprávy, v Průzkumníku řešení klikněte pravým tlačítkem na projekt klienta a spusťte ji.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`