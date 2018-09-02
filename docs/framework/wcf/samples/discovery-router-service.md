---
title: Služba zjišťování směrovačů
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 9c0c409eb6cf3146a198b9f4bcd6d76660f5da36
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43409111"
---
# <a name="discovery-router-service"></a>Služba zjišťování směrovačů
Tento příklad ukazuje, jak předávat zprávy zjišťování do jiného koncového bodu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Zjišťování směrování  
  
## <a name="discussion"></a>Diskuse  
 Zjišťování směrování je užitečné pro scénáře, ve kterém hledá klienta ke službě pomocí proxy serveru a proxy serveru Nepozná takové služby, ale zná další proxy. Tento proxy server může předat paket zjišťování od tohoto klienta na druhý server proxy. Druhý proxy můžete vyhledat službu a vracet odpovědi na původní klienta.  
  
 V této ukázce klient odešle zprávu do komponenty směrování zjišťování. Tato zpráva se pošle určitý koncový bod zjišťování směrovače. Směrovač pak předá zprávu UDP vícesměrového vysílání koncový bod. Průzkumné zprávy dostane k vícesměrového vysílání koncových bodů a služba naslouchá na vícesměrového vysílání UDP, že adresa reaguje na zjišťování směrovače. Zjišťování směrovače odpovědi shromažďuje a odesílá zpět do klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Sestavte ukázku.  
  
2.  Spuštění spustitelného souboru DiscoveryRouter.  
  
3.  Spusťte spustitelný soubor služby z adresáře sestavení.  
  
4.  Spusťte klientský spustitelný soubor. Všimněte si, že klient vyhledá službu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
