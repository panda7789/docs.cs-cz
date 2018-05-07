---
title: Protokol spolehlivého zasílání zpráv verze 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 8ff02bc6953ec1e5030dd0b592a352b7e23ab0d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="reliable-messaging-protocol-version-11"></a>Protokol spolehlivého zasílání zpráv verze 1.1
Toto téma obsahuje podrobné informace o nasazení Windows Communication Foundation (WCF) pro WS-ReliableMessaging protokol února 2007 (verze 1.1) nezbytné pro vzájemná spolupráce pomocí přenosového protokolu HTTP. WCF dodržuje specifikaci WS-ReliableMessaging s omezení a objasnění, která jsou popsané v tomto tématu. Poznámka: verze 1.1 protokolu WS-ReliableMessaging je implementováno začínající [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].  
  
 Protokolu WS-ReliableMessaging. února 2007 protokol je implementována ve WCF pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Pro usnadnění práce tématu používá Tyhle role:  
  
-   Iniciátor: Klienta, která zahájí vytváření sekvence WS-spolehlivé zprávy.  
  
-   Respondér: Služba, která přijímá požadavky je iniciátor.  
  
 Tento dokument používá předpony a obory názvů v následující tabulce.  
  
|Předpona|Obor názvů|  
|-|-|  
|Správce systémových prostředků|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|wsrmp|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|netrmp|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|WSP|(WS-Policy 1.2 nebo WS-Policy 1.5)|  
  
## <a name="messaging"></a>Zasílání zpráv  
  
### <a name="sequence-creation"></a>Vytvoření pořadí  
 Implementuje WCF `CreateSequence` a `CreateSequenceResponse` pořadí zprávy a pokuste se vytvořit spolehlivé zasílání zpráv. Platí následující omezení:  
  
-   B1101: Iniciátoru WCF používá koncový bod odkaz na stejné jako `CreateSequence` zprávy `ReplyTo`, `AcksTo` a `Offer/Endpoint`.  
  
-   R1102: `AcksTo`, `ReplyTo` a `Offer/Endpoint` v odkazuje na koncový bod `CreateSequence` zprávy musí mít hodnoty adres s identické řetězcové vyjádření tak, že budou odpovídat octet-wise.  
  
    -   WCF respondér ověřuje, že část identifikátoru URI `AcksTo`, `ReplyTo` a `Endpoint` odkazy koncového bodu jsou identické před vytvořením sekvenci.  
  
-   R1103: `AcksTo`, `ReplyTo` a `Offer/Endpoint` odkazy na koncový bod v `CreateSequence` zprávy musí mít stejnou sadu parametrů odkaz.  
  
    -   WCF nevynucuje, ale předpokládá, že odkaz parametry `AcksTo`, `ReplyTo` a `Offer/Endpoint` koncový bod odkazuje na `CreateSequence` jsou identické a používá parametry odkaz z `ReplyTo` reference koncového bodu pro konverzace pořadí zprávy a potvrzení.  
  
-   B1104: Iniciátoru WCF negeneruje nepovinný `Expires` nebo `Offer/Expires` element v `CreateSequence` zprávy.  
  
-   B1105: Při přístupu k `CreateSequence` používá respondér WCF zpráva, `Expires` hodnotu `CreateSequence` element jako `Expires` hodnotu ve `CreateSequenceResponse` element. Jinak respondér WCF přečte a ignoruje `Expires` a `Offer/Expires` hodnoty.  
  
-   B1106: Při přístupu k `CreateSequenceResponse` zpráva iniciátoru WCF načte volitelné `Expires` hodnotu, ale nepoužívá se.  
  
-   B1107: Iniciátor WCF a respondér vždy generovat nepovinný `IncompleteSequenceBehavior` element v `CreateSequence/Offer` a `CreateSequenceResponse` elementy.  
  
-   B1108: WCF se používá pouze `DiscardFollowingFirstGap` a `NoDiscard` hodnoty ve `IncompleteSequenceBehavior` elementu.  
  
    -   Využívá WS-ReliableMessaging `Offer` mechanismus pro vytvoření dvou komunikaci korelační pořadí, které vytvářejí relaci.  
  
