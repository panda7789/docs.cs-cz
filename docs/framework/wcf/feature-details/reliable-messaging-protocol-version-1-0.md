---
title: Protokol spolehlivého zasílání zpráv verze 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: 8d192afcffca52136d6d71de49770c5a5ad13895
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/29/2020
ms.locfileid: "84202307"
---
# <a name="reliable-messaging-protocol-version-10"></a>Protokol spolehlivého zasílání zpráv verze 1.0

Toto téma obsahuje podrobné informace o implementaci Windows Communication Foundation (WCF) pro protokol WS-Reliable Messaging únor 2005 (verze 1,0), který je nezbytný pro zajištění meziprovozu pomocí přenosu HTTP. WCF sleduje specifikace zasílání zpráv WS-Reliable s omezeními a vyjasněmi popsanými v tomto tématu. Počítejte s tím, že protokol WS-ReliableMessaging verze 1,0 je implementován od WinFX.

Protokol WS-Reliable Messaging únor 2005 se implementuje v WCF pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> .

Pro usnadnění práce téma používá následující role:

- Iniciátor: klient, který iniciuje vytvoření sekvence zpráv WS-Reliable

- Respondér: služba, která přijímá žádosti iniciátora

Tento dokument používá předpony a obory názvů v následující tabulce.

|Předpona|Obor názvů|
|------------|---------------|
|správcem|`http://schemas.xmlsoap.org/ws/2005/02/rm`|
|netrm|`http://schemas.microsoft.com/ws/2006/05/rm`|
|s|`http://www.w3.org/2003/05/soap-envelope`|
|WSA|`http://schemas.xmlsoap.org/ws/2005/08/addressing`|
|wsse|`http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd`|

## <a name="messaging"></a>Zasílání zpráv

### <a name="sequence-establishment-messages"></a>Sekvence – zprávy pro vytváření sekvencí

Technologie WCF `CreateSequence` implementuje `CreateSequenceResponse` zprávy a vytvoří spolehlivé pořadí zpráv. Platí následující omezení:

- B1101: iniciátor WCF negeneruje Volitelný element Expires ve `CreateSequence` zprávě nebo v případech, kdy `CreateSequence` zpráva obsahuje `Offer` element, volitelný `Expires` element v `Offer` elementu.

- B1102: při přístupu ke `CreateSequence` zprávě WCF `Responder` odesílá a přijímá oba `Expires` prvky, pokud existují, ale nepoužívá jejich hodnoty.

Zasílání zpráv WS-Reliable zavádí `Offer` mechanismus pro vytvoření dvou vzájemně se korelačních sekvencí, které tvoří relaci.

- R1103: Pokud `CreateSequence` obsahuje `Offer` element, musí mít respondér spolehlivého zasílání zpráv buď přijmout sekvenci a reagovat s `CreateSequenceResponse` `wsrm:Accept` elementem, který vytváří dvě korelační posloupnosti konverzace, nebo `CreateSequence` žádost odmítnout.

- R1104: `SequenceAcknowledgement` a zprávy aplikací, které jsou v sekvenci konverzace, musí být odeslány na `ReplyTo` odkaz na koncový bod v `CreateSequence` .

- R1105: `AcksTo` a `ReplyTo` odkazy koncových bodů v `CreateSequence` musí mít hodnoty adres, které odpovídají oktetu.

  Respondér WCF ověřuje, zda je část identifikátoru URI `AcksTo` a `ReplyTo` EPRs identická před vytvořením sekvence.

- Odkazy R1106: `AcksTo` a `ReplyTo` Endpoint v `CreateSequence` by měly mít stejnou sadu parametrů odkazu.

  WCF vynutilo, ale předpokládá, že [Reference Parameters] `AcksTo` a `ReplyTo` on `CreateSequence` jsou identické a používá [Reference Parameters] z `ReplyTo` reference koncového bodu pro potvrzení a zprávy sekvence konverzace.

- R1107: Pokud jsou vytvořeny dvě sekvence konverzace pomocí `Offer` mechanismu `SequenceAcknowledgement` a zprávy aplikací, které jsou přenášeny do sekvencí konverzace, musí být odeslány na `ReplyTo` odkaz koncového bodu `CreateSequence` .

