---
title: Migrace WSE 3.0 Web Services do WCF
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a7e7187eb6ed444ba2c28aa301ce4b3b16129030
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>Migrace WSE 3.0 Web Services do WCF
Výhody migrace WSE 3.0 webových služeb pro [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] zahrnují lepší výkon a podporuje další přenosy, další bezpečnostní scénáře a WS-* specifikace. Webová služba, která je migrována z WSE 3.0, která [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] může mít až 200 až 400 % výkonu v přírůstcích. Další informace o přenosech nepodporuje [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], najdete v části [volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Seznam scénáře podporované nástrojem [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], najdete v části [běžné scénáře zabezpečení](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Seznam specifikace, které jsou podporovány [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], najdete v části [Průvodce interoperabilitou protokolů webových služeb](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 V následujících částech najdete pokyny o tom, jak migrovat WSE 3.0 webové služby pro konkrétní funkci [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
## <a name="general"></a>Obecné  
 WSE 3.0 a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace patří úroveň interoperabilita a společnou sadu terminologie. WSE 3.0 a [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace jsou úroveň umožňuje vzájemnou spolupráci založené na sadu WS-* specifikace, které oba podporují. Když WSE 3.0 nebo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] vyvinutý aplikace je společnou sadu technologiím, jako jsou názvy kontrolní výrazy připraveného zabezpečení ve WSE a režimy ověřování.  
  
 I když jsou mezi mnoha podobné aspekty [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] a technologie ASP.NET nebo WSE 3.0 programovací modely, se liší. Podrobnosti o [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] programovací model, najdete v části [základní programovací životní cyklus](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
>  Migrace WSE webové služby do WCF [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj lze použít ke generování klienta. Tohoto klienta, ale obsahuje rozhraní a třídy, které lze použít jako počáteční bod pro služby WCF příliš. Rozhraní, které se vygenerovaly <xref:System.ServiceModel.OperationContractAttribute> atribut použitý k členům kontrakt s <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> vlastnost nastavena na hodnotu `*`. Když klient WSE volání webové služby s tímto nastavením, je vyvolána následující výjimky: **Web.Services3.ResponseProcessingException: WSE910: došlo k chybě při zpracování zprávy s odpovědí, a můžete najít v vnitřní chyba výjimka**. Toto riziko lze nastavit <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> vlastnost <xref:System.ServiceModel.OperationContractAttribute> atribut jinou hodnotu než`null` hodnotu, jako například `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`.  
  
## <a name="security"></a>Zabezpečení  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>WSE 3.0 webové služby, které jsou zabezpečené pomocí souboru zásad  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby soubor konfigurace můžete použít k zabezpečení služby a že mechanismus je podobný soubor zásad WSE 3.0. Ve WSE 3.0 při zabezpečení webové služby pomocí soubor zásad použijete připraveného security assertion nebo výraz vlastních zásad. Kontrolní výrazy připraveného zabezpečení mapovat úzce režim ověřování [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zabezpečení prvku vazby. Není pouze [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] režimy ověřování a kontrolní výrazy připraveného zabezpečení WSE 3.0 se stejným názvem nebo podobně jejich zabezpečení zprávy pomocí stejné typy přihlašovacích údajů. Například `usernameForCertificate` připraveného security assertion ve WSE 3.0 se mapuje `UsernameForCertificate` režim ověřování v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. Následující příklady kódu ukazují, jak minimální zásadu, která používá `usernameForCertificate` připraveného security assertion ve WSE 3.0 se mapuje `UsernameForCertificate` režim ověřování v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ve vlastní vazby.  
  
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
  
 K migraci nastavení zabezpečení WSE 3.0 Web služby, které jsou určené v soubor zásad, který chcete [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], vlastní vazby je nutné vytvořit v konfiguračním souboru, a to security assertion musí být nastavená na režim ekvivalentní ověřování. Kromě toho musí být vlastní vazby nakonfigurován pro použití v srpnu 2004 specifikaci WS-Addressing Pokud WSE 3.0 klienti komunikují se službou. Když migrovaných [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] služba nevyžaduje komunikaci s klienty WSE 3.0 a musí udržovat pouze paritní zabezpečení, zvažte použití [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] definovaná systémem vazby s příslušná nastavení zabezpečení místo vytvoření vlastní vazba.  
  
 Následující tabulka uvádí mapování mezi soubor zásad WSE 3.0 a jeho ekvivalent vlastní vazby ve [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
|Kontrolní výraz WSE 3.0 to zabezpečení|Konfigurace vlastních vazeb WCF|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security / >|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security / >|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 Další informace o vytváření vlastních vazeb ve službě WCF najdete v tématu [vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>WSE 3.0 webové služby, které jsou zabezpečené pomocí kódu aplikace  
 Jestli WSE 3.0 nebo [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] se používá, požadavky na zabezpečení lze zadat v kódu aplikace místo v konfiguraci. Ve WSE 3.0 toho dosahuje tak, že vytvoříte třídu odvozenou z `Policy` třídy a tím požadavky na přidání voláním `Add` metoda. Další informace o zadávání požadavky na zabezpečení v kódu najdete v tématu [postupy: zabezpečené webové bez službu pomocí souboru zásad](http://go.microsoft.com/fwlink/?LinkId=73747). V [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], abyste mohli určit požadavky na zabezpečení v kódu, vytvořte instanci <xref:System.ServiceModel.Channels.BindingElementCollection> třídu a přidejte instance <xref:System.ServiceModel.Channels.SecurityBindingElement> k <xref:System.ServiceModel.Channels.BindingElementCollection>. Kontrolní výraz požadavky na zabezpečení jsou nastaveny pomocí statické režimu pomocné metody ověřování <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy. Další informace o určení požadavky na zabezpečení v kódu pomocí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], najdete v části [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md) a [postupy: vytvoření elementu SecurityBindingElement pro Zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>Výraz WSE 3.0 vlastních zásad  
 Ve WSE 3.0 existují dva typy kontrolních výrazů vlastních zásad: ty, které zabezpečení zprávu protokolu SOAP a ty, které není zabezpečené zprávu protokolu SOAP. Kontrolní výrazy zásad, které zabezpečené protokolu SOAP zprávy jsou odvozeny od WSE 3.0 `SecurityPolicyAssertion` třídy a koncepční ekvivalent v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy.  
  
 Důležitá poznámka: je, že kontrolní výrazy připraveného zabezpečení WSE 3.0 jsou podmnožinou [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] režimy ověřování. Pokud jste vytvořili vlastní zásady assertion ve WSE 3.0, může být ekvivalentní [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] režim ověřování. Například WSE 3.0 neposkytuje assertion CertificateOverTransport zabezpečení, která se o ekvivalent `UsernameOverTransport` assertion připraveného zabezpečení, ale používá certifikát X.509 pro účely ověření klienta. Pokud jste definovali vlastní výraz vlastních zásad pro tento scénář [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] díky migrace je přehledné. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Definuje režim ověřování pro tento scénář, můžete využít výhod statické ověřování režimu pomocné metody pro konfiguraci [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
 Pokud není k dispozici [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] režim ověřování, který je ekvivalentní assertion vlastní zásady, které slouží k zabezpečení protokolu SOAP zprávy odvození třídy z <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] třídy a zadání ekvivalentní vazby element. Další podrobnosti najdete v tématu [postupy: vytvoření vlastní vazby pomocí elementu SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Převést vlastní zásady kontrolní výraz, který nezabezpečuje zprávu protokolu SOAP, najdete v části [filtrování](../../../../docs/framework/wcf/feature-details/filtering.md) a ukázky [vlastní zachycování zpráv](../../../../docs/framework/wcf/samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>Token WSE 3.0 vlastní zabezpečení  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Programovací model pro vytvoření vlastního tokenu se liší od WSE 3.0. Podrobnosti o vytváření vlastního tokenu ve WSE najdete v tématu [vytváření vlastní tokeny zabezpečení](http://go.microsoft.com/fwlink/?LinkID=73750). Podrobnosti o vytvoření vlastního tokenu v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], najdete v části [postupy: vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>WSE 3.0 vlastní Správce tokenu  
 Programovací model pro vytváření vlastních tokenů manager se liší v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] než WSE 3.0. Podrobnosti o tom, jak vytvořit vlastní tokenu správce a ostatní součásti, které jsou požadovány pro token vlastní zabezpečení najdete v tématu [postupy: vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
>  Pokud jste vytvořili vlastní `UsernameToken` Správce tokenů zabezpečení [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] poskytuje snadný nástroj k určení logiku ověřování než vytváření vlastní zabezpečení Správce tokenu. Další podrobnosti najdete v tématu [postupy: použití vlastní uživatelské jméno a heslo validátoru](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>WSE 3.0 webové služby, které používají MTOM kódování zprávy protokolu SOAP  
 Jako WSE 3 aplikaci, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace můžete zadat zprávu MTOM kódování v konfiguraci. Chcete-li provést migraci tohoto nastavení, přidejte [ \<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) pro vazbu pro danou službu. Následující příklad kódu ukazuje, jak kódování MTOM je zadaný v WSE 3.0 pro službu, která je ekvivalentní v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
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
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>WSE 3.0 aplikací, které používají rozhraní API WSE zasílání zpráv  
 Pokud rozhraní API WSE zasílání zpráv se používá k získat přímý přístup do formátu XML, které informace se předávají mezi klientem a webové služby, aplikace lze převést na použití "Prostý formát XML" (POX). Další podrobnosti o POX najdete v tématu [vzájemná funkční spolupráce s aplikacemi POX](../../../../docs/framework/wcf/feature-details/interoperability-with-pox-applications.md). Další informace o rozhraní API WSE zasílání zpráv najdete v tématu [odesílání a přijímání protokolu SOAP zprávy pomocí WSE zasílání zpráv na úrovni rozhraní API](http://go.microsoft.com/fwlink/?LinkID=73755).  
  
## <a name="transports"></a>Přenosy  
  
### <a name="tcp"></a>TCP  
 Ve výchozím nastavení, klienty WSE 3.0 a webové služby, které odesílají zprávy protokolu SOAP pomocí přenos TCP nespolupracují s [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] klientů a webové služby. Tato nekompatibilita je z důvodu rozdíly v rámcovacích používat v protokolu TCP a z důvodů výkonu. Ale [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] ukázka podrobnosti o tom, jak implementovat vlastní relaci protokolu TCP, které spolupracuje s WSE 3.0. Podrobnosti o této ukázky najdete v tématu [přenos: součinnost TCP ve WSE 3.0](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Chcete-li určit, že [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikace používá přenos TCP, použijte [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Vlastní přenosu  
 Ekvivalent vlastní přenos WSE 3.0 v [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] je rozšíření kanálu. Podrobnosti o vytváření rozšíření pro kanál najdete v tématu [rozšíření vrstvy kanálu](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Viz také  
 [Základní programovací životní cyklus](../../../../docs/framework/wcf/basic-programming-lifecycle.md)  
 [Vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)  
 [Postupy: Vytvoření SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
