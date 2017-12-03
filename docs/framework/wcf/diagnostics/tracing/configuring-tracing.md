---
title: "Konfigurace trasování"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: tracing [WCF]
ms.assetid: 82922010-e8b3-40eb-98c4-10fc05c6d65d
caps.latest.revision: "53"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 1b3b200e26d4d615dd67c13770073b76dac78005
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="configuring-tracing"></a>Konfigurace trasování
Toto téma popisuje, jak můžete povolit trasování, nakonfigurujte trasování zdrojů pro vydávání trasování a nastavte úrovně trasování, trasování aktivit sady a šíření pro podporu trasování začátku do konce korelace a nastavte trasování – moduly naslouchání pro přístup k trasování.  
  
 Doporučení nastavení trasování v provozním prostředí nebo ladění prostředí, najdete v části [doporučená nastavení pro trasování a protokolování zpráv](../../../../../docs/framework/wcf/diagnostics/tracing/recommended-settings-for-tracing-and-message-logging.md).  
  
> [!IMPORTANT]
>  V systému Windows 8 je nutné spustit vaší aplikace zvýšených oprávnění (Spustit jako správce), aby aplikace generují protokoly trasování.  
  
## <a name="enabling-tracing"></a>Povolení trasování  
 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)]výstupy následující data pro diagnostické trasování:  
  
-   Trasování pro milníky procesu pro všechny součásti aplikací, jako je například volání operací kód výjimky, upozornění a další důležité zpracování událostí.  
  
-   Události systému Windows chybu při trasování funkce nefunguje správně. V tématu [protokolování událostí](../../../../../docs/framework/wcf/diagnostics/event-logging/index.md).  
  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]trasování je postavený na <xref:System.Diagnostics>. Pokud chcete používat trasování, byste měli definovat trasování zdrojů v konfiguračním souboru nebo v kódu. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]definuje zdroj trasování pro každou [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] sestavení. `System.ServiceModel` Zdroj trasování je nejvíce Obecné [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zdroj trasování a záznamů zpracování milníky napříč [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] komunikačního balíku z zadávání ponechat přenosu zadávání nebo nechat uživatelského kódu. `System.ServiceModel.MessageLogging` Zdroj trasování zaznamenává všechny zprávy, které toku prostřednictvím systému.  
  
 Ve výchozím nastavení není povoleno trasování. Aktivujte trasování, musíte vytvořit naslouchací proces trasování a nastaví úroveň trasování než "Off" zdroje vybraného trasování v konfiguraci. v opačném [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] negeneruje žádné trasování. Pokud nezadáte naslouchací proces, trasování se automaticky zakáže. Pokud je definována naslouchací proces, ale není zadána žádná, úroveň je nastavena na "Off", ve výchozím nastavení, což znamená, že jsou vydávány žádné trasování.  
  
 Pokud používáte [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] body rozšiřitelnosti například vlastní operaci invokers by měl emitování vlastní trasování. Je to proto, pokud byste implementovat bod rozšiřitelnosti, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] mohou už negeneruje standardní trasování ve výchozí cestě. Pokud není implementujete ruční trasování podporu generování trasování, nemusíte vidět trasování, které očekáváte.  
  
 Trasování lze nakonfigurovat úpravou konfiguračního souboru aplikace – buď soubor Web.config pro Web webové aplikace nebo Appname.exe.config vlastním hostováním aplikací. Následuje příklad takové úpravy. Další informace o těchto nastaveních najdete v části "Konfigurace trasování – moduly naslouchání na využívat trasování".  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
            <listeners>  
               <add name="traceListener"   
                   type="System.Diagnostics.XmlWriterTraceListener"   
                   initializeData= "c:\log\Traces.svclog" />  
            </listeners>  
         </source>  
      </sources>  
   </system.diagnostics>  
