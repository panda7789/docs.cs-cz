---
title: "Rozšíření trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 2b971a99-16ec-4949-ad2e-b0c8731a873f
caps.latest.revision: "28"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 235b1a8454d573264f0bbe3cd5f9809d88d08209
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="extending-tracing"></a>Rozšíření trasování
Tento příklad ukazuje, jak rozšířit [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] trasování funkce napsáním uživatelské aktivity trasování v kódu klienta a služby. To umožňuje uživateli vytvořit trasování aktivity a seskupovat trasování do logické jednotky práce. Je také možné vazbu mezi aktivitami prostřednictvím přenosu (v rámci stejné koncového bodu) a šíření (v koncových bodů). V této ukázce je povoleno trasování pro klienta a služby. Další informace o tom, jak povolit trasování v konfiguračních souborech klienta a služby najdete v tématu [trasování a protokolování zpráv](../../../../docs/framework/wcf/samples/tracing-and-message-logging.md).  
  
 Tato ukázka je založena na [Začínáme](../../../../docs/framework/wcf/samples/getting-started-sample.md).  
  
> [!NOTE]
>  Nastavení postupu a sestavení pokyny k této ukázce jsou umístěné na konci tohoto tématu.  
  
> [!IMPORTANT]
>  Ukázky může být již nainstalován ve vašem počítači. Před pokračováním zkontrolovat na následující adresář (výchozí).  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  Pokud tento adresář neexistuje, přejděte na [Windows Communication Foundation (WCF) a ukázky Windows Workflow Foundation (WF) pro rozhraní .NET Framework 4](http://go.microsoft.com/fwlink/?LinkId=150780) ke stažení všechny [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] a [!INCLUDE[wf1](../../../../includes/wf1-md.md)] ukázky. Tato ukázka se nachází v následujícím adresáři.  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Management\ExtendingTracing`  
  
## <a name="tracing-and-activity-propagation"></a>Trasování a rozšíření aktivity  
 Uživatelem definované aktivity trasování umožňuje uživateli vytvořit své vlastní aktivity trasování pro trasování skupiny do logické jednotky práce, correlate aktivit prostřednictvím přenosů a šíření a snížit náklady na výkon [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] trasování (například místo na disku souboru protokolu).  
  
### <a name="adding-custom-sources"></a>Přidání vlastních zdrojů  
 Uživatelem definované trasování mohou být přidány do kódu klienta a služby. Přidání zdroje trasování konfiguračních souborů klienta služby Windows nebo povolit pro toto vlastní trasování zaznamenat a zobrazí v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md). Následující kód ukazuje, jak přidat vlastní trasování zdroj s názvem `ServerCalculatorTraceSource` do konfiguračního souboru.  
  
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
 Pro vazbu mezi aktivitami přímo v koncových bodů, `propagateActivity` musí být nastaven `true` v `System.ServiceModel` zdroj trasování. Navíc k šíření trasování bez průchodu přes [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aktivit, trasování ServiceModel aktivita musí být vypnutý. To můžete vidět v následujícím příkladu kódu.  
  
> [!NOTE]
>  Vypnutí trasování aktivity ServiceModel není stejně, jako když úroveň trasování odlišené `switchValue` , nastavena na vypnuto.  
  
```xml  
<system.diagnostics>  
    <sources>  
      <source name="System.ServiceModel" switchValue="Warning" propagateActivity="true">  
  
    ...  
  
       </source>  
    </sources>  
</system.diagnostics>  
```  
  
### <a name="lessening-performance-cost"></a>Lessening snížený výkon  
 Nastavení `ActivityTracing` vypnuto v `System.ServiceModel` zdroj trasování, vygeneruje soubor trasování, který obsahuje pouze uživatelské aktivity trasování, bez trasování aktivity ServiceModel zahrnuty. Výsledkem je mnohem menší velikost souboru protokolu. Však moci korelovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zpracování trasování se ztratí.  
  
##### <a name="to-set-up-build-and-run-the-sample"></a>Pokud chcete nastavit, sestavit a spustit ukázku  
  
1.  Ujistěte se, že jste provedli [jednorázové postup nastavení pro ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md).  
  
2.  Sestavení C# nebo Visual Basic .NET edice řešení, postupujte podle pokynů v [vytváření ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/building-the-samples.md).  
  
3.  Spustit ukázku v konfiguraci s jednou nebo mezi počítači, postupujte podle pokynů v [spuštění ukázky Windows Communication Foundation](../../../../docs/framework/wcf/samples/running-the-samples.md).  
  
## <a name="see-also"></a>Viz také  
 [Ukázky monitorování AppFabric](http://go.microsoft.com/fwlink/?LinkId=193959)
