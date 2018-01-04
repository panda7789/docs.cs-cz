---
title: "Protokol spolehlivého zasílání zpráv verze 1.1"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 67df8b539109d7e4dafcbc42ad7679643767021a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="reliable-messaging-protocol-version-11"></a>Protokol spolehlivého zasílání zpráv verze 1.1
Toto téma popisuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] podrobnosti implementace protokolu WS-ReliableMessaging. února 2007 (verze 1.1) protokolu potřebné pro vzájemná spolupráce pomocí přenosového protokolu HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]dodržuje specifikaci WS-ReliableMessaging s omezení a objasnění, která jsou popsané v tomto tématu. Poznámka: verze 1.1 protokolu WS-ReliableMessaging je implementováno začínající [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].  
  
 Protokolu WS-ReliableMessaging. února 2007 protokol je implementována ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Pro usnadnění práce tématu používá Tyhle role:  
  
-   Iniciátor: Klienta, která zahájí vytváření sekvence WS-spolehlivé zprávy.  
  
-   Respondér: Služba, která přijímá požadavky je iniciátor.  
  
 Tento dokument používá předpony a obory názvů v následující tabulce.  
  
|Předpona|Obor názvů|  
|-|-|  
|Správce systémových prostředků|http://docs.oasis-open.org/ws-RX/wsrm/200702|  
|netrm|http://schemas.microsoft.com/ws/2006/05/RM|  
|s|http://www.w3.org/2003/05/SOAP-Envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/Addressing|  
|wsse|http://docs.oasis-open.org/WSS/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|wsrmp|http://docs.oasis-open.org/ws-RX/wsrmp/200702|  
|netrmp|http://schemas.microsoft.com/ws-RX/wsrmp/200702|  
|WSP|(WS-Policy 1.2 nebo WS-Policy 1.5)|  
  
## <a name="messaging"></a>Zasílání zpráv  
  
### <a name="sequence-creation"></a>Vytvoření pořadí  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje `CreateSequence` a `CreateSequenceResponse` pořadí zprávy a pokuste se vytvořit spolehlivé zasílání zpráv. Platí následující omezení:  
  
-   B1101: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor používá koncový bod odkaz na stejné jako `CreateSequence` zprávy `ReplyTo`, `AcksTo` a `Offer/Endpoint`.  
  
-   R1102: `AcksTo`, `ReplyTo` a `Offer/Endpoint` v odkazuje na koncový bod `CreateSequence` zprávy musí mít hodnoty adres s identické řetězcové vyjádření tak, že budou odpovídat octet-wise.  
  
    -   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér ověřuje, že část identifikátoru URI `AcksTo`, `ReplyTo` a `Endpoint` odkazy koncového bodu jsou identické před vytvořením sekvenci.  
  
-   R1103: `AcksTo`, `ReplyTo` a `Offer/Endpoint` odkazy na koncový bod v `CreateSequence` zprávy musí mít stejnou sadu parametrů odkaz.  
  
    -   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]nevynucuje, ale předpokládá, které se odkazují parametry `AcksTo`, `ReplyTo` a `Offer/Endpoint` koncový bod odkazuje na `CreateSequence` jsou identické a používá parametry odkaz z `ReplyTo` reference koncového bodu pro konverzace pořadí zprávy a potvrzení.  
  
-   B1104: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor negeneruje nepovinný `Expires` nebo `Offer/Expires` element v `CreateSequence` zprávy.  
  
