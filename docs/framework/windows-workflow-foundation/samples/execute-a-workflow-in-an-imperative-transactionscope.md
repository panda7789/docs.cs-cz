---
title: "Pracovní postup provést v imperativní TransactionScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 530a590931a1cb3994406e5605f8da2853ceddaf
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a>Pracovní postup provést v imperativní TransactionScope
Tento příklad ukazuje postup spuštění pracovního postupu pomocí <xref:System.Activities.WorkflowInvoker> pod <xref:System.Transactions.Transaction> z imperativní kód C#.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V imperativní C# kódu <xref:System.Transactions.TransactionScope> se používá k zapouzdření sadu práci, kterou provádí ve stejné transakci. <xref:System.Transactions.TransactionScope> Funguje tak, že vytváření vedlejším transakce a inicializace <xref:System.Transactions.Transaction.Current%2A> vlastnosti, která lze přistupovat pomocí veškerou práci vykonáván v daném vláknu.  
  
 Ekvivalentní chování pracovního postupu získáte musí provést další práci při inicializaci modulu runtime <xref:System.Transactions.Transaction.Current%2A> před provedením každou aktivitu, protože pracovní postup nespravuje spřažení podprocesu mezi aktivitami. Tato podpora runtime jejich výsledné chování je, že při spouštění pracovního postupu s <xref:System.Activities.WorkflowInvoker> uvnitř <xref:System.Transactions.TransactionScope>, je zaručeno, že všechny aktivity spustit v kontextu vedlejším transakce vytvořené <xref:System.Transactions.TransactionScope>.  
  
 Pracovní postup může mít pouze jeden vedlejším transakci pro každou instanci pracovního postupu; vnořené transakce nejsou k dispozici. I když pracovní postup obsahuje <xref:System.Activities.Statements.TransactionScope> aktivity, to nevytvoří novou vnitřní transakci. Místo toho vedlejším transakce, která byla vytvořena mimo pracovní postup znovu použije.  
  
 Ukázka začíná nový <xref:System.Transactions.TransactionScope>, vytiskne ID transakce a začne pracovního postupu pomocí <xref:System.Activities.WorkflowInvoker>. Pracovní postup vytiskne transakce ID znovu zobrazující to je stejné transakci a pak spustí <xref:System.Activities.Statements.TransactionScope>, potom dokončí. <xref:System.Activities.WorkflowInvoker.Invoke%2A> Volání na <xref:System.Activities.WorkflowInvoker> je synchronní, takže původní vlákno zablokuje, dokud dokončení pracovního postupu. Po dokončení pracovního postupu transakce je dokončena a uvolnění prostředků.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení ImperativeTransactionSample.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Pokud chcete spustit řešení, stisknutím klávesy F5.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`