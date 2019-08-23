---
title: Protokoly webových služeb podporované vazbami vzájemné spolupráce poskytnutými systémem
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: 963325604f66ddd4f8470933584b7880c86403bc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69951563"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Protokoly webových služeb podporované vazbami vzájemné spolupráce poskytnutými systémem
Windows Communication Foundation (WCF) je postaven na spolupráci s webovými službami, které podporují sadu specifikací označovaných jako specifikace webových služeb. Pro zjednodušení konfigurace služby pro osvědčené postupy interoperability přináší WCF tři interoperabilní vazby poskytované systémem: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>a <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. Pro interoperabilitu s organizací pro účely standardů OASIS (Structured Information Standards) zahrnuje WCF jednu interoperabilní vazbu poskytovanou systémem: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. V případě publikace metadat zahrnuje WCF dvě interoperabilní vazby poskytované systémem: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) a [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). V tomto tématu je uveden seznam specifikací, které poskytuje podpora vazeb interoperabilních systémem.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Protokoly webových služeb podporované pomocí vazeb basicHttpBinding, wsHttpBinding, ws2007HttpBinding a wsDualHttpBinding  
  
### <a name="all-bindings"></a>Všechny vazby  
 Vazby BasicHttpBinding >, [ \<WSHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)a [ \<WS2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) podporují následující protokoly. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)  
  
> [!NOTE]
> Informace o vazbách použitých k publikování metadat naleznete v části "systémové vazby metadat" dále v tomto tématu.  
  
