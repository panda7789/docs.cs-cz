---
title: "Protokoly zasílání zpráv"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5b20bca7-87b3-4c8f-811b-f215b5987104
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: fef5fc58adeac99bcd2cac0fda8a72dde2797001
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="messaging-protocols"></a>Protokoly zasílání zpráv
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Kanál zásobníku využívá kódování a přenos kanály transformace reprezentace interní zprávy do jeho přenosový formát a odesílat je pomocí konkrétního přenosu. Nejběžnější přenos používá funkční spolupráce při webové služby, je HTTP, a nejběžnější kódování používá webové služby jsou na základě XML SOAP 1.1, SOAP 1.2 a zpráva přenosu optimalizace mechanismus (MTOM).  
  
 Toto téma popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podrobnosti implementace pro následující protokoly zaměstnaní <xref:System.ServiceModel.Channels.HttpTransportBindingElement>.  
  
|Specifikace či dokumentu|Odkaz|  
|-----------------------------|----------|  
|HTTP 1.1|http://www.ietf.org/rfc/rfc2616.txt|  
|SOAP 1.1 vazby HTTP|http://www.w3.org/TR/2000/Note-SOAP-20000508/, část 7|  
|SOAP 1.2 vazby HTTP|http://www.w3.org/TR/soap12-part2/, část 7|  
  
 Toto téma popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementace podrobnosti pro následující protokoly <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> využívají.  
  
|Specifikace či dokumentu|Odkaz|  
|-----------------------------|----------|  
|XML|http://www.w3.org/TR/rec-XML|  
|SOAP 1.1|http://www.w3.org/TR/2000/Note-SOAP-20000508/|  
|SOAP 1.2 jádra|http://www.w3.org/TR/soap12-part1/|  
|Adresování WS 2004/08|http://www.w3.org/submission/2004/SUBM-WS-Addressing-20040810/|  
|W3C webových služeb adresování 1.0 – základní|http://www.w3.org/TR/2006/rec-ws-addr-Core-20060509|  
|W3C webových služeb adresování 1.0 - vazby protokolu SOAP|http://www.w3.org/TR/2006/rec-ws-addr-SOAP-20060509|  
|W3C webových služeb adresování 1.0 - vazby WSDL|http://www.w3.org/TR/2006/CR-ws-addr-WSDL-20060529/|  
W3C webových služeb adresování 1.0 - metadat|http://www.w3.org/TR/ws-addr-metadata/|  
|Vazba SOAP1.1 WSDL|http://www.w3.org/TR/WSDL/|  
|Vazba SOAP1.2 WSDL|http://www.w3.org/submission/wsdl11soap12/|  
  
 Toto téma popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementace podrobnosti pro následující protokoly <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> využívá.  
  
|Specifikace či dokumentu|Odkaz|  
|-----------------------------|----------|  
|XOP|http://www.w3.org/TR/xop10/|  
|MTOM + SOAP 1.2 vazby|http://www.w3.org/TR/soap12-MTOM/|  
|MTOM SOAP 1.1 vazby|http://www.w3.org/submission/soap11mtom10/|  
|Výraz WS-zásad MTOM|http://www.w3.org/submission/2006/SUBM-ws-MTOMPolicy-20061101/.|  
  
 Následující obory názvů XML a přidružené předpony se používají v tomto tématu.  
  
|Předpona|Namespace Uniform Resource Identifier (URI)|  
|------------|---------------------------------------------------|  
|s.11|http://schemas.xmlsoap.org/soap/envelope|  
|S12|http://www.w3.org/2003/05/SOAP-Envelope|  
|wsa|http://www.w3.org/2004/08/Addressing|  
|wsam|http://www.w3.org/2007/05/Addressing/metadata|  
|wsap|http://schemas.xmlsoap.org/ws/2004/09/Policy/Addressing|  
|wsa10|http://www.w3.org/2005/08/Addressing|  
|wsaw10|http://www.w3.org/2006/05/Addressing/WSDL|  
|XOP|http://www.w3.org/2004/08/XOP/Include|  
|xmime|http://www.w3.org/2004/06/xmlmime<br /><br /> http://www.w3.org/2005/05/xmlmime|  
distribučního bodu|http://schemas.microsoft.com/NET/2006/06/duplex|  
  
## <a name="soap-11-and-soap-12"></a>SOAP 1.1 a SOAP 1.2  
  
### <a name="envelope-and-processing-model"></a>Obálky a zpracování modelu  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje zpracování obálky protokolu SOAP 1.1 Basic Profile 1.1 (základní parametr 11) a základní profil 1.0 (SSBP10). SOAP 1.2 obálky zpracování je implementována následující část SOAP12-1.  
  
 Tato část popisuje některé volby implementace provedenou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] s ohledem na základní parametr 11 a část SOAP12-1.  
  
#### <a name="mandatory-header-processing"></a>Zpracování povinnou hlavičku  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]dodržuje pravidla pro zpracování hlavičky označena `mustUnderstand` popsané v protokolu SOAP 1.1 a SOAP 1.2 specifikace, s následující rozdíly.  
  
 Zprávu, která přejde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] kanál zásobníku zpracovává jednotlivé kanály nakonfiguroval prvky přidružené vazeb, například, kódování textu zprávy, zabezpečení, spolehlivé zasílání zpráv a transakce. Každý kanál rozpozná hlavičky z přidružených oboru názvů a označí je jako rozumí. Jakmile zprávu zadá dispečera, přečte operaci formátování záhlaví očekávanou odpovídající kontrakt zprávy nebo operaci a značky, které jim rozumím jim. Pak dispečera ověřuje, zda nejsou žádné zbývající hlavičky rozumí ale označen jako `mustUnderstand` a vyvolá výjimku. Zprávy, které obsahují `mustUnderstand` hlavičky, které jsou zaměřeny na příjemce nejsou zpracovávány kód příjemce aplikace.  
  
 Například vrstvený zpracování umožňuje oddělení mezi infrastruktury vrstvy a aplikaci vrstvy protokolu SOAP uzlu:  
  