-   B1105: Při přístupu k `CreateSequence` zpráva, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér používá `Expires` hodnotu ve `CreateSequence` element jako `Expires` hodnotu `CreateSequenceResponse` element. V opačném [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér přečte a ignoruje `Expires` a `Offer/Expires` hodnoty.  
  
-   B1106: Při přístupu k `CreateSequenceResponse` zpráv, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor načte volitelné `Expires` hodnotu, ale nepoužívá se.  
  
-   B1107: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor a respondér vždy generovat nepovinný `IncompleteSequenceBehavior` element v `CreateSequence/Offer` a `CreateSequenceResponse` elementy.  
  
-   B1108: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá jenom `DiscardFollowingFirstGap` a `NoDiscard` hodnoty ve `IncompleteSequenceBehavior` elementu.  
  
    -   Využívá WS-ReliableMessaging `Offer` mechanismus pro vytvoření dvou komunikaci korelační pořadí, které vytvářejí relaci.  
  
-   B1109: Pokud `CreateSequence` obsahuje `Offer` elementu, jedním ze způsobů [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér odmítne nabízený pořadí podle reagovat se `CreateSequenceResponse` bez `Accept` elementu.  
  
-   B1110: Pokud spolehlivého zasílání zpráv respondér odmítne nabízený pořadí, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor závady nově vytvořeným pořadí.  
  
-   B1111: Pokud `CreateSequence` neobsahuje `Offer` prvek, obousměrný [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér odmítne nabízený pořadí podle reagovat se `CreateSequenceRefused` selhání.  
  
-   R1112: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, `[address]` vlastnost `CreateSequenceResponse/Accept/AcksTo` reference koncového bodu musí odpovídat cílový identifikátor URI z `CreateSequence` zpráva bajtu bajtů.  
  
-   R1113: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, musí se poslat všechny zprávy na obou pořadí předávaných z iniciátoru k příjemce, na odkaz na stejný koncový bod.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]pomocí protokolu WS-ReliableMessaging zřizuje spolehlivé relace mezi iniciátoru a odpovídající počítač. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Implementaci protokolu WS-ReliableMessaging poskytuje spolehlivé relace jednosměrné, požadavku a odpovědi a plně duplexní režim vzory pro zasílání zpráv. WS-ReliableMessaging `Offer` mechanismus na `CreateSequence` a `CreateSequenceResponse` umožňuje vytvořit dva korelační konverzace pořadí a poskytuje protokol relace, který je vhodný pro všechny zprávy koncové body. Protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje záruku zabezpečení pro takové relace včetně ochrany začátku do konce relace integritu, je potřeba zajistit, aby přicházejí zprávy určené pro stejné strany na stejný cíl. To také umožňuje "Prasátko zálohování" pořadí potvrzení u zpráv s aplikací. Proto se týkají omezení R1102, R1112 a R1113 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 Příklad `CreateSequence` zprávy.  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:MessageID>  
    <wsa:ReplyTo>  
        <wsa:Address>http://Business456.com/clientA</wsa:Address>   
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequence>  
      <wsrm:AcksTo>  
        <wsa:Address>http://Business456.com/clientA</wsa:Address>  
      </wsrm:AcksTo>  
      <wsrm:Offer>  
        <wsrm:Identifier>urn:uuid:066b4730-fc82-458a-a5c1-210be4fb4e4e</wsrm:Identifier>  
        <wsrm:Endpoint>  
          <wsa:Address>http://Business456.com/clientA</wsa:Address>  
        </wsrm:Endpoint>  
        <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>  
      </wsrm:Offer>  
    </wsrm:CreateSequence>  
  </s:Body>  
</s:Envelope>  
```  
  
 Příklad `CreateSequenceResponse` zprávy.  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CreateSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:949cca61-8813-42ff-ab33-18d9e3fa82fa</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CreateSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:IncompleteSequenceBehavior>DiscardFollowingFirstGap</wsrm:IncompleteSequenceBehavior>  
      <wsrm:Accept>  
        <wsrm:AcksTo>  
          <wsa:Address>http://BusinessABC.com/serviceA</wsa:Address>  
        </wsrm:AcksTo>  
      </wsrm:Accept>  
    </wsrm:CreateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="closing-a-sequence"></a>Zavřením sekvenci  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]používá `CloseSequence` a `CloseSequenceResponse` zprávy pro vypnutí spolehlivé zasílání zpráv spouštěná zdroje. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Spolehlivé zasílání zpráv cílové neiniciuje vypnutí a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spolehlivé zasílání zpráv zdroj nepodporuje vypnutí spouštěná cílové spolehlivé zasílání zpráv. Platí následující omezení:  
  
-   B1201: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vždycky odešle zdroj spolehlivé zasílání zpráv `CloseSequence` zpráva vypnout sekvenci.  
  
-   B1202: Zdroji spolehlivé zasílání zpráv čeká na potvrzení plný rozsah pořadí zprávy před odesláním `CloseSequence` zprávy.  
  
-   B1203: Zdroji spolehlivé zasílání zpráv vždy obsahuje volitelné `LastMsgNumber` element Pokud sekvenci neobsahuje zprávy.  
  
-   R1204: Cílový spolehlivé zasílání zpráv nesmí iniciovat vypnutí odesláním `CloseSequence` zprávy.  
  
-   B1205: po přijetí `CloseSequence` zpráv, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spolehlivé zasílání zpráv zdroj považuje pořadí nekompletní a odešle chybu.  
  
 Příklad `CloseSequence` zprávy.  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:MessageID>  
    <wsa:ReplyTo>  
      <wsa:Address>http://Business456.com/clientA</wsa:Address>  
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CloseSequence>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>  
    </wsrm:CloseSequence>  
  </s:Body>  
</s:Envelope>  
Example CloseSequenceResponse message:  
<s:Envelope>  
  <s:Header>  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>  
      <wsrm:Final></wsrm:Final>  
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/CloseSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:6ce1d4c3-e1c1-474f-a8c9-4210e37f7877</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">http://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:CloseSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
    </wsrm:CloseSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequence-termination"></a>Pořadí ukončení  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]především používá `TerminateSequence/TerminateSequenceResponse` handshake po dokončení `CloseSequence/CloseSequenceResponse` metody handshake. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Spolehlivé zasílání zpráv cílové neiniciuje ukončení a zdroji spolehlivé zasílání zpráv nepodporuje ukončení spouštěná cílové spolehlivé zasílání zpráv. Platí následující omezení:  
  
-   B1301: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor odesílá jenom `TerminateSequence` zpráva po úspěšném dokončení `CloseSequence/CloseSequenceResponse` metody handshake.  
  
-   R1302: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ověří, jestli `LastMsgNumber` element je konzistentní napříč všemi `CloseSequence` a `TerminateSequence` zprávy pro daného pořadí. To znamená, že `LastMsgNumber` buď není přítomen na všech `CloseSequence` a `TerminateSequence` zprávy, nebo je přítomen a na všechny stejné `CloseSequence` a `TerminateSequence` zprávy.  
  
-   B1303: Při přijímání `TerminateSequence` zprávy po `CloseSequence/CloseSequenceResponse` handshake, odpoví cílové spolehlivé zasílání zpráv `TerminateSequenceResponse` zprávy. Protože má zdroj spolehlivé zasílání zpráv konečné potvrzení před odesláním `TerminateSequence` zprávy, cílový spolehlivé zasílání zpráv zná bez nepochybně, že je pořadí skončí a uvolní prostředky okamžitě.  
  
-   B1304: Při přijímání `TerminateSequence` zpráv starších než `CloseSequence/CloseSequenceResponse` handshake, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spolehlivé zasílání zpráv cílové odpoví `TerminateSequenceResponse` zprávy. Pokud cílový spolehlivé zasílání zpráv zjistí, že neexistují žádné nekonzistence v pořadí, cílový spolehlivé zasílání zpráv čeká na dobu zadané cílové aplikace před opětovného získání prostředků, aby klient riziko pro příjem konečné potvrzení. Jinak cílové spolehlivé zasílání zpráv okamžitě získá prostředky a označuje cílové aplikace, že je pořadí končí nejistých zobrazením `Faulted` událostí.  
  
 Příklad `TerminateSequence` zprávy.  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequence</wsa:Action>  
    <wsa:MessageID>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:MessageID>  
    <wsa:ReplyTo>  
      <wsa:Address>http://Business456.com/clientA</wsa:Address>  
    </wsa:ReplyTo>  
    <wsa:To s:mustUnderstand="1">http://BusinessABC.com/serviceA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:TerminateSequence>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:LastMsgNumber>30</wsrm:LastMsgNumber>  
      </wsrm:TerminateSequence>  
  </s:Body>  
</s:Envelope>  
Example TerminateSequenceResponse message:  
<s:Envelope>  
  <s:Header>  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Lower="1" Upper="30"></wsrm:AcknowledgementRange>  
      <wsrm:Final></wsrm:Final>  
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    <wsa:Action s:mustUnderstand="1">http://docs.oasis-open.org/ws-rx/wsrm/200702/TerminateSequenceResponse</wsa:Action>  
    <wsa:RelatesTo>urn:uuid:3597a398-4f3c-40f4-9335-8f1515572fdf</wsa:RelatesTo>  
    <wsa:To s:mustUnderstand="1">://Business456.com/clientA</wsa:To>  
  </s:Header>  
  <s:Body>  
    <wsrm:TerminateSequenceResponse>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
    </wsrm:TerminateSequenceResponse>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="sequences"></a>Sekvence  
 Následuje seznam omezení, která se týkají pořadí:  
  
-   B1401:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje a přistupuje k pořadová čísla vyšší než `xs:long`na maximální hodnotu (včetně), 9223372036854775807.  
  
 Příklad `Sequence` záhlaví.  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a>Žádost o potvrzení  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]používá `AckRequested` záhlaví jako mechanismus keep-alive.  
  
 Příklad `AckRequested` záhlaví.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a>Bylo potvrzení SequenceAcknowledgement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]používá mechanismus "Prasátko zpětným" pro potvrzení pořadí, které jsou součástí služby WS-spolehlivé zasílání zpráv. Platí následující omezení:  
  
-   R1601: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` záhlaví může být součástí jakékoli aplikace zprávy předaných zamýšlený příjemce. Vzdálený koncový bod musí být schopni přistupovat zařazována složená `SequenceAcknowledgement` záhlaví.  
  
-   B1602: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] negeneruje `SequenceAcknowledgement` hlavičky, které obsahují `Nack` elementy. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]ověří, že každý `Nack` elementu obsahuje pořadové číslo, ale jinak ignoruje `Nack` elementu a hodnotu.  
  
 Příklad `SequenceAcknowledgement` záhlaví.  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging chyb  
 Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementaci protokolu WS-ReliableMessaging chyb. Platí následující omezení:  
  
