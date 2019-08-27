---
title: Služba zjišťování směrovačů
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: 9434c26fb12b73ea4f1c185658b03cb95a3a2310
ms.sourcegitcommit: 581ab03291e91983459e56e40ea8d97b5189227e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/27/2019
ms.locfileid: "70039832"
---
# <a name="discovery-router-service"></a>Služba zjišťování směrovačů
Tato ukázka předvádí, jak předávané zprávy zjišťování do jiného koncového bodu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Směrování zjišťování  
  
## <a name="discussion"></a>Účely  
 Směrování zjišťování je užitečné ve scénáři, ve kterém klient hledá službu pomocí proxy serveru a proxy server tuto službu neví, ale ví o jiném proxy serveru. Tento proxy server může přeposláním paketu zjišťování od tohoto klienta k druhému proxy serveru. Druhý proxy server může hledat službu a vracet odpovědi původnímu klientovi.  
  
 V této ukázce klient pošle zprávu na součást směrování zjišťování. Tato zpráva se odešle do konkrétního koncového bodu ve směrovači zjišťování. Směrovač pak přepošle zprávu na koncový bod vícesměrového vysílání UDP. Zpráva testu se překročí na koncový bod vícesměrového vysílání a služba, která naslouchá na adrese vícesměrového vysílání UDP, reaguje na tento směrovač zjišťování. Směrovač zjišťování shromáždí odpovědi a pošle je zpátky klientovi.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Sestavte ukázku.  
  
2. Spusťte spustitelný soubor DiscoveryRouter.  
  
3. Spusťte spustitelný soubor služby z adresáře buildu.  
  
4. Spusťte klientský spustitelný soubor. Všimněte si, že klient vyhledává službu.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
