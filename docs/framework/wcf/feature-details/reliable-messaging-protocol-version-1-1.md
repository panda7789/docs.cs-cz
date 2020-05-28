---
title: Protokol spolehlivého zasílání zpráv verze 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: ad0a77842c10965749eab4e76bb123938e07e9d5
ms.sourcegitcommit: ee5b798427f81237a3c23d1fd81fff7fdc21e8d3
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/28/2020
ms.locfileid: "84144718"
---
# <a name="reliable-messaging-protocol-version-11"></a>Protokol spolehlivého zasílání zpráv verze 1.1

Toto téma obsahuje podrobnosti o implementaci Windows Communication Foundation (WCF) pro protokol WS-ReliableMessaging únor 2007 (verze 1,1), který je nezbytný pro meziprovozu pomocí přenosu HTTP. WCF sleduje specifikace WS-ReliableMessaging s omezeními a vysvětleními, které jsou vysvětleny v tomto tématu. Počítejte s tím, že protokol WS-ReliableMessaging verze 1,1 je implementován od .NET Framework 3,5.

Protokol WS-ReliableMessaging únor 2007 je implementován v WCF pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> .

Pro usnadnění práce téma používá následující role:

- Iniciátor: klient, který iniciuje vytvoření sekvence zpráv WS-Reliable.

- Responder: služba, která přijímá žádosti iniciátoru.

 Tento dokument používá předpony a obory názvů v následující tabulce.

|Předpona|Obor názvů|
|-|-|
|správcem|`http://docs.oasis-open.org/ws-rx/wsrm/200702`|
|netrm|`http://schemas.microsoft.com/ws/2006/05/rm`|
|s|`http://www.w3.org/2003/05/soap-envelope`|
|WSA|`http://schemas.xmlsoap.org/ws/2005/08/addressing`|
|wsse|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|
|wsrmp|`http://docs.oasis-open.org/ws-rx/wsrmp/200702`|
|netrmp|`http://schemas.microsoft.com/ws-rx/wsrmp/200702`|
|WSP|(WS-Policy 1,2 nebo WS-Policy 1,5)|

## <a name="messaging"></a>Zasílání zpráv

### <a name="sequence-creation"></a>Vytvoření sekvence

Služba WCF `CreateSequence` implementuje `CreateSequenceResponse` zprávy a k vytvoření spolehlivé sekvence zasílání zpráv. Platí následující omezení:

- B1101: iniciátor WCF používá stejný odkaz na koncový bod jako `CreateSequence` zprávu `ReplyTo` `AcksTo` a `Offer/Endpoint` .

- R1102: `AcksTo` `ReplyTo` `Offer/Endpoint` odkazy koncového bodu (a) ve `CreateSequence` zprávě musí mít hodnoty adresy s identickými reprezentacemi řetězců tak, aby odpovídaly oktetu.

  - Respondér WCF ověřuje, že část identifikátoru URI `AcksTo` `ReplyTo` a `Endpoint` odkazy koncového bodu jsou stejné před vytvořením sekvence.

- R1103: `AcksTo` odkazy na `ReplyTo` `Offer/Endpoint` koncový bod ve `CreateSequence` zprávě by měly mít stejnou sadu parametrů odkazu.

  - Služba WCF neuplatňuje, ale předpokládá, že odkazové parametry `AcksTo` `ReplyTo` a `Offer/Endpoint` odkazy na koncový bod `CreateSequence` jsou identické a používá referenční parametry z `ReplyTo` reference koncového bodu pro potvrzení a zprávy sekvence konverzace.

- B1104: iniciátor WCF negeneruje Volitelný `Expires` `Offer/Expires` element or ve `CreateSequence` zprávě.

- B1105: při přístupu ke `CreateSequence` zprávě používá RESPONDÉR WCF `Expires` hodnotu v `CreateSequence` prvku jako `Expires` hodnotu v `CreateSequenceResponse` elementu. V opačném případě respondér WCF načte a ignoruje `Expires` `Offer/Expires` hodnoty a.

