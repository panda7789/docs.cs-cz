---
title: Protokoly webových služeb podporované vazbami vzájemné spolupráce poskytnutými systémem
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 80fa0e501f425bd5b917059e90f2811f075db651
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746894"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Protokoly webových služeb podporované vazbami vzájemné spolupráce poskytnutými systémem
Windows Communication Foundation (WCF) je postaven na spolupráci s webovými službami, které podporují sadu specifikací označovaných jako specifikace webových služeb. Pro zjednodušení konfigurace služby pro osvědčené postupy interoperability přináší WCF tři interoperabilní vazby poskytované systémem: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>a <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. Pro interoperabilitu s organizací pro účely postupu standardů OASIS (Structured Information Standards) zahrnuje WCF jednu interoperabilní vazbu poskytovanou systémem: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. V případě publikace metadat zahrnuje WCF dvě interoperabilní vazby poskytované systémem: [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) a [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). V tomto tématu je uveden seznam specifikací, které poskytuje podpora vazeb interoperabilních systémem.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Protokoly webových služeb podporované pomocí vazeb basicHttpBinding, wsHttpBinding, ws2007HttpBinding a wsDualHttpBinding  
  
### <a name="all-bindings"></a>Všechny vazby  
 [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)a [\<WS2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) vazby podporují následující protokoly.  
  
> [!NOTE]
> Informace o vazbách použitých k publikování metadat naleznete v části "systémové vazby metadat" dále v tomto tématu.  
  
