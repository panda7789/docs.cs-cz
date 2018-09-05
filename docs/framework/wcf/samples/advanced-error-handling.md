---
title: Pokročilé zpracování chyb
ms.date: 03/30/2017
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
ms.openlocfilehash: 72fb9885408759f5781501b548f81625d258d13c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745249"
---
# <a name="advanced-error-handling"></a>Pokročilé zpracování chyb
V této ukázce směrovací službou Windows Communication Foundation (WCF). Směrovací služba je komponenta WCF, který umožňuje snadno do aplikace zahrnout směrovač založené na obsahu. Tato ukázka předvádí, jak služba Směrování inteligentně obnoví z chyb, transakce a dalších složitější zasílání zpráv konceptů, jako jsou vícesměrové vysílání.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno na svém počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a>Ukázka podrobnosti  
 V této ukázce směrovací služba je nakonfigurovaná pro čtení zprávu z fronty MSMQ a služby vícesměrového vysílání tuto zprávu do dvou seznamů, front. Jeden seznam se používá pro fronty služby a jiné se používá pro fronty protokolování.  
  
 Proto, že ve výchozím nastavení, MSMQ vazby, který služba Směrování nakonfigurované na použití podporuje použití transakcí, směrovací služba zajišťuje, že je zpráva transakční a alespoň jednu frontu v každém seznamu přijatých před odesílajících sestavy do vstupní fronty ( `InQ`), který byl úspěšně směrovat zprávy. Proto v případě, kdy nejsou k dispozici obě služby front nebo obě z fronty protokolování, směrovací službou hlásí, že zprávu nejde směrovat, a vstupní fronty by provedlo určitou akci. Tato akce se skládá z přesun zprávy do fronty nedoručených zpráv systému.  
  
#### <a name="to-use-this-sample"></a>Pro fungování této ukázky  
  
1.  > [!IMPORTANT]
    >  Nainstalujte službu MSMQ před spuštěním této ukázky. Pokud služba MSMQ nainstalovaná není, vrátí se zprávou výjimky při spuštění ukázky. Najdete pokyny k instalaci služby MSMQ v [instalace řízení front zpráv (MSMQ)](https://go.microsoft.com/fwlink/?LinkId=166437).  
  
     Pomocí [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)], otevřete AdvancedErrorHandling.sln.  
  
2.  Stisknutím klávesy **F5** nebo **CTRL + SHIFT + B** v sadě Visual Studio.  
  
    1.  Pokud vytvoříte aplikaci pomocí kombinace kláves CTRL + SHIFT + B, je nutné spustit aplikaci na. / RoutingService/bin/debug/RoutingService.exe.  
  
3.  V okně konzoly stiskněte klávesu ENTER pro spuštění klienta.  
  
4.  Klient odešle různé statistické údaje o front pro každý případ.  
  
    1.  Následuje výstupu vráceného pro případ 1 (bez chyb).  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  Následuje výstupu vráceného pro případ 3 (primární služby a protokolování chyb fronty).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  Následuje výstupu vráceného pro případ 4 (primární služba fronty a frontu selhání primárního a záložního protokolování).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  Následuje výstupu vráceného pro případ 2 (Chyba fronty primární služby).  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a>Konfigurovat pomocí kódu nebo souboru App.config  
 Ukázka lodí umožňují definovat chování ve směrovači použít soubor App.config. Můžete také změnit název souboru RoutingService\App.config na jiný tak, aby nebyl rozpoznán a změňte hodnotu `configDriven` pole RoutingService\Program.cs k `false` použití konfigurace definované v kódu. Některé z metod má za následek stejné chování směrovače.  
  
### <a name="scenario"></a>Scénář  
 Tento příklad ukazuje, že služba směrování můžete zpracovat možnosti zasílání zpráv, jako je například transakce kontextu přijetí a, můžete využít tyto možnosti jako součást správné zpracování chybových scénářů.  
  
### <a name="real-world-scenario"></a>Reálné scénáře  
 Contoso chce využívat transakční obdrží prostřednictvím službě Směrování a ujistěte se, že všechny nezbytné služby dostávat informace i během chybové stavy. Kromě toho co by rádi chyby zpracovávat správně a automaticky a selhání, aby oznámený v případě, že zpráva se doručit, i když se používá logiku zpracování chyb. Pro tento účel konfigurace služby směrování služby převzít služby při selhání ke konkrétním koncovým bodům podle očekávání a směrovací služba zpracovává chybové situace, což zahrnuje vytváření, dokončení a vrácení zpět nebo přerušením transakce přijímání kontextů jako nezbytné.  
  
## <a name="see-also"></a>Viz také  
 [Hostování AppFabric a ukázky trvalosti](https://go.microsoft.com/fwlink/?LinkId=193961)
