---
title: Protokol spolehlivého zasílání zpráv verze 1.1
ms.date: 03/30/2017
ms.assetid: 0da47b82-f8eb-42da-8bfe-e56ce7ba6f59
ms.openlocfilehash: 6b8732e0b48797c219b53bb8bf70e1ba57e25c42
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61933988"
---
# <a name="reliable-messaging-protocol-version-11"></a>Protokol spolehlivého zasílání zpráv verze 1.1
Toto téma obsahuje podrobné informace o nasazení Windows Communication Foundation (WCF) pro WS-ReliableMessaging protokol února 2007 (verze 1.1) nezbytné pro spolupráci pomocí přenos pomocí protokolu HTTP. WCF dodržuje specifikaci WS-ReliableMessaging s omezením a vyjasnění je vysvětleno v tomto tématu. Všimněte si, že se implementuje protokol WS-ReliableMessaging verze 1.1 počínaje [!INCLUDE[netfx35_long](../../../../includes/netfx35-long-md.md)].  
  
 WS-ReliableMessaging února 2007 protokol je implementován ve službě WCF pomocí <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>.  
  
 Pro usnadnění práce tématu používá Tyhle role:  
  
-   Iniciátor: Klient, který zahájí vytváření pořadí zpráv WS-Reliable.  
  
-   Respondér: Služba, která bude přijímat žádosti je iniciátor.  
  
 Tento dokument používá předpony a obory názvů v následující tabulce.  
  
|Předpona|Obor názvů|  
|-|-|  
|wsrm|http://docs.oasis-open.org/ws-rx/wsrm/200702|  
|netrm|http://schemas.microsoft.com/ws/2006/05/rm|  
|s|http://www.w3.org/2003/05/soap-envelope|  
|wsa|http://schemas.xmlsoap.org/ws/2005/08/addressing|  
|wsse|http://docs.oasis-open.org/wss/2004/01/oasis-200401-wssecurity-secext-1.0.xsd|  
|wsrmp|http://docs.oasis-open.org/ws-rx/wsrmp/200702|  
|netrmp|http://schemas.microsoft.com/ws-rx/wsrmp/200702|  
|wsp|(WS-Policy 1.2 nebo WS-Policy 1.5)|  
  
## <a name="messaging"></a>Zasílání zpráv  
  
### <a name="sequence-creation"></a>Vytváření pořadí  
 Implementuje WCF `CreateSequence` a `CreateSequenceResponse` pořadí zpráv k navázání spolehlivé zasílání zpráv. Platí následující omezení:  
  
-   B1101: Iniciátor WCF používá stejný koncový bod odkaz jako `CreateSequence` zprávy `ReplyTo`, `AcksTo` a `Offer/Endpoint`.  
  
-   R1102: `AcksTo`, `ReplyTo` a `Offer/Endpoint` v odkazuje na koncový bod `CreateSequence` zpráva musí mít identickou řetězcovou reprezentaci hodnoty adres tak, aby odpovídaly octet-wise.  
  
    -   WCF respondér ověřuje, že část identifikátoru URI `AcksTo`, `ReplyTo` a `Endpoint` Reference koncového bodu jsou identické před vytvořením sekvenci.  
  
-   R1103: `AcksTo`, `ReplyTo` a `Offer/Endpoint` v odkazuje na koncový bod `CreateSequence` zpráva by měla mít stejnou sadu parametrů odkazu.  
  
    -   WCF nevynucuje, ale předpokládá velikost tento odkaz parametry `AcksTo`, `ReplyTo` a `Offer/Endpoint` koncový bod odkazuje na `CreateSequence` jsou identické a používá parametry odkazů z `ReplyTo` reference koncového bodu pro potvrzení a konverzace pořadí zpráv.  
  
-   B1104: Iniciátor WCF negeneruje nepovinný `Expires` nebo `Offer/Expires` element v `CreateSequence` zprávy.  
  
-   B1105: Při přístupu k `CreateSequence` zprávy WCF respondér používá `Expires` hodnota v `CreateSequence` prvek jako `Expires` hodnota v `CreateSequenceResponse` elementu. V opačném případě respondér WCF přečte a ignoruje `Expires` a `Offer/Expires` hodnoty.  
  