- R1108: Pokud jsou vytvořeny dvě posloupnosti konverzace pomocí mechanismu nabídky, `[address]` vlastnost `wsrm:AcksTo` podřízeného prvku odkazu koncového bodu `wsrm:Accept` prvku `CreateSequenceResponse` musí odpovídat cílovému identifikátoru URI `CreateSequence` .

- R1109: při vytváření dvou sekvencí konverzace pomocí `Offer` mechanismu se zprávy odesílané iniciátorem a potvrzením zpráv podle respondéru musí odeslat do stejného odkazu na koncový bod.

  WCF používá zasílání zpráv WS-Reliable k navazování spolehlivých relací mezi iniciátorem a respondérem. Implementace zasílání zpráv WS-Reliable pro WCF zajišťuje spolehlivou relaci pro jednosměrné, požadavek-odpověď a plně duplexní vzory zasílání zpráv. Mechanizmus pro zasílání zpráv WS-Reliable `Offer` `CreateSequence` / `CreateSequenceResponse` vám umožní vytvořit dvě korelační posloupnosti konverzace a poskytuje protokol relace, který je vhodný pro všechny koncové body zprávy. Vzhledem k tomu, že WCF poskytuje záruku zabezpečení pro takovou relaci, včetně ucelené ochrany integrity relace, je praktické zajistit, aby zprávy určené ke stejné straně byly doručeny do stejného umístění. To také umožňuje piggyé potvrzení sekvence pro zprávy aplikací. Proto se omezení R1104, R1105 a R1108 vztahují na WCF.

Příklad `CreateSequence` zprávy

```xml
<s:Envelope>
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequence
    </a:Action>
    <a:ReplyTo>
      <a:Address>
         http://Business456.com/clientA
      </a:Address>
    </a:ReplyTo>
    <a:MessageID>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </a:MessageID>
    <a:To s:mustUnderstand="1">
      http://Business456.com/clientA
    </a:To>
  </s:Header>
  <s:Body>
    <wsrm:CreateSequence>
      <wsrm:AcksTo>
       <wsa:Address>
         http://Business456.com/clientA
       </wsa:Address>
     </wsrm:AcksTo>
     <wsrm:Offer>
      <wsrm:Identifier>
        urn:uuid:0afb8d36-bf26-4776-b8cf-8c91fddb5496
      </wsrm:Identifier>
     </wsrm:Offer>
   </wsrm:CreateSequence>
  </s:Body>
</s:Envelope>
```

 Příklad `CreateSequenceResponse` zprávy

```xml
<s:Envelope>
  <s:Header>
    <a:Action s:mustUnderstand="1">
      http://schemas.xmlsoap.org/ws/2005/02/rm/CreateSequenceResponse
    </a:Action>
    <a:RelatesTo>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </a:RelatesTo>
    <a:To s:mustUnderstand="1">
      http://Business456.com/clientA
    </a:To>
  </s:Header>
  <s:Body>
   <wsrm:CreateSequenceResponse>
    <Identifier>
     urn:uuid:eea0a36c-b38a-43e8-8c76-2fabe2d76386
    </Identifier>
    <Accept>
    <AcksTo>
      <a:Address>
        http://BusinessABC.com/serviceA
      </a:Address>
    </AcksTo>
    </Accept>
   </wsrm:CreateSequenceResponse>
  </s:Body>
</s:Envelope>
```

### <a name="sequence"></a>Sequence

Následuje seznam omezení, která platí pro sekvence:

- B1201: WCF generuje a přistupuje k pořadovým číslům, která nejsou vyšší než `xs:long` maximální celková hodnota, 9223372036854775807.

- B1202: WCF vždy generuje poslední zprávu těle s identifikátorem URI akce `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .

- B1203: WCF přijme a doručí zprávu s hlavičkou sekvence, která obsahuje `LastMessage` element, pokud identifikátor URI akce není `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` .

Příklad záhlaví sekvence

```xml
<wsrm:Sequence>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
  <wsrm:MessageNumber>
    10
  </wsrm:MessageNumber>
  <wsrm:LastMessage/>
 </wsrm:Sequence>
