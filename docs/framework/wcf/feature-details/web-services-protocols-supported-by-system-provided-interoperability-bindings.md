---
title: Protokoly webových služeb podporované vazbami vzájemné spolupráce poskytnutými systémem
ms.date: 03/30/2017
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
ms.openlocfilehash: b77e0bf52e20ce5bd8f1c0deecfc822e9f910675
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64648375"
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Protokoly webových služeb podporované vazbami vzájemné spolupráce poskytnutými systémem
Windows Communication Foundation (WCF) je určený pro spolupráci s webovými službami, které podporují sadu specifikace říká specifikací webových služeb. Pokud chcete zjednodušit konfiguraci služby pro spolupráci osvědčené postupy, WCF zavádí tři interoperabilní vazby poskytované systémem: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>, a <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. WCF pro spolupráci s organizací standardů rozvoj z strukturovaných informace standardy OASIS (Organization) zahrnuje jeden interoperabilní vazeb poskytovaných systémem: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. Metadata publikace WCF obsahuje dvě interoperabilní vazby poskytované systémem: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) a [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Toto téma obsahuje seznam specifikace, které podporují interoperabilní vazby poskytované systémem.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Webové služby protokoly podporované vazbami basicHttpBinding, wsHttpBinding, ws2007HttpBinding a wsDualHttpBinding  
  
### <a name="all-bindings"></a>Všechny vazby  
 [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), a [ \<ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) podporu vazeb ve službě Tyto protokoly.  
  
> [!NOTE]
>  Informace o vazbách k publikování metadat naleznete v části "Metadata vazeb System-Provided" dále v tomto tématu.  
  
|Kategorie|Protocol (Protokol)|Specifikace a využití|  
|--------------|--------------|-----------------------------|  
|Přenos|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`, a `WS2007HttpBinding` použít přenosy HTTP a HTTPS.|  
|Zasílání zpráv|MTOM|[MTOM](https://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding`, a `ws2007HttpBinding` podporují zpráv přenosu optimalizace mechanismus (MTOM). Nepoužívá se ve výchozím nastavení. Chcete-li použít MTOM, nastavte `messageEncoding` atribut `"Mtom"`.<br /><br /> Příklad:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadata|WSDL 1.1|[WSDL 1.1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> WCF webové služby WSDL (Description Language) používá k popisu služby.|  
|Metadata|WS-Policy|[WS-Policy](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> WCF používá k popisu služby požadavky a možnostmi specifikaci WS-Policy spolu s kontrolní výrazy specifického pro doménu.|  
|Metadata|1.5 WS-Policy|[1.5 WS-Policy](https://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> WCF používá k popisu služby požadavky a možnostmi specifikaci WS-Policy spolu s kontrolní výrazy specifického pro doménu.|  
|Metadata|WS-PolicyAttachment|[WS-PolicyAttachment](https://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> WCF implementuje WS-PolicyAttachment připojit výrazy zásad v různých oborech v webové služby WSDL (Description Language).|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF implementuje WS-MetadataExchange pro načtení schématu XML, WSDL a WS-Policy.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategorie|Protocol (Protokol)|Specifikace a využití|  
|--------------|--------------|-----------------------------|  
|Zasílání zpráv|PROTOKOL SOAP 1.1|[PROTOKOL SOAP 1.1](https://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> V souladu s Basic Profile 1.1 `basicHttpBinding` prvek implementuje zprávy protokolu SOAP 1.1.|  
|Zabezpečení|Zabezpečení zpráv SOAP WSS 1.0|[Zabezpečení zpráv SOAP WSS 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> V souladu s základní profil zabezpečení `basicHttpBinding` prvek implementuje specifikace zabezpečení zpráv SOAP zabezpečení služby (webové služby WSS) 1.0 pro uživatelské jméno/heslo a zabezpečení založené na X.509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Zabezpečení|Profil UsernameToken zabezpečení zprávy protokolu SOAP WSS 1.0|[Profil UsernameToken zabezpečení zprávy protokolu SOAP WSS 1.0](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Zabezpečení|WSS protokolu SOAP zprávy X.509 certifikátu tokenu profil zabezpečení 1.0|[WSS protokolu SOAP zprávy X.509 certifikátu tokenu profil zabezpečení 1.0](https://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding ws2007HttpBinding a wsDualHttpBinding  
  
|Kategorie|Protocol (Protokol)|Specifikace a využití|  
|--------------|--------------|-----------------------------|  
|Zasílání zpráv|PROTOKOL SOAP 1.2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Zasílání zpráv framework](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (včetně vazby HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Zasílání zpráv|WS-Addressing 2005/08|[Webové služby adresování Core 1.0-](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Webové služby SOAP adresování 1.0-](https://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> `wsHttpBinding`, `ws2007HttpBinding`, A `wsDualHttpBinding` implementace WS-Addressing World Wide Web Consortium (W3C) doporučení Povolit asynchronní zasílání zpráv, korelace zprávy a adresování mechanismy přenosu doménově neutrální.<br /><br /> WCF nepodporuje šifrování záhlaví WS-Addressing, i když je to povoleno parametrem WS-* specifikace.|  
|Zasílání zpráv|WS-Addressing 1.0 - metadat|[WS-Addressing metadat 1.0](https://www.w3.org/2007/05/addressing/metadata) podporu pro tento protokol se povoluje nastavením verze zásad chování ServiceMetadata – s policyversion nastavena na 1.2 (výchozí), popis wsdl je v souladu s WS-Addressing wsdl, s policyversion nastavena na 1.5, popis wsdl je kompatibilní s metadaty ws-addressing.<br /><br /> WCF nepodporuje šifrování záhlaví WS-Addressing, i když je to povoleno parametrem WS-* specifikace.|  
|Zabezpečení|Zabezpečení zpráv SOAP WSS 1.0|[Zabezpečení zpráv SOAP WSS 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Použít, když `securityMode` atribut je nastaven na "wsSecurityOverHttp" (výchozí) a parametry jsou nakonfigurovány pomocí `wsSecurity` podřízený element.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Zabezpečení|Doplněk WSS protokolu SOAP zprávy zabezpečení UsernameToken Profile 1.1|[Profil UsernameToken zabezpečení zprávy protokolu SOAP WSS 1.0](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> Použít, když `wsSecurity` elementu `authenticationMode` atribut je nastaven na "Username".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Zabezpečení|WSS protokolu SOAP zprávy zabezpečení X.509 certifikátu tokenu Profile 1.1|[WSS protokolu SOAP zprávy zabezpečení X.509 certifikátu tokenu Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> Používání pro ochranu zpráva při `wsSecurity` elementu `authenticationMode` atribut je nastaven na "Username", "Certifikáty" nebo "None". Kromě toho to používat pro ověřování klientů při `wsSecurity` elementu `authenticationMode` atribut je nastaven na "Certifikátu".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpečení|Doplněk WSS protokolu SOAP zprávy zabezpečení Token protokolu Kerberos Profile 1.1|[Doplněk WSS protokolu SOAP zprávy zabezpečení Token protokolu Kerberos Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> Používání pro ochranu ověřování a zpráva při `wsSecurity` elementu `authenticationMode` atribut je nastaven na "Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpečení|WS-SecureConversation|[WS-SecureConversation](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Použít k poskytnutí zabezpečenou relaci při `security/@mode` atribut je nastaven na "Zpráva" a `message/@establishSecurityContext` atribut je nastaven na hodnotu "PRAVDA" (výchozí).|  
|Zabezpečení|WS-Trust|[WS-Trust](https://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> Použít WS-SecureConversation (viz výše).|  
|Spolehlivé zasílání zpráv|WS-ReliableMessaging|[WS-ReliableMessaging](https://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> Použijte, pokud je vazba konfigurována pro použití `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transakce|WS-AtomicTransaction|[WS-AtomicTransaction](https://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> Používá se pro komunikaci mezi správci transakcí. Klienti WCF a služby vždy používá správce místní transakce.|  
|Transakce|Koordinace WS|[WS-Coordination](https://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> Použijte tok kontext transakce při `flowTransactions` atribut je nastaven na "Povoleno" nebo "Required".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>wsFederationHttpBinding a ws2007FederationHttpBinding  
 [ \<WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a [ \<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) prvky jsou zavedené kvůli zajištění podpory pro federovaných scénářích, kde je třetí strana vystaví token pro ověření klienta. Kromě protokolech používaných `wsHttpBinding`, `wsFederationHttpBinding` využívá:  
  
- `WS-Trust` pro vydávání tokenů.  
  
- Doplněk WSS zabezpečení kontrolní výrazy SAML (Markup Language) Token profil 1.0 a 1.1 pro nejčastěji běžně vydané formát tokenu.  
  
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
  
## <a name="system-provided-metadata-bindings"></a>Vazby poskytované systémem metadat  
 Následující tabulky popisují protokoly podporované vazbami interoperabilní metadat poskytované systémem zveřejněn prostřednictvím <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> třídy.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 [ \<MexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) vazba podporuje následující protokoly. Další informace o použití této vazbě naleznete v tématu [publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategorie|Protocol (Protokol)|Specifikace a využití|  
|--------------|--------------|-----------------------------|  
|Přenos|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)|  
|Zasílání zpráv|PROTOKOL SOAP 1.2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Zasílání zpráv framework](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (včetně vazby HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Zasílání zpráv|WS-Addressing 2005/08|[Webové služby adresování Core 1.0-](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Webové služby SOAP adresování 1.0-](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF implementuje WS-MetadataExchange pro načtení schématu XML, WSDL a WS-Policy.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) podporuje následující protokoly. Další informace o použití této vazbě naleznete v tématu [publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategorie|Protocol (Protokol)|Specifikace a využití|  
|--------------|--------------|-----------------------------|  
|Přenos|HTTP 1.1|[HTTP 1.1](https://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> Zabezpečení přenosu je povoleno.|  
|Zasílání zpráv|PROTOKOL SOAP 1.2|[Primer](https://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Zasílání zpráv framework](https://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (včetně vazby HTTP)](https://go.microsoft.com/fwlink/?LinkId=95329)|  
|Zasílání zpráv|WS-Addressing 2005/08|[Webové služby adresování Core 1.0-](https://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Webové služby SOAP adresování 1.0-](https://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> WCF implementuje WS-MetadataExchange pro načtení schématu XML, WSDL a WS-Policy.|  
  
## <a name="see-also"></a>Viz také:

- [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)
- [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)
- [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)
- [\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)
- [\<mexHttpsBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)
- [\<mexHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
