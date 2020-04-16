---
title: Protokoly zasílání zpráv
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 814347c77b54c4450aabf0a4f3966df223360663
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463835"
---
# <a name="messaging-protocols"></a>Protokoly zasílání zpráv

Zásobník kanálu WCF (Windows Communication Foundation) využívá kódování a přenos kanálů k transformaci reprezentace interní zprávy do svého formátu drátu a odeslat pomocí určitého přenosu. Nejběžnější přenos používaný pro interoperabilitu webových služeb je HTTP a nejběžnější kódování používaná webovými službami jsou SOAP 1.1, SOAP 1.2 a Message Transmission Optimization Mechanism (MTOM).

Toto téma popisuje podrobnosti implementace WCF <xref:System.ServiceModel.Channels.HttpTransportBindingElement>pro následující protokoly používané .

Specifikace/dokument:

- [HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)
- [SOAP 1.1 VAZBA HTTP](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), oddíl 7
- [SOAP 1.2 HTTP vazba](https://www.w3.org/TR/soap12-part2) Oddíl 7

Toto téma popisuje podrobnosti implementace WCF pro následující protokoly, které <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> zaměstnávají.

Specifikace/dokument:

- [Xml](https://www.w3.org/TR/REC-xml)
- [MÝDLO 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [MÝDLO 1.2 Jádro](https://www.w3.org/TR/soap12-part1/)
- [WS-Adresování 2004/08](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [W3C Webové služby Adresování 1.0 - Core](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [W3C Web Services Addressing 1.0 - SOAP Binding](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [W3C Webové služby adresování 1.0 - WSDL vazba](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [W3C Web Services Addressing 1.0 - Metadata](https://www.w3.org/TR/ws-addr-metadata/)
- [WSDL SOAP1.1 Vazba](https://www.w3.org/TR/wsdl/)
- [WSDL SOAP1.2 Vazba](https://www.w3.org/Submission/wsdl11soap12/)

Toto téma popisuje podrobnosti implementace WCF pro následující protokoly, které <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> zaměstnává.

Specifikace/dokument:

- [XOP](https://www.w3.org/TR/xop10/)
- [MTOM + SOAP 1.2 Vazba](https://www.w3.org/TR/soap12-mtom/)
- [MTOM SOAP 1.1 Vazba](https://www.w3.org/Submission/soap11mtom10/)
- [Kontrolní výraz zásad služby MTOM WS](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

V celém tématu se používají následující obory názvů XML a přidružené předpony:

| Předpona | Identifikátor prostředku oboru názvů (URI) |
|------------|---------------------------------------------------|
| S11 | `http://schemas.xmlsoap.org/soap/envelope` |
| s12 |`http://www.w3.org/2003/05/soap-envelope` |
| wsa |`http://www.w3.org/2004/08/addressing` |
| wsam (Wsam) |`http://www.w3.org/2007/05/addressing/metadata` |
| wsap |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| wsa10 řekl: |`http://www.w3.org/2005/08/addressing` |
| wsaw10 |`http://www.w3.org/2006/05/addressing/wsdl` |
| xop |`http://www.w3.org/2004/08/xop/include` |
| xmime |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| Dp |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a>MÝDLO 1.1 a SOAP 1.2

### <a name="envelope-and-processing-model"></a>Obálka a model zpracování
WCF implementuje soap 1.1 obálky zpracování podle základníprofil 1.1 (BP11) a základní profil 1.0 (SSBP10). SOAP 1.2 Zpracování obálek je implementováno po SOAP12-Part1.

Tento oddíl vysvětluje některé volby implementace přijaté WCF, pokud jde o BP11 a SOAP12-Part1.

#### <a name="mandatory-header-processing"></a>Povinné zpracování záhlaví
WCF se řídí pravidly `mustUnderstand` pro zpracování hlaviček označených ve specifikacích SOAP 1.1 a SOAP 1.2 s následujícími variantami.

Zpráva, která vstupuje do zásobníku kanálu WCF, je zpracována jednotlivými kanály nakonfigurovanými přidruženými prvky vazby, například kódováním textových zpráv, zabezpečením, spolehlivým zasíláním zpráv a transakcemi. Každý kanál rozpozná záhlaví z přidruženého oboru názvů a označí je jako srozumitelné. Jakmile zpráva zadá dispečera, operace formatter čte záhlaví očekávané odpovídající zprávy/operace smlouvy a označí je pochopil. Potom dispečer ověří, zda všechny zbývající záhlaví `mustUnderstand` nejsou chápány, ale označeny jako a vyvolá výjimku. Zprávy, `mustUnderstand` které obsahují záhlaví, které jsou zaměřeny na příjemce nejsou zpracovány kód emitované aplikace příjemce.

Takové vrstvené zpracování umožňuje oddělení mezi vrstvami infrastruktury a aplikačními vrstvami uzlu SOAP:

- B1111: Záhlaví, které nejsou pochopeny jsou zjištěny po zpracování zprávy zásobníku kanálu infrastruktury WCF, ale před zpracováním aplikací

     Hodnota `mustUnderstand` záhlaví se liší mezi SOAP 1.1 a SOAP 1.2. Základní profil 1.1 `mustUnderstand` vyžaduje, aby hodnota byla 0 nebo 1 pro zprávy SOAP 1.1. SOAP 1.2 umožňuje 0, `false` `true` 1 , a jako hodnoty, ale doporučuje `xs:boolean` vyzařovat`false` `true`kanonické reprezentace hodnot ( , ).

- B1112: WCF `mustUnderstand` vyzařuje hodnoty 0 a 1 pro soap 1.1 a SOAP 1.2 verze obálky SOAP. WCF přijímá celý hodnotový `xs:boolean` prostor `mustUnderstand` pro záhlaví (0, 1, `false`, `true`)

#### <a name="soap-faults"></a>CHYBY SOAP
Následuje seznam implementací chyb SOAP specifických pro WCF.

- B2121: WCF vrátí následující kódy chyb `s11:mustUnderstand` `s11:Client`SOAP `s11:Server`1.1: , , a .

- B2122: WCF vrátí následující kódy chyb `s12:MustUnderstand` `s12:Sender`SOAP `s12:Receiver`1.2: , , a .

### <a name="http-binding"></a>Vazba HTTP

#### <a name="soap-11-http-binding"></a>SOAP 1.1 HTTP vazba
WCF implementuje VAZBU SOAP1.1 HTTP podle oddílu 3.4 specifikace základního profilu 1.1 s následujícími vyjasněními:

- B2211: Služba WCF neimplementuje přesměrování požadavků HTTP POST.

- B2212: Klienti WCF podporují HTTP Cookies v souladu s 3.4.8.

#### <a name="soap-12-http-binding"></a>SOAP 1.2 HTTP vazba
WCF implementuje SOAP 1.2 HTTP vazbu, jak je popsáno ve specifikaci SOAP 1.2-part 2 (SOAP12Part2) s následujícím vysvětlením.

SOAP 1.2 zavedl volitelný parametr `application/soap+xml` akce pro typ média. Tento parametr je užitečný pro optimalizaci odeslání zprávy bez nutnosti analyzovat text zprávy SOAP při ws adresování není použit.

- R2221: `application/soap+xml` Parametr akce, pokud je k dispozici na požadavku `soapAction` SOAP `wsoap12:operation` 1.2, musí odpovídat atributu na elementu uvnitř odpovídající vazby WSDL.

- R2222: `application/soap+xml` Parametr akce, pokud je k dispozici na `wsa:Action` zprávě SOAP 1.2, musí odpovídat při ws adresování 2004/08 nebo WS adresování 1.0 jsou používány.

Pokud ws adresování je zakázáno a příchozí požadavek `Action` neobsahuje parametr akce, zpráva se považuje za není zadán.

## <a name="ws-addressing"></a>WS-adresování
WCF implementuje 3 verze WS-Addressing:

- WS-Adresování 2004/08

- W3C Web Services Addressing 1.0 Core (ADDR10-CORE) a SOAP Vazba (ADDR10-SOAP)

- WS-Adresování 1.0 - Metadata

### <a name="endpoint-references"></a>Odkazy na koncový bod
Všechny verze WS-Addressing, které implementuje WCF použít odkazy na koncový bod k popisu koncových bodů.

#### <a name="endpoint-references-and-ws-addressing-versions"></a>Odkazy na koncové ho a ws adresování verze
WCF implementuje řadu protokolů infrastruktury, které používají WS-Adresování a zejména `EndpointReference` element a `W3C.WsAddressing.EndpointReferenceType` třídy (například WS-ReliableMessaging, WS-SecureConversation a WS-Trust). WCF podporuje použití obou verzí WS-Addressing s jinými protokoly infrastruktury. Koncové body WCF podporují jednu verzi ws adresování na koncový bod.

Pro R3111 obor názvů `EndpointReference` pro prvek nebo typ používaný ve zprávách vyměňovaných s koncovým bodem WCF musí odpovídat verzi WS adresování implementované tímto koncovým bodem.

Například pokud koncový bod WCF implementuje WS-ReliableMessaging, `AcksTo` záhlaví vrácené takový koncový bod uvnitř `EncodingBinding` `CreateSequenceResponse` používá WS-Addressing verze, která určuje prvek pro tento koncový bod.

#### <a name="endpoint-references-and-metadata"></a>Odkazy na koncové ho a metadata
Řada scénářů vyžaduje komunikaci metadat nebo odkaz na metadata pro daný koncový bod.

B3121: WCF používá mechanismy popsané ve specifikaci WS-MetadataExchange (MEX) Oddíl 6 zahrnout metadata pro odkazy na koncové parametry podle hodnoty nebo odkazem.

Zvažte scénář, kdy služba WCF vyžaduje ověření pomocí tokenu jazyka s výrazy zabezpečení `http://sts.fabrikam123.com`(SAML) vydaného vystavitelem tokenu na adrese . Koncový bod WCF popisuje tento požadavek ověřování `sp:IssuedToken` pomocí `sp:Issuer` kontrolního výrazu s vnořeným kontrolním výrazem odkazujícím na vystavittele tokenu. Klientské aplikace, `sp:Issuer` které přistupují k kontrolnímu výrazu, potřebují vědět, jak komunikovat s koncovým bodem vystavitele tokenu. Klient potřebuje znát metadata o vystaviteli tokenu. Pomocí rozšíření metadat odkazu koncového bodu definované v MEX WCF poskytuje odkaz na metadata vystavitela tokenu.

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
Pro obě verze WS-Addressing wcf používá následující záhlaví zpráv, jak `wsa:To` `wsa:ReplyTo`je `wsa:Action` `wsa:MessageID`předepsáno `wsa:RelatesTo`specifikace , , , , a .

B3211: Pro všechny verze WS adresování WCF vyznamenání, ale nevytváří po vybalení, `wsa:FaultTo` `wsa:From`WS adresování záhlaví zpráv a .

Aplikace, které interagují s aplikacemi WCF můžete přidat tyto hlavičky zpráv a WCF bude zpracovávat odpovídajícím způsobem.

#### <a name="reference-parameters-and-properties"></a>Referenční parametry a vlastnosti

WCF implementuje zpracování referenčních parametrů koncového bodu a referenčních vlastností v souladu s příslušnými specifikacemi.

B3221: Při konfiguraci pro použití WS-Addressing 2004/08 koncové body WCF nerozlišují mezi zpracováním vlastností reference a referenčními parametry.

### <a name="message-exchange-patterns"></a>Vzory výměny zpráv
Posloupnost zpráv zapojených do vyvolání operace webové služby se označuje jako *vzor výměny zpráv*. WCF podporuje jednosměrné, požadavek odpověď a duplexní zprávy exchange vzory. Tato část objasňuje ws adresování požadavky na zpracování zpráv v závislosti na vzoru výměny zpráv se používá.

V této části žadatel odešle první zprávu a respondér obdrží první zprávu.

#### <a name="one-way-message"></a>Jednosměrná zpráva
Když je koncový bod WCF nakonfigurován `Action` tak, aby podporoval zprávy s daným způsobem, který se řídí jednosměrným vzorem, koncový bod WCF následuje následující chování a požadavky. Není-li uvedeno jinak, chování a pravidla platí pro obě verze WS-Adresování podporované v WCF:

- R3311: Žadatel musí `wsa:To`obsahovat , `wsa:Action`a záhlaví pro všechny referenční parametry určené odkazem na koncový bod. Při ws adresování 2004/08 a [reference vlastnosti] jsou určeny odkaz na koncový bod, odpovídající záhlaví musí být přidány do zprávy příliš.

- B3312: Žadatel může `MessageID`obsahovat `ReplyTo` `FaultTo` , a záhlaví. Infrastruktura přijímače je bude ignorovat a budou předány do aplikace.

- R3313: Pokud je použit protokol HTTP a na straně protokolu HTTP není odesílána žádná zpráva, musí respondér odeslat odpověď HTTP s prázdným tělem a stavovým kódem HTTP 202.

     Pokud je přenos HTTP používán a smlouva operace deklaruje zprávu jednosměrně, odpověď HTTP lze stále použít pro `SequenceAcknowledgement` odesílání zpráv infrastruktury – například spolehlivé zasílání zpráv může odeslat zprávu na odpověď HTTP.

- B3314: WCF respondér neodešle zprávu o chybě v reakci na jednosměrnou zprávu.

#### <a name="request-reply"></a>Požadavek a odpověď
Pokud je koncový bod WCF nakonfigurován `Action` pro zprávu s danou tak, aby sledovala vzor požadavku a odpovědi, koncový bod WCF následuje následující chování a požadavky. Není-li uvedeno jinak, chování a pravidla platí pro obě verze WS-Adresování podporované v WCF:

- R3321: Žadatel musí zahrnout do `wsa:To` `wsa:Action`požadavku `wsa:MessageID`, , a hlavičky pro všechny referenční parametry nebo referenční vlastnosti (nebo obojí) určené odkazem na koncový bod.

- R3322: Při ws `ReplyTo` adresování 2004/08 musí být také zahrnuty v požadavku.

- R3323: Při ws adresování 1.0 a `ReplyTo` není k dispozici v požadavku, výchozí odkaz na `http://www.w3.org/2005/08/addressing/anonymous` koncový bod s [adresa] vlastnost rovná se používá.

- R3324: Žadatel musí `wsa:To`obsahovat `wsa:Action` `wsa:RelatesTo` , a záhlaví ve zprávě odpovědi, jakož i záhlaví pro všechny referenční parametry `ReplyTo` nebo referenční vlastnosti (nebo obojí) určené odkazem na koncový bod v požadavku.

### <a name="web-services-addressing-faults"></a>Chyby adresování webových služeb
R3411: WCF vytváří následující chyby definované WS adresování 2004/08.

| kód | Příčina |
|----------|-----------|
| `wsa:DestinationUnreachable` | Zpráva byla doručena s, `ReplyTo` která se liší od odpovědi adresu stanovenou pro tento kanál; neexistuje žádný koncový bod naslouchání na adresu zadanou v hlavičce Do. |
| `wsa:ActionNotSupported` | kanály infrastruktury nebo dispečer přidružený ke koncovému `Action` bodu nerozpoznávají akci zadanou v hlavičce. |

R3412: WCF vytváří následující chyby definované WS adresování 1.0.

| kód | Příčina |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | Duplikát `wsa:To`, `wsa:ReplyTo`nebo `wsa:From` `wsa:MessageID`. `wsa:RelatesTo` Duplikovat `RelationshipType`se stejným . |
| `wsa10:MessageAddressingHeaderRequired` | Chybí požadovaná hlavička adresování. |
| `wsa10:DestinationUnreachable` | Zpráva byla doručena `ReplyTo` s, která se liší od odpovědi adresu vytvořenou pro tento kanál. Neexistuje žádný koncový bod naslouchání na adresu zadanou v hlavičce Do. |
| `wsa10:ActionNotSupported` | Akce zadaná `Action` v hlavičce není rozpoznána kanály infrastruktury nebo dispečerem přidruženým ke koncovému bodu. |
| `wsa10:EndpointUnavailable` | Rm kanál odešle tuto chybu zpět, označující koncový bod nebude `CreateSequence` zpracovávat sekvence na základě kontroly adresování záhlaví zprávy. |

Kód v předchozích tabulkách se mapuje v `FaultCode` SOAP 1.1 a `SubCode` (s Code=Sender) v SOAP 1.2.

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1.1 Tvrzení o vazbě a zásadách WS

#### <a name="indicating-use-of-ws-addressing"></a>Označující použití ws-adresování
WCF používá kontrolní výrazy zásad k označení podpory koncového bodu pro konkrétní verzi WS-Addressing.

Následující tvrzení zásad má předmět zásad koncového bodu [WS-PA] a označuje zprávy odeslané a přijaté z koncového bodu musí používat WS-Addressing 2004/08.

```xml
<wsap:UsingAddressing />
```

Toto tvrzení zásad rozšiřuje ws adresování 2004/08 specifikace.

Následující tvrzení zásad to znamená, že zprávy odeslané nebo přijaté musí používat WS-Addressing 1.0.

```xml
<wsam:Addressing/>
```

Následující tvrzení zásad má předmět zásad koncového bodu [WS-PA] a označuje, že zprávy odeslané a přijaté z koncového bodu musí používat WS-Addressing 2004/08.

```xml
<wsaw10:UsingAddressing />
```

Prvek `wsaw10:UsingAddressing` je vypůjčen z [WS-Addressing-WSDL] a používá se v kontextu WS-Policy v souladu s uvedenou specifikací, oddíl 3.1.2.

Použití adresování nemění sémantiku WSDL 1.1, SOAP 1.1 a SOAP 1.2 HTTP vazby. Například pokud je očekávána odpověď na požadavek, který je odeslán do koncového bodu, který používá adresování a WSDL SOAP 1.x HTTP vazby, odpověď musí být odeslána pomocí odpovědi HTTP.

Pro odpovědi odeslané přes odpověď http, WS-AM kontrolní výraz je:

```xml
<wsam:AnonymousResponses/>
```

Úplné tvrzení zásad může vypadat takto:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Existují však vzory výměny zpráv, které těží z toho, že mezi žadatelem a respondérem jsou vytvořena dvě nezávislá konverzní připojení HTTP, například nevyžádané jednosměrné zprávy odeslané respondérem.

WCF nabízí funkci, kterou dva základní kanály přenosu mohou tvořit složený duplexní kanál, kde jeden kanál se používá pro vstupní zprávy a druhý se používá pro výstupní zprávy. V případě přenosu HTTP composite duplex poskytuje dvě připojení http. Žadatel používá jedno připojení k odesílání zpráv respondérovi a respondér používá druhé k odesílání zpráv zpět žadateli.

Pro odpovědi odeslané přes samostatné požadavky http, ws-am tvrzení je

```xml
<wsam:NonAnonymousResponses/>
```

Úplné tvrzení zásad může vypadat takto:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Použití následující ho výrazu, který má předmět zásad koncového bodu [WS-PA] na koncové body, které používají WSDL 1.1 SOAP 1.x HTTP vazby vyžaduje dvě samostatné konverzní http připojení, které mají být použity pro zprávy přetékající od respondéru k respondéru a respondér na žadateli, resp.

```xml
<cdp:CompositeDuplex/>
```

Předchozí příkaz vede k následujícím `wsa:ReplyTo` požadavkům v záhlaví pro zprávy požadavku:

- R3514: Požadavek zprávy odeslané do `ReplyTo` koncového `[address]` bodu musí `http://www.w3.org/2005/08/addressing/anonymous` mít záhlaví s vlastností není rovno, pokud koncový bod používá WSDL 1.1 SOAP 1.x HTTP vazby a má alternativu zásad s `wsap10:UsingAddressing` nebo `wsap:UsingAddressing` kontrolní výraz spolu s `cdp:CompositeDuplex` připojeným.

- R3515: Požadavek zprávy odeslané do `ReplyTo` koncového `[address]` bodu `http://www.w3.org/2005/08/addressing/anonymous`musí mít záhlaví `ReplyTo` s vlastností rovnou , nebo nemusí mít záhlaví vůbec, pokud koncový bod `wsap10:UsingAddressing` používá WSDL 1.1 SOAP 1.x HTTP vazby a má alternativu zásad s kontrolní výraz a žádný `cdp:CompositeDuplex` kontrolní výraz připojen.

- R3516: Požadavek zprávy odeslané do `ReplyTo` koncového `[address]` bodu `http://www.w3.org/2005/08/addressing/anonymous` musí mít záhlaví s vlastností, která se rovná, pokud koncový bod `wsap:UsingAddressing` používá `cdp:CompositeDuplex` WSDL 1.1 SOAP 1.x HTTP vazby a má alternativu zásad s kontrolní výraz a bez kontrolnívýraz připojen.

WS adresování WSDL specifikace pokusí popsat podobné vazby `<wsaw:Anonymous/>` protokolu zavedením element se třemi textové hodnoty (povinné, `wsa:ReplyTo` volitelné a zakázané) k označení požadavků na záhlaví (oddíl 3.2). Bohužel taková definice prvku není zvláště použitelná jako výraz v kontextu WS-Policy, protože vyžaduje rozšíření specifické pro doménu pro podporu průniku alternativy pomocí takový prvek jako kontrolní výraz. Tato definice prvku také označuje `ReplyTo` hodnotu záhlaví na rozdíl od chování koncového bodu v drátě, což je specifické pro přenos HTTP.

#### <a name="action-definition"></a>Definice akce
WS-Addressing 2004/08 definuje `wsa:Action` atribut `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` pro prvky. WS-Addressing 1.0 WSDL vazba (WS-ADDR10-WSDL) `wsaw10:Action`definuje podobný atribut .

Jediný rozdíl mezi těmito dvěma je výchozí akce vzor sémantiku popsané v části 3.3.2 WS-ADDR a oddíl 4.4.4 WS-ADDR10-WSDL, příslušně.

Je rozumné mít dva koncové body, `portType` které sdílejí stejné (nebo smlouvy, v terminologii WCF), ale pomocí různých verzí WS adresování. Ale vzhledem k tomu, že Action je definován `portType` a `portType`neměla by se měnit mezi koncovými body, které implementují , je nemožné podporovat oba výchozí vzory akcí.

Chcete-li vyřešit tuto kontroverzi, WCF `Action` podporuje jednu verzi atributu.

B3521: WCF `wsaw10:Action` používá `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` atribut na prvky definované v WS-ADDR10-WSDL k určení `Action` IDENTIFIKÁTORU URI pro odpovídající zprávy bez ohledu na ws adresování verze používané koncovým bodem.

#### <a name="use-endpoint-reference-inside-wsdl-port"></a>Použití odkazu koncového bodu uvnitř portu WSDL
WS-ADDR10-WSDL oddíl 4.1 `wsdl:port` rozšiřuje prvek `<wsa10:EndpointReference…/>` zahrnout podřízený prvek k popisu koncového bodu v WS adresování termíny. WCF rozšiřuje tento nástroj na WS-Addressing 2004/08, umožňuje `<wsa:EndpointReference…/>` zobrazit `wsdl:port`jako podřízený prvek .

- R3531: Pokud koncový bod má připojené alternativy zásad s výrazem `<wsaw10:UsingAddressing/>` zásad, odpovídající `wsdl:port` prvek může obsahovat podřízený prvek `<wsa10:EndpointReference …/>`.

- R3532: Pokud `wsdl:port` a obsahuje `<wsa10:EndpointReference …/>`podřízený prvek , `wsa10:EndpointReference/wsa10:Address` podřízená `@address` hodnota prvku `wsdl:port` / `wsdl:location` musí odpovídat hodnotě atributu prvku na stejné úrovni.

- R3533: Pokud koncový bod má připojené `<wsap:UsingAddressing/>` alternativy zásad `wsdl:port` s výrazem zásad, odpovídající prvek může obsahovat podřízený prvek `<wsa:EndpointReference …/>`.

- R3534: Pokud `wsdl:port` a obsahuje `<wsa:EndpointReference …/>` `wsa:EndpointReference/wsa:Address` podřízený prvek , musí hodnota `@address` podřízeného `wsdl:port` prvku odpovídat hodnotě atributu prvku na stejné úrovni. / `wsdl:location`

### <a name="composition-with-ws-security"></a>Složení s WS-Security
Podle části aspektu zabezpečení v WS-ADDR a WS-ADDR10, všechny adresování záhlaví zpráv se doporučuje podepsat společně s textem zprávy svázat je dohromady.

Při ws-security se používá pro ochranu integrity zprávy, WS adresování záhlaví zpráv, stejně jako záhlaví vyplývající z referenční parametry nebo vlastnosti (nebo obojí) musí být podepsány společně s textem zprávy.

### <a name="examples"></a>Příklady

#### <a name="one-way-message"></a>Jednosměrná zpráva
V tomto scénáři odesílatel odešle jednosměrnou zprávu příjemci. SOAP 1.2, HTTP 1.1 a W3C WS-Addressing 1.0 se používají.

Struktura požadavku na zprávu: Záhlaví `wsa10:To` `wsa10:Action` zpráv obsahují a prvky. Text zprávy obsahuje `<app:Ping>` určitý prvek z oboru názvů aplikace.

Hlavičky HTTP: Cíl v post odpovídá `wsa10:To` URI v prvku.

Hlavička typu obsahu má `application/soap+xml` hodnotu požadovanou soap 1.2. Parametry `charset` `action` a jsou zahrnuty. Parametr `action` hlavičky Typu obsahu odpovídá hodnotě `wsa10:Action` záhlaví zprávy.

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

Příjemce odpoví prázdnou odpovědí HTTP a stavem 202. Příklad odpovědi HTTP:

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

## <a name="soap-message-transmission-optimization-mechanism"></a>Mechanismus optimalizace přenosu zpráv SOAP
Tato část popisuje podrobnosti implementace WCF pro mtom PROTOKOLU HTTP SOAP. Technologie MTOM je mechanismus kódování zpráv SOAP stejné třídy jako tradiční kódování textu/XML nebo binární kódování WCF. MTOM zahrnuje následující:

- Mechanismus kódování a balení XML popsaný [XOP], který optimalizuje informační položky XML obsahující binární data kódovaná základnou 64 do samostatných binárních částí.

- Zapouzdření balíčku XOP MIME, které serializuje XML Infoset a každou binární část balíčku XOP do samostatné části MIME.

- Kódování MIME XOP aplikované na obálku SOAP 1.x.

- Přenosová vazba HTTP.

Je možné použít MTOM s non-HTTP přenosy s WCF. V tomto tématu se však zaměříme na HTTP.

Formát MTOM využívá velkou sadu specifikací pokrývajících samotné MTOM, XOP a MIME. Modularita této sady specifikací ztěžuje rekonstrukci přesných požadavků na formát a sémantiku zpracování. Tato část popisuje požadavky na formát a zpracování vazby Protokolu HTTP mtom.

### <a name="mtom-message-encoding"></a>Kódování zpráv MTOM

#### <a name="generating-mtom-messages"></a>Generování zpráv MTOM
Oddíl [XOP] 3.1 popisuje proces kódování XML s položkami informací o elementech, které obsahují hodnoty base64 do abstraktně definovaného balíčku XOP.

Následující posloupnost kroků popisuje proces kódování specifické pro MTOM:

1. Ujistěte se, že obálka SOAP, která má `[namespace name]` `http://www.w3.org/2004/08/xop/include` být `[local name]` zakódována, neobsahuje žádnou položku informací o prvku s a a a `Include`.

2. Vytvořte prázdný balíček MIME.

3. Identifikujte v rámci původní informační sady XML položky informací o elementech, které mají být optimalizovány. Pro položky, které mají být optimalizovány, musí být znaky, které tvoří `[children]` `xs:base64Binary` položku informací o prvku, v kanonické podobě (viz XSD-2, 3.2.16 base64Binary) a nesmí obsahovat žádné prázdné znaky předcházející, vřádící s obsahem neprázdné mezery nebo za ním.

4. Vytvořte obálku XOP SOAP, která je kopií původní obálky SOAP, ale s podřízenými `xop:Include` položkami informací o každém prvku identifikovanými v předchozím kroku nahrazeny položkou informací o prvku, která je vytvořena takto:

    1. Transformujte nahrazené znaky na binární data jejich zpracováním jako data kódovaná base64.

    2. Vygenerujte jedinečnou hodnotu záhlaví Content-ID, která splňuje požadavky R3133 a R3134.

    3. Vygenerujte hlavičku MIME s hodnotou binární.

    4. Pokud položka informací o prvku, která je optimalizována `xop:Include` ([nadřazená] položky informací o nově vloženém prvku), obsahuje položku informace o atributu, `xmime:contentType` vygenerujte hlavičku MIME typu obsahu s hodnotou atributu. `xmime:contentType`

    5. Generovat nový binární MIME část s obsahem tvořenbinární data dekódována z nahrazených znaků zpracovaných jako base64, Content-ID záhlaví z 4b, Obsah-Transfer-Kódování záhlaví z 4c, Content-Type záhlaví, pokud jsou generovány v kroku 4d.

    6. Přidejte `href` atribut `xop:Include` k prvku s hodnotou cid: uri odvozené z hodnoty hlavičky Content-ID generované v kroku 4b. Odeberte ohraničující znaky "\<" a ">", uniknete zbývajícímu řetězci adresou URL a přidejte předponu `cid:`. Následující minimální znaková sada je nutné uvozena RFC1738 a RFC2396. Ostatní znaky mohou být uvozeny.

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. Vytvořte kořenový díl MIME s obálkou XOP SOAP z kroku 4.

6. Napište záhlaví protokolu HTTP, včetně hlavičky typu obsahu HTTP.

7. Napište balíček MIME.

#### <a name="processing-mtom-messages"></a>Zpracování zpráv MTOM
Zpracování zprávy MTOM je přesný opak procesu popsaného v předchozí části Generování zpráv MTOM:

1. Ujistěte se, že kořenová `application/xop+xml`část MIME má typ obsahu .

2. Vytvořte obálku SOAP analýzou kořenové části MIME balíčku jako dokumentu XML. Kódování znaků je určeno `charset` parametrem typu Content-Type kořenové části MIME.

3. Pro každou položku informací o prvku v konstruované soap envelope, která má `xop:Include` jako jediný člen své vlastnosti [children] položku s informacemi o prvku:

    1. Odeberte `cid:` předponu a unescape všechny sekvence uri-escape (RFC 2396) v hodnotě `@href` atribut u `xop:Include` prvku. Výsledek uzavřete do\<" ", ">".

    2. Vyhledejte část MIME s hodnotou záhlaví Content-ID, která odpovídá řetězci odvozenému v kroku 3a.

    3. Nahraďte položku `xop:Include` informací `children` o elementu, která se zobrazí ve vlastnosti každé položky, položkami informací o znaku, které představují kódování canonical base64 (viz XSD-2, `xop:Include` 3.2.16 base64Binary) těla entity části MIME identifikované v kroku 3b (účinně nahradit položku informací o prvku daty rekonstruovanými z dílu balíčku).

#### <a name="http-content-type-header"></a>Hlavička typu obsahu HTTP
Následuje seznam wcf vysvětlení pro formát hlavičky typu obsahu HTTP soap 1.x MTOM kódované zprávy odvozené z požadavků uvedených ve specifikaci MTOM sám a jsou odvozeny z MTOM a RFC 2387.

- R4131: Hlavička typu obsahu HTTP musí mít hodnotu multipart/related (bez rozlišování velkých a malých písmen) a její parametry. Názvy parametrů nerozlišují malá a velká písmena. Pořadí parametrů není významné.

- Úplný formulář Backus-Naur (BNF) záhlaví typu obsahu pro zprávy MIME je uveden v oddíle 5.1 rfc 2045.

- R4132: Hlavička typu obsahu HTTP musí mít `application/xop+xml` parametr typu s hodnotou uzavřenou v uvozovkách.

Zatímco požadavek na použití dvojitých uvozovek není v rfc 2387 explicitní, text pozoruje, že všechny\@parametry typu multipart/related média s největší pravděpodobností obsahují vyhrazené znaky jako " " nebo "/", a proto potřebují dvojité uvozovky.

- R4133: Hlavička typu obsahu HTTP by měla mít počáteční parametr s hodnotou hlavičky Content-ID části MIME, která obsahuje obálku SOAP 1.x, uzavřenou v uvozovkách. Pokud je parametr start vynechán, první část MIME musí obsahovat obálku SOAP 1.x.

- R4134: Hlavička typu obsahu HTTP pro zprávu kódovku SOAP 1.1 MTOM musí obsahovat parametr start-info s hodnotou text/xml, která je uzavřena v uvozovkách.

- R4135: Hlavička typu obsahu HTTP pro zprávu kódovku SOAP 1.2 MTOM musí `application/soap+xml`obsahovat parametr start-info s hodnotou , uzavřenou v uvozovkách.

- R4136: Hlavička typu obsahu HTTP pro zprávu kódovku SOAP 1.x MTOM musí mít parametr hranice s hodnotou (uzavřenou v uvozovkách), která odpovídá hranici MIME BNF definované v RFC 2046, oddíl 5.1.1

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     Příklady:

     Správné

    ```
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     Správné

    ```
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     Nesprávné

    ```
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a>Infoset MIME část
Obálka SOAP 1.x je zapouzdřena jako kořenová část balíčku `infoset` XOP MIME a často se nazývá součást.

- R4141: Obálka SOAP 1.x musí být zapouzdřena jako kořenová `infoset` část balíčku XOP MIME, nazývaná součást a odkazovaná z typu obsahu HTTP.

- R4142: Část `Infoset` SOAP musí obsahovat následující `Content-ID`hlavičky MIME: , `Content-Transfer-Encoding`, a `Content-Type`.

Formát hlavičky Content-ID je definován rfc 2045 jako

```
"Content-ID" ":" msg-id
```

kde `msg-id` je definována v RFC 2822 (která nahrazuje RFC 822, uvedeno v RFC 2045) jako:

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

a je fakticky e-mailovou\<adresou uzavřenou v " " a ">". Předpona `[CFWS]` a přípona byly přidány v RFC 2822 nést komentáře a by neměly být použity k zachování interoperability.

R4143: Hodnota hlavičky Content-ID pro část MIME `msg-id` infosady musí následovat výroba z `[CFWS]` RFC 2822 s vynechánou předponou a příponou.

Řada implementací MIME uvolnila požadavky na hodnotu uzavřenou v "\<" a `absoluteURI` ">"\<jako e-mailovou adresu a použitou v " " , ">" kromě e-mailové adresy. Tato verze WCF používá hodnoty hlavičky MIME content id formuláře:

```
Content-ID: <http://tempuri.org/0>
```

R4144: Procesory MTOM by měly přijímat hodnoty záhlaví `msg-id`Content-ID, které odpovídají následujícímu uvolněnému .

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

MIME (RFC 2045) poskytuje hlavičku Content-Transfer-Encoding pro komunikaci kódování obsahu části MIME. Výchozí definice pro kódování content-transfer-encoding je 7bitová, což není vhodné pro většinu zpráv SOAP, takže hlavička content-transfer-encoding je potřebná pro větší interoperabilitu:

- R4145: Část SOAP Infoset musí obsahovat hlavičku content-transfer-encoding.

- R4146: Pokud je kódování znaku SOAP Envelope UTF-8, hodnota hlavičky Content-Transfer-Encoding musí být 8bitová.

- R4147: Pokud je kódování znaku SOAP Obálka UTF-16, hodnota hlavičky content-transfer-encoding musí být binární.

- Podle [XOP] oddílu 5,

- R4148: Část SOAP1.1 Infoset musí obsahovat hlavičku typu content-type s typem média application/xop+xml a parametry type="text/xml" a znakovou sadou.

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- R4149: Část SOAP 1.2 Infoset musí obsahovat hlavičku Typu obsahu s typem `application/xop+xml` média a parametry type="`application/soap+xml`" a `charset`.

    ```
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     Zatímco XOP definuje `charset` parametr `application/xop+xml` pro volitelné, je potřeba pro interoperabilitu podobnou požadavku BP 1.1 na `charset` parametr pro typ `text/xml` média.

- R41410: `type` Parametry a `charset` musí být k dispozici v záhlaví typu obsahu části SOAP 1.x Infoset.

#### <a name="wcf-endpoint-support-for-mtom"></a>Podpora koncového bodu WCF pro MTOM
Účelem MTOM je zakódovat zprávu SOAP pro optimalizaci dat kódovaných base64. Následuje seznam omezení:

- R4151: Všechny položky informací o prvku, který obsahuje data kódovaná base64, mohou být optimalizovány.

- B4152: WCF optimalizuje položky informací o elementech, které obsahují data kódovaná base64 a přesahují délku 1024 bajtů.

Koncový bod WCF nakonfigurovaný pro použití mtom bude vždy odesílat zprávy kódované mtom. I v případě, že žádné části splňují požadovaná kritéria, zpráva je stále kódována MTOM (serializována jako balíček MIME s jedním dílem MIME obsahujícím obálku SOAP).

### <a name="ws-policy-assertion-for-mtom"></a>WS-Policy Assertion pro MTOM
WCF používá následující kontrolní výraz zásad k označení využití mtom podle koncového bodu:

```xml
<wsoma:OptimizedMimeSerialization />
```

- R4211: Předchozí výraz zásad má předmět zásad koncového bodu a určuje, že všechny zprávy odeslané a přijaté z koncového bodu musí být optimalizovány pomocí MTOM.

- B4212: Při konfiguraci pro použití optimalizace MTOM přidá koncový bod WCF kontrolní `wsdl:binding`výraz zásad mtom k zásadám připojeným k odpovídající .

### <a name="composition-with-ws-security"></a>Složení s WS-Security
MTOM je mechanismus kódování, `text/xml` který je podobný wcf binární XML. MTOM nabízí přirozené složení s WS-Security a dalšíws-* protokoly: zpráva zabezpečená pomocí WS-Security lze optimalizovat pomocí MTOM.

### <a name="examples"></a>Příklady

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>WCF SOAP 1.1 Zpráva kódovaná pomocí mtoma

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

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>WCF Secure SOAP 1.2 Zpráva kódovaná pomocí MTOM
V tomto příkladu je zpráva kódována pomocí mtom a SOAP 1.2, která je chráněna pomocí ws-security. Binární části identifikované pro kódování jsou `BinarySecurityToken` `CipherValue` obsah `EncryptedData` , odpovídající šifrovanému podpisu a šifrovanému tělu. Všimněte `CipherValue` si, `EncryptedKey` že of nebyl identifikován pro optimalizaci WCF, protože jeho délka je menší než 1024 bajtů.

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
