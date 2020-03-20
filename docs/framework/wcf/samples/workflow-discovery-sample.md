---
title: Ukázka zjišťování pracovního postupu
ms.date: 03/30/2017
ms.assetid: 82cc43f1-3c8f-4771-ac19-a75ac936e2c3
ms.openlocfilehash: b3a2d88028f3854746d4e1d2fad80aae4f6be7be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143483"
---
# <a name="workflow-discovery-sample"></a>Ukázka zjišťování pracovního postupu
Tato ukázka ukazuje, jak zjistit službu pracovního postupu a jak vytvořit vlastní aktivitu kódu, která vyhledá konkrétní službu.  
  
## <a name="demonstrates"></a>Demonstruje  
 Zjišťování aktivity hledání a využití pracovního postupu  
  
## <a name="discussion"></a>Diskuse  
 V první části ukázky je služba pracovního postupu zjistitelná pomocí konfigurace. Konfiguraci lze také použít k použití služby odpovídajícím způsobem s vlastní metadata (například obory). Na straně klienta ukázka používá vlastní kód aktivity, která používá Zjišťování k vyhledání služby odpovídající konkrétní smlouvy. Aktivita kódu vyvezuje identifikátor URI, který je později používán aktivitou odesílání.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Tato ukázka používá koncové body HTTP, které musí mít správné adresy ACL správné adresy URL ke spuštění (podrobnosti naleznete [v tématu Konfigurace protokolu HTTP a HTTPS).](../feature-details/configuring-http-and-https.md) Provedení následujícího příkazu na příkazovém řádku se zvýšenými oprávněními by mělo přidat příslušné akly. Pokud prostředí nerozumí formátu proměnné, nahraďte doménu a uživatelské jméno následujícími argumenty.  
  
     **netsh http přidat urlacl url=http://+:8000/ \\user=%DOMAIN% %UserName%**  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\WorkflowDiscovery`
