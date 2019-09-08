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
ms.openlocfilehash: dfe169cd6c8d9a643e90e98fc9f22bf116d4335f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795986"
---
# <a name="administration-and-diagnostics"></a>Správa a diagnostika
Windows Communication Foundation (WCF) poskytuje bohatou sadu funkcí, které vám pomůžou monitorovat různé fáze životního cyklu aplikace. Například můžete použít konfiguraci k nastavení služeb a klientů při nasazení. WCF zahrnuje velkou sadu čítačů výkonu, které vám pomůžou posoudit výkon aplikace. WCF také zpřístupňuje kontrolní data služby za běhu prostřednictvím poskytovatele WCF rozhraní WMI (Windows Management Instrumentation) (WMI). V případě, že dojde k chybě nebo pokud aplikace nefunguje správně, můžete použít protokol událostí a zjistit, jestli nedošlo k nějaké významné chybě. Můžete také použít protokolování a trasování zpráv, abyste viděli, jaké události se v aplikaci děje od začátku do konce. Tyto funkce pomáhají vývojářům a odborníkům v oblasti IT řešit problémy s aplikací WCF, když se nechová správně.  
  
> [!NOTE]
> Pokud dochází k chybám bez konkrétních podrobných informací, měli byste povolit `includeExceptionDetailInFaults` atribut [ \<serviceDebug >](../../configure-apps/file-schema/wcf/servicedebug.md) konfiguračního prvku. Tato možnost dává pokyn WCF k posílání podrobností o výjimce klientům, což vám umožní detekovat mnoho běžných problémů bez nutnosti pokročilejší diagnostiky. Další informace najdete v tématu [odesílání a příjem chyb](../sending-and-receiving-faults.md).  
  
## <a name="diagnostics-features-provided-by-wcf"></a>Diagnostické funkce poskytované službou WCF  
 WCF poskytuje následující funkce diagnostiky:  
  
- Koncové trasování poskytuje data instrumentace pro řešení potíží s aplikací bez použití ladicího programu. WCF sleduje výstupy pro milníky procesů a také chybové zprávy. To může zahrnovat otevření objektu pro vytváření kanálů nebo posílání a přijímání zpráv hostitelem služby. Trasování lze povolit pro spuštěnou aplikaci, aby mohla monitorovat její průběh. Další informace najdete v tématu věnovaném [trasování](./tracing/index.md) . Chcete-li pochopit, jak lze pomocí trasování ladit aplikaci, přečtěte si téma [použití trasování pro řešení potíží s aplikací](./tracing/using-tracing-to-troubleshoot-your-application.md) .  
  
- Protokolování zpráv umožňuje zobrazit, jak budou zprávy vypadat před přenosem i po něm. Další informace najdete v tématu [protokolování zpráv](message-logging.md) .  
  
- Trasování událostí zapisuje události do protokolu událostí pro případné významné problémy. Pak můžete použít Prohlížeč událostí k prohlédnutí všech neobvyklých. Další informace najdete v tématu [protokolování událostí](./event-logging/index.md) .  
  
- Čítače výkonu vystavené prostřednictvím nástroje sledování výkonu vám umožní monitorovat stav aplikace a systému. Další informace najdete v tématu [čítače výkonu](./performance-counters/index.md) .  
  
- <xref:System.ServiceModel.Configuration> Obor názvů umožňuje načíst konfigurační soubory a nastavit koncový bod služby nebo klienta. Objektový model můžete použít ke skriptování změn v mnoha aplikacích v případě, že aktualizace musí být nasazeny do mnoha počítačů. Alternativně můžete pomocí [nástroje Configuration Editor (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md) upravit nastavení konfigurace pomocí Průvodce grafickým uživatelským rozhraním. Další informace najdete v tématu [Konfigurace aplikace](configuring-your-application.md) .  
  
- Rozhraní WMI umožňuje zjistit, jaké služby naslouchá na počítači, a používané vazby. Další informace najdete v tématu [použití rozhraní WMI (Windows Management Instrumentation) pro diagnostiku](./wmi/index.md) .  
  
 WCF také nabízí několik nástrojů grafického uživatelského rozhraní a nástrojů příkazového řádku, které usnadňují vytváření, nasazování a správu aplikací WCF. Další informace najdete v tématu [Windows Communication Foundation Tools](../tools.md). Například můžete použít [nástroj Editor konfigurace (SvcConfigEditor. exe)](../configuration-editor-tool-svcconfigeditor-exe.md) k vytvoření a úpravám nastavení konfigurace WCF pomocí Průvodce místo přímé úpravy XML. Můžete také použít [Nástroj Prohlížeč trasování služby (SvcTraceViewer. exe)](../service-trace-viewer-tool-svctraceviewer-exe.md) k zobrazení, seskupení a filtrování zpráv trasování, abyste mohli diagnostikovat, opravovat a ověřovat problémy se službami WCF.  
  
## <a name="see-also"></a>Viz také:

- [Konfigurace vaší aplikace](configuring-your-application.md)
- [Nasazení služeb](deploying-services.md)
- [Přehled výjimek](./exceptions-reference/index.md)
- [Protokolování událostí](./event-logging/index.md)
- [Protokolování zpráv](message-logging.md)
- [Editor konfigurace (SvcConfigEditor.exe)](../configuration-editor-tool-svcconfigeditor-exe.md)
- [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../service-trace-viewer-tool-svctraceviewer-exe.md)
- [Nástroj ServiceModelReg.exe](servicemodel-registration-tool.md)
- [Trasování](./tracing/index.md)
- [Diagnostika prostřednictvím rozhraní WMI (Windows Management Instrumentation)](./wmi/index.md)
- [Čítače výkonu](./performance-counters/index.md)
- [Nástroje Windows Communication Foundation](../tools.md)
