---
title: Asynchronní komunikace
ms.date: 03/30/2017
ms.assetid: 128dc092-9eb2-4e33-9470-9a7f62b60df6
ms.openlocfilehash: e1bc63b5d3178b8e98350dedd8eb0791e0e35589
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79142873"
---
# <a name="asynchronous-communication"></a>Asynchronní komunikace
Tato ukázka ukazuje, jak se ve výchozím nastavení provádí komunikace mezi dvěma různými službami Nadace pracovních postupů systému Windows (WF).  
  
## <a name="demonstrates"></a>Demonstruje  
 Asynchronní komunikace [!INCLUDE[wf1](../../../../includes/wf1-md.md)] mezi službami.  
  
## <a name="discussion"></a>Diskuse  
 Tato ukázka ukazuje, [!INCLUDE[wf1](../../../../includes/wf1-md.md)] jak se komunikace mezi aplikacemi provádí asynchronně pomocí zasílání zpráv aktivity poskytované rozhraní .NET Framework.  
  
 Tento příklad se skládá z následujících tří projektů.  
  
 Služba CreditCheckService  
 Tato služba obdrží kreditní skóre určité osoby nebo hodnotu položky, kterou chcete získat, a poté rozhodne, zda je úvěr dané osobě poskytnut.  
  
 Služba RentalApprovalService  
 Tato služba obdrží žádost od osoby, která potřebuje nějaký kredit. Tato služba komunikuje asynchronně s `CreditCheckService` rozhodnout, zda je platná aplikace úvěru.  
  
 Klient  
 Klient synchronně komunikuje s tím, `RentalApprovalService` zda je úvěr schválen.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Klepněte pravým tlačítkem myši na řešení **AsynchronousCommunication** a vyberte příkaz **Vlastnosti**.  
  
2. V **pole Common Properties**vyberte možnost Projekt po **spuštění**a **vyberte možnost Více projektů po spuštění**.  
  
3. Přesuňte **RentalApprovalService** na první pozici v seznamu, následovanou **CreditCheckService**, následovanou **Klientem**. Nastavte akci **Zahájení** u všech tří projektů.  
  
4. Klepněte na tlačítko **OK**a spusťte ukázku stisknutím klávesy F5.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\AsynchronousCommunication`
