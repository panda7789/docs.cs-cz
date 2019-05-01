---
title: Asynchronní komunikace
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: a9da04e2c6d3c131603211f53c54fd25dde8d338
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62005586"
---
# <a name="asynchronous-communication"></a>Asynchronní komunikace
Tato ukázka předvádí, jak je komunikace mezi dvěma různými službami Windows Workflow Foundation (WF) provádět asynchronně ve výchozím nastavení.  
  
## <a name="demonstrates"></a>Demonstruje  
 Asynchronní komunikace mezi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] služby.  
  
## <a name="discussion"></a>Diskuse  
 Tato ukázka předvádí, jak komunikaci mezi [!INCLUDE[wf1](../../../../includes/wf1-md.md)] aplikací se provádí asynchronně pomocí zasílání zpráv aktivity poskytované rozhraní .NET Framework.  
  
 Tento příklad se skládá z následujících tří projektů.  
  
 CreditCheckService  
 Tato služba přijímá skóre kredit konkrétní osoby nebo hodnotu položky, která má získat a potom rozhodne, zda tento kredit dostane osobě.  
  
 RentalApprovalService  
 Tato služba přijímá aplikace od osoby, která je potřeba zkontrolovat některé kredit. Tato služba komunikují asynchronně `CreditCheckService` rozhodnout, zda žádosti o kredit je platný.  
  
 Klient  
 Klient komunikuje s synchronně `RentalApprovalService` vědět, jestli je tento kredit schválená.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Klikněte pravým tlačítkem myši **AsynchronousCommunication** řešení a vyberte **vlastnosti**.  
  
2. V **společné vlastnosti**vyberte **spouštěný projekt**a vyberte **více projektů po spuštění**.  
  
3. Přesunout **RentalApprovalService** na první místo v seznamu, za nímž následuje **CreditCheckService**následovaný **klienta**. Nastavte **Start** akci u všech tří projektů.  
  
4. Klikněte na tlačítko **OK**, a stiskněte klávesu F5 ke spuštění ukázky.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
