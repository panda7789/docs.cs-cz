---
title: Místní kanál
ms.date: 03/30/2017
ms.assetid: fa1917a4-f701-4e82-a439-14a16282c7cc
ms.openlocfilehash: 87e140395ac2fb5702d8655cf970da8a60c991ec
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79144504"
---
# <a name="local-channel"></a>Místní kanál
Místní kanál je přenosový kanál WCF (Windows Communication Foundation), který se používá pro komunikaci v rámci stejné domény aplikace. To je užitečné pro scénáře, kde klient a služba jsou spuštěny ve stejné doméně aplikace a je třeba se vyhnout režii typického zásobníku kanálu WCF (serializace a deserializace zpráv).  
  
## <a name="demonstrates"></a>Demonstruje  
 Místní kanál  
  
## <a name="discussion"></a>Diskuse  
 Ukázka se skládá ze dvou souborů projektu:  
  
- **LocalChannel**: Programová reprezentace místního kanálu v rámci aktuální domény aplikace. V tomto projektu odesílající součást umístí zprávu do fronty v paměti a přijímající součást odřadí zprávu do fronty, aby ji přijala.  
  
- **ClientAndService**: Tento projekt je hostitelem služby v konzolové aplikaci a potom spustí klienta pro volání služby ze stejné domény aplikace.  
  
 Návrh místního kanálu přeskočí zásobník kanálu i proces serializace, aby se zvýšila rychlost. Kanál místního přenosu je implementován pomocí fronty k přenosu volání služby z klienta do služby a vrátit hodnotu klientovi zpět. Místo serializace parametrů a vrácených hodnot ukázka objekty zkopíruje.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Sestavení a spuštění řešení LocalChannel.  
  
2. Hostitel služby je spuštěn a klient volá službu pomocí místního kanálu. Zobrazí se okno konzoly zobrazující výsledky volání služby.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\LocalChannel`