- B1106: při přístupu ke `CreateSequenceResponse` zprávě INICIÁTOR WCF přečte volitelnou `Expires` hodnotu, ale nepoužije ji.

- B1107: iniciátor WCF a respondér vždy vygeneruje volitelný `IncompleteSequenceBehavior` element v `CreateSequence/Offer` `CreateSequenceResponse` elementech a.

- B1108: WCF používá pouze `DiscardFollowingFirstGap` hodnoty a `NoDiscard` v `IncompleteSequenceBehavior` elementu.

  - WS-ReliableMessaging využívá `Offer` mechanismus pro vytvoření dvou vzájemně se korelačních sekvencí konverzace, které tvoří relaci.

- B1109: Pokud `CreateSequence` obsahuje `Offer` element, pak jednosměrné respondér WCF odmítne nabízenou sekvenci tím, že odpoví `CreateSequenceResponse` bez `Accept` prvku.

- B1110: Pokud spolehlivý respondér zasílání zpráv odmítne nabízenou sekvenci, vyhledá iniciátor WCF nově vytvořenou sekvenci.

- B1111: Pokud neobsahuje `CreateSequence` `Offer` element, OBOUSMĚRNÝ respondér WCF odmítne nabízenou sekvenci tím, že odpoví na `CreateSequenceRefused` chybu.

- R1112: při vytváření dvou sekvencí konverzace pomocí `Offer` mechanismu se `[address]` vlastnost `CreateSequenceResponse/Accept/AcksTo` odkazu na koncový bod musí shodovat s cílovým identifikátorem URI `CreateSequence` bajtu zprávy pro bajt.

- R1113: v případě, že se pomocí mechanismu vytvoří dvě sekvence konverzace `Offer` , musí se všechny zprávy v obou sekvencích toku od iniciátoru k tomuto partnerovi odeslat do stejného odkazu na koncový bod.

WCF používá ke zřízení spolehlivých relací mezi iniciátorem a respondérem WS-ReliableMessaging. Implementace WCF WS-ReliableMessaging poskytuje spolehlivou relaci pro jednosměrné, požadavek-odpověď a plně duplexní vzory zasílání zpráv. Mechanismus WS-ReliableMessaging `Offer` on `CreateSequence` a `CreateSequenceResponse` umožňuje vytvořit dvě korelační posloupnosti konverzace a poskytuje protokol relace, který je vhodný pro všechny koncové body zprávy. Vzhledem k tomu, že WCF poskytuje záruku zabezpečení pro takovou relaci, včetně ucelené ochrany integrity relací, je praktické zajistit, aby zprávy určené pro stejnou stranu byly doručeny do stejného umístění. To také umožňuje "Piggy-Back" (potvrzování sekvencí) pro zprávy aplikací. Proto se omezení R1102, R1112 a R1113 vztahují na WCF.

Příklad `CreateSequence` zprávy

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

Příklad `CreateSequenceResponse` zprávy

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

### <a name="closing-a-sequence"></a>Uzavírání sekvence

Služba WCF používá `CloseSequence` `CloseSequenceResponse` zprávy a pro vypnutí spolehlivého zdroje zpráv – iniciování. Cíl spolehlivého zasílání zpráv WCF neinicializuje vypnutí a zdroj spolehlivého zasílání zpráv WCF nepodporuje vypnutí spolehlivého cíle zasílání zpráv. Platí následující omezení:

- B1201: zdroj spolehlivého zasílání zpráv WCF vždycky pošle `CloseSequence` zprávu pro vypnutí sekvence.

- B1202: zdroj spolehlivého zasílání zpráv čeká na potvrzení plného rozsahu zpráv sekvence před odesláním `CloseSequence` zprávy.

- B1203: spolehlivý zdroj zasílání zpráv vždy obsahuje volitelný `LastMsgNumber` element, pokud sekvence neobsahuje zprávy.

- R1204: cíl spolehlivého zasílání zpráv nesmí iniciovat vypnutí odesláním `CloseSequence` zprávy.

