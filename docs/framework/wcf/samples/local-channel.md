---
title: Místní kanál
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 6bc1fac22f6eed3c9acb6b86f7611cbfb4e1d371
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714887"
---
# <a name="local-channel"></a>Místní kanál
Místní kanál je transportní kanál Windows Communication Foundation (WCF), který se používá ke komunikaci ve stejné doméně aplikace. To je užitečné ve scénářích, kdy klient a služba běží ve stejné aplikační doméně a režie typického zásobníku kanálu WCF (serializace a deserializace zpráv) se musí vyhnout.  
  
## <a name="demonstrates"></a>Demonstruje  
 Místní kanál  
  
## <a name="discussion"></a>Účely  
 Ukázka se skládá ze dvou souborů projektu:  
  
- **LocalChannel**: Programová reprezentace místního kanálu v rámci aktuální domény aplikace. V tomto projektu součást odeslání umístí zprávu do fronty v paměti a přijímající součást rozřadí zprávu k jejímu přijetí.  
  
- **ClientAndService**: Tento projekt hostuje službu v konzolové aplikaci a potom spustí klienta, který bude volat službu ze stejné domény aplikace.  
  
 Návrh místního kanálu přeskočí zásobník kanálů a proces serializace, aby se zvýšila rychlost. Místní transportní kanál je implementován pomocí fronty pro přenos volání služby od klienta ke službě a vrácení hodnoty zpět klientovi. Místo serializace parametrů a vrácených hodnot ukázka kopíruje objekty.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Sestavte a spusťte řešení LocalChannel.  
  
2. Hostitel služby je spuštěn a klient volá službu pomocí místního kanálu. Zobrazí se okno konzoly pro zobrazení výsledků volání služby.  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
