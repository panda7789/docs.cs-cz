---
title: Trasování a protokolování zpráv
description: Naučte se používat nástroj pro prohlížení služby Service Trace Viewer (SvcTraceViewer.exe) k zobrazení trasování a protokolů zpráv pomocí této ukázky WFC.
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: bb49334252c2415223b0f8f5559a6dc838d175e3
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246022"
---
# <a name="tracing-and-message-logging"></a>Trasování a protokolování zpráv
Tato ukázka demonstruje, jak povolit trasování a protokolování zpráv. Výsledné trasování a protokoly zpráv se zobrazují pomocí [nástroje Service Trace Viewer (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md). Tato ukázka je založena na [Začínáme](getting-started-sample.md).  
  
> [!NOTE]
> Postup nastavení a pokyny pro sestavení pro tuto ukázku najdete na konci tohoto tématu.  
  
## <a name="tracing"></a>Trasování  
 Windows Communication Foundation (WCF) používá mechanismus trasování definovaný v <xref:System.Diagnostics> oboru názvů. V tomto trasovacím modelu jsou data trasování vytvořena pomocí zdrojů trasování, které aplikace implementuje. Jednotlivé zdroje jsou označeny názvem. Trasovat příjemce: Vytvoření posluchačů trasování pro zdroje trasování, pro které chtějí získat informace. Chcete-li přijímat data trasování, je nutné vytvořit naslouchací proces pro zdroj trasování. V rámci služby WCF to můžete udělat přidáním následujícího kódu do konfiguračního souboru služby nebo klienta nastavením zdroje trasování modelu služby `switchValue` :  
  
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
  
 Další informace o zdrojích trasování naleznete v části zdroj trasování v tématu [Konfigurace trasování](../diagnostics/tracing/configuring-tracing.md) .  
  
## <a name="activity-tracing-and-propagation"></a>Trasování aktivit a šíření  
 `ActivityTracing`Povolení a `propagateActivity` nastavení `true` ve `system.ServiceModel` zdrojích trasování pro klienta i službu poskytují korelaci trasování v rámci logických jednotek zpracování (aktivity), napříč aktivitami v koncových bodech (prostřednictvím přenosů aktivit) a napříč aktivitami zahrnujícími více koncových bodů (prostřednictvím šíření ID aktivity).  
  
 Tyto tři mechanismy (aktivity, přenosy a šíření) vám mohou pomoci najít hlavní příčinu chyby rychleji pomocí nástroje Prohlížeč trasování služby. Další informace najdete v tématu [použití prohlížeče trasování služby pro zobrazení korelačních trasování a odstraňování potíží](../diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Je možné roztáhnout trasování, které poskytuje ServiceModel, vytvořením trasování aktivity definované uživatelem. Trasování uživatelsky definované aktivity umožňuje uživateli vytvářet aktivity trasování pro:  
  
- Seskupí trasování do logických pracovních jednotek.  
  
- Korelujte aktivity prostřednictvím přenosů a šíření.  
  
- Snížit náklady na výkon trasování WCF (například náklady na místo na disku souboru protokolu).  
  
 Další informace o uživatelsky definovaném trasování aktivit najdete v ukázce [rozšíření trasování](extending-tracing.md) .  
  
## <a name="message-logging"></a>Protokolování zpráv  
 Protokolování zpráv lze povolit v klientech i službě jakékoli aplikace WCF. Chcete-li povolit protokolování zpráv, musíte do klienta nebo služby přidat následující kód:  
  
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
  
 Při záznamu zprávy je typ trasování závislý na tom, zda je sledován v klientovi nebo na serveru. Například zpráva "Přidat", která je odeslána klientovi, je sledována pod kategorií "TransportWrite" na klientovi, zatímco stejná zpráva je sledována pod kategorií "TransportRead" ve službě.  
  
 Nakonfigurujte naslouchací proces trasování přidáním následujícího kódu do <xref:System.Diagnostics> oddílu App.config souboru klienta nebo Web.config souboru služby:  
  
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
  
 Zprávy jsou protokolovány ve formátu XML v cílovém adresáři zadaném v konfiguračním souboru.  
  
> [!NOTE]
> Trasovací soubory se nevytvoří bez prvotního vytvoření adresáře protokolu. Ujistěte se, že adresář C:\logs\ existuje, nebo zadejte alternativní adresář protokolování v konfiguraci naslouchacího procesu. Další informace najdete v úvodních pokynech k nastavení na konci tohoto dokumentu.  
  
 Další informace o protokolování zpráv najdete v tématu [Konfigurace protokolování zpráv](../diagnostics/configuring-message-logging.md) .  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [postup jednorázového nastavení pro Windows Communication Foundation ukázky](one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Před spuštěním ukázky trasování a protokolování zpráv vytvořte adresář C:\logs\, ve kterém bude služba zapisovat soubory. svclog do. Název tohoto adresáře je definovaný v konfiguračním souboru jako cesta pro trasování a zprávy, které se mají protokolovat a které je možné změnit. Udělte síťové službě uživatele přístup pro zápis do adresáře Logs.  
  
3. Chcete-li sestavit edici C#, C++ nebo Visual Basic .NET, postupujte podle pokynů v tématu [sestavování ukázek Windows Communication Foundation](building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v části [spuštění ukázek Windows Communication Foundation](running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky již mohou být nainstalovány v počítači. Než budete pokračovat, vyhledejte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přečtěte si [ukázky Windows Communication Foundation (WCF) a programovací model Windows Workflow Foundation (WF) pro .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) ke stažení všech Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázek. Tato ukázka se nachází v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Viz také

- [Trasování](../diagnostics/tracing/index.md)
- [Ukázky monitorování technologie AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
