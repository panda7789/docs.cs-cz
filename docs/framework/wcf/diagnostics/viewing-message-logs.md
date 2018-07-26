---
title: Prohlížení protokolů zpráv
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: 025d4020002a56deb9d5b8a2fe628f50cabad4d3
ms.sourcegitcommit: 2d8b7488d94101b534ca3e9780b1c1e840233405
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/23/2018
ms.locfileid: "39198507"
---
# <a name="viewing-message-logs"></a>Prohlížení protokolů zpráv
Toto téma popisuje, jak můžete zobrazit protokoly zpráv.  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a>Při zobrazení zprávy přihlásí prohlížeče trasování služeb  
 Zpráva se bude transformovat, jako je zpracován programovacím modelem WCF. Proto zprávu přihlašováno odráží jenom obsah zprávy v okamžiku, kdy byla zapsána, není obsah na lince.  
  
 Protože výstup protokolování zpráv nemá žádný vztah k přenosu formát zprávy, vždy protokolování zpráv výstupy dekódovanou zprávu. Pokud jste nakonfigurovali správně protokolování zpráv, všechny Protokolovaná zpráva musí být ve formátu prostého textu. Například formát (prostý text) zaznamenaných zpráv nemá vliv využití kodér binárních zpráv.  
  
 Výstup XmlWriterTraceListener je soubor, který obsahuje posloupnost fragmentů XML. Byste měli vědět, že soubor není platný soubor XML. Doporučuje se, že používáte [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) Chcete-li zobrazit soubory protokolu zpráv. Další informace o tom, jak pomocí tohoto nástroje naleznete v tématu [pomocí prohlížeče trasování služeb k zobrazení korelovaných trasování a řešení potíží](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 Zprávy jsou v prohlížeče trasování služeb uvedené v **zpráva** kartu. Zprávy, které způsobily, nebo jsou související s, Chyba při zpracování jsou zvýrazněné žlutou barvou (úroveň upozornění) nebo červený (úroveň chyb), v závislosti na závažnosti chyby. Dvojitým kliknutím na zprávu zobrazí trasování zpráv v rámci zpracování požadavku.  
  
> [!NOTE]
>  Pokud zpráva neobsahuje žádné záhlaví `<header/>` značka je zaznamenána.  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a>Zobrazení zprávy zaprotokolované pomocí klienta, se při předávání a služby  
 Vaše prostředí může obsahovat klienta, který odešle zprávu do přenos, který následně předá zprávu do služby. Při protokolování zpráv je povolená na všech třech umístěních, a všechny tři protokoly zpráv jsou zobrazeny v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) současně, bude nesprávně vykreslit výměny zpráv protokolu. Je to proto, `CorrelationId` a `ActivityId` v záhlaví zprávy nejsou jedinečné pro každý pár send-receive.  
  
 Chcete-li vyřešit tento problém můžete použít jednu z následujících metod.  
  
-   Zobrazit pouze dvě ze tří protokolů zpráv v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) kdykoli.  
  
-   Pokud si musí zobrazit všechny tři protokoly v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ve stejnou dobu, můžete upravit se službou Relay vytvoříte tak, že vytvoříte nový <xref:System.ServiceModel.Channels.Message> instance. Tato instance musí být kopie tělo z příchozí zprávy a navíc všechny hlavičky s výjimkou `ActivityId` a `Action` záhlaví. Následující příklad kódu ukazuje, jak to provést.  
  
```  
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
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a>Výjimečných případech nesprávné zpráva protokolování obsahu  
 Za následujících podmínek nemusí být právě protokolované zprávy přesnou reprezentací octet stream k dispozici na lince.  
  
-   BasicHttpBinding, hlavičky obálky se protokolují pro příchozí zprávy v / adresování/žádný obor názvů.  
  
-   Prázdné znaky může lišit.  
  
-   Pro příchozí zprávy může být jinak reprezentována prázdné prvky. Například \<značka >\</označit > namísto \<značky / >  
  
-   Když je zakázáno přihlášení známého PII, buď ve výchozím nastavení nebo explicitní nastavení enableLoggingKnownPii = "true".  
  
-   Kódování je povolená pro transformaci na UTF-8.  
  
## <a name="see-also"></a>Viz také  
 [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Protokolování zpráv](../../../../docs/framework/wcf/diagnostics/message-logging.md)
