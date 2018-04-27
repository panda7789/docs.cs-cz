---
title: Pokročilé zpracování chyb
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
caps.latest.revision: 21
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 35911a80e7686a1023f42115f785fb64d949aeff
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="advanced-error-handling"></a>Pokročilé zpracování chyb
Tento příklad ukazuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] směrování služby. Služba směrování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] komponenty, která usnadňuje do aplikace zahrnout směrovač podle obsahu. Tento příklad ukazuje, jak službu Směrování inteligentně zotavení z chyb, s použitím transakce a jiné složitější zasílání zpráv koncepty, jako je například vícesměrového vysílání.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalována na váš počítač. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V této ukázce je nakonfigurovaná služba Směrování ke čtení zprávy ze služby MSMQ fronty a vícesměrové vysílání tuto zprávu na dva seznamy front. Jeden seznam se používá pro fronty služby service a jiné pro protokolování fronty.  
  
 Protože ve výchozím nastavení, MSMQ vazby, který služba Směrování nakonfigurován na použití podporuje použití transakcí, vytvoří se, že je zpráva transakcí a přijaté podle alespoň jedna fronta v každém seznamu před zprávy (příchozí fronty směrovací službou `InQ`), byl úspěšně směrovat zprávy. Proto v případě, kde je k dispozici obě fronty služby service nebo obě fronty protokolování, službu Směrování sestav, že není možné směrovat zprávy a vstupní fronty by měl určitou akci. Tato akce se skládá z přesunu zprávy do fronty nedoručených zpráv systému.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  > [!IMPORTANT]
    >  Nainstalujte službu MSMQ před spuštěním této ukázce. Pokud služby MSMQ není nainstalovaná, vrátí se zprávou výjimky při spuštění ukázky. Pokyny k instalaci služby MSMQ lze najít na [instalaci řízení front zpráv (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437).  
  
     Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete AdvancedErrorHandling.sln.  
  
2.  Stiskněte klávesu **F5** nebo **CTRL + SHIFT + B** v sadě Visual Studio.  
  
    1.  Pokud vytvoříte aplikaci s CTRL + SHIFT + B, je nutné spustit aplikaci na. / RoutingService/bin/debug/RoutingService.exe.  
  
3.  V okně konzoly stiskněte klávesu ENTER pro spuštění klienta.  
  
4.  Klient se vrátí různé statistické údaje o fronty pro každý případ.  
  
    1.  Zde je výstup pro případ 1 (žádný počet selhání).  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  Zde je výstup pro případ 3 (primární služby a protokolování chyb fronty).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  Zde je výstup pro případ 4 (primární služba fronty a fronty selhání primární a záložní protokolování).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  Zde je výstup pro případ 2 (Chyba primární služba fronty).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Konfigurovat pomocí kódu nebo App.config  
 Ukázka lodě, umožňují použít soubor App.config k definování chování směrovače. Můžete také změnit název souboru RoutingService\App.config na jinou tak, aby nebyla rozpoznána a změňte hodnotu `configDriven` pole RoutingService\Program.cs k `false` používat konfigurace definované v kódu. Buď metoda výsledkem stejné chování z směrovači.  
  
### <a name="scenario"></a>Scénář  
 Tento příklad znázorňuje, můžete službu Směrování zpracování rozšířené možnosti zasílání zpráv, jako je například transakce a přijímat kontextu a že ji můžete využít tyto možnosti jako součást správně zpracování chyby scénáře.  
  
### <a name="real-world-scenario"></a>Scénář skutečných  
 Contoso chce využívat transakční obdrží prostřednictvím směrování služby pro zajištění informace i během chybové stavy všechny nezbytné služby. Kromě toho se mu správně a automaticky zpracovávat chyby a selhání, aby byly hlášené v případě, že zprávu nedoručitelných, i když využité zpracování logiky chyb. Pro tento účel je potřeba nakonfigurovat službu směrování k převzetí služeb při selhání ke konkrétním koncovým bodům podle očekávání a služba Směrování zpracovává situacích chyby, který zahrnuje vytváření, dokončení a vrácení zpět nebo ruší se transakce a příjem kontextů jako nezbytné.  
  
## <a name="see-also"></a>Viz také  
 [Ukázky trvalosti a hostování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193961)
