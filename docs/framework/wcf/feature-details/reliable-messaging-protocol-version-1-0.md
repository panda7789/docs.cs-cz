---
title: Protokol spolehlivého zasílání zpráv verze 1.0
ms.date: 03/30/2017
ms.assetid: a5509a5c-de24-4bc2-9a48-19138055dcce
ms.openlocfilehash: f45a0d5e50e9ab8a07a203d2c40ad36ef298a40d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497049"
---
# <a name="reliable-messaging-protocol-version-10"></a>Protokol spolehlivého zasílání zpráv verze 1.0
Toto téma obsahuje podrobné informace o nasazení Windows Communication Foundation (WCF) pro WS-spolehlivého zasílání zpráv protokolu únor 2005 (verze 1.0) nezbytné pro vzájemná spolupráce pomocí přenosového protokolu HTTP. WCF dodržuje specifikaci WS-spolehlivé zasílání zpráv s omezení a objasnění, která jsou popsané v tomto tématu. Poznámka: verze 1.0 protokolu WS-ReliableMessaging je implementováno počínaje [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)].  
  
 Služby WS-spolehlivé zasílání zpráv únor 2005 protokol je implementována ve WCF pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Pro usnadnění práce tématu používá Tyhle role:  
  
-   Iniciátor: klienta, která zahájí vytváření sekvence WS-spolehlivé zpráv  
  
-   Respondér: na službu, kterou přijme je iniciátor požadavky  
  
 Tento dokument používá předpony a obory názvů v následující tabulce.  
  
|Předpona|Obor názvů|  
|------------|---------------|  
|Správce systémových prostředků|http://schemas.xmlsoap.org/ws/2005/02/rm|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
  
## <a name="messaging"></a>Zasílání zpráv  
  
### <a name="sequence-establishment-messages"></a>Pořadí vytváření zpráv  
 Implementuje WCF `CreateSequence` a `CreateSequenceResponse` zprávy a pokuste se vytvořit sekvenci spolehlivé zpráv. Platí následující omezení:  
  
-   B1101: Iniciátoru WCF negeneruje Volitelný element Expires v `CreateSequence` zpráva nebo v případech při `CreateSequence` zpráva obsahuje `Offer` element, volitelné `Expires` element v `Offer` elementu.  
  
-   B1102: Při přístupu k `CreateSequence` zprávy, WCF`Responder` odesílá a přijímá obě `Expires` elementů, pokud existují, ale nepoužívá jejich hodnot.  
  
 WS-spolehlivé zasílání zpráv představuje `Offer` mechanismus pro vytvoření dvou komunikaci korelační pořadí, které vytvářejí relaci.  
  
-   R1103: Pokud `CreateSequence` obsahuje `Offer` element spolehlivého zasílání zpráv respondér musíte buď přijmout sekvenci a odpoví `CreateSequenceResponse` obsahující `wsrm:Accept` elementu, které tvoří dvě korelační komunikaci pořadí nebo odmítnout `CreateSequence` požadavku.  
  
-   R1104: `SequenceAcknowledgement` a aplikace zpráv odesílaných na pořadí konverzace zaslána `ReplyTo` odkaz na koncový bod `CreateSequence`.  
  
-   R1105: `AcksTo` a `ReplyTo` v odkazuje na koncový bod `CreateSequence` musí mít hodnoty adres, které odpovídají octet-wise.  
  
     WCF respondér ověřuje, že část identifikátoru URI `AcksTo` a `ReplyTo` odkazy na koncové body jsou identické před vytvořením sekvenci.  
  
-   R1106: `AcksTo` a `ReplyTo` koncový bod odkazů v `CreateSequence` by měly mít stejnou sadu parametrů odkaz.  
  
     WCF nevynucuje, ale předpokládá, že [odkaz na parametry] `AcksTo` a `ReplyTo` na `CreateSequence` jsou identické a používá [odkaz na parametry] z `ReplyTo` reference koncového bodu pro potvrzení a konverzace pořadí zprávy.  
  
-   R1107: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` a aplikace zpráv odesílaných na pořadí konverzace zaslána `ReplyTo` odkaz na koncový bod `CreateSequence`.  
  
-   R1108: Pokud dva komunikaci pořadí jsou vytvořena pomocí nabídky mechanismus, `[address]` vlastnost `wsrm:AcksTo` podřízený prvek Reference koncového bodu `wsrm:Accept` element `CreateSequenceResponse` musí odpovídat byte-wise cílový identifikátor URI z `CreateSequence`.  
  
-   R1109: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, zprávy odeslané iniciátor a potvrzení na zprávy pomocí respondér musí být odeslána na odkaz na stejný koncový bod.  
  
     WCF používá k vytvoření spolehlivé relace mezi iniciátor a respondér WS-spolehlivé zasílání zpráv. Implementace služby WS-spolehlivé zasílání zpráv na WCF poskytuje spolehlivé relace pro jednosměrné, požadavku a odpovědi a úplné duplexní režim vzory pro zasílání zpráv. WS-spolehlivé zasílání zpráv `Offer` mechanismus na `CreateSequence` / `CreateSequenceResponse` umožňuje vytvořit dva pořadí korelační konverzace a poskytuje protokol relace, který je vhodný pro všechny zprávy koncové body. Protože WCF poskytuje záruku zabezpečení relace, včetně ochrany začátku do konce relace integritu, je potřeba zajistit, aby přicházejí zprávy určené pro stejné stranu stejný cíl. To také umožňuje Prasátko zálohování pořadí potvrzení u zpráv s aplikací. Proto platí omezení R1104, R1105 a R1108 pro WCF.  
  
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
 Následuje seznam omezení, která se týkají pořadí:  
  
-   Generuje B1201:WCF a přístupů pořadí čísla vyšší než `xs:long`na maximální hodnotu (včetně), 9223372036854775807.  
  
-   B1202:WCF vždy vygeneruje prázdný vozidlo poslední zprávu s akcí URI z http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.  
  
-   B1203: WCF obdrží a doručí zprávu s hlavičkou pořadí, který obsahuje `LastMessage` elementu, pokud identifikátor URI akce není http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage.  
  
 Příklad hlavičky pořadí.  
  
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
  
### <a name="ackrequested-header"></a>AckRequested záhlaví  
 Používá WCF `AckRequested` záhlaví jako mechanismus keep-alive. WCF negeneruje nepovinný `MessageNumber` elementu. Po přijetí zprávy s `AckRequested` hlavičky, která obsahuje `MessageNumber` ignoruje elementu WCF `MessageNumber` hodnota elementu, jak je znázorněno v následujícím příkladu.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>  
    urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
  </wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement-header"></a>Záhlaví SequenceAcknowledgement do důvěryhodné  
 WCF používá Prasátko zpětný mechanismus pro potvrzení pořadí, které jsou součástí služby WS-spolehlivé zasílání zpráv.  
  
-   R1401: Pokud dva komunikaci pořadí jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` záhlaví může být součástí jakékoli aplikace zprávy předaných zamýšlený příjemce.  
  
-   B1402: Když WCF musíte vygenerovat potvrzení před obdržením všechny zprávy pořadí (třeba, aby pokryl `AckRequested` zpráva), vygeneruje WCF `SequenceAcknowledgement` hlavičky, která obsahuje rozsah 0-0, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>  
        urn:uuid:addabbbf-60cb-44d3-8c5b-9e0841629a36  
      </wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="0" Lower="0"/>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B1403: WCF negeneruje `SequenceAcknowledgement` hlavičky, které obsahují `Nack` elementu, ale podporuje `Nack` elementy.  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging chyb  
 Následuje seznam omezení, která se týkají implementace WCF WS-spolehlivé zasílání zpráv chyb:  
  
-   B1501: WCF negeneruje `MessageNumberRollover` chyb.  
  
-   Koncový bod B1502:WCF může generovat `CreateSequenceRefused` chyb, jak je popsáno ve specifikaci.  
  
-   B1503:when koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení, vygeneruje další WCF `CreateSequenceRefused` poruch dílčí, `netrm:ConnectionLimitReached`, jak je znázorněno v následujícím příkladu.  
  
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
  
### <a name="ws-addressing-faults"></a>Adresování WS chyb  
 Protože WS-spolehlivé zasílání zpráv používá WS-Addressing, WS-spolehlivého zasílání zpráv WCF implementace může generovat WS-Addressing chyb. Tato část se zabývá WS-Addressing chyb, které WCF explicitně generuje ve vrstvě služby WS-spolehlivé zasílání zpráv:  
  
-   B1601:WCF generuje selhání zpráva adresování záhlaví vyžaduje, pokud platí jedna z následujících:  
  
    -   Chybí zprávu `Sequence` záhlaví a `Action` záhlaví.  
  
    -   A `CreateSequence` chybí zpráva `MessageId` záhlaví.  
  
    -   A `CreateSequence` chybí zpráva `ReplyTo` záhlaví.  
  
-   B1602:WCF generuje selhání akce není podporována odpovědi na zprávu, která chybí `Sequence` záhlaví a má `Action` záhlaví, který není rozpoznaný ve specifikaci WS-spolehlivé zasílání zpráv.  
  
-   B1603:WCF generuje koncový bod k dispozici k označení, že koncový bod nezpracovává pořadí na základě zkoumání selhání `CreateSequence` zprávu o adrese hlavičky.  
  
## <a name="protocol-composition"></a>Protokol složení  
  
### <a name="composition-with-ws-addressing"></a>Složení s adresováním WS  
 Podporuje dvě verze WS-Addressing WCF: WS-Addressing 2004/08 [WS-ADDR] a adresování W3C WS 1.0 doporučení [WS-ADDR-CORE] a [WS-ADDR-SOAP].  
  
 Při zmínkami WS-spolehlivé zasílání zpráv specifikaci WS-Addressing 2004/08 pouze se neomezuje verze WS-Addressing má být použit. Následuje seznam omezení, která se týkají WCF:  
  
-   R2101: obě WS-Addressing 2004/08 a WS-Addressing 1.0 lze použít s WS-spolehlivé zasílání zpráv.  
  
-   Jedna verze R2102:A WS-Addressing musí použít v rámci dané WS-spolehlivé zasílání zpráv pořadí nebo pár konverzace pořadí korelační pomocí `wsrm:Offer` mechanismus.  
  
### <a name="composition-with-soap"></a>Složení protokol SOAP  
 WCF podporuje SOAP 1.1 a SOAP 1.2 s WS-spolehlivé zasílání zpráv.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Složení s WS-zabezpečení a WS-SecureConversation  
 WCF poskytuje ochranu pořadí WS-spolehlivé zasílání zpráv pomocí zabezpečení přenosu (HTTPS), složení s WS-zabezpečení a složení s WS zabezpečené konverzace. Následuje seznam omezení, která se týkají WCF:  
  
-   R2301: K ochraně integrity pořadí WS-spolehlivé zasílání zpráv kromě integrity a důvěrnosti jednotlivých zpráv, WCF vyžaduje, že se musí použít WS zabezpečené konverzace.  
  
-   R2302:awS-zabezpečené konverzace relace je nutné vytvořit před zřízením sequence(s) WS-spolehlivé zasílání zpráv.  
  
-   R2303: Pokud WS-spolehlivé zasílání zpráv pořadí životnost překročí WS zabezpečené konverzace doba platnosti relace, `SecurityContextToken` navázat pomocí WS zabezpečené konverzace musí obnovit pomocí odpovídající vazby WS bezpečné obnovení konverzace.  
  
-   B2304:ws-spolehlivé zasílání zpráv pořadí nebo pár korelační konverzace pořadí jsou vždy vázány na jedné relace WS-SecureConversation.  
  
     Generuje zdroji WCF `wsse:SecurityTokenReference` element v části rozšiřitelnost element `CreateSequence` zprávy.  
  
-   R2305:when skládá s WS zabezpečené konverzace `CreateSequence` zpráva musí obsahovat `wsse:SecurityTokenReference` elementu.  
  
## <a name="ws-reliable-messaging-ws-policy-assertion"></a>WS-spolehlivého zasílání zpráv výraz WS-zásad  
 WCF používá WS-spolehlivého zasílání zpráv WS-Policy kontrolní výraz `wsrm:RMAssertion` k popisu možnosti koncových bodů. Následuje seznam omezení, která se týkají WCF:  
  
-   B3001: Připojí WCF `wsrm:RMAssertion` výraz WS-zásad na `wsdl:binding` elementy. WCF podporuje obě přílohy do `wsdl:binding` a `wsdl:port` elementy.  
  
-   B3002: WCF podporuje následující volitelné vlastnosti assertion WS-spolehlivé zasílání zpráv a umožňuje řídit je na WCF`ReliableMessagingBindingElement`:  
  
    -   `wsrm:InactivityTimeout`  
  
    -   `wsrm:AcknowledgementInterval`  
  
     Následuje příklad.  
  
    ```xml  
    <wsrm:RMAssertion>  
      <wsrm:InactivityTimeout Milliseconds="600000" />  
      <wsrm:AcknowledgementInterval Milliseconds="200" />  
    </wsrm:RMAssertion>  
    ```  
  
## <a name="flow-control-ws-reliable-messaging-extension"></a>Tok řízení WS-spolehlivé zasílání zpráv rozšíření  
 K poskytování volitelné další náročnější řídit tok zpráv pořadí WCF používá rozšíření WS-spolehlivé zasílání zpráv.  
  
 Řízení toku povolíte nastavením `ReliableSessionBindingElement`na `FlowControlEnabled``bool` vlastnost `true`. Následuje seznam omezení, která se týkají WCF:  
  
-   B4001: WCF generuje Pokud je povoleno spolehlivého zasílání zpráv řízení toku, `netrm:BufferRemaining` element v elementu rozšiřitelnosti služby `SequenceAcknowledgement` záhlaví.  
  
-   B4002: Pokud je povoleno spolehlivého zasílání zpráv řízení toku, WCF nevyžaduje `netrm:BufferRemaining` element v `SequenceAcknowledgement` záhlaví, jak je znázorněno v následujícím příkladu.  
  
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
  
-   B4003: Používá WCF `netrm:BufferRemaining` indikující, kolik nových zpráv spolehlivého zasílání zpráv cílové můžete ukládat do vyrovnávací paměti.  
  
-   B4004: Služba WCF spolehlivého zasílání zpráv omezí generovaný počet zpráv přenášených při cílové aplikace spolehlivého zasílání zpráv nemůže přijímat rychlé zprávy. Zpráv spolehlivého zasílání zpráv cílové vyrovnávací paměti a hodnota elementu hodnota klesne na 0.  
  
-   B4005: Generuje WCF `netrm:BufferRemaining` celé číslo hodnoty od 0 do 4096 (včetně) a načte hodnoty celé číslo mezi 0 a `xs:int`na `maxInclusive` hodnotu 214748364 (včetně).  
  
## <a name="message-exchange-patterns"></a>Vzory Exchange zpráv  
 Tato část popisuje WCF na chování při WS-spolehlivé zasílání zpráv se používá pro různé vzorce výměny zpráv. Pro každý vzorce výměny zpráv jsou považovány za následující dvě nasazení scénáře:  
  
-   Bez adresovatelné iniciátor: Iniciátor je za bránou firewall; Respondér můžete doručování zpráv k iniciátoru jenom v odpovědi HTTP.  
  
-   Adresovatelné iniciátor: Iniciátor i respondér mohou být odesílány požadavky HTTP; jinými slovy dvě konverzace HTTP připojení lze navázat.  
  
### <a name="one-way-non-addressable-initiator"></a>Jednosměrné, adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 WCF poskytuje vzorce výměny zpráv jednosměrný pomocí jednoho pořadí přes jeden kanál protokolu HTTP. WCF používá k přenosu všech zpráv ze serveru RMS RMD a odpovědi protokolu HTTP k přenosu všech zprávy RMD RMS požadavky HTTP.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Generuje iniciátoru WCF `CreateSequence` zprávu s žádné nabídky. Zajišťuje respondér WCF `CreateSequence` nemá žádné nabídky před vytvořením sekvenci. WCF respondér reaguje na `CreateSequence` žádosti s `CreateSequenceResponse` zprávy.  
  
#### <a name="sequenceacknowledgement"></a>Bylo potvrzení SequenceAcknowledgement  
 Iniciátor WCF zpracovává potvrzení na odpověď všechny zprávy s výjimkou `CreateSequence` zprávu a chybové zprávy. WCF respondér vždy vygeneruje samostatné potvrzení v odpovědi na obou pořadí a `AckRequested` zprávy.  
  
#### <a name="terminatesequence-message"></a>Zpráva TerminateSequence  
 Zpracovává WCF `TerminateSequence` jako Jednosměrná operace znamená odpověď HTTP, která má prázdným textem zprávy a stavový kód HTTP 202.  
  
### <a name="one-way-addressable-initiator"></a>Jedním ze způsobů, adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 WCF poskytuje vzorce výměny zpráv jednosměrný pomocí jednoho pořadí přes příchozí a odchozí kanál protokolu Http. WCF využívá k přenosu všechny zprávy požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Generuje iniciátoru WCF `CreateSequence` zprávu s žádné nabídky. WCF respondér zajišťuje, že `CreateSequence` nemá žádné nabídky před vytvořením sekvenci. Přenáší respondér WCF `CreateSequenceResponse` zprávu na požadavek HTTP řešit pomocí `ReplyTo` reference koncového bodu.  
  
### <a name="duplex-addressable-initiator"></a>Duplexní, adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 WCF poskytuje vzorce výměny zpráv plně asynchronní obousměrný pomocí dvou pořadí přes příchozí a odchozí kanál protokolu HTTP. WCF využívá k přenosu všechny zprávy požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Generuje iniciátoru WCF `CreateSequence` zprávu s nabídku. WCF respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci. Odešle WCF `CreateSequenceResponse` na požadavek HTTP adresovaných `CreateSequence`na `ReplyTo` reference koncového bodu.  
  
#### <a name="sequence-lifetime"></a>Doba platnosti pořadí  
 WCF považuje za jednu relaci plně duplexní dvě pořadí.  
  
 Při generování chybu, která závady jedním sekvenčním, WCF očekává, že vzdálený koncový bod pro poruch obě pořadí. Při čtení chybu, která jedním sekvenčním chyb, chyb WCF obě pořadí.  
  
 WCF můžete zavřít jeho odchozí pořadí a pokračovat ve zpracování zprávy v jeho příchozí pořadí. Naopak WCF můžete zpracovat ukončení příchozí pořadí a pokračovat v odesílání zpráv na jeho odchozí pořadí.  
  
### <a name="request-reply-non-addressable-initiator"></a>Požadavek odpověď,-adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 Poskytuje jednosměrný WCF a vzorce výměny zpráv požadavku a odpovědi pomocí dvou pořadí více než jeden kanál protokolu HTTP. WCF používá požadavků HTTP k přenosu zpráv je žádost o pořadí a odpovědi HTTP používá k přenosu zpráv sekvence odpovědí.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Generuje iniciátoru WCF `CreateSequence` zprávu s nabídku. WCF respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci. WCF respondér reaguje na `CreateSequence` žádosti s `CreateSequenceResponse` zprávy.  
  
#### <a name="one-way-message"></a>Jednosměrné zpráv  
 Protokol exchange jednosměrný zprávy úspěšně dokončil, iniciátoru WCF přenáší zprávu požadavku pořadí na požadavek HTTP a přijímá samostatnou `SequenceAcknowledgement` zprávu na odpovědi HTTP. `SequenceAcknowledgement` Musí potvrdit zprávy odesílané informace.  
  
 Respondér WCF může odpovědět na žádost o potvrzení, chybu nebo odpověď s prázdným textem zprávy a stavový kód HTTP 202.  
  