```

### <a name="ackrequested-header"></a>AckRequested hlavičku

WCF používá `AckRequested` záhlaví jako mechanismus pro udržení naživu. WCF negeneruje Volitelný `MessageNumber` element. Po přijetí zprávy s `AckRequested` hlavičkou, která obsahuje `MessageNumber` element, WCF ignoruje `MessageNumber` hodnotu prvku, jak je znázorněno v následujícím příkladu.

```xml
<wsrm:AckRequested>
  <wsrm:Identifier>
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
  </wsrm:Identifier>
</wsrm:AckRequested>
```

### <a name="sequenceacknowledgement-header"></a>SequenceAcknowledgement hlavičku

WCF používá Piggy mechanismus pro potvrzení sekvencí, která jsou k dispozici v zasílání zpráv WS-Reliable.

- R1401: Pokud se pomocí mechanismu vytvoří dvě posloupnosti konverzace `Offer` , `SequenceAcknowledgement` může se hlavička zahrnout do jakékoli zprávy aplikace předané zamýšlenému příjemci.

- B1402: Pokud WCF musí vygenerovat potvrzení před přijetím zpráv sekvence (například pro splnění `AckRequested` zprávy), WCF vygeneruje `SequenceAcknowledgement` hlavičku, která obsahuje rozsah 0-0, jak je znázorněno v následujícím příkladu.

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="0" Lower="0"/>
  </wsrm:SequenceAcknowledgement>
  ```

- B1403: WCF negeneruje `SequenceAcknowledgement` hlavičky, které obsahují `Nack` element, ale podporuje `Nack` prvky.

### <a name="ws-reliablemessaging-faults"></a>Chyby WS-ReliableMessaging

Následující seznam obsahuje omezení, která se vztahují na implementaci WCF pro zasílání zpráv WS-Reliable:

- B1501: WCF negeneruje `MessageNumberRollover` chyby.

- B1502: koncový bod WCF může generovat `CreateSequenceRefused` chyby, jak je popsáno ve specifikaci.

- B1503: když koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení, WCF vygeneruje další `CreateSequenceRefused` podkód chyby, `netrm:ConnectionLimitReached` jak je znázorněno v následujícím příkladu.

  ```xml
  <s:Envelope>
    <s:Header>
      <wsa:Action>
        http://schemas.xmlsoap.org/ws/2005/08/addressing/fault
      </wsa:Action>
    </s:Header>
    <s:Body>
      <s:Fault>
        <s:Code>
          <s:Value>
            s:Receiver
          </s:Value>
          <s:Subcode>
            <s:Value>
              wsrm:CreateSequenceRefused
            </s:Value>
            <s:Subcode>
              <s:Value>
                netrm:ConnectionLimitReached
              </s:Value>
            </s:Subcode>
          </s:Subcode>
        </s:Code>
        <s:Reason>
          <s:Text xml:lang="en">
            [Reason]
          </s:Text>
        </s:Reason>
      </s:Fault>
    </s:Body>
  </s:Envelope>
  ```

### <a name="ws-addressing-faults"></a>Chyby WS-Addressing

Protože zasílání zpráv WS-Reliable používá WS-Addressing, služba WCF WS-Reliable Messaging může způsobit chyby WS-Addressing. Tato část se zabývá chybami WS-Addressing, které WCF explicitně generuje ve vrstvě zasílání zpráv WS-Reliable:

- B1601: WCF vygeneruje hlavičku adresování zpráv o chybách, která je vyžadována, pokud je splněna jedna z následujících podmínek:

  - Ve zprávě chybí `Sequence` záhlaví a `Action` záhlaví.

  - Ve `CreateSequence` zprávě chybí `MessageId` záhlaví.

  - Ve `CreateSequence` zprávě chybí `ReplyTo` záhlaví.

- B1602: WCF vygeneruje akci selhání, která není podporována v odpovědi na zprávu s chybějící `Sequence` hlavičkou a má `Action` záhlaví, které není rozpoznáno ve specifikaci zasílání zpráv WS-Reliable.

