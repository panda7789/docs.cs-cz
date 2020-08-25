---
title: Protokoly zasílání zpráv
ms.date: 03/30/2017
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
ms.openlocfilehash: 69a92bfb406e2e1af3bdcbb0316711dbf531204b
ms.sourcegitcommit: 9c45035b781caebc63ec8ecf912dc83fb6723b1f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/25/2020
ms.locfileid: "88812052"
---
# <a name="messaging-protocols"></a>Protokoly zasílání zpráv

Zásobník kanálů Windows Communication Foundation (WCF) využívá kódování a přenosové kanály k transformaci interní reprezentace zpráv do jejího formátu a jejich odeslání pomocí konkrétního přenosu. Nejběžnější přenos používaný pro interoperabilitu webových služeb je HTTP a nejběžnější kódování používané webovými službami jsou založené na jazyce XML SOAP 1,1, SOAP 1,2 a mechanizmus pro optimalizaci přenosu zpráv (MTOM).

Toto téma popisuje podrobnosti implementace WCF pro následující protokoly zaměstnané nástrojem <xref:System.ServiceModel.Channels.HttpTransportBindingElement> .

Specifikace/dokument:

- [HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)
- [Vazba SOAP 1,1 http](https://www.w3.org/TR/2000/NOTE-SOAP-20000508), část 7
- [Vazba SOAP 1,2 http](https://www.w3.org/TR/soap12-part2) Oddíl 7

Toto téma popisuje podrobnosti implementace WCF pro následující protokoly, které <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> využívají.

Specifikace/dokument:

- [XML](https://www.w3.org/TR/REC-xml)
- [PROTOKOL SOAP 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)
- [Jádro protokolu SOAP 1,2](https://www.w3.org/TR/soap12-part1/)
- [WS-Addressing 2004/08](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)
- [Webové služby W3C Addressing 1,0 – jádro](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509)
- [Webové služby W3C Addressing 1,0 – vazba SOAP](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509)
- [Webové služby W3C Addressing 1,0 – Vazba WSDL](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)
- [Webové služby W3C Addressing 1,0 – metadata](https://www.w3.org/TR/ws-addr-metadata/)
- [Vazba WSDL SOAP 1.1](https://www.w3.org/TR/wsdl/)
- [Vazba WSDL SOAP 1.2](https://www.w3.org/Submission/wsdl11soap12/)

Toto téma popisuje podrobnosti implementace WCF pro následující protokoly, které se <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> používají.

Specifikace/dokument:

- [XOP](https://www.w3.org/TR/xop10/)
- [Vazba MTOM + SOAP 1,2](https://www.w3.org/TR/soap12-mtom/)
- [Vazba MTOM SOAP 1,1](https://www.w3.org/Submission/soap11mtom10/)
- [MTOM WS-Policy – kontrolní výraz](https://www.w3.org/Submission/2006/SUBM-WS-MTOMPolicy-20061101/)

V rámci tohoto tématu se používají následující obory názvů XML a přidružené předpony:

| Předpona | Obor názvů identifikátoru URI (Uniform Resource Identifier) |
|------------|---------------------------------------------------|
| s11 | `http://schemas.xmlsoap.org/soap/envelope` |
| S12 |`http://www.w3.org/2003/05/soap-envelope` |
| WSA |`http://www.w3.org/2004/08/addressing` |
| wsam |`http://www.w3.org/2007/05/addressing/metadata` |
| wsap |`http://schemas.xmlsoap.org/ws/2004/09/policy/addressing` |
| wsa10 |`http://www.w3.org/2005/08/addressing` |
| wsaw10 |`http://www.w3.org/2006/05/addressing/wsdl` |
| XOP |`http://www.w3.org/2004/08/xop/include` |
| xmime |`http://www.w3.org/2004/06/xmlmime`<br /><br /> `http://www.w3.org/2005/05/xmlmime` |
| DP |`http://schemas.microsoft.com/net/2006/06/duplex` |

## <a name="soap-11-and-soap-12"></a>SOAP 1,1 a SOAP 1,2

### <a name="envelope-and-processing-model"></a>Model obálky a zpracování
WCF implementuje zpracování obálek SOAP 1,1 následující po základním profilu 1,1 (BP11) a Basic Profile 1,0 (SSBP10). Zpracování obálek SOAP 1,2 se implementuje po SOAP12-part1.

V této části jsou vysvětleny určité možnosti implementace, které služba WCF provedla v souvislosti s BP11 a SOAP12-part1.

#### <a name="mandatory-header-processing"></a>Povinné zpracování hlaviček
WCF sleduje pravidla pro zpracování hlaviček označená `mustUnderstand` ve specifikacích protokolu soap 1,1 a soap 1,2 s následujícími variantami.

Zpráva, která vstupuje do zásobníku kanálu WCF, je zpracována jednotlivými kanály nakonfigurovanými pomocí přidružených prvků vazby, například kódování textových zpráv, zabezpečení, spolehlivého zasílání zpráv a transakcí. Každý kanál rozpoznává záhlaví z přidruženého oboru názvů a označí je jako srozumitelnější. Jakmile zpráva vstoupí do dispečera, formátovací modul operace čte hlavičky očekávané odpovídající kontraktem zprávy/operace a označuje jejich pochopení. Potom dispečer ověří, zda nejsou žádné zbývající hlavičky srozumitelné, ale označeny jako `mustUnderstand` a vyvolá výjimku. Zprávy, které obsahují `mustUnderstand` hlavičky cílené na příjemce, nejsou zpracovávány kódem aplikace příjemce.

Takové vrstvené zpracování umožňuje oddělení vrstev infrastruktury a aplikačních vrstev uzlu SOAP:

- B1111: po zpracování zprávy zásobníkem kanálu infrastruktury WCF jsou zjištěny nesrozumitelné hlavičky, ale ještě před tím, než je zpracuje aplikace

     `mustUnderstand`Hodnota hlavičky se liší mezi SOAP 1,1 a soap 1,2. Základní profil 1,1 vyžaduje, aby byla `mustUnderstand` hodnota 0 nebo 1 pro zprávy SOAP 1,1. Protokol SOAP 1,2 povoluje hodnoty 0, 1, `false` a `true` jako hodnoty, ale doporučuje vysílat kanonické vyjádření `xs:boolean` hodnot ( `false` , `true` ).

- B1112: WCF generuje `mustUnderstand` hodnoty 0 a 1 pro verze soap 1,1 a soap 1,2 obálky protokolu SOAP. WCF akceptuje celý prostor hodnoty `xs:boolean` pro `mustUnderstand` záhlaví (0, 1, `false` , `true` ).

#### <a name="soap-faults"></a>Chyby protokolu SOAP
Následuje seznam implementací selhání protokolu SOAP specifických pro WCF.

- B2121: WCF vrátí následující kódy chyb SOAP 1,1: `s11:mustUnderstand` , `s11:Client` a `s11:Server` .

- B2122: WCF vrátí následující kódy chyb SOAP 1,2: `s12:MustUnderstand` , `s12:Sender` a `s12:Receiver` .

### <a name="http-binding"></a>Vazba HTTP

#### <a name="soap-11-http-binding"></a>Vazba SOAP 1,1 HTTP
WCF implementuje vazbu protokolu HTTP protokolu SOAP 1.1 podle specifikace Basic Profile 1,1, část 3,4 s následujícími objasněmi:

- B2211: Služba WCF neimplementuje přesměrování požadavků HTTP POST.

- B2212: Klienti WCF podporují soubory cookie HTTP v souladu s 3.4.8.

#### <a name="soap-12-http-binding"></a>Vazba SOAP 1,2 HTTP
WCF implementuje vazbu HTTP protokolu SOAP 1,2, jak je popsáno ve specifikaci SOAP 1,2-Part 2 (SOAP12Part2), s následujícími objasněmi.

Protokol SOAP 1,2 představil pro typ média volitelný parametr Action `application/soap+xml` . Tento parametr je vhodný k optimalizaci odesílání zpráv, aniž by bylo nutné, aby tělo zprávy SOAP bylo analyzováno, pokud není použito WS-Addressing.

- R2221: `application/soap+xml` parametr Action, pokud je přítomen v žádosti SOAP 1,2, musí odpovídat `soapAction` atributu v `wsoap12:operation` elementu uvnitř odpovídající vazby WSDL.

- R2222: `application/soap+xml` parametr Action, pokud je přítomen ve zprávě SOAP 1,2, se musí shodovat, `wsa:Action` když se používají WS-addressing 2004/08 nebo WS-addressing 1,0.

Pokud je protokol WS-Addressing zakázán a příchozí požadavek neobsahuje parametr Action, zpráva `Action` se považuje za nespecifikovanou.

## <a name="ws-addressing"></a>WS-Addressing
WCF implementuje 3 verze elementu WS-Addressing:

- WS-Addressing 2004/08

- Webové služby W3C Addressing 1,0 Core (ADDR10-CORE) a SOAP Binding (ADDR10-SOAP)

- WS-Addressing 1,0 – metadata

### <a name="endpoint-references"></a>Odkazy na koncový bod
Všechny verze elementu WS-Addressing, které služba WCF implementuje k popisu koncových bodů pomocí odkazů na koncový bod.

#### <a name="endpoint-references-and-ws-addressing-versions"></a>Odkazy na koncové body a verze WS-Addressing
Služba WCF implementuje řadu protokolů infrastruktury, které používají WS-Addressing, a zejména `EndpointReference` element a `W3C.WsAddressing.EndpointReferenceType` třídu (například WS-RELIABLEMESSAGING, WS-SECURECONVERSATION a WS-Trust). Služba WCF podporuje použití libovolné verze elementu WS-Addressing s dalšími protokoly infrastruktury. Koncové body WCF podporují jednu verzi elementu WS-Addressing na jeden koncový bod.

V případě R3111 musí obor názvů pro `EndpointReference` element nebo typ použitý ve zprávách vyměňovaných s koncovým bodem WCF odpovídat verzi elementu WS-Addressing implementovaného tímto koncovým bodem.

Například pokud koncový bod WCF implementuje WS-ReliableMessaging, `AcksTo` Hlavička vrácená tímto koncovým bodem v rámci `CreateSequenceResponse` používá verzi WS-Addressing, kterou `EncodingBinding` prvek určuje pro tento koncový bod.

#### <a name="endpoint-references-and-metadata"></a>Odkazy a metadata koncového bodu
Řada scénářů vyžaduje komunikaci metadat nebo odkaz na metadata pro daný koncový bod.

B3121: WCF využívá mechanismy popsané v části specifikace WS-MetadataExchange (MEX) 6, aby zahrnovaly metadata odkazů na koncový bod podle hodnoty nebo odkazu.

Vezměte v úvahu scénář, ve kterém služba WCF vyžaduje ověření pomocí tokenu SAML (Security Assert Markup Language) vydaného vystavitelem tokenu na adrese `http://sts.fabrikam123.com` . Koncový bod WCF popisuje tento požadavek na ověření pomocí `sp:IssuedToken` kontrolního výrazu s vnořeným `sp:Issuer` kontrolním výrazem ukazujícím na vystavitele tokenu. Klientské aplikace, které přistupují k `sp:Issuer` kontrolnímu výrazu, musí znát, jak komunikovat s koncovým bodem vystavitele tokenu. Klient potřebuje znát metadata vystavitele tokenu. Pomocí rozšíření metadat odkazů na koncový bod definovaný v MEX poskytuje WCF odkaz na metadata vystavitele tokenu.

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

### <a name="message-addressing-headers"></a>Hlavičky adresování zpráv

#### <a name="message-headers"></a>Záhlaví zpráv
Pro verze WS-Addressing používá WCF následující záhlaví zpráv, jak jsou předepsány specifikacemi `wsa:To` , `wsa:ReplyTo` , `wsa:Action` , `wsa:MessageID` a `wsa:RelatesTo` .

B3211: pro všechny verze WS-Addressing se služba WCF dodrží, ale neposkytuje žádné z polí, záhlaví zpráv WS-Addressing `wsa:FaultTo` a `wsa:From` .

Aplikace, které komunikují s aplikacemi WCF, můžou přidat tato záhlaví zpráv a WCF je zpracovat odpovídajícím způsobem.

#### <a name="reference-parameters-and-properties"></a>Referenční parametry a vlastnosti

WCF implementuje zpracování parametrů odkazu na koncový bod a referenční vlastnosti v souladu s příslušnými specifikacemi.

B3221: Pokud je nakonfigurovaná pro použití WS-Addressing 2004/08, koncové body WCF nerozlišují mezi vlastnostmi odkazu na zpracování a referenčními parametry.

### <a name="message-exchange-patterns"></a>Vzorce výměny zpráv
Posloupnost zpráv zapojených do vyvolání operace webové služby se nazývá *vzor výměny zpráv*. WCF podporuje jednosměrné, požadavek-odpověď a duplexní vzory výměny zpráv. Tato část vysvětluje požadavky WS-Addressing při zpracování zpráv v závislosti na použitém vzoru výměny zpráv.

V celé této části žadatel pošle první zprávu a příjemce obdrží první zprávu.

#### <a name="one-way-message"></a>Jednosměrná zpráva
Když je koncový bod WCF nakonfigurovaný tak, aby podporoval zprávy s daným předaným `Action` způsobem, koncový bod WCF sleduje následující chování a požadavky. Pokud není uvedeno jinak, chování a pravidla se vztahují na obě verze elementu WS-Addressing podporovaných ve službě WCF:

- R3311: Žadatel musí zahrnout `wsa:To` `wsa:Action` hlavičky, a pro všechny referenční parametry určené odkazem na koncový bod. Při použití specifikace WS-Addressing 2004/08 a [Reference Properties] jsou určeny odkazem koncového bodu, musí být také do zprávy přidány odpovídající hlavičky.

- B3312: Žadatel může zahrnovat `MessageID` `ReplyTo` hlavičky, a `FaultTo` . Infrastruktura přijímače je ignoruje a předává se do aplikace.

- R3313: Pokud je použit protokol HTTP a v nožkě odpovědi HTTP není odeslána žádná zpráva, musí respondér odeslat odpověď HTTP s prázdným textem a stavovým kódem HTTP 202.

     Je-li použit přenos HTTP a kontrakt operace deklaruje zprávu jednosměrná, může být odpověď HTTP stále používána k posílání zpráv infrastruktury, například spolehlivé zasílání zpráv může odesílat `SequenceAcknowledgement` zprávy na odpovědi HTTP.

- B3314: respondér WCF neodesílá zprávu o chybě jako odpověď na jednosměrnou zprávu.

#### <a name="request-reply"></a>Požadavek a odpověď
Pokud je pro zprávu s daným koncovým bodem WCF nakonfigurované pravidlo `Action` , které se řídí vzorem požadavek-odpověď, pak koncový bod WCF sleduje chování a požadavky níže. Pokud není uvedeno jinak, chování a pravidla se vztahují na obě verze elementu WS-Addressing podporovaných ve službě WCF:

- R3321: Žadatel musí zahrnout do hlaviček Request,, `wsa:To` `wsa:Action` `wsa:MessageID` a pro všechny referenční parametry nebo vlastnosti odkazu (nebo obojí) určené odkazem na koncový bod.

- R3322: při použití elementu WS-Addressing 2004/08 `ReplyTo` musí být do žádosti zahrnut i.

- R3323: Pokud se používá specifikace WS-Addressing 1,0 a `ReplyTo` v žádosti chybí, použije se výchozí odkaz na koncový bod s vlastností [address], která se rovná `http://www.w3.org/2005/08/addressing/anonymous` .

- R3324: Žadatel musí ve `wsa:To` `wsa:Action` `wsa:RelatesTo` zprávě odpovědi zahrnovat hlavičky, a i hlavičky všech referenčních parametrů nebo referenčních vlastností (nebo obou) určených `ReplyTo` odkazem koncového bodu v žádosti.

### <a name="web-services-addressing-faults"></a>Chyby adresování webových služeb
R3411: WCF generuje následující chyby definované pomocí elementu WS-Addressing 2004/08.

| Kód | Příčina |
|----------|-----------|
| `wsa:DestinationUnreachable` | Zpráva dorazila se systémem `ReplyTo` , který se liší od adresy pro odpověď vytvořené pro tento kanál. na adrese zadané v hlavičce komu není žádný koncový bod naslouchá. |
| `wsa:ActionNotSupported` | kanály infrastruktury nebo dispečera přidružené ke koncovému bodu nerozpoznají akci určenou v `Action` hlavičce. |

R3412: WCF generuje následující chyby definované pomocí elementu WS-Addressing 1,0.

| Kód | Příčina |
|----------|-----------|
| `wsa10:InvalidAddressingHeader` | Duplicitní `wsa:To` , `wsa:ReplyTo` , `wsa:From` nebo `wsa:MessageID` . Duplikovat `wsa:RelatesTo` se stejným `RelationshipType` . |
| `wsa10:MessageAddressingHeaderRequired` | Chybí požadované záhlaví adresování. |
| `wsa10:DestinationUnreachable` | Zpráva dorazila se systémem `ReplyTo` , který se liší od adresy pro odpověď vytvořené pro tento kanál. Na adrese určené v hlavičce to nenaslouchá žádný koncový bod. |
| `wsa10:ActionNotSupported` | Akce zadaná v hlavičce není `Action` rozpoznaná pro kanály infrastruktury ani dispečera přidružené ke koncovému bodu. |
| `wsa10:EndpointUnavailable` | Kanál RM pošle tuto chybu zpátky, což znamená, že koncový bod nezpracuje sekvenci na základě zkoumání `CreateSequence` hlaviček adresování zprávy. |

Kód v předchozích tabulkách je mapován na `FaultCode` v protokolu soap 1,1 a `SubCode` (s kódem = odesilatele) v protokolu SOAP 1,2.

### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>Vazba WSDL 1,1 a kontrolní výrazy WS-Policy

#### <a name="indicating-use-of-ws-addressing"></a>Označení použití elementu WS-Addressing
WCF používá kontrolní výrazy zásad k označení podpory koncového bodu pro konkrétní verzi WS-Addressing.

Následující kontrolní výraz zásad má předmět zásad koncového bodu [WS-PA] a indikuje, že zprávy odeslané a přijímané z koncového bodu musí používat WS-Addressing 2004/08.

```xml
<wsap:UsingAddressing />
```

Tento kontrolní výraz zásady rozšiřuje specifikaci WS-Addressing 2004/08.

Následující kontrolní výraz zásad znamená, že zprávy odeslané/přijaté musí používat WS-Addressing 1,0.

```xml
<wsam:Addressing/>
```

Následující kontrolní výraz zásad má předmět zásad koncového bodu [WS-PA] a označuje, že zprávy odesílané a přijímané z koncového bodu musí používat WS-Addressing 2004/08.

```xml
<wsaw10:UsingAddressing />
```

`wsaw10:UsingAddressing`Element je vypůjčený z [WS-Addressing-WSDL] a používá se v kontextu WS-Policy, která je v souladu s touto specifikací, část 3.1.2.

Použití adresování nemění sémantiku vazeb protokolu HTTP v rámci WSDL 1,1, SOAP 1,1 a SOAP 1,2. Pokud se například očekává odpověď na požadavek, který je odeslán do koncového bodu, který používá adresování a vazby HTTP SOAP 1. x, je nutné odpověď odeslat pomocí odpovědi HTTP.

Pro odpovědi odeslané přes odpověď protokolu HTTP je kontrolní výraz WS-AM:

```xml
<wsam:AnonymousResponses/>
```

Výraz úplných zásad by mohl vypadat takto:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:AnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Existují však vzory výměny zpráv, které mají výhodu ze dvou nezávislých připojení k odeslání HTTP mezi žadatelem a respondérem, například nevyžádanými jednosměrné zprávy odesílané respondérem.

Služba WCF nabízí funkci, kterou dva podkladové transportní kanály můžou tvořit složený duplexní kanál, ve kterém se pro vstupní zprávy používá jeden kanál a druhý se používá pro výstupní zprávy. V případě přenosu protokolu HTTP poskytuje složené duplexní spojení dvě konverzace HTTP. Žadatel používá jedno připojení k posílání zpráv na respondér a partner používá druhý k posílání zpráv zpět žadateli.

Pro odpovědi odeslané přes samostatné požadavky HTTP je kontrolní výraz WS-am

```xml
<wsam:NonAnonymousResponses/>
```

Výraz úplných zásad by mohl vypadat takto:

```xml
<wsam:Addressing>
    <wsp:Policy>
        <wsam:NonAnonymousResponses />
    </wsp:Policy>
</wsam:Addressing>
```

Použijte následující kontrolní výraz, který má předmět zásad koncového bodu [WS-PA] u koncových bodů používajících vazby WSDL 1,1 protokolu SOAP 1. x vyžaduje, aby se pro zprávy, které jsou v žadateli a respondérem na žadatele, použila dvě samostatná připojení HTTP, v uvedeném pořadí.

```xml
<cdp:CompositeDuplex/>
```

Předchozí příkaz vede na následující požadavky v `wsa:ReplyTo` hlavičce pro zprávy s požadavky:

- R3514: zprávy požadavku odeslané do koncového bodu musí mít `ReplyTo` záhlaví s `[address]` vlastností, které se nerovná, `http://www.w3.org/2005/08/addressing/anonymous` Pokud koncový bod používá vazbu http WSDL 1,1 SOAP 1. x a má alternativu k zásadě `wsap10:UsingAddressing` s `wsap:UsingAddressing` kontrolním výrazem nebo `cdp:CompositeDuplex` připojeným k němu.

- R3515: zprávy požadavku odeslané do koncového bodu musí mít `ReplyTo` záhlaví s `[address]` vlastností Equal `http://www.w3.org/2005/08/addressing/anonymous` nebo nesmí mít vůbec `ReplyTo` hlavičku, pokud koncový bod používá vazbu http WSDL 1,1 SOAP 1. x a má alternativu zásady s `wsap10:UsingAddressing` kontrolním výrazem a není `cdp:CompositeDuplex` připojen žádný kontrolní výraz.

- R3516: zprávy požadavku odeslané do koncového bodu musí mít `ReplyTo` hlavičku s `[address]` vlastností rovnou, `http://www.w3.org/2005/08/addressing/anonymous` Pokud koncový bod používá vazbu http WSDL 1,1 SOAP 1. x a má alternativu k zásadě s `wsap:UsingAddressing` kontrolním výrazem a není `cdp:CompositeDuplex` připojen žádný kontrolní výraz.

Specifikace WSDL WS-Addressing se pokusí popsat podobné vazby protokolu tím, že zavádí element `<wsaw:Anonymous/>` se třemi textovými hodnotami (povinné, volitelné a zakázané), které označují požadavky v `wsa:ReplyTo` hlavičce (oddíl 3,2). Tato definice elementu bohužel není zvlášť použitelná jako kontrolní výraz v kontextu specifikace WS-Policy, protože vyžaduje rozšíření specifická pro doménu pro podporu průniku alternativ pomocí takového prvku jako kontrolního výrazu. Tato definice elementu také označuje hodnotu `ReplyTo` záhlaví na rozdíl od chování koncového bodu na lince, což umožňuje přenos přes protokol HTTP.

#### <a name="action-definition"></a>Definice akce
WS-Addressing 2004/08 definuje `wsa:Action` atribut pro `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` prvky. WS-Addressing 1,0 WSDL Binding (WS-ADDR10-WSDL) definuje podobný atribut `wsaw10:Action` .

Jediným rozdílem mezi těmito dvěma hodnotami je výchozí sémantika vzorců popsaná v části 3.3.2 specifikace WS-ADDR a sekce 4.4.4 elementu WS-ADDR10-WSDL, v uvedeném pořadí.

Je vhodné mít dva koncové body, které sdílejí stejný `portType` (nebo kontrakt v terminologii WCF), ale používají různé verze elementu WS-Addressing. Ale vzhledem k tomu, že tato akce je definována a nesmí se `portType` měnit mezi koncovými body, které implementují `portType` , není možné podporovat jak výchozí vzor akce.

Pro vyřešení tohoto Controversy podporuje WCF jedinou verzi `Action` atributu.

B3521: WCF používá `wsaw10:Action` atribut u `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementů definovaných v WS-ADDR10-WSDL k určení `Action` identifikátoru URI pro odpovídající zprávy bez ohledu na verzi WS-Addressing, kterou používá koncový bod.

#### <a name="use-endpoint-reference-inside-wsdl-port"></a>Použít odkaz na koncový bod uvnitř portu WSDL
WS-ADDR10-WSDL oddíl 4,1 rozšiřuje `wsdl:port` element tak, aby zahrnoval `<wsa10:EndpointReference…/>` podřízený element k popisu koncového bodu v rámci podmínek WS-Addressing. WCF rozšiřuje tento nástroj na WS-Addressing 2004/08, což umožňuje `<wsa:EndpointReference…/>` zobrazení jako podřízený element `wsdl:port` .

- R3531: Pokud má koncový bod připojenou alternativu zásady s `<wsaw10:UsingAddressing/>` kontrolním výrazem zásady, odpovídající `wsdl:port` prvek může obsahovat podřízený element `<wsa10:EndpointReference …/>` .

- R3532: Pokud `wsdl:port` obsahuje podřízený element `<wsa10:EndpointReference …/>` , `wsa10:EndpointReference/wsa10:Address` hodnota podřízeného elementu se musí shodovat s hodnotou `@address` atributu elementu na stejné úrovni `wsdl:port` / `wsdl:location` .

- R3533: Pokud má koncový bod připojenou alternativu zásad s `<wsap:UsingAddressing/>` kontrolním výrazem zásad, odpovídající `wsdl:port` element může obsahovat podřízený element `<wsa:EndpointReference …/>` .

- R3534: Pokud `wsdl:port` obsahuje podřízený element `<wsa:EndpointReference …/>` , `wsa:EndpointReference/wsa:Address` hodnota podřízeného elementu se musí shodovat s hodnotou `@address` atributu elementu na stejné úrovni `wsdl:port` / `wsdl:location` .

### <a name="composition-with-ws-security"></a>Složení pomocí WS-Security
V souladu s aspekty zabezpečení v oddílech WS-ADDR a WS-ADDR10 se doporučuje podepisovat všechna záhlaví zpráv adres, aby je bylo možné propojit společně s textem zprávy.

Pokud se pro ochranu integrity zpráv používá protokol WS-Security, záhlaví zpráv WS-Addressing a záhlaví, které jsou výsledkem z referenčních parametrů nebo vlastností (nebo obojí), musí být podepsané spolu s textem zprávy.

### <a name="examples"></a>Příklady

#### <a name="one-way-message"></a>Jednosměrná zpráva
V tomto scénáři odesílatel pošle jednosměrnou zprávu příjemci. Používají se protokoly SOAP 1,2, HTTP 1,1 a W3C WS-Addressing 1,0.

Struktura zprávy požadavku: záhlaví zpráv obsahují `wsa10:To` `wsa10:Action` prvky a. Tělo zprávy obsahuje konkrétní `<app:Ping>` prvek z oboru názvů aplikace.

Hlavičky HTTP: cíl v příspěvku odpovídá identifikátoru URI v `wsa10:To` elementu.

Hlavička Content-Type má hodnotu `application/soap+xml` podle požadavku SOAP 1,2. Parametry `charset` a `action` jsou zahrnuty. `action`Parametr záhlaví Content-Type se shoduje s hodnotou v `wsa10:Action` záhlaví zprávy.

```http
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

Příjemce odpoví prázdnou odpovědí HTTP a stav 202. Příklad odpovědi HTTP:

```http
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
Tato část popisuje podrobnosti implementace WCF pro HTTP SOAP pro MTOM. Technologie MTOM je mechanismus kódování zpráv SOAP stejné třídy jako tradiční kódování text/XML nebo binární kódování služby WCF. MTOM zahrnuje tyto:

- Mechanismus kódování a balení XML popsaný [XOP], který optimalizuje položky XML s informacemi, které obsahují binární data kódovaná pomocí Base64, do samostatných binárních částí.

- Zapouzdření MIME balíčku XOP, který zabalí XML sadu a každou binární část balíčku XOP do samostatné části MIME

- Kódování MIME XOP použité pro obálku SOAP 1. x.

- Vazba přenosu HTTP.

U služby WCF je možné použít MTOM s přenosem jiným než HTTP. V tomto tématu se ale zaměříme na HTTP.

Formát MTOM využívá velkou sadu specifikací, které se týkají samotného MTOM, XOP a MIME. Modularita této sady upřesnění je trochu obtížné rekonstruovat přesné požadavky na sémantiku formátu a zpracování. Tato část popisuje požadavky na formát a zpracování pro vazbu na MTOM protokolu HTTP.

### <a name="mtom-message-encoding"></a>Kódování zprávy MTOM

#### <a name="generating-mtom-messages"></a>Generování zpráv MTOM
Oddíl [XOP] 3,1 popisuje proces kódování XML s položkami informací o prvcích, které obsahují hodnoty Base64, do abstraktního definovaného balíčku XOP.

Následující posloupnost kroků popisuje proces kódování specifický pro MTOM:

1. Ujistěte se, že obálka protokolu SOAP, která má být zakódována, neobsahuje žádné položky informací o elementu s `[namespace name]` `http://www.w3.org/2004/08/xop/include` a `[local name]` `Include` .

2. Vytvořte prázdný balíček MIME.

3. Identifikujte se v rámci originální sady XML – informační položky prvku, které se mají optimalizovat. Pro položky, které mají být optimalizovány, musí být znaky, které tvoří `[children]` položku informací o prvku, v kanonické formě `xs:base64Binary` (viz XSD-2, 3.2.16 kódovaná base64Binary) a nesmí obsahovat žádné prázdné znaky před, vloženou s nebo za neprázdným obsahem.

4. Vytvořte obálku XOP SOAP, která je kopií původní obálky protokolu SOAP, ale s podřízenými položkami každé položky informací o elementu identifikované v předchozím kroku nahradila `xop:Include` položka informací o elementu vytvořenou takto:

    1. Převeďte nahrazené znaky na binární data jejich zpracováním jako data zakódovaná ve formátu base64.

    2. Vygenerujte jedinečnou hodnotu hlavičky Content-ID, která bude vyhovovat požadavkům R3133 a R3134.

    3. Vygenerujte hlavičku MIME Content-Transfer-Encoding s hodnotou Binary.

    4. Pokud je položka informací o prvku optimalizovaná ([Parent] nově vložené `xop:Include` informace o elementu) `xmime:contentType` , vygeneruje hlavičku MIME Content-Type s hodnotou `xmime:contentType` atributu.

    5. Vygeneruje novou binární část MIME s obsahem vytvořeným binárními daty, která byla dekódována z nahrazených znaků zpracovaných jako base64, hlavička Content-ID z 4. hlavičky Content-Transfer-Encoding z 4C, hlavička Content-Type, pokud je vygenerována v kroku 4d.

    6. Přidejte `href` atribut k `xop:Include` elementu s hodnotou CID: identifikátor URI odvozený z hodnoty hlavičky Content-ID vygenerované v kroku 4b. Odstraňte ohraničující " \<" and "> " znaky, adresu URL – řídicí znak zbývajícího řetězce a přidejte předponu `cid:` . Následující minimální znaková sada musí být uvozena řídicími znaky RFC1738 a RFC2396. Jiné znaky mohou být uvozeny řídicími znaky.

        ```
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"
        ```

5. Vytvořte kořenovou část MIME s obálkou XOP SOAP z kroku 4.

6. Zápis hlaviček protokolu HTTP včetně záhlaví Content-Type protokolu HTTP.

7. Zapište balíček MIME.

#### <a name="processing-mtom-messages"></a>Zpracování zpráv MTOM
Zpracování zprávy MTOM je přesné vrácení procesu popsaného v předchozí části "generování zpráv MTOM":

1. Ujistěte se, že kořenová část MIME má typ Content-Type `application/xop+xml` .

2. Vytvořte obálku protokolu SOAP tím, že proanalyzujete kořenovou část MIME balíčku jako dokument XML. Kódování znaků je určeno `charset` parametrem Content-Type kořenové části MIME.

3. Pro každou položku informací o elementu v konstruované obálce SOAP, která má jako jediný člen své vlastnosti [children], `xop:Include` položku informací o elementu:

    1. Odeberte `cid:` předponu a zrušte řídicí sekvence všech identifikátorů Escape URI (RFC 2396) v hodnotě `@href` atributu `xop:Include` elementu. Vložte výsledný řetězec do řetězce " \<", "> ".

    2. Vyhledejte část MIME s hodnotou hlavičky Content-ID, která odpovídá řetězci odvozenému v kroku 3a.

    3. Nahraďte `xop:Include` položku informací o elementu, která se zobrazí ve `children` Vlastnosti každé položky, pomocí položek informací o znacích, které reprezentují kanonické kódování Base64 (viz XSD-2, 3.2.16 kódovaná base64Binary) těla entity části MIME identifikované v kroku 3B (efektivně nahraďte `xop:Include` položku informací o elementu daty znovu vytvořenými z části balíčku).

#### <a name="http-content-type-header"></a>Hlavička Content-Type protokolu HTTP
Následuje seznam vyčiření WCF pro formát obsahu HTTP Content-Type zprávy protokolu SOAP 1. x, která je odvozena z požadavků uvedených ve specifikaci MTOM a jsou odvozena z MTOM a RFC 2387.

- R4131: Hlavička Content-Type protokolu HTTP musí mít hodnotu multipart/s (bez rozlišení velkých a malých písmen) a její parametry. V názvech parametrů se nerozlišují malá a velká písmena. Pořadí parametrů není důležité.

- Úplný formulář Backus-Naur (BNF) záhlaví Content-Type pro zprávy MIME je uveden v dokumentu RFC 2045, Section 5,1.

- R4132: Hlavička Content-Type protokolu HTTP musí mít parametr typu s hodnotou `application/xop+xml` uzavřenou v uvozovkách.

I když požadavek na použití dvojitých uvozovek není v RFC 2387 explicitní, text se bude řídit tím, že všechny parametry typu média s více částmi nebo s nimi budou pravděpodobně obsahovat rezervované znaky, jako například " \@ " nebo "/", a proto musí být dvojité uvozovky.

- R4133: Hlavička Content-Type protokolu HTTP by měla mít parametr Start s hodnotou hlavičky Content-ID části MIME, která obsahuje obálku SOAP 1. x uzavřenou do dvojitých uvozovek. Pokud je parametr Start vynechán, první část MIME musí obsahovat obálku SOAP 1. x.

- R4134: Hlavička Content-Type protokolu HTTP pro zprávu kódovaná v protokolu SOAP 1,1 musí zahrnovat parametr start-info s hodnotou text/XML uzavřenou do uvozovek.

- R4135: Hlavička Content-Type protokolu HTTP pro zprávu kódovaná pomocí protokolu SOAP 1,2 musí zahrnovat parametr start-info s hodnotou `application/soap+xml` uzavřenou do dvojitých uvozovek.

- R4136: Hlavička Content-Type protokolu HTTP pro zprávu s protokolem SOAP 1. x MTOM musí mít parametr hranice s hodnotou (uzavřenou do dvojitých uvozovek), která odpovídá BNF hranice MIME definované v dokumentu RFC 2046, oddíl 5.1.1.

    ```
    boundary := 0*69<bchars> bcharsnospace
    bchars := bcharsnospace / " "
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"
    ```

     Příklady:

     ODSTRANĚNÍ

    ```http
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"
    ```

     ODSTRANĚNÍ

    ```http
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

     ŠPATNÝ

    ```http
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"
    ```

#### <a name="infoset-mime-part"></a>Součást MIME informačního dílu
Obálka SOAP 1. x je zapouzdřená jako kořenová součást balíčku XOP MIME a často se nazývá `infoset` součást.

- R4141: obálka SOAP 1. x musí být zapouzdřena jako kořenová část balíčku rozhraní XOP MIME, která se nazývá `infoset` součást a odkazuje na typ obsahu HTTP.

- R4142: část SOAP `Infoset` musí zahrnovat následující záhlaví MIME: `Content-ID` , `Content-Transfer-Encoding` a `Content-Type` .

Formát záhlaví Content-ID je definován v dokumentu RFC 2045 jako

```
"Content-ID" ":" msg-id
```

kde `msg-id` je definován v dokumentu rfc 2822 (který nahrazuje specifikaci rfc 822, na kterou odkazuje rfc 2045) jako:

```
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]
```

a je to efektivně e-mailová adresa uzavřená v rámci " \<" and  "> ". `[CFWS]`Předpona a přípona byla přidána do RFC 2822, aby mohla přenášet komentáře a neměla by se používat k zachování interoperability.

R4143: hodnota hlavičky Content-ID pro součást MIME pro informační sadu musí splňovat `msg-id` produkci z dokumentu RFC 2822 s `[CFWS]` vynechánými částmi předpony a příponami.

Určitý počet implementací MIME má za následek, že pro hodnotu uzavřenou v rámci " \<" and "> " má být e-mailová adresa, která se používá `absoluteURI` \<" , "> společně s e-mailovou adresou. Tato verze WCF používá hodnoty záhlaví MIME Content-ID ve formátu:

```
Content-ID: <http://tempuri.org/0>
```

R4144: procesory MTOM by měly přijmout hodnoty hlaviček Content-ID, které odpovídají následujícímu uvolněnému `msg-id` .

```
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]
mail-address   =     id-left "@" id-right
```

MIME (RFC 2045) poskytuje hlavičku Content-Transfer-Encoding pro komunikaci s kódováním obsahu části MIME. Výchozí hodnota definovaná pro kódování Content-Transfer-Encoding je 7 bitů, což není vhodné pro většinu zpráv SOAP, takže hlavička Content-Transfer-Encoding je nutná pro lepší interoperabilitu:

- R4145: část informačního doplňku SOAP musí obsahovat hlavičku Content-Transfer-Encoding.

- R4146: Pokud kódování znaků obálky protokolu SOAP je UTF-8, hodnota hlavičky Content-Transfer-Encoding musí být 8 bitů.

- R4147: Pokud je kódování znaků obálky protokolu SOAP UTF-16, hodnota hlavičky Content-Transfer-Encoding musí být binární.

- Podle [XOP] sekce 5,

- R4148: část s informačními zprávami SOAP 1.1 musí obsahovat hlavičku Content-Type s typem média Application/XOP + XML a Parameters Type = "text/XML" a charset

    ```http
    Content-Type: application/xop+xml;
                  charset=utf-8;type="text/xml"
    ```

- R4149: část s obsahem součásti SOAP 1,2 musí obsahovat hlavičku Content-Type s typem média `application/xop+xml` a parametry Type = " `application/soap+xml` " a `charset` .

    ```http
    Content-Type: application/xop+xml;
                  charset=utf-8;type="application/soap+xml"
    ```

     A když XOP definuje `charset` parametr pro `application/xop+xml` , aby byl volitelný, je potřeba pro interoperabilitu podobnou požadavku BP 1,1 u `charset` parametru pro `text/xml` typ média.

- R41410: `type` parametry a se musí nacházet `charset` v hlavičce Content-Type součásti sady ODHLAŠOVÁNÍ protokolu SOAP 1. x.

#### <a name="wcf-endpoint-support-for-mtom"></a>Podpora koncových bodů WCF pro MTOM
Účelem MTOM je zakódovat zprávu SOAP pro optimalizaci dat kódovaných v kódování Base64. Níže je seznam omezení:

- R4151: je možné optimalizovat všechny informace o elementu, které obsahují data kódovaná pomocí Base64.

- B4152: WCF optimalizuje položky informací o elementu, které obsahují data kódovaná pomocí Base64, a překračují 1024 bajtů.

Koncový bod WCF nakonfigurovaný k použití MTOM bude vždycky odesílat zprávy kódované v rámci MTOM. I když žádné části nesplňují požadovaná kritéria, zpráva je stále v kódování MTOM (serializovaná jako balíček MIME s jednou částí MIME obsahující obálku protokolu SOAP).

### <a name="ws-policy-assertion-for-mtom"></a>Kontrolní výraz WS-Policy pro MTOM
Služba WCF používá následující kontrolní výraz zásad pro indikaci využití MTOM Endpoint:

```xml
<wsoma:OptimizedMimeSerialization />
```

- R4211: kontrolní výraz předchozí zásady má předmět zásad koncového bodu, který určuje, že všechny zprávy odeslané do a přijaté z koncového bodu musí být optimalizované pomocí MTOM.

- B4212: Pokud je nakonfigurované použití optimalizace MTOM, koncový bod WCF přidá do zásady připojené k odpovídajícímu výrazu zásadu MTOM `wsdl:binding` .

### <a name="composition-with-ws-security"></a>Složení pomocí WS-Security
MTOM je kódovací mechanismus, který se podobá `text/xml` a binární XML služby WCF. MTOM nabízí přirozené složení pomocí WS-Security a dalších protokolů WS-*: zpráva zabezpečená pomocí WS-Security se dá optimalizovat pomocí MTOM.

### <a name="examples"></a>Příklady

#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>Zpráva WCF SOAP 1,1 zakódovaná pomocí MTOM

```http
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

#### <a name="wcf-secure-soap-12-message-encoded-using-mtom"></a>Zabezpečená zpráva SOAP 1,2 WCF kódovaná pomocí MTOM
V tomto příkladu je zpráva kódovaná pomocí MTOM a protokolu SOAP 1,2, který je chráněný pomocí WS-Security. Binární části identifikované pro kódování jsou obsahem `BinarySecurityToken` , který `CipherValue` `EncryptedData` odpovídá zašifrovanému podpisu a šifrovanému textu. Všimněte si, že `CipherValue` `EncryptedKey` služba nebyla identifikována pro optimalizaci pomocí služby WCF, protože její délka je menší než 1024 bajtů.

```http
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
