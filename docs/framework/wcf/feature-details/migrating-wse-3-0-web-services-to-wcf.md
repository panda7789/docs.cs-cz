---
title: Migrace WSE 3.0 Web Services do WCF
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 21e36be178bb0dd0c52213d8c4c1387a564a0e5a
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43779809"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>Migrace WSE 3.0 Web Services do WCF
Výhody migrace WSE 3.0 Web services na Windows Communication Foundation (WCF) zahrnují lepší výkon a podporu další přenosy, další bezpečnostní scénáře a WS-* specifikace. Webová služba, která je migrována z WSE 3.0 na WCF může docházet k až k 200 až 400 % zlepšení výkonu. Další informace o přenosech podporované službou WCF najdete v tématu [volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Seznam scénáře podporované službou WCF najdete v tématu [běžné scénáře zabezpečení](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Seznam specifikací, které jsou podporovány službou WCF najdete v tématu [Průvodce interoperabilitou protokolů webových služeb](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 Následující části obsahují pokyny o tom, jak migrovat konkrétní funkce WSE 3.0 webovou službu WCF.  
  
## <a name="general"></a>Obecné  
 Aplikace WSE 3.0 a WCF patří přenosový interoperability a společnou sadu terminologie. Jsou aplikace WSE 3.0 a WCF přenosový interoperabilní založené na sadě WS-* specifikace, které obě podporují. Když se vyvíjí aplikace WSE 3.0 nebo WCF není společnou sadu terminologie, jako jsou názvy kontrolní výrazy na klíč zabezpečení ve WSE a režimů ověřování.  
  
 I když jsou podobné aspektech mezi WCF a ASP.NET nebo WSE 3.0 programovací modely, jsou odlišné. Podrobnosti o tomto programovacím modelu WCF najdete v tématu [základní programovací životní cyklus](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
>  Migrace WSE webové služby WCF [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj můžete použít ke generování klienta. Klient ale obsahuje rozhraní a třídy, které lze použít jako počáteční bod pro služby WCF příliš. Rozhraní, které jsou generovány <xref:System.ServiceModel.OperationContractAttribute> atribut použitý k členům kontrakt s <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> nastavenou na `*`. Když klient WSE volá webová služba s tímto nastavením, je vyvolána následující výjimka: **Web.Services3.ResponseProcessingException: WSE910: došlo k chybě při zpracování zprávy s odpovědí a chyby najdete ve vnitřní výjimka**. Chcete-li tento problém zmírnit, nastavte <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> vlastnost <xref:System.ServiceModel.OperationContractAttribute> atribut non-`null` hodnoty, jako například `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`.  
  
## <a name="security"></a>Zabezpečení  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>WSE 3.0 webové služby, které jsou zabezpečené pomocí zásad souboru  
 Služby WCF můžete použít konfigurační soubor pro zabezpečení služby a tento mechanismus je podobný soubor zásad WSE 3.0. Při zabezpečování webové služby s použitím souboru zásad WSE 3.0 použijete kontrolní výraz na klíč zabezpečení nebo kontrolní výraz vlastní zásady. Kontrolní výrazy na klíč zabezpečení úzce namapovat na režim ověřování elementu vazby zabezpečení WCF. Nejen jsou režimy ověřování WCF a kontrolní výrazy ve WSE 3.0 na klíč zabezpečení se stejným názvem nebo podobně, jsou zabezpečené zprávy pomocí stejné typy přihlašovacích údajů. Například `usernameForCertificate` kontrolního výrazu zabezpečení na klíč ve službě WSE 3.0 se mapuje `UsernameForCertificate` režim ověřování ve službě WCF. Následující příklady kódu ukazují, jak minimální zásadu, která se používá `usernameForCertificate` kontrolního výrazu zabezpečení na klíč ve službě WSE 3.0 se mapuje `UsernameForCertificate` režim ověřování ve službě WCF v vlastní vazby.  
  
 **WSE 3.0**  
  
```xml  
<policies>  
  <policy name="MyPolicy">  
    <usernameForCertificate messageProtectionOrder="SignBeforeEncrypt"  
                            requireDeriveKeys="true"/>  
  </policy>  
</policies>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <security authenticationMode="UserNameForCertificate"   
              messageProtectionOrder="SignBeforeEncrypt"  
              requireDerivedKeys="true"/>  
  </binding>  
</customBinding>  
```  
  
 Chcete-li migrovat nastavení zabezpečení ve WSE 3.0 webové služby, které jsou uvedeny v souboru zásad do WCF, musí být vytvořený vlastní vazby v konfiguračním souboru a kontrolní výraz na klíč zabezpečení musí být nastaveno na její ekvivalentní ověřování režimu. Kromě toho vlastní vazby musí být nakonfigurován pro použití ze srpna 2004 specifikace WS-Addressing, pokud WSE 3.0 klienti komunikují se službou. Když nevyžaduje komunikaci s klienty WSE 3.0 a musí udržovat pouze zabezpečení parity migrované služby WCF, zvažte použití vazby WCF definované v systému s příslušná bezpečnostní nastavení místo vytvoření vlastní vazby.  
  
 Následující tabulka uvádí mapování mezi soubor zásad WSE 3.0 a ekvivalentní vlastní vazby ve službě WCF.  
  
|Kontrolní výraz WSE 3.0 na klíč zabezpečení|Konfigurace vlastních vazeb WCF|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security / >|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 Další informace o vytváření vlastních vazeb ve službě WCF najdete v tématu [vlastních vazeb](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>WSE 3.0 webové služby, které jsou zabezpečené pomocí kódu aplikace  
 Jestli se používá ve WSE 3.0 nebo WCF, požadavky na zabezpečení lze zadat v aplikačním kódu místo v konfiguraci. Ve službě WSE 3.0 toho dosahuje tím, že vytvoříte třídu, která je odvozena z `Policy` třídy a tím požadavky na přidání voláním `Add` metoda. Další informace o určení požadavků na zabezpečení v kódu, naleznete v tématu [postupy: zabezpečené webové služby bez použití do souboru zásad](https://go.microsoft.com/fwlink/?LinkId=73747). Ve službě WCF, chcete-li určit požadavky na zabezpečení v kódu, vytvoření instance <xref:System.ServiceModel.Channels.BindingElementCollection> třídu a přidejte instance <xref:System.ServiceModel.Channels.SecurityBindingElement> k <xref:System.ServiceModel.Channels.BindingElementCollection>. Požadavky na zabezpečení kontrolního výrazu jsou nastaveny pomocí statické ověření režimu pomocných metod třídy <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy. Další informace o určení požadavků na zabezpečení v kódu pomocí technologie WCF najdete v tématu [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md) a [postupy: vytvoření elementu SecurityBindingElement pro zadaný Režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>Kontrolní výraz WSE 3.0 vlastních zásad  
 Ve službě WSE 3.0 jsou dva typy kontrolních výrazů vlastních zásad: ty, které zabezpečení zprávy protokolu SOAP a ty, které nezabezpečíte zprávu protokolu SOAP. Kontrolní výrazy zásad zabezpečení zprávy protokolu SOAP odvozovat WSE 3.0 `SecurityPolicyAssertion` třídy a koncepční ekvivalent ve službě WCF je <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy.  
  
 Důležitá poznámka: je, že kontrolní výrazy ve WSE 3.0 na klíč zabezpečení jsou podskupinou režimů ověřování WCF. Pokud vytvoříte kontrolní výraz vlastní zásady ve WSE 3.0, může být ekvivalentní režim ověřování WCF. Například WSE 3.0 neposkytuje kontrolní výraz CertificateOverTransport zabezpečení, který je ekvivalentní k `UsernameOverTransport` kontrolního výrazu zabezpečení na klíč, ale používá certifikát X.509 pro účely ověřování klienta. Pokud jste definovali vlastní kontrolní výraz vlastní zásady pro tento scénář, WCF provede migraci jednoduché. WCF definuje režim ověřování pro tento scénář, takže můžete využít ověřování statické metody helper režimu konfigurace WCF<xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
 Když není režim ověřování WCF, která je ekvivalentní k vlastní zásady pro kontrolní výraz, který zabezpečuje zprávy protokolu SOAP, odvoďte třídu z <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>WCF třídy a určit element ekvivalentní vazby. Další podrobnosti najdete v tématu [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Převést vlastní zásady pro kontrolní výraz, který nezabezpečuje zprávu protokolu SOAP, najdete v článku [filtrování](../../../../docs/framework/wcf/feature-details/filtering.md) a ukázku [vlastní zachycování zpráv](../../../../docs/framework/wcf/samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>WSE 3.0 vlastní bezpečnostní Token  
 Programovacího modelu WCF pro vytvoření vlastního tokenu se liší od WSE 3.0. Podrobnosti o vytvoření vlastního tokenu ve WSE najdete v tématu [vytváření vlastní tokeny zabezpečení](https://go.microsoft.com/fwlink/?LinkID=73750). Podrobnosti o vytvoření vlastního tokenu ve službě WCF najdete v tématu [postupy: vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 vlastní Správce tokenů  
 Programovací model pro vytvoření vlastního správce tokenů se liší ve službě WCF než WSE 3.0. Podrobnosti o tom, jak vytvořit vlastní Správce tokenů a další součásti, které jsou požadovány pro vlastní bezpečnostní token, naleznete v tématu [postupy: vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
>  Pokud jste si vytvořili vlastní `UsernameToken` Správce tokenů zabezpečení WCF poskytuje mechanismus pro snazší zadat logiku ověřování než vytvoření vlastního zabezpečení Správce tokenů. Další podrobnosti najdete v tématu [postupy: použití vlastní uživatelské jméno a heslo validátoru](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>WSE 3.0 webové služby, které používají MTOM kódování zprávy protokolu SOAP  
 Jako WSE 3 aplikace můžete určit aplikace WCF zprávu MTOM kódování v konfiguraci. Chcete-li provést migraci tohoto nastavení, přidejte [ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) vazby pro službu. Následující příklad kódu ukazuje, jak kódování MTOM určen ve WSE 3.0 pro službu, která je ekvivalentní ve službě WCF.  
  
 **WSE 3.0**  
  
```xml  
<messaging>  
    <mtom clientMode="On"/>  
</messaging>  
```  
  
 **WCF**  
  
```xml  
<customBinding>  
  <binding name="MyBinding">  
    <mtomMessageEncoding/>  
  </binding>  
</customBinding>  
```  
  
## <a name="messaging"></a>Zasílání zpráv  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>WSE 3.0 aplikace, který pomocí rozhraní API zasílání zpráv ve WSE  
 Při použití rozhraní API zasílání zpráv ve WSE získat přímý přístup do formátu XML, které jsou předávány mezi klientem a webovou službu aplikace lze převést na použití "Plain Old XML" (POX). Další podrobnosti o POX najdete v tématu [vzájemná funkční spolupráce s aplikacemi POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md). Další podrobnosti o rozhraní API zasílání zpráv ve WSE najdete v tématu [odesílání a příjem zpráv pomocí WSE zasílání zpráv rozhraní API protokolu SOAP](https://go.microsoft.com/fwlink/?LinkID=73755).  
  
## <a name="transports"></a>Přenosy  
  
### <a name="tcp"></a>TCP  
 Ve výchozím nastavení klienty WSE 3.0 a webové služby, které odesílání zpráv SOAP s použitím přenosu protokolu TCP nespolupracují s klienty WCF a webových služeb. K této nekompatibilitě je z důvodu rozdílů v rámce v protokolu TCP a z důvodů výkonu. Ale Ukázky WCF podrobně popisuje, jak implementovat vlastní relace TCP, který spolupracuje s WSE 3.0. Podrobnosti o této ukázce najdete v tématu [přenos: součinnost TCP ve WSE 3.0](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Chcete-li určit, který používá aplikace WCF přenosu protokolu TCP, použijte [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Vlastní přenosu  
 Ekvivalent WSE 3.0 vlastní přenos ve službě WCF je rozšířením kanálu. Podrobnosti o vytváření rozšíření pro kanál najdete v tématu [rozšíření vrstvy kanálu](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Viz také  
 [Základní programovací životní cyklus](../../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Postupy: Vytvoření SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
