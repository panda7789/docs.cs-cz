---
title: Protokol spolehlivého zasílání zpráv verze 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: cff07ae23e83a68c4cafa1ca122d84db98163d0d
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/04/2018
ms.locfileid: "48583949"
---
# <a name="reliable-messaging-protocol-version-10"></a>Protokol spolehlivého zasílání zpráv verze 1.0
Toto téma obsahuje podrobné informace o nasazení Windows Communication Foundation (WCF) pro posílání WS-Reliable February 2005 (verze 1.0) protokolu, které jsou nezbytné pro spolupráci pomocí přenos pomocí protokolu HTTP. WCF dodržuje specifikaci WS-Reliable zasílání zpráv s omezením a vyjasnění je vysvětleno v tomto tématu. Všimněte si, že protokol WS-ReliableMessaging verze 1.0 se implementuje počínaje [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 WS-Reliable zasílání zpráv February 2005 protokol je implementován ve službě WCF pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Pro usnadnění práce tématu používá Tyhle role:  
  
-   Iniciátor: klienta, který iniciuje WS-Reliable zpráva sekvence vytvoření  
  
-   Odpovídající zařízení: služby, která bude přijímat žádosti je iniciátor  
  
 Tento dokument používá předpony a obory názvů v následující tabulce.  
  
|Předpona|Obor názvů|  
|------------|---------------|  
|Správce systémových prostředků|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a>Zasílání zpráv  
  
### <a name="sequence-establishment-messages"></a>Pořadí zpráv zařízení  
 Implementuje WCF `CreateSequence` a `CreateSequenceResponse` zprávy k navázání spolehlivé zprávy sekvence. Platí následující omezení:  
  
-   B1101: WCF iniciátoru negeneruje Volitelný element platnost vyprší v `CreateSequence` zprávy nebo v případech při `CreateSequence` zpráva obsahuje `Offer` elementu, volitelný `Expires` element v `Offer` elementu.  
  
-   B1102: Při přístupu k `CreateSequence` zpráv WCF`Responder` odesílá a přijímá obě `Expires` elementů, pokud existují, ale nepoužívá jejich hodnoty.  
  
 Zasílání zpráv WS-Reliable zavádí `Offer` mechanismus k navázání dvou komunikaci korelační sekvence, které tvoří relace.  
  
-   R1103: Pokud `CreateSequence` obsahuje `Offer` element spolehlivé zasílání zpráv respondér musí přijmout sekvenci a odpoví `CreateSequenceResponse` , která obsahuje `wsrm:Accept` elementu, které tvoří dvě korelační komunikaci pořadí nebo odmítnout `CreateSequence` požadavku.  
  
-   R1104: `SequenceAcknowledgement` a zprávy aplikace směřující na první sekvenci se musí odeslat na `ReplyTo` odkaz na koncový bod `CreateSequence`.  
  
-   R1105: `AcksTo` a `ReplyTo` v odkazuje na koncový bod `CreateSequence` musí mít adresa hodnoty, které odpovídají octet-wise.  
  
     WCF respondér ověřuje, že část identifikátoru URI `AcksTo` a `ReplyTo` odkazy na koncové body jsou identické před vytvořením sekvenci.  
  
-   R1106: `AcksTo` a `ReplyTo` odkazy na koncový bod v `CreateSequence` by měly mít stejnou sadu parametrů odkazu.  
  
     WCF nevynucuje, ale předpokládá, že [odkaz na parametry] `AcksTo` a `ReplyTo` na `CreateSequence` jsou identické a používá [odkaz na parametry] z `ReplyTo` reference koncového bodu pro potvrzení a konverzace pořadí zpráv.  
  
-   R1107: Při komunikaci dvě pořadí jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` a zasílají zprávy aplikace směřující na pořadí konverzace `ReplyTo` odkaz na koncový bod `CreateSequence`.  
  
-   R1108: Při komunikaci dvě pořadí jsou vytvořena pomocí mechanismu nabídku `[address]` vlastnost `wsrm:AcksTo` podřízený element Reference koncového bodu `wsrm:Accept` elementu `CreateSequenceResponse` musí odpovídat byte-wise cílový identifikátor URI z `CreateSequence`.  
  
-   R1109: Při komunikaci dvě pořadí jsou vytvořena pomocí `Offer` mechanismus, zprávy odeslané iniciátoru a potvrzení do zprávy podle respondér se musí odeslat na stejné Reference koncového bodu.  
  
     WCF používá k navázání spolehlivé relace mezi iniciátor i respondér zasílání zpráv WS-Reliable. Implementace zasílání zpráv WS-Reliable WCF poskytuje spolehlivé relace pro jednosměrný požadavek odpověď a plně duplexní způsobů zasílání zpráv. Posílání WS-Reliable `Offer` mechanismus `CreateSequence` / `CreateSequenceResponse` umožňuje vytvoření dvou sekvencí korelační konverzace a poskytuje protokol relace, který je vhodný pro všechny koncové body zprávy. Protože WCF poskytuje záruku zabezpečení pro relaci, včetně začátku do konce ochranu integrity relace, je potřeba Ujistěte se, že stejný cíl přicházejí zprávy určené stejné osobě. Díky tomu také Prasátko zálohováním pořadí potvrzení na zprávy aplikace. Proto platí omezení R1104 R1105 a R1108 pro WCF.  
  
 Příklad `CreateSequence` zprávy.  
  
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
  
 Příklad `CreateSequenceResponse` zprávy.  
  
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
  
### <a name="sequence"></a>Pořadí  
 Následuje seznam omezení, které se vztahují na pořadí:  
  
-   Generuje B1201:WCF a přístupy pořadí čísel vyšší než `xs:long`na maximální hodnotu (včetně), 9223372036854775807.  
  
-   B1202:WCF vždy vygeneruje prázdný-s v těle poslední zprávu s akcí identifikátor URI z `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.  
  
-   B1203: WCF přijímá a doručí zprávu s hlavičkou sekvenci, který obsahuje `LastMessage` elementu, dokud není identifikátor URI akce `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`.  
  
 Příklad pořadí záhlaví.  
  
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
  
### <a name="ackrequested-header"></a>Záhlaví AckRequested  
 Používá WCF `AckRequested` záhlaví jako vhodný mechanismus keep-alive. WCF negeneruje nepovinný `MessageNumber` elementu. Při přijetí zprávy s `AckRequested` hlavičku, která obsahuje `MessageNumber` ignoruje WCF elementu, `MessageNumber` hodnota elementu, jak je znázorněno v následujícím příkladu.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a>Záhlaví SequenceAcknowledgement do důvěryhodné  
 WCF používá Prasátko back mechanismus pro potvrzení pořadí součástí zasílání zpráv WS-Reliable.  
  
-   R1401: Při komunikaci dvě pořadí jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` záhlaví mohou být zahrnuty do jakékoli aplikace zprávy odesílané informace zamýšlený příjemce.  
  
-   B1402: Při WCF musíte vygenerovat potvrzení před obdržením všechny zprávy sekvence (například splňují `AckRequested` zpráva), vygeneruje WCF `SequenceAcknowledgement` hlavičku, která obsahuje rozsah 0-0, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B1403: WCF negeneruje `SequenceAcknowledgement` hlavičky, které obsahují `Nack` element, ale podporuje `Nack` elementy.  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging chyb  
 Následuje seznam omezení, které se vztahují k implementaci WCF zasílání zpráv WS-Reliable chyb:  
  
-   B1501: WCF negeneruje `MessageNumberRollover` chyb.  
  
-   Koncový bod B1502:WCF může generovat `CreateSequenceRefused` chyb, jak je popsáno ve specifikaci.  
  
-   B1503:when koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení, vygeneruje dalších WCF `CreateSequenceRefused` selhání podřízeného, `netrm:ConnectionLimitReached`, jak je znázorněno v následujícím příkladu.  
  
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
  
### <a name="ws-addressing-faults"></a>WS-Addressing chyb  
 Protože zasílání zpráv WS-Reliable používá WS-Addressing, zasílání zpráv WS-Reliable WCF implementace může způsobit chyby WS-Addressing. Tato část zahrnuje chyby WS-Addressing, WCF, které explicitně vytvoří ve vrstvě zasílání zpráv WS-Reliable:  
  
-   B1601:WCF generuje selhání zpráva adresování požadované záhlaví, když je splněna jedna z následujících akcí:  
  
    -   Chybí zpráva `Sequence` záhlaví a `Action` záhlaví.  
  
    -   A `CreateSequence` chybí zpráva `MessageId` záhlaví.  
  
    -   A `CreateSequence` chybí zpráva `ReplyTo` záhlaví.  
  
-   B1602:WCF generuje selhání akce není podporována při zprávu, která chybí `Sequence` záhlaví a má `Action` hlavičku, která není rozpoznaná ve specifikaci zasílání zpráv WS-Reliable.  
  
-   B1603:WCF generuje selhání koncového bodu není k dispozici pro označení, že koncový bod nezpracovává pořadí na základě posouzení `CreateSequence` adrese záhlaví zprávy.  
  
## <a name="protocol-composition"></a>Protokol sestavení  
  
### <a name="composition-with-ws-addressing"></a>Kompozice s WS-Addressing  
 Podporuje dvě verze WS-Addressing WCF: WS-Addressing 2004/08 [WS-ADDR] a 1.0 doporučení W3C WS-Addressing [WS-ADDR – CORE] a [WS-ADDR SOAP].  
  
 While zmínky o zasílání zpráv WS-Reliable specifikace WS-Addressing 2004/08 pouze neomezuje verze WS-Addressing má být použit. Následuje seznam omezení, které se vztahují na WCF:  
  
-   R2101: oba WS-Addressing 2004/08 a WS-Addressing 1.0 je možné pomocí zasílání zpráv WS-Reliable.  
  
-   R2102:A jednu verzi elementu WS-Addressing musí využívat v rámci dané sekvence WS-Reliable zasílání zpráv nebo dvojice posloupností první korelační pomocí `wsrm:Offer` mechanismus.  
  
### <a name="composition-with-soap"></a>Složení u protokolu SOAP  
 WCF podporuje použití SOAP 1.1 a SOAP 1.2 zasílání zpráv WS-Reliable.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Kompozice s WS-Security a WS-SecureConversation  
 WCF poskytuje ochranu pro zasílání zpráv WS-Reliable pořadí pomocí zabezpečeného přenosu (HTTPS), kompozice s WS-Security a skládání s WS-Secure Conversation. Následuje seznam omezení, které se vztahují na WCF:  
  
-   R2301: ochrana integrity sekvenci zasílání zpráv WS-Reliable kromě integritu a důvěrnost jednotlivé zprávy, WCF vyžaduje, že musí použít WS-Secure Conversation.  
  
-   R2302:awS-zabezpečenou konverzací relace musí být vytvořen před navazování sequence(s) zasílání zpráv WS-Reliable.  
  
-   R2303: Pokud posílání WS-Reliable pořadí životnost překročí WS-Secure Conversation životnost relace `SecurityContextToken` lze navázat pomocí WS-Secure Conversation musí obnovovat pomocí odpovídající vazby WS-Secure obnovení konverzace.  
  
-   B2304:ws – pořadí spolehlivé zasílání zpráv nebo dvojice posloupností korelační konverzace jsou vždy vázány na jedné relace WS-SecureConversation.  
  
     Vygeneruje zdroj WCF `wsse:SecurityTokenReference` element v oddílu rozšíření elementu `CreateSequence` zprávy.  
  
-   R2305:when utvořený za použití WS-Secure Conversation `CreateSequence` musí obsahovat zprávu `wsse:SecurityTokenReference` elementu.  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a>WS-Reliable kontrolní výraz zasílání zpráv WS-Policy  
 WCF používá WS-Reliable zasílání zpráv WS-Policy kontrolní `wsrm:RMAssertion` k popisu funkce koncových bodů. Následuje seznam omezení, které se vztahují na WCF:  
  
-   B3001: Připojí WCF `wsrm:RMAssertion` WS-Policy kontrolního výrazu k `wsdl:binding` elementy. WCF podporuje obě příloh `wsdl:binding` a `wsdl:port` elementy.  
  
-   B3002: WCF podporuje následující volitelné vlastnosti zasílání zpráv WS-Reliable kontrolní výraz a zajišťuje kontrolu nad nimi v WCF`ReliableMessagingBindingElement`:  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     Následuje příklad.  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a>Tok řízení zasílání zpráv WS-Reliable rozšíření  
 K zajištění volitelné další přesnější kontrolu nad tok pořadí zpráv WCF používá rozšíření zasílání zpráv WS-Reliable.  
  
 Řízení toku se povoluje nastavením `ReliableSessionBindingElement`společnosti `FlowControlEnabled``bool` vlastnost `true`. Následuje seznam omezení, které se vztahují na WCF:  
  
-   B4001: WCF generuje když je povolené spolehlivé zasílání zpráv řízení toku, `netrm:BufferRemaining` element v elementu rozšiřitelnost `SequenceAcknowledgement` záhlaví.  
  
-   B4002: Když je povolené spolehlivé zasílání zpráv řízení toku, WCF nevyžaduje, aby `netrm:BufferRemaining` prvek nacházet v `SequenceAcknowledgement` záhlaví, jak je znázorněno v následujícím příkladu.  
  
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
  
-   B4003: Používá WCF `netrm:BufferRemaining` označuje, kolik nové zprávy spolehlivého zasílání zpráv cílové uložit do vyrovnávací paměti.  
  
-   B4004: omezuje počet zpráv přenášet-li cílová aplikace spolehlivé zasílání zpráv nelze rychle přijímat zprávy, které služba WCF spolehlivé zasílání zpráv. Spolehlivé zasílání zpráv cílové vyrovnávací paměti zpráv a název elementu klesne na hodnotu 0.  
  
-   B4005: Generuje WCF `netrm:BufferRemaining` celočíselné hodnoty rozsahu od 0 do 4096 (včetně) a čte hodnoty celé číslo mezi 0 a `xs:int`společnosti `maxInclusive` hodnota 214748364 (včetně).  
  
## <a name="message-exchange-patterns"></a>Vzorky serveru Exchange zprávu  
 Tato část popisuje WCF na chování při zasílání zpráv WS-Reliable se používá pro různé vzorce výměny zpráv. Pro každý vzoru výměny zpráv se považují následující scénáře dvě nasazení:  
  
-   Bez bajtově Adresovatelného iniciátor: Iniciátor je za bránou firewall; Respondér doručovat zprávy do iniciátoru jenom v odpovědi protokolu HTTP.  
  
-   Adresovatelný iniciátor: Iniciátor i respondér mohou být odesílány požadavky HTTP; jinými slovy je možné navázat připojení prostřednictvím protokolu HTTP dvě konverzace.  
  
### <a name="one-way-non-addressable-initiator"></a>Jednosměrný, bajtově adresovatelného iniciátor  
  
#### <a name="binding"></a>Vazba  
 WCF poskytuje vzoru výměny zpráv jednosměrné pomocí jednoho pořadí přes jeden kanál protokolu HTTP. Přenést všechny zprávy ze serveru RMS a odpovědi protokolu HTTP RMD přenášet všechny zprávy z RMD k serveru RMS pomocí WCF požadavky HTTP.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Generuje iniciátoru WCF `CreateSequence` zprávu s žádné nabídky. Zajišťuje respondér WCF `CreateSequence` nemá žádnou nabídku před vytvořením sekvenci. Odpovídá respondér WCF `CreateSequence` žádost s `CreateSequenceResponse` zprávy.  
  
#### <a name="sequenceacknowledgement"></a>Třída SequenceAcknowledgement  
 Iniciátor WCF zpracovává potvrzování odpověď všech zpráv s výjimkou `CreateSequence` zprávu a chybové zprávy. WCF respondér vždy generovat samostatné potvrzení v reakci na obou pořadí a `AckRequested` zprávy.  
  
#### <a name="terminatesequence-message"></a>Zprávu TerminateSequence dříve  
 Zpracovává WCF `TerminateSequence` jako Jednosměrná operace, což znamená odpovědi protokolu HTTP má prázdným textem zprávy a stavovým kódem HTTP 202.  
  
### <a name="one-way-addressable-initiator"></a>Jedním ze způsobů, adresovatelný iniciátor  
  
#### <a name="binding"></a>Vazba  
 WCF poskytuje vzoru výměny zpráv jednosměrné pomocí jednoho pořadí za příchozí a odchozí kanálu protokolu Http. WCF používá k přenosu všech zpráv požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavovým kódem HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Generuje iniciátoru WCF `CreateSequence` zprávu s žádné nabídky. WCF respondér zajišťuje, že `CreateSequence` nemá žádnou nabídku před vytvořením sekvenci. Přenáší respondér WCF `CreateSequenceResponse` mluví zprávu na požadavek HTTP `ReplyTo` reference koncového bodu.  
  
### <a name="duplex-addressable-initiator"></a>Duplexní, adresovatelný iniciátor  
  
#### <a name="binding"></a>Vazba  
 WCF poskytuje základní vzor obousměrný plně asynchronních zpráv exchange pomocí dvou sekvencí přes příchozí a odchozí kanálu protokolu HTTP. WCF používá k přenosu všech zpráv požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavovým kódem HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Generuje iniciátoru WCF `CreateSequence` zpráva nabídkou. WCF respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci. Odešle WCF `CreateSequenceResponse` adresované na požadavku HTTP `CreateSequence`společnosti `ReplyTo` reference koncového bodu.  
  
#### <a name="sequence-lifetime"></a>Doba života pořadí  
 WCF považuje dvou sekvencí jeden plně duplexní relace.  
  
 Při generování chybu, která chyb jedním sekvenčním WCF očekává, že vzdálený koncový bod na selhání obou pořadí. Při čtení chybu, která jedním sekvenčním chyb, chyb WCF obou pořadí.  
  
 WCF zavřít jeho odchozí pořadí a pokračovat ve zpracování zprávy na jeho příchozí pořadí. Naopak WCF zpracovávat zavřít příchozí pořadí a i nadále odesílat zprávy v jeho výstupní sekvence.  
  
### <a name="request-reply-non-addressable-initiator"></a>Požadavek odpověď, bajtově Adresovatelného iniciátor  
  
#### <a name="binding"></a>Vazba  
 Poskytuje jednosměrný WCF a vzorce výměny zpráv žádost odpověď pomocí dvou pořadí více než jeden kanál protokolu HTTP. WCF používá k přenosu žádosti o pořadí zpráv požadavků HTTP a použije odpovědi protokolu HTTP přenášet zprávy sekvence odpovědí.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Generuje iniciátoru WCF `CreateSequence` zpráva nabídkou. WCF respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci. Odpovídá respondér WCF `CreateSequence` žádost s `CreateSequenceResponse` zprávy.  
  
#### <a name="one-way-message"></a>Jednosměrná zpráva  
 Protokol exchange jednosměrná zpráva se úspěšně dokončil, iniciátor WCF přenáší zprávy sekvence do požadavku na požadavku HTTP a přijímá samostatný `SequenceAcknowledgement` zprávy na odpovědi HTTP. `SequenceAcknowledgement` Musí potvrzení zprávy odesílané informace.  
  
 WCF respondér můžete odpovědět na požadavek na potvrzení, chybu nebo jinou odpověď s prázdným textem zprávy a stavovým kódem HTTP 202.  
  
#### <a name="two-way-messages"></a>Dvě způsob, jak zprávy  
 Protokol pro výměnu zpráv dvousměrné úspěšně dokončit, iniciátor WCF přenáší zprávy sekvence do požadavku na požadavku HTTP a přijímá zprávy sekvence odpovědí na odpovědi HTTP. Odpovědi musí mít `SequenceAcknowledgement` potvrdil pořadí zprávy s požadavkem přenosu.  
  
 WCF respondér můžete odpovědět na požadavek odpovědi na žádost, chybu nebo jinou odpověď s prázdným textem zprávy a stavovým kódem HTTP 202.  
  
 Z důvodu přítomnosti jednosměrné zprávy a načasování odpovědi aplikace mít žádnou souvislost pořadové číslo sekvence zprávy požadavku a pořadovým číslem zprávy odpovědi.  
  
#### <a name="retrying-replies"></a>Opakování pokusu o odpovědi  
 WCF spoléhá na korelace požadavku a odpovědi HTTP pro korelace protokol exchange obousměrný zprávy. Z toho důvodu je iniciátor WCF nezastaví opakování zprávy sekvence do žádosti o potvrzení zprávy s požadavkem pořadí ale místo toho v případě, že představuje odpověď HTTP potvrzení, uživatel zpráv nebo selhání. WCF respondér zopakuje pokus o odpovědi na větev žádosti HTTP požadavku, ke kterému je korelační odpověď.  
  
#### <a name="lastmessage-exchange"></a>Třídy LastMessage Exchange  
 Iniciátor WCF generuje a přenáší prázdnou vozidlo poslední zprávu na větev žádosti protokolu HTTP. WCF vyžaduje odpověď, ale ignoruje zprávu skutečné odpovědi. WCF respondér odpovědi na požadavek pořadí s v těle prázdný poslední zprávu s poslední zprávu s v těle prázdná sekvence odpovědí.  
  
 Pokud respondér WCF obdrží poslední zprávu, ve kterém je identifikátor URI akce není `http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage`, WCF odpovědi s poslední zprávou. V případě protokol pro výměnu obousměrný zpráva poslední zprávou přenáší zprávy aplikace; v případě protokol pro výměnu jednosměrná zpráva poslední zprávou je prázdný.  
  
 WCF respondér nevyžaduje potvrzení pro poslední zprávu s v těle prázdná sekvence odpovědí.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence dříve Exchange  
 Po všech požadavků mít přijetí platné odpovědi iniciátoru WCF generuje a odesílá požadavek pořadí `TerminateSequence` zprávu na větev žádosti protokolu HTTP. WCF vyžaduje odpověď, ale ignoruje zprávu skutečné odpovědi. WCF respondér odpoví na požadavek pořadí `TerminateSequence` zprávu s odpovědí pořadí `TerminateSequence` zprávy.  
  
 V sekvenci normální ukončení obě `TerminateSequence` zprávy mají plný rozsah `SequenceAcknowledgement`.  
  
### <a name="requestreply-addressable-initiator"></a>Žádost odpověď, adresovatelný iniciátor  
  
#### <a name="binding"></a>Vazba  
 WCF poskytuje vzoru výměny zpráv žádost odpověď pomocí dvou sekvencí za příchozí a odchozí kanálu protokolu HTTP. WCF používá k přenosu všech zpráv požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavovým kódem HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Generuje iniciátoru WCF `CreateSequence` zpráva nabídkou. WCF respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci. Odešle WCF `CreateSequenceResponse` adresované na požadavku HTTP `CreateSequence`společnosti `ReplyTo` reference koncového bodu.  
  
#### <a name="requestreply-correlation"></a>Korelace požadavku/odpovědi  
 Iniciátor WCF zajišťuje také nesete zprávy požadavku všechny aplikace `MessageId` a `ReplyTo` reference koncového bodu. Iniciátor WCF se vztahuje `CreateSequence` zprávy `ReplyTo` reference koncového bodu pro každou zprávu žádosti o aplikace. Respondér WCF vyžaduje také nesete zprávy příchozí žádosti `MessageId` a `ReplyTo`. WCF respondér zajišťuje, že identifikátor URI reference koncového bodu z obou `CreateSequence` a všechny zprávy požadavku aplikace jsou identické.
