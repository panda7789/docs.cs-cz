---
title: Migrace WSE 3.0 Web Services do WCF
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 50939253027ff82a256b9627305c26fb69e13be9
ms.sourcegitcommit: 09b4090b78f52fd09b0e430cd4b26576f1fdf96e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/17/2020
ms.locfileid: "76212148"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>Migrace WSE 3.0 Web Services do WCF
Výhody migrace webových služeb WSE 3,0 na Windows Communication Foundation (WCF) zahrnují Vylepšený výkon a podporu dalších přenosů, další scénáře zabezpečení a specifikace WS-*. Webová služba, která je migrována z WSE 3,0 na technologii WCF, může vyskytnout až 200% a 400 zvýšení výkonu. Další informace o přenosech podporovaných službou WCF najdete v tématu [Volba přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Seznam scénářů podporovaných službou WCF najdete v tématu [běžné scénáře zabezpečení](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Seznam specifikací podporovaných službou WCF najdete v tématu [Průvodce interoperabilitou protokolů webových služeb](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 Následující části obsahují pokyny k migraci konkrétní funkce webové služby WSE 3,0 na WCF.  
  
## <a name="general"></a>Obecné  
 WSE 3,0 a aplikace WCF zahrnují interoperabilitu na úrovni drátu a společnou sadu terminologie. WSE 3,0 a aplikace WCF jsou interoperabilní na úrovni drátu na základě sady specifikací WS-*, které obě podporují. Když je vyvíjena aplikace WSE 3,0 nebo WCF, je k dispozici společná sada terminologie, například názvy klíč kontrolních výrazů zabezpečení v WSE a v režimech ověřování.  
  
 I když mezi programovacími modely WCF a ASP.NET nebo WSE 3,0 existuje mnoho podobných aspektů, jsou různé. Podrobnosti o programovacím modelu WCF najdete v tématu [životní cyklus základního programování](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
> K migraci webové služby WSE do WCF můžete použít nástroj [Svcutil. exe (. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) k vygenerování klienta. Tento klient však obsahuje rozhraní a třídy, které lze použít jako výchozí bod pro službu WCF. Rozhraní, která jsou generována, mají atribut <xref:System.ServiceModel.OperationContractAttribute> použit u členů kontraktu s vlastností <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> nastavenou na hodnotu `*`. Když klient WSE volá webovou službu s tímto nastavením, vyvolá se tato výjimka: **Web. Services3. ResponseProcessingException: WSE910: během zpracování zprávy odpovědi došlo k chybě a v vnitřní výjimce**se zobrazí chyba. Chcete-li toto omezení zmírnit, nastavte vlastnost <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> atributu <xref:System.ServiceModel.OperationContractAttribute> na hodnotu, která není`null`, například `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`.  
  
## <a name="security"></a>Zabezpečení –  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Webové služby WSE 3,0, které jsou zabezpečené pomocí souboru zásad  
 Služby WCF můžou použít konfigurační soubor k zabezpečení služby a tento mechanismus je podobný souboru zásad WSE 3,0. V WSE 3,0 při zabezpečení webové služby pomocí souboru zásad použijte kontrolní výraz zabezpečení klíč nebo vlastní kontrolní výraz zásady. Kontrolní výrazy zabezpečení klíč se úzce mapují do režimu ověřování elementu vazby zabezpečení WCF. Pouze režimy ověřování WCF a kontrolní výrazy zabezpečení WSE 3,0 klíč s názvem stejné nebo podobně zabezpečují zprávy pomocí stejných typů přihlašovacích údajů. Například kontrolní výraz zabezpečení `usernameForCertificate` klíč v WSE 3,0 se mapuje do režimu ověřování `UsernameForCertificate` ve službě WCF. Následující příklady kódu ukazují, jak minimální zásada, která používá kontrolní výraz zabezpečení `usernameForCertificate` klíč v WSE 3,0, se mapuje do režimu ověřování `UsernameForCertificate` ve WCF ve vlastní vazbě.  
  
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
  
 Chcete-li migrovat nastavení zabezpečení webové služby WSE 3,0, které jsou zadány v souboru zásad do služby WCF, je nutné vytvořit vlastní vazbu v konfiguračním souboru a kontrolní výraz zabezpečení klíč musí být nastaven na odpovídající režim ověřování. Kromě toho musí být vlastní vazba nakonfigurovaná tak, aby používala specifikaci WS-Addressing ze srpna 2004, když klienti WSE 3,0 komunikují se službou. Pokud migrovaná služba WCF nevyžaduje komunikaci s klienty WSE 3,0 a musí zachovat jenom paritu zabezpečení, zvažte použití vazeb definovaných systémem WCF s odpovídajícím nastavením zabezpečení namísto vytvoření vlastní vazby.  
  
 Následující tabulka uvádí mapování mezi souborem zásad WSE 3,0 a ekvivalentní vlastní vazbou ve službě WCF.  
  
|Kontrolní výraz zabezpečení WSE 3,0 klíč|Konfigurace vlastní vazby WCF|  
|----------------------------------------|--------------------------------------|  
|\<usernameOverTransportSecurity/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate10Security/>|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<mutualCertificate11Security/>|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 Další informace o vytváření vlastních vazeb v technologii WCF najdete v tématu [Custom Bindings](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Webové služby WSE 3,0, které jsou zabezpečené pomocí kódu aplikace  
 Bez ohledu na to, jestli se používá WSE 3,0 nebo WCF, se požadavky na zabezpečení dají zadat v kódu aplikace, ne v konfiguraci. V WSE 3,0 je to provedeno vytvořením třídy, která je odvozena z třídy `Policy` a následně přidáním požadavků voláním metody `Add`. Další informace o tom, jak zadat požadavky na zabezpečení v kódu, naleznete v tématu [How to: Security a Web Service bez použití souboru zásad](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa528763(v=msdn.10)). V rámci služby WCF pro určení požadavků na zabezpečení v kódu vytvořte instanci třídy <xref:System.ServiceModel.Channels.BindingElementCollection> a přidejte do <xref:System.ServiceModel.Channels.BindingElementCollection>instanci <xref:System.ServiceModel.Channels.SecurityBindingElement>. Požadavky kontrolního výrazu zabezpečení jsou nastaveny pomocí pomocných metod režimu statického ověřování třídy <xref:System.ServiceModel.Channels.SecurityBindingElement>. Další informace o tom, jak zadat požadavky na zabezpečení v kódu pomocí WCF, naleznete v tématu [How to: Create a Custom Binding using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md) a [Postupy: Create a SecurityBindingElement pro zadaný režim ověřování](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>Kontrolní výraz vlastní zásady WSE 3,0  
 V WSE 3,0 existují dva typy kontrolních výrazů vlastní zásady: ty, které zabezpečují zprávu SOAP a ty, které nezabezpečují zprávu SOAP. Kontrolní výrazy zásad, které zabezpečují zprávy protokolu SOAP ze třídy WSE 3,0 `SecurityPolicyAssertion` a koncepční ekvivalent v technologii WCF je <xref:System.ServiceModel.Channels.SecurityBindingElement> třídy.  
  
 Důležité je Ukázat, že kontrolní výrazy zabezpečení WSE 3,0 klíč jsou podmnožinou režimů ověřování WCF. Pokud jste vytvořili kontrolní výraz vlastní zásady v WSE 3,0, může to být ekvivalentní režim ověřování WCF. Například WSE 3,0 neposkytuje kontrolní výraz zabezpečení CertificateOverTransport, který je ekvivalentem `UsernameOverTransport` kontrolního výrazu zabezpečení klíč, ale používá certifikát X. 509 pro účely ověřování klientů. Pokud jste pro tento scénář definovali vlastní kontrolní výraz zásad, WCF migraci zjednoduší. WCF definuje režim ověřování pro tento scénář, takže můžete využít pomocné metody režimu statického ověřování ke konfiguraci<xref:System.ServiceModel.Channels.SecurityBindingElement>WCF.  
  
 Pokud neexistuje režim ověřování WCF, který je ekvivalentní k kontrolnímu výrazu vlastní zásady, který zabezpečuje zprávy protokolu SOAP, odvozuje třídu od <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> nebo <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>třídy WCF a zadejte ekvivalentní prvek vazby. Další podrobnosti najdete v tématu [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Chcete-li převést kontrolní výraz vlastní zásady, který nezabezpečuje zprávu protokolu SOAP, přečtěte si téma [filtrování](../../../../docs/framework/wcf/feature-details/filtering.md) a ukázka [vlastního zachytávací zpráv](../../../../docs/framework/wcf/samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>Vlastní token zabezpečení WSE 3,0  
 Programovací model WCF pro vytvoření vlastního tokenu se liší od WSE 3,0. Podrobnosti o vytvoření vlastního tokenu v WSE najdete v tématu [vytváření vlastních tokenů zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529304(v=msdn.10)). Podrobnosti o vytvoření vlastního tokenu ve službě WCF najdete v tématu [How to: Create a Custom Token](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>Správce vlastního tokenu WSE 3,0  
 Programovací model pro vytvoření vlastního správce tokenů se liší v WCF než WSE 3,0. Podrobnosti o tom, jak vytvořit vlastního správce tokenů a další součásti, které jsou potřeba pro vlastní token zabezpečení, najdete v tématu [How to: Create a Custom Token](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
> Pokud jste vytvořili vlastního správce tokenů zabezpečení `UsernameToken`, WCF vám usnadní mechanizmus určení logiky ověřování než vytvoření vlastního správce tokenů zabezpečení. Další podrobnosti najdete v tématu [Postupy: použití vlastního validátoru uživatelského jména a hesla](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>Webové služby WSE 3,0 používající zprávy protokolu SOAP kódované pomocí MTOM  
 Podobně jako aplikace WSE 3 může aplikace WCF určit kódování zprávy MTOM v konfiguraci. Chcete-li toto nastavení migrovat, přidejte do vazby pro službu [\<mtomMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) . Následující příklad kódu ukazuje, jak je kódování MTOM zadáno v WSE 3,0 pro službu, která je ekvivalentem služby WCF.  
  
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
  
## <a name="messaging"></a>Messaging  
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>Aplikace WSE 3,0, které používají rozhraní API pro zasílání zpráv WSE  

 Pokud se k získání přímého přístupu k souboru XML, který komunikuje mezi klientem a webovou službou, používá rozhraní API pro zasílání zpráv WSE, může být aplikace převedena tak, aby používala "obyčejné staré XML" (POX). Další podrobnosti o POX najdete v tématu [interoperabilita s aplikacemi POX](interoperability-with-pox-applications.md). Další informace o rozhraní API pro zasílání zpráv WSE najdete v tématu [odesílání a příjem zpráv SOAP pomocí rozhraní API pro zasílání zpráv WSE](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529293(v=msdn.10)).  
  
## <a name="transports"></a>Přenosy  
  
### <a name="tcp"></a>TCP  
 Ve výchozím nastavení klienti a webové služby WSE 3,0, které odesílají zprávy protokolu SOAP pomocí přenosového protokolu TCP, nespolupracují s klienty WCF a webovými službami. Tato nekompatibilita je způsobená rozdíly v rámcích používaných v protokolu TCP a z důvodů výkonu. Ukázka služby WCF ale podrobně popisuje, jak implementovat vlastní relaci TCP, která spolupracuje s WSE 3,0. Podrobnosti o této ukázce najdete v tématu [přenos: interoperabilita TCP WSE 3,0](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Chcete-li určit, že aplikace WCF používá přenos TCP, použijte [\<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Vlastní přenos  
 Ekvivalentem vlastního přenosu WSE 3,0 v rámci WCF je rozšíření kanálu. Podrobnosti o vytváření rozšíření kanálu najdete v tématu [rozšíření vrstvy kanálu](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Viz také:

- [Základní programovací životní cyklus](../../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [Vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Postupy: Vytvoření SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
