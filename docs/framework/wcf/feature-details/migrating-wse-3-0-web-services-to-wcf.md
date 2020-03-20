---
title: Migrace WSE 3.0 Web Services do WCF
ms.date: 03/30/2017
ms.assetid: 7bc5fff7-a2b2-4dbc-86cc-ecf73653dcdc
ms.openlocfilehash: 8f79674350109d111fe263704dee6c40c1a12451
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184567"
---
# <a name="migrating-wse-30-web-services-to-wcf"></a>Migrace WSE 3.0 Web Services do WCF
Mezi výhody migrace webových služeb WSE 3.0 do služby Windows Communication Foundation (WCF) patří zvýšení výkonu a podpora dalších přenosů, další scénáře zabezpečení a specifikace WS-* . Webová služba migrovaná z WSE 3.0 na WCF může zaznamenat zlepšení výkonu až o 200 % až 400 %. Další informace o přenosech podporovaných WCF naleznete v [tématu Výběr přenosu](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md). Seznam scénářů podporovaných wcf naleznete [v tématu běžné scénáře zabezpečení](../../../../docs/framework/wcf/feature-details/common-security-scenarios.md). Seznam specifikací podporovaných wcf naleznete v [tématu Web Services Protocols Interoperability Guide](../../../../docs/framework/wcf/feature-details/web-services-protocols-interoperability-guide.md).  
  
 Následující části obsahují pokyny k migraci konkrétní funkce webové služby WSE 3.0 do wcf.  
  
## <a name="general"></a>Obecné  
 Aplikace WSE 3.0 a WCF zahrnují interoperabilitu na úrovni drátu a společný soubor terminologie. Aplikace WSE 3.0 a WCF jsou interoperabilní na úrovni drátu na základě sady specifikací WS-*, které obě podporují. Při vývoji aplikace WSE 3.0 nebo WCF je společná sada terminologie, jako jsou názvy kontrolnívýrazy zabezpečení na klíč v WSE a režimy ověřování.  
  
 Přestože existuje mnoho podobných aspektů mezi WCF a ASP.NET nebo WSE 3.0 programovací modely, jsou různé. Podrobnosti o programovacím modelu WCF naleznete v [tématu Základní životní cyklus programování](../../../../docs/framework/wcf/basic-programming-lifecycle.md).  
  
> [!NOTE]
> Chcete-li migrovat webovou službu WSE do WCF [nástroj ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) nástroj lze použít ke generování klienta. Tento klient však obsahuje rozhraní a třídy, které lze použít jako výchozí bod pro službu WCF příliš. Rozhraní, které jsou generovány <xref:System.ServiceModel.OperationContractAttribute> mají atribut použít pro členy <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> smlouvy `*`s vlastností nastavenou na . Když klient WSE volá webovou službu s tímto nastavením, je vyvolána následující výjimka: **Web.Services3.ResponseProcessingException: WSE910: Při zpracování zprávy odpovědi došlo k chybě a chybu můžete najít ve vnitřní výjimce**. Chcete-li to <xref:System.ServiceModel.OperationContractAttribute.ReplyAction%2A> zmírnit, <xref:System.ServiceModel.OperationContractAttribute> nastavte vlastnost`null` atributu na `http://Microsoft.WCF.Documentation/ResponseToOCAMethod`hodnotu bez hodnoty, například .  
  
## <a name="security"></a>Zabezpečení  
  
### <a name="wse-30-web-services-that-are-secured-using-a-policy-file"></a>Webové služby WSE 3.0 zabezpečené pomocí souboru zásad  
 WCF služby můžete použít konfigurační soubor k zabezpečení služby a tento mechanismus je podobný souboru zásad WSE 3.0. Ve službě WSE 3.0 při zabezpečení webové služby pomocí souboru zásad použijete kontrolní výraz zabezpečení na klíč nebo vlastní kontrolní výraz zásady. Kontrolní výrazy zabezpečení na klíč mapovat úzce na režim ověřování wcf prvek vazby zabezpečení. Nejen, že jsou režimy ověřování WCF a WSE 3.0 kontrolní výrazy zabezpečení na klíč s názvem stejné nebo podobně, zabezpečují zprávy pomocí stejných typů pověření. Například kontrolní `usernameForCertificate` výraz zabezpečení na klíč ve WSE `UsernameForCertificate` 3.0 mapuje na režim ověřování v WCF. Následující příklady kódu ukazují, jak se `usernameForCertificate` minimální zásada, která používá kontrolní `UsernameForCertificate` výraz zabezpečení na klíč ve WSE 3.0, mapuje na režim ověřování v WCF ve vlastní vazbě.  
  
 **WSE 3,0**  
  
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
  
 Chcete-li migrovat nastavení zabezpečení webové služby WSE 3.0, která jsou určena v souboru zásad do wcf, musí být vytvořena vlastní vazba v konfiguračním souboru a kontrolní výraz zabezpečení na klíč musí být nastaven na ekvivalentní režim ověřování. Kromě toho musí být vlastní vazba nakonfigurována tak, aby používala specifikaci WS-Addressing ze srpna 2004, když klienti WSE 3.0 komunikují se službou. Pokud migrovaná služba WCF nevyžaduje komunikaci s klienty WSE 3.0 a musí pouze udržovat paritu zabezpečení, zvažte použití vazby definované systémem WCF s příslušným nastavením zabezpečení namísto vytvoření vlastní vazby.  
  
 V následující tabulce je uvedeno mapování mezi souborem zásad WSE 3.0 a ekvivalentní vlastní vazbou v wcf.  
  