-   B1109: Pokud `CreateSequence` obsahuje `Offer` elementu jedním ze způsobů respondér WCF odmítne nabízený pořadí podle reagovat se `CreateSequenceResponse` bez `Accept` elementu.  
  
-   B1110: Pokud spolehlivého zasílání zpráv respondér odmítne nabízený pořadí, závady iniciátoru WCF nově vytvořeným pořadí.  
  
-   B1111: Pokud `CreateSequence` neobsahuje `Offer` elementu obousměrný respondér WCF odmítne nabízený pořadí podle reagovat se `CreateSequenceRefused` selhání.  
  
-   R1112: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, `[address]` vlastnost `CreateSequenceResponse/Accept/AcksTo` reference koncového bodu musí odpovídat cílový identifikátor URI z `CreateSequence` zpráva bajtu bajtů.  
  
-   R1113: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, musí se poslat všechny zprávy na obou pořadí předávaných z iniciátoru k příjemce, na odkaz na stejný koncový bod.  
  
 WCF pomocí protokolu WS-ReliableMessaging zřizuje spolehlivé relace mezi iniciátoru a odpovídající počítač. Implementace WCF WS-ReliableMessaging poskytuje spolehlivé relace jednosměrné, požadavku a odpovědi a plně duplexní režim vzory pro zasílání zpráv. WS-ReliableMessaging `Offer` mechanismus na `CreateSequence` a `CreateSequenceResponse` umožňuje vytvořit dva korelační konverzace pořadí a poskytuje protokol relace, který je vhodný pro všechny zprávy koncové body. Protože WCF poskytuje záruku zabezpečení relace, včetně ochrany začátku do konce relace integritu, je potřeba zajistit, aby přicházejí zprávy určené pro stejné strany na stejný cíl. To také umožňuje "Prasátko zálohování" pořadí potvrzení u zpráv s aplikací. Proto platí omezení R1102, R1112 a R1113 pro WCF.  
  
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
 Používá WCF `CloseSequence` a `CloseSequenceResponse` zprávy pro vypnutí spolehlivé zasílání zpráv spouštěná zdroje. Spolehlivé zasílání zpráv WCF cílové neiniciuje vypnutí a zdroji WCF spolehlivé zasílání zpráv nepodporuje vypnutí spolehlivé zasílání zpráv spouštěná na cílový. Platí následující omezení:  
  
-   B1201: Zdroji spolehlivé zasílání zpráv WCF vždycky odešle `CloseSequence` zpráva vypnout sekvenci.  
  
-   B1202: Zdroji spolehlivé zasílání zpráv čeká na potvrzení plný rozsah pořadí zprávy před odesláním `CloseSequence` zprávy.  
  
-   B1203: Zdroji spolehlivé zasílání zpráv vždy obsahuje volitelné `LastMsgNumber` element Pokud sekvenci neobsahuje zprávy.  
  
-   R1204: Cílový spolehlivé zasílání zpráv nesmí iniciovat vypnutí odesláním `CloseSequence` zprávy.  
  
-   B1205: po přijetí `CloseSequence` zprávu, zdroji WCF spolehlivé zasílání zpráv považuje pořadí nekompletní a odešle chybu.  
  
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
 WCF primárně používá `TerminateSequence/TerminateSequenceResponse` handshake po dokončení `CloseSequence/CloseSequenceResponse` metody handshake. Spolehlivé zasílání zpráv WCF cílové neiniciuje ukončení a zdroji spolehlivé zasílání zpráv nepodporuje ukončení spolehlivé zasílání zpráv spouštěná na cílový. Platí následující omezení:  
  
-   B1301: Iniciátoru WCF pouze odešle `TerminateSequence` zpráva po úspěšném dokončení `CloseSequence/CloseSequenceResponse` metody handshake.  
  
-   R1302: WCF ověří, jestli `LastMsgNumber` element je konzistentní napříč všemi `CloseSequence` a `TerminateSequence` zprávy pro daného pořadí. To znamená, že `LastMsgNumber` buď není přítomen na všech `CloseSequence` a `TerminateSequence` zprávy, nebo je přítomen a na všechny stejné `CloseSequence` a `TerminateSequence` zprávy.  
  