-   B1106: Při přístupu k `CreateSequenceResponse` zprávu, iniciátor WCF načte volitelný `Expires` hodnotu, ale nepoužívá se.  
  
-   B1107: WCF iniciátor i respondér vždy generovat nepovinný `IncompleteSequenceBehavior` prvek `CreateSequence/Offer` a `CreateSequenceResponse` elementy.  
  
-   B1108: WCF použije pouze `DiscardFollowingFirstGap` a `NoDiscard` hodnoty v `IncompleteSequenceBehavior` elementu.  
  
    -   Využívá WS-ReliableMessaging `Offer` mechanismus k navázání dvou komunikaci korelační sekvence, které tvoří relace.  
  
-   B1109: Pokud `CreateSequence` obsahuje `Offer` elementu jedním ze způsobů respondér WCF odmítne nabízený pořadí reakcí s `CreateSequenceResponse` bez `Accept` elementu.  
  
-   B1110: Pokud spolehlivé zasílání zpráv respondér odmítne nabízený pořadí, iniciátor WCF chyb nově zavedených pořadí.  
  
-   B1111: Pokud `CreateSequence` neobsahuje `Offer` prvku obousměrný respondér WCF odmítne nabízený pořadí reakcí s `CreateSequenceRefused` selhání.  
  
-   R1112: Při dvou sekvencí konverzace jsou vytvořena pomocí `Offer` mechanismus, `[address]` vlastnost `CreateSequenceResponse/Accept/AcksTo` reference koncového bodu musí odpovídat cílový identifikátor URI z `CreateSequence` zpráva bajtu bajtů.  
  
-   R1113: Při dvou sekvencí konverzace jsou vytvořena pomocí `Offer` mechanismus, všechny zprávy v obou pořadí z iniciátoru tok na straně odpovídajícího se musí odeslat na stejné reference koncového bodu.  
  
 WCF WS-ReliableMessaging používá k navázání spolehlivé relace mezi iniciátorem a příjemce. Implementace WCF WS-ReliableMessaging poskytuje spolehlivé relace pro jednosměrný požadavek odpověď a plně duplexní způsobů zasílání zpráv. WS-ReliableMessaging `Offer` mechanismus `CreateSequence` a `CreateSequenceResponse` vám umožní navázání dvou korelační konverzace pořadí a poskytuje protokol relace, který je vhodný pro všechny koncové body zprávy. Protože WCF poskytuje záruku zabezpečení pro relaci, včetně začátku do konce ochranu integrity relace, je potřeba Ujistěte se, že zprávy určené pro stejný stranu přejít na stejný cíl. Díky tomu také "Prasátko zálohováním" pořadí potvrzení na zprávy aplikace. Proto platí omezení R1102 R1112 a R1113 pro WCF.  
  
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
  
### <a name="closing-a-sequence"></a>Zavření sekvence  
 Používá WCF `CloseSequence` a `CloseSequenceResponse` zprávy pro vypnutí spolehlivé zasílání zpráv spuštěno zdrojem. Spolehlivé zasílání zpráv WCF cílové nespustí, vypnutí a zdroj spolehlivé zasílání zpráv WCF nepodporuje vypnutí iniciované cílové spolehlivé zasílání zpráv. Platí následující omezení:  
  
-   B1201: Spolehlivé zasílání zpráv WCF zdroje vždy posílá `CloseSequence` zprávu ukončení sekvence.  
  
-   B1202: Zdroj spolehlivé zasílání zpráv čeká na potvrzení z široké spektrum pořadí zprávy před odesláním `CloseSequence` zprávy.  
  
-   B1203: Spolehlivé zasílání zpráv zdroj vždy obsahuje volitelný `LastMsgNumber` element není-li posloupnost neobsahuje zprávy.  
  
-   R1204: Spolehlivé zasílání zpráv cílové nesmí iniciovat vypnutí odesláním `CloseSequence` zprávy.  
  
-   B1205: Po přijetí `CloseSequence` zprávy, zdroje spolehlivé zasílání zpráv WCF považuje za neúplné sekvence a odesílá chybu.  
  
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
  