- B1205: po přijetí `CloseSequence` zprávy nepovažuje zdroj spolehlivých zpráv WCF sekvenci nekompletní a pošle chybu.

 Příklad `CloseSequence` zprávy

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
```

Příklad `CloseSequenceResponse` zprávy:

```xml
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

### <a name="sequence-termination"></a>Ukončení sekvence

WCF primárně používá `TerminateSequence/TerminateSequenceResponse` metodu handshake po dokončení `CloseSequence/CloseSequenceResponse` metody handshake. Cíl spolehlivého zasílání zpráv WCF nezahajuje ukončení a spolehlivý zdroj přenosu dat nepodporuje ukončení iniciované spolehlivým cílem zasílání zpráv. Platí následující omezení:

- B1301: iniciátor WCF odesílá `TerminateSequence` zprávu pouze po úspěšném dokončení `CloseSequence/CloseSequenceResponse` metody handshake.

- R1302: WCF ověřuje, že `LastMsgNumber` element je konzistentní napříč všemi `CloseSequence` `TerminateSequence` zprávami pro danou sekvenci. To znamená, že `LastMsgNumber` buď není přítomen u všech `CloseSequence` `TerminateSequence` zpráv, nebo je přítomna a shodná se všemi `CloseSequence` a `TerminateSequence` zprávami.

- B1303: když `TerminateSequence` po signalizaci obdržíte zprávu `CloseSequence/CloseSequenceResponse` , cíl spolehlivého zasílání zpráv odpoví `TerminateSequenceResponse` zprávou. Vzhledem k tomu, že zdroj spolehlivého zasílání zpráv má závěrečné potvrzení, před odesláním `TerminateSequence` zprávy, bude cíl spolehlivého zasílání zpráv vědět bez pochybnosti o ukončení sekvence a okamžitě Redeklarace prostředků.

- B1304: při přijímání `TerminateSequence` zprávy před `CloseSequence/CloseSequenceResponse` metodou handshake odpoví cíl spolehlivého zasílání zpráv WCF `TerminateSequenceResponse` zprávou. Pokud cíl spolehlivého zasílání zpráv zjistí, že v sekvenci nejsou žádné nekonzistence, čeká cíl spolehlivého zasílání zpráv na zadaný čas aplikace, než se uvolní prostředky, aby klient mohl získat konečné potvrzení. V opačném případě cíl spolehlivého zasílání zpráv Redeklarace prostředků okamžitě a označuje cíl aplikace, který sekvence končí, pomocí vyvolání `Faulted` události.

Příklad `TerminateSequence` zprávy

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
```

Příklad `TerminateSequenceResponse` zprávy:

```xml
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

Následuje seznam omezení, která platí pro sekvence:

- B1401: WCF generuje a přistupuje k pořadovým číslům, která nejsou vyšší než `xs:long` maximální celková hodnota, 9223372036854775807.

Příklad `Sequence` záhlaví.

```xml
<wsrm:Sequence s:mustUnderstand="1">
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:MessageNumber>1</wsrm:MessageNumber>
</wsrm:Sequence>
```

### <a name="request-acknowledgement"></a>Potvrzení žádosti

WCF používá `AckRequested` záhlaví jako mechanismus udržování.

Příklad `AckRequested` záhlaví.

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

WCF používá mechanizmus "Piggy-Back" pro potvrzení sekvencí, které jsou k dispozici v zasílání zpráv WS-Reliable. Platí následující omezení:

- R1601: Pokud se pomocí mechanismu vytvoří dvě posloupnosti konverzace `Offer` , `SequenceAcknowledgement` může se hlavička zahrnout do jakékoli zprávy aplikace předané zamýšlenému příjemci. Vzdálený koncový bod musí být schopný získat přístup k složenému `SequenceAcknowledgement` záhlaví.

