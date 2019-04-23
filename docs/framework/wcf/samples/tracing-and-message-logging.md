---
title: Trasování a protokolování zpráv
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 079decb76b45566f354418d671145f0c284628c7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59322131"
---
# <a name="tracing-and-message-logging"></a>Trasování a protokolování zpráv
Tato ukázka předvádí, jak povolit trasování a protokolování zpráv. Výsledné trasování a protokolování zprávy lze zobrazit pomocí [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Postup a sestavení pokynů pro tuto ukázku se nachází na konci tohoto tématu.  
  
## <a name="tracing"></a>Trasování  
 Windows Communication Foundation (WCF) používá mechanismus trasování, které jsou definovány v <xref:System.Diagnostics> oboru názvů. V tomto modelu trasování je dat trasování vyprodukované zdroji trasování, které implementují aplikace. Každý zdroj je identifikována názvem. Trasování uživatelé vytváří naslouchacích procesů trasování pro trasování zdrojů, které chtějí získat informace. Pokud chcete přijímat data trasování, musíte vytvořit naslouchací proces pro zdroj trasování. Ve službě WCF, to lze provést přidáním následujícího kódu do konfiguračního souboru služby nebo klienta tak, že nastavíte zdroj trasování modelu služby `switchValue`:  
  
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
  
 Další informace o zdrojů trasování, naleznete v části Zdroj trasování v [Konfigurace trasování](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md) tématu.  
  
## <a name="activity-tracing-and-propagation"></a>Trasování aktivit a šíření  
 S `ActivityTracing` povolené a `propagateActivity` nastavena na `true` v `system.ServiceModel` zdroje trasování klienta a služby poskytovat korelace trasování v rámci logické jednotky (aktivity), zpracování napříč aktivity v rámci koncových bodů ( pomocí aktivity převody) a také napříč aktivity pokrývající několik koncových bodů (prostřednictvím šíření ID aktivity).  
  
 Tyto tři mechanismy (aktivity, přenosy a šíření) vám pomůže najít hlavní příčinu chyby více rychle pomocí nástroje prohlížeče trasování služeb. Další informace najdete v tématu [pomocí prohlížeče trasování služeb k zobrazení korelovaných trasování a řešení potíží](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Je možné rozšířit trasování, která je poskytována ServiceModel tak, že vytvoříte trasy definované uživatelem aktivity. Trasování činnosti uživatelem definované umožňuje uživateli vytvořit trasování činnosti:  
  
-   Skupina trasování do logických jednotek práce.  
  
-   Je možné korelovat aktivity prostřednictvím přenosů a šíření.  
  
-   Snížit náklady na trasování WCF (například náklady místa na disku souboru protokolu).  
  
 Další informace o trasování aktivity uživatelem definované, najdete v tématu [rozšíření trasování](../../../../docs/framework/wcf/samples/extending-tracing.md) vzorku.  
  
## <a name="message-logging"></a>Protokolování zpráv  
 Jak na klienta a služby z libovolné aplikace WCF je možné povolit protokolování zpráv. Povolit protokolování zpráv, musíte přidat následující kód k klienta nebo službě:  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <diagnostics>  
      <!-- Enable Message Logging here. -->  
      <!-- log all messages received or sent at the transport or service model levels -->  
      <messageLogging logEntireMessage="true"  
                      maxMessagesToLog="300"  
                      logMessagesAtServiceLevel="true"  
                      logMalformedMessages="true"  
                      logMessagesAtTransportLevel="true" />  
    </diagnostics>  
  </system.serviceModel>  
</configuration>  
```  
  
 Když se zaznamená zprávu, typ trasování závisí na tom, jestli jsou trasovány na klienta nebo serveru. Například zpráva "Add" odeslaný klientem je sledována v kategorii "TransportWrite" u klienta, že stejné zprávy je sledována v kategorii "TransportRead" na službu.  
  
 Konfigurace naslouchacího procesu trasování přidáním následujícího kódu <xref:System.Diagnostics> část souboru App.config klienta nebo v souboru Web.config služby:  
  
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
  
 Zprávy jsou protokolovány ve formátu XML v cílovém adresáři zadané v konfiguračním souboru.  
  
> [!NOTE]
>  Trasovací soubory nejsou vytvořeny bez vytvoření původně adresář protokolu. Ujistěte se, že existuje adresář C:\logs\ nebo určit alternativní protokolování adresář v konfiguraci naslouchacího procesu. Přečtěte si pokyny počáteční nastavení na konci tohoto dokumentu pro další informace.  
  
 Další informace o protokolování zpráv, najdete v článku [konfigurace protokolování zpráv](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md) tématu.  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1. Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Před spuštěním ukázky trasování a protokolování zpráv vytvořte adresář C:\logs\ pro službu zápis .svclog soubory, které chcete. Název tohoto adresáře je definována v konfiguračním souboru jako cestu pro trasování a zprávy, která je zaznamenána a je možné změnit. Poskytnout uživatel Network Service přístup pro zápis k adresáři s protokoly.  
  
3. K sestavení edice řešení C#, C++ nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Viz také:

- [Trasování](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)
