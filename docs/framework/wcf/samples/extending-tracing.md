---
title: Rozšíření trasování
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: a7231d340d2528a42c8cbb5294d812d52db92d54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183693"
---
# <a name="extending-tracing"></a>Rozšíření trasování
Tato ukázka ukazuje, jak rozšířit windows komunikace Foundation (WCF) trasování funkce zápisem uživatelem definované trasování aktivit v kódu klienta a služby. To umožňuje uživateli vytvářet aktivity trasování a skupiny trasování do logické jednotky práce. Je také možné korelovat aktivity prostřednictvím přenosů (v rámci stejného koncového bodu) a šíření (napříč koncovými body). V této ukázce je povoleno trasování pro klienta i službu. Další informace o povolení trasování v konfiguračních souborech klientů a služeb naleznete v [tématu Trasování a Protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Tato ukázka je založena na [začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
> Postup nastavení a sestavení pokyny pro tuto ukázku jsou umístěny na konci tohoto tématu.  
  
> [!IMPORTANT]
> Ukázky mohou být již nainstalovány v počítači. Před pokračováním zkontrolujte následující (výchozí) adresář.  
>
> `<InstallDrive>:\WF_WCF_Samples`  
>
> Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a Windows Workflow Foundation (WF) Ukázky pro rozhraní .NET Framework 4](https://www.microsoft.com/download/details.aspx?id=21459) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka je umístěna v následujícím adresáři.  
>
> `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>Trasování a šíření aktivit  
 Uživatelem definované trasování aktivit umožňuje uživateli vytvářet vlastní aktivity trasování k seskupení trasování do logických jednotek práce, korelovat aktivity prostřednictvím přenosů a šíření a shrábnout náklady na výkon trasování WCF (například náklady na místo na disku souboru protokolu).  
  
### <a name="adding-custom-sources"></a>Přidání vlastních zdrojů  
 Uživatelem definované trasování lze přidat do kódu klienta i služby. Přidání zdrojů trasování do konfiguračních souborů klienta nebo služby umožňuje zaznamenat a zobrazit tyto vlastní trasování v [nástroji Service Trace Viewer (SvcTraceViewer.exe).](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) Následující kód ukazuje, jak přidat uživatelem `ServerCalculatorTraceSource` definovaný zdroj trasování pojmenovaný do konfiguračního souboru.  
  
```xml  
<system.diagnostics>  
    <sources>  
        <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
        <source name="ServerCalculatorTraceSource" switchValue="Information,ActivityTracing">  
            <listeners>  
                <add type="System.Diagnostics.DefaultTraceListener" name="Default">  
                    <filter type="" />  
                </add>  
                <add name="xml">  
                    <filter type="" />  
                </add>  
            </listeners>  
        </source>  
    </sources>  
    <sharedListeners>  
       <add initializeData="C:\logs\ServerTraces.svclog" type="System.Diagnostics.XmlWriterTraceListener"  
        name="xml" traceOutputOptions="Callstack">  
            <filter type="" />  
        </add>  
    </sharedListeners>  
    <trace autoflush="true" />  
</system.diagnostics>....  
....  
```  
  
### <a name="correlating-activities"></a>Korelační činnosti  
 Chcete-li korelovat aktivity `propagateActivity` přímo mezi `true` koncovými `System.ServiceModel` body, musí být atribut nastaven na ve zdroji trasování. Také chcete-li šířit trasování bez procházení wcf aktivity, sledování aktivity ServiceModel musí být vypnuto. To lze vidět v následujícím příkladu kódu.  
  
> [!NOTE]
> Vypnutí trasování aktivity ServiceModel není totéž jako s úroveň `switchValue` trasování, označené vlastností, vypnuto.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>Snížení nákladů na výkon  
 Nastavení `ActivityTracing` vypnout `System.ServiceModel` ve zdroji trasování generuje trasovací soubor, který obsahuje pouze uživatelem definované trasování aktivity, bez jakékoli trasování aktivity ServiceModel zahrnuty. Výsledkem je soubor protokolu mnohem menší velikosti. Však je ztracena možnost korelovat trasování zpracování WCF.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Nastavení, sestavení a spuštění ukázky  
  
1. Ujistěte se, že jste provedli [jednorázový postup instalace pro ukázky windows communication foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2. Chcete-li vytvořit c# nebo Visual Basic .NET vydání řešení, postupujte podle pokynů v [sestavení windows communication foundation ukázky](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3. Chcete-li spustit ukázku v konfiguraci jednoho nebo mezi počítači, postupujte podle pokynů v [části Spuštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také

- [Vzorky monitorování appfabricu](https://docs.microsoft.com/previous-versions/appfabric/ff383407(v=azure.10))