- B1602: WCF negeneruje `SequenceAcknowledgement` hlavičky, které obsahují `Nack` elementy. WCF ověřuje, že každý `Nack` prvek obsahuje pořadové číslo, ale jinak ignoruje `Nack` prvek a hodnotu.

 Příklad `SequenceAcknowledgement` záhlaví.

```xml
<wsrm:SequenceAcknowledgement>
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>
</wsrm:SequenceAcknowledgement>
```

### <a name="ws-reliablemessaging-faults"></a>Chyby WS-ReliableMessaging

Následující seznam obsahuje omezení, která se vztahují na implementaci WCF s chybami WS-ReliableMessaging. Platí následující omezení:

- B1701: WCF negeneruje `MessageNumberRollover` chyby.

- B1702: přes SOAP 1,2, když koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení, WCF vygeneruje vnořený `CreateSequenceRefused` podkód chyby, `netrm:ConnectionLimitReached` jak je znázorněno v následujícím příkladu.

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

### <a name="ws-addressing-faults"></a>Chyby WS-Addressing

Vzhledem k tomu, že WS-ReliableMessaging používá WS-ReliableMessaging, implementace WCF WS-ReliableMessaging může generovat a odesílat chyby WS-Addressing. Tato část se zabývá chybami WS-Addressing, které WCF explicitně generuje a odesílá ve vrstvě WS-ReliableMessaging:

- B1801: WCF vygeneruje a přenáší `Message Addressing Header Required` chybu, pokud je splněna jedna z následujících podmínek:

  - V `CreateSequence` `CloseSequence` nebo ve `TerminateSequence` zprávě chybí `MessageId` záhlaví.

  - V `CreateSequence` `CloseSequence` nebo ve `TerminateSequence` zprávě chybí `ReplyTo` záhlaví.

  - V `CreateSequenceResponse` `CloseSequenceResponse` nebo ve `TerminateSequenceResponse` zprávě chybí `RelatesTo` záhlaví.

- B1802: WCF vygeneruje a přenáší `Endpoint Unavailable` chybu, aby označovala, že nenaslouchá žádný koncový bod, který může zpracovat sekvenci na základě zkoumání hlaviček adres ve `CreateSequence` zprávě.

## <a name="protocol-composition"></a>Složení protokolu

### <a name="composition-with-ws-addressing"></a>Složení pomocí WS-Addressing

Služba WCF podporuje dvě verze elementu WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] a W3C WS-Addressing 1,0 Recommendations [WS-ADDR-CORE] a [WS-ADDR-SOAP].

I když specifikace WS-ReliableMessaging zmiňuje pouze WS-Addressing 2004/08, neomezuje použití verze WS-Addressing. Následuje seznam omezení, která platí pro WCF:

- R2101: Služba WS-Addressing 2004/08 a WS-Addressing 1,0 se dá použít se zasíláním zpráv WS-Reliable.

- R2102: v rámci dané sekvence WS-ReliableMessaging musí být použita jedna verze elementu WS-Addressing nebo dvojice sekvencí konverzace v souvislosti s použitím `Offer` mechanismu.

### <a name="composition-with-soap"></a>Složení pomocí protokolu SOAP

Služba WCF podporuje použití protokolu SOAP 1,1 i SOAP 1,2 se zasíláním zpráv WS-Reliable.

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Složení pomocí WS-Security a WS-SecureConversation

Služba WCF poskytuje ochranu pro sekvence WS-ReliableMessaging pomocí zabezpečeného přenosu (HTTPS), složení pomocí WS-Security a složení pomocí konverzace WS-Secure. Protokol WS-ReliableMessaging 1,1, WS-Security 1,1 a WS-Secure konverzace 1,3 by se měl používat společně. Následuje seznam omezení, která platí pro WCF:

- R2301: aby byla zajištěna ochrana integrity sekvence WS-ReliableMessaging Kromě integrity a důvěrnosti jednotlivých zpráv, služba WCF vyžaduje, aby se používala konverzace WS-Secure.

- R2302: AWS – před vytvořením posloupností WS-ReliableMessaging je nutné vytvořit relaci konverzace s zabezpečenou relací.

