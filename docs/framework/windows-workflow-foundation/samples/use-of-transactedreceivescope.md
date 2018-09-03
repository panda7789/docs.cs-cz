---
title: Použití TransactedReceiveScope
ms.date: 03/30/2017
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
ms.openlocfilehash: bc1c418f3fa116f5e1c1647af3543a38122842f5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/03/2018
ms.locfileid: "43481468"
---
# <a name="use-of-transactedreceivescope"></a>Použití TransactedReceiveScope
Tento příklad ukazuje, jak transakce z klienta na server pomocí <xref:System.Activities.Statements.TransactionScope> vytvořit novou transakci na straně klienta a <xref:System.ServiceModel.Activities.TransactedReceiveScope> a zobrazí se zpráva s sdružení transakcí oboru životnost transakce na serveru. Vzorek se skládá ze dvou projektů, které vyplnit rolí klienta a serveru.  
  
## <a name="client-application"></a>Klientská aplikace  
 Klientská aplikace běží pracovní postup, který vytiskne ID distribuované transakce, odešle zprávu do serveru, tok transakce, obdrží odpověď, znovu vytiskne ID distribuované transakce a dokončí. Pokud ID distribuované transakce je zpočátku zobrazí, je prázdný identifikátor GUID je pouze místní transakce.  
  
## <a name="server-application"></a>Serverová aplikace  
 Serverový projekt je podobné, ale pracovní postup je hostován v <xref:System.ServiceModel.Activities.WorkflowServiceHost> vzhledem k tomu, že musí naslouchat na koncový bod pro zprávu od klienta. Pracovní postup se jedná o <xref:System.ServiceModel.Activities.TransactedReceiveScope>, který obdrží převedené transakce z klienta, vytiskne zprávu, která byla odeslána, vytiskne ID distribuované transakce a odešle odpověď do klienta. ID distribuované transakce je teď prázdný identifikátor GUID a pokud aktivitu s ohledem na transakce byla přidána do těla <xref:System.ServiceModel.Activities.TransactedReceiveScope>, by provést v rámci toku transakce.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení TransactedReceiveScope.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.  
  
3.  Po úspěšném sestavení, klikněte pravým tlačítkem na řešení a vyberte **nastavit projekty po spuštění**. V dialogovém okně vyberte **více projektů po spuštění** a zajistit akci pro oba projekty **Start**.  
  
4.  Stiskněte F5 nebo vyberte **spustit ladění** z **ladění** nabídky. Alternativně můžete stisknutím kláves CTRL + F5 nebo vyberte **spustit bez ladění** z **ladění** nabídky spustit bez ladění.  
  
    > [!NOTE]
    >  Na serveru musí běžet před spuštěním klienta. Výstup z okna konzoly, který je hostitelem služby označuje, kdy byla spuštěna.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`