---
title: Korelovaná Kalkulačka
ms.date: 03/30/2017
ms.assetid: c365166e-6552-49a4-bf17-9f4e597d4d41
ms.openlocfilehash: 71cfdd0906ef20ec36b76ef5e508a4551b9fe3fe
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43384668"
---
# <a name="correlated-calculator"></a>Korelovaná Kalkulačka
Tento příklad ukazuje, jak pomocí aktivit zasílání zpráv (<xref:System.ServiceModel.Activities.Receive> a <xref:System.ServiceModel.Activities.SendReply>) v návrháři se korelace na základě obsahu na základě parametru ve zprávě. V tomto scénáři jsou operace kalkulačky v paralelní doprovodný. Instance a korelaci (na základě `CalculatorId`) se vytvoří, když je první zpráva odeslána do pracovního postupu a následné zprávy se stejnou `CalculatorId` se odesílají do této instance, dokud volat operaci resetování. Klient je implementovaný jako aplikaci WPF, která používá proxy server založený na kódu klienta ke komunikaci se službou.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Spustit [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] v zvýšenou úroveň oprávnění, otevřete soubor řešení For.sln.  
  
    1.  Přejděte do složky, která obsahuje [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
    2.  Klikněte pravým tlačítkem na Devenv.exe a vyberte **spustit jako správce**.  
  
2.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení CorrelatedCalculator.sln.  
  
3.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
4.  Chcete-li spustit projekt služby, stiskněte CTRL + F5.  
  
5.  Jakmile služba je připravená a naslouchá pro zprávy, v Průzkumníku řešení klikněte pravým tlačítkem na projekt klienta a spusťte jej.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\CorellatedCalculator`