-   B1303: Při přijímání `TerminateSequence` zprávy po `CloseSequence/CloseSequenceResponse` handshake, odpoví cílové spolehlivé zasílání zpráv `TerminateSequenceResponse` zprávy. Protože má zdroj spolehlivé zasílání zpráv konečné potvrzení před odesláním `TerminateSequence` zprávy, cílový spolehlivé zasílání zpráv zná bez nepochybně, že je pořadí skončí a uvolní prostředky okamžitě.  
  
-   B1304: Při přijímání `TerminateSequence` zpráv starších než `CloseSequence/CloseSequenceResponse` handshake, odpoví cílové WCF spolehlivé zasílání zpráv `TerminateSequenceResponse` zprávy. Pokud cílový spolehlivé zasílání zpráv zjistí, že neexistují žádné nekonzistence v pořadí, cílový spolehlivé zasílání zpráv čeká na dobu zadané cílové aplikace před opětovného získání prostředků, aby klient riziko pro příjem konečné potvrzení. Jinak cílové spolehlivé zasílání zpráv okamžitě získá prostředky a označuje cílové aplikace, že je pořadí končí nejistých zobrazením `Faulted` událostí.  
  
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
  
-   Generuje B1401:WCF a přístupů pořadí čísla vyšší než `xs:long`na maximální hodnotu (včetně), 9223372036854775807.  
  
 Příklad `Sequence` záhlaví.  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a>Žádost o potvrzení  
 Používá WCF `AckRequested` záhlaví jako mechanismus keep-alive.  
  
 Příklad `AckRequested` záhlaví.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a>Bylo potvrzení SequenceAcknowledgement  
 WCF používá mechanismus "Prasátko zpětným" pro potvrzení pořadí, které jsou součástí služby WS-spolehlivé zasílání zpráv. Platí následující omezení:  
  
