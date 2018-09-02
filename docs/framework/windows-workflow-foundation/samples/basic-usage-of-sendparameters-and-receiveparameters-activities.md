---
title: Základní použití aktivit SendParameters a ReceiveParameters
ms.date: 03/30/2017
ms.assetid: 1b6b1681-3d41-403f-bfe2-3f600f24aa8c
ms.openlocfilehash: c13999ad1571a6413e30e801b6c642000f8e4654
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2018
ms.locfileid: "43467692"
---
# <a name="basic-usage-of-sendparameters-and-receiveparameters-activities"></a>Základní použití aktivit SendParameters a ReceiveParameters
Tento příklad ukazuje použití <xref:System.ServiceModel.Activities.SendParametersContent> a <xref:System.ServiceModel.Activities.ReceiveParametersContent> aktivity. Služba zpřístupňuje jedna operace, která přijímá řetězcový argument a vrátí vstupní zpět do klienta. Vzorek ukazuje, jak nastavit parametry pro tyto zasílání zpráv aktivity.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Services\SendReceiveParameters`  
  
#### <a name="using-this-sample"></a>Pomocí této ukázky  
  
1.  Načítání řešení projektu v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a sestavte projekt.  
  
2.  Nejprve spusťte aplikaci EchoWorkflowService vygenerované v \EchoWorkflowService\bin\debug [základní adresář řešení].  
  
3.  Za druhé spusťte aplikaci EchoWorkflowClient vygenerované v \EchoWorkflowClient\bin\debug [základní adresář řešení].  
  
4.  Klient volá operace služby Echo a zobrazí výsledky. Jakmile budete hotovi, stisknutím klávesy ENTER ukončete klienta a pak službu.