- R2303: Pokud doba života sekvence WS-ReliableMessaging přesáhne dobu života relace WS-, je `SecurityContextToken` nutné obnovit navázání pomocí konverzace WS-Secure pomocí odpovídající vazby obnovení služby WS-Secure.

- B2304: sekvence WS-ReliableMessaging nebo dvojice korelačních sekvencí konverzace jsou vždycky vázané na jednu relaci WS-SecureConversation.

- R2305: při sestavování s konverzací WS-Secure vyžaduje WCF respondér, aby `CreateSequence` zpráva obsahovala `wsse:SecurityTokenReference` element a `wsrm:UsesSequenceSTR` hlavičku.

 Příklad `UsesSequenceSTR` záhlaví.

```xml
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>
```

### <a name="composition-with-ssltls-sessions"></a>Složení s relacemi SSL/TLS

WCF nepodporuje kompozici s relacemi SSL/TLS:

- B2401: WCF negeneruje `wsrm:UsesSequenceSSL` hlavičku.

- R2402: iniciátor spolehlivého zasílání zpráv nesmí odeslat `CreateSequence` zprávu s `wsrm:UsesSequenceSSL` hlavičkou na respondér WCF.

### <a name="composition-with-ws-policy"></a>Složení pomocí WS-Policy

WCF podporuje dvě verze WS-Policy: WS-Policy 1,2 a WS-Policy 1,5.

## <a name="ws-reliablemessaging-ws-policy-assertion"></a>Kontrolní výraz WS-ReliableMessaging WS-Policy

WCF používá kontrolní výraz WS-ReliableMessaging WS-Policy `wsrm:RMAssertion` k popisu možností koncových bodů. Následuje seznam omezení, která platí pro WCF:

- B3001: WCF připojí `wsrmn:RMAssertion` kontrolní výraz WS-Policy k `wsdl:binding` elementům. WCF podporuje obě přílohy až `wsdl:binding` po `wsdl:port` elementy.

- B3002: WCF nikdy negeneruje `wsp:Optional` značku.

- B3003: při přístupu k `wsrmp:RMAssertion` kontrolnímu výrazu WS-Policy WCF ignoruje `wsp:Optional` značku a považuje zásadu WS-RM za povinnou.

- R3004: vzhledem k tomu, že WCF nevytváří s relacemi SSL/TLS, WCF neakceptuje zásady, které určují `wsrmp:SequenceTransportSecurity` .

- B3005: WCF vždy generuje `wsrmp:DeliveryAssurance` element.

- B3006: WCF vždy určuje `wsrmp:ExactlyOnce` záruku doručení.

- B3007: WCF generuje a přečte následující vlastnosti kontrolního výrazu WS-ReliableMessaging a poskytuje jejich kontrolu na WCF `ReliableSessionBindingElement` :

  - `netrmp:InactivityTimeout`

  - `netrmp:AcknowledgementInterval`

  Příklad `RMAssertion` .

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

## <a name="flow-control-ws-reliablemessaging-extension"></a>Rozšíření pro řízení toku WS-ReliableMessaging

WCF používá rozšiřitelnost WS-ReliableMessaging k zajištění volitelného dalšího užšího řízení toku zpráv sekvence.

Řízení toku je povoleno nastavením <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> vlastnosti na hodnotu `true` . Následuje seznam omezení, která platí pro WCF:

- B4001: Pokud je povoleno řízení toku spolehlivého zasílání zpráv, WCF vygeneruje `netrm:BufferRemaining` element v rozšiřitelnosti elementu `SequenceAcknowledgement` záhlaví, jak je znázorněno v následujícím příkladu.

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>8</netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- B4002: i když je povolené řízení toku spolehlivého zasílání zpráv, WCF nevyžaduje `netrm:BufferRemaining` element v `SequenceAcknowledgement` hlavičce.

- B4003: cíl spolehlivého zasílání zpráv WCF používá `netrm:BufferRemaining` k určení, kolik nových zpráv může ukládat do vyrovnávací paměti.

