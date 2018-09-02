---
title: Kanály WCF povolenou třídou ReceiveContext
ms.date: 03/30/2017
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
ms.openlocfilehash: d7f80d0874606129876fbf7dfa30c0327680b922
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43442743"
---
# <a name="receivecontext-enabled-wcf-channels"></a>Kanály WCF povolenou třídou ReceiveContext
V této ukázce užitečnost <xref:System.ServiceModel.Channels.ReceiveContext>-povoleno kanály WCF. Ukázka implementuje službu, která vrátí součin dvou čísel pomocí NetMSMQ kanálu.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> Třída umožňuje aplikaci se rozhodnout, jestli se má přístup ke zprávě, nebo nechat ji ve frontě pro další zpracování, i když byly podrobeny obsah zprávy. V této ukázce klient odešle náhodné celých čísel na transakční frontu. `ProductCalculator` Služba přijímá zprávy a zkontroluje obsah zprávy, které jsou celá čísla, chcete-li zjistit, zda lze vypočítat produktu. Pokud operace služby nepočítá produktu, zpráva se znovu zařadí do fronty a lze znovu přijímat pomocí služby naslouchání ve frontě.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Ujistěte se, že je nainstalovaný Microsoft Message Queuing (MSMQ).  
  
    1.  Chcete-li nainstalovat služby MSMQ v [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:  
  
        1.  V **správce serveru**, klikněte na tlačítko **funkce**.  
  
        2.  V pravém podokně v části **Souhrn funkcí**, klikněte na tlačítko **přidat funkce**.  
  
        3.  V okně výsledný rozbalte **služby Řízení front zpráv**.  
  
        4.  Rozbalte **služba Řízení front zpráv**.  
  
        5.  Klikněte na tlačítko **Integrace adresářové služby** (pro počítače připojené k doméně) a potom klikněte na tlačítko **podpora protokolu HTTP**.  
  
        6.  Klikněte na tlačítko **Další**a potom klikněte na tlačítko **nainstalovat**.  
  
    2.  Chcete-li nainstalovat služby MSMQ v [!INCLUDE[wv](../../../../includes/wv-md.md)]:  
  
        1.  Otevřít **ovládací panely**.  
  
        2.  Klikněte na tlačítko **programy** a pak v části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce Windows**.  
  
        3.  Rozbalte **Server Microsoft Message Queue (MSMQ)**, rozbalte **jádra serveru Microsoft Message Queue (MSMQ)** a poté zaškrtněte políčka pro následující funkce služby Řízení front zpráv k instalaci:  
  
            -   Server služby Řízení front zpráv  
  
            -   MSMQ domény služby integrace služby Active Directory (pro počítače připojené k doméně)  
  
            -   Podpora protokolu HTTP služby MSMQ  
  
        4.  Klikněte na tlačítko **OK**.  
  
        5.  Pokud se zobrazí výzva k restartování počítače, klikněte na tlačítko **OK** k dokončení instalace.  
  
2.  Ujistěte se, že [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] je nainstalován v počítači.  
  
3.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení ReceiveContextProductGenerator.sln.  
  
4.  Abyste mohli sestavit řešení, stiskněte kombinaci kláves CTRL + SHIFT + B.  
  
5.  Abyste mohli spustit řešení, stiskněte CTRL + F5.
