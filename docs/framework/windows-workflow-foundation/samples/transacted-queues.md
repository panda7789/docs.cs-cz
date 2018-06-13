---
title: Zpracované fronty
ms.date: 03/30/2017
ms.assetid: b1b011dd-5e0b-482c-9bb0-9d8727038f14
ms.openlocfilehash: b125158a113079d87eb6926393d5a2b5fe326824
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33519678"
---
# <a name="transacted-queues"></a>Zpracované fronty
Tento příklad ukazuje, jak integrovat front a transakce ve Windows Workflow Foundation (WF) k vytvoření služby spolehlivou a škálovatelnou. A <!--zz <xref:System.Activities.TransactionScope>--> `System.Activities.TransactionScope` se v pracovním postupu klienta používá k odeslání zprávy do fronty v transakci pomocí <xref:System.ServiceModel.NetMsmqBinding>. A <xref:System.ServiceModel.Activities.TransactedReceiveScope> se používá na serveru pro příjem zpráv z fronty a aktualizovat stav pracovního postupu ve stejné transakci.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.Activities.Statements.TransactionScope>, <xref:System.ServiceModel.Activities.TransactedReceiveScope>, <xref:System.ServiceModel.NetMsmqBinding>, <xref:System.ServiceModel.Activities.Receive>a na základě obsahu korelace.  
  
## <a name="discussion"></a>Diskusní  
 K předvedení funkcí zahrnuté v této ukázce `RewardsPoints` vytvoření služby pracovního postupu, která uchovává informace o body vytvořené a použít pro daný účet. Klient použije <xref:System.Activities.WorkflowInvoker> k simulaci publikování různé požadavky do fronty. Vytvořit zprávu do fronty v rámci transakce, <xref:System.ServiceModel.Activities.Send> aktivity může být umístěna uvnitř <xref:System.Activities.Statements.TransactionScope.Body%2A> z <xref:System.Activities.Statements.TransactionScope>. V této ukázce klient spouští první, za nímž následuje serveru, a ukazují, jak ve frontě zpráv můžete oddělit klientské a serverové aplikace.  
  
 Po dokončení klienta služby je nakonfigurovaná a je hostovaná. Jakmile se otevře, začne zpracování zprávy, které již byly umístěny do fronty. Každou zprávu přijme a zpracuje ve stejné transakci serveru. V této ukázce je první přijaté zprávy `CreateAccount` požadavek, který vytvoří instanci a inicializuje obsahu korelace na základě názvu účtu předanou v rámci zprávu požadavku. Modelování druh služby by se dalo očekávat v reálném světě se následující dva <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity, které zpracovávají `AddPoints` a `UsePoints` zpráv ukládány do paralelních větvích v rámci `while` cykly, aby se mohl zpracovávat tyto zprávy opakovaně v libovolném pořadí.  
  
 <xref:System.Activities.Statements.TransactionScope> a <xref:System.ServiceModel.Activities.TransactedReceiveScope> mají bod implicitní trvalost na konci jejich obory, takže pomocí těchto aktivit v [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v kombinaci s front je spolehlivý způsob, jak přesunout z jeden konzistentní stav pracovní postup na další, a zajistit, aby se zprávy nikdy ztratit.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Instalace a konfigurace služby MSMQ. V tématu [instalaci služby Řízení front zpráv](http://go.microsoft.com/fwlink/?LinkId=178526) podrobnosti.  
  
2.  Ujistěte se, zda je spuštěna služba MSDTC spuštěním následujícího příkazu na příkazovém řádku. `net start msdtc`  
  
3.  Kompilace projektu a otevřete spustitelný soubor nebo otevřete projekt ve [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a vyberte možnost spustit z nabídky ladění. Nejprve je vytvářena fronta, pak klient spustí a odešle zprávy do fronty a nakonec spuštění služby a zpracování zprávy. Chcete-li program ukončit, stiskněte klávesu ENTER.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedQueues`
