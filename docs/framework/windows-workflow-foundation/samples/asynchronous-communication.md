---
title: Asynchronní komunikace
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: b5cf788ce4587dacb5a7642e25cb1b5b1e6f3e3c
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70044362"
---
# <a name="asynchronous-communication"></a>Asynchronní komunikace
Tato ukázka předvádí, jak je komunikace mezi dvěma různými programovací model Windows Workflow Foundation (WF) ve výchozím nastavení prováděna asynchronně.  
  
## <a name="demonstrates"></a>Demonstruje  
 Asynchronní komunikace mezi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] službami.  
  
## <a name="discussion"></a>Účely  
 V této ukázce se dozvíte, [!INCLUDE[wf1](../../../../includes/wf1-md.md)] jak je komunikace mezi aplikacemi prováděna asynchronně pomocí aktivit zasílání zpráv, které poskytuje .NET Framework.  
  
 Tato ukázka se skládá z následujících tří projektů.  
  
 CreditCheckService  
 Tato služba obdrží kreditní skóre konkrétní osoby nebo hodnotu položky, která má být získána, a pak rozhodne, zda je daný kredit dán osobě.  
  
 RentalApprovalService  
 Tato služba obdrží aplikaci od osoby, která je v potřebě nějakého kreditu. Tato služba komunikuje asynchronně s nástrojem `CreditCheckService` k rozhodnutí, zda je aplikace pro kredit platná.  
  
 Klient  
 Klient komunikuje synchronně s nástrojem `RentalApprovalService` , aby bylo možné zjistit, zda je kredit schválen.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Klikněte pravým tlačítkem na řešení **AsynchronousCommunication** a vyberte **vlastnosti**.  
  
2. V možnosti **společné vlastnosti**vyberte možnost **projekt po spuštění**a vyberte možnost **více projektů po spuštění**.  
  
3. Přesuňte **RentalApprovalService** na první pozici v seznamu, za kterou následuje **CreditCheckService**a pak na **klienta**. Nastavte akci **spuštění** na všech třech projektech.  
  
4. Klikněte na **OK**a stisknutím klávesy F5 spusťte ukázku.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
