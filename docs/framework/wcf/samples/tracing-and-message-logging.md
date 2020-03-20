---
title: Trasování a protokolování zpráv
ms.date: 03/30/2017
helpviewer_keywords:
- Tracing and logging
ms.assetid: a4f39bfc-3c5e-4d51-a312-71c5c3ce0afd
ms.openlocfilehash: 9ffb7a99540b953fc93a22d2296caf86f294d25d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79143821"
---
# <a name="tracing-and-message-logging"></a>Trasování a protokolování zpráv
Tato ukázka ukazuje, jak povolit trasování a protokolování zpráv. Výsledné trasování a protokoly zpráv jsou zobrazeny pomocí [nástroje Service Trace Viewer Tool (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> Postup instalace a pokyny k sestavení pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
## <a name="tracing"></a>Trasování  
 Windows Communication Foundation (WCF) používá mechanismus <xref:System.Diagnostics> trasování definované v oboru názvů. V tomto modelu trasování trasovací data je vytvářena zdroje trasování, které aplikace implementují. Každý zdroj je identifikován názvem. Trace spotřebitelé vytvořit naslouchací procesy trasování pro zdroje trasování, pro které chtějí načíst informace. Chcete-li přijímat data trasování, musíte vytvořit naslouchací proces pro zdroj trasování. V WCF to lze provést přidáním následujícího kódu do konfiguračního souboru služby `switchValue`nebo klienta nastavením zdroje trasování modelu služby :  
  
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
  
 Další informace o zdrojích trasování naleznete v části Zdroj trasování v tématu [Konfigurace trasování.](../../../../docs/framework/wcf/diagnostics/tracing/configuring-tracing.md)  
  
## <a name="activity-tracing-and-propagation"></a>Sledování a šíření aktivit  
 Povolení `ActivityTracing` a `propagateActivity` nastavení `true` ve `system.ServiceModel` zdrojích trasování pro klienta i službu poskytují korelaci trasování v rámci logických jednotek zpracování (aktivity), napříč aktivitami v rámci koncových bodů (prostřednictvím přenosů aktivit) a napříč aktivitami zahrnujícími více koncových bodů (prostřednictvím šíření ID aktivity).  
  
 Tyto tři mechanismy (aktivity, přenosy a šíření) vám mohou pomoci rychleji vyhledat hlavní příčinu chyby pomocí nástroje Prohlížeč trasování služby. Další informace naleznete [v tématu Použití prohlížeče trasování služby pro zobrazení korelovaných trasování a řešení potíží](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Je možné rozšířit trasování, které je poskytováno ServiceModel vytvořením uživatelem definované trasování aktivity. Uživatelem definované trasování aktivit umožňuje uživateli vytvářet aktivity trasování do:  
  
- Seskupit trasování do logických jednotek práce.  
  
- Korelovat aktivity prostřednictvím přenosů a šíření.  
  
- Směřovat náklady na výkon trasování WCF (například náklady na místo na disku souboru protokolu).  
  
 Další informace o trasování aktivity definované uživatelem naleznete v tématu [Rozšíření trasování](../../../../docs/framework/wcf/samples/extending-tracing.md) ukázka.  
  
## <a name="message-logging"></a>Protokolování zpráv  
 Protokolování zpráv lze povolit v klientovi i ve službě libovolné aplikace WCF. Chcete-li povolit protokolování zpráv, je nutné přidat do klienta nebo služby následující kód:  
  
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
  
 Při zaznamenání zprávy, typ trasování závisí na tom, zda je trasována na straně klienta nebo serveru. Například zpráva "Přidat", která je odeslána klientovi je sledována v rámci kategorie "TransportWrite" na straně klienta, zatímco stejná zpráva je sledována v rámci kategorie "TransportRead" ve službě.  
  
 Nakonfigurujte naslouchací proces trasování přidáním následujícího kódu do <xref:System.Diagnostics> části souboru App.config klienta nebo souboru Web.config služby:  
  
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
  
 Zprávy jsou protokolovány ve formátu XML v cílovém adresáři určeném v konfiguračním souboru.  
  
> [!NOTE]
> Trasovací soubory nejsou vytvořeny bez počátečního vytvoření adresáře protokolu. Ujistěte se, že adresář C:\logs\ existuje, nebo zadejte alternativní adresář protokolování v konfiguraci naslouchacího procesu. Další informace naleznete v pokynech k počátečnímu nastavení na konci tohoto dokumentu.  
  
 Další informace o protokolování zpráv naleznete v tématu [Konfigurace protokolování zpráv.](../../../../docs/framework/wcf/diagnostics/configuring-message-logging.md)  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Před spuštěním ukázky Trasování a Protokolování zpráv vytvořte adresář C:\logs\ pro službu, do které bude zapisovat soubory Svclog. Název tohoto adresáře je definován v konfiguračním souboru jako cesta pro trasování a zprávy, které mají být zaznamenány a lze je změnit. Poučte uživateli síťovou službu přístup k adresáři protokolů.  
  
3. Chcete-li vytvořit c#, C++ nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
4. Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\TracingAndLogging`  
  
## <a name="see-also"></a>Viz také

- [Trasování](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
