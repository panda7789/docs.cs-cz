---
title: "Korelace dotazu LINQ zprávy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b746872e-57b1-4514-b337-53398a0e0deb
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1207f371da5b447903e2846229860fd8c214a46e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="linq-message-query-correlation"></a>Korelace dotazu LINQ zprávy
Tento příklad znázorňuje, jak to provést pomocí vlastní korelace na základě obsahu <xref:System.ServiceModel.Dispatcher.MessageQuery> implementace oproti poskytované systémem <xref:System.ServiceModel.XPathMessageQuery>.  
  
## <a name="demonstrates"></a>Demonstruje  
 Vlastní <xref:System.ServiceModel.Dispatcher.MessageQuery>, korelace na základě obsahu.  
  
## <a name="discussion"></a>Diskusní  
 Tento příklad ukazuje, jak rozšířit z <xref:System.ServiceModel.Dispatcher.MessageQuery> základní třída pro účely korelace. Vlastní implementace `LinqMessageQuery`, umožňuje uživatelům poskytnout XName najít ve zprávě pomocí XLinq. Data načtená v dotazu se používá k korelace klíče k odeslání zprávy a pokuste se k instanci pracovního postupu vhodné.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Tato ukázka zpřístupní služby pracovního postupu pomocí koncových bodů protokolu HTTP. Použít tuto ukázku, správné seznamy ACL adresa URL musí být přidán (viz [konfigurace HTTP a HTTPS](http://go.microsoft.com/fwlink/?LinkId=70353) podrobnosti), spuštění sady Visual Studio jako správce, nebo spuštěním následujícího příkazu řádku se zvýšenými oprávněními přidejte příslušné seznamy ACL. Zajistěte, aby uživatelské jméno a doména jsou nahrazována.  
  
    ```  
    netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%  
    ```  
  
2.  Jakmile se přidají adresy URL seznamy ACL, použijte následující postup.  
  
    1.  Sestavte řešení.  
  
    2.  Pravým tlačítkem myši řešení a výběrem nastavit více projektů spuštění **nastavit projekty po spuštění**. Přidat **služby** a **klienta** (v tomto pořadí) jako více projektů spuštění.  
  
    3.  Spusťte aplikaci. Konzole klienta ukazuje pracovní postup odesílání pořadí a přijetí id pořadí nákupu a následně potvrzení pořadí. Okno služby zobrazí zpracovávaných požadavků.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Services\LinqMessageQueryCorrelation`
