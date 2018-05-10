---
title: Prohlížení protokolů zpráv
ms.date: 03/30/2017
ms.assetid: 3012fa13-f650-45fb-aaea-c5cca8c7d372
ms.openlocfilehash: 4fa205b52e3d19d2421d93297b5689422775f719
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/07/2018
---
# <a name="viewing-message-logs"></a>Prohlížení protokolů zpráv
Toto téma popisuje, jak můžete zobrazit protokoly zpráv.  
  
## <a name="viewing-message-logs-in-the-service-trace-viewer"></a>Při zobrazení zprávy přihlásí prohlížeče trasování služeb  
 Zprávu se transformuje, jako je zpracován WCF. Proto zprávu protokolována odráží jenom obsah zprávy v místě, které ho protokolu byla zaznamenána, není obsah v drátové síti.  
  
 Vzhledem k tomu, že výstup protokolování zpráv nemá žádný vztah k přenosu formát zprávy, vždy protokolování zpráv výstupy dekódované zprávy. Pokud jste nakonfigurovali protokolování správně zpráv, jakékoli zaznamenané zprávy musí být ve formátu prostého textu. Formát zprávy zaznamenané (prostý text) není například vliv použití kodéru zprávy v binární.  
  
 Výstup XmlWriterTraceListener je soubor, který obsahuje posloupnost fragmenty kódu XML. Byste měli vědět, že soubor není platný soubor XML. Je doporučeno používat [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) k zobrazení souborů protokolů zpráv. Další informace o tom, jak pomocí tohoto nástroje najdete v tématu [pomocí prohlížeče trasování služeb pro zobrazení korelační trasování a Poradce při potížích s](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md).  
  
 V prohlížeči trasování služby, zprávy jsou uvedeny v **zpráva** kartě. Zprávy, které způsobily, nebo jsou související s, chyba zpracování jsou vyznačené na žlutý (varování úroveň) nebo červený (úroveň chyb), v závislosti na závažnosti chyby. Dvojitým kliknutím na zprávu, na které se vyvolá trasování zpráv v kontextu požadavku na zpracování.  
  
> [!NOTE]
>  Pokud zpráva není hlavička, ne `<header/>` značky přihlášen.  
  
## <a name="viewing-messages-logged-by-a-client-a-relay-and-a-service"></a>Zobrazení zprávy zaznamenané klienta, předávání a služby  
 Klient, který odešle zprávu do předávání, které následně předá zprávu do služby může obsahovat vaše prostředí. Pokud je povoleno protokolování zpráv na všech tří umístění, a jsou všechny tři protokoly zprávy zobrazit v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) současně, bude nesprávně vykreslen výměny zpráv protokolu. Důvodem je, že `CorrelationId` a `ActivityId` v záhlaví zprávy nejsou pro každý pár send-receive jedinečné.  
  
 Chcete-li vyřešit tento problém můžete jednu z následujících metod.  
  
-   Zobrazit pouze dvě ze tří protokolů zpráv v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) kdykoli.  
  
-   Pokud musíte zobrazit všechny tři protokoly v [nástroj Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md) ve stejnou dobu, můžete upravit tak, že vytvoříte novou službu předávání přes <xref:System.ServiceModel.Channels.Message> instance. Tato instance musí být kopie obsahu příchozí zprávy, včetně všech záhlaví s výjimkou `ActivityId` a `Action` hlavičky. Následující příklad kódu ukazuje, jak to udělat.  
  
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
  
## <a name="exceptional-cases-for-inaccurate-message-logging-content"></a>Výjimečných případech pro obsah protokolování nesprávné zprávy  
 Za těchto podmínek zprávy protokolována nemusí být přesné reprezentace datového proudu octet přítomen v drátové síti.  
  
-   Pro BasicHttpBinding, se zaznamenávají obálky hlavičky pro příchozí zprávy v / adresování/žádný obor názvů.  
  
-   Může být neshoda prázdné znaky.  
  
-   Pro příchozí zprávy může být reprezentován prázdné prvky jinak. Například \<značka >\</značka > místo \<značka / >  
  
-   Když je zakázáno známé PII protokolování buď ve výchozím nastavení nebo explicitní nastavení enableLoggingKnownPii = "true".  
  
-   Kódování je povolený pro převod na UTF-8.  
  
## <a name="see-also"></a>Viz také  
 [Prohlížeč trasování služeb (SvcTraceViewer.exe)](../../../../docs/framework/wcf/service-trace-viewer-tool-svctraceviewer-exe.md)  
 [Použití prohlížeče trasování služeb k zobrazení korelovaných tras a řešení problémů](../../../../docs/framework/wcf/diagnostics/tracing/using-service-trace-viewer-for-viewing-correlated-traces-and-troubleshooting.md)  
 [Protokolování zpráv](../../../../docs/framework/wcf/diagnostics/message-logging.md)
