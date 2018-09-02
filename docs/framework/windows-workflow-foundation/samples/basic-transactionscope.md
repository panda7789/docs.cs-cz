---
title: Základní TransactionScope
ms.date: 03/30/2017
ms.assetid: 1e22b76a-76de-43b4-9be7-7a86ed3d5a44
ms.openlocfilehash: b3c673040d40ca91d8ab4a79e847d61e6f507ed1
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43415420"
---
# <a name="basic-transactionscope"></a>Základní TransactionScope
Tento příklad se skládá ze čtyř scénáře, která spustí ukazující, jak vnořit <xref:System.Activities.Statements.TransactionScope> instancí. První scénář popisuje, vnoření 3. stran aktivitu z nich má autor žádné informace o procesu vytváření. Druhý a třetí scénáře ukazují, jak jsou dodržovány vypršení časových limitů a finální scénář ukazuje <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> nastavení.  
  
## <a name="nesting-of-transactionscopeactivity"></a>Vnoření aktivity typu TransactionScopeActivity  
 Pracovní postup pro první scénář se skládá z pořadí dvou <xref:System.Activities.Statements.WriteLine> aktivity a <xref:System.Activities.Statements.TransactionScope>. Text <xref:System.Activities.Statements.TransactionScope> je posloupnost ještě dva <xref:System.Activities.Statements.WriteLine> aktivity, vlastní aktivitu, která vytiskne místní identifikátor transakce a třetí strany aktivity. Aktivity třetích stran `TransactionScopeTest` obsahuje <xref:System.Activities.Statements.TransactionScope> i vědět, když autor pracovního postupu. Tento scénář znázorňuje, že <xref:System.Activities.Statements.TransactionScope> aktivity mohou být vnořené.  
  
## <a name="time-outs"></a>Časové limity  
 Pracovní postup pro druhý scénář je téměř shodná s první. `TransactionScopeTest` Bylo nahrazeno tématem <xref:System.Activities.Statements.TransactionScope>. Text <xref:System.Activities.Statements.TransactionScope> pěti sekund zpoždění a časový limit pro transakce je nastavena na 2 sekundy. Časový limit pro vnější <xref:System.Activities.Statements.TransactionScope> nastaven na 10 sekund. Všimněte si, že je dodržena nejmenší vypršení časového limitu v oboru a transakce vyprší časový limit.  
  
 Pracovní postup pro třetí scénář je téměř shodná se scénářem 2. Aktivitě delay přesunula z textu vnitřního <xref:System.Activities.Statements.TransactionScope> ihned po jeho v sekvenci, který je tělo vnější <xref:System.Activities.Statements.TransactionScope>. Transakce jsou stále vyprší časový limit, ale protože dvě druhý časový limit vnitřní <xref:System.Activities.Statements.TransactionScope> už neplatí. Transakce vyprší za 10 sekund po vnější <xref:System.Activities.Statements.TransactionScope> dojde k překročení časového limitu.  
  
## <a name="aborting-on-transaction-failure"></a>Přerušuje se při selhání transakce  
 Tento pracovní postup je podobný scénáři tři, s tím rozdílem, časové limity byly nahrazeny <xref:System.Activities.Statements.TransactionScope.AbortInstanceOnTransactionFailure%2A> vlastnost. Všimněte si, že příznaky všechny vnitřní podřízené položky, pokud nastavení, musí odpovídat vnější <xref:System.Activities.Statements.TransactionScope>. V tomto scénáři nejsou a je vyvolána výjimka, jestliže se otevře pracovní postup.  
  
#### <a name="to-run-the-sample"></a>Chcete-li spustit ukázku  
  
1.  Otevřete řešení BasicTransactionScopeSample.sln v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)].  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B nebo vyberte **sestavit řešení** z **sestavení** nabídky.  
  
3.  Po sestavení byla úspěšná, stiskněte klávesu F5 nebo vyberte **spustit ladění** z **ladění** nabídky. Případně můžete stisknutím kláves CTRL + F5 nebo vyberte **spustit bez ladění** z **ladění** nabídky spustit bez ladění.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Basic\Transactions\BasicTransactionScope`