-   R1601: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` záhlaví může být součástí jakékoli aplikace zprávy předaných zamýšlený příjemce. Vzdálený koncový bod musí být schopni přistupovat zařazována složená `SequenceAcknowledgement` záhlaví.  
  
-   B1602: WCF negeneruje `SequenceAcknowledgement` hlavičky, které obsahují `Nack` elementy. WCF ověří, že každý `Nack` elementu obsahuje pořadové číslo, ale jinak ignoruje `Nack` elementu a hodnotu.  
  
 Příklad `SequenceAcknowledgement` záhlaví.  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging chyb  
 Následuje seznam omezení, které se vztahují na WCF implementaci protokolu WS-ReliableMessaging chyb. Platí následující omezení:  
  
-   B1701: WCF negeneruje `MessageNumberRollover` chyb.  
  
-   B1702: Přes SOAP 1.2, pokud koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení, WCF generuje vnořený `CreateSequenceRefused` poruch dílčí, `netrm:ConnectionLimitReached`, jak je znázorněno v následujícím příkladu.  
  
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
 Protože WS-ReliableMessaging používá WS-Addressing, implementace WCF WS-ReliableMessaging může generovat a přenášet WS-Addressing chyb. Tato část se zabývá WS-Addressing chyb, které WCF explicitně generuje a odesílá ve vrstvě protokolu WS-ReliableMessaging:  
  
-   B1801:WCF generuje a odesílá `Message Addressing Header Required` poruch, když je splněna jedna z následujících akcí:  
  
    -   A `CreateSequence`, `CloseSequence` nebo `TerminateSequence` chybí zpráva `MessageId` záhlaví.  
  
    -   A `CreateSequence`, `CloseSequence` nebo `TerminateSequence` chybí zpráva `ReplyTo` záhlaví.  
  
    -   A `CreateSequenceResponse`, `CloseSequenceResponse`, nebo `TerminateSequenceResponse` chybí zpráva `RelatesTo` záhlaví.  
  
-   B1802:WCF generuje a odesílá `Endpoint Unavailable` selhání označíte, neexistuje žádný koncový bod naslouchání, který může zpracovat pořadí podle zkoumání adresování hlavičky v `CreateSequence` zprávy.  
  
## <a name="protocol-composition"></a>Protokol složení  
  
### <a name="composition-with-ws-addressing"></a>Složení s adresováním WS  
 Podporuje dvě verze WS-Addressing WCF: WS-Addressing 2004/08 [WS-ADDR] a adresování W3C WS 1.0 doporučení [WS-ADDR-CORE] a [WS-ADDR-SOAP].  
  
 Při zmínkami specifikace protokolu WS-ReliableMessaging pouze WS-Addressing 2004/08, se neomezuje verze WS-Addressing má být použit. Následuje seznam omezení, která se týkají WCF:  
  
-   R2101: Obě WS-Addressing 2004/08 a WS-Addressing 1.0 lze použít s WS-spolehlivé zasílání zpráv.  
  
-   R2102: Jedné verzi protokolu WS-Addressing musí použít v rámci daného pořadí WS-ReliableMessaging nebo pár konverzace pořadí korelační pomocí `Offer` mechanismus.  
  
### <a name="composition-with-soap"></a>Složení protokol SOAP  
 WCF podporuje použití SOAP 1.1 a SOAP 1.2 s WS-spolehlivé zasílání zpráv.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Složení s WS-zabezpečení a WS-SecureConversation  
 WCF poskytuje ochranu WS-ReliableMessaging pořadí pomocí zabezpečení přenosu (HTTPS), složení s WS-zabezpečení a složení s WS zabezpečené konverzace. Protokol WS-ReliableMessaging 1.1, WS-zabezpečení 1.1 a protokol WS-zabezpečené konverzace 1.3 musí použít společně. Následuje seznam omezení, která se týkají WCF:  
  
-   R2301: K ochraně integrity pořadí WS-ReliableMessaging kromě integrity a důvěrnosti jednotlivých zpráv, WCF vyžaduje, aby se musí použít WS zabezpečené konverzace.  
  
-   R2302:awS-zabezpečené konverzace relace je nutné vytvořit před zřízením WS-ReliableMessaging sequence(s).  
  
-   R2303: Pokud WS-ReliableMessaging pořadí životnost překročí WS zabezpečené konverzace doba platnosti relace, `SecurityContextToken` navázat pomocí WS zabezpečené konverzace musí obnovit pomocí odpovídající vazby WS bezpečné obnovení konverzace.  
  
-   B2304:WS-ReliableMessaging pořadí nebo pár korelační konverzace pořadí jsou vždy vázány na jedné relace WS-SecureConversation.  
  
-   R2305: Když skládá s WS zabezpečené konverzace, respondér WCF vyžaduje, aby `CreateSequence` obsahovat zprávy `wsse:SecurityTokenReference` element a `wsrm:UsesSequenceSTR` záhlaví.  
  
 Příklad `UsesSequenceSTR` záhlaví.  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a>Složení s relací SSL/TLS.  
 WCF nepodporuje složení s protokolem SSL/TLS relace:  
  
-   B2401: WCF negeneruje `wsrm:UsesSequenceSSL` záhlaví.  
  
-   R2402: Spolehlivého zasílání zpráv iniciátor nesmí odesílat `CreateSequence` zpráv s `wsrm:UsesSequenceSSL` hlavičky k respondér WCF.  
  
### <a name="composition-with-ws-policy"></a>Složení zásadám WS  
 WCF podporuje dvě verze WS-Policy: WS-Policy 1.2 a WS-Policy 1.5.  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging WS-výraz zásad  
 WCF pomocí protokolu WS-ReliableMessaging WS-Policy Assertion `wsrm:RMAssertion` k popisu možnosti koncových bodů. Následuje seznam omezení, která se týkají WCF:  
  
-   B3001: Připojí WCF `wsrmn:RMAssertion` výraz WS-zásad na `wsdl:binding` elementy. WCF podporuje obě přílohy do `wsdl:binding` a `wsdl:port` elementy.  
  
-   B3002: WCF nikdy vygeneruje `wsp:Optional` značky.  
  
-   B3003: Při přístupu k `wsrmp:RMAssertion` Assertion WS-Policy, ignoruje WCF `wsp:Optional` značky a zpracovává zásady WS-RM jako povinné.  
  
-   R3004: Protože WCF není tvoří s relací SSL/TLS, WCF nepřijímá zásady, které určují `wsrmp:SequenceTransportSecurity`.  
  
-   B3005: WCF vždy vygeneruje `wsrmp:DeliveryAssurance` elementu.  
  
-   B3006: WCF vždy určuje `wsrmp:ExactlyOnce` záruky doručení.  
  
-   B3007: WCF generuje a čte následující vlastnosti protokolu WS-ReliableMessaging kontrolní výraz a zajišťuje kontrolu nad je na WCF`ReliableSessionBindingElement`:  
  
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
 WCF využívá rozšiřitelnost protokolu WS-ReliableMessaging volitelné další náročnější řídit tok zpráv pořadí.  
  
 Řízení toku povolíte nastavením `ReliableSessionBindingElement`na `FlowControlEnabled``boolean` vlastnost `true`. Následuje seznam omezení, která se týkají WCF:  
  
-   B4001: WCF generuje Pokud je povoleno spolehlivého zasílání zpráv řízení toku, `netrm:BufferRemaining` element v elementu rozšiřitelnosti služby `SequenceAcknowledgement` záhlaví, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4002: I když je povolena spolehlivého zasílání zpráv řízení toku, WCF nevyžaduje `netrm:BufferRemaining` element v `SequenceAcknowledgement` záhlaví.  
  
-   B4003: Používá WCF spolehlivého zasílání zpráv cílové `netrm:BufferRemaining` indikující, kolik nové zprávy můžete ukládat do vyrovnávací paměti.  
  
-   Je povolený B4004:when spolehlivého zasílání zpráv řízení toku, zdroji WCF spolehlivého zasílání zpráv používá hodnotu `netrm:BufferRemaining` pro přenos zpráv omezení.  
  
-   B4005: Generuje WCF `netrm:BufferRemaining` celé číslo hodnoty od 0 do 4096 (včetně) a načte hodnoty celé číslo mezi 0 a `xs:int`na `maxInclusive` hodnotu 214748364 (včetně).  
  
## <a name="message-exchange-patterns"></a>Vzory Exchange zpráv  
 Tato část popisuje WCF na chování při použití protokolu WS-ReliableMessaging pro různé vzorce výměny zpráv. Pro každý vzorce výměny zpráv jsou považovány za následující dvě nasazení scénáře:  
  
-   Bez adresovatelné iniciátor: Iniciátor je za bránou firewall; Respondér můžete doručování zpráv na iniciátoru pouze na odpovědi HTTP.  
  
-   Adresovatelné iniciátor: Iniciátor i respondér mohou být odesílány požadavky HTTP; jinými slovy dvě konverzace HTTP připojení lze navázat.  
  
### <a name="one-way-non-addressable-initiator"></a>Jednosměrné, adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 WCF poskytuje vzorce výměny zpráv jednosměrný pomocí jednoho pořadí přes jeden kanál protokolu HTTP. WCF využívá k přenosu všech zpráv z iniciátoru do odpovědí respondéru a HTTP k přenosu všech zpráv z odpovídající partner iniciátoru požadavky HTTP.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Přenáší iniciátoru WCF `CreateSequence` zpráv bez `Offer` elementu na požadavek HTTP a očekává `CreateSequenceResponse` zprávu na odpovědi HTTP. Vytvoří posloupnost respondér WCF a odesílá `CreateSequenceResponse` zpráv bez `Accept` elementu na odpovědi HTTP.  
  
#### <a name="sequenceacknowledgement"></a>Bylo potvrzení SequenceAcknowledgement  
 Iniciátor WCF zpracovává potvrzení na odpověď všechny zprávy s výjimkou `CreateSequence` zprávu a chybové zprávy. WCF respondér vždy přenáší samostatné potvrzení na odpovědi HTTP do všech pořadí a `AckRequested` zprávy.  
  
#### <a name="closesequence-exchange"></a>CloseSequence Exchange  
 Přenáší iniciátoru WCF `CloseSequence` zpráva na požadavek HTTP a očekává `CreateSequenceResponse` zprávu na odpovědi HTTP. Přenáší respondér WCF `CloseSequenceResponse` zprávu na odpovědi HTTP.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 Přenáší iniciátoru WCF `TerminateSequence` zpráva na požadavek HTTP a očekává `TerminateSequenceResponse` zprávu na odpovědi HTTP. Přenáší respondér WCF `TerminateSequenceResponse` zprávu na odpovědi HTTP.  
  
### <a name="one-way-addressable-initiator"></a>Jedním ze způsobů, adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 Poskytuje WCF pomocí jednoho pořadí přes jeden vzorce výměny zpráv jednosměrný příchozí a jeden odchozí kanál protokolu HTTP. WCF využívá k přenosu všechny zprávy požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Přenáší iniciátoru WCF `CreateSequence` zpráv bez `Offer` elementu na požadavek HTTP. Vytvoří posloupnost respondér WCF a odesílá `CreateSequenceResponse` zpráv bez `Accept` elementu na požadavek HTTP.  
  
### <a name="duplex-addressable-initiator"></a>Duplexní, adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 Poskytuje WCF pomocí dvou vzorce výměny zpráv plně asynchronní, obousměrný pořadí více než jeden příchozí a jeden odchozí kanál protokolu HTTP. Tato vzorce výměny zpráv můžete kombinovat s `Request/Reply`, `Addressable` vzorce výměny zpráv iniciátor omezeným způsobem. WCF využívá k přenosu všechny zprávy požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Přenáší iniciátoru WCF `CreateSequence` zpráv s `Offer` elementu na požadavek HTTP. WCF respondér zajišťuje, že `CreateSequence` má `Offer` elementu, pak vytvoří sekvenci a odesílá `CreateSequenceResponse` zpráv s `Accept` element.  
  
#### <a name="sequence-lifetime"></a>Doba platnosti pořadí  
 WCF považuje za jednu relaci plně duplexní dvě pořadí.  
  
 Při generování chybu, která závady jedním sekvenčním, WCF očekává, že vzdálený koncový bod pro poruch obě pořadí. Při čtení chybu, která jedním sekvenčním chyb, chyb WCF obě pořadí.  
  
 WCF můžete zavřít jeho odchozí pořadí a pokračovat ve zpracování zprávy v jeho příchozí pořadí. Naopak WCF můžete zpracovat ukončení příchozí pořadí a pokračovat v odesílání zpráv na jeho odchozí pořadí.  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a>Požadavek odpověď a jednosměrné, adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 Poskytuje jednosměrný WCF a vzorce výměny zpráv požadavku a odpovědi pomocí dvou pořadí více než jeden kanál protokolu HTTP. WCF využívá k přenosu všech zpráv z iniciátoru do odpovědí respondéru a HTTP k přenosu všech zpráv z odpovídající partner iniciátoru požadavky HTTP.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Přenáší iniciátoru WCF `CreateSequence` zpráv s `Offer` elementu na požadavek HTTP a očekává `CreateSequenceResponse` zprávu na odpovědi HTTP. Vytvoří posloupnost respondér WCF a odesílá `CreateSequenceResponse` zpráv s `Accept` elementu na odpovědi HTTP.  
  
#### <a name="one-way-message"></a>Jednosměrné zpráv  
 Úspěšné dokončení jednosměrný zpráva systému exchange, iniciátoru WCF přenáší zprávu požadavku pořadí na požadavek HTTP a přijímá samostatnou `SequenceAcknowledgement` zprávu na odpovědi HTTP. `SequenceAcknowledgement` Musí potvrdit zprávy odesílané informace.  
  
 Respondér WCF může odpovědět na požadavek potvrzení, chybu nebo odpověď s prázdným textem zprávy a stavový kód HTTP 202.  
  
#### <a name="two-way-messages"></a>Dvě způsob zprávy  
 Protokol pro výměnu zpráv dvoucestné úspěšně dokončil, iniciátoru WCF přenáší zprávu požadavku pořadí na požadavek HTTP a přijme zprávu o odpovědi pořadí na odpovědi HTTP. Odpovědi musí mít `SequenceAcknowledgement` to pořadí zprávu požadavku v úvahu přenosu.  
  
 Respondér WCF může odpovědět na požadavek s odpověď protokolu aplikace, chybu nebo odpověď s prázdným textem zprávy a stavový kód HTTP 202.  
  
 Z důvodu přítomnosti jednosměrný zprávy a načasování odpovědi aplikací mít žádné korelace pořadové číslo sekvence zprávy požadavku a pořadovým číslem zprávy odpovědi.  
  
#### <a name="retrying-replies"></a>Opakováním odpovědi  
 WCF spoléhá na korelace požadavku a odpovědi HTTP pro korelace protokol exchange obousměrný zprávy. Z toho důvodu iniciátoru WCF nezastaví opakování zprávu požadavku pořadí při potvrdí se bez pořadí zprávu požadavku, ale spíš, když představuje odpověď HTTP `SequenceAcknowledgement`, aplikace a odpovědi nebo selhání. WCF respondér opakuje odpovědi na odpovědi HTTP požadavku, ke kterému je korelační odpovědi.  
  
#### <a name="closesequence-exchange"></a>CloseSequence Exchange  
 Po přijetí všechny zprávy sekvence odpovědí a potvrzení pro všechny zprávy s jedním ze způsobů požadavky pořadí, přenáší iniciátoru WCF `CloseSequence` zpráva pro pořadí požadavek na požadavek HTTP a očekává `CloseSequenceResponse` na odpovědi HTTP.  
  
 Zavřením sekvence požadavku implicitně zavře odpověď pořadí. To znamená, že iniciátoru WCF zahrnuje sekvence odpovědí konečné `SequenceAcknowledgement` na `CloseSequence` zprávu a pořadí odpovědi nemá `CloseSequence` exchange.  
  
 WCF respondér zajistí všechny odpovědi jsou potvrzené a odesílá `CloseSequenceResponse` zprávu na odpovědi HTTP.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 Po přijetí `CloseSequenceResponse` odesílá zprávy iniciátoru WCF `TerminateSequence` zpráva pro pořadí požadavek na požadavek HTTP a očekává `TerminateSequenceResponse` na odpovědi HTTP.  
  
 Podobně jako `CloseSequence` systému exchange, ukončení pořadí žádost implicitně ukončí odpověď pořadí. To znamená, že iniciátoru WCF zahrnuje sekvence odpovědí konečné `SequenceAcknowledgement` na `TerminateSequence` zprávu a pořadí odpovědi nemá `TerminateSequence` exchange.  
  
 Přenáší respondér WCF `TerminateSequenceResponse` zprávu na odpovědi HTTP.  
  
### <a name="requestreply-addressable-initiator"></a>Požadavek nebo odpověď, adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 WCF poskytuje vzorce výměny zpráv požadavku a odpovědi pomocí dvou pořadí více než jeden příchozí a jeden odchozí kanál protokolu HTTP. Tato vzorce výměny zpráv můžete kombinovat s `Duplex, Addressable` vzorce výměny zpráv iniciátor omezeným způsobem. WCF využívá k přenosu všechny zprávy požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Přenáší iniciátoru WCF `CreateSequence` zpráv s `Offer` elementu na požadavek HTTP. Respondér WCF zajišťuje, že `CreateSequence` má `Offer` element potom vytvoří sekvenci a odesílá `CreateSequenceResponse` zpráv s `Accept` element.  
  
#### <a name="requestreply-correlation"></a>Korelace požadavku/odpovědi  
 Následující část se vztahuje na všechny korelační požadavky a odpovědi:  
  
-   WCF zajistí všechny opatřeny zprávy žádost o aplikaci `ReplyTo` reference koncového bodu a `MessageId`.  
  
-   WCF platí odkaz na místní koncový bod jako každou zprávu žádosti o aplikace `ReplyTo`. Odkaz na místní koncový bod je `CreateSequence` zprávy `ReplyTo` pro iniciátory a `CreateSequence` zprávy `To` pro respondér.  
  
-   WCF zajistí, že příchozí požadavek zprávy opatřeny `MessageId` a `ReplyTo`.  
  
-   Zajišťuje WCF `ReplyTo` identifikátor URI koncového bodu odkaz všechny zprávy požadavku aplikace odkaz na místní koncový bod shodovat s dříve definovaným.  
  
-   WCF zajistí, že všechny odpovědi berte správný `RelatesTo` a `To` hlavičky následující `wsa` pravidla korelace požadavku/odpovědi.
