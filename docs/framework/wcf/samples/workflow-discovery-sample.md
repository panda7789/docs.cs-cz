---
title: "Ukázka zjišťování pracovního postupu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3cf150562beaacb56596b90e1680adca97dd24a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="workflow-discovery-sample"></a>Ukázka zjišťování pracovního postupu
Tento příklad znázorňuje, jak zjistitelnost služby pracovních postupů a jak vytvořit vlastní kód aktivity, která hledá pro konkrétní službu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Aktivita zjišťování najít a využití pracovního postupu  
  
## <a name="discussion"></a>Diskusní  
 V první části Ukázky, se provádí zjistitelný služby pracovního postupu pomocí konfigurace. Konfigurace lze také použít službu správně s vlastní metadata (například obory). Příklad na straně klienta používá aktivitu vlastní kód, který používá k hledání zjišťování služby odpovídající konkrétní smlouvou. Kód aktivity výstupy identifikátor URI, který se později používá pomocí aktivity odeslání.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Tato ukázka používá koncových bodů protokolu HTTP, které musí mít správnou adresu URL seznamy řízení přístupu ke spuštění (v tématu [konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti). Spuštěním následujícího příkazu na příkazovém řádku se zvýšenými oprávněními měli přidat příslušné seznamy ACL. Nahraďte domény a uživatelské jméno pro následující argumenty, pokud vaše prostředí nerozumí formát proměnné.  
  
     **netsh http přidejte adresu url urlacl = http: / / +: 8000 / uživatele domény % =\\% UserName %**  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