- B1603: WCF generuje koncový bod selhání, aby označoval, že koncový bod nezpracovává sekvenci na základě zkoumání `CreateSequence` hlaviček adresování zprávy.

## <a name="protocol-composition"></a>Složení protokolu

### <a name="composition-with-ws-addressing"></a>Složení pomocí WS-Addressing

Služba WCF podporuje dvě verze elementu WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] a W3C WS-Addressing 1,0 Recommendations [WS-ADDR-CORE] a [WS-ADDR-SOAP].

Specifikace zasílání zpráv WS-Reliable zmiňuje pouze WS-Addressing 2004/08, ale neomezuje použití verze WS-Addressing. Následuje seznam omezení, která platí pro WCF:

- R2101: Služba WS-Addressing 2004/08 a WS-Addressing 1,0 se dá použít se zasíláním zpráv WS-Reliable.

- R2102: v rámci dané sekvence zasílání zpráv WS-Reliable musí být použita jedna verze elementu WS-Addressing nebo dvojice sekvencí konverzace v souvislosti s použitím `wsrm:Offer` mechanismu.

### <a name="composition-with-soap"></a>Složení pomocí protokolu SOAP

Služba WCF podporuje použití protokolu SOAP 1,1 i SOAP 1,2 se zasíláním zpráv WS-Reliable.

### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Složení pomocí WS-Security a WS-SecureConversation

Služba WCF poskytuje ochranu pro sekvence zasílání zpráv WS-Reliable pomocí zabezpečeného přenosu (HTTPS), složení WS-Security a složení s konverzací WS-Secure. Následuje seznam omezení, která platí pro WCF:

- R2301: aby byla zajištěna ochrana integrity sekvence zasílání zpráv WS-Reliable, kromě integrity a důvěrnosti jednotlivých zpráv, vyžaduje WCF použití konverzace WS-Secure.

- R2302: AWS – před vytvořením posloupností zasílání zpráv WS-Reliable je nutné zřídit relaci konverzace s zabezpečeným zabezpečením.

- R2303: Pokud doba trvání sekvence zasílání zpráv WS-Reliable přesáhne dobu života relace WS-Secure, je `SecurityContextToken` nutné obnovit pomocí příslušné vazby obnovení WS-Secure konverzaci.

- B2304: sekvence zasílání zpráv WS-Reliable nebo dvojice korelačních sekvencí konverzace jsou vždycky vázané na jednu relaci WS-SecureConversation.

  Zdroj WCF generuje `wsse:SecurityTokenReference` element v sekci rozšiřitelnosti elementu `CreateSequence` zprávy.

- R2305: Pokud se skládá s konverzací WS-Secure, `CreateSequence` musí zpráva obsahovat `wsse:SecurityTokenReference` element.

## <a name="ws-reliable-messaging-ws-policy-assertion"></a>WS-Reliable Messaging WS-Policy – kontrolní výraz

WCF používá kontrolní výraz WS-Reliable zasílání zpráv WS-Policy `wsrm:RMAssertion` k popisu možností koncových bodů. Následuje seznam omezení, která platí pro WCF:

- B3001: WCF připojí `wsrm:RMAssertion` kontrolní výraz WS-Policy k `wsdl:binding` elementům. WCF podporuje obě přílohy až `wsdl:binding` po `wsdl:port` elementy.

- B3002: WCF podporuje následující volitelné vlastnosti kontrolního výrazu protokolu WS-Reliable pro zasílání zpráv a poskytuje kontrolu nad nimi na WCF `ReliableMessagingBindingElement` :

  - `wsrm:InactivityTimeout`

  - `wsrm:AcknowledgementInterval`

  Následuje příklad.

  ```xml
  <wsrm:RMAssertion>
    <wsrm:InactivityTimeout Milliseconds="600000" />
    <wsrm:AcknowledgementInterval Milliseconds="200" />
  </wsrm:RMAssertion>
  ```

