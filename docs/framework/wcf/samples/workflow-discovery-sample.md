---
title: Ukázka zjišťování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 1076e7045ca546fed7e6902f69406bfc002c4c26
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777103"
---
# <a name="workflow-discovery-sample"></a>Ukázka zjišťování pracovního postupu
Tato ukázka předvádí, jak zjistitelnost služby pracovního postupu a jak si můžete vytvořit vlastní kód aktivitou, která hledá konkrétní službu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Zjišťování najít aktivitu a využití pracovního postupu  
  
## <a name="discussion"></a>Diskuse  
 V první části Ukázky tvoří zjistitelné služby pracovního postupu pomocí konfigurace. Konfigurace lze také použít službu odpovídajícím způsobem s vlastní metadata (například obory). Ukázka používá na klientovi, kód vlastní aktivitu, která používá k hledání zjišťování služby odpovídající konkrétní smlouvy. Aktivita s kódem výstupy identifikátor URI, který se používá později pomocí aktivity odeslání.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Tato ukázka používá koncové body HTTP, které musí mít odpovídající seznamy ACL adresu URL pro spuštění (viz [konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti). Spuštěním následujícího příkazu na příkazovém řádku se zvýšenými oprávněními přidejte příslušné seznamy ACL. Nahraďte doména a uživatelské jméno pro následující argumenty, pokud vaše prostředí nerozumí formát proměnné.  
  
     **netsh http přidat adresu url urlacl =http://+:8000/ uživatele domény % =\\% UserName %**  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
