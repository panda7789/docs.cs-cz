---
title: Služba zjišťování směrovačů
ms.date: 03/30/2017
ms.assetid: 3d30af47-b24f-40e5-833a-24d77125c9e6
ms.openlocfilehash: b98568dd00841b3f2e86ee1fd69390b690e2bf73
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="discovery-router-service"></a>Služba zjišťování směrovačů
Tento příklad znázorňuje způsob zjišťování zprávy předány jiný koncový bod.  
  
## <a name="demonstrates"></a>Demonstruje  
 Zjišťování směrování  
  
## <a name="discussion"></a>Diskusní  
 Zjišťování směrování je užitečné v scénář, ve kterém klient hledá služby pomocí proxy serveru a proxy server nemá informace o těchto služeb, ale zná jiné proxy. Tento proxy server může předat paket zjišťování od tohoto klienta na druhý server proxy. Druhý proxy server můžete vyhledejte službu a vrátit odpovědí na původní klienta.  
  
 V této ukázce klient odešle zprávu do směrování součást zjišťování. Tato zpráva je odeslána na konkrétní na směrovači zjišťování. Směrovač pak předá zprávu UDP vícesměrového vysílání koncový bod. Test zprávy nedostane mimo vícesměrového vysílání koncový bod a službu nenaslouchá UDP, vícesměrového vysílání, že adresa reaguje na zjišťování směrovače. Směrovač zjišťování shromažďuje odpovědi a odešle je zpět do klienta.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Sestavte ukázku.  
  
2.  Spuštění spustitelného souboru DiscoveryRouter.  
  
3.  Spusťte spustitelný soubor služby z adresáře sestavení.  
  
4.  Spustíte spustitelný soubor klienta. Všimněte si, že klient vyhledá službu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\DiscoveryRouter`
