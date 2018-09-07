---
title: Vnoření TransactionScope služby
ms.date: 03/30/2017
ms.assetid: e7e1ba64-1384-4eba-add8-415636e2d6d0
ms.openlocfilehash: cf73c0c2d061f1c997a8ade5d7b2bf61887915ca
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44067247"
---
# <a name="nesting-of-transactionscope-within-a-service"></a>Vnoření TransactionScope služby
Tento příklad se skládá z těchto dvou scénářů, která spustí ukazující, jak zpracovat <xref:System.Activities.Statements.TransactionScope> instance aktivity v rámci služby. Nejprve transakce se inicializuje pomocí <xref:System.Activities.Statements.TransactionScope> aktivitu, chcete-li vytvořit novou transakci na straně klienta a <xref:System.ServiceModel.Activities.TransactedReceiveScope> pro příjem a oboru životnost transakce na serveru. První scénář v rámci služby běží sekundární <xref:System.Activities.Statements.TransactionScope> aktivity k předvedení vnořené <xref:System.Activities.Statements.TransactionScope> aktivity v rámci služby. Druhý scénář popisuje, jak jsou dodržovány vypršení časových limitů uvnitř vnořeného <xref:System.Activities.Statements.TransactionScope> aktivity.  
  
## <a name="client-application"></a>Klientská aplikace  
 Klientská aplikace spustí pracovní postup, který se spustí <xref:System.Activities.Statements.TransactionScope> aktivity, vytiskne ID distribuované transakce odešle zprávu do serveru, tok transakce, obdrží odpověď, znovu vytiskne ID distribuované transakce a dokončí. Dělá to jednou pro každý scénář služby.  
  
## <a name="server-application"></a>Serverová aplikace  
 Serverový projekt je hostován v <xref:System.ServiceModel.Activities.WorkflowServiceHost>, která vytvoří koncový bod pro poslech zprávu od klienta. Pracovní postup se jedná o <xref:System.ServiceModel.Activities.TransactedReceiveScope>, který obdrží převedené transakce z klienta, vytiskne ID distribuované transakce a pak spustí sekundy <xref:System.Activities.Statements.TransactionScope> aktivity. Do prvního scénáře je transakce dokončena úspěšně. V druhém scénáři, text <xref:System.Activities.Statements.TransactionScope> aktivita je zpoždění pěti sekund a časový limit pro transakce je nastavena na 2 sekundy. Když transakce vyprší časový limit transakce byla přerušena.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení TransactionServiceExample.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.  
  
3.  Po úspěšném sestavení, klikněte pravým tlačítkem na řešení a vyberte **nastavit projekty po spuštění**. V dialogovém okně vyberte **více projektů po spuštění** a zajistit akci pro oba projekty **Start**.  
  
4.  Stiskněte F5 nebo vyberte **spustit ladění** z **ladění** nabídky. Alternativně můžete stisknutím kláves CTRL + F5 nebo vyberte **spustit bez ladění** z **ladění** nabídky spustit bez ladění.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TRSComposability`
