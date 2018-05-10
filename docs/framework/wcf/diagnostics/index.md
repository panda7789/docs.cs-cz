---
title: Správa a diagnostika
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation, diagnostics
- Windows Communication Foundation, administration
- diagnostics [WCF]
- WCF, diagnostics
- administration [WCF]
- WCF, administration
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
ms.openlocfilehash: c69d5681b186fdfae168ceea8b35f5786eaf02c9
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="administration-and-diagnostics"></a>Správa a diagnostika
Windows Communication Foundation (WCF) poskytuje bohatou sadu funkcí, které umožňují monitorovat různých fázích životního aplikace. Například můžete použít konfiguraci nastavení služeb a klientů v nasazení. WCF obsahuje velké sady čítačů výkonu můžete měřit výkon vaší aplikace. WCF taky zpřístupňuje dat kontroly služby za běhu prostřednictvím poskytovatele WCF Windows Management Instrumentation (WMI). Při vyskytne chyba nebo spustí funguje nesprávně aplikace, můžete zobrazit, pokud nic významné došlo k chybě v protokolu událostí. Můžete také použít protokolování zpráv a trasování a zjistěte, jaké události jsou situaci klient server ve vaší aplikaci. Tyto funkce pomáhat vývojáře a IT odborníky odstraňování aplikace WCF při nepracuje správně.  
  
> [!NOTE]
>  Pokud se vám chyb s nejsou žádné konkrétní podrobné informace, měli byste povolit `includeExceptionDetailInFaults` atribut [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) konfigurační prvek. To se dá pokyn WCF Odeslat podrobnosti výjimky pro klienty, která umožňuje detekci bez nutnosti pokročilejší diagnostiku mnoho běžných problémů. Další informace najdete v tématu [odesílání a přijímání chyb](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>Diagnostické funkce poskytované službou WCF  
 WCF poskytuje následující funkce diagnostics:  
  
-   Trasování začátku do konce poskytuje data instrumentace pro řešení potíží s aplikace bez použití ladicí program. WCF výstupy trasování pro proces milníky, jakož i chybové zprávy. To může zahrnovat otevření kanálu nebo odesílání a přijímání zpráv pomocí hostitele služby. Trasování je možné zapnout pro běžící aplikaci monitorovat její postup. Další informace najdete v tématu [trasování](../../../../docs/framework/wcf/diagnostics/tracing/index.md) tématu. Abyste pochopili, jak můžete trasování ladění aplikace, najdete v článku [pomocí trasování řešení vaše aplikace](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) tématu.  
  
-   Protokolování zpráv umožňuje zobrazit vzhled zprávy před a po přenosu. Další informace najdete v tématu [protokolování zpráv](../../../../docs/framework/wcf/diagnostics/message-logging.md) tématu.  
  
-   Události trasování událostí se zapisují do protokolu událostí pro potíže hlavní. Potom můžete v prohlížeči událostí k prozkoumání abnormality. Další informace najdete v tématu [protokolování událostí](../../../../docs/framework/wcf/diagnostics/event-logging/index.md) tématu.  
  
-   Čítače výkonu, které jsou k dispozici prostřednictvím nástroje Sledování výkonu umožňují sledovat vaše aplikace a stavu systému. Další informace najdete v tématu [čítače výkonu](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md) tématu.  
  
-   <xref:System.ServiceModel.Configuration> Obor názvů umožňuje načíst konfigurační soubory a nastavit koncový bod služby nebo klienta. Model objektu do skriptu změny mnoho aplikací můžete použít při aktualizace musí být nasazený na mnoha počítačích. Alternativně můžete použít [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) upravit konfigurační nastavení pomocí průvodce s grafickým uživatelským rozhraním. Další informace najdete v tématu [konfigurace vaše aplikace](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md) tématu.  
  
-   Rozhraní WMI umožňuje zjistit, jaké služby jsou naslouchá na počítači a vazby, které jsou používány. Další informace najdete v tématu [pomocí rozhraní Windows Management Instrumentation pro diagnostiku](../../../../docs/framework/wcf/diagnostics/wmi/index.md) tématu.  
  
 WCF také poskytuje několik nástrojů grafického uživatelského rozhraní a příkazový řádek, aby bylo snazší pro vás k vytvoření, nasazení a správě aplikací služby WCF. Další informace najdete v tématu [nástroje služby Windows Communication Foundation](../../../../docs/framework/wcf/tools.md). Například můžete použít [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) vytvořit a upravit nastavení konfigurace WCF pomocí průvodce, místo přímou úpravou kódu XML. Můžete také [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) Pokud chcete zobrazit, skupiny a filtrovat zprávy trasování tak, aby lze diagnostikovat, opravte a zkontrolujte problémy s služby WCF.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace vaší aplikace](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)  
 [Nasazení služeb](../../../../docs/framework/wcf/diagnostics/deploying-services.md)  
 [Přehled výjimek](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)  
 [Protokolování událostí](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [Protokolování zpráv](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Editor konfigurace (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Nástroj ServiceModelReg.exe](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)  
 [Trasování](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)](../../../../docs/framework/wcf/diagnostics/wmi/index.md)  
 [Čítače výkonu](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)  
 [Nástroje Windows Communication Foundation](../../../../docs/framework/wcf/tools.md)