- B4004: Pokud je povolené řízení toku spolehlivých přenosů zpráv, používá zdroj dat služby WCF spolehlivý `netrm:BufferRemaining` přenos zpráv hodnotu k omezení přenosu zpráv.

- B4005: WCF generuje `netrm:BufferRemaining` celočíselné hodnoty mezi 0 a 4096 včetně a čte celočíselné hodnoty mezi 0 `xs:int` a `maxInclusive` hodnotou 214748364 včetně.

## <a name="message-exchange-patterns"></a>Vzorce výměny zpráv

Tato část popisuje chování služby WCF při použití protokolu WS-ReliableMessaging pro různé vzorce výměny zpráv. Pro každý vzor výměny zpráv se považují za tyto dva scénáře nasazení:

- Neadresovatelný iniciátor: iniciátor je za bránou firewall; Respondér může doručovat zprávy do iniciátoru pouze na odpovědích HTTP.

- Adresovatelný iniciátor: odesílat požadavky HTTP můžou jenom iniciátor a respondér. Jinými slovy, lze navázat dvě připojení s opačným protokolem HTTP.

### <a name="one-way-non-addressable-initiator"></a>Jednosměrný, neadresovatelný iniciátor

#### <a name="binding"></a>Vazba

WCF poskytuje jednosměrný vzor výměny zpráv pomocí jedné sekvence přes jeden kanál HTTP. WCF používá požadavky HTTP k přenosu všech zpráv od iniciátoru do respondérů a odpovědí HTTP na předávání všech zpráv od odpovídajícího příjemce k iniciátoru.

#### <a name="createsequence-exchange"></a>CreateSequence Exchange

Iniciátor WCF přenáší `CreateSequence` zprávu bez `Offer` prvku na požadavku HTTP a očekává `CreateSequenceResponse` zprávu v odpovědi HTTP. Respondér WCF vytvoří sekvenci a přenáší `CreateSequenceResponse` zprávu bez `Accept` elementu v odpovědi HTTP.

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

Iniciátor WCF zpracovává potvrzení odpovědi všech zpráv kromě zpráv `CreateSequence` a zpráv o chybách. Respondér WCF vždy přenáší samostatné potvrzení odezvy HTTP do všech sekvencí a `AckRequested` zpráv.

#### <a name="closesequence-exchange"></a>CloseSequence Exchange

Iniciátor WCF přenáší `CloseSequence` zprávu na požadavek HTTP a očekává `CreateSequenceResponse` zprávu v odpovědi HTTP. Respondér WCF přenáší `CloseSequenceResponse` zprávu v odpovědi HTTP.

#### <a name="terminatesequence-exchange"></a>TerminateSequence – Exchange

Iniciátor WCF přenáší `TerminateSequence` zprávu na požadavek HTTP a očekává `TerminateSequenceResponse` zprávu v odpovědi HTTP. Respondér WCF přenáší `TerminateSequenceResponse` zprávu v odpovědi HTTP.

### <a name="one-way-addressable-initiator"></a>Jedním ze způsobů, jak adresovatelné iniciátory

#### <a name="binding"></a>Vazba

WCF poskytuje jednosměrný vzor výměny zpráv pomocí jedné sekvence přes jeden příchozí a jeden odchozí kanál HTTP. WCF používá požadavky HTTP k přenosu všech zpráv. Všechny odpovědi HTTP mají prázdný text a stavový kód HTTP 202.

#### <a name="createsequence-exchange"></a>CreateSequence Exchange

Iniciátor WCF přenáší `CreateSequence` zprávu bez `Offer` elementu v požadavku HTTP. Respondér WCF vytvoří sekvenci a přenáší `CreateSequenceResponse` zprávu bez `Accept` elementu na požadavek HTTP.

### <a name="duplex-addressable-initiator"></a>Duplexní, adresovatelný iniciátor

#### <a name="binding"></a>Vazba

