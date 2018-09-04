---
title: Spuštění pracovního postupu v Imperativním oboru
ms.date: 03/30/2017
ms.assetid: bd0e8686-c1d0-4400-a541-da94ed03afc7
ms.openlocfilehash: 2744434e807664ca93b4f5bc27a1f3b89716ce87
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520167"
---
# <a name="execute-a-workflow-in-an-imperative-transactionscope"></a>Spuštění pracovního postupu v Imperativním oboru
Tento příklad ukazuje, jak spustit pracovní postup pomocí <xref:System.Activities.WorkflowInvoker> v části <xref:System.Transactions.Transaction> z imperativního kódu jazyka C#.  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V imperativního kódu jazyka C# <xref:System.Transactions.TransactionScope> se používá k zapouzdření sadu práci, která se spustí v rámci stejné transakce. <xref:System.Transactions.TransactionScope> Funguje tak, že okolí transakce vytváření a inicializaci <xref:System.Transactions.Transaction.Current%2A> vlastnost, která lze poté přistupovat pomocí veškerou práci provádí v daném vláknu.  
  
 Získat ekvivalentního chování v pracovním postupu, musí provést nadbytečné práci spojené se inicializuje modul runtime <xref:System.Transactions.Transaction.Current%2A> před spuštěním každé aktivity, protože pracovní postup nespravuje spřažení vláken mezi aktivitami. Díky této podpoře modulu runtime výsledné chování je, že při provádění pracovního postupu s <xref:System.Activities.WorkflowInvoker> uvnitř <xref:System.Transactions.TransactionScope>, všechny aktivity se zaručeně spustí v kontextu transakci okolí Autor <xref:System.Transactions.TransactionScope>.  
  
 Pracovní postup může mít pouze jedné okolí transakce pro každou instanci pracovního postupu; vnořené transakce nejsou k dispozici. I v případě, pracovní postup obsahuje <xref:System.Activities.Statements.TransactionScope> aktivity, nevytvoří novou vnitřní transakci. Místo toho okolí transakce, který byl vytvořen mimo pracovní postup opakovaně používá.  
  
 Ukázka začíná nové <xref:System.Transactions.TransactionScope>, vytiskne ID transakce a začne pracovního postupu pomocí <xref:System.Activities.WorkflowInvoker>. Pracovní postup vytiskne transakce ID znovu, zobrazuje, že je stejné transakce, pak spustí <xref:System.Activities.Statements.TransactionScope>, pak dokončí. <xref:System.Activities.WorkflowInvoker.Invoke%2A> Volat <xref:System.Activities.WorkflowInvoker> je synchronní, takže původní vlákno blokuje, dokud dokončení pracovního postupu. Po dokončení pracovního postupu je transakce dokončena a uvolnění prostředků.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení ImperativeTransactionSample.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Abyste mohli spustit řešení, stiskněte klávesu F5.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\ImperativeTransaction`