### <a name="sequence-termination"></a>Ukončení sekvence  
 WCF primárně používá `TerminateSequence/TerminateSequenceResponse` handshake po dokončení `CloseSequence/CloseSequenceResponse` handshake. Spolehlivé zasílání zpráv WCF cílové nespustí, ukončení a spolehlivé zasílání zpráv zdroj nepodporuje ukončení iniciované cílové spolehlivé zasílání zpráv. Platí následující omezení:  
  
-   B1301: Iniciátor WCF odesílá pouze `TerminateSequence` po úspěšném dokončení se zobrazí zpráva `CloseSequence/CloseSequenceResponse` handshake.  
  
-   R1302: WCF ověří, jestli `LastMsgNumber` element je konzistentní napříč všemi `CloseSequence` a `TerminateSequence` zpráv pro dané sekvence. To znamená, že `LastMsgNumber` buď není k dispozici na všech `CloseSequence` a `TerminateSequence` zprávy, nebo je k dispozici a stejné ve všech `CloseSequence` a `TerminateSequence` zprávy.  
  
-   B1303: Při přijímání `TerminateSequence` zpráv po `CloseSequence/CloseSequenceResponse` handshake, odpoví cílové spolehlivé zasílání zpráv `TerminateSequenceResponse` zprávy. Vzhledem k tomu, že zdroj spolehlivé zasílání zpráv má závěrečné potvrzení před odesláním `TerminateSequence` zprávy, cílový spolehlivé zasílání zpráv ví bez nepochybně, že sekvence se ukončí a okamžitě uvolní prostředky.  
  
-   B1304: Při přijímání `TerminateSequence` zpráv starších než `CloseSequence/CloseSequenceResponse` handshake, odpoví cílové WCF spolehlivé zasílání zpráv `TerminateSequenceResponse` zprávy. Pokud cílový spolehlivé zasílání zpráv zjistí, že neexistují žádné nekonzistence v sekvenci, spolehlivé zasílání zpráv místo určení čeká, dobu zadané cílové aplikace před uvolní prostředky, by klientovi umožňoval riziko pro příjem závěrečné potvrzení. V opačném případě cílové spolehlivé zasílání zpráv okamžitě uvolní prostředky a označuje cílové aplikace, že sekvence končí nejisté vyvoláním `Faulted` událostí.  
  
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
 Následuje seznam omezení, které se vztahují na pořadí:  
  
-   Generuje B1401:WCF a přístupy pořadí čísel vyšší než `xs:long`na maximální hodnotu (včetně), 9223372036854775807.  
  
 Příklad `Sequence` záhlaví.  
  
```xml  
<wsrm:Sequence s:mustUnderstand="1">  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:MessageNumber>1</wsrm:MessageNumber>  
</wsrm:Sequence>  
```  
  
### <a name="request-acknowledgement"></a>Žádost o potvrzení  
 Používá WCF `AckRequested` záhlaví jako vhodný mechanismus keep-alive.  
  
 Příklad `AckRequested` záhlaví.  
  
```xml  
<wsrm:AckRequested>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
</wsrm:AckRequested>  
```  
  
### <a name="sequenceacknowledgement"></a>Třída SequenceAcknowledgement  
 WCF používá mechanismus "Prasátko zpět" pro potvrzení pořadí součástí zasílání zpráv WS-Reliable. Platí následující omezení:  
  
-   R1601: Po dvou sekvencí konverzace jsou vytvořena pomocí `Offer` mechanismus, `SequenceAcknowledgement` záhlaví mohou být zahrnuty do jakékoli aplikace zprávy odesílané informace zamýšlený příjemce. Vzdálený koncový bod musí být schopen získat přístup zařazována složená `SequenceAcknowledgement` záhlaví.  
  
-   B1602: WCF negeneruje `SequenceAcknowledgement` hlavičky, které obsahují `Nack` elementy. WCF ověří, že každý `Nack` element obsahuje pořadové číslo, ale jinak ignoruje `Nack` elementu a hodnotu.  
  
 Příklad `SequenceAcknowledgement` záhlaví.  
  
