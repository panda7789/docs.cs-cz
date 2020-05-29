---
title: Ukázka zjišťování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: 1c6210472b594aec02bdf47f472a1a8b1823230c
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202063"
---
# <a name="workflow-discovery-sample"></a>Ukázka zjišťování pracovního postupu
V této ukázce se dozvíte, jak vytvořit službu pracovního postupu a jak vytvořit vlastní aktivitu kódu, která vyhledává konkrétní službu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vyhledání aktivity a využití pracovního postupu  
  
## <a name="discussion"></a>Účely  
 V první části ukázky se služba pracovního postupu provedla zjistitelným použitím konfigurace. Konfiguraci je také možné použít k odpovídajícímu uplatnění služby s vlastními metadaty (například obory). V klientovi ukázka používá vlastní aktivitu kódu, která používá zjišťování k vyhledání služby, která odpovídá konkrétnímu kontraktu. Aktivita kódu má za výstupem identifikátor URI, který je později používán aktivitou odeslání.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Tato ukázka používá koncové body HTTP, které musí mít správné seznamy ACL adres URL pro spuštění (podrobnosti najdete v tématu [Konfigurace HTTP a HTTPS](../feature-details/configuring-http-and-https.md) ). Provedením následujícího příkazu na příkazovém řádku se zvýšenými oprávněními by se měly přidat příslušné seznamy ACL. Pokud vaše prostředí nerozumí formátu proměnné, nahraďte doménu a uživatelské jméno pro následující argumenty.  
  
    `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`
  
> [!IMPORTANT]
> Ukázky už můžou být na vašem počítači nainstalované. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
