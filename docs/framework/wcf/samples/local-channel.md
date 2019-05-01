---
title: Místní kanál
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 1711909ada4756dd2723f62160eef0ad12c03174
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989830"
---
# <a name="local-channel"></a>Místní kanál
Místní kanál je přenosový kanál Windows Communication Foundation (WCF), který se používá ke komunikaci v rámci stejné doméně aplikace. To je užitečné pro scénáře, kdy klient a služba běží ve stejné doméně aplikace a musí se jim vyhnout nároky na typické kanál zásobníku WCF (serializaci a deserializaci zpráv).  
  
## <a name="demonstrates"></a>Demonstruje  
 Místní kanál  
  
## <a name="discussion"></a>Diskuse  
 Ukázkový soubor obsahuje dva soubory projektu:  
  
- **LocalChannel**: Programové reprezentace místního kanálu v rámci aktuální domény aplikace. V tomto projektu odesílání komponenty umístí zprávu do fronty v paměti a přijímající součást zrušení fronty zprávy ji přijmout.  
  
- **ClientAndService**: Tento projekt hostuje službu v konzolové aplikaci a pak spustí klienta k volání služby z v rámci stejné doméně aplikace.  
  
 Místní kanál návrhu přeskočí zásobníku kanálu a zvýšit rychlost procesu serializace. Místní přenosový kanál se implementuje pomocí fronty k přenosu volání služby z klienta do služby a k vrácení hodnoty zpět do klienta. Místo serializaci parametrů a vrácených hodnot, ukázka zkopíruje objekty.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Sestavte a spusťte LocalChannel řešení.  
  
2. Hostitel služby je spuštěn a klient zavolá službu pomocí místního kanálu. Chcete-li zobrazit výsledky volání služby, zobrazí se okno konzoly.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
