---
title: Rozšíření trasování
ms.date: 03/30/2017
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
ms.openlocfilehash: 02dfcc099883ed1d5e97b4f7b1a1f76d49b27a20
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43740690"
---
# <a name="extending-tracing"></a>Rozšíření trasování
Tato ukázka předvádí, jak rozšířit funkci trasování Windows Communication Foundation (WCF) zápisem aktivit uživatelem definované trasy v kódu klienta a služby. To umožňuje uživateli vytvořit trasování aktivity a seskupit trasování do logických jednotek práce. Také je možné korelovat aktivity prostřednictvím převody (v rámci stejný koncový bod) a šíření (napříč koncovými body). V této ukázce je povoleno trasování klienta a služby. Další informace o tom, jak povolit trasování v konfiguračních souborů klienta a služby, najdete v části [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Postupu a sestavení pokyny k instalaci pro tuto ukázku se nachází na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Vzorky mohou již být nainstalováno ve vašem počítači. Před pokračováním zkontrolujte následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) stáhnout všechny Windows Communication Foundation (WCF) a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>Trasování a šíření aktivity  
 Uživatelem definované aktivity trasování umožňuje uživateli vytvořit své vlastní aktivity trasování pro trasování skupiny do logických jednotek práce, korelovat aktivity prostřednictvím přenosů a šíření hodnoty a snížit náklady na trasování WCF (například místo na disku nákladů souboru protokolu).  
  
### <a name="adding-custom-sources"></a>Přidání vlastních zdrojů  
 Uživatelem definované trasy je přidat do kódu klienta a služby. Přidání zdroje trasování konfiguračních souborů klienta nebo služby umožňují vlastní trasování mají být zaznamenány a zobrazí v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Následující kód ukazuje, jak přidat zdroj uživatelem definované trasování s názvem `ServerCalculatorTraceSource` do konfiguračního souboru.  
  
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
  
### <a name="correlating-activities"></a>Korelace aktivity  
 Ke korelaci aktivit přímo napříč koncovými body, `propagateActivity` atribut musí být nastaven na `true` v `System.ServiceModel` zdroje trasování. Navíc bez nutnosti kontaktovat WCF aktivity rozšíření trasování, ServiceModel trasování aktivity musí být vypnutý. To můžete vidět v následujícím příkladu kódu.  
  
> [!NOTE]
>  Vypnutí trasování aktivity ServiceModel není stejná jako úroveň trasování, udávají `switchValue` vlastnost, nastavena na hodnotu off.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>Lessening snížení výkonu  
 Nastavení `ActivityTracing` vypnuté v `System.ServiceModel` zdroj trasování vygeneruje trasovací soubor, který obsahuje pouze uživatelské aktivity trasování, bez jakékoli ServiceModel trasování aktivity zahrnuta. Výsledkem je mnohem menší velikosti souboru protokolu. Však dojde ke ztrátě příležitosti ke korelaci zpracování trasování WCF.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Chcete-li nastavit, sestavte a spusťte ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  K sestavení edice řešení C# nebo Visual Basic .NET, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spusťte ukázku v konfiguraci s jedním nebo více počítači, postupujte podle pokynů v [spouštění ukázek Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Ukázky AppFabric monitorování](https://go.microsoft.com/fwlink/?LinkId=193959)