WCF poskytuje plně asynchronní obousměrný způsob výměny zpráv pomocí dvou sekvencí přes jeden příchozí a jeden odchozí kanál HTTP. Tento vzor výměny zpráv může být smíšený se `Request/Reply` `Addressable` vzorem výměny zpráv iniciátora v omezeném směru. WCF používá k přenosu všech zpráv požadavky HTTP. Všechny odpovědi HTTP mají prázdný text a stavový kód HTTP 202.

#### <a name="createsequence-exchange"></a>CreateSequence Exchange

Iniciátor WCF přenáší `CreateSequence` zprávu s `Offer` elementem v požadavku HTTP. Respondér WCF zajišťuje, že `CreateSequence` má `Offer` element, potom vytvoří sekvenci a přenáší `CreateSequenceResponse` zprávu s `Accept` prvkem.

#### <a name="sequence-lifetime"></a>Doba platnosti sekvence

WCF považuje dvě sekvence za jednu plně duplexní relaci.

Při generování chyby, která chybí jednu sekvenci, služba WCF očekává, že vzdálený koncový bod selže v obou sekvencích. Při čtení chyby, která chybí jednu sekvenci, chyby WCF obě sekvence.

WCF může zavřít svou odchozí sekvenci a nadále zpracovávat zprávy v její vstupní sekvenci. V opačném případě může WCF zpracovat ukončení příchozí sekvence a pokračovat v posílání zpráv ve výstupní sekvenci.

### <a name="request-reply-and-one-way-non-addressable-initiator"></a>Požadavek – odpověď a jednosměrný, neadresovatelný iniciátor

#### <a name="binding"></a>Vazba

WCF poskytuje jednosměrné a rychlé zprávy s požadavkem na odpověď pomocí dvou sekvencí přes jeden kanál HTTP. WCF používá požadavky HTTP k přenosu všech zpráv od iniciátoru do respondérů a odpovědí HTTP na předávání všech zpráv od odpovídajícího příjemce k iniciátoru.

#### <a name="createsequence-exchange"></a>CreateSequence Exchange

Iniciátor WCF přenáší `CreateSequence` zprávu s `Offer` elementem v požadavku HTTP a očekává `CreateSequenceResponse` zprávu v odpovědi HTTP. Respondér WCF vytvoří sekvenci a přenáší `CreateSequenceResponse` zprávu s `Accept` prvkem v odpovědi HTTP.

#### <a name="one-way-message"></a>Jednosměrná zpráva

Aby bylo možné provést jednosměrnou výměnu zpráv, iniciátor WCF odešle zprávu sekvence požadavku na požadavek HTTP a obdrží samostatnou `SequenceAcknowledgement` zprávu o odpovědi HTTP. `SequenceAcknowledgement`Musí potvrdit přenesenou zprávu.

Respondér WCF může odpovědět na žádost s potvrzením, chybou nebo odpovědí s prázdným tělem a kódem stavu HTTP 202.

#### <a name="two-way-messages"></a>Dvě jednosměrné zprávy

Aby bylo možné úspěšně dokončit oboustranný protokol výměny zpráv, iniciátor WCF přenese zprávu sekvence požadavku na požadavek HTTP a obdrží zprávu sekvence odpovědi v odpovědi HTTP. Odpověď musí `SequenceAcknowledgement` zasílat potvrzení přenosu zprávy sekvence požadavku.

Respondér WCF může odpovědět na požadavek pomocí odpovědi aplikace, chyby nebo odpovědi s prázdným kódem a stavovým kódem HTTP 202.

Z důvodu přítomnosti jednosměrných zpráv a časování odpovědí na aplikace není pořadové číslo zprávy sekvence požadavku a pořadové číslo zprávy odpovědi nijak korelace.

#### <a name="retrying-replies"></a>Opakování odpovědí