|Kategorie|Protocol (Protokol)|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Přenos|HTTP 1,1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`a `WS2007HttpBinding` použít přenosy HTTP a HTTPS.|  
|Zasílání zpráv|MAXIMÁLNÍ|[MAXIMÁLNÍ](https://www.w3.org/TR/soap12-mtom/)<br /><br /> `basicHttpBinding`, `wsHttpBinding`a `ws2007HttpBinding` podporují mechanismus pro optimalizaci přenosů zpráv (MTOM). Nepoužívá se ve výchozím nastavení. Chcete-li použít MTOM, nastavte atribut `messageEncoding` na hodnotu `"Mtom"`.<br /><br /> Příklad:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadata|WSDL 1,1|[WSDL 1,1](https://www.w3.org/TR/wsdl/)<br /><br /> WCF používá k popisu služeb službu Web Services Description Language (WSDL).|  
|Metadata|WS-Policy|[WS-Policy](https://www.w3.org/Submission/WS-Policy/)<br /><br /> Služba WCF používá specifikace WS-Policy spolu s kontrolními výrazy specifickými pro doménu k popisu požadavků a možností služby.|  
|Metadata|WS-Policy 1,5|[WS-Policy 1,5](https://www.w3.org/TR/2007/CR-ws-policy-20070605/)<br /><br /> Služba WCF používá specifikace WS-Policy spolu s kontrolními výrazy specifickými pro doménu k popisu požadavků a možností služby.|  
|Metadata|WS-PolicyAttachment|[WS-PolicyAttachment](http://specs.xmlsoap.org/ws/2004/09/policy/ws-policyattachment.pdf)<br /><br /> WCF implementuje příkazy WS-PolicyAttachment pro připojení výrazů zásad v různých oborech v jazyce WSDL (Web Services Description Language).|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implementuje WS-MetadataExchange k načtení schématu XML, WSDL a WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategorie|Protocol (Protokol)|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Zasílání zpráv|PROTOKOL SOAP 1,1|[PROTOKOL SOAP 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)<br /><br /> V souladu se základním profilem 1,1 `basicHttpBinding` prvek implementuje protokol SOAP 1,1 Message Protocol.|  
|Zabezpečení|WSS SOAP Message Security 1,0|[WSS SOAP Message Security 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> V souladu se základním profilem zabezpečení `basicHttpBinding` element implementuje specifikaci specifikace Web Services Security (WSS) SOAP Message Security 1,0 pro uživatelské jméno/heslo a zabezpečení založené na X. 509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Zabezpečení|WSS SOAP Message Security UsernameToken Profile 1,0|[WSS SOAP Message Security UsernameToken Profile 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Zabezpečení|WSS SOAP Message Security Security X. 509 – profil tokenu certifikátu 1,0|[WSS SOAP Message Security Security X. 509 – profil tokenu certifikátu 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding a wsDualHttpBinding  
  
|Kategorie|Protocol (Protokol)|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Zasílání zpráv|PROTOKOL SOAP 1,2|[Základy](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Rozhraní pro zasílání zpráv](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (včetně vazby HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Zasílání zpráv|WS-Addressing 2005/08|[Webové služby Addressing 1,0 – Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Webové služby Addressing 1,0 – SOAP](https://www.w3.org/TR/ws-addr-soap/)<br /><br /> `wsHttpBinding`, `ws2007HttpBinding`a `wsDualHttpBinding` implementují doporučení specifikace WS-Addressing konsorcium World Wide Web (W3C), která umožňuje asynchronní zasílání zpráv, korelace zpráv a mechanizmy adresování v neutrálním přenosu.<br /><br /> Služba WCF nepodporuje šifrování hlaviček WS-Addressing, přestože jsou povoleny specifikacemi WS-*.|  
|Zasílání zpráv|WS-Addressing 1,0 – metadata|[Metadata specifikace WS-addressing 1,0](https://www.w3.org/2007/05/addressing/metadata/) Podpora pro tento protokol je povolená nastavením verze zásady v oddílu serviceMetadata chování – s PolicyVersion nastavenou na 1,2 (výchozí), popis WSDL je kompatibilní s elementem WS-Addressing WSDL s PolicyVersion nastavenou na 1,5, popis WSDL je kompatibilní s metadaty WS-Addressing.<br /><br /> Služba WCF nepodporuje šifrování hlaviček WS-Addressing, přestože jsou povoleny specifikacemi WS-*.|  
|Zabezpečení|WSS SOAP Message Security 1,0|[WSS SOAP Message Security 1,0](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)<br /><br /> Použijte, pokud je atribut `securityMode` nastaven na "wsSecurityOverHttp" (výchozí) a parametry jsou nakonfigurovány pomocí `wsSecurity` podřízeného prvku.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Zabezpečení|WSS SOAP Message Security UsernameToken Profile 1,1|[WSS SOAP Message Security UsernameToken Profile 1,0](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> Použijte, pokud je atribut `authenticationMode` elementu `wsSecurity` nastavený na username.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Zabezpečení|WSS SOAP Message Security Security X. 509 – profil tokenu certifikátu 1,1|[WSS SOAP Message Security Security X. 509 – profil tokenu certifikátu 1,1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)<br /><br /> Tuto možnost použijte pro ochranu zpráv, pokud je atribut `wsSecurity` elementu `authenticationMode` nastaven na "username", "Certificate" nebo "none". Kromě toho použijte tuto možnost pro ověřování klientů, pokud je atribut `authenticationMode` elementu `wsSecurity` nastaven na "Certificate".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpečení|WSS SOAP Message Security – profil tokenu protokolu Kerberos 1,1|[WSS SOAP Message Security – profil tokenu protokolu Kerberos 1,1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)<br /><br /> Používá se pro ověřování a ochranu zpráv, když je atribut `authenticationMode` elementu `wsSecurity` nastavený na Windows.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpečení|WS-SecureConversation|[WS-SecureConversation](http://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> Slouží k poskytnutí zabezpečené relace, pokud je atribut `security/@mode` nastaven na hodnotu "Message" a atribut `message/@establishSecurityContext` je nastaven na hodnotu "true" (výchozí).|  
|Zabezpečení|WS-Trust|[WS-Trust](http://specs.xmlsoap.org/ws/2005/02/trust/ws-trust.pdf)<br /><br /> Používá se WS-SecureConversation (viz výše).|  
|Spolehlivé zasílání zpráv|WS-ReliableMessaging|[WS-ReliableMessaging](http://specs.xmlsoap.org/ws/2005/02/rm/ws-reliablemessaging.pdf)<br /><br /> Použijte, když je vazba nakonfigurovaná tak, aby používala `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transakce|WS-AtomicTransaction|[WS-AtomicTransaction](http://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)<br /><br /> Používá se pro komunikaci mezi správci transakcí. Klienti a služby WCF používají vždy místní správce transakcí.|  
|Transakce|WS-koordinace|[WS-koordinace](https://docs.microsoft.com/previous-versions/ms951231(v=msdn.10))<br /><br /> Slouží k toku kontextu transakce, pokud je atribut `flowTransactions` nastaven na hodnotu povoleno nebo požadováno.<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding a ws2007FederationHttpBinding  
 Pro zajištění podpory pro federované scénáře, kdy třetí strana vydá token, který slouží k ověření klienta, se zavedly [\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a [\<WS2007FederationHttpBinding prvky >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) . Kromě protokolů používaných `wsHttpBinding``wsFederationHttpBinding` využívá:  
  
- `WS-Trust` pro vystavení tokenu  
  
- Profil tokenu protokolu SAML (WSS Security Assert Markup Language) 1,0 a 1,1 pro nejčastěji vydaný formát tokenu.  
  
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
  
 Další informace najdete v tématu [federace](../../../../docs/framework/wcf/feature-details/federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>Vazby metadat poskytovaných systémem  
 V následujících tabulkách jsou popsány protokoly podporované systémem poskytované vazby metadat, které jsou zpřístupněny <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> třídou.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 Vazba [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) podporuje následující protokoly. Další informace o použití této vazby najdete v tématu [publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategorie|Protocol (Protokol)|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Přenos|HTTP 1,1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)|  
|Zasílání zpráv|PROTOKOL SOAP 1,2|[Základy](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Rozhraní pro zasílání zpráv](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (včetně vazby HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Zasílání zpráv|WS-Addressing 2005/08|[Webové služby Addressing 1,0 – Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Webové služby Addressing 1,0 – SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implementuje WS-MetadataExchange k načtení schématu XML, WSDL a WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) podporuje následující protokoly. Další informace o použití této vazby najdete v tématu [publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategorie|Protocol (Protokol)|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Přenos|HTTP 1,1|[HTTP 1,1](https://www.ietf.org/rfc/rfc2616.txt)<br /><br /> Zabezpečení přenosu je povolené.|  
|Zasílání zpráv|PROTOKOL SOAP 1,2|[Základy](https://www.w3.org/TR/soap12-part0/)<br /><br /> [Rozhraní pro zasílání zpráv](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)<br /><br /> [Adjuncts (včetně vazby HTTP)](https://www.w3.org/TR/soap12-part2/)|  
|Zasílání zpráv|WS-Addressing 2005/08|[Webové služby Addressing 1,0 – Core](https://www.w3.org/TR/ws-addr-core/)<br /><br /> [Webové služby Addressing 1,0 – SOAP](https://www.w3.org/TR/ws-addr-soap/)|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](http://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)<br /><br /> WCF implementuje WS-MetadataExchange k načtení schématu XML, WSDL a WS-Policy.|  
  
## <a name="see-also"></a>Viz také

- [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
