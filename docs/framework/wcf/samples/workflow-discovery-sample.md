---
title: Ukázka zjišťování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: b503e6231741fb049dbd8e9fdaae73c127ceaa51
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/03/2019
ms.locfileid: "74714998"
---
# <a name="workflow-discovery-sample"></a>Ukázka zjišťování pracovního postupu
V této ukázce se dozvíte, jak vytvořit službu pracovního postupu a jak vytvořit vlastní aktivitu kódu, která vyhledává konkrétní službu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vyhledání aktivity a využití pracovního postupu  
  
## <a name="discussion"></a>Účely  
 V první části ukázky se služba pracovního postupu provedla zjistitelným použitím konfigurace. Konfiguraci je také možné použít k odpovídajícímu uplatnění služby s vlastními metadaty (například obory). V klientovi ukázka používá vlastní aktivitu kódu, která používá zjišťování k vyhledání služby, která odpovídá konkrétnímu kontraktu. Aktivita kódu má za výstupem identifikátor URI, který je později používán aktivitou odeslání.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Tato ukázka používá koncové body HTTP, které musí mít správné seznamy ACL adres URL pro spuštění (podrobnosti najdete v tématu [Konfigurace HTTP a HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353) ). Provedením následujícího příkazu na příkazovém řádku se zvýšenými oprávněními by se měly přidat příslušné seznamy ACL. Pokud vaše prostředí nerozumí formátu proměnné, nahraďte doménu a uživatelské jméno pro následující argumenty.  
  
     **netsh http Add urlacl URL =http://+:8000/ uživatel =% DOMAIN%\\ % UserName%**  
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>   
> `<InstallDrive>:\WF_WCF_Samples`  
>   
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] Samples. Tato ukázka se nachází v následujícím adresáři.  
>   
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