</configuration>  
```  
  
> [!NOTE]
>  Chcete-li upravit konfigurační soubor [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] projektu služby v [!INCLUDE[vs_current_short](../../../../../includes/vs-current-short-md.md)], klikněte pravým tlačítkem na soubor konfigurace aplikace – buď soubor Web.config pro Web webové aplikace nebo Appname.exe.config pro vlastním hostováním aplikaci v  **Průzkumník řešení**. Zvolte **upravit konfiguraci WCF** položky kontextové nabídky. Spustí se [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md), což umožňuje změnit nastavení konfigurace pro [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] služeb pomocí grafického uživatelského rozhraní.  
  
## <a name="configuring-trace-sources-to-emit-traces"></a>Konfigurace trasování zdroje pro vydávání trasování  
 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]definuje zdroj trasování pro každé sestavení. Trasování generované v rámci sestavení jsou dostupné přes naslouchací procesy definované pro tento zdroj. Následující zdroje trasování jsou definovány:  
  
-   System.ServiceModel: Protokoly všech fázích [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] zpracování, vždy, když je pro čtení konfigurace, zpráva se zpracuje v přenos, je zabezpečení zpracování zprávy odeslaných za uživatelského kódu a tak dále.  
  
-   Poslouchají: Zaznamená všechny zprávy, které toku prostřednictvím systému.  
  
-   System.IdentityModel.  
  
-   System.ServiceModel.Activation.  
  
-   System.IO.Log: Protokolování pro rozhraní .NET Framework na běžné Log File System (CLFS).  
  
-   System.Runtime.Serialization: Protokoly Pokud jsou objekty číst nebo zapisovat.  
  
-   CardSpace.  
  
 Každý zdroj trasování používat stejné (sdílené) naslouchací proces, můžete nakonfigurovat, jak je uvedeno v následujícím příkladu konfigurace.  
  
```xml  
<configuration>  
    <system.diagnostics>  
        <sources>  
            <source name="System.ServiceModel"   
                    switchValue="Information, ActivityTracing"  
                    propagateActivity="true">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="CardSpace">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IO.Log">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.Runtime.Serialization">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
            <source name="System.IdentityModel">  
                <listeners>  
                    <add name="xml" />  
                </listeners>  
            </source>  
        </sources>  
  
        <sharedListeners>  
            <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="c:\log\Traces.svclog" />  
        </sharedListeners>  
    </system.diagnostics>  
</configuration>  
```  
  
 Kromě toho můžete přidat vlastní trasování zdrojů, jak ukazuje následující příklad, pro vydávání trasování kódu uživatele.  
  
```xml  
<system.diagnostics>  
   <sources>  
       <source name="UserTraceSource" switchValue="Warning, ActivityTracing" >  
          <listeners>  
              <add name="xml"  
                 type="System.Diagnostics.XmlWriterTraceListener"  
                 initializeData="C:\logs\UserTraces.svclog" />  
          </listeners>  
       </source>  
   </sources>  
   <trace autoflush="true" />   