WCF spoléhá na korelaci požadavku HTTP na korelaci protokolu výměny zpráv se dvěma způsoby. Z tohoto důvodu se iniciátor WCF neukončí opakování zprávy sekvence požadavku při potvrzení zprávy sekvence požadavku, ale místo toho, aby odpověď HTTP zajišťovala odpověď `SequenceAcknowledgement` , aplikaci nebo chybu. Služby WCF respondér opakuje odpovědi na odpověď HTTP žádosti, na kterou je tato odpověď korelační.

#### <a name="closesequence-exchange"></a>CloseSequence Exchange

Po přijetí všech zpráv sekvence odpovědí a potvrzení pro všechny jednosměrné zprávy sekvence požadavků iniciátor WCF přenáší `CloseSequence` zprávu pro sekvenci požadavku HTTP a očekává `CloseSequenceResponse` odpověď HTTP.

Uzavírání sekvence požadavků implicitně uzavře sekvenci odpovědí. To znamená, že iniciátor WCF zahrnuje finální sekvenci odpovědí `SequenceAcknowledgement` ve `CloseSequence` zprávě a sekvence odpovědí nemá `CloseSequence` výměnu.

Respondér WCF zajišťuje potvrzení všech odpovědí a přenáší `CloseSequenceResponse` zprávu o odpovědi HTTP.

#### <a name="terminatesequence-exchange"></a>TerminateSequence – Exchange

Po přijetí `CloseSequenceResponse` zprávy INICIÁTOR WCF přenáší `TerminateSequence` zprávu pro sekvenci požadavku HTTP a očekává `TerminateSequenceResponse` odpověď HTTP.

Podobně jako `CloseSequence` Výměna sekvence požadavků ukončuje sekvenci odpovědí implicitně. To znamená, že iniciátor WCF zahrnuje finální sekvenci odpovědí `SequenceAcknowledgement` ve `TerminateSequence` zprávě a sekvence odpovědí nemá `TerminateSequence` výměnu.

Respondér WCF přenáší `TerminateSequenceResponse` zprávu v odpovědi HTTP.

### <a name="requestreply-addressable-initiator"></a>Požadavek nebo odpověď, adresovatelný iniciátor

#### <a name="binding"></a>Vazba

WCF poskytuje vzor výměny zpráv požadavek-odpověď pomocí dvou sekvencí přes jeden příchozí a jeden odchozí kanál HTTP. Tento vzor výměny zpráv může být `Duplex, Addressable` ve formě omezeného vzoru výměny zpráv iniciátoru. WCF používá požadavky HTTP k přenosu všech zpráv. Všechny odpovědi HTTP mají prázdný text a stavový kód HTTP 202.

#### <a name="createsequence-exchange"></a>CreateSequence Exchange

Iniciátor WCF přenáší `CreateSequence` zprávu s `Offer` elementem v požadavku HTTP. Respondér WCF zajišťuje, že `CreateSequence` má `Offer` element potom vytvoří sekvenci a přenáší `CreateSequenceResponse` zprávu s `Accept` prvkem.

#### <a name="requestreply-correlation"></a>Korelace žádosti a odpovědi

Následující postup se týká všech korelačních požadavků a odpovědí:

- Služba WCF zajišťuje, aby všechny zprávy žádosti o aplikace byly označeny jako `ReplyTo` odkaz koncového bodu a `MessageId` .

- WCF používá odkaz na místní koncový bod jako každou zprávu žádosti o aplikaci `ReplyTo` . Odkaz na místní koncový bod je `CreateSequence` zpráva `ReplyTo` pro iniciátor a `CreateSequence` zprávu `To` pro respondér.

- WCF zajišťuje, aby příchozí zprávy s požadavkem byly označeny `MessageId` a `ReplyTo` .

- Služba WCF zajišťuje, aby se `ReplyTo` identifikátor URI odkazu na koncový bod všech zpráv žádostí o aplikace shodoval s odkazem na místní koncový bod definovaným dříve.

- WCF zajišťuje, aby všechny odpovědi byly opatřeny správnými `RelatesTo` a `To` hlavičkou následujících `wsa` pravidel korelace požadavků a odpovědí.
