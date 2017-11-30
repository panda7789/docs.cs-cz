---
title: "Základní TransactionScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1e22b76a-76de-43b4-9be7-7a86ed3d5a44
caps.latest.revision: "13"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d4f9d9e966a0a6d8fa48d195b17438b3d78b32a9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="basic-transactionscope"></a>Základní TransactionScope
Tato ukázka se skládá ze čtyř scénářů, spusťte znázorňující vnořit <xref:System.Activities.Statements.TransactionScope> instance. První scénář ukazuje vnoření aktivitu 3. stran, které autor nemá žádné informace o konstrukce. Druhý a třetí scénáře ukazují, jak jsou dodržovány vypršení časových limitů a poslední scénář ukazuje <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> nastavení.  
  
## <a name="nesting-of-transactionscopeactivity"></a>Vnoření aktivity typu TransactionScopeActivity  
 Pracovní postup pro první scénář se skládá z pořadí dva <xref:System.Activities.Statements.WriteLine> aktivity a <xref:System.Activities.Statements.TransactionScope>. Text <xref:System.Activities.Statements.TransactionScope> je posloupnost dva další <xref:System.Activities.Statements.WriteLine> aktivity, vlastní aktivity, která vytiskne identifikátor místní transakce a třetí strany aktivity. Aktivita třetích stran `TransactionScopeTest` obsahuje <xref:System.Activities.Statements.TransactionScope> i když nemá žádný způsob, jak zjistit Autor pracovního postupu. Tento scénář ukazuje, že <xref:System.Activities.Statements.TransactionScope> aktivity mohou být použity.  
  
## <a name="time-outs"></a>Vypršení časových limitů  
 Pracovní postup pro druhý scénář je téměř shodné s prvním. `TransactionScopeTest` Byla nahrazena <xref:System.Activities.Statements.TransactionScope>. Text <xref:System.Activities.Statements.TransactionScope> zpoždění pěti sekund a časový limit pro transakci je nastavená na dvou sekund. Časový limit pro vnější <xref:System.Activities.Statements.TransactionScope> nastaven na 10 sekund. Upozorňujeme, že je dodržena nejmenší časový limit v oboru a transakce časového limitu.  
  
 Pracovní postup pro třetí scénář je téměř shodná scénář dva. Aktivita zpoždění přesunula z textu vnitřního <xref:System.Activities.Statements.TransactionScope> ihned po jeho v pořadí, který je text vnější <xref:System.Activities.Statements.TransactionScope>. Transakce stále časový limit, ale protože dva druhé časový limit vnitřního <xref:System.Activities.Statements.TransactionScope> už neplatí. Transakce vyprší za 10 sekund při vnější <xref:System.Activities.Statements.TransactionScope> byl překročen časový limit.  
  
## <a name="aborting-on-transaction-failure"></a>Přerušení na selhání transakce  
 Tento pracovní postup je podobný scénář č. 3, s výjimkou byly nahrazeny vypršení časových limitů <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> vlastnost. Všimněte si, že příznaků všechny podřízené objekty vnitřní, pokud nastavení, musí odpovídat vnější <xref:System.Activities.Statements.TransactionScope>. V tomto scénáři Ne a je vyvolána výjimka, když se otevře pracovního postupu.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení BasicTransactionScopeSample.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.  
  
3.  Po sestavení proběhla úspěšně, stiskněte klávesu F5, nebo vyberte **spustit ladění** z **ladění** nabídky. Případně můžete stisknutím kláves CTRL + F5 nebo vybrat **spustit bez ladění** z **ladění** nabídku spustit bez ladění.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\BasicTransactionScope`  
  
## <a name="see-also"></a>Viz také