|Kontrolní výraz zabezpečení WSE 3.0 na klíč|Konfigurace vlastní vazby WCF|  
|----------------------------------------|--------------------------------------|  
|\<uživatelOverTransportSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UserNameOverTransport" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<vzájemnéCertificate10Security />|`<customBinding>   <binding name="MyBinding">     <security messageSecurityVersion="WSSecurity10WSTrustFebruary2005WSSecureConversationFebruary2005WSSecurityPolicy11BasicSecurityProfile10" authenticationMode="MutualCertificate" />     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<usernameForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="UsernameForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<anonymousForCertificateSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="AnonymousForCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<kerberosSecurity />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="Kerberos"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
|\<vzájemnéCertificate11Security />|`<customBinding>   <binding name="MyBinding">     <security authenticationMode="MutualCertificate"/>     <textMessageEncoding messageVersion="Soap12WSAddressingAugust2004" />   </binding> </customBinding>`|  
  
 Další informace o vytváření vlastnívazby v WCF naleznete [v tématu vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
### <a name="wse-30-web-services-that-are-secured-using-application-code"></a>Webové služby WSE 3.0 zabezpečené pomocí kódu aplikace  
 Zda wse 3.0 nebo WCF se používá, požadavky na zabezpečení lze zadat v kódu aplikace namísto v konfiguraci. V WSE 3.0 to je dosaženo vytvořením třídy, která je odvozena `Policy` z `Add` třídy a potom přidáním požadavků voláním metody. Další podrobnosti o určení požadavků na zabezpečení v kódu naleznete v [tématu Postup: Zabezpečení webové služby bez použití souboru zásad](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa528763(v=msdn.10)). V WCF, chcete-li zadat požadavky na <xref:System.ServiceModel.Channels.BindingElementCollection> zabezpečení v kódu, <xref:System.ServiceModel.Channels.SecurityBindingElement> vytvořte <xref:System.ServiceModel.Channels.BindingElementCollection>instanci třídy a přidejte instanci a do . Požadavky kontrolního výrazu zabezpečení jsou nastaveny pomocí <xref:System.ServiceModel.Channels.SecurityBindingElement> pomocných metod režimu statického ověřování třídy. Další podrobnosti o určení požadavků na zabezpečení v kódu pomocí WCF naleznete v [tématu How to: Create a Custom Binding Using the SecurityBindingElement](how-to-create-a-custom-binding-using-the-securitybindingelement.md) and [How to: Create a SecurityBindingElement for a Specified Authentication Mode](how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
### <a name="wse-30-custom-policy-assertion"></a>Kontrolní výraz vlastní ch odvažité zásady WSE 3.0  
 V WSE 3.0 existují dva typy vlastní zásady kontrolní výrazy: ty, které zabezpečují zprávu SOAP a ty, které nezabezpečují zprávu SOAP. Výrazy zásad, které zabezpečují zprávy `SecurityPolicyAssertion` SOAP odvozené z třídy <xref:System.ServiceModel.Channels.SecurityBindingElement> WSE 3.0 a konceptuálního ekvivalentu v WCF, je třída.  
  
 Důležitým bodem je, že wse 3.0 kontrolní výrazy zabezpečení na klíč jsou podmnožinou režimů ověřování WCF. Pokud jste vytvořili vlastní kontrolní výraz zásad y wse 3.0, může být ekvivalentní wcf režim ověřování. Například WSE 3.0 neposkytuje potvrzení zabezpečení CertificateOverTransport, `UsernameOverTransport` který je ekvivalentní kontrolní výraz zabezpečení na klíč, ale používá certifikát X.509 pro účely ověřování klienta. Pokud jste definovali vlastní uplatnění zásad y pro tento scénář, WCF provede migraci přímočarou. WCF definuje režim ověřování pro tento scénář, takže můžete využít metod y pomocníka<xref:System.ServiceModel.Channels.SecurityBindingElement>režimu statického ověřování ke konfiguraci WCF .  
  
 Pokud neexistuje režim ověřování WCF, který je ekvivalentní vlastní výraz zásad, který <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>zabezpečuje zprávy SOAP, odvodit třídu z třídy <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> WCF nebo <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>zadat ekvivalentní prvek vazby. Další podrobnosti naleznete v [tématu How to: Create a Custom Binding Using the SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
 Chcete-li převést vlastní kontrolní výraz zásady, který nezabezpečuje zprávu SOAP, naleznete [v tématu Filtrování](../../../../docs/framework/wcf/feature-details/filtering.md) a [ukázkový vlastní zachycovač zpráv](../../../../docs/framework/wcf/samples/custom-message-interceptor.md).  
  
### <a name="wse-30-custom-security-token"></a>Vlastní token zabezpečení WSE 3.0  
 Programovací model WCF pro vytvoření vlastního tokenu se liší od WSE 3.0. Podrobnosti o vytvoření vlastního tokenu ve WSE naleznete v [tématu Vytváření vlastních tokenů zabezpečení](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529304(v=msdn.10)). Podrobnosti o vytvoření vlastního tokenu v WCF najdete v [tématu Postup: Vytvoření vlastního tokenu](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
### <a name="wse-30-custom-token-manager"></a>Správce vlastních tokenů WSE 3.0  
 Programovací model pro vytvoření správce vlastních tokenů se liší v WCF než WSE 3.0. Podrobnosti o tom, jak vytvořit vlastní správce tokenů a další součásti, které jsou požadovány pro vlastní token zabezpečení, naleznete v [tématu How to: Create a Custom Token](../../../../docs/framework/wcf/extending/how-to-create-a-custom-token.md).  
  
> [!NOTE]
> Pokud jste vytvořili `UsernameToken` vlastní správce tokenů zabezpečení, WCF poskytuje jednodušší mechanismus pro určení logiky ověřování než vytvoření vlastního správce tokenů zabezpečení. Další podrobnosti naleznete v [tématu Postup: Použití vlastního uživatelského jména a validátoru hesla](../../../../docs/framework/wcf/feature-details/how-to-use-a-custom-user-name-and-password-validator.md).  
  
### <a name="wse-30-web-services-that-use-mtom-encoded-soap-messages"></a>Webové služby WSE 3.0, které používají zprávy SOAP kódované mtomem  
 Podobně jako aplikace WSE 3 může aplikace WCF určit kódování zprávy MTOM v konfiguraci. Chcete-li migrovat toto nastavení, přidejte [ \<mtomMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/mtommessageencoding.md) do vazby pro službu. Následující příklad kódu ukazuje, jak je kódování MTOM zadáno ve WSE 3.0 pro službu, která je ekvivalentní v WCF.  
  
 **WSE 3,0**  
  
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
  
### <a name="wse-30-applications-that-use-the-wse-messaging-api"></a>WSE 3.0 Aplikace, které používají WSE Messaging API  

 Pokud wse messaging API slouží k získání přímého přístupu k XML, který je komunikován mezi klientem a webové služby, aplikace může být převedena na použití "Plain Old XML" (POX). Další podrobnosti o POX naleznete [v tématu Interoperabilita s aplikacemi POX](interoperability-with-pox-applications.md). Další podrobnosti o rozhraní WSE Messaging API naleznete v [tématu odesílání a přijímání zpráv SOAP pomocí rozhraní WSE Messaging API](https://docs.microsoft.com/previous-versions/dotnet/netframework-2.0/aa529293(v=msdn.10)).  
  
## <a name="transports"></a>Přenosy  
  
### <a name="tcp"></a>TCP  
 Ve výchozím nastavení klienti WSE 3.0 a webové služby, které odesílají zprávy SOAP pomocí přenosu TCP, nespolupracují s klienty WCF a webovými službami. Tato nekompatibilita je způsobena rozdíly v rámování použitém v protokolu TCP a z důvodů výkonu. Ukázka WCF však podrobně popisuje, jak implementovat vlastní relaci TCP, která spolupracuje s WSE 3.0. Podrobnosti o této ukázce naleznete v [tématu Transport: WSE 3.0 TCP Interoperability](../../../../docs/framework/wcf/samples/transport-wse-3-0-tcp-interoperability.md).  
  
 Chcete-li určit, že aplikace WCF používá přenos TCP, použijte [ \<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
### <a name="custom-transport"></a>Vlastní doprava  
 Ekvivalent WSE 3.0 vlastní přenos v WCF je rozšíření kanálu. Podrobnosti o vytvoření rozšíření kanálu naleznete v [tématu Rozšíření vrstvy kanálu](../../../../docs/framework/wcf/extending/extending-the-channel-layer.md).  
  
## <a name="see-also"></a>Viz také

- [Základní programovací životní cyklus](../../../../docs/framework/wcf/basic-programming-lifecycle.md)
- [Vlastní vazby](../../../../docs/framework/wcf/extending/custom-bindings.md)
- [Postupy: Vytvoření vlastní vazby pomocí SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Postupy: Vytvoření elementu SecurityBindingElement pro zadaný režim ověřování](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