## <a name="flow-control-ws-reliable-messaging-extension"></a>Rozšíření pro zasílání zpráv WS-Reliable pro řízení toku

WCF používá rozšiřitelnost zpráv WS-Reliable k zajištění volitelného dalšího užšího řízení nad tokem zpráv sekvence.

Řízení toku je povoleno nastavením <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> vlastnosti na hodnotu `true` . Následuje seznam omezení, která platí pro WCF:

- B4001: Pokud je povoleno řízení toku spolehlivého zasílání zpráv, WCF vygeneruje `netrm:BufferRemaining` element v rozšiřitelnosti elementu v `SequenceAcknowledgement` hlavičce.

- B4002: Pokud je povoleno řízení toku spolehlivého zasílání zpráv, WCF nevyžaduje `netrm:BufferRemaining` element, který by měl být přítomen v `SequenceAcknowledgement` hlavičce, jak je znázorněno v následujícím příkladu.

  ```xml
  <wsrm:SequenceAcknowledgement>
    <wsrm:Identifier>
      http://fabrikam123.com/abc
    </wsrm:Identifier>
    <wsrm:AcknowledgementRange Upper="1" Lower="1"/>
    <netrm:BufferRemaining>
      8
    </netrm:BufferRemaining>
  </wsrm:SequenceAcknowledgement>
  ```

- B4003: WCF používá `netrm:BufferRemaining` k určení, kolik nových zpráv může být cílem spolehlivého zasílání zpráv ukládat do vyrovnávací paměti.

- B4004: služba spolehlivého zasílání zpráv WCF omezuje počet přenesených zpráv, když cílová aplikace spolehlivého zasílání zpráv nemůže přijímat zprávy rychle. Zprávy cíle spolehlivého zasílání zpráv a hodnota elementu se přemístí na 0.

- B4005: WCF generuje `netrm:BufferRemaining` celočíselné hodnoty mezi 0 a 4096 včetně a čte celočíselné hodnoty mezi 0 `xs:int` a `maxInclusive` hodnotou 214748364 včetně.

## <a name="message-exchange-patterns"></a>Vzorce výměny zpráv

Tato část popisuje chování služby WCF při zasílání zpráv WS-Reliable pro různé vzorce výměny zpráv. Pro každý vzor výměny zpráv se považují za tyto dva scénáře nasazení:

- Iniciátor bez adresování: iniciátor je za bránou firewall; Respondér může doručovat zprávy iniciátorovi pouze v odpovědích HTTP.

- Adresovatelný iniciátor: odesílat požadavky HTTP můžou jenom iniciátor a respondér. Jinými slovy, lze navázat dvě připojení s opačným protokolem HTTP.

### <a name="one-way-non-addressable-initiator"></a>Jednosměrný, neadresovatelný iniciátor

#### <a name="binding"></a>Vazba

WCF poskytuje jednosměrný vzor výměny zpráv pomocí jedné sekvence přes jeden kanál HTTP. WCF používá požadavky HTTP k přenosu všech zpráv z RMS do RMD a odpověď protokolu HTTP pro přenos všech zpráv z RMD do služby RMS.

#### <a name="createsequence-exchange"></a>CreateSequence Exchange

Iniciátor WCF vygeneruje `CreateSequence` zprávu bez nabídky. Respondér WCF zajišťuje, že `CreateSequence` před vytvořením sekvence neobsahuje žádnou nabídku. Respondér WCF odpoví na `CreateSequence` požadavek `CreateSequenceResponse` zprávou.

#### <a name="sequenceacknowledgement"></a>SequenceAcknowledgement

Iniciátor WCF zpracovává potvrzení odpovědi všech zpráv kromě zpráv `CreateSequence` a zpráv o chybách. Respondér WCF vždy generuje samostatné potvrzení v reakci na jak sekvenci, tak `AckRequested` zprávy.

#### <a name="terminatesequence-message"></a>Zpráva TerminateSequence

WCF se považuje `TerminateSequence` za jednosměrnou operaci, což znamená, že odpověď HTTP má prázdný kód a stavový kód http 202.

### <a name="one-way-addressable-initiator"></a>Jedním ze způsobů, jak adresovatelné iniciátory

