---
title: Ukázka zjišťování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 9a0d3ad22b4663ee71b5b2aa8d0e3d64f20996d8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59311655"
---
# <a name="workflow-discovery-sample"></a>Ukázka zjišťování pracovního postupu
Tato ukázka předvádí, jak zjistitelnost služby pracovního postupu a jak si můžete vytvořit vlastní kód aktivitou, která hledá konkrétní službu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Zjišťování najít aktivitu a využití pracovního postupu  
  
## <a name="discussion"></a>Diskuse  
 V první části Ukázky tvoří zjistitelné služby pracovního postupu pomocí konfigurace. Konfigurace lze také použít službu odpovídajícím způsobem s vlastní metadata (například obory). Ukázka používá na klientovi, kód vlastní aktivitu, která používá k hledání zjišťování služby odpovídající konkrétní smlouvy. Aktivita s kódem výstupy identifikátor URI, který se používá později pomocí aktivity odeslání.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Tato ukázka používá koncové body HTTP, které musí mít odpovídající seznamy ACL adresu URL pro spuštění (viz [konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti). Spuštěním následujícího příkazu na příkazovém řádku se zvýšenými oprávněními přidejte příslušné seznamy ACL. Nahraďte doména a uživatelské jméno pro následující argumenty, pokud vaše prostředí nerozumí formát proměnné.  
  
     **netsh http přidat adresu url urlacl =http://+:8000/ uživatele domény % =\\% UserName %**  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
