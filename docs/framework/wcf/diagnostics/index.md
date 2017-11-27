---
title: "Správa a diagnostika"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, diagnostics
- Windows Communication Foundation, administration
- diagnostics [WCF]
- WCF, diagnostics
- administration [WCF]
- WCF, administration
ms.assetid: 34c81c08-0e0f-4fbc-9ae8-91948640ee43
caps.latest.revision: "19"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2f103570cf7d94a9ac6256f3db991c44767fa7c4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="administration-and-diagnostics"></a>Správa a diagnostika
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]poskytuje bohatou sadu funkcí, které umožňují monitorovat různých fázích životního aplikace. Například můžete použít konfiguraci nastavení služeb a klientů v nasazení. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]obsahuje velké sady čítačů výkonu můžete měřit výkon vaší aplikace. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]taky zpřístupňuje dat kontroly služby za běhu prostřednictvím [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zprostředkovatele Windows Management Instrumentation (WMI). Při vyskytne chyba nebo spustí funguje nesprávně aplikace, můžete zobrazit, pokud nic významné došlo k chybě v protokolu událostí. Můžete také použít protokolování zpráv a trasování a zjistěte, jaké události jsou situaci klient server ve vaší aplikaci. Tyto funkce pomůže vývojáře a IT odborníky řešení potíží [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace při nepracuje správně.  
  
> [!NOTE]
>  Pokud se vám chyb s nejsou žádné konkrétní podrobné informace, měli byste povolit `includeExceptionDetailInFaults` atribut [ \<serviceDebug >](../../../../docs/framework/configure-apps/file-schema/wcf/servicedebug.md) konfigurační prvek. Tím se nastaví [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Odeslat podrobnosti výjimky pro klienty, které umožňuje detekovat mnoho běžných problémů bez nutnosti pokročilejší diagnostiku. Další informace najdete v tématu [odesílání a přijímání chyb](../../../../docs/framework/wcf/sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>Diagnostické funkce poskytované službou WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poskytuje následující funkce diagnostics:  
  
-   Trasování začátku do konce poskytuje data instrumentace pro řešení potíží s aplikace bez použití ladicí program. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]výstupy trasování pro proces milníky, jakož i chybové zprávy. To může zahrnovat otevření kanálu nebo odesílání a přijímání zpráv pomocí hostitele služby. Trasování je možné zapnout pro běžící aplikaci monitorovat její postup. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][trasování](../../../../docs/framework/wcf/diagnostics/tracing/index.md) tématu. Abyste pochopili, jak můžete trasování ladění aplikace, najdete v článku [pomocí trasování řešení vaše aplikace](../../../../docs/framework/wcf/diagnostics/tracing/using-tracing-to-troubleshoot-your-application.md) tématu.  
  
-   Protokolování zpráv umožňuje zobrazit vzhled zprávy před a po přenosu. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][protokolování zpráv](../../../../docs/framework/wcf/diagnostics/message-logging.md) tématu.  
  
-   Události trasování událostí se zapisují do protokolu událostí pro potíže hlavní. Potom můžete v prohlížeči událostí k prozkoumání abnormality. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][protokolování událostí](../../../../docs/framework/wcf/diagnostics/event-logging/index.md) tématu.  
  
-   Čítače výkonu, které jsou k dispozici prostřednictvím nástroje Sledování výkonu umožňují sledovat vaše aplikace a stavu systému. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][čítače výkonu](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md) tématu.  
  
-   <xref:System.ServiceModel.Configuration> Obor názvů umožňuje načíst konfigurační soubory a nastavit koncový bod služby nebo klienta. Model objektu do skriptu změny mnoho aplikací můžete použít při aktualizace musí být nasazený na mnoha počítačích. Alternativně můžete použít [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) upravit konfigurační nastavení pomocí průvodce s grafickým uživatelským rozhraním. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][konfigurace vaše aplikace](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md) tématu.  
  
-   Rozhraní WMI umožňuje zjistit, jaké služby jsou naslouchá na počítači a vazby, které jsou používány. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][pomocí rozhraní Windows Management Instrumentation pro diagnostiku](../../../../docs/framework/wcf/diagnostics/wmi/index.md) tématu.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]také poskytuje několik grafického uživatelského rozhraní a nástroje příkazového řádku snadno vytvářet, nasazovat a spravovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Nástroje služby Windows Communication Foundation](../../../../docs/framework/wcf/tools.md). Například můžete použít [nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md) můžete vytvářet a upravovat [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] konfigurační nastavení pomocí průvodce, místo přímou úpravou kódu XML. Můžete také [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) Pokud chcete zobrazit, skupiny a filtrovat zprávy trasování tak, aby lze diagnostikovat, opravte a zkontrolujte problémy s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby.  
  
## <a name="see-also"></a>Viz také  
 [Konfigurace aplikace](../../../../docs/framework/wcf/diagnostics/configuring-your-application.md)  
 [Nasazení služeb](../../../../docs/framework/wcf/diagnostics/deploying-services.md)  
 [Přehled výjimek](../../../../docs/framework/wcf/diagnostics/exceptions-reference/index.md)  
 [Protokolování událostí](../../../../docs/framework/wcf/diagnostics/event-logging/index.md)  
 [Protokolování zpráv](../../../../docs/framework/wcf/diagnostics/message-logging.md)  
 [Nástroj Configuration Editor (SvcConfigEditor.exe)](../../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)  
 [Nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Nástroj ServiceModelReg.exe](../../../../docs/framework/wcf/diagnostics/servicemodel-registration-tool.md)  
 [Trasování](../../../../docs/framework/wcf/diagnostics/tracing/index.md)  
 [Pomocí rozhraní Windows Management Instrumentation pro diagnostiku](../../../../docs/framework/wcf/diagnostics/wmi/index.md)  
 [Čítače výkonu](../../../../docs/framework/wcf/diagnostics/performance-counters/index.md)  
 [Nástroje služby Windows Communication Foundation](../../../../docs/framework/wcf/tools.md)
