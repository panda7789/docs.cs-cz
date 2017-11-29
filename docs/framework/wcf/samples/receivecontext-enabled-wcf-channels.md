---
title: "Kanály WCF povolenou třídou ReceiveContext"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d990d119-7321-4b8c-852b-10256f59f9b0
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ec3b161ec9dedc2cbf389d8ec5ac4629cf54e007
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="receivecontext-enabled-wcf-channels"></a>Kanály WCF povolenou třídou ReceiveContext
Tento příklad znázorňuje užitečnost <xref:System.ServiceModel.Channels.ReceiveContext>-Povolit kanály WCF. Ukázka implementuje služby Vrátí součin dvou čísel pomocí NetMSMQ kanál.  
  
 <xref:System.ServiceModel.Channels.ReceiveContext> Třída umožňuje aplikaci rozhodnout, jestli se má přístup ke zprávě, nebo nechte ve frontě pro další zpracování, i když obsah zprávy být zkontrolovány. V této ukázce klient odešle náhodných celá čísla do transakční fronty. `ProductCalculator` Služba přijímá zprávy a zkontroluje, zda obsahuje obsah zprávy, které jsou celá čísla, chcete-li zjistit, jestli je možné vypočítat produktu. Pokud operace služby nepočítá produktu, zpráva se vrátit zpět do fronty a lze znovu přijímat pomocí služby naslouchá na fronty.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí):  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři:  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Binding\Net\MSMQ\ReceiveContextProductGenerator`  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  Zkontrolujte, zda je nainstalovaný Microsoft služby Řízení front zpráv (MSMQ).  
  
    1.  Chcete-li nainstalujte službu MSMQ na [!INCLUDE[lserver](../../../../includes/lserver-md.md)]:  
  
        1.  V **správce serveru**, klikněte na tlačítko **funkce**.  
  
        2.  V pravém podokně v části **Souhrn funkcí**, klikněte na tlačítko **přidat funkce**.  
  
        3.  V okně výsledné rozbalte **služby Řízení front zpráv**.  
  
        4.  Rozbalte položku **služby Řízení front zpráv**.  
  
        5.  Klikněte na tlačítko **Integrace adresářové služby** (pro počítače připojené k doméně) a potom klikněte na **podpora protokolu HTTP**.  
  
        6.  Klikněte na tlačítko **Další**a potom klikněte na **nainstalovat**.  
  
    2.  Chcete-li nainstalujte službu MSMQ na [!INCLUDE[wv](../../../../includes/wv-md.md)]:  
  
        1.  Otevřete **ovládací panely**.  
  
        2.  Klikněte na tlačítko **programy** a pak v části **programy a funkce**, klikněte na tlačítko **zapnout nebo vypnout funkce systému Windows**.  
  
        3.  Rozbalte položku **Server Microsoft Message Queue (MSMQ)**, rozbalte položku **jádra serveru Microsoft Message Queue (MSMQ)**a pak zaškrtněte políčka pro následující funkce služby Řízení front zpráv k instalaci:  
  
            -   Server služby Řízení front zpráv  
  
            -   Active Directory Domain Services integrována (pro počítače připojené k doméně)  
  
            -   Podpora protokolu HTTP služby MSMQ  
  
        4.  Click **OK**.  
  
        5.  Pokud se zobrazí výzva k restartování počítače, klikněte na tlačítko **OK** k dokončení instalace.  
  
2.  Ujistěte se, že [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] je nainstalován v počítači.  
  
3.  Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete soubor řešení ReceiveContextProductGenerator.sln.  
  
4.  Sestavte řešení, stiskněte CTRL + SHIFT + B.  
  
5.  Chcete-li spustit řešení, stiskněte CTRL + F5.
