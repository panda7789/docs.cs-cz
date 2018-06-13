---
title: Ukázka zjišťování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: ec4b956a28048c0c30a4eadb0473adb34334fa92
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33503436"
---
# <a name="workflow-discovery-sample"></a>Ukázka zjišťování pracovního postupu
Tento příklad znázorňuje, jak zjistitelnost služby pracovních postupů a jak vytvořit vlastní kód aktivity, která hledá pro konkrétní službu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Aktivita zjišťování najít a využití pracovního postupu  
  
## <a name="discussion"></a>Diskusní  
 V první části Ukázky, se provádí zjistitelný služby pracovního postupu pomocí konfigurace. Konfigurace lze také použít službu správně s vlastní metadata (například obory). Příklad na straně klienta používá aktivitu vlastní kód, který používá k hledání zjišťování služby odpovídající konkrétní smlouvou. Kód aktivity výstupy identifikátor URI, který se později používá pomocí aktivity odeslání.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Tato ukázka používá koncových bodů protokolu HTTP, které musí mít správnou adresu URL seznamy řízení přístupu ke spuštění (v tématu [konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti). Spuštěním následujícího příkazu na příkazovém řádku se zvýšenými oprávněními měli přidat příslušné seznamy ACL. Nahraďte domény a uživatelské jméno pro následující argumenty, pokud vaše prostředí nerozumí formát proměnné.  
  
     **netsh http přidejte adresu url urlacl =http://+:8000/ uživatele domény % =\\% UserName %**  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
