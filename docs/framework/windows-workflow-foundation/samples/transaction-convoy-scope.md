---
title: Oboru Convoy transakce
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 37141708-a29f-4b6a-81fe-f8a11f825061
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: b5fc8834fb72163a615633d81232e25768683278
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="transaction-convoy-scope"></a>Oboru Convoy transakce
Tento příklad ukazuje, jak vytvořit paralelní Convoy zasílání zpráv vzor aktivity ve spojení s <xref:System.ServiceModel.Activities.TransactedReceiveScope> pro modelování protokol, kde několik operací, může dojít v libovolném pořadí všechny ve stejné transakci. Tento příklad také ukazuje, jak <xref:System.ServiceModel.Activities.TransactedReceiveScope> automaticky vytvoří novou transakci, pokud jeden není předávány na server, tak klient neprovede použití jakékoli transakce.  
  
 Ukázkový soubor obsahuje dva projekty pracovního postupu, které představují klientem a serverem. Projektu klienta se spustí pracovní postup, který začíná odesláním zprávy k navázání připojení serveru pracovního postupu, která inicializuje korelaci a spustí transakční obor pro zbytek aktivity zasílání zpráv. Klient <xref:System.Activities.Statements.Sequence> aktivity obsahuje počáteční <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> pár a potom <xref:System.Activities.Statements.Parallel> aktivitu tři větve. U každé větve odešle zprávu jednosměrný k serveru. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> Vlastnost <xref:System.Activities.Statements.Parallel> aktivity je nastavený na `false` tak, aby všechny tři větve dokončit.  
  
 Pracovní postup serveru je podobná klienta pracovního postupu, s výjimkou zasílání zpráv aktivity jsou orientované směrem komunikace na straně serveru a jsou obsaženy v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivity tak, aby všechny pracovat done provede ve stejné transakci. První zpráva odeslaná na server, transakce se vytvoří a přišla vedlejším rozsahu <xref:System.ServiceModel.Activities.TransactedReceiveScope> body, aby všechny aktivity v rámci tohoto rozsahu přístup transakce. Potom všechny obdrží provést paralelně. Všechny obdrží musí provést pouze jednou, jak je popsáno podmínka dokončení na paralelní aktivity. Bod implicitní trvalost existuje na konci <xref:System.ServiceModel.Activities.TransactedReceiveScope> textu a operace trvalost je také provést v rámci stejné transakci.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení ParallelConvoySample.sln.  
  
2.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
3.  Zajistěte, aby že oba projekty jsou nastaveny na spustit.  
  
    1.  V **Průzkumníku řešení**, klikněte pravým tlačítkem na řešení a vyberte **nastavit projekty po spuštění**.  
  
    2.  Vyberte **více projektů po spuštění** a zkontrolujte akci pro oba projekty je nastavená na **spustit**.  
  
4.  Chcete-li spustit řešení, stiskněte CTRL + F5.  
  
     Server výtisků `Server is running`, což naznačuje server je připraven.  
  
     Stisknutím libovolné klávesy v okně konzoly klienta ke spuštění ukázky.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedConvoyScope`  
  
## <a name="see-also"></a>Viz také
