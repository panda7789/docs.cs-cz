---
title: "Trasování a protokolování zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
caps.latest.revision: "53"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: d37e050933f0f94a74fcabe3afe007ad2333d58a
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="tracing-and-message-logging"></a>Trasování a protokolování zpráv
Tento příklad znázorňuje postup povolení trasování a protokolování zpráv. Výsledné trasování a protokolů zpráv jsou zobrazit pomocí [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  V postupu a sestavení pokynech k instalaci této ukázce jsou umístěné na konci tohoto tématu.  
  
## <a name="tracing"></a>Trasování  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]používá mechanismus trasování definovaný v <xref:System.Diagnostics> oboru názvů. V tomto modelu trasování dat trasování je produkovaný trasování zdrojů, které implementují aplikace. Každý zdroj je identifikována názvem. Trasování uživatelé vytváří trasování – moduly naslouchání pro trasování zdrojů, pro které se chcete získat informace. Pro příjem dat trasování, je nutné vytvořit naslouchací proces pro zdroj trasování. V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], tento krok můžete provést přidáním následující kód do buď služby nebo klienta konfigurační soubor nastavením zdroj trasování modelu služby `switchValue`:  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-service.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>  
```  
  
 Další informace o trasování zdrojů, najdete v části Zdroj trasování v [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tématu.  
  
## <a name="activity-tracing-and-propagation"></a>Trasování aktivit a šíření  
 S `ActivityTracing` povolená a `propagateActivity` nastavena na `true` v `system.ServiceModel` zdroje trasování pro klienta a služby poskytovat korelace trasování v rámci logické jednotky zpracování (aktivity), mezi aktivity v rámci (koncové body prostřednictvím přenosu aktivity) a napříč aktivity pokrývání uzlů několik koncových bodů (prostřednictvím šíření ID aktivity).  
  
 Tyto tři mechanismy (aktivit, přenosy a šíření) můžete najít další rychle pomocí nástroje prohlížeče trasování služeb hlavní příčinu chyby. Další informace najdete v tématu [pomocí prohlížeče trasování služeb pro zobrazení korelační trasování a Poradce při potížích s](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Je možné rozšířit trasování ServiceModel od tak, že vytvoříte vlastní aktivitu trasování. Trasování aktivit uživatelem definované umožňuje uživateli vytvořit trasování aktivity:  
  
-   Skupiny trasování do logické jednotky práce.  
  
-   Korelovat aktivity prostřednictvím přenosů a šíření.  
  
-   Snížit náklady na výkon [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] trasování (například disk místo náklady souboru protokolu).  
  
 Další informace o trasování aktivity definovaný uživatelem, najdete v tématu [rozšíření trasování](../../../../docs/framework/wcf/samples/extending-tracing.md) ukázka.  
  
## <a name="message-logging"></a>Protokolování zpráv  
 Protokolování zpráv se dá nastavit klienta a služby všech [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace. Pokud chcete povolit protokolování zpráv, musíte přidat následující kód u klienta nebo služby:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels >  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 Když se zaznamená zprávu, typ trasování, závisí na tom, jestli jsou trasovány na klienta nebo serveru. Například zprávu "Přidat", které je odesláno klienta trasovaný v kategorii "TransportWrite" na straně klienta, zatímco stejnou zprávu trasovaný v kategorii "TransportRead" na službu.  
  
 Nakonfigurovat naslouchací proces trasování přidáním následující kód, který <xref:System.Diagnostics> části souboru App.config klienta nebo v souboru Web.config služby:  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Information,ActivityTracing"  
        propagateActivity="true">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
      <source name="System.ServiceModel.MessageLogging">  
        <listeners>  
          <add name="xml" />  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add initializeData="C:\logs\TracingAndLogging-client.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" />  
    </sharedListeners>  
    <trace autoflush="true" />  
  </system.diagnostics>  
```  
  
 Zprávy jsou protokolovány ve formátu XML v cílovém adresáři zadaný v konfiguračním souboru.  
  
> [!NOTE]
>  Trasovací soubory nejsou vytvořeny bez původně vytvoření adresář protokolu. Ujistěte se, že existuje adresář C:\logs\ nebo zadejte alternativní protokolování adresář v konfiguraci naslouchacího procesu. Postupujte podle pokynů počáteční nastavení na konci tohoto dokumentu pro další informace.  
  
 Další informace o protokolování zpráv najdete v tématu [konfigurace protokolování zpráv](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tématu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Před spuštěním ukázky trasování a protokolování zpráv, vytvořte adresář C:\logs\ pro službu zápis .svclog soubory. Název tohoto adresáře je definována v konfiguračním souboru jako cestu pro trasování a zprávy, která je zaznamenána a lze změnit. Poskytněte uživatel oprávnění k zápisu síťová služba k adresáři s protokoly.  
  
3.  Sestavení C#, C++ nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
