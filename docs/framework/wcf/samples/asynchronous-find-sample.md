---
title: Ukázka asynchronního hledání
ms.date: 03/30/2017
ms.assetid: 7a713a25-c1f4-42e1-8c4a-93d64ca45a3b
ms.openlocfilehash: 37edcb4d1f04eb56d3f24ca3acc3543d7f9696f5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43424388"
---
# <a name="asynchronous-find-sample"></a>Ukázka asynchronního hledání
Tento příklad ukazuje způsob použití operace asynchronního hledání z klientské aplikace.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 Výhodou po tomto vzoru návrhu je, že klient obdrží oznámení asynchronně koncových bodů umístěný jako výsledek požadavku hledání. Pokud chcete zobrazit, jak to funguje, otevřete soubor Client.cs. Poznámka: <xref:System.ServiceModel.Discovery.DiscoveryClient> objekt má dva delegáty připojené k jeho obslužné rutiny událostí. Jeden delegáta je volána, když <xref:System.ServiceModel.Discovery.DiscoveryClient.FindCompleted> událost se vyvolá, a druhé je volána pokaždé, když <xref:System.ServiceModel.Discovery.DiscoveryClient.FindProgressChanged> událost se vyvolá. Tato ukázka vysvětluje, jak tento vzor můžete využít ve vaší aplikaci.  
  
> [!NOTE]
>  Tato ukázka používá koncové body HTTP a spustit, musí být přidán správné seznamy ACL adresy URL. Další informace najdete v tématu [konfigurace HTTP a HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md). Provádění se zvýšenými oprávněními následující příkaz by měl přidat příslušné seznamy ACL. Můžete se k nahrazení domény a uživatelské jméno pro následující argumenty, pokud příkaz nefunguje, jak je. `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete AsyncFind.sln.  
  
2.  Stiskněte kombinaci kláves CTRL + SHIFT + B, abyste mohli sestavit řešení.  
  
3.  Otevřít [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] příkazový řádek a přejděte do adresáře \WCF\Basic\Discovery\AsyncFind\CS\service\bin\Debug nebo \WCF\Basic\Discovery\AsyncFind\VB\service\bin\Debug a spustit Service.exe.  
  
4.  Po spuštění služby, přejděte do \WCF\Basic\Discovery\AsyncFind\CS\client\bin\Debug nebo WCF\Basic\Discovery\AsyncFind\VB\client\bin\Debug adresáře a spusťte Client.exe.  
  
5.  Podívejte se, že klient moci vyhledat a volání služby.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\AsyncFind`  
  
## <a name="see-also"></a>Viz také
