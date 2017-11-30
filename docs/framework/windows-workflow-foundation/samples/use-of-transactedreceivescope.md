---
title: "Použití TransactedReceiveScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d455f1dc-bfc5-43d6-8ae9-bc3b3a3ea08a
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b01352910c52d117d7ab0adcd94320ff9cf6931d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="use-of-transactedreceivescope"></a>Použití TransactedReceiveScope
Tento příklad ukazuje postup toku transakce z klienta na server pomocí <xref:System.Activities.Statements.TransactionScope> vytvořit novou transakci na straně klienta a <xref:System.ServiceModel.Activities.TransactedReceiveScope> přijmout zprávu s sdružení transakcí a obor životnost transakce na serveru. Ukázkový soubor obsahuje dva projekty, které plnění rolí klienta a serveru.  
  
## <a name="client-application"></a>Klientské aplikace  
 Klientská aplikace spustí pracovní postup, který vypíše ID distribuované transakce, odešle zprávu do serveru, tok transakce, obdrží odpověď, znovu vytiskne ID distribuované transakce a dokončení. Pokud je ID distribuované transakce původně výtisků, je prázdný identifikátor GUID, protože transakce je jenom místní.  
  
## <a name="server-application"></a>Aplikace serveru  
 Serverový projekt je podobný, ale pracovní postup je hostován v <xref:System.ServiceModel.Activities.WorkflowServiceHost> protože musí naslouchat na koncový bod pro zprávu od klienta. Pracovní postup se jedná o <xref:System.ServiceModel.Activities.TransactedReceiveScope>, který obdrží sdružení transakcí z klienta, zobrazí zprávu, která byla odeslána, vytiskne ID distribuované transakce a odešle odpověď klientovi. ID distribuované transakce je teď prázdný identifikátor GUID a pokud aktivitu deklaracemi transakce byla přidána do textu <xref:System.ServiceModel.Activities.TransactedReceiveScope>, by provést pod sdružení transakcí.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení TransactedReceiveScope.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.  
  
3.  Po sestavení proběhla úspěšně, klikněte pravým tlačítkem na řešení a vyberte **nastavit projekty po spuštění**. V dialogovém okně vyberte **více projektů po spuštění** a zajistit akci pro oba projekty **spustit**.  
  
4.  Stisknutím klávesy F5 nebo vyberte **spustit ladění** z **ladění** nabídky. Alternativně můžete stisknutím kláves CTRL + F5 nebo vybrat **spustit bez ladění** z **ladění** nabídku spustit bez ladění.  
  
    > [!NOTE]
    >  Server musí být spuštěn před spuštěním klienta. Výstup z okna konzoly, který je hostitelem služby určuje, kdy bylo zahájeno.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\TransactedReceiveScope`  
  
## <a name="see-also"></a>Viz také
