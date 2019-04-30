---
title: Protokoly zasílání zpráv
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: a5292914cfebc79bf8a9af1c852dd8feec99eba4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61948119"
---
# <a name="messaging-protocols"></a>Protokoly zasílání zpráv

Zásobník kanál Windows Communication Foundation (WCF) používá kódování a přenos kanály pro transformaci zprávě interní reprezentace do jeho přenosový formát a jejich odesílání pomocí konkrétní přenos. Je nejběžnější přenos používá pro interoperabilitu webových služeb HTTP a nejběžnější kódování používá webové služby jsou zpráv přenosu optimalizace mechanismus (MTOM), založený na formátu XML SOAP 1.1 a SOAP 1.2.

Toto téma obsahuje podrobnosti o těchto protokolů náhradník implementaci WCF <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.

Dokument/specifikace:

- [HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)
- [Ze SOAP 1.1 vazbu protokolu HTTP](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), část 7
- [Ze SOAP 1.2 vazby HTTP](https://www.w3.org/TR/soap12-part2) sekce 7

Toto téma obsahuje podrobnosti o implementaci WCF pro následující protokoly <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> využívat.

Dokument/specifikace:

- [XML](https://www.w3.org/TR/REC-xml)
- [PROTOKOL SOAP 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [Ze SOAP 1.2 Core](https://www.w3.org/TR/soap12-part1/)
- [WS-Addressing 2004/08](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [W3C webových služeb adresování Core 1.0-](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [W3C webových služeb adresování 1.0 - vazba SOAP](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [W3C webových služeb adresování 1.0 - Vazba WSDL](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [W3C webových služeb adresování 1.0 - metadat](https://www.w3.org/TR/ws-addr-metadata/)
- [Vazba WSDL SOAP1.1](https://www.w3.org/TR/wsdl/)
- [Vazba WSDL SOAP1.2](https://www.w3.org/Submission/wsdl11soap12/)

Toto téma obsahuje podrobnosti o implementaci WCF pro následující protokoly <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> využívá.

Dokument/specifikace:

- [XOP](https://www.w3.org/TR/xop10/)
- [MTOM + SOAP 1.2 vazby](https://www.w3.org/TR/soap12-mtom/)
- [MTOM SOAP 1.1 vazbu](https://www.w3.org/Submission/soap11mtom10/)
- [Kontrolní výraz MTOM WS-Policy](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

Následující obory názvů XML a přidružené předpony se používají v tomto tématu:

| Předpona | Namespace Uniform Resource Identifier (URI) |
|------------|---------------------------------------------------|
| s11 | `http://schemas.xmlsoap.org/soap/envelope` |
| s12 |`http://www.w3.org/2003/05/soap-envelope` |
| wsa |`http://www.w3.org/2004/08/addressing` |
| wsam |`http://www.w3.org/2007/05/addressing/metadata` |
| wsap |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| wsa10 |`http://www.w3.org/2005/08/addressing` |
| wsaw10 |`http://www.w3.org/2006/05/addressing/wsdl` |
| XOP |`http://www.w3.org/2004/08/xop/include` |
| xmime |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| dp |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a>Protokol SOAP 1.1 a SOAP 1.2

### <a name="envelope-and-processing-model"></a>Obálka a zpracování modelu
WCF implementuje zpracování obálky protokolu SOAP 1.1 Basic Profile 1.1 (základní parametr 11) a základní profil 1.0 (SSBP10). Ze SOAP 1.2 obálky zpracování se implementují podle SOAP12 – část 1.

Tato část popisuje některé volby implementace provedenou WCF s ohledem na základní parametr 11 a SOAP12 – část 1.

#### <a name="mandatory-header-processing"></a>Zpracování povinnou hlavičku
WCF dodržuje pravidla pro zpracování záhlaví označená `mustUnderstand` podle specifikace SOAP 1.1 a SOAP 1.2 s následujícím změnám.

Zpráva, která vstupuje do zásobníku kanál WCF zpracovává jednotlivé kanály nakonfiguroval prvky přidružené vazeb, například kódování textu zprávy, zabezpečení, spolehlivé zasílání zpráv a transakce. Každý kanál rozpozná hlavičky z oboru přidružených a označí je jako srozumitelný. Jakmile zprávu zadá dispečer, načte formátovací modul operace záhlaví očekává odpovídající zpráva nebo operace kontraktu a značky, které je srozumitelný. Dispečer se ověří, zda nejsou žádné zbývající záhlaví porozuměl jsem jim ale označené jako `mustUnderstand` a vyvolá výjimku. Zprávy, které obsahují `mustUnderstand` hlavičky, které jsou cíleny na straně příjemce nezpracovávají kódem přijímající aplikace.

Tyto vrstvy zpracování umožňuje oddělení mezi vrstev infrastruktury a aplikací vrstvy uzlu SOAP:

- B1111: Zjištění hlavičky, které nejsou rozpoznána. po zpracování zprávy zásobník infrastruktury kanálu WCF, ale předtím, než je zpracován programovacím modelem aplikace

     `mustUnderstand` Hodnota hlavičky se liší mezi SOAP 1.1 a SOAP 1.2. Basic Profile 1.1 vyžaduje, aby `mustUnderstand` hodnota být 0 nebo 1 pro zprávy SOAP 1.1. Protokol SOAP 1.2 umožňuje 0, 1, `false`, a `true` hodnoty, ale doporučuje generování canonical reprezentace `xs:boolean` hodnoty (`false`, `true`).

- B1112: Vysílá WCF `mustUnderstand` hodnoty 0 a 1 pro verze protokolu SOAP 1.1 a SOAP 1.2 obálku protokolu SOAP. WCF přijímá celou hodnotu prostor `xs:boolean` pro `mustUnderstand` záhlaví (0, 1, `false`, `true`)

#### <a name="soap-faults"></a>Chyby protokolu SOAP
Následuje seznam implementace proti konkrétní WCF SOAP.

- B2121: Vrátí následující kódy chyb protokolu SOAP 1.1 WCF: `s11:mustUnderstand`, `s11:Client`, a `s11:Server`.

- B2122: Vrátí následující kódy chyb protokolu SOAP 1.2 WCF: `s12:MustUnderstand`, `s12:Sender`, a `s12:Receiver`.

### <a name="http-binding"></a>Vazbu protokolu HTTP

#### <a name="soap-11-http-binding"></a>Ze SOAP 1.1 vazbu protokolu HTTP
WCF implementuje vazby SOAP1.1 HTTP podle specifikace Basic Profile 1.1 s následující vyjasnění části 3.4:

- B2211: Služba WCF neimplementuje přesměrování požadavků HTTP POST.

- B2212: Klienti WCF podporují soubory cookie protokolu HTTP v souladu s 3.4.8.

#### <a name="soap-12-http-binding"></a>Ze SOAP 1.2 vazbu protokolu HTTP
WCF implementuje vazba SOAP 1.2 HTTP, jak je popsáno ve specifikaci protokolu SOAP 1.2 – část 2 (SOAP12Part2) s následující vyjasnění.

Parametr volitelný akce pro zavedené SOAP 1.2 `application/soap+xml` typ média. Tento parametr je užitečný pro optimalizaci odeslání zprávy bez nutnosti analyzovat text zprávy protokolu SOAP při adresování WS-Addressing není použit.

- R2221: `application/soap+xml` Parametr akce, pokud je k dispozici na vyžádání SOAP 1.2, musí odpovídat `soapAction` atribut na `wsoap12:operation` element v rámci odpovídající Vazba WSDL.

- R2222: `application/soap+xml` Musí odpovídat parametru akce, pokud je k dispozici na zprávu protokolu SOAP 1.2 `wsa:Action` při použití WS-Addressing 2004/08 nebo WS-Addressing 1.0.

Když příchozí požadavek neobsahuje parametr akce WS-Addressing je zakázaná, zpráva `Action` je považováno za nevyhovující zadané.

## <a name="ws-addressing"></a>WS-Addressing
WCF implementuje 3 verze WS-Addressing:

- WS-Addressing 2004/08

- Webové služby W3C adresování Core 1.0 (ADDR10 než CORE) a SOAP vazby (ADDR10 protokolu SOAP)

- WS-Addressing 1.0 - metadat

### <a name="endpoint-references"></a>Reference koncového bodu
Všechny verze WS-Addressing, který implementuje WCF pomocí odkazů na koncový bod k popisu koncových bodů.

#### <a name="endpoint-references-and-ws-addressing-versions"></a>Reference koncového bodu a WS-Addressing verze
WCF implementuje číslo z protokolů infrastruktury, které používají WS-Addressing, zejména `EndpointReference` elementu a `W3C.WsAddressing.EndpointReferenceType` tříd (například WS-ReliableMessaging, WS-SecureConversation a WS-Trust). WCF podporuje používání jedné verze elementu WS-Addressing s dalšími protokoly infrastruktury. Koncových bodů WCF podporovat jednu verzi elementu WS-Addressing jeden koncový bod.

Pro R3111, obor názvů pro `EndpointReference` element nebo typ použitý v zpráv pomocí koncových bodů WCF, které si vyměňují musí odpovídat verzi elementu WS-Addressing implementovaná tímto koncovým bodem.

Například, pokud koncový bod WCF implementuje WS-ReliableMessaging `AcksTo` vrácený takové koncový bod v záhlaví `CreateSequenceResponse` používá verzi elementu WS-Addressing, který `EncodingBinding` prvek určuje pro tento koncový bod.

#### <a name="endpoint-references-and-metadata"></a>Reference koncového bodu a metadat
Různé scénáře vyžadují komunikaci metadata nebo odkaz na metadata pro daný koncový bod.

B3121: WCF využívá mechanismy, které je popsáno ve specifikaci WS-MetadataExchange (MEX) části 6 obsahovat metadata ohledně Reference koncového bodu podle hodnoty nebo odkazu.

Představte si třeba situaci, kde služba WCF vyžaduje ověřování pomocí tokenu zabezpečení kontrolní výrazy SAML (Markup Language) vydaného službou vydavatel tokenu v `http://sts.fabrikam123.com`. Koncový bod WCF popisuje tento požadavek ověřování s použitím `sp:IssuedToken` kontrolní výraz s vnořeným `sp:Issuer` kontrolní výraz odkazuje na vydavatele tokenu. Klientské aplikace, které přistupují k `sp:Issuer` kontrolní výraz potřebovat vědět, jak ke komunikaci s koncovým bodem vydavatel tokenu. Klient musí vědět, metadata o vydavatel tokenu. Pomocí rozšíření metadat odkaz na koncový bod definovaný v MEX, WCF poskytuje odkaz na metadata vydavatele tokenu.

```xml
<sp:IssuedToken>
  <sp:Issuer>
    <wsa10:Address>
      http://sts.fabrikam123.com
    </wsa10:Address>
    <wsa10:Metadata>
      <mex:Metadata>
        <mex:MetadataSection>
          <mex:MetadataReference>
            <wsa10:Address>
              http://sts.fabrikam123.com/mex
            </wsa10:Address>
          </mex:MetadataReference>
        </mex:MetadataSection>
      </mex:Metadata>
    </wsa10:Metadata>
  </sp:Issuer>
</sp:IssuedToken>
```

### <a name="message-addressing-headers"></a>Záhlaví adresování zpráv

#### <a name="message-headers"></a>Záhlaví zpráv
Pro obě verze WS-Addressing WCF používá následující záhlaví zpráv podle specifikace `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, a `wsa:RelatesTo`.

B3211: Pro všechny verze WS-Addressing, respektuje WCF, ale nevytvoří hned po spuštění záhlaví zpráv WS-Addressing `wsa:FaultTo` a `wsa:From`.

Aplikace, které pracují s aplikací služby WCF můžete přidat že tyto hlavičky zpráv a WCF se jejich zpracování odpovídajícím způsobem.

#### <a name="reference-parameters-and-properties"></a>Odkaz na parametry a vlastnosti

WCF implementuje zpracování parametrů odkaz na koncový bod a vlastnosti odkaz v souladu s odpovídající specifikací.

B3221: Když konfigurován pro použití WS-Addressing 2004/08, koncových bodů WCF nerozlišují mezi zpracování vlastnosti odkazu a parametry odkazů.

### <a name="message-exchange-patterns"></a>Vzorky serveru Exchange zprávu
Pořadí zpráv při volání operace webové služby, které se označuje jako *vzoru výměny zpráv*. Podporuje WCF jednosměrné, požadavek odpověď a duplexní zprávy vyměňují vzory. Tato část vysvětluje WS-Addressing požadavky na zpracování v závislosti na vzorce výměny zpráv používá zprávy.

V celé této části se pošle žadateli první zprávu a příjemce dostane první zprávu.

#### <a name="one-way-message"></a>Jednosměrná zpráva
Když koncového bodu WCF je nakonfigurována pro podporu zprávy s daný `Action` dodržovat jednosměrné vzor koncového bodu WCF následuje následující chování a požadavky. Pokud není uvedeno jinak, platí pro obě verze WS-Addressing podporované ve službě WCF chování a pravidla:

- R3311: Musí zahrnovat žadateli `wsa:To`, `wsa:Action`, tak i hlaviček parametrů odkaz na určeném reference koncového bodu. Když se používá WS-Addressing 2004/08 a [referenční vlastnosti] jsou určena podle reference koncového bodu odpovídající záhlaví musí být přidané do zprávy příliš.

- B3312: Může zahrnovat žadateli `MessageID`, `ReplyTo`, a `FaultTo` záhlaví. Příjemce infrastruktury je bude ignorovat a bude předávat do aplikace.

- R3313: Když se používá protokol HTTP a žádná zpráva se odesílá na větev odpovědi protokolu HTTP, musíte odeslat straně odpovídajícího odpověď HTTP s prázdným textem zprávy a stavový kód HTTP 202.

     Když kontrakt deklaruje zprávu jednosměrný přenos pomocí protokolu HTTP se používá, odpověď HTTP je stále možné pro odesílání zpráv infrastruktury – například můžete odesílat spolehlivé zasílání zpráv `SequenceAcknowledgement` zprávu na odpovědi HTTP.

- B3314: WCF respondér neodesílá zprávu o chybě v reakci na zprávu jednosměrná.

#### <a name="request-reply"></a>Požadavek a odpověď
Když koncového bodu WCF je nakonfigurován pro zprávu s danou `Action` Pokud chcete postupovat podle vzoru požadavek odpověď, koncového bodu WCF řídí chování a požadavcích na. Pokud není uvedeno jinak, platí pro obě verze WS-Addressing podporované ve službě WCF chování a pravidla:

- R3321: V požadavku musí obsahovat žadateli `wsa:To`, `wsa:Action`, `wsa:MessageID`, tak i hlaviček pro všechny parametry odkazu nebo referenční vlastnosti (nebo obojí) určené reference koncového bodu.

- R3322: Při použití WS-Addressing 2004/08 `ReplyTo` musí také obsahovat žádosti.

- R3323: Při použití WS-Addressing 1.0 a `ReplyTo` není k dispozici v požadavku, výchozí koncový bod odkaz s vlastností [address] rovna `http://www.w3.org/2005/08/addressing/anonymous` se používá.

- R3324: Musí zahrnovat žadateli `wsa:To`, `wsa:Action`, a `wsa:RelatesTo` záhlaví ve zprávě odpovědi a také hlavičky pro všechny parametry odkazu nebo referenční vlastnosti (nebo obojí) určené `ReplyTo` reference koncového bodu v požadavku.

### <a name="web-services-addressing-faults"></a>Na vyřešení chyby webové služby
R3411: WCF vytvoří následující chyby definované WS-Addressing 2004/08.

| Kód | Příčina |
|----------|-----------|
| `wsa:DestinationUnreachable` | Zpráva dorazila s `ReplyTo` , která se liší od adresa pro odpovědi pro tento kanál, neexistuje žádný koncový bod na adrese určené v záhlaví Komu. |
| `wsa:ActionNotSupported` | kanály infrastruktury nebo dispečer spojená s koncovým bodem nebyl rozpoznán akce určená ve `Action` záhlaví. |

R3412: WCF vytvoří následující chyby definované WS-Addressing 1.0.

| Kód | Příčina |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | Duplicitní `wsa:To`, `wsa:ReplyTo`, `wsa:From` nebo `wsa:MessageID`. Duplicitní `wsa:RelatesTo` se stejným `RelationshipType`. |
| `wsa10:MessageAddressingHeaderRequired` | Chybí požadované záhlaví adresování. |
| `wsa10:DestinationUnreachable` | Zpráva dorazila s `ReplyTo` , která se liší od adresa pro odpovědi pro tento kanál. Neexistuje žádný koncový bod na adrese určené v záhlaví Komu. |
| `wsa10:ActionNotSupported` | Zadaná v akci `Action` hlavička nebyla rozpoznána infrastruktury kanály nebo dispečer spojená s koncovým bodem. |
| `wsa10:EndpointUnavailable` | Kanál RM odešle tato porucha zpět, která koncový bod nezpracuje pořadí na základě posouzení `CreateSequence` adrese záhlaví zprávy. |

Do mapy kódu v předchozích tabulkách `FaultCode` v protokolu SOAP 1.1 a `SubCode` (kód = odesílatele) v protokolu SOAP 1.2.

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1.1 vazbu a kontrolní výrazy WS-Policy

#### <a name="indicating-use-of-ws-addressing"></a>Použití elementu WS-Addressing označující
WCF používá k označení podporu koncového bodu pro konkrétní verzi elementu WS-Addressing kontrolní výrazy zásad.

Následující kontrolní výraz zásad má koncový bod zásad předmět [WS-PA] a indikuje, že zprávy odeslané a přijaté z koncového bodu musí používat WS-Addressing 2004/08.

```xml
<wsap:UsingAddressing />
```

Tento kontrolní výraz zásad argumentech specifikaci WS-Addressing 2004/08.

Následující výraz zásad, že to znamená, že zprávy odeslat/přijmout musí používat WS-Addressing 1.0.

```xml
<wsam:Addressing/>
```

Následující kontrolní výraz zásad má předmět zásad koncový bod [WS-PA] a označuje, že musíte používat zprávy odeslané a přijaté z koncového bodu WS-Addressing 2004/08.

```xml
<wsaw10:UsingAddressing />
```

`wsaw10:UsingAddressing` Element si z [WS-Addressing-WSDL] a používá se v kontextu v souladu s specifikaci WS-Policy, části 3.1.2.

Použijte adresování nezmění sémantiku WSDL 1.1, SOAP 1.1 a SOAP 1.2 HTTP vazeb. Například pokud odpověď na žádost o odeslání do koncového bodu, který používá vazbu protokolu HTTP 1.x adresování a WSDL SOAP, musí poslat odpověď pomocí odpovědi HTTP.

O reakcích zaslaného prostřednictvím protokolu http odpovědi je WS-AM kontrolního výrazu:

```xml
<wsam:AnonymousResponses/>
```

Kontrolní výraz zásad dokončení může vypadat takto:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Existují však zpráv exchange vzory, kterým přináší výhody máte dvě nezávislé konverzace HTTP připojení mezi žadatelem a respondér, například nevyžádané jednosměrné zprávy odesílané straně odpovídajícího.

WCF nabízí funkce, pomocí kterého můžete tvoří dvě základní přenosové kanály kompozitní duplexní kanál, ve kterém jeden kanál se používá pro zprávy o zadávání a druhý se používá pro výstupní zprávy. V případě přenos pomocí protokolu HTTP kompozitní duplexní poskytuje dvě připojení HTTP konverzace. Žadatel používá jedno připojení pro odesílání zpráv na straně odpovídajícího a druhé straně odpovídajícího používá k odesílání zpráv zpět žadateli.

O reakcích zaslaného prostřednictvím požadavků http samostatné je kontrolní výraz ws-am

```xml
<wsam:NonAnonymousResponses/>
```

Kontrolní výraz zásad dokončení může vypadat takto:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Použijte následující kontrolní výraz, který má koncový bod zásad subjektu [WS-PA] na koncové body, které používají vazby WSDL 1.1 SOAP 1.x HTTP vyžaduje dva samostatné konverzace připojení protokolu HTTP má být použit pro zpráv odesílaných ze žadatel respondér a respondér žadatel, v uvedeném pořadí.

```xml
<cdp:CompositeDuplex/>
```

Předchozí příkaz vede k následující požadavky `wsa:ReplyTo` záhlaví zpráv požadavku:

- R3514: Požádat o zprávy odeslané do koncového bodu musí mít `ReplyTo` záhlaví s `[address]` vlastnost `http://www.w3.org/2005/08/addressing/anonymous` Pokud koncový bod používá vazby WSDL 1.1 SOAP 1.x HTTP a má alternativní zásady s `wsap10:UsingAddressing` nebo `wsap:UsingAddressing` kontrolního výrazu s velkou provázaností `cdp:CompositeDuplex` připojen.

- R3515: Požádat o zprávy odeslané do koncového bodu musí mít `ReplyTo` záhlaví s `[address]` vlastností `http://www.w3.org/2005/08/addressing/anonymous`, nebo není `ReplyTo` záhlaví na všechny, pokud koncový bod používá vazby WSDL 1.1 SOAP 1.x HTTP a má alternativní zásady s `wsap10:UsingAddressing` kontrolní výraz a ne `cdp:CompositeDuplex` kontrolní výraz připojen.

- R3516: Požádat o zprávy odeslané do koncového bodu musí mít `ReplyTo` záhlaví s `[address]` vlastností `http://www.w3.org/2005/08/addressing/anonymous` Pokud koncový bod používá vazby WSDL 1.1 SOAP 1.x HTTP a má alternativní zásady s `wsap:UsingAddressing` kontrolní výraz a ne `cdp:CompositeDuplex` kontrolní výraz připojen.

Specifikace WS-addressing WSDL pokusí popisují podobnými vazbami protokol zavedením element `<wsaw:Anonymous/>` tři textové hodnoty (povinné, volitelné a zakázané) k označení požadavky na `wsa:ReplyTo` hlavičky (část 3.2). Bohužel tyto definice prvku není jako kontrolní výraz v kontextu aplikace WS-Policy, zejména použitelné, protože vyžaduje specifického pro doménu rozšíření pro podporu je určena průsečíkem alternativy pomocí takový prvek jako kontrolní výraz. Tato definice prvku také určuje hodnotu `ReplyTo` záhlaví na rozdíl od chování koncového bodu na lince, což usnadňuje konkrétní přenos pomocí protokolu HTTP.

#### <a name="action-definition"></a>Definice akce
Definuje WS-Addressing 2004/08 `wsa:Action` atribut pro `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementy. WS-Addressing 1.0 WSDL vazby (WS-ADDR10 WSDL) definuje podobně jako atribut `wsaw10:Action`.

Jediným rozdílem mezi těmito dvěma je výchozí akce vzor sémantiku podle 3.3.2 WS-ADDR a části bodu 4.4.4 WS-ADDR10-WSDL.

Je možné logicky mít dva koncové body, které sdílejí stejný `portType` (nebo smlouvy, v, řečeno terminologií WCF), ale používáte různé verze WS-Addressing. Ale vzhledem k tomu, že je definována akce `portType` a by neměly měnit napříč koncovými body, které implementují `portType`, bude možné podporovat obě výchozí akci zpracování.

Chcete-li vyřešit tento spor, WCF podporuje jednu verzi `Action` atribut.

B3521: Používá WCF `wsaw10:Action` atribut na `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementy definované v WS-ADDR10-WSDL k určení `Action` identifikátor URI pro odpovídající zprávy bez ohledu na verzi elementu WS-Addressing používá koncový bod.

#### <a name="use-endpoint-reference-inside-wsdl-port"></a>Použití koncového bodu odkaz na vnitřní WSDL portu
WS WSDL ADDR10 oddíle 4.1 rozšiřuje `wsdl:port` prvek, který chcete zahrnout `<wsa10:EndpointReference…/>` podřízený prvek k podrobnému popisu, koncový bod WS-Addressing podmínky. Tento nástroj na WS-Addressing 2004/08 rozbalí WCF umožňuje `<wsa:EndpointReference…/>` jako podřízený prvek `wsdl:port`.

- R3531: Pokud koncový bod má alternativu připojené zásady s `<wsaw10:UsingAddressing/>` kontrolního výrazu zásad odpovídající `wsdl:port` element může obsahovat podřízený element `<wsa10:EndpointReference …/>`.

- R3532: Pokud `wsdl:port` obsahuje podřízený element `<wsa10:EndpointReference …/>`, `wsa10:EndpointReference/wsa10:Address` hodnota podřízeného elementu musí odpovídat hodnotě `@address` atribut na stejné úrovni `wsdl:port` / `wsdl:location` elementu.

- R3533: Pokud koncový bod má alternativu připojené zásady s `<wsap:UsingAddressing/>` kontrolního výrazu zásad odpovídající `wsdl:port` element může obsahovat podřízený element `<wsa:EndpointReference …/>`.

- R3534: Pokud `wsdl:port` obsahuje podřízený element `<wsa:EndpointReference …/>`, `wsa:EndpointReference/wsa:Address` hodnota podřízeného elementu musí odpovídat hodnotě `@address` atribut na stejné úrovni `wsdl:port` / `wsdl:location` elementu.

### <a name="composition-with-ws-security"></a>Kompozice s WS-Security
Podle části posouzení zabezpečení v WS-ADDR a WS-ADDR10 všechny adresování zpráv hlavičky doporučují podepsat spolu s text zprávy je svázat dohromady.

Pokud WS-Security slouží pro ochranu integrity zprávy, musí být podepsané zprávy WS-Addressing, záhlaví, jakož i hlavičky je výsledkem odkaz parametry vlastnosti (nebo obojí) společně s tělo zprávy.

### <a name="examples"></a>Příklady

#### <a name="one-way-message"></a>Jednosměrná zpráva
V tomto scénáři odesílatel odešle zprávu jednosměrné příjemci. SOAP 1.2, protokol HTTP 1.1 a 1.0 W3C WS-Addressing se používají.

Struktura zprávy požadavku: Zahrnout záhlaví zpráv `wsa10:To` a `wsa10:Action` elementy. Tělo zprávy obsahuje konkrétní `<app:Ping>` element z oboru aplikace.

Hlavičky protokolu HTTP: Odpovídá identifikátoru URI v cíli v příspěvku `wsa10:To` elementu.

Hlavička Content-Type má hodnotu `application/soap+xml` podle požadavku SOAP 1.2. Parametry `charset` a `action` jsou zahrnuty. `action` Odpovídá hodnotě parametru hlavičku Content-Type `wsa10:Action` záhlaví zprávy.

```
POST http://fabrikam123.com/Service HTTP/1.1
Content-Type: application/soap+xml; charset=utf-8;  
              action="http://fabrikam123.com/Service/OneWay"
Host: 131.107.72.15
Content-Length: 1501
Expect: 100-continue
Proxy-Connection: Keep-Alive
<s12:Envelope>
  <s12:Header>
    <wsa10:To s12:mustUnderstand="1">
        http://fabrikam123.com/Service
    </wsa10:To>
    <wsa10:Action s12:mustUnderstand="1">
        http://fabrikam123.com/Service/OneWay 
    </wsa10:Action>
  </s12:Header>
  <s12:Body>
    <Ping xmlns="http://fabrikam123.com/Service/">
      <Text>Hello World</Text>
    </Ping>
  </s12:Body>
</s12:Envelope>
```

Příjemce odpoví prázdnou odpověď HTTP a stav 202. Příklad odpovědi protokolu HTTP:

```
HTTP/1.1 202 Accepted
Date: Fri, 15 Jul 2005 08:56:07 GMT
Server: Microsoft-IIS/6.0
MicrosoftOfficeWebServer: 5.0_Pub
X-Powered-By: ASP.NET
X-AspNet-Version: 2.0.50215
Cache-Control: private
Content-Length: 0
```

## <a name="soap-message-transmission-optimization-mechanism"></a>Mechanismus optimalizaci přenosu zprávy protokolu SOAP
Tato část popisuje podrobnosti implementace WCF MTOM SOAP protokolu HTTP. Technologie MTOM je mechanismus kódování SOAP zprávy stejné třídy jako kódování tradiční text/XML nebo WCF binární kódování. MTOM zahrnuje následující položky:

- Kódování XML a balení mechanismus popsal [XOP], který optimalizuje XML informačních položek do samostatných částí binární obsahující binární data zakódovaná ve formátu base64.

- Zapouzdření MIME XOP balíčku, který serializuje informační sadu XML a každá část binární balíčku XOP do samostatné části MIME.

- MIME XOP kódování u protokolu SOAP 1.x obálky.

- HTTP přenosu vazby.

Je možné použít MTOM s jiným protokolem než HTTP přenosy s použitím technologie WCF. Ale v tomto tématu se zaměříme na protokolu HTTP.

Formát MTOM využívá velké sady specifikace pokrývající MTOM samotné XOP a MIME. Modularitu této specifikace sady je poněkud obtížné rekonstrukci přesných požadavcích na sémantiku formátu a zpracování. Tato část popisuje požadavky na zpracování a formát vazby MTOM HTTP.

### <a name="mtom-message-encoding"></a>Kódování MTOM zpráv

#### <a name="generating-mtom-messages"></a>Generování zprávy MTOM
[XOP] části 3.1 popisuje postup kódování XML pomocí elementu informačních položek, které obsahují hodnoty ve formátu base64 do abstraktně definovaná balíčku XOP.

Následující sled kroků popisuje proces kódování MTOM konkrétní:

1. Zajistěte, aby obsahoval obálku protokolu SOAP být zakódovaný, aby se žádná položka informace o elementu s `[namespace name]` z `http://www.w3.org/2004/08/xop/include` a `[local name]` z `Include`.

2. Vytvořte prázdný balíček MIME.

3. Identifikujte v rámci původní XML informační sadu položek informací elementu optimalizovat. Pro položky, které chcete optimalizovat, znaky, které tvoří `[children]` informace prvku položky musí být v kanonickém tvaru z `xs:base64Binary` (viz XSD-2, 3.2.16 base64Binary) a nesmí obsahovat žádné prázdné znaky před vložené, nebo Následující obsah prázdné znaky.

4. Vytvoří obálku protokolu SOAP XOP, který je kopií původního obálku protokolu SOAP, ale s podřízenými informace každého prvku bod identifikován v předchozím kroku nahrazuje `xop:Include` položka informací o elementu vypočte takto:

    1. Transformujte nahrazené znaků na binární data zpracováním jako data zakódovaná ve formátu base64.

    2. Generovat jedinečný hodnota hlavičky Content-ID, která splňuje požadavky R3133 a R3134.

    3. Vygenerujte hlavička MIME Content-Transfer-Encoding s binární hodnotu.

    4. Pokud element položka informací o optimalizaci ([nadřazený] nově vloženou `xop:Include` položek informací elementu) má `xmime:contentType` atribut položky informace, generování záhlaví Content-Type MIME s hodnotou `xmime:contentType` atribut.

    5. Generovat nové binární část MIME s obsahem tvořen binární data dekódovaná z nahrazené znaky zpracovány jako base64, Hlavička Content-ID z 4b, Hlavička Content-Transfer-Encoding ze 4 jádra, Hlavička Content-Type, pokud je vygenerovaný v kroku 4d.

    6. Přidat `href` atribut `xop:Include` element s hodnotou cid: identifikátor uri odvozený od hodnota hlavičky Content-ID vygenerované v kroku 4b. Odebrat nadřazený "\<" a ">" znaky adresy URL řídicí zbývající řetězec a přidejte tuto předponu `cid:`. Následující minimální znaková sada je povinná-li být uvozena RFC1738 a RFC2396. Může být uvozena jiné znaky.

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. Vytvoření kořenové části MIME se XOP obálku protokolu SOAP z kroku 4.

6. Zápis hlavičky protokolu HTTP, včetně hlavičku HTTP Content-Type.

7. Zapsat balíček MIME.

#### <a name="processing-mtom-messages"></a>Zpracování zprávy MTOM
Zpracování MTOM zpráva je přesně naopak procesu popsaného v předchozím "generování MTOM zprávy" části:

1. Ujistěte se, má kořenová část MIME Content-Type `application/xop+xml`.

2. Sestavení obálky protokolu SOAP analýzou kořenovou část MIME balíčku jako dokument XML. Kódování znaků závisí `charset` parametru Content-Type kořenovou část MIME.

3. Pro každou položku element informace konstruovaný obálku protokolu SOAP, která má, jako jedinými členy vlastností [podřízené] `xop:Include` položek informací elementu:

    1. Odeberte `cid:` Předpona a unescape – identifikátor URI – řídicí sekvence všechny (RFC 2396) v hodnotě `@href` atribut `xop:Include` elementu. Uzavřete výsledný řetězec v "\<", ">".

    2. Vyhledejte část MIME s hodnota hlavičky Content-ID, který se shoduje s řetězcem odvozené v kroku 3a.

    3. Nahradit `xop:Include` položka informací o elementu, který se zobrazí `children` vlastnosti každé položky s položkami znak informace, které představují kódování canonical base64 (viz XSD-2, 3.2.16 base64Binary) z obsahu entity část MIME identifikovali v kroku 3b (efektivně nahradit `xop:Include` položka informací o elementu s daty, které jsou znovu vytvořena z část balíček).

#### <a name="http-content-type-header"></a>Hlavičku HTTP Content-Type
Následující seznam obsahuje WCF objasnit, kontaktujte pro formát hlavičky protokolu HTTP Content-Type 1.x kódování MTOM zprávy SOAP odvozený od požadavky uvedené v samotnou specifikaci MTOM a jsou odvozeny z MTOM a dokumentu RFC 2387.

- R4131: Hlavičku HTTP Content-Type musí mít hodnotu multipart/related (velká a malá písmena) a jeho parametry. Názvy parametrů rozlišují velikost písmen. Parametr pořadí není důležité.

- Úplné Backus-Naur formuláře (BNF) hlavičky Content-Type pro zprávy MIME je uvedena v RFC 2045, část 5.1.

- R4132: Hlavičku HTTP Content-Type musí mít parametr typu s hodnotou `application/xop+xml` uzavřený do dvojitých uvozovek.

Požadavek na použití dvojitých uvozovek není definován v dokumentu RFC 2387, text dodržuje všechny parametry typu multipart/related média pravděpodobně obsahovat vyhrazené znaky, jako je "\@" nebo "/" a je proto nutné dvojité uvozovky značky.

- R4133: Hlavičku HTTP Content-Type musí mít parametr počáteční hodnotu hlavičky Content-ID z část MIME obsahující SOAP 1.x obálky, uzavřen do dvojitých uvozovek. Pokud tento parametr spuštění se vynechá, první část MIME musí obsahovat SOAP 1.x obálky.

- R4134: Hlavičku HTTP Content-Type pro zprávu MTOM SOAP 1.1 kódovaný musí obsahovat úvodní informace o parametr s hodnotou typu text/xml, uzavřen do dvojitých uvozovek.

- R4135: Hlavičku HTTP Content-Type pro zprávu SOAP 1.2 MTOM kódovaný musí obsahovat úvodní informace o parametr s hodnotou `application/soap+xml`, uzavřené v dvojitých uvozovkách.

- R4136: Hlavičku HTTP Content-Type pro zprávu MTOM kódováním SOAP 1.x musí mít parametr hranic s hodnotou (uzavřený v dvojitých uvozovkách), který odpovídá ohraničení MIME BNF definovaný v dokumentu RFC 2046 části 5.1.1

    ```
    boundary := 0*69<bchars> bcharsnospace 
    bchars := bcharsnospace / " " 
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+" 
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     Příklady:

     OPRAVIT

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     OPRAVIT

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     NESPRÁVNÝ

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1" 
    ```

#### <a name="infoset-mime-part"></a>Část MIME informační sadu
SOAP 1.x obálky je zapouzdřen v rámci kořenového balíček XOP MIME a se často nazývá `infoset` část.

- R4141: SOAP 1.x obálky musí být zapouzdřen v rámci kořenového balíček XOP MIME, volá se, `infoset` část a odkazované z HTTP Content-Type.

- R4142: SOAP `Infoset` část musí obsahovat následující hlavičky MIME: `Content-ID`, `Content-Transfer-Encoding`, a `Content-Type`.

Formát hlavičky Content-ID je definován specifikací 2045 RFC jako

```
"Content-ID" ":" msg-id
```

kde `msg-id` je definován v dokumentu RFC 2822, (, který nahrazuje RFC 822 odkazovat v dokumentu RFC 2045) jako:

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

a je efektivně e-mailovou adresu uzavřený do složených závorek "\<" a ">". `[CFWS]` Předpon a přípon byly přidány v dokumentu RFC 2822 provádět komentáře a neměl by se zachovat vzájemná funkční spolupráce.

R4143: Musí následovat hodnota záhlaví Content-ID pro část MIME informační sadu `msg-id` produkčním prostředí z 2822 RFC s `[CFWS]` předpon a přípon částí vynechán.

Počet implementací MIME mírnější požadavky pro hodnotu uzavřený do složených závorek "\<" a ">" bude e-mailovou adresu a použít `absoluteURI` uzavřeny v "\<", ">" Kromě e-mailovou adresu. Tato verze služby WCF používá hodnoty hlavičky MIME Content-ID ve formátu:

```
Content-ID: <http://tempuri.org/0> 
```

R4144: Procesory MTOM by měla přijímat hlavička Content-ID hodnoty, které odpovídají následující mírnější `msg-id`.

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

MIME (RFC 2045) obsahuje hlavičku Content-Transfer-Encoding komunikovat kódování obsahu části MIME. Definované pro Content-Transfer-Encoding výchozí hodnota je 7 bitů, což není vhodný pro většinu zprávy protokolu SOAP, takže hlavičku Content-Transfer-Encoding je potřeba větší interoperability:

- R4145: Část SOAP informační sadu musí obsahovat hlavičku Content-Transfer-Encoding.

- R4146: Pokud kódování znaků pro obálku protokolu SOAP je UTF-8, hodnotu hlavičky Content-Transfer-Encoding musí být 8 bitů.

- R4147: Pokud kódování znaků pro obálku protokolu SOAP je UTF-16, musí být binární hodnotu hlavičky Content-Transfer-Encoding.

- Závislosti [XOP] části 5

- R4148: SOAP1.1 informační sadu část musí obsahovat hlavičku Content-Type s typ média application/xop + xml a parametry type = "text/xml" a znaková sada

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- R4149: Část SOAP 1.2 informační sadu musí obsahovat hlavičku Content-Type s typem média `application/xop+xml` a parametry type = "`application/soap+xml`" a `charset`.

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     Zatímco XOP definuje `charset` parametr pro `application/xop+xml` být volitelné, je potřeba podobný BP 1.1 požadavek na funkční spolupráce `charset` parametr pro `text/xml` typ média.

- R41410: `type` a `charset` parametry musí být k dispozici v hlavičce Content-Type části SOAP 1.x informační sadu.

#### <a name="wcf-endpoint-support-for-mtom"></a>Podpora koncových bodů WCF MTOM
Účelem MTOM je určený ke kódování zprávy protokolu SOAP pro optimalizaci dat s kódováním base64. Následuje seznam omezení:

- R4151: Může být optimalizován libovolnou položku informace o elementu, který obsahuje data zakódovaná ve formátu base64.

- B4152: WCF optimalizuje element informačních položek, které obsahují data zakódovaná ve formátu base64 a přesáhnout délku 1024 bajtů.

Koncový bod WCF, který je nakonfigurován pro použití MTOM vždycky odešlou MTOM kódování zprávy. I v případě, že žádné části splňovat požadovaná kritéria, zprávy se stále kódování MTOM (serializovat jako balíček MIME s jednou částí MIME obsahující obálku protokolu SOAP).

### <a name="ws-policy-assertion-for-mtom"></a>Kontrolní výraz WS-Policy pro MTOM
WCF používá k označení MTOM využití koncovým bodem následující kontrolní výraz zásad:

```xml
<wsoma:OptimizedMimeSerialization ... />
```

- R4211: Předchozí kontrolního výrazu zásad má předmětu zásad koncového bodu a určuje, že všechny zprávy odesílané do a z koncového bodu musí být optimalizovalo pomocí MTOM.

- B4212: Pokud konfigurován pro použití MTOM optimalizace, koncový bod WCF přidá kontrolní výraz zásad MTOM zásady připojené k odpovídající `wsdl:binding`.

### <a name="composition-with-ws-security"></a>Kompozice s WS-Security
MTOM je mechanismus, který je podobný `text/xml` a WCF binární formát XML. MTOM nabízí přirozené složení s WS-Security a dalších WS-* protokoly: zpráva zabezpečena WS-Security, lze optimalizovat pomocí funkce MTOM.

### <a name="examples"></a>Příklady

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>WCF SOAP 1.1 zpráva kódovaný pomocí MTOM

```
POST http://131.107.72.15/Mtom/svc/service.svc/Soap11MtomUTF8 HTTP/1.1
SOAPAction: "http://xmlsoap.org/echoBinaryAsString"
Content-Type: multipart/related;type="application/xop+xml";
              start="<http://tempuri.org/0>";start-info="text/xml";
       boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
Host: 131.107.72.15
Content-Length: 1501
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="text/xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/">
  <s:Body>
    <EchoBinaryAsString xmlns="http://xmlsoap.org/Ping">
      <array>
        <xop:Include
         href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206521093670"
         xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </array>
    </EchoBinaryAsString>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
Content-ID: <http://tempuri.org/1/632618206521093670>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
…Binary Content..
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1
```

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>Zabezpečení WCF SOAP 1.2 zpráva kódovaný pomocí MTOM
V tomto příkladu je zpráva kódovaný pomocí MTOM a SOAP 1.2, který je chráněný pomocí WS-Security. Binární částí pro kódování se obsah `BinarySecurityToken`, `CipherValue` z `EncryptedData` odpovídající šifrované podpis a šifrovaného textu. Všimněte si, že `CipherValue` z `EncryptedKey` nebyla identifikována pro optimalizaci službou WCF, protože její délka je menší pak 1024 bajtů.

```
POST http://131.107.72.15/Mtom/service.svc/Soap12MtomSecureSignEncrypt HTTP/1.1
Content-Type: multipart/related; type="application/xop+xml";
              start="<http://tempuri.org/0>";
            boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3";
              start-info="application/soap+xml"; 
              action="http://xmlsoap.org/echoBinaryAsString"
Host: 131.107.72.15
Content-Length: 1941
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/0>
Content-Transfer-Encoding: 8bit
Content-Type: application/xop+xml;charset=utf-8;type="application/soap+xml"
<s:Envelope xmlns:s="http://schemas.xmlsoap.org/soap/envelope/" xmlns:u="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">
  <s:Header>
    <o:Security s:mustUnderstand="1" xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
      <u:Timestamp u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-5">
        <u:Created>2005-09-09T06:57:32.488Z</u:Created>
        <u:Expires>2005-09-09T07:02:32.488Z</u:Expires>
      </u:Timestamp>
      <o:BinarySecurityToken u:Id="uuid-4d4ee765-5717-4d53-9ac9-99bddc07df6c-2" ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509v3" EncodingType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0#Base64Binary">
        <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F1%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
      </o:BinarySecurityToken>
      <e:EncryptedKey Id="_1" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#rsa-oaep-mgf1p"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:KeyIdentifier ValueType="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0#X509SubjectKeyIdentifier">Xeg55vRyK3ZhAEhEf+YT0z986L0=</o:KeyIdentifier>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>          <e:CipherValue>oQfpxwT8/SAGyZQzKE2b4yO6dXuQj7pwJ+5CGL3Rf7C06bQ5ttMoQ9GLJcQYkXTzin+WwHEgs5bj5ml9HKTW9QAU5JJ6lksdymmQvWP5ZtGPBVchO4sofEGoCKmBiZL/DYS/cnbzgnc/3a6NYnc10y2fWGaGLiqa00zijAw7o0Y=</e:CipherValue>
        </e:CipherData>
      </e:EncryptedKey>
      <c:DerivedKeyToken u:Id="_2" xmlns:c="http://schemas.xmlsoap.org/ws/2005/02/sc">
        <o:SecurityTokenReference>
          <o:Reference URI="#_1"/>
        </o:SecurityTokenReference>
        <c:Nonce>OrEPRX7fISIS4sXYWPMv3g==</c:Nonce>
      </c:DerivedKeyToken>
      <e:ReferenceList xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:DataReference URI="#_3"/>
        <e:DataReference URI="#_4"/>
      </e:ReferenceList>
      <e:EncryptedData Id="_4" Type="http://www.w3.org/2001/04/xmlenc#Element" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
        <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
        <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
          <o:SecurityTokenReference>
            <o:Reference URI="#_2"/>
          </o:SecurityTokenReference>
        </KeyInfo>
        <e:CipherData>
          <e:CipherValue>
            <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F2%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
          </e:CipherValue>
        </e:CipherData>
      </e:EncryptedData>
    </o:Security>
  </s:Header>
  <s:Body u:Id="_0">
    <e:EncryptedData Id="_3" Type="http://www.w3.org/2001/04/xmlenc#Content" xmlns:e="http://www.w3.org/2001/04/xmlenc#">
      <e:EncryptionMethod Algorithm="http://www.w3.org/2001/04/xmlenc#aes256-cbc"/>
      <KeyInfo xmlns="http://www.w3.org/2000/09/xmldsig#">
        <o:SecurityTokenReference xmlns:o="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-secext-1.0.xsd">
          <o:Reference URI="#_2"/>
        </o:SecurityTokenReference>
      </KeyInfo>
      <e:CipherData>
        <e:CipherValue>
          <xop:Include href="cid:http%3A%2F%2Ftempuri.org%2F3%2F632618206525089430" xmlns:xop="http://www.w3.org/2004/08/xop/include"/>
        </e:CipherValue>
      </e:CipherData>
    </e:EncryptedData>
  </s:Body>
</s:Envelope>
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/1/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary content of BinarySecurityToken - X509 Certificate...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/2/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted primary signature...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3
Content-ID: <http://tempuri.org/3/632618206525089430>
Content-Transfer-Encoding: binary
Content-Type: application/octet-stream
...Binary serialization of the encrypted Body...
--uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=3--
```