#### <a name="binding"></a>Vazba

WCF poskytuje jednosměrný vzor výměny zpráv pomocí jedné sekvence přes příchozí a odchozí kanál http. WCF používá požadavky HTTP k přenosu všech zpráv. Všechny odpovědi HTTP mají prázdný text a stavový kód HTTP 202.

#### <a name="createsequence-exchange"></a>CreateSequence Exchange

Iniciátor WCF vygeneruje `CreateSequence` zprávu bez nabídky. Respondér WCF zajišťuje, aby `CreateSequence` před vytvořením sekvence nedošlo k žádné nabídce. Respondér WCF přenáší `CreateSequenceResponse` zprávu na požadavek HTTP adresovaný `ReplyTo` odkazem na koncový bod.

### <a name="duplex-addressable-initiator"></a>Duplexní, adresovatelný iniciátor

#### <a name="binding"></a>Vazba

WCF poskytuje plně asynchronní obousměrný vzor výměny zpráv pomocí dvou sekvencí přes příchozí a odchozí kanál HTTP. WCF používá požadavky HTTP k přenosu všech zpráv. Všechny odpovědi HTTP mají prázdný text a stavový kód HTTP 202.

#### <a name="createsequence-exchange"></a>CreateSequence Exchange

Iniciátor WCF vygeneruje `CreateSequence` zprávu s nabídkou. Respondér WCF zajišťuje, že `CreateSequence` před vytvořením sekvence obsahuje nabídku. WCF pošle `CreateSequenceResponse` požadavek na protokol HTTP adresovaný na `CreateSequence` `ReplyTo` odkaz na koncový bod.

#### <a name="sequence-lifetime"></a>Doba platnosti sekvence

WCF považuje dvě sekvence za jednu plně duplexní relaci.

Při generování chyby, která chybí jednu sekvenci, služba WCF očekává, že vzdálený koncový bod selže v obou sekvencích. Při čtení chyby, která chybí jednu sekvenci, chyby WCF obě sekvence.

WCF může zavřít svou odchozí sekvenci a nadále zpracovávat zprávy v její vstupní sekvenci. V opačném případě může WCF zpracovat ukončení příchozí sekvence a pokračovat v posílání zpráv ve výstupní sekvenci.

### <a name="request-reply-non-addressable-initiator"></a>Požadavek-odpověď, neadresovatelný iniciátor

#### <a name="binding"></a>Vazba

WCF poskytuje jednosměrné a rychlé zprávy s požadavkem na odpověď pomocí dvou sekvencí přes jeden kanál HTTP. WCF používá požadavky HTTP k přenosu zpráv sekvence požadavků a používá odpovědi HTTP k přenosu zpráv sekvence odpovědí.

#### <a name="createsequence-exchange"></a>CreateSequence Exchange

Iniciátor WCF vygeneruje `CreateSequence` zprávu s nabídkou. Respondér WCF zajišťuje, že `CreateSequence` před vytvořením sekvence obsahuje nabídku. Respondér WCF odpoví na `CreateSequence` požadavek `CreateSequenceResponse` zprávou.

#### <a name="one-way-message"></a>Jednosměrná zpráva

Aby bylo možné úspěšně provést jednosměrnou výměnu zpráv, iniciátor WCF přenáší zprávu sekvence požadavků na požadavek HTTP a obdrží samostatnou `SequenceAcknowledgement` zprávu o odpovědi HTTP. `SequenceAcknowledgement`Musí potvrdit přenesenou zprávu.

Respondér WCF může odpovědět na žádost s potvrzením, chybou nebo odpovědí s prázdným tělem a kódem stavu HTTP 202.

#### <a name="two-way-messages"></a>Dvě jednosměrné zprávy

Aby bylo možné úspěšně dokončit oboustranný protokol výměny zpráv, iniciátor WCF přenese zprávu sekvence požadavku na požadavek HTTP a obdrží zprávu sekvence odpovědi v odpovědi HTTP. Odpověď musí `SequenceAcknowledgement` zasílat potvrzení přenosu zprávy sekvence požadavku.

