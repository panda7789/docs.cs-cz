---
title: Doprovodný obor transakcí
ms.date: 03/30/2017
ms.assetid: 37141708-a29f-4b6a-81fe-f8a11f825061
ms.openlocfilehash: fa1da6df5ad5256665610c9b3c2df7d706cef63c
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43536088"
---
# <a name="transaction-convoy-scope"></a>Doprovodný obor transakcí
Tato ukázka předvádí, jak vytvořit paralelní doprovodný zasílání zpráv aktivity vzorce ve spojení s <xref:System.ServiceModel.Activities.TransactedReceiveScope> modelování protokolu, kde počet operací může dojít v libovolném pořadí vše v rámci stejné transakce. Tento příklad také ukazuje, jak <xref:System.ServiceModel.Activities.TransactedReceiveScope> automaticky vytvoří novou transakci, pokud jeden není byly převedeny do serveru, tak klient nepoužívá používat z jakékoli transakce.  
  
 Ukázkový soubor obsahuje dva projekty pracovního postupu, které představují klientem a serverem. Klientský projekt spustí pracovní postup, který začíná odesláním zprávy spustit pracovní postup serveru, která inicializuje korelaci a transakční obor pro zbytek zasílání zpráv aktivity spustí. Klient <xref:System.Activities.Statements.Sequence> aktivita obsahuje počáteční <xref:System.ServiceModel.Activities.Send> a <xref:System.ServiceModel.Activities.ReceiveReply> pár a pak <xref:System.Activities.Statements.Parallel> aktivity tři větví. Každá větev pošle zprávu jednosměrné k serveru. <xref:System.Activities.Statements.Parallel.CompletionCondition%2A> Vlastnost <xref:System.Activities.Statements.Parallel> aktivity je nastavený na `false` tak, aby všechny tři větve dokončit.  
  
 Pracovní postup serveru je podobný klienta pracovní postup s tím rozdílem, zasílání zpráv aktivity je zaměřen na komunikace na straně serveru a jsou obsaženy v rámci <xref:System.ServiceModel.Activities.TransactedReceiveScope> aktivitu tak, aby všechny pracovní Hotovo provede v rámci stejné transakce. První zpráva odeslaná na serveru, transakce je vytvořen a je k okolí rozsahu <xref:System.ServiceModel.Activities.TransactedReceiveScope> textu, aby všechny aktivity v rámci tohoto oboru transakce přístup. Potom všechny obdrží paralelně spustit. Všechny obdrží musí provést pouze jednou, jak je uvedeno ve stavu dokončení na paralelní aktivity. Na implicitní trvalost bod existuje na konci <xref:System.ServiceModel.Activities.TransactedReceiveScope> textu a operace trvalosti je také spuštěn v rámci stejné transakce.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Pomocí [!INCLUDE[vs2010](../../../../includes/vs2010-md.md)], otevřete soubor řešení ParallelConvoySample.sln.  
  
2.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
3.  Ujistěte se, že oba projekty jsou nastavené na spuštění.  
  
    1.  V **Průzkumníka řešení**, klikněte pravým tlačítkem na řešení a vyberte **nastavit projekty po spuštění**.  
  
    2.  Vyberte **více projektů po spuštění** a zkontrolujte akci pro oba projekty je nastavená na **Start**.  
  
4.  Abyste mohli spustit řešení, stiskněte CTRL + F5.  
  
     Vytiskne server `Server is running`, který označuje server připravený.  
  
     Stisknutím jakékoli klávesy v okně konzoly klienta ke spuštění ukázky.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WF\Scenario\Transactions\TransactedConvoyScope`