```xml  
<wsrm:SequenceAcknowledgement>  
  <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
  <wsrm:AcknowledgementRange Lower="1" Upper="1"></wsrm:AcknowledgementRange>  
</wsrm:SequenceAcknowledgement>  
```  
  
### <a name="ws-reliablemessaging-faults"></a>WS-ReliableMessaging chyb  
 Následuje seznam omezení, které se vztahují k implementaci WCF WS-ReliableMessaging chyb. Platí následující omezení:  
  
-   B1701: WCF negeneruje `MessageNumberRollover` chyb.  
  
-   B1702: Přes protokol SOAP 1.2, když koncový bod služby dosáhne svého limitu připojení a nemůže zpracovat nová připojení, WCF vygeneruje vnořený `CreateSequenceRefused` selhání podřízeného, `netrm:ConnectionLimitReached`, jak je znázorněno v následujícím příkladu.  
  
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
  
### <a name="ws-addressing-faults"></a>WS-Addressing chyb  
 Vzhledem k tomu WS-ReliableMessaging používá WS-Addressing, může provádění WCF WS-ReliableMessaging generování a přenosu WS-Addressing chyb. Tato část zahrnuje chyby WS-Addressing, WCF explicitně generuje a odesílá ve vrstvě WS-ReliableMessaging:  
  
-   B1801:WCF generuje a přenáší `Message Addressing Header Required` selhání, když je splněna jedna z následujících akcí:  
  
    -   A `CreateSequence`, `CloseSequence` nebo `TerminateSequence` chybí zpráva `MessageId` záhlaví.  
  
    -   A `CreateSequence`, `CloseSequence` nebo `TerminateSequence` chybí zpráva `ReplyTo` záhlaví.  
  
    -   A `CreateSequenceResponse`, `CloseSequenceResponse`, nebo `TerminateSequenceResponse` chybí zpráva `RelatesTo` záhlaví.  
  
-   B1802:WCF generuje a přenáší `Endpoint Unavailable` selhání k označení, neexistuje žádný koncový bod, který dokáže zpracovat pořadí založené na posouzení adresování záhlaví ve `CreateSequence` zprávy.  
  
## <a name="protocol-composition"></a>Protokol sestavení  
  
### <a name="composition-with-ws-addressing"></a>Kompozice s WS-Addressing  
 WCF podporuje dvě verze WS-Addressing: WS-Addressing 2004/08 [WS-ADDR] a W3C WS-Addressing 1.0 doporučení [WS-ADDR – CORE] a [WS-ADDR SOAP].  
  
 Zatímco zmínky WS-ReliableMessaging specifikace WS-Addressing 2004/08 pouze neomezuje verze WS-Addressing má být použit. Následuje seznam omezení, které se vztahují na WCF:  
  
-   R2101: WS-Addressing 2004/08 a WS-Addressing 1.0 je možné pomocí zasílání zpráv WS-Reliable.  
  
-   R2102: Jednu verzi elementu WS-Addressing musí využívat v rámci dané sekvence WS-ReliableMessaging nebo dvojice posloupností první korelační pomocí `Offer` mechanismus.  
  
### <a name="composition-with-soap"></a>Složení u protokolu SOAP  
 WCF podporuje použití SOAP 1.1 a SOAP 1.2 zasílání zpráv WS-Reliable.  
  
### <a name="composition-with-ws-security-and-ws-secureconversation"></a>Kompozice s WS-Security a WS-SecureConversation  
 WCF poskytuje ochranu pro WS-ReliableMessaging pořadí pomocí zabezpečeného přenosu (HTTPS), kompozice s WS-Security a skládání s WS-Secure Conversation. Protokol WS-ReliableMessaging 1.1, WS-Security 1.1 a protokol WS-Secure 1.3 konverzace musí použít společně. Následuje seznam omezení, které se vztahují na WCF:  
  
-   R2301: Pro ochranu integrity WS-ReliableMessaging pořadí kromě integritu a důvěrnost jednotlivé zprávy, WCF vyžaduje, že musí použít WS-Secure Conversation.  
  
-   R2302:awS-zabezpečenou konverzací relace musí být vytvořen před navazování WS-ReliableMessaging sequence(s).  
  
-   R2303: Pokud pořadí životnost WS-ReliableMessaging překročí WS-Secure Conversation životnost relace `SecurityContextToken` lze navázat pomocí WS-Secure Conversation musí obnovovat pomocí odpovídající vazby WS-Secure obnovení konverzace.  
  
-   B2304:WS-ReliableMessaging pořadí nebo dvojice posloupností korelační konverzace jsou vždy vázány na jedné relace WS-SecureConversation.  
  
-   R2305: Při skládání s WS-Secure Conversation, respondér WCF vyžaduje, aby `CreateSequence` zpráva obsahovat `wsse:SecurityTokenReference` elementu a `wsrm:UsesSequenceSTR` záhlaví.  
  
 Příklad `UsesSequenceSTR` záhlaví.  
  
```xml  
<wsrm:UsesSequenceSTR></wsrm:UsesSequenceSTR>  
```  
  
### <a name="composition-with-ssltls-sessions"></a>Složení pomocí relace protokolu SSL/TLS  
 WCF nepodporuje složení pomocí relace protokolu SSL/TLS:  
  
-   B2401: WCF negeneruje `wsrm:UsesSequenceSSL` záhlaví.  
  
-   R2402: Spolehlivé zasílání zpráv iniciátoru nesmí odeslat `CreateSequence` zprávy s `wsrm:UsesSequenceSSL` záhlaví respondér WCF.  
  
### <a name="composition-with-ws-policy"></a>Kompozice s WS-Policy  
 WCF podporuje dvě verze WS-Policy: WS-Policy 1.2 a WS-Policy 1.5.  
  
## <a name="ws-reliablemessaging-ws-policy-assertion"></a>WS-ReliableMessaging WS-kontrolní výraz zásad  
 WCF používá WS-ReliableMessaging WS-Policy kontrolní `wsrm:RMAssertion` k popisu funkce koncových bodů. Následuje seznam omezení, které se vztahují na WCF:  
  
-   B3001: Připojí WCF `wsrmn:RMAssertion` WS-Policy kontrolního výrazu k `wsdl:binding` elementy. WCF podporuje obě příloh `wsdl:binding` a `wsdl:port` elementy.  
  
-   B3002: Nikdy generuje WCF `wsp:Optional` značky.  
  
-   B3003: Při přístupu k `wsrmp:RMAssertion` kontrolní výraz WS-Policy, ignoruje WCF `wsp:Optional` označit a zpracovává zásady WS-RM jako povinné.  
  
-   R3004: Protože WCF compose není s relací SSL/TLS, WCF nepřijímá žádné zásady, které určují `wsrmp:SequenceTransportSecurity`.  
  
-   B3005: Vždy generovat WCF `wsrmp:DeliveryAssurance` elementu.  
  
-   B3006: Vždy určuje WCF `wsrmp:ExactlyOnce` pojištění doručení.  
  
-   B3007: WCF generuje a přečte následující vlastnosti WS-ReliableMessaging kontrolní výraz a zajišťuje kontrolu nad nimi v WCF`ReliableSessionBindingElement`:  
  
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
  
## <a name="flow-control-ws-reliablemessaging-extension"></a>Tok řízení WS-ReliableMessaging rozšíření  
 K zajištění volitelné další přesnější kontrolu nad tok pořadí zpráv WCF používá WS-ReliableMessaging rozšiřitelnosti.  
  
 Řízení toku se povoluje nastavením <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled?displayProperty=nameWithType> vlastnost `true`. Následuje seznam omezení, které se vztahují na WCF:  
  
-   B4001: Pokud spolehlivé zasílání zpráv řízení toku je povolena, vygeneruje WCF `netrm:BufferRemaining` element v elementu rozšiřitelnost `SequenceAcknowledgement` záhlaví, jak je znázorněno v následujícím příkladu.  
  
    ```xml  
    <wsrm:SequenceAcknowledgement>  
      <wsrm:Identifier>urn:uuid:656652b8-9af2-4e94-9d07-2dc21c05ed27</wsrm:Identifier>  
      <wsrm:AcknowledgementRange Upper="1" Lower="1"/>             
      <netrm:BufferRemaining>8</netrm:BufferRemaining>  
    </wsrm:SequenceAcknowledgement>  
    ```  
  
-   B4002: I když spolehlivé zasílání zpráv řízení toku je povoleno, WCF nevyžaduje, aby `netrm:BufferRemaining` prvek `SequenceAcknowledgement` záhlaví.  
  
-   B4003: Cíl pro spolehlivé zasílání zpráv WCF používá `netrm:BufferRemaining` označuje, kolik nové zprávy uložit do vyrovnávací paměti.  
  
-   Je povolený B4004:when spolehlivé zasílání zpráv řízení toku, zdroj WCF spolehlivé zasílání zpráv používá hodnotu `netrm:BufferRemaining` pro přenos zpráv omezení.  
  
-   B4005: Generuje WCF `netrm:BufferRemaining` celočíselné hodnoty rozsahu od 0 do 4096 (včetně) a čte hodnoty celé číslo mezi 0 a `xs:int`společnosti `maxInclusive` hodnota 214748364 (včetně).  
  
## <a name="message-exchange-patterns"></a>Vzorky serveru Exchange zprávu  
 Tato část popisuje chování WCF. Pokud WS-ReliableMessaging slouží pro různé vzorce výměny zpráv. Pro každý vzoru výměny zpráv se považují následující scénáře dvě nasazení:  
  
-   Bajtově Adresovatelného iniciátor: Iniciátor nachází za bránou firewall; Respondér doručovat zprávy do iniciátor pouze na odpovědi HTTP.  
  
-   Adresovatelný iniciátor: Iniciátor i respondér mohou být odesílány požadavky HTTP; jinými slovy je možné navázat připojení prostřednictvím protokolu HTTP dvě konverzace.  
  
### <a name="one-way-non-addressable-initiator"></a>Jednosměrný, bajtově adresovatelného iniciátor  
  
#### <a name="binding"></a>Vazba  
 WCF poskytuje vzoru výměny zpráv jednosměrné pomocí jednoho pořadí přes jeden kanál protokolu HTTP. Přenést všechny zprávy z iniciátoru do odpovědí respondéru a HTTP přenášet všechny zprávy z straně odpovídajícího iniciátoru pomocí WCF požadavky HTTP.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Iniciátor WCF přenáší `CreateSequence` zprávu bez `Offer` elementu na požadavek HTTP a očekává, že `CreateSequenceResponse` zprávy na odpovědi HTTP. Vytvoří posloupnost respondér WCF a přenáší `CreateSequenceResponse` zprávu bez `Accept` element na odpovědi HTTP.  
  
#### <a name="sequenceacknowledgement"></a>Třída SequenceAcknowledgement  
 Iniciátor WCF zpracovává potvrzování odpověď všech zpráv s výjimkou `CreateSequence` zprávu a chybové zprávy. WCF respondér vždy přenese samostatné potvrzení na odpovědi HTTP do všech pořadí a `AckRequested` zprávy.  
  
#### <a name="closesequence-exchange"></a>CloseSequence Exchange  
 Iniciátor WCF přenáší `CloseSequence` zprávy na požadavek HTTP a očekává, že `CreateSequenceResponse` zprávy na odpovědi HTTP. Přenáší respondér WCF `CloseSequenceResponse` zprávy na odpovědi HTTP.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence dříve Exchange  
 Iniciátor WCF přenáší `TerminateSequence` zprávy na požadavek HTTP a očekává, že `TerminateSequenceResponse` zprávy na odpovědi HTTP. Přenáší respondér WCF `TerminateSequenceResponse` zprávy na odpovědi HTTP.  
  
### <a name="one-way-addressable-initiator"></a>Jedním ze způsobů, adresovatelný iniciátor  
  
#### <a name="binding"></a>Vazba  
 WCF poskytuje vzoru výměny zpráv jednosměrné pomocí jednoho pořadí přes jednu vstupní a jednu výstupní kanál protokolu HTTP. WCF používá k přenosu všech zpráv požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavovým kódem HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Iniciátor WCF přenáší `CreateSequence` zprávu bez `Offer` elementu na požadavek HTTP. Vytvoří posloupnost respondér WCF a přenáší `CreateSequenceResponse` zprávu bez `Accept` elementu na požadavek HTTP.  
  
### <a name="duplex-addressable-initiator"></a>Duplexní, adresovatelný iniciátor  
  
#### <a name="binding"></a>Vazba  
 Poskytuje WCF pomocí dvou vzoru výměny zpráv plně asynchronní, pokud vytvoříte obousměrný pořadí více než jeden vstupní a jednu výstupní kanál protokolu HTTP. Tento vzorce výměny zpráv lze kombinovat s `Request/Reply`, `Addressable` vzoru výměny zpráv iniciátoru omezeným způsobem. WCF používá k přenosu všech zpráv požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavovým kódem HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Iniciátor WCF přenáší `CreateSequence` zprávy s `Offer` elementu na požadavek HTTP. WCF respondér zajišťuje, že `CreateSequence` má `Offer` elementu, pak vytvoří sekvenci a přenáší `CreateSequenceResponse` zprávy s `Accept` elementu.  
  
#### <a name="sequence-lifetime"></a>Doba života pořadí  
 WCF považuje dvou sekvencí jeden plně duplexní relace.  
  
 Při generování chybu, která chyb jedním sekvenčním WCF očekává, že vzdálený koncový bod na selhání obou pořadí. Při čtení chybu, která jedním sekvenčním chyb, chyb WCF obou pořadí.  
  
 WCF zavřít jeho odchozí pořadí a pokračovat ve zpracování zprávy na jeho příchozí pořadí. Naopak WCF zpracovávat zavřít příchozí pořadí a i nadále odesílat zprávy v jeho výstupní sekvence.  
  
### <a name="request-reply-and-one-way-non-addressable-initiator"></a>Požadavek odpověď a jednosměrný, bajtově Adresovatelného iniciátor  
  
#### <a name="binding"></a>Vazba  
 Poskytuje jednosměrný WCF a vzorce výměny zpráv žádost odpověď pomocí dvou pořadí více než jeden kanál protokolu HTTP. Přenést všechny zprávy z iniciátoru do odpovědí respondéru a HTTP přenášet všechny zprávy z straně odpovídajícího iniciátoru pomocí WCF požadavky HTTP.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Iniciátor WCF přenáší `CreateSequence` zprávy s `Offer` elementu na požadavek HTTP a očekává, že `CreateSequenceResponse` zprávy na odpovědi HTTP. Vytvoří posloupnost respondér WCF a přenáší `CreateSequenceResponse` zprávy s `Accept` element na odpovědi HTTP.  
  
#### <a name="one-way-message"></a>Jednosměrná zpráva  
 Jednosměrná zpráva exchange úspěšně dokončit, iniciátor WCF přenáší zprávy sekvence do požadavku na požadavku HTTP a přijímá samostatný `SequenceAcknowledgement` zprávy na odpovědi HTTP. `SequenceAcknowledgement` Musí potvrzení zprávy odesílané informace.  
  
 WCF respondér může odpovědět na požadavek na potvrzení, chybu nebo jinou odpověď s prázdným textem zprávy a stavovým kódem HTTP 202.  
  
#### <a name="two-way-messages"></a>Dvě způsob, jak zprávy  
 Protokol pro výměnu zpráv dvousměrné úspěšně dokončit, iniciátor WCF přenáší zprávy sekvence do požadavku na požadavku HTTP a přijímá zprávy sekvence odpovědí na odpovědi HTTP. Odpovědi musí mít `SequenceAcknowledgement` potvrdil pořadí zprávy s požadavkem přenosu.  
  
 WCF respondér může odpovědět na požadavek odpovědi na žádost, chybu nebo jinou odpověď s prázdným textem zprávy a stavovým kódem HTTP 202.  
  
 Z důvodu přítomnosti jednosměrné zprávy a načasování odpovědi aplikace mít žádnou souvislost pořadové číslo sekvence zprávy požadavku a pořadovým číslem zprávy odpovědi.  
  
#### <a name="retrying-replies"></a>Opakování pokusu o odpovědi  
 WCF spoléhá na korelace požadavku a odpovědi HTTP pro korelace protokol exchange obousměrný zprávy. Z tohoto důvodu je iniciátor WCF nezastaví opakování zprávy sekvence do požadavku při potvrzení pořadí zprávy s požadavkem, ale spíše, při představuje odpověď HTTP `SequenceAcknowledgement`, odpověď aplikace nebo selhání. WCF respondér zopakuje pokus o odpovědi na odpovědi HTTP požadavku, ke kterému je korelační odpověď.  
  
#### <a name="closesequence-exchange"></a>CloseSequence Exchange  
 Po přijetí všechny zprávy sekvence odpovědí a potvrzení pro všechny zprávy sekvence jednosměrný požadavek, přenáší iniciátoru WCF `CloseSequence` zpráva sekvence požadavku na požadavek HTTP a očekává, že `CloseSequenceResponse` na odpovědi HTTP.  
  
 Zavřením sekvence požadavku implicitně zavření sekvence odpovědí. To znamená, že je iniciátor WCF obsahuje koncový sekvence odpovědí `SequenceAcknowledgement` na `CloseSequence` zprávu a sekvence odpovědí nemá `CloseSequence` exchange.  
  
 WCF respondér zajišťuje všechny odpovědi jsou potvrzeny a vysílá `CloseSequenceResponse` zprávy na odpovědi HTTP.  
  
#### <a name="terminatesequence-exchange"></a>TerminateSequence dříve Exchange  
 Po přijetí `CloseSequenceResponse` přenáší zprávy, iniciátor WCF `TerminateSequence` zpráva sekvence požadavku na požadavek HTTP a očekává, že `TerminateSequenceResponse` na odpovědi HTTP.  
  
 Podobně jako `CloseSequence` exchange ukončuje sekvence požadavku implicitně ukončí sekvence odpovědí. To znamená, že je iniciátor WCF obsahuje koncový sekvence odpovědí `SequenceAcknowledgement` na `TerminateSequence` zprávu a sekvence odpovědí nemá `TerminateSequence` exchange.  
  
 Přenáší respondér WCF `TerminateSequenceResponse` zprávy na odpovědi HTTP.  
  
### <a name="requestreply-addressable-initiator"></a>Žádost odpověď, adresovatelný iniciátor  
  
#### <a name="binding"></a>Vazba  
 WCF poskytuje vzoru výměny zpráv žádost odpověď pomocí dvou pořadí více než jeden vstupní a jednu výstupní kanál protokolu HTTP. Tento vzorce výměny zpráv lze kombinovat s `Duplex, Addressable` vzoru výměny zpráv iniciátoru omezeným způsobem. WCF používá k přenosu všech zpráv požadavků HTTP. Všechny odpovědi protokolu HTTP být prázdným textem zprávy a stavovým kódem HTTP 202.  
  
#### <a name="createsequence-exchange"></a>CreateSequence Exchange  
 Iniciátor WCF přenáší `CreateSequence` zprávy s `Offer` elementu na požadavek HTTP. WCF respondér zajišťuje, že `CreateSequence` má `Offer` prvek pak vytvoří sekvenci a přenáší `CreateSequenceResponse` zprávy s `Accept` elementu.  
  
#### <a name="requestreply-correlation"></a>Korelace požadavku/odpovědi  
 Následující část se vztahuje na všechny korelační požadavky a odpovědi:  
  
-   Zajišťuje také nesete zprávy požadavku všechny aplikace, WCF `ReplyTo` reference koncového bodu a `MessageId`.  
  
-   WCF platí odkaz na místní koncový bod jako každou zprávu požadavku aplikace `ReplyTo`. Odkaz na místním koncovým bodem je `CreateSequence` zprávy `ReplyTo` pro iniciátor a `CreateSequence` zprávy `To` pro respondér.  
  
-   WCF zajišťuje také nesete zprávy příchozí žádosti `MessageId` a `ReplyTo`.  
  
-   Zajišťuje WCF `ReplyTo` reference koncového bodu identifikátor URI zprávy požadavku všechny aplikace odpovídat odkaz na místní koncový bod definovaný dříve.  
  
-   WCF se zajistí, že všechny odpovědi označena správná `RelatesTo` a `To` záhlaví po `wsa` pravidla korelace požadavku/odpovědi.