#### <a name="two-way-messages"></a>Dvě způsob zprávy  
 Protokol pro výměnu zpráv dvoucestné úspěšně dokončil, iniciátoru WCF přenáší zprávu požadavku pořadí na požadavek HTTP a přijme zprávu o odpovědi pořadí na odpovědi HTTP. Odpovědi musí mít `SequenceAcknowledgement` to pořadí zprávu požadavku v úvahu přenosu.  
  
 Požadavek s odpověď protokolu aplikace, chybu nebo odpověď s prázdným textem zprávy a stavový kód HTTP 202 může odpovědět respondér WCF.  
  
 Z důvodu přítomnosti jednosměrný zprávy a načasování odpovědi aplikací mít žádné korelace pořadové číslo sekvence zprávy požadavku a pořadovým číslem zprávy odpovědi.  
  
#### <a name="retrying-replies"></a>Opakováním odpovědi  
 WCF spoléhá na korelace požadavku a odpovědi HTTP pro korelace protokol exchange obousměrný zprávy. Z toho důvodu iniciátoru WCF nezastaví opakování zprávu požadavku pořadí při potvrdí se bez pořadí zprávu požadavku, ale místo v případě, že představuje odpověď HTTP potvrzení, uživatel zpráv nebo selhání. WCF respondér opakuje odpovědi na větev požadavku HTTP požadavku, ke kterému je korelační odpovědi.  
  
#### <a name="lastmessage-exchange"></a>Třídy LastMessage Exchange  
 Iniciátor WCF generuje a odesílá prázdný vozidlo poslední zprávy na větev požadavku HTTP. WCF vyžaduje odpověď, ale ignoruje zprávu skutečné odpovědi. WCF respondér odpovědi na požadavek pořadí prázdný vozidlo poslední zprávu s prázdný vozidlo poslední zprávu odpovědi pořadí.  
  
 Pokud respondér WCF přijme zprávu o poslední, ve kterém akce identifikátor URI není http://schemas.xmlsoap.org/ws/2005/02/rm/LastMessage, WCF odpovědi s poslední zprávou. V případě protokol pro výměnu obousměrný zpráva poslední zprávou představuje aplikace zpráva; v případě protokol pro výměnu jednosměrný zpráva poslední zprávou je prázdný.  
  
 WCF respondér nevyžaduje potvrzení pro prázdný vozidlo poslední zprávu odpovědi pořadí.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence Exchange  
 Pokud všechny požadavky obdrželi platný odpovědi, iniciátoru WCF generuje a odesílá požadavek pořadí `TerminateSequence` zprávu na větev požadavku HTTP. WCF vyžaduje odpověď, ale ignoruje zprávu skutečné odpovědi. WCF respondér reaguje na požadavek pořadí `TerminateSequence` zprávu s odpovědí pořadí `TerminateSequence` zprávy.  
  
 V pořadí normální vypnutí i `TerminateSequence` zprávy provádění plný rozsah `SequenceAcknowledgement`.  
  
### <a name="requestreply-addressable-initiator"></a>Požadavek nebo odpověď, adresovatelné iniciátor  
  
#### <a name="binding"></a>Vazba  
 WCF poskytuje vzorce výměny zpráv požadavku a odpovědi pomocí dvou pořadí přes příchozí a odchozí kanál protokolu HTTP. WCF využívá k přenosu všechny zprávy požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavový kód HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Generuje iniciátoru WCF `CreateSequence` zprávu s nabídku. WCF respondér zajišťuje, že `CreateSequence` má nabídku před vytvořením sekvenci. Odešle WCF `CreateSequenceResponse` na požadavek HTTP adresovaných `CreateSequence`na `ReplyTo` reference koncového bodu.  
  
#### <a name="requestreply-correlation"></a>Korelace požadavku/odpovědi  
 Iniciátor WCF zajistí všechny opatřeny zprávy žádost o aplikaci `MessageId` a `ReplyTo` reference koncového bodu. Iniciátor WCF se vztahuje `CreateSequence` zprávy `ReplyTo` koncový bod odkazu na každou zprávu požadavku aplikací. Příjemce WCF vyžaduje, že příchozí požadavek zprávy opatřeny `MessageId` a `ReplyTo`. WCF respondér zajišťuje, že odkaz na koncový bod URI i `CreateSequence` a všechny zprávy požadavku aplikace jsou identické.