Respondér WCF může odpovědět na požadavek pomocí odpovědi aplikace, chyby nebo odpovědi s prázdným kódem a stavovým kódem HTTP 202.

Z důvodu přítomnosti jednosměrných zpráv a časování odpovědí na aplikace není pořadové číslo zprávy sekvence požadavku a pořadové číslo zprávy odpovědi nijak korelace.

#### <a name="retrying-replies"></a>Opakování odpovědí

WCF spoléhá na korelaci požadavku HTTP na korelaci protokolu výměny zpráv se dvěma způsoby. Z tohoto důvodu se iniciátor WCF neukončí opakování zprávy sekvence požadavku při potvrzení zprávy sekvence požadavku, ale místo toho, aby odpověď protokolu HTTP zajišťovala potvrzení, zprávu uživatele nebo chybu. Respondér WCF reaguje na odezvu požadavku HTTP žádosti, na kterou je tato odpověď korelační.

#### <a name="lastmessage-exchange"></a>Třídy LastMessage Exchange

Iniciátor WCF vygeneruje a přenáší prázdnou poslední zprávu těle na nožkě požadavku HTTP. WCF vyžaduje odpověď, ale ignoruje skutečnou zprávu odpovědi. Respondér WCF odpovídá poslední zprávě s prázdným těle sekvencí požadavku pomocí poslední zprávy těle sekvence odpovědí.

Pokud respondér WCF obdrží poslední zprávu, ve které není identifikátor URI akce, odešle `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage` odpověď WCF k poslední zprávě. V případě obousměrného protokolu výměny zpráv ponese Poslední zpráva zprávu aplikace. v případě jednosměrného protokolu výměny zpráv je poslední zpráva prázdná.

V rámci služby WCF Responder není vyžadováno potvrzení pro poslední zprávu prázdného těle sekvence odpovědí.

#### <a name="terminatesequence-exchange"></a>TerminateSequence – Exchange

Když všechny požadavky obdrží platnou odpověď, iniciátor WCF vygeneruje a přenese zprávu sekvence požadavků `TerminateSequence` na nožku požadavku HTTP. WCF vyžaduje odpověď, ale ignoruje skutečnou zprávu odpovědi. Respondér WCF odpoví na zprávu pořadí požadavků `TerminateSequence` pomocí zprávy sekvence odpovědí `TerminateSequence` .

V normální sekvenci vypnutí obě `TerminateSequence` zprávy zanášejí celý rozsah `SequenceAcknowledgement` .

### <a name="requestreply-addressable-initiator"></a>Požadavek nebo odpověď, adresovatelný iniciátor

#### <a name="binding"></a>Vazba

WCF poskytuje vzor výměny zpráv požadavek-odpověď pomocí dvou sekvencí přes příchozí a odchozí kanál HTTP. WCF používá požadavky HTTP k přenosu všech zpráv. Všechny odpovědi HTTP mají prázdný text a stavový kód HTTP 202.

#### <a name="createsequence-exchange"></a>CreateSequence Exchange

Iniciátor WCF vygeneruje `CreateSequence` zprávu s nabídkou. Respondér WCF zajišťuje, že `CreateSequence` před vytvořením sekvence obsahuje nabídku. WCF pošle `CreateSequenceResponse` požadavek na protokol HTTP adresovaný na `CreateSequence` `ReplyTo` odkaz na koncový bod.

#### <a name="requestreply-correlation"></a>Korelace žádosti a odpovědi

Iniciátor WCF zajišťuje, aby všechny zprávy žádosti o aplikace byly označeny `MessageId` `ReplyTo` odkazem a koncovým bodem. Iniciátor WCF používá `CreateSequence` `ReplyTo` odkaz na koncový bod zprávy na každé zprávě žádosti o aplikaci. Respondér WCF vyžaduje, aby příchozí zprávy žádosti byly označeny `MessageId` a `ReplyTo` . Respondér WCF zajišťuje shodu identifikátoru URI odkazu koncového bodu pro `CreateSequence` všechny zprávy žádostí o aplikaci i všechny.