|Kategorie|Protocol|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Přepravu|HTTP 1,1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding` a`WS2007HttpBinding` použijte přenosy HTTP a HTTPS.|  
|Messaging|MAXIMÁLNÍ|[MTOM](https://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding` a`ws2007HttpBinding` podporují mechanismus pro optimalizaci přenosu zpráv (MTOM). Nepoužívá se ve výchozím nastavení. Chcete-li použít MTOM, `messageEncoding` nastavte atribut `"Mtom"`na.<br /><br /> Příklad:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadata|WSDL 1,1|[WSDL 1,1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> WCF používá k popisu služeb službu Web Services Description Language (WSDL).|  
|Metadata|WS-Policy|[WS-Policy](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> Služba WCF používá specifikace WS-Policy spolu s kontrolními výrazy specifickými pro doménu k popisu požadavků a možností služby.|  
|Metadata|WS-Policy 1,5|[WS-Policy 1,5](https://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> Služba WCF používá specifikace WS-Policy spolu s kontrolními výrazy specifickými pro doménu k popisu požadavků a možností služby.|  
|Metadata|WS-PolicyAttachment|[WS-PolicyAttachment](https://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> WCF implementuje příkazy WS-PolicyAttachment pro připojení výrazů zásad v různých oborech v jazyce WSDL (Web Services Description Language).|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF implementuje WS-MetadataExchange k načtení schématu XML, WSDL a WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategorie|Protocol|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Messaging|PROTOKOL SOAP 1,1|[PROTOKOL SOAP 1,1](https://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> V souladu se základním profilem 1,1 `basicHttpBinding` prvek implementuje protokol zpráv SOAP 1,1.|  
|Zabezpečení|WSS SOAP Message Security 1,0|[WSS SOAP Message Security 1,0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> V souladu se základním profilem `basicHttpBinding` zabezpečení prvek implementuje specifikaci specifikace Web Services Security (WSS) SOAP Message Security 1,0 pro uživatelské jméno/heslo a zabezpečení založené na X. 509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Zabezpečení|WSS SOAP Message Security UsernameToken Profile 1,0|[WSS SOAP Message Security UsernameToken Profile 1,0](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Zabezpečení|WSS SOAP Message Security Security X. 509 – profil tokenu certifikátu 1,0|[WSS SOAP Message Security Security X. 509 – profil tokenu certifikátu 1,0](https://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding, ws2007HttpBinding a wsDualHttpBinding  
  
|Kategorie|Protocol|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Messaging|PROTOKOL SOAP 1,2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Rozhraní pro zasílání zpráv](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (včetně vazby HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Messaging|WS-Addressing 2005/08|[Webové služby Addressing 1,0 – Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Webové služby Addressing 1,0 – SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> Rozhraní `wsHttpBinding`, `ws2007HttpBinding` a`wsDualHttpBinding` implementují doporučení WS-Addressing konsorcium World Wide Web (W3C) pro povolení asynchronního zasílání zpráv, korelace zpráv a mechanismů pro adresování v neutrálním přenosu.<br /><br /> Služba WCF nepodporuje šifrování hlaviček WS-Addressing, přestože jsou povoleny specifikacemi WS-*.|  
|Messaging|WS-Addressing 1,0 – metadata|[Metadata specifikace WS-addressing 1,0](https://www.w3.org/2007/05/addressing/metadata) Podpora pro tento protokol je povolená nastavením verze zásady v oddílu serviceMetadata chování – s PolicyVersion nastavenou na 1,2 (výchozí), popis WSDL je kompatibilní s elementem WS-Addressing WSDL s PolicyVersion nastavenou na 1,5, popis WSDL je kompatibilní s metadaty WS-Addressing.<br /><br /> Služba WCF nepodporuje šifrování hlaviček WS-Addressing, přestože jsou povoleny specifikacemi WS-*.|  
|Zabezpečení|WSS SOAP Message Security 1,0|[WSS SOAP Message Security 1,0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Použijte, pokud `securityMode` je atribut nastaven na "wsSecurityOverHttp" (výchozí) a parametry jsou konfigurovány `wsSecurity` pomocí podřízeného elementu.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Zabezpečení|WSS SOAP Message Security UsernameToken Profile 1,1|[WSS SOAP Message Security UsernameToken Profile 1,0](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> Použijte, pokud `wsSecurity` je `authenticationMode` atribut elementu nastavený na username.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Zabezpečení|WSS SOAP Message Security Security X. 509 – profil tokenu certifikátu 1,1|[WSS SOAP Message Security Security X. 509 – profil tokenu certifikátu 1,1](https://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> Tuto `wsSecurity` možnost použijte pro ochranu zpráv, je `authenticationMode` -li atribut elementu nastaven na "username", "Certificate" nebo "none". Kromě toho použijte tuto možnost pro ověřování klienta, `wsSecurity` Pokud je `authenticationMode` atribut prvku nastaven na "Certificate".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpečení|WSS SOAP Message Security – profil tokenu protokolu Kerberos 1,1|[WSS SOAP Message Security – profil tokenu protokolu Kerberos 1,1](https://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> Používá se pro ověřování a ochranu zpráv, `wsSecurity` když je `authenticationMode` atribut elementu nastavený na Windows.<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpečení|WS-SecureConversation|[WS-SecureConversation](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Slouží k poskytnutí zabezpečené relace, pokud `security/@mode` je atribut nastaven na hodnotu "Message" `message/@establishSecurityContext` a atribut je nastaven na hodnotu "pravda" (výchozí).|  
|Zabezpečení|WS-Trust|[WS-Trust](https://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> Používá se WS-SecureConversation (viz výše).|  
|Spolehlivé zasílání zpráv|WS-ReliableMessaging|[WS-ReliableMessaging](https://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> Použijte, pokud je vazba nakonfigurovaná na `reliableSession`použití.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transakce|WS-AtomicTransaction|[WS-AtomicTransaction](https://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> Používá se pro komunikaci mezi správci transakcí. Klienti a služby WCF používají vždy místní správce transakcí.|  
|Transakce|WS-koordinace|[WS-Coordination](https://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> Slouží k vytvoření toku transakčního kontextu, `flowTransactions` Pokud je atribut nastaven na hodnotu povoleno nebo požadováno.<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding a ws2007FederationHttpBinding  
 WSFederationHttpBinding > a [WS2007FederationHttpBinding prvky > jsou představeny pro zajištění podpory pro federované scénáře, kdy třetí strana vydá token použitý k ověření klienta. \<](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) Kromě protokolů používaných nástrojem `wsHttpBinding` `wsFederationHttpBinding` nástroj využívá:  
  
- `WS-Trust`pro vystavení tokenu.  
  
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
 V následujících tabulkách jsou popsány protokoly podporované systémem, které jsou k dispozici vazby <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> metadat, které poskytuje třída.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 Vazba [ mexHttpBinding>podporujenásledujícíprotokoly.\<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) Další informace o použití této vazby najdete v tématu [publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategorie|Protocol|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Přepravu|HTTP 1,1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)|  
|Messaging|PROTOKOL SOAP 1,2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Rozhraní pro zasílání zpráv](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (včetně vazby HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Messaging|WS-Addressing 2005/08|[Webové služby Addressing 1,0 – Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Webové služby Addressing 1,0 – SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF implementuje WS-MetadataExchange k načtení schématu XML, WSDL a WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 mexHttpsBinding > podporuje následující protokoly. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) Další informace o použití této vazby najdete v tématu [publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategorie|Protocol|Specifikace a použití|  
|--------------|--------------|-----------------------------|  
|Přepravu|HTTP 1,1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> Zabezpečení přenosu je povolené.|  
|Messaging|PROTOKOL SOAP 1,2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Rozhraní pro zasílání zpráv](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (včetně vazby HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Messaging|WS-Addressing 2005/08|[Webové služby Addressing 1,0 – Core](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Webové služby Addressing 1,0 – SOAP](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF implementuje WS-MetadataExchange k načtení schématu XML, WSDL a WS-Policy.|  
  
## <a name="see-also"></a>Viz také:

- [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