-   B1701: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] negeneruje `MessageNumberRollover` chyb.  
  
-   B1702: Přes SOAP 1.2, pokud koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje vnořený `CreateSequenceRefused` poruch dílčí, `netrm:ConnectionLimitReached`, jak je znázorněno v následujícím příkladu.  
  
```xml  
<s:Envelope>  
  <s:Header>  
    <wsa:Action>http://docs.oasis-open.org/ws-rx/wsrm/200702/fault</wsa:Action>  
  </s:Header>  
  <s:Body>  
    <s:Fault>  
      <s:Code>  
        <s:Value>s:Receiver</s:Value>  
        <s:Subcode>  
          <s:Value>wsrm:CreateSequenceRefused</s:Value>  
          <s:Subcode>  
            <s:Value>netrm:ConnectionLimitReached</s:Value>  
          </s:Subcode>  
        </s:Subcode>  
      </s:Code>  
      <s:Reason>  
        <s:Text xml:lang="en">Server 'http://BusinessABC.com/serviceA' is too busy to process this request. Try again later.</s:Text>  
      </s:Reason>  
    </s:Fault>  
  </s:Body>  
</s:Envelope>  
```  
  
### <a name="ws-addressing-faults"></a>Adresování WS chyb  
 Protože WS-ReliableMessaging používá adresování WS [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementaci protokolu WS-ReliableMessaging může vygenerovat a přenést WS-Addressing chyb. Tato část zahrnuje WS-Addressing chyb, který [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] explicitně generuje a odesílá ve vrstvě protokolu WS-ReliableMessaging:  
  
-   B1801:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje a odesílá `Message Addressing Header Required` poruch, když je splněna jedna z následujících akcí:  
  
    -   A `CreateSequence`, `CloseSequence` nebo `TerminateSequence` chybí zpráva `MessageId` záhlaví.  
  
    -   A `CreateSequence`, `CloseSequence` nebo `TerminateSequence` chybí zpráva `ReplyTo` záhlaví.  
  
    -   A `CreateSequenceResponse`, `CloseSequenceResponse`, nebo `TerminateSequenceResponse` chybí zpráva `RelatesTo` záhlaví.  
  
-   B1802:[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje a odesílá `Endpoint Unavailable` selhání označíte, neexistuje žádný koncový bod naslouchání, který může zpracovat pořadí podle zkoumání adresování hlavičky v `CreateSequence` zprávy.  
  
## <a name="protocol-composition"></a>Protokol složení  
  
### <a name="composition-with-ws-addressing"></a>Složení s adresováním WS  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje dvě verze WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] a adresování W3C WS 1.0 doporučení [WS-ADDR-CORE] a [WS-ADDR-SOAP].  
  
 Při zmínkami specifikace protokolu WS-ReliableMessaging pouze WS-Addressing 2004/08, se neomezuje verze WS-Addressing má být použit. Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R2101: Obě WS-Addressing 2004/08 a WS-Addressing 1.0 lze použít s WS-spolehlivé zasílání zpráv.  
  
-   R2102: Jedné verzi protokolu WS-Addressing musí použít v rámci daného pořadí WS-ReliableMessaging nebo pár konverzace pořadí korelační pomocí `Offer` mechanismus.  
  
### <a name="composition-with-soap"></a>Složení protokol SOAP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje použití SOAP 1.1 a SOAP 1.2 s WS-spolehlivé zasílání zpráv.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Složení s WS-zabezpečení a WS-SecureConversation  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poskytuje ochranu WS-ReliableMessaging pořadí pomocí zabezpečení přenosu (HTTPS), složení s WS-zabezpečení a složení s WS zabezpečené konverzace. Protokol WS-ReliableMessaging 1.1, WS-zabezpečení 1.1 a protokol WS-zabezpečené konverzace 1.3 musí použít společně. Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R2301: K ochraně integritu WS-ReliableMessaging pořadí kromě integrity a důvěrnosti jednotlivých zpráv [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyžaduje, že se musí použít WS zabezpečené konverzace.  
  
-   R2302:awS-zabezpečené konverzace relace je nutné vytvořit před zřízením WS-ReliableMessaging sequence(s).  
  
-   R2303: Pokud WS-ReliableMessaging pořadí životnost překročí WS zabezpečené konverzace doba platnosti relace, `SecurityContextToken` navázat pomocí WS zabezpečené konverzace musí obnovit pomocí odpovídající vazby WS bezpečné obnovení konverzace.  
  
-   B2304:WS-ReliableMessaging pořadí nebo pár korelační konverzace pořadí jsou vždy vázány na jedné relace WS-SecureConversation.  
  
-   R2305: Když skládá s WS zabezpečené konverzace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér vyžaduje, aby `CreateSequence` zpráva obsahovat `wsse:SecurityTokenReference` element a `wsrm:UsesSequenceSTR` záhlaví.  
  
 Příklad `UsesSequenceSTR` záhlaví.  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a>Složení s relací SSL/TLS.  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]nepodporuje složení s protokolem SSL/TLS relace:  
  
-   B2401: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] negeneruje `wsrm:UsesSequenceSSL` záhlaví.  
  
