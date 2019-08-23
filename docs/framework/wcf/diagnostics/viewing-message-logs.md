---
title: Prohlížení protokolů zpráv
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: c926833a48331f191b6dcc3323f0dfda329b7014
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968673"
---
# <a name="viewing-message-logs"></a>Prohlížení protokolů zpráv
Toto téma popisuje, jak můžete zobrazit protokoly zpráv.  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a>Zobrazení protokolů zpráv v prohlížeči trasování služby  
 Zpráva bude transformovaná tak, jak je zpracována službou WCF. Proto se zaprotokolovaná zpráva odrážejí pouze obsah zprávy v okamžiku, kdy byl protokol, nikoli obsah na drátě.  
  
 Vzhledem k tomu, že výstup protokolování zpráv nemá žádný vztah k formátu přenosu zprávy, bude protokolování zpráv vždy výstupem dekódování zprávy. Pokud jste správně nakonfigurovali protokolování zpráv, všechny protokolované zprávy by měly být v prostém textu. Například formát (prostý text) protokolovaných zpráv není ovlivněn využitím binárního kodéru zpráv.  
  
 Výstupem XmlWriterTraceListener je soubor, který obsahuje sekvenci fragmentů XML. Měli byste si uvědomit, že soubor není platný soubor XML. Pro zobrazení souborů protokolu zpráv se doporučuje použít [Nástroj pro prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) . Další informace o použití tohoto nástroje najdete v tématu [použití prohlížeče trasování služby pro zobrazení korelačních trasování a odstraňování potíží](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 V prohlížeči trasování služby jsou zprávy uvedeny na kartě **zpráva** . Zprávy, které způsobily nebo souvisejí s, se chyba zpracování zvýrazní žlutě (úroveň upozornění) nebo červenou (úroveň chyby) v závislosti na závažnosti chyby. Dvojím kliknutím na zprávu se zobrazí trasování zprávy v kontextu žádosti o zpracování.  
  
> [!NOTE]
> Pokud zpráva neobsahuje hlavičku, není protokolována `<header/>` žádná značka.  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a>Zobrazení zpráv protokolovaných klientem, přenosem a službou  
 Vaše prostředí může obsahovat klienta, který pošle zprávu do přenosu, který následně přepošle zprávu službě. Pokud je povoleno protokolování zpráv na všech třech místech a všechny tři protokoly zpráv se zobrazují současně v [nástroji Service Trace Viewer (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) současně, budou se zprávy o výměně protokolu zpráv nesprávně vykreslovat. Důvodem je, že `CorrelationId` a `ActivityId` v záhlaví zprávy nejsou jedinečné pro každou dvojici Send-Receive.  
  
 K vyřešení tohoto problému můžete použít některou z následujících metod.  
  
- V [nástroji Prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) si kdykoli zobrazit jenom dva ze tří protokolů zpráv.  
  
- Pokud je nutné zobrazit všechny tři protokoly v [nástroji Prohlížeč trasování služby (SvcTraceViewer. exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) současně, můžete službu Relay změnit vytvořením nové <xref:System.ServiceModel.Channels.Message> instance. Tato instance by měla být kopií textu příchozí zprávy a všech hlaviček kromě `ActivityId` hlaviček a. `Action` Následující příklad kódu ukazuje, jak to provést.  
  
```csharp
Message outgoingMessage = Message.CreateMessage(incomingMessage.Version, incomingMessage.Headers.Action, incomingMessage.GetReaderAtBodyContents());  
  
for (int i = 0; i < incomingMessage.Headers.Count; i++)  
{  
   if (incomingMessage.Headers[i].Name.Equals("ActivityId", StringComparison.InvariantCultureIgnoreCase) ||  
incomingMessage.Headers[i].Name.Equals("Action", StringComparison.InvariantCultureIgnoreCase))  
   {  
      continue;  
    }  
    outgoingMessage.Headers.CopyHeaderFrom(incomingMessage, i);  
}  
```  
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a>Výjimečné případy pro nepřesný obsah protokolování zpráv  
 V následujících podmínkách nemusí být protokolovaná zpráva přesným znázorněním oktetu přítomného na lince.  
  
- Pro BasicHttpBinding se pro příchozí zprávy v oboru názvů/Addressing/None protokolují hlavičky obálek.  
  
- Nelze neshodovat prázdné znaky.  
  
- Pro příchozí zprávy mohou být prázdné prvky reprezentovány jinak. Například \<Tag >\</Tag > namísto \<Tag/>  
  
- Je-li známé protokolování PII zakázáno buď ve výchozím nastavení, nebo explicitním nastavením enableLoggingKnownPii = "true".  
  
- Kódování je povoleno pro transformaci do UTF-8.  
  
## <a name="see-also"></a>Viz také:

- [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)
- [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)
- [Protokolování zpráv](../../../../docs/framework/wcf/diagnostics/message-logging.md)