-   B1111: Hlavičky, které nejsou rozumí se zjistí po zpracovává zprávy [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zásobník kanál infrastruktury, ale předtím, než je zpracován aplikací  
  
     `mustUnderstand` Hodnota hlavičky se liší mezi SOAP 1.1 a SOAP 1.2. Basic Profile 1.1 vyžaduje, aby `mustUnderstand` hodnota být 0 nebo 1 pro zprávy SOAP 1.1. SOAP 1.2 umožňuje 0, 1, `false`, a `true` hodnoty, ale doporučuje emitování kanonický reprezentace `xs:boolean` hodnoty (`false`, `true`).  
  
-   B1112: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vysílá `mustUnderstand` hodnoty 0 a 1 pro verze protokolu SOAP 1.1 a SOAP 1.2 obálky protokolu SOAP. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]přijímá prostor celou hodnotu `xs:boolean` pro `mustUnderstand` záhlaví (0, 1, `false`, `true`)  
  
#### <a name="soap-faults"></a>Chyb SOAP  
 Následuje seznam [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-konkrétní implementace chybu protokolu SOAP.  
  
-   B2121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vrátí následující kódy chyb protokolu SOAP 1.1: `s11:mustUnderstand`, `s11:Client`, a `s11:Server`.  
  
-   B2122: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vrátí následující kódy chyb protokolu SOAP 1.2: `s12:MustUnderstand`, `s12:Sender`, a `s12:Receiver`.  
  
### <a name="http-binding"></a>Vazba HTTP  
  
#### <a name="soap-11-http-binding"></a>SOAP 1.1 vazby HTTP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje vazby SOAP1.1 HTTP následující specifikace Basic Profile 1.1 oddíl 3.4 objasnění následující:  
  
-   B2211: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služby neimplementuje přesměrování požadavky HTTP POST.  
  
-   B2212: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klienti podporují soubory cookie protokolu HTTP v souladu s 3.4.8.  
  
#### <a name="soap-12-http-binding"></a>SOAP 1.2 vazby HTTP  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]jak je popsáno v protokolu SOAP 1.2 část 2 (SOAP12Part2) specifikace s následující objasnění, implementuje vazby protokolu SOAP 1.2 HTTP.  
  
 Parametr volitelné akce pro zavedená SOAP 1.2 `application/soap+xml` typ média. Tento parametr je užitečné k optimalizaci odesílání zpráv bez nutnosti analyzovat do těla protokolu SOAP zprávy při adresování WS nepoužívá.  
  
-   R2221: `application/soap+xml` parametr akce, pokud jsou k dispozici na vyžádání SOAP 1.2, musí odpovídat `soapAction` atributu u `wsoap12:operation` prvku v odpovídající vazby WSDL.  
  
-   R2222: `application/soap+xml` parametr akce, pokud jsou k dispozici na zprávu protokolu SOAP 1.2 musí odpovídat `wsa:Action` při použití služby WS-Addressing 2004/08 nebo WS-Addressing 1.0.  
  
 Když WS-Addressing je zakázána a příchozí požadavek neobsahuje parametr akce, zprávy `Action` považuje za není zadaný.  
  
## <a name="ws-addressing"></a>Adresování WS  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje 3 verze WS adresování:  
  
-   Adresování WS 2004/08  
  
-   Adresování 1.0 jádra (ADDR10-jader) a vazbu (ADDR10 protokolu SOAP) SOAP W3C webové služby  
  
-   Adresování WS 1.0 - metadat  
  
### <a name="endpoint-references"></a>Odkazy na koncový bod  
 Všechny verze WS-Addressing který [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementuje pomocí koncového bodu odkazy popisují koncové body.  
  
#### <a name="endpoint-references-and-ws-addressing-versions"></a>Odkazy na koncový bod a adresování WS verze  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje číslo infrastruktury protokolů, které používají služby WS-Addressing, zejména `EndpointReference` elementu a `W3C.WsAddressing.EndpointReferenceType` – třída (například WS-ReliableMessaging, WS-SecureConversation a WS-Trust). [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje použití buď verzi WS-Addressing s ostatními protokoly infrastruktury. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Koncové body podporovat jednu verzi WS-Addressing na jeden koncový bod.  
  
 Pro R3111, obor názvů pro `EndpointReference` element nebo typ použitý v zprávy se vyměňují [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncového bodu musí odpovídat verzi WS adresování implementované tento koncový bod.  
  
 Například pokud [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementuje koncový bod protokolu WS-ReliableMessaging `AcksTo` hlavička bodem uvnitř `CreateSequenceResponse` používá verzi WS-Addressing, `EncodingBinding` element určuje pro tento koncový bod.  
  
#### <a name="endpoint-references-and-metadata"></a>Odkazy na koncový bod a Metadata  
 Různé scénáře vyžadují komunikaci metadata nebo odkaz na metadata pro daný koncový bod.  
  
 B3121: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] využívá mechanismy popsána ve specifikaci WS-MetadataExchange (MEX) část 6 Zahrnout metadata pro koncový bod odkazy hodnotou nebo odkazem.  
  
 Zvažte scénář, kde [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba vyžaduje, aby ověření pomocí tokenu zabezpečení kontrolní výrazy Markup Language (SAML) vydaný vydavatel tokenu v http://sts.fabrikam123.com. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Koncový bod popisuje tento požadavek ověřování pomocí `sp:IssuedToken` kontrolní výraz s vnořeným `sp:Issuer` assertion odkazující na vydavatel tokenu. Klientských aplikací, které přístup `sp:Issuer` assertion muset vědět, jak ke komunikaci s koncovým bodem tokenu vystavitele. Klient musí vědět, metadata o vydavatel tokenu. Pomocí rozšíření koncový bod odkaz metadata definovaná v MEX, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje odkaz na metadata vydavatel tokenu.  
  
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
  
### <a name="message-addressing-headers"></a>Adresování hlavičky zpráv  
  
#### <a name="message-headers"></a>Hlavičky zpráv  
 Pro obě verze WS-Addressing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá následující záhlaví zprávy podle specifikace `wsa:To`, `wsa:ReplyTo`, `wsa:Action`, `wsa:MessageID`, a `wsa:RelatesTo`.  
  
 B3211: pro všechny verze WS-Addressing [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ctí, ale nevytváří předinstalované, WS-Addressing hlavičky zpráv `wsa:FaultTo` a `wsa:From`.  
  
 Aplikace, které spolupracují s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace můžete přidat tyto zprávy hlavičky a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] jejich zpracování odpovídajícím způsobem.  
  
#### <a name="reference-parameters-and-properties"></a>Odkaz na parametry a vlastnosti  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje zpracování parametrů odkaz na koncový bod a p – referenční informace  
  
 vlastnosti v souladu s příslušnými specifikace.  
  
 B3221: Pokud nakonfigurovaná pro použití služby WS-Addressing 2004/08 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncové body nerozlišují mezi zpracování vlastnosti odkazu a odkaz na parametry.  
  
### <a name="message-exchange-patterns"></a>Vzory Exchange zpráv  
 Pořadí zpráv zahrnutých v operaci volání webové služby se označuje jako *vzorce výměny zpráv*. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]podporuje jednosměrné, požadavku a odpovědi a duplexní zprávu výměna vzory. Tato část vysvětluje, WS-Addressing požadavky na zpracování v závislosti na vzorce výměny zpráv používá zpráv.  
  
 V této části žadatel odešle první zprávy a příjemce obdrží první zprávu.  
  
#### <a name="one-way-message"></a>Jednosměrné zpráv  
 Při [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod je nakonfigurován pro podporu zprávy s dané `Action` sledovat jednosměrného vzor, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod dodržuje následující požadavky a chování. Pokud není uvedeno jinak, chování a pravidla platí pro obě verze WS-Addressing podporované v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R3311: Žadatel musí zahrnovat `wsa:To`, `wsa:Action`a hlavičky pro všechny parametry odkaz určeného odkaz na koncový bod. Když se používá WS-Addressing 2004/08 a [Vlastnosti odkazu] jsou určené odkaz na koncový bod odpovídající hlavičky musí být přidaný do zprávy příliš.  
  
-   B3312: Žadatel může zahrnovat `MessageID`, `ReplyTo`, a `FaultTo` hlavičky. Příjemce infrastruktury je bude ignorovat a se předají do aplikace.  
  
-   R3313: Když se používá protokol HTTP a odesílání žádné zprávy na větev odpověď HTTP, musíte odeslat odpovídající počítač s prázdným textem zprávy a HTTP 202 stavový kód HTTP odpovědi.  
  
     Pokud přenos HTTP je používán a kontrakt operaci deklaruje zprávu jednosměrné, odpověď HTTP pořád můžou použít pro odesílání zpráv infrastruktury – například může odesílat spolehlivé zasílání zpráv `SequenceAcknowledgement` zprávu na odpovědi HTTP.  
  
-   B3314: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] respondér neodesílá zprávu o chybě v odpovědi na zprávu jednosměrná.  
  
#### <a name="request-reply"></a>Požadavek a odpověď  
 Při [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod je nakonfigurován pro zprávu s danou `Action` podle vzoru požadavku a odpovědi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod řídí chování a požadavky uvedené níže. Pokud není uvedeno jinak, chování a pravidla platí pro obě verze WS-Addressing podporované v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]:  
  
-   R3321: Žadatel musí zahrnovat v požadavku `wsa:To`, `wsa:Action`, `wsa:MessageID`, tak i hlaviček pro všechny parametry odkaz nebo odkaz na vlastnosti (nebo obě) určeného odkaz na koncový bod.  
  
-   R3322: Pokud je použita WS-Addressing 2004/08, `ReplyTo` musí také obsahovat žádosti.  
  
-   R3323: Pokud se používá WS-Addressing 1.0 a `ReplyTo` není přítomný v požadavku, odkaz na výchozí koncový bod s rovno "http://www.w3.org/2005/08/addressing/anonymous" [address] vlastnost se používá.  
  
-   R3324: Žadatel musí zahrnovat `wsa:To`, `wsa:Action`, a `wsa:RelatesTo` hlavičky v odpovědi, jakož i hlavičky pro všechny parametry odkaz nebo odkaz na vlastnosti (nebo obě) určeného `ReplyTo` odkaz na koncový bod v požadavek.  
  
### <a name="web-services-addressing-faults"></a>Webové služby adresování chyb  
 R3411: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vytváří následující chyb definované WS-Addressing 2004/08.  
  
|Kód|příčina|  
|----------|-----------|  
|wsa:DestinationUnreachable|Zpráva dorazila po uplynutí `ReplyTo` , se liší od navázána pro tento kanál adresu; neexistuje žádný koncový bod naslouchá na adresu zadanou v hlavičce na.|  
|wsa:ActionNotSupported|kanály infrastruktury nebo dispečera přiřazené ke koncovému bodu nerozpoznávají zadaná v akci `Action` záhlaví.|  
  
 R3412: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vytváří následující chyb definované WS-Addressing 1.0.  
  
|Kód|příčina|  
|----------|-----------|  
|wsa10:InvalidAddressingHeader|Duplicitní `wsa:To`, `wsa:ReplyTo`, `wsa:From` nebo `wsa:MessageID`. Duplicitní `wsa:RelatesTo` se stejným `RelationshipType`.|  
|wsa10:MessageAddressingHeaderRequired|Požadovaná hlavička Addressing nebyl nalezen.|  
|wsa10:DestinationUnreachable|Zpráva dorazila po uplynutí `ReplyTo` která se liší od navázána pro tento kanál adresu. Neexistuje žádný koncový bod naslouchá na adresu zadanou v hlavičce na.|  
|wsa10:ActionNotSupported|Zadaná v akci `Action` hlavička nebyla rozpoznána infrastruktury kanály nebo dispečera přiřazené ke koncovému bodu.|  
|wsa10:EndpointUnavailable|Kanál RM odešle tato porucha zpět, označující koncový bod nezpracuje pořadí na základě zkoumání `CreateSequence` zprávu o adrese hlavičky.|  
  
 Kód v předchozích tabulkách se mapuje na `FaultCode` v SOAP 1.1 a `SubCode` (s kódem = odesílatele) v protokolu SOAP 1.2.  
  
### <a name="wsdl-11-binding-and-ws-policy-assertions"></a>WSDL 1.1 vazby a WS-Policy kontrolní výrazy  
  
#### <a name="indicating-use-of-ws-addressing"></a>Označující použití adresování WS  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]koncový bod podporu pro konkrétní verzi WS-Addressing použije výrazy zásad.  
  
 Následující výraz zásad má koncový bod zásad subjektu [WS-PA] a znamená, že zprávy odeslané a přijaté z koncového bodu musí používat WS-Addressing 2004/08.  
  
```xml  
<wsap:UsingAddressing />  
```  
  
 Tento výraz zásad argumentech specifikace WS-Addressing 2004/08.  
  
 Následující výraz zásad, že to znamená, že který zprávy odeslat/přijmout musí používat WS-Addressing 1.0.  
  
```xml
<wsam:Addressing/>   
```  
  
 Následující výraz zásad má předmět zásad služby Endpoint [WS-PA] a označuje, že zprávy odeslané a přijaté z koncového bodu musí používat WS-Addressing 2004/08.  
  
```xml  
<wsaw10:UsingAddressing />  
```  
  
 `wsaw10:UsingAddressing` Elementu je vždy pouze vypůjčí na [WS-adresování-WSDL] a je použita v kontextu služby WS-Policy v souladu s této specifikaci se v části 3.1.2.  
  
 Použití Addressing nezmění sémantika WSDL 1.1, SOAP 1.1 a SOAP 1.2 HTTP vazby. Například pokud je odpověď na žádost, kterou posílá koncový bod, který používá Addressing a WSDL SOAP vazby HTTP 1.x očekávána, musí se odpovědi poslat pomocí odpověď HTTP.  
  
 Pro odpovědi, odešlou přes odpověď http WS-AM kontrolní výraz je:  
  
```xml  
<wsam:AnonymousResponses/>  
```  
  
 Výraz dokončení zásad může vypadat například takto:  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
        <wsam:AnonymousResponses />   
    </wsp:Policy>  
</wsam:Addressing>  
```  
  
 Existují však vzory exchange zprávu, využívající má dva nezávislé konverzace HTTP připojení mezi žadatel a respondér, například nevyžádané jednosměrný zprávy odeslané respondér.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]nabízí funkce, pomocí kterého můžete dvě základní přenosové kanály formuláři složené duplexní kanál, kde jeden kanál je používána pro vstupní zprávy a druhý je používána pro zprávy výstup. V případě přenos HTTP poskytuje složené duplexní dvě připojení HTTP konverzace. Žadatel používá jedno připojení k odesílání zpráv do odpovídající partner a odpovídající partner dalších odesílání zprávy zpět na žadatel.  
  
 Pro odpovědi, odešlou přes požadavky http samostatné ws-am kontrolní výraz je  
  
```xml  
<wsam:NonAnonymousResponses/>  
```  
  
 Výraz dokončení zásad může vypadat například takto:  
  
```xml  
<wsam:Addressing>  
    <wsp:Policy>  
      <wsam:NonAnonymousResponses />   
   </wsp:Policy>  
  </wsam:Addressing>  
```  
  
 Následující kontrolní výraz, který má koncový bod zásad subjektu [WS-PA] na koncové body, které pomocí vazby HTTP 1.x WSDL 1.1 SOAP vyžaduje dva samostatné konverzace připojení protokolu HTTP má být použit pro zpráv předávaných z žadatel respondér a respondér k žadatel, v uvedeném pořadí.  
  
```xml  
<cdp:CompositeDuplex/>  
```  
  
 Předchozí příkaz vede k následující požadavky `wsa:ReplyTo` hlavičky pro žádosti o zprávy:  
  
-   R3514: Žádosti o zprávy odeslané do koncového bodu musí mít `ReplyTo` hlavička s `[address]` vlastnost "http://www.w3.org/2005/08/addressing/anonymous" není rovno, pokud koncový bod používá vazbu 1.x HTTP WSDL 1.1 SOAP a má alternativní zásady s `wsap10:UsingAddressing` nebo `wsap:UsingAddressing` assertion kombinaci s `cdp:CompositeDuplex` připojen.  
  
-   R3515: Žádosti o zprávy odeslané do koncového bodu musí mít `ReplyTo` hlavička s `[address]` vlastnost rovno "http://www.w3.org/2005/08/addressing/anonymous", nebo není `ReplyTo` záhlaví na všechny, pokud koncový bod používá WSDL 1.1 SOAP 1.x HTTP vazby a má zásadu alternativní s `wsap10:UsingAddressing` kontrolní výraz a ne `cdp:CompositeDuplex` assertion připojen.  
  
-   R3516: Žádosti o zprávy odeslané do koncového bodu musí mít `ReplyTo` hlavička s `[address]` vlastnost rovno "http://www.w3.org/2005/08/addressing/anonymous" Pokud koncový bod používá vazbu 1.x HTTP WSDL 1.1 SOAP a má zásadu alternativní s `wsap:UsingAddressing` kontrolní výraz a ne `cdp:CompositeDuplex` assertion připojen.  
  
 Specifikace WS-addressing WSDL pokusí popisují podobné vazby protokolu zavedením element `<wsaw:Anonymous/>` s tři textové hodnoty (vyžaduje, volitelné a zakázané) k označení požadavky na `wsa:ReplyTo` hlavičky (část 3.2). Bohužel taková definice elementu není zvlášť jako kontrolní výrazy v kontextu služby WS-zásad, protože vyžaduje rozšíření specifické pro doménu, které podporují průnik alternativy pomocí takový prvek jako kontrolní výrazy. Taková definice elementu také určuje hodnota `ReplyTo` záhlaví oproti chování koncového bodu v drátové síti, takže je konkrétní přenos HTTP.  
  
#### <a name="action-definition"></a>Definice akce  
 Definuje WS-Addressing 2004/08 `wsa:Action` atribut pro `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` elementy. Adresování WS 1.0 WSDL vazby (WS-ADDR10-WSDL) definuje atribut podobné `wsaw10:Action`.  
  
 Jediným rozdílem mezi těmito dvěma je sémantiky vzor výchozí akce popsané v 3.3.2 WS-ADDR a oddílu bodu 4.4.4 WS-ADDR10-WSDL, v uvedeném pořadí.  
  
 Je možné logicky tak, aby měl dva koncové body, které sdílejí stejné `portType` (nebo kontrakt, v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] terminologie), ale používání různých verzí WS adres. Ale vzhledem k tomu, že je definována akce `portType` a neměli měnit napříč koncovými body, které implementují `portType`, bude možné podporovat i výchozí akci zpracování.  
  
 Chcete-li vyřešit tento sporům [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podporuje jednu verzi `Action` atribut.  
  
 B3521: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá `wsaw10:Action` atributu u `wsdl:portType/wsdl:operation/[wsdl:input | wsdl:output | wsdl:fault]` dle WS-ADDR10-WSDL k určení `Action` identifikátor URI pro odpovídající zprávy, bez ohledu na verzi WS-Addressing používá koncový bod.  
  
#### <a name="use-endpoint-reference-inside-wsdl-port"></a>Použití koncový bod odkaz uvnitř WSDL portu  
 WS-ADDR10-WSDL části 4.1 rozšiřuje `wsdl:port` elementu, který chcete zahrnout `<wsa10:EndpointReference…/>` podřízený element k popisu koncový bod v WS-Addressing podmínky. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]rozšíří na adresování WS 2004/08, tento nástroj umožňuje `<wsa:EndpointReference…/>` vypadaly jako podřízeného prvku `wsdl:port`.  
  
-   R3531: Pokud koncový bod má alternativu připojené zásady s `<wsaw10:UsingAddressing/>` výraz zásad, příslušné `wsdl:port` element může obsahovat podřízený element `<wsa10:EndpointReference …/>`.  
  
-   R3532: Pokud `wsdl:port` obsahuje podřízený element `<wsa10:EndpointReference …/>`, `wsa10:EndpointReference/wsa10:Address` podřízený element hodnota musí odpovídat hodnotě `@address` atribut na stejné úrovni `wsdl:port` / `wsdl:location` element.  
  
-   R3533: Pokud koncový bod má alternativu připojené zásady s `<wsap:UsingAddressing/>` výraz zásad, příslušné `wsdl:port` element může obsahovat podřízený element `<wsa:EndpointReference …/>`.  
  
-   R3534: Pokud `wsdl:port` obsahuje podřízený element `<wsa:EndpointReference …/>`, `wsa:EndpointReference/wsa:Address` podřízený element hodnota musí odpovídat hodnotě `@address` atribut na stejné úrovni `wsdl:port` / `wsdl:location` element.  
  
### <a name="composition-with-ws-security"></a>Složení s WS-zabezpečení  
 Podle zabezpečení části aspekt WS-ADDR a WS-ADDR10 se doporučuje všechny adresování hlavičky zpráv být podepsané společně s text zprávy pro vazbu je společně.  
  
 Pokud WS-zabezpečení se používá pro ochranu integrity zprávy, musí být podepsané WS-Addressing zpráva hlavičky, jakož i hlavičky výsledkem parametry odkaz nebo vlastnosti (nebo obě) společně s tělo zprávy.  
  
### <a name="examples"></a>Příklady  
  
#### <a name="one-way-message"></a>Jednosměrné zpráv  
 V tomto scénáři odesílatel odešle zprávu jednosměrný k příjemce. SOAP 1.2, HTTP 1.1 a 1.0 W3C WS-Addressing se používají.  
  
 Struktura zprávu požadavku: Záhlaví zprávy zahrnují `wsa10:To` a `wsa10:Action` elementy. Tělo zprávy obsahuje konkrétní `<app:Ping>` element z oboru názvů aplikace.  
  
 Hlavičky protokolu HTTP: Cíl v BLOGU odpovídá identifikátoru URI v `wsa10:To` elementu.  
  
 Hlavička Content-Type má hodnotu `application/soap+xml` podle požadavku SOAP 1.2. Parametry `charset` a `action` jsou zahrnuty. `action` Hodnota odpovídá parametru hlavičku Content-Type `wsa10:Action` záhlaví zprávy.  
  
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
  
 Příjemce odpoví s prázdnou odpověď HTTP a stav 202. Příklad odpověď HTTP:  
  
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
  
## <a name="soap-message-transmission-optimization-mechanism"></a>Mechanismus Optimalizace přenosu zpráv protokolu SOAP  
 Tato část popisuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] podrobnosti implementace pro MTOM SOAP protokolu HTTP. Technologie MTOM je protokolu SOAP zprávy kódování mechanismus stejnou třídou jako kódování tradiční text/XML nebo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binárního kódování. MTOM zahrnuje následující položky:  
  
-   Kódování XML a mechanismus balení [XOP] popsaného který optimalizuje položky informace XML obsahující binární data s kódováním base64 na samostatné části binární.  
  
-   MIME zapouzdření XOP balíčku, který serializuje informační sadu XML a každý binární součást balíčku XOP do samostatné části standardu MIME.  
  
-   MIME XOP kódování u SOAP 1.x obálku.  
  
-   HTTP přenosu vazby.  
  
 Je možné použít MTOM s jiným protokolem než HTTP přenosy s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Ale v tomto tématu se zaměříme na protokolu HTTP.  
  
 Formát MTOM využívá velké sady specifikace, které se týkají MTOM sám sebe, XOP a MIME. Modularitu této sady specifikace ztěžuje poněkud rekonstrukci přesných požadavcích na sémantiku formátu a zpracování. Tato část popisuje požadavky na zpracování a formát pro vazbu protokolu HTTP MTOM.  
  
### <a name="mtom-message-encoding"></a>Kódování MTOM zpráv  
  
#### <a name="generating-mtom-messages"></a>Generování zprávy MTOM  
 [XOP] části 3.1 popisuje proces kódování XML s položkami informace element, které obsahují hodnoty base64 do balíčku abstraktně definované XOP.  
  
 Následující pořadí kroků popisuje proces kódování MTOM konkrétní:  
  
1.  Zajistěte, aby obsahoval obálku protokolu SOAP kódovaný žádná položka informace o elementu s `[namespace name]` z "http://www.w3.org/2004/08/xop/include" a `[local name]` z `Include`.  
  
2.  Vytvořte prázdný balíček MIME.  
  
3.  Identifikujte v původní informační sadu XML položky informace o elementu, které chcete optimalizovat. Pro položky, které chcete optimalizovat, znaky, tvoří `[children]` informace o elementu položky musí být v kanonickém tvaru `xs:base64Binary` (viz XSD-2, 3.2.16 pomocí base64Binary) a nesmí obsahovat žádné prázdné znaky před vložením s, nebo Následující obsah neprázdný.  
  
4.  Vytvoří obálku protokolu SOAP XOP, který je kopií původního obálky protokolu SOAP, ale s podřízenými položkami každý element informací nahrazuje položku identifikovat v předchozím kroku `xop:Include` element informace položka vytvořená následujícím způsobem:  
  
    1.  Transformace nahrazené znaků do binární data zpracováním je jako data s kódováním base64.  
  
    2.  Generovat jedinečný hodnota hlavičky Content-ID, který splňuje požadavky R3133 a R3134.  
  
    3.  Vygenerujte hlavička kódování přenosu obsahu MIME s binární hodnotu.  
  
    4.  Pokud se informace o položce element optimalizována ([nadřazený] nově vloženého `xop:Include` element informace položky) má `xmime:contentType` atribut položky informace, vygenerujte hlavičku Content-Type MIME s hodnotou `xmime:contentType` atribut.  
  
    5.  Generovat nové části binární standardu MIME s obsahem tvořená binární data dekódovat z nahrazené znaky zpracovávány jako base64, Hlavička Content-ID ze 4b, Hlavička kódování přenosu obsahu ze 4c, Hlavička Content-Type, pokud vygenerované v kroku 4d.  
  
    6.  Přidat `href` atribut `xop:Include` element s hodnotou cid: identifikátor uri odvozené od hodnota hlavičky Content-ID vygenerované v kroku 4b. Odebrat uzavírací "\<" a ">" znaky adresy URL řídicí zbývající řetězec a přidat předponu `cid:`. Je potřeba předcházet RFC1738 a RFC2396 následující minimální znakovou sadu. Můžete uvozené jiné znaky.  
  
        ```  
        Hexadecimal 00-1F , 7F, 20, "<" | ">" | "#" | "%" | <">  
        "{" | "}" | "|" | "\" | "^" | "[" | "]" | "`" | "~" | "^"  
        ```  
  
5.  Vytvořte Kořenová část MIME s XOP obálku protokolu SOAP z kroku 4.  
  
6.  Zápisu hlavičky protokolu HTTP, včetně hlavičku HTTP Content-Type.  
  
7.  Zápis balíček MIME.  
  
#### <a name="processing-mtom-messages"></a>Zpracování zpráv MTOM  
 Zpracování MTOM zpráva je přesný zpětného procesu popsané v předchozím "generování MTOM zprávy" části:  
  
1.  Ujistěte se, má kořenová část MIME Content-Type `application/xop+xml`.  
  
2.  Vytvořte obálku protokolu SOAP analýzou kořenu MIME součást balíčku jako dokument XML. Kódování znaků je dáno `charset` parametr Content-Type kořenové části MIME.  
  
3.  Pro každou položku informace element v sestavené obálku protokolu SOAP, který má, jako jedinou člen jeho [podřízené položky] vlastnosti, `xop:Include` element informace položky:  
  
    1.  Odeberte `cid:` předpony a unescape všechny URI – řídicí sekvence (RFC 2396) v hodnotě `@href` atribut `xop:Include` elementu. Uzavřete výsledný řetězec v "\<", ">".  
  
    2.  Vyhledejte část MIME s hodnota hlavičky Content-ID, který se shoduje s řetězcem odvozený v krok 3a.  
  
    3.  Nahraďte `xop:Include` položky informace o elementu, který se zobrazí v `children` vlastnost každé položky se položky znak informace, které představují kódování base64 kanonický (viz XSD-2, 3.2.16 pomocí base64Binary) textu entity části standardu MIME v kroku 3b identifikuje (efektivně nahradit `xop:Include` položky informace o elementu s daty znovu vytvořena z součást balíčku).  
  
#### <a name="http-content-type-header"></a>Hlavičku HTTP Content-Type  
 Následuje seznam [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] objasnění, která pro formát hlavičky protokolu HTTP Content-Type kódování MTOM zprávy protokolu SOAP 1.x odvozené od požadavky uvedené v specifikace MTOM sám a jsou odvozené z MTOM a dokumentu RFC 2387.  
  
-   R4131: Hlavičku HTTP Content-Type musí mít hodnotu multipart/related (velká a malá písmena) a jeho parametry. Názvy parametrů jsou velká a malá písmena. Parametr pořadí není důležité.  
  
-   Úplné Backus-Naur formuláře (BNF) hlavičky Content-Type pro zprávy MIME je uvedena v chodu 2045 RFC, část 5.1.  
  
-   R4132: Hlavičku HTTP Content-Type musí mít parametr typu s hodnotou `application/xop+xml` uzavřena v uvozovkách.  
  
 Přestože není definován v dokumentu RFC 2387 požadavek na použijte uvozovky, text dodržuje, že všechny typu multipart/related média parametry nejpravděpodobnější obsahovat vyhrazené znaky jako "@" or "/" a je proto třeba dvojitých uvozovek.  
  
-   R4133: Hlavičku HTTP Content-Type musí mít parametr s hodnotou hlavičku Content-ID části standardu MIME, který obsahuje SOAP 1.x obálky, uzavřena v uvozovkách. Pokud je spuštění parametr vynechán, první část MIME musí obsahovat SOAP 1.x obálku.  
  
-   R4134: Hlavičku HTTP Content-Type pro zprávu protokolu SOAP 1.1 MTOM kódovaný musí obsahovat úvodní informace parametr s hodnotou typu text/xml, uzavřena v uvozovkách.  
  
-   R4135: Hlavičku HTTP Content-Type pro zprávu protokolu SOAP 1.2 MTOM kódováním musí obsahovat úvodní informace parametr s hodnotou `application/soap+xml`, uzavřené v uvozovkách.  
  
-   R4136: Hlavičku HTTP Content-Type pro zprávu protokolu SOAP 1.x kódování MTOM musí mít parametr hranic s hodnotou (uzavřena v uvozovkách), který odpovídá MIME hranice, na které BNF definované v dokumentu RFC 2046 části 5.1.1  
  
    ```  
    boundary := 0*69<bchars> bcharsnospace   
    bchars := bcharsnospace / " "   
    bcharsnospace :=    DIGIT / ALPHA / "'" / "(" / ")" / "+"   
                        / "_" / "," / "-" / "." / "/" / ":" / "=" / "?"  
    ```  
  
     Příklady:  
  
     OPRAVTE  
  
    ```  
    Content-Type: multipart/related; type="application/xop+xml";start=" <part0@tempuri.org>";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1";start-info="text/xml"  
    ```  
  
     OPRAVTE  
  
    ```  
    Content-Type: Multipart/Related; type="application/xop+xml";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"  
    ```  
  
     NESPRÁVNÝ  
  
    ```  
    Content-Type: Multipart/Related; type=application/xop+xml;start=" <part0@tempuri.org>";start-info="text/xml";boundary="uuid:0ca0e16e-feb1-426c-97d8-c4508ada5e82+id=1"   
    ```  
  
#### <a name="infoset-mime-part"></a>Část MIME informační sadu  
 SOAP 1.x obálky je zapouzdřený jako část kořenové XOP MIME balíčku a se často říká `infoset` část.  
  
-   R4141: SOAP 1.x obálky musí zapouzdřené jako část kořenové XOP MIME balíčku, volá se `infoset` část a odkazované z hlavičku HTTP Content-Type.  
  
-   R4142: SOAP `Infoset` část musí zahrnovat následující hlavičky MIME: `Content-ID`, `Content-Transfer-Encoding`, a `Content-Type`.  
  
 Formát hlavičky Content-ID je definované chodu 2045 RFC jako  
  
```  
"Content-ID" ":" msg-id  
```  
  
 kde `msg-id` je definován v dokumentu RFC 2822, (který nahrazuje RFC 822, kterou se odkazuje v chodu 2045 RFC) jako:  
  
```  
msg-id    =       [CFWS] "<" id-left "@" id-right ">" [CFWS]  
```  
  
 a efektivně e-mailovou adresu uzavřena v rámci "\<" a ">". `[CFWS]` Předponu a příponu byly přidány RFC 2822 k provedení komentáře a nesmí se použít k zachování interoperability.  
  
 R4143: Musí následovat hodnota hlavičky Content-ID pro část MIME informační sadu `msg-id` produkční z RFC 2822 s `[CFWS]` předponu a příponu částí tento parametr vynechán.  
  
 Počet implementací MIME zmírnit požadavky pro hodnotu v rámci uzavřené "\<" a ">" jako e-mailovou adresu a použít `absoluteURI` v "\<", ">" Kromě e-mailovou adresu. Tato verze [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] používá hodnoty hlavičky Content-ID MIME ve tvaru:  
  
```  
Content-ID: <http://tempuri.org/0>   
```  
  
 R4144: MTOM procesory musí přijmout záhlaví Content-ID hodnoty, které odpovídají následující zmírnit `msg-id`.  
  
```  
msg-id-relaxed =     [CFWS] "<" (absoluteURI | mail-address) ">" [CFWS]  
mail-address   =     id-left "@" id-right  
```  
  
 MIME (RFC chodu 2045) poskytuje hlavičku kódování přenosu obsahu pro komunikaci, kódování obsahu části standardu MIME. Výchozí hodnota definovaná pro kódování přenosu obsahu je 7 bitů, což není vhodná pro většinu protokolu SOAP zprávy, aby bylo možné hlavičku Content-Transfer-Encoding větší interoperability:  
  
-   R4145: Informační SOAP sadu část musí obsahovat hlavičku kódování přenosu obsahu.  
  
-   R4146: Pokud kódování znaků pro obálku protokolu SOAP je UTF-8, musí být hodnota hlavičky Content-Transfer-Encoding 8 bitů.  
  
-   R4147: Pokud je znak obálku protokolu SOAP kódování UTF-16, hodnota hlavičky kódování přenosu obsahu musí být binární.  
  
-   Závislosti [XOP] část 5,  
  
-   R4148: Informační SOAP1.1 sadu část musí obsahovat hlavičku Content-Type s typ média application/xop + xml a parametry type = "text/xml" a znaková sada  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="text/xml"  
    ```  
  
-   R4149: Část informační SOAP 1.2 sadu musí obsahovat hlavičku Content-Type s typem média `application/xop+xml` a parametry type = "`application/soap+xml`" a `charset`.  
  
    ```  
    Content-Type: application/xop+xml;  
                  charset=utf-8;type="application/soap+xml"  
    ```  
  
     Při definuje XOP `charset` parametr pro `application/xop+xml` jako volitelnou, je potřeba pro spolupráci podobná BP 1.1 požadavek na `charset` parametr pro `text/xml` typ média.  
  
-   R41410: `type` a `charset` parametry musí být v hlavičce Content-Type části informační sadu 1.x protokolu SOAP.  
  
#### <a name="wcf-endpoint-support-for-mtom"></a>Podpora koncový bod WCF MTOM  
 Účelem MTOM je určený ke kódování zprávu protokolu SOAP k optimalizaci data s kódováním base64. Následuje seznam omezení:  
  
-   R4151: Může optimalizovat libovolnou položku informace element, který obsahuje data s kódováním base64.  
  
-   B4152: [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] optimalizuje položky element informace, které obsahují data s kódováním base64 a přesáhnout délku 1024 bajtů.  
  
 A [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod nakonfigurovaný na použití MTOM vždycky odešlou kódování MTOM zprávy. I v případě, že žádné části splňují kritéria požadovaná, zpráva je stále kódování MTOM (serializovat jako balíček MIME s jedné součásti MIME obsahující obálku protokolu SOAP).  
  
### <a name="ws-policy-assertion-for-mtom"></a>Výraz WS-zásad pro MTOM  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Následující výraz zásad se používá k označení MTOM využití pomocí koncového bodu:  
  
```xml  
<wsoma:OptimizedMimeSerialization ... />  
```  
  
-   R4211: Předchozí výraz zásad má subjektu zásad koncového bodu a určuje, že všechny zprávy odesílané do a z koncového bodu musí být optimalizovány s použitím MTOM.  
  
-   B4212: Pokud nakonfigurovaná pro použití MTOM optimalizace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] koncový bod přidá kontrolní výrazy zásad MTOM zásady připojené k odpovídající `wsdl:binding`.  
  
### <a name="composition-with-ws-security"></a>Složení s WS-zabezpečení  
 MTOM je mechanismus kódování, který je podobný `text/xml` a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] binární XML. MTOM nabízí přirozené složení s WS-zabezpečení a jiné WS-* protokoly: zprávu zabezpečené pomocí protokolu WS-zabezpečení lze optimalizovat pomocí MTOM.  
  
### <a name="examples"></a>Příklady  
  
#### <a name="wcf-soap-11-message-encoded-using-mtom"></a>WCF SOAP 1.1 zpráva kódované pomocí MTOM  
  
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
 V tomto příkladu je zpráva kódované pomocí MTOM a SOAP 1.2, který je chráněný pomocí protokolu WS-zabezpečení. Binární části identifikovat pro kódování jsou obsah `BinarySecurityToken`, `CipherValue` z `EncryptedData` odpovídající šifrované podpisu a šifrovaný text. Všimněte si, že `CipherValue` z `EncryptedKey` nebyla určená pro optimalizaci podle [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], protože jeho délka je menší pak 1024 bajtů.  
  
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
