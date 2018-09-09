---
title: Fronty využívající transakce
ms.date: 03/30/2017
ms.assetid: b1b011dd-5e0b-482c-9bb0-9d8727038f14
ms.openlocfilehash: db6a9686334eefb02b9360827a23ca8363127eb5
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44253192"
---
# <a name="transacted-queues"></a>Fronty využívající transakce
Tato ukázka předvádí, jak integrovat fronty a transakce ve Windows Workflow Foundation (WF) k vytváření spolehlivých a škálovatelných služeb. A <!--zz <xref:System.Activities.TransactionScope>--> `System.Activities.TransactionScope` je v pracovním postupu klienta použít k odeslání zprávy do fronty v transakci pomocí <xref:System.ServiceModel.NetMsmqBinding>. A <xref:System.ServiceModel.Activities.TransactedReceiveScope> se používá na serveru pro příjem zpráv z fronty a aktualizaci stavu pracovního postupu v rámci stejné transakce.  
  
## <a name="demonstrates"></a>Demonstruje  
 <xref:System.Activities.Statements.TransactionScope>, <xref:System.ServiceModel.Activities.TransactedReceiveScope>, <xref:System.ServiceModel.NetMsmqBinding>, <xref:System.ServiceModel.Activities.Receive>a korelace na základě obsahu.  
  
## <a name="discussion"></a>Diskuse  
 K předvedení funkcí zahrnuté v této ukázce `RewardsPoints` vytvoření služby pracovního postupu, která uchovává informace o bodech vytvořené a použít pro daný účet. Klient používá <xref:System.Activities.WorkflowInvoker> simulace různých požadavků do fronty pro odesílání. K publikování zpráv do fronty v rámci transakce, <xref:System.ServiceModel.Activities.Send> aktivity mohou být umístěny uvnitř <xref:System.Activities.Statements.TransactionScope.Body%2A> z <xref:System.Activities.Statements.TransactionScope>. V této ukázce, klient spouští první, za nímž následuje serveru tak, aby ukazují, jak ve frontě zpráv můžete oddělit klientské a serverové aplikace.  
  
 Po dokončení klienta služba je nakonfigurovaná a je hostovaná. Jakmile se otevře, začne zpracování zprávy, které již byly umístěny ve frontě. Každou zprávu přijme a zpracuje v rámci stejné transakce serveru. V této ukázce je první přijatá zpráva `CreateAccount` požadavek, který vytvoří instanci a inicializuje obsahu korelace na základě názvu účtu předané jako část zprávy s požadavkem. Modelování typ služby, které by se dalo očekávat v reálném světě se následující dva <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity, které zpracovávají `AddPoints` a `UsePoints` zpráv ukládány do paralelních větví v rámci `while` opakovat tak, aby se může zpracovat tyto zprávy opakovaně v libovolném pořadí.  
  
 <xref:System.Activities.Statements.TransactionScope> a <xref:System.ServiceModel.Activities.TransactedReceiveScope> mají jako implicitní trvalost bod na konci jejich obory, tak pomocí těchto aktivit v [!INCLUDE[wf1](../../../../includes/wf1-md.md)] v kombinaci s frontami je spolehlivý způsob, jak přesunout pracovního postupu z jednoho stavu konzistentní vzhledem k aplikacím na další, přitom zajistit, že jsou zprávy nikdy ztratit.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Instalace a konfigurace služby MSMQ. Zobrazit [instalaci služby Řízení front zpráv](https://go.microsoft.com/fwlink/?LinkId=178526) podrobnosti.  
  
2.  Zkontrolujte, zda je spuštěna služba MSDTC spuštěním následujícího příkazu na příkazovém řádku. `net start msdtc`  
  
3.  Zkompilujte projekt a otevře spustitelný soubor nebo otevřete projekt v [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)] a vyberte možnost spuštění z nabídky ladění. Nejprve se vytvoří frontu, pak běží klientem a odešle zprávy do fronty a nakonec spuštění služby a zprávy zpracuje. Chcete-li ukončit program, stiskněte klávesu ENTER.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedQueues`