-   R2402: Spolehlivého zasílání zpráv iniciátor nesmí odesílat `CreateSequence` zpráv s `wsrm:UsesSequenceSSL` hlavičky k [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér.  
  
### <a name="composition-with-ws-policy"></a>Složení zásadám WS  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje dvě verze WS-Policy: WS-Policy 1.2 a WS-Policy 1.5.  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging WS-výraz zásad  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]používá výraz WS-zásad protokolu WS-ReliableMessaging `wsrm:RMAssertion` k popisu možnosti koncových bodů. Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   B3001: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] připojí `wsrmn:RMAssertion` výraz WS-zásad na `wsdl:binding` elementy. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje oba přílohy do `wsdl:binding` a `wsdl:port` elementy.  
  
-   B3002: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nikdy vygeneruje `wsp:Optional` značky.  
  
-   B3003: Při přístupu k `wsrmp:RMAssertion` výraz WS-zásad [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ignoruje `wsp:Optional` značky a zpracovává zásady WS-RM jako povinné.  
  
-   R3004: Protože [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] není tvoří s relací SSL/TLS, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nepřijímá zásady, které určují `wsrmp:SequenceTransportSecurity`.  
  
-   B3005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vždy vygeneruje `wsrmp:DeliveryAssurance` elementu.  
  
-   B3006: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vždy určuje `wsrmp:ExactlyOnce` záruky doručení.  
  
-   B3007: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje a čte následující vlastnosti protokolu WS-ReliableMessaging kontrolní výraz a zajišťuje kontrolu nad je na [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] `ReliableSessionBindingElement`:  
  
    -   `netrmp:InactivityTimeout`  
  
    -   `netrmp:AcknowledgementInterval`  
  
     Příklad `RMAssertion`.  
  
    ```xml  
    <wsrmp:RMAssertion>  
      <wsp:Policy>  
        <wsrmp:SequenceSTR/>  
        <wsrmp:DeliveryAssurance>  
          <wsp:Policy>  
            <wsrmp:ExactlyOnce/>  
            <wsrmp:InOrder/>  
          </wsp:Policy>  
        </wsrmp:DeliveryAssurance>  
      </wsp:Policy>  
      <netrmp:InactivityTimeout Milliseconds="600000"/>  
      <netrmp:AcknowledgementInterval Milliseconds="200"/>  
    </wsrmp:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliablemessaging-extension"></a>Rozšíření protokolu WS-ReliableMessaging toku řízení  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]rozšiřitelnost protokolu WS-ReliableMessaging používá k poskytnutí volitelné další náročnější řídit tok zpráv pořadí.  
  
 Řízení toku povolíte nastavením `ReliableSessionBindingElement`na `FlowControlEnabled``boolean` vlastnost `true`. Tady je seznam omezení, která se týkají [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   B4001: Když spolehlivého zasílání zpráv toku řízení je povoleno, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `netrm:BufferRemaining` element v elementu rozšiřitelnosti služby `SequenceAcknowledgement` záhlaví, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4002: I když spolehlivého zasílání zpráv řízení toku je povoleno, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nevyžaduje `netrm:BufferRemaining` element v `SequenceAcknowledgement` záhlaví.  
  
-   B4003: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spolehlivého zasílání zpráv cílové používá `netrm:BufferRemaining` indikující, kolik nové zprávy můžete ukládat do vyrovnávací paměti.  
  
-   B4004:when spolehlivého zasílání zpráv řízení toku je povoleno, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] spolehlivého zasílání zpráv zdroj používá hodnotu `netrm:BufferRemaining` pro přenos zpráv omezení.  
  
-   B4005: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] generuje `netrm:BufferRemaining` celé číslo hodnoty od 0 do 4096 (včetně) a načte hodnoty celé číslo mezi 0 a `xs:int`na `maxInclusive` hodnotu 214748364 (včetně).  
  
## <a name="message-exchange-patterns"></a>Vzory Exchange zpráv  
 Tato část popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]na chování při použití protokolu WS-ReliableMessaging pro různé vzorce výměny zpráv. Pro každý vzorce výměny zpráv jsou považovány za následující dvě nasazení scénáře:  
  
-   Bez adresovatelné iniciátor: Iniciátor je za bránou firewall; Respondér můžete doručování zpráv na iniciátoru pouze na odpovědi HTTP.  
  
-   Adresovatelné iniciátor: Iniciátor i respondér mohou být odesílány požadavky HTTP; jinými slovy dvě konverzace HTTP připojení lze navázat.  
  
### <a name="one-way-non-addressable-initiator"></a>Jednosměrné, adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poskytuje vzorce výměny zpráv jednosměrný pomocí jednoho pořadí přes jeden kanál protokolu HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]využívá k přenosu všech zpráv z iniciátoru do odpovědí respondéru a HTTP k přenosu všech zpráv z odpovídající partner iniciátoru požadavky HTTP.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přenáší iniciátor `CreateSequence` zpráv bez `Offer` elementu na požadavek HTTP a očekává `CreateSequenceResponse` zprávu na odpovědi HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér vytvoří sekvenci a odesílá `CreateSequenceResponse` zpráv bez `Accept` elementu na odpovědi HTTP.  
  
#### <a name="sequenceacknowledgement"></a>Bylo potvrzení SequenceAcknowledgement  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Iniciátor zpracovává potvrzení na odpověď všechny zprávy s výjimkou `CreateSequence` zprávu a chybové zprávy. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér vždy přenáší samostatné potvrzení na odpovědi HTTP do všech pořadí a `AckRequested` zprávy.  
  
#### <a name="closesequence-exchange"></a>CloseSequence Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přenáší iniciátor `CloseSequence` zpráva na požadavek HTTP a očekává `CreateSequenceResponse` zprávu na odpovědi HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér přenáší `CloseSequenceResponse` zprávu na odpovědi HTTP.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přenáší iniciátor `TerminateSequence` zpráva na požadavek HTTP a očekává `TerminateSequenceResponse` zprávu na odpovědi HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér přenáší `TerminateSequenceResponse` zprávu na odpovědi HTTP.  
  
### <a name="one-way-addressable-initiator"></a>Jedním ze způsobů, adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poskytuje pomocí jednoho pořadí přes jeden vzorce výměny zpráv jednosměrný příchozí a jeden odchozí kanál protokolu HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]používá k přenosu všech zpráv požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přenáší iniciátor `CreateSequence` zpráv bez `Offer` elementu na požadavek HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér vytvoří sekvenci a odesílá `CreateSequenceResponse` zpráv bez `Accept` elementu na požadavek HTTP.  
  
### <a name="duplex-addressable-initiator"></a>Duplexní, adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poskytuje dvě pomocí vzorce výměny zpráv plně asynchronní, obousměrný pořadí více než jeden příchozí a jeden odchozí kanál protokolu HTTP. Tato vzorce výměny zpráv můžete kombinovat s `Request/Reply`, `Addressable` vzorce výměny zpráv iniciátor omezeným způsobem. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]používá k přenosu všech zpráv požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přenáší iniciátor `CreateSequence` zpráv s `Offer` elementu na požadavek HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér zajišťuje, že `CreateSequence` má `Offer` elementu, pak vytvoří sekvenci a odesílá `CreateSequenceResponse` zpráv s `Accept` element.  
  
#### <a name="sequence-lifetime"></a>Doba platnosti pořadí  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]dvě pořadí považuje za jednu relaci plně duplexní.  
  
 Při generování chybu, která závady jedním sekvenčním [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] očekává vzdálený koncový bod pro poruch obě pořadí. Při čtení chybu, která závady jedním sekvenčním [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] závady obě pořadí.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]můžete zavřít jeho odchozí pořadí a pokračovat ve zpracování zprávy v jeho příchozí pořadí. Naopak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] může zpracovat ukončení příchozí pořadí a pokračovat v odesílání zpráv na jeho odchozí pořadí.  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a>Požadavek odpověď a jednosměrné, adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poskytuje jednosměrný a požadavku a odpovědi vzorce výměny zpráv pomocí dvou pořadí více než jeden kanál protokolu HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]využívá k přenosu všech zpráv z iniciátoru do odpovědí respondéru a HTTP k přenosu všech zpráv z odpovídající partner iniciátoru požadavky HTTP.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přenáší iniciátor `CreateSequence` zpráv s `Offer` elementu na požadavek HTTP a očekává `CreateSequenceResponse` zprávu na odpovědi HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér vytvoří sekvenci a odesílá `CreateSequenceResponse` zpráv s `Accept` elementu na odpovědi HTTP.  
  
#### <a name="one-way-message"></a>Jednosměrné zpráv  
 Jednosměrné zpráva exchange úspěšně dokončil, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor přenáší zprávu požadavku pořadí na požadavek HTTP a přijímá samostatnou `SequenceAcknowledgement` zprávu na odpovědi HTTP. `SequenceAcknowledgement` Musí potvrdit zprávy odesílané informace.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér může odpovědět na požadavek potvrzení, chybu nebo odpověď s prázdným textem zprávy a stavový kód HTTP 202.  
  
#### <a name="two-way-messages"></a>Dvě způsob zprávy  
 Protokol pro výměnu zpráv dvoucestné úspěšně dokončil, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor přenáší zprávu požadavku pořadí na požadavek HTTP a přijme zprávu o odpovědi pořadí na odpovědi HTTP. Odpovědi musí mít `SequenceAcknowledgement` to pořadí zprávu požadavku v úvahu přenosu.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér může odpovědět na požadavek s odpověď protokolu aplikace, chybu nebo odpověď s prázdným textem zprávy a stavový kód HTTP 202.  
  
 Z důvodu přítomnosti jednosměrný zprávy a načasování odpovědi aplikací mít žádné korelace pořadové číslo sekvence zprávy požadavku a pořadovým číslem zprávy odpovědi.  
  
#### <a name="retrying-replies"></a>Opakováním odpovědi  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]spoléhá na korelace požadavku a odpovědi HTTP pro korelace protokol exchange obousměrný zprávy. Z toho důvodu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor nezastaví opakování zprávu požadavku pořadí při potvrdí se bez pořadí zprávu požadavku, ale spíš, když představuje odpověď HTTP `SequenceAcknowledgement`, aplikace odpovědi nebo selhání. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér opakování odpovědi na odpovědi HTTP požadavku, ke kterému je korelační odpovědi.  
  
#### <a name="closesequence-exchange"></a>CloseSequence Exchange  
 Po přijetí všechny zprávy sekvence odpovědí a potvrzení pro všechny zprávy s jedním ze způsobů požadavky pořadí, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přenáší iniciátor `CloseSequence` zpráva pro pořadí požadavek na požadavek HTTP a očekává `CloseSequenceResponse` na HTTP odpověď.  
  
 Zavřením sekvence požadavku implicitně zavře odpověď pořadí. To znamená [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor zahrnuje sekvence odpovědí konečné `SequenceAcknowledgement` na `CloseSequence` zprávu a pořadí odpovědi nemá `CloseSequence` exchange.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér zajistí všechny odpovědi jsou potvrzené a odesílá `CloseSequenceResponse` zprávu na odpovědi HTTP.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 Po přijetí `CloseSequenceResponse` zpráv, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] přenáší iniciátor `TerminateSequence` zpráva pro pořadí požadavek na požadavek HTTP a očekává `TerminateSequenceResponse` na odpovědi HTTP.  
  
 Podobně jako `CloseSequence` systému exchange, ukončení pořadí žádost implicitně ukončí odpověď pořadí. To znamená [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] iniciátor zahrnuje sekvence odpovědí konečné `SequenceAcknowledgement` na `TerminateSequence` zprávu a pořadí odpovědi nemá `TerminateSequence` exchange.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér přenáší `TerminateSequenceResponse` zprávu na odpovědi HTTP.  
  
### <a name="requestreply-addressable-initiator"></a>Požadavek nebo odpověď, adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]poskytuje vzorce výměny zpráv požadavku a odpovědi pomocí dvou pořadí více než jeden příchozí a jeden odchozí kanál protokolu HTTP. Tato vzorce výměny zpráv můžete kombinovat s `Duplex, Addressable` vzorce výměny zpráv iniciátor omezeným způsobem. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]používá k přenosu všech zpráv požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Přenáší iniciátor `CreateSequence` zpráv s `Offer` elementu na požadavek HTTP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Respondér zajišťuje, že `CreateSequence` má `Offer` element potom vytvoří sekvenci a odesílá `CreateSequenceResponse` zpráv s `Accept` elementu.  
  
#### <a name="requestreply-correlation"></a>Korelace požadavku/odpovědi  
 Následující část se vztahuje na všechny korelační požadavky a odpovědi:  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zajistí všechny opatřeny zprávy žádost o aplikaci `ReplyTo` reference koncového bodu a `MessageId`.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]odkaz na místní koncový bod se vztahuje jako každou zprávu žádosti o aplikace `ReplyTo`. Odkaz na místní koncový bod je `CreateSequence` zprávy `ReplyTo` pro iniciátory a `CreateSequence` zprávy `To` pro respondér.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zajišťuje, že příchozí požadavek zprávy opatřeny `MessageId` a `ReplyTo`.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zajišťuje `ReplyTo` identifikátor URI koncového bodu odkaz všechny zprávy požadavku aplikace odkaz na místní koncový bod shodovat s dříve definovaným.  
  
-   [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]zajišťuje, že všechny odpovědi berte správný `RelatesTo` a `To` hlavičky následující `wsa` pravidla korelace požadavku/odpovědi.
