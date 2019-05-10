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
ms.openlocfilehash: 5df95c6b5f91cd4f36bd03c1bd291f7a44025ee9
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64600089"
---
# <a name="administration-and-diagnostics"></a>Správa a diagnostika
Windows Communication Foundation (WCF) poskytuje bohatou sadu funkcí, které vám pomohou sledovat různých fázích životního aplikace. Například můžete použít konfiguraci nastavení služeb a klientů v nasazení. WCF obsahuje velké sady čítače výkonu umožňují měřit výkon vaší aplikace. WCF také poskytuje dat kontroly služby za běhu pomocí zprostředkovatele WCF Windows Management Instrumentation (WMI). Při aplikaci dojde k selhání nebo spuštění funguje správně, můžete použít v protokolu událostí zobrazíte, pokud žádné významné došlo k chybě. Pokud chcete zjistit, jaké události jsou děje začátku do konce ve vaší aplikaci můžete také použít protokolování zpráv a trasování. Tyto funkce pomůžou vývojářům a IT profesionály řešení aplikaci WCF při nepracuje správně.  
  
> [!NOTE]
>  Pokud se vám zobrazuje chyb se žádné informace o konkrétní podrobnosti, měli byste povolit `includeExceptionDetailInFaults` atribut [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) konfiguračního prvku. Toto dá pokyn odesílat podrobnosti o výjimce klientům, WCF, která umožňuje zjišťovat řadou běžných problémů bez nutnosti pokročilé diagnostiky. Další informace najdete v tématu [odesílání a příjem chyb](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>Diagnostické funkce poskytované službou WCF  
 WCF poskytuje následující funkce diagnostiky:  
  
- Trasování začátku do konce obsahuje data instrumentace aplikace bez použití ladicího programu. WCF výstup trasování pro proces milníky, stejně jako chybové zprávy. To může zahrnovat otevření objektu pro vytváření kanálů nebo odeslání a příjem zpráv pomocí hostitele služby. Trasování je možné povolit pro běžící aplikaci můžete sledovat její průběh. Další informace najdete v tématu [trasování](../../../../docs/framework/wcf/diagnostics/tracing/index.md) tématu. Vysvětlení, jak vám pomůže trasování ladění vaší aplikace, najdete v tématu [pomocí trasování řešení potíží s aplikace](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) tématu.  
  
- Protokolování zpráv umožňuje zobrazit, jak zprávy se zobrazují před i po přenosu. Další informace najdete v tématu [protokolování zpráv](../../../../docs/framework/wcf/diagnostics/message-logging.md) tématu.  
  
- Trasování událostí zapisuje události do protokolu událostí pro všechny hlavní problémy. Pak můžete v prohlížeči událostí k prozkoumání jakékoli anomálie. Další informace najdete v tématu [protokolování událostí](../../../../docs/framework/wcf/diagnostics/event-logging/index.md) tématu.  
  
- Čítače výkonu, které jsou vystaveny prostřednictvím monitorování výkonu umožňují sledovat vaše aplikace a stavu systému. Další informace najdete v tématu [čítače výkonu](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md) tématu.  
  
- <xref:System.ServiceModel.Configuration> Obor názvů umožňuje načíst konfigurační soubory a nastavit koncový bod služby ani klienta. Objektový model pro skript změn k velkému počtu aplikací můžete použít při aktualizace musí být nasazený na mnoha počítačích. Alternativně můžete použít [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) upravit nastavení konfigurace pomocí grafického uživatelského rozhraní průvodce. Další informace najdete v tématu [konfigurace aplikace](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md) tématu.  
  
- Rozhraní WMI umožňuje zjistit, které služby naslouchají na počítači a vazby, které se používají. Další informace najdete v tématu [pomocí Windows Management Instrumentation k diagnostice](../../../../docs/framework/wcf/diagnostics/wmi/index.md) tématu.  
  
 WCF také poskytuje několik nástrojů pro grafické uživatelské rozhraní a příkazový řádek, aby bylo snazší pro vás k vytvoření, nasazení a správě aplikací služby WCF. Další informace najdete v tématu [nástroje Windows Communication Foundation](../../../../docs/framework/wcf/tools.md). Například můžete použít [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) můžete vytvářet a upravovat nastavení konfigurace WCF pomocí průvodce, místo pro úpravy XML přímo. Můžete také použít [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) k zobrazení, seskupit a filtrovat zprávy trasování, aby můžete diagnostikovat, opravit a ověřte problémy se službami WCF.  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace vaší aplikace](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)
- [Nasazení služeb](../../../../docs/framework/wcf/diagnostics/deploying-services.md)
- [Přehled výjimek](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)
- [Protokolování událostí](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)
- [Protokolování zpráv](../../../../docs/framework/wcf/diagnostics/message-logging.md)
- [Editor konfigurace (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [Nástroj ServiceModelReg.exe](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)
- [Trasování](../../../../docs/framework/wcf/diagnostics/tracing/index.md)
- [Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)](../../../../docs/framework/wcf/diagnostics/wmi/index.md)
- [Čítače výkonu](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)
- [Nástroje Windows Communication Foundation](../../../../docs/framework/wcf/tools.md)
