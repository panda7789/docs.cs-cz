---
title: Služba zjišťování směrovačů
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 149dd69cdd1972465f4b7cb48ab657492d3f21d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183731"
---
# <a name="discovery-router-service"></a>Služba zjišťování směrovačů
Tato ukázka ukazuje, jak předat zprávy zjišťování do jiného koncového bodu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Směrování zjišťování  
  
## <a name="discussion"></a>Diskuse  
 Směrování zjišťování je užitečné ve scénáři, ve kterém klient hledá službu pomocí proxy serveru a proxy server o takové službě neví, ale ví o jiném serveru proxy. Tento proxy server může předat paket zjišťování z tohoto klienta druhému serveru proxy. Druhý proxy server může vyhledat službu a vrátit odpovědi původnímu klientovi.  
  
 V této ukázce klient odešle zprávu součásti směrování zjišťování. Tato zpráva je odeslána do určitého koncového bodu na směrovači zjišťování. Směrovač pak předá zprávu koncovému bodu vícesměrového vysílání UDP. Zpráva sondy zhasne do koncového bodu vícesměrového vysílání a služba naslouchající na adrese vícesměrového vysílání UDP odpoví na tento směrovač zjišťování. Zjišťování směrovač shromažďuje odpovědi a odešle je zpět klientovi.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Sestavte ukázku.  
  
2. Spusťte spustitelný soubor DiscoveryRouter.  
  
3. Spusťte spustitelný soubor služby z adresáře sestavení.  
  
4. Spusťte spustitelný soubor klienta. Všimněte si, že klient vyhledá službu.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
