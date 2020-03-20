---
title: Protokoly webových služeb podporované vazbami vzájemné spolupráce poskytnutými systémem
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: a1e67401a09370a46bc7a3e8546c95467bc18b67
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184147"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Protokoly webových služeb podporované vazbami vzájemné spolupráce poskytnutými systémem
Windows Communication Foundation (WCF) je vytvořen a spolupracuje s webovými službami, které podporují sadu specifikací označovaných jako specifikace webových služeb. Pro zjednodušení konfigurace služby pro osvědčené postupy interoperability zavádí WCF tři <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>interoperabilní systémová vazba: , <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>, a <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. Pro interoperabilitu se standardy Organizace pro rozvoj strukturovaných informačních standardů (OASIS) <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>obsahuje WCF jednu interoperabilní systémovou vazbu: . Pro publikování metadat WCF obsahuje dvě interoperabilní systémem poskytované vazby: [ \<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) a [ \<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Toto téma uvádí specifikace, které podporují interoperabilní vazby poskytované systémem.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Protokoly webových služeb podporované základní vazbou HttpBinding, wsHttpBinding, ws2007HttpBinding a wsDualHttpBindingBindingBinding  
  
### <a name="all-bindings"></a>Všechna vázání  
 [ \<Základnívazba>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)a [ \<ws2007HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) vazby podporují následující protokoly.  
  
> [!NOTE]
> Informace o vazbách použitých k publikování metadat naleznete v části "Vazby metadat zajišťovaná systémem" dále v tomto tématu.  
  
|Kategorie|Protocol (Protokol)|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Přenos|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`a `WS2007HttpBinding` použijte přenosy HTTP a HTTPS.|  
|Zasílání zpráv|Mtom|[Mtom](https://www.w3.org/TR/soap12-mtom/)<br /><br /> `basicHttpBinding`, `wsHttpBinding`a `ws2007HttpBinding` podporují mechanismus optimalizace přenosu zpráv (MTOM). Ve výchozím nastavení se nepoužívá. Chcete-li použít mtom, nastavte `messageEncoding` atribut na `"Mtom"`.<br /><br /> Příklad:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadata|WSDL 1,1|[WSDL 1,1](https://www.w3.org/TR/wsdl/)<br /><br /> WCF používá jazyk popisu webových služeb (WSDL) k popisu služeb.|  
|Metadata|Zásady WS|[Zásady WS](https://www.w3.org/Submission/WS-Policy/)<br /><br /> WCF používá ws-policy specifikace spolu s kontrolními výrazy specifické pro doménu k popisu požadavků na služby a schopností.|  
|Metadata|WS-Policy 1,5|[WS-Policy 1,5](https://www.w3.org/TR/2007/CR-ws-policy-20070605/)<br /><br /> WCF používá ws-policy specifikace spolu s kontrolními výrazy specifické pro doménu k popisu požadavků na služby a schopností.|  
|Metadata|Připojení zásad WS|[Připojení zásad WS](http://specs.xmlsoap.org/ws/2004/09/policy/ws-policyattachment.pdf)<br /><br /> WCF implementuje WS-PolicyAttachment připojit výrazy zásad v různých oborech v jazyce popis webových služeb (WSDL).|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implementuje WS-MetadataExchange k načtení schématu XML, WSDL a WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategorie|Protocol (Protokol)|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Zasílání zpráv|MÝDLO 1,1|[MÝDLO 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)<br /><br /> V souladu se základním profilem `basicHttpBinding` 1.1 prvek implementuje protokol zprávy SOAP 1.1.|  
|Zabezpečení|Zabezpečení zprávy SLUŽBY SOAP wss 1.0|[Zabezpečení zprávy SLUŽBY SOAP wss 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> V souladu se základním profilem zabezpečení implementuje `basicHttpBinding` prvek specifikaci Zabezpečení zpráv 1.0 (Zabezpečení zabezpečení zabezpečení webových služeb) (Zabezpečení zabezpečení wss) pro uživatelské jméno/heslo a zabezpečení založené na X.509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Zabezpečení|WSS SOAP Zpráva Zabezpečení UsernameToken Profil 1.0|[WSS SOAP Zpráva Zabezpečení UsernameToken Profil 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Zabezpečení|WSS SOAP zabezpečení zpráv X.509 Profil tokenu certifikátu 1.0|[WSS SOAP zabezpečení zpráv X.509 Profil tokenu certifikátu 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>WsHttpBinding, ws2007HttpBinding a wsDualHttpBinding  
  
|Kategorie|Protocol (Protokol)|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Zasílání zpráv|MÝDLO 1,2|[Základy](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Rozhraní zasílání zpráv](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Doplňky (včetně HTTP vazby)](https://www.w3.org/TR/soap12-part2/)|  
|Zasílání zpráv|WS-Adresování 2005/08|[Web Services Addressing 1.0 - Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Webové služby adresování 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)<br /><br /> `wsHttpBinding`, `ws2007HttpBinding`a `wsDualHttpBinding` implementovat World Wide Web Consortium (W3C) WS adresování doporučení povolit asynchronní zasílání zpráv, korelace zpráv a přenosově neutrální adresování mechanismy.<br /><br /> WCF nepodporuje šifrování ws adresování záhlaví i když je to povoleno specifikace WS-*.|  
|Zasílání zpráv|WS-Adresování 1.0 - Metadata|[WS-Adresování 1.0 Metadata](https://www.w3.org/2007/05/addressing/metadata/) Podpora tohoto protokolu je povolena nastavením verze zásad v ServiceMetadata behavior - s policyversion nastavena na 1.2 (výchozí), WSDL popis je kompatibilní s WS-Addressing wsdl, s policyversion nastavena na 1,5, wsdl popis je kompatibilní s ws adresování metadata.<br /><br /> WCF nepodporuje šifrování ws adresování záhlaví i když je to povoleno specifikace WS-*.|  
|Zabezpečení|Zabezpečení zprávy SLUŽBY SOAP wss 1.0|[Zabezpečení zprávy SLUŽBY SOAP wss 1.0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> Použijte, `securityMode` pokud je atribut nastaven na "wsSecurityOverHttp" (výchozí) `wsSecurity` a parametry jsou konfigurovány pomocí podřízeného prvku.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Zabezpečení|WSS SOAP Message Security UsernameToken Profil 1.1|[WSS SOAP Zpráva Zabezpečení UsernameToken Profil 1.0](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> Použijte, `wsSecurity` když je `authenticationMode` atribut prvku nastaven na "Uživatelské jméno".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Zabezpečení|WSS SOAP zabezpečení zpráv X.509 Profil tokenu certifikátu 1.1|[WSS SOAP zabezpečení zpráv X.509 Profil tokenu certifikátu 1.1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)<br /><br /> Ochrana zpráv slouží `wsSecurity` k ochraně, pokud je `authenticationMode` atribut prvku nastaven na "Uživatelské jméno", "Certifikát" nebo "Žádný". Navíc použijte pro ověřování klienta, `wsSecurity` pokud `authenticationMode` je atribut prvku nastaven na "Certifikát".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpečení|Profil tokenu protokolu Kerberos služby WSS SOAP 1.1|[Profil tokenu protokolu Kerberos služby WSS SOAP 1.1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)<br /><br /> Slouží k ověřování a `wsSecurity` ochraně `authenticationMode` zpráv, pokud je atribut prvku nastaven na "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpečení|WS zabezpečená konverzace|[WS zabezpečená konverzace](http://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> Slouží k poskytnutí zabezpečené `security/@mode` relace, pokud je atribut `message/@establishSecurityContext` nastaven na "Zpráva" a atribut je nastaven na hodnotu "true" (výchozí).|  
|Zabezpečení|WS-Trust|[WS-Trust](http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf)<br /><br /> Používá WS-SecureConversation (viz výše).|  
|Spolehlivé zasílání zpráv|WS-SpolehlivéZasílání zpráv|[WS-SpolehlivéZasílání zpráv](http://specs.xmlsoap.org/ws/2005/02/rm/ws-reliablemessaging.pdf)<br /><br /> Použijte, pokud je vazba nakonfigurována pro použití `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transakce|WS AtomicTransaction|[WS AtomicTransaction](http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)<br /><br /> Slouží pro komunikaci mezi správci transakcí. Klienti a služby WCF vždy používají místní správce transakcí.|  
|Transakce|WS-Koordinace|[WS-Koordinace](https://docs.microsoft.com/previous-versions/ms951231(v=msdn.10))<br /><br /> Slouží k toku kontextu `flowTransactions` transakce, pokud je atribut nastaven na "Povoleno" nebo "Povinné".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>WsFederationHttpBinding a ws2007FederationHttpBinding  
 [ \<WsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a [ \<ws2007FederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) prvky jsou zavedeny poskytovat podporu pro federované scénáře, kde třetí strana vydává token používaný k ověření klienta. Kromě protokolů používaných `wsHttpBinding`v `wsFederationHttpBinding` , pákové efekty:  
  
- `WS-Trust`pro vystavení tokenu.  
  
- WSS Potvrzení zabezpečení Značkovací jazyk (SAML) Profil tokenu 1.0 a 1.1 pro nejčastěji vydaný formát tokenu.  
  
 Příklad:  
  
```xml  
<wsFederationHttpBinding>  
  <binding name="myBinding">  
     <security mode="Message">  
       <message issuedKeyType="Symmetric"
                issuedTokenType="http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1">  
         <issuerMetadata address =
         'http://localhost/FederationSample/HomeRealmSTS/STS.svc/mex'>  
       </message>  
     </security>  
  </binding>  
</wsFederationHttpBinding>  
```  
  
 Další informace naleznete v tématu [Federation](../../../../docs/framework/wcf/feature-details/federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>Vazby metadat poskytované systémem  
 Následující tabulky popisují protokoly podporované systémem poskytované interoperabilní vazby metadat <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> vystavené třídou.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 Vazba [ \<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) podporuje následující protokoly. Další informace o použití této vazby naleznete v [tématu Publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategorie|Protocol (Protokol)|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Přenos|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)|  
|Zasílání zpráv|MÝDLO 1,2|[Základy](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Rozhraní zasílání zpráv](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Doplňky (včetně HTTP vazby)](https://www.w3.org/TR/soap12-part2/)|  
|Zasílání zpráv|WS-Adresování 2005/08|[Web Services Addressing 1.0 - Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Webové služby adresování 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implementuje WS-MetadataExchange k načtení schématu XML, WSDL a WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 mexHttpsBinding>podporuje následující protokoly. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) Další informace o použití této vazby naleznete v [tématu Publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategorie|Protocol (Protokol)|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Přenos|HTTP 1.1|[HTTP 1.1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> Zabezpečení přenosu je povoleno.|  
|Zasílání zpráv|MÝDLO 1,2|[Základy](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Rozhraní zasílání zpráv](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Doplňky (včetně HTTP vazby)](https://www.w3.org/TR/soap12-part2/)|  
|Zasílání zpráv|WS-Adresování 2005/08|[Web Services Addressing 1.0 - Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Webové služby adresování 1.0 - SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implementuje WS-MetadataExchange k načtení schématu XML, WSDL a WS-Policy.|  
  
## <a name="see-also"></a>Viz také

- [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<základní>httpbinding](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<vazby httpbinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<>wsDualHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<>mexHttpsBinding](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<>mexHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