</system.diagnostics>  
```  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]vytváření uživatelem definované trasování zdrojů, najdete v části [rozšíření trasování](../../../../../docs/framework/wcf/samples/extending-tracing.md).  
  
## <a name="configuring-trace-listeners-to-consume-traces"></a>Konfigurace trasování – moduly naslouchání využívat trasování  
 V době běhu [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] informační kanály trasování dat naslouchací procesy, které zpracovávají data. [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)]nabízí několik předdefinovaných naslouchací procesy pro <xref:System.Diagnostics>, který se liší ve formátu používají pro výstup. Můžete také přidat vlastní naslouchací proces typy.  
  
 Můžete použít `add` Chcete-li určit název a typ naslouchací proces trasování, kterou chcete použít. V našem příkladu konfigurace jsme pojmenovali naslouchací proces `traceListener` a přidat standardní naslouchací proces trasování rozhraní .NET Framework (`System.Diagnostics.XmlWriterTraceListener`) jako typ, který chcete použít. Můžete přidat libovolný počet trasování – moduly naslouchání pro každý zdroj. Naslouchací proces trasování vysílá trasování do souboru, je nutné zadat výstupní soubor umístění a název v konfiguračním souboru. To se provádí nastavením `initializeData` k názvu souboru pro tento naslouchací proces. Pokud nezadáte název souboru, je generována náhodného názvu souboru na základě typu naslouchací proces používá. Pokud <xref:System.Diagnostics.XmlWriterTraceListener> se použije, generuje se název souboru bez přípony. Pokud budete implementovat vlastní naslouchací proces, můžete také použít tento atribut přijímat data inicializace než název souboru. Například můžete zadat identifikátor databáze pro tento atribut.  
  
 Můžete nakonfigurovat vlastní naslouchací odeslat trasování v drátové síti, například ke vzdálené databázi. Jako modul pro nasazení aplikace by měl vynutit řízení správné přístupu na protokoly trasování ve vzdáleném počítači.  
  
 Můžete také nakonfigurovat naslouchací prostřednictvím kódu programu. [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Postupy: vytvoření a inicializace naslouchacích procesů trasování](http://go.microsoft.com/fwlink/?LinkId=94648) a [vytváření vlastní TraceListener](http://go.microsoft.com/fwlink/?LinkId=96239).  
  
> [!CAUTION]
>  Protože `System.Diagnostics.XmlWriterTraceListener` nejsou bezpečné pro vlákna, zdroj trasování může zamknutí prostředků, výhradně, při výstupu trasování. Pokud mnoho vláken výstup trasování ke zdroji trasování, který je nakonfigurován pro použití této naslouchací proces, může dojít, sporu prostředků, výsledkem problém významně zvýšit výkon. Chcete-li vyřešit tento problém, měli byste implementovat vlastní naslouchací proces, který je bezpečný pro přístup z více vláken.  
  
## <a name="trace-level"></a>Úroveň trasování  
 Úroveň trasování řídí `switchValue` nastavení zdroje trasování. Úrovní trasování k dispozici jsou popsané v následující tabulce.  
  
|Úroveň trasování|Povaha sledovaného události|Obsah sledovaných událostí|Sledovaných událostí|Cílový uživatel|  
|-----------------|----------------------------------|-----------------------------------|--------------------|-----------------|  
|Off|Není k dispozici|Není k dispozici|Žádné trasování jsou vydávány.|Není k dispozici|  
|Kritická|"Zápornou" události: události, které označují neočekávané zpracování nebo chybový stav.||Jsou zaznamenány neošetřených výjimek, včetně následujících:<br /><br /> – OutOfMemoryException<br />-Výjimka ThreadAbortException (všechny ThreadAbortExceptionHandler vyvolá modulu CLR)<br />-StackOverflowException (nemůže být zachycena)<br />-ConfigurationErrorsException –<br />-SEHException –<br />-Chyby spuštění aplikací<br />-Failfast události<br />-Systém přestane reagovat.<br />-Škodlivých zpráv: zpráva trasování, které způsobí selhání aplikace.|Správci<br /><br /> Vývojáři aplikací|  
|Chyba|"Zápornou" události: události, které označují neočekávané zpracování nebo chybový stav.|Došlo k neočekávané zpracování. Aplikaci se nepodařilo provést úlohu podle očekávání. Aplikace je však stále spuštěný a funkční.|Všechny výjimky jsou protokolovány.|Správci<br /><br /> Vývojáři aplikací|  
|Upozornění|"Zápornou" události: události, které označují neočekávané zpracování nebo chybový stav.|Možný problém došlo k chybě nebo může dojít, ale stále funkce aplikace správně. Však nemusí dál fungovat správně.|-Aplikace přijímá více požadavků než jeho nastavení omezení povolit.<br />-Přijímající fronta je téměř své maximální kapacity nakonfigurované.<br />-Byla překročena časový limit.<br />-Pověření jsou odmítnuta.|Správci<br /><br /> Vývojáři aplikací|  
|Informace o|"Pozitivní" události: události, které označit úspěšné milníky|Důležité a úspěšné milníky provádění aplikací, bez ohledu na to, zda aplikace funguje správně, nebo ne.|Obecně platí jsou generovány, zprávy, které jsou užitečné pro monitorování a diagnostice stav systému, měření výkonu nebo profilace. Tyto informace můžete použít pro správu výkon a plánování kapacity:<br /><br /> -Kanály se vytvoří.<br />-Naslouchací procesy koncový bod se vytvoří.<br />-Zpráva zadá nebo nechá přenosu.<br />-Načte token zabezpečení.<br />– Nastavení konfigurace je pro čtení.|Správci<br /><br /> Vývojáři aplikací<br /><br /> Vývojáři produktu.|  
|Verbose|"Pozitivní" události: události, které označit milníky úspěšné.|Jsou vydávány nízkou úroveň události pro uživatele kódu a údržby.|Obecně platí můžete tato úroveň optimalizace ladění nebo aplikace.<br /><br /> -Záhlaví srozumitelné zprávy.|Správci<br /><br /> Vývojáři aplikací<br /><br /> Vývojáři produktu.|  
|ActivityTracing||Události toku mezi aktivitami zpracování a součásti.|Tato úroveň umožňuje správci a vývojáři ke korelaci aplikací ve stejné doméně aplikace:<br /><br /> -Trasování pro hranice aktivity, jako je například spuštění a zastavení.<br />-Trasování pro přenosy.|Všechny|  
|Všechny||Aplikace může fungovat správně. Všechny události jsou vydávány.|Všechny předchozí události.|Všechny|  
  
 Úrovně z podrobné na kritický přibývají na sebe, který je každou úroveň trasování obsahuje všechny úrovně nad ním s výjimkou úroveň Off. Například naslouchací proces naslouchání na úrovni upozornění obdrží trasování kritické chyby a upozornění. Všechny úroveň zahrnuje události z podrobné na kritický a aktivity události trasování.  
  
> [!CAUTION]
>  Úrovně informace, podrobný nebo ActivityTracing vygeneroval velké množství trasování, které může mít negativní vliv propustnost zpráv, pokud jste použili až všechny dostupné prostředky na počítači.  
  
## <a name="configuring-activity-tracing-and-propagation-for-correlation"></a>Konfigurace trasování aktivit a šíření pro korelace  
 `activityTracing` Hodnota parametru `switchValue` atribut slouží k povolení trasování aktivity, který vysílá trasování pro aktivity hranice a přenosy v rámci koncové body.  
  
> [!NOTE]
>  Když použijete určité funkce rozšiřitelnost v [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)], může získat <xref:System.NullReferenceException> při zapnutém trasování aktivity. Chcete-li tento problém vyřešit, zkontrolujte konfigurační soubor vaší aplikace a ujistěte se, že `switchValue` atribut pro vaše zdroj trasování není nastavený na `activityTracing`.  
  
 `propagateActivity` Atribut uvádí, zda by mělo být předáno aktivity na ostatní koncové body, které jsou součástí výměny zpráv. Nastavením této hodnoty na `true`, můžete provést trasovací soubory generované žádné dva koncové body a sledovat, jak sadu trasování na jeden koncový bod předávány sadu trasování na jiný koncový bod.  
  
 [!INCLUDE[crabout](../../../../../includes/crabout-md.md)]trasování aktivit a šíření, najdete v části [šíření](../../../../../docs/framework/wcf/diagnostics/tracing/propagation.md).  
  
 Obě `propagateActivity` a `ActivityTracing` logické hodnoty, na které se týkají System.ServiceModel TraceSource. `ActivityTracing` Hodnota platí také pro libovolný zdroj trasování, včetně [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] nebo uživatelem definované snímků.  
  
 Nelze použít `propagateActivity` atribut s uživatelem definované trasování zdrojů. Šíření ID aktivity uživatele kódu, je nutné nenastavíte ServiceModel `ActivityTracing`, zároveň ponechat ServiceModel `propagateActivity` atribut nastaven na `true`.  
  
## <a name="see-also"></a>Viz také  
 [Trasování](../../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Správa a Diagnostika](../../../../../docs/framework/wcf/diagnostics/index.md)  
 [Postupy: vytváření a inicializace trasování – moduly naslouchání](http://go.microsoft.com/fwlink/?LinkId=94648)  
 [Vytváření vlastních TraceListener](http://go.microsoft.com/fwlink/?LinkId=96239)
