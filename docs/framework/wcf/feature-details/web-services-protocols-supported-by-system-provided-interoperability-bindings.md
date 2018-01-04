---
title: "Protokoly webových služeb podporované vazbami vzájemné spolupráce poskytnutými systémem"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WS-protocols
- Web services protocols
- Windows Communication Foundation, Web service protocols
ms.assetid: 1f7fc4ff-30fe-4e46-adda-91caad3b06c6
caps.latest.revision: "39"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4bfc4342435580796423056889b1c3bd22153740
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="web-services-protocols-supported-by-system-provided-interoperability-bindings"></a>Protokoly webových služeb podporované vazbami vzájemné spolupráce poskytnutými systémem
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]byl vytvořen, aby spolupracovat s webovými službami, které podporují sadu specifikace označované jako specifikací webových služeb. Pro zjednodušení konfigurace služby pro interoperabilita osvědčených postupů, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zavádí tři umožňuje vzájemnou spolupráci vazby poskytované systémem: <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>, <xref:System.ServiceModel.WSHttpBinding?displayProperty=nameWithType>, a <xref:System.ServiceModel.WSDualHttpBinding?displayProperty=nameWithType>. Pro spolupráci s organizace rozvoj z strukturovaných informace standardy (OASIS) standardů [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zahrnuje jednu vzájemná spolupráce poskytnutými systémem vazbu: <xref:System.ServiceModel.WS2007HttpBinding?displayProperty=nameWithType>. Metadata publikace [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zahrnuje dvě umožňuje vzájemnou spolupráci vazby poskytované systémem: [ \<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) a [ \<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md). Toto téma uvádí specifikace, které podporují umožňuje vzájemnou spolupráci vazby poskytované systémem.  
  
## <a name="web-services-protocols-supported-by-basichttpbinding-wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding-bindings"></a>Webové služby protokoly podporované vazbami basicHttpBinding, wsHttpBinding, – ws2007HttpBinding a – wsDualHttpBinding  
  
### <a name="all-bindings"></a>Všechny vazby  
 [ \<BasicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md), [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), a [ \<– ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md) vazby podporu Tyto protokoly.  
  
> [!NOTE]
>  Informace o vazby se používá k publikování metadat najdete v části "System-Provided metadat vazby" dál v tomto tématu.  
  
|Kategorie|Protokol|Specifikace a využití|  
|--------------|--------------|-----------------------------|  
|Přenos|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> `BasicHttpBinding`, `WSHttpBinding`, a `WS2007HttpBinding` použít přenosy HTTP a HTTPS.|  
|Zasílání zpráv|MTOM|[MTOM](http://go.microsoft.com/fwlink/?LinkId=95326)<br /><br /> `basicHttpBinding`, `wsHttpBinding`, a `ws2007HttpBinding` podporu zpráva přenosu optimalizace mechanismus (MTOM). Nepoužívá se ve výchozím nastavení. Chcete-li použít MTOM, nastavte `messageEncoding` atribut `"Mtom"`.<br /><br /> Příklad:<br /><br /> `<wsHttpBinding> <binding messageEncoding="Mtom"/> </wsHttpBinding>`|  
|Metadata|WSDL 1.1|[WSDL 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Webové služby popis Language (WSDL) používá k popisu služby.|  
|Metadata|WS-zásad|[WS-zásad](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Specifikace WS-Policy společně s kontrolní výrazy specifické pro doménu se používá k popisu služby požadavky a možnosti.|  
|Metadata|WS-Policy 1.5|[WS-Policy 1.5](http://go.microsoft.com/fwlink/?LinkId=95327)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]Specifikace WS-Policy společně s kontrolní výrazy specifické pro doménu se používá k popisu služby požadavky a možnosti.|  
|Metadata|WS-PolicyAttachment|[WS-PolicyAttachment](http://go.microsoft.com/fwlink/?LinkId=95328)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje WS-PolicyAttachment připojit výrazy zásad v různých oborech v webové služby popis Language (WSDL).|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje WS-MetadataExchange pro načtení schématu XML, WSDL a WS-zásad.|  
  
### <a name="basichttpbinding"></a>basicHttpBinding  
  
|Kategorie|Protokol|Specifikace a využití|  
|--------------|--------------|-----------------------------|  
|Zasílání zpráv|SOAP 1.1|[SOAP 1.1](http://go.microsoft.com/fwlink/?LinkId=90520)<br /><br /> V souladu s Basic Profile 1.1 `basicHttpBinding` element implementuje protokol zprávu SOAP 1.1.|  
|Zabezpečení|Zabezpečení zpráv protokolu SOAP WSS 1.0|[Zabezpečení zpráv protokolu SOAP WSS 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> V souladu s základní profil zabezpečení `basicHttpBinding` element implementuje specifikace Web Services zabezpečení (WSS) zabezpečení zpráv protokolu SOAP 1.0 pro uživatelské jméno a heslo a zabezpečení na základě X.509.<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential &#124;                     "Message" .../> </binding> </basicHttpBinding>`|  
|Zabezpečení|Profil UsernameToken zabezpečení protokolu SOAP zprávy WSS 1.0|[Profil UsernameToken zabezpečení protokolu SOAP zprávy WSS 1.0](http://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> `<basicHttpBinding> <binding name="Binding1"> <security mode="TransportWithMessageCredential"> <transport clientCredentialType="Basic"/> </security> </basicHttpBinding>`|  
|Zabezpečení|WSS protokolu SOAP zprávy X.509 certifikátu tokenu profil zabezpečení 1.0|[WSS protokolu SOAP zprávy X.509 certifikátu tokenu profil zabezpečení 1.0](http://go.microsoft.com/fwlink/?LinkId=95335)<br /><br /> `<basicHttpBinding>   <security mode="Message"> <message clientCredentialType="Certificate"/> </security> </basicHttpBinding>`|  
  
### <a name="wshttpbinding-ws2007httpbinding-and-wsdualhttpbinding"></a>wsHttpBinding – ws2007HttpBinding a – wsDualHttpBinding  
  
|Kategorie|Protokol|Specifikace a využití|  
|--------------|--------------|-----------------------------|  
|Zasílání zpráv|SOAP 1.2|[Úvod do](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Zasílání zpráv framework](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (včetně vazby HTTP)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|Zasílání zpráv|Adresování WS 2005/08|[Webové služby adresování 1.0 – základní](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Webové služby SOAP adresování 1.0-](http://go.microsoft.com/fwlink/?LinkId=95330)<br /><br /> `wsHttpBinding`, `ws2007HttpBinding`, A `wsDualHttpBinding` implementovat doporučení World Wide Web Consortium (W3C) WS-Addressing Povolit asynchronní zasílání zpráv, korelace zprávy a adresování mechanismy přenosu jazykově neutrální.<br /><br /> WCF nepodporuje šifrování WS-Addressing hlaviček, i když je to povoleno pomocí protokolu WS-* specifikace.|  
|Zasílání zpráv|Adresování WS 1.0 - metadat|[Adresování WS Metadata 1.0](http://www.w3.org/2007/05/addressing/metadata) podporu pro tento protokol je povolená nastavením zásad verze v chování ServiceMetadata - s policyversion nastavena na 1.2 (výchozí), je kompatibilní s WS-Addressing wsdl popis wsdl s policyversion nastavena na 1.5, popis wsdl je kompatibilní s ws-addressing metadat.<br /><br /> WCF nepodporuje šifrování WS-Addressing hlaviček, i když je to povoleno pomocí protokolu WS-* specifikace.|  
|Zabezpečení|Zabezpečení zpráv protokolu SOAP WSS 1.0|[Zabezpečení zpráv protokolu SOAP WSS 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)<br /><br /> Použijte, když `securityMode` je nastavena na hodnotu "wsSecurityOverHttp" (výchozí) a parametry jsou nakonfigurovány pomocí `wsSecurity` podřízený element.<br /><br /> `<wsHttpBinding>   <binding name="myBinding">      <security mode="Message" .../>   </binding> </wsHttpBinding>`|  
|Zabezpečení|Profil UsernameToken zabezpečení protokolu SOAP zprávy WSS 1.1|[Profil UsernameToken zabezpečení protokolu SOAP zprávy WSS 1.0](http://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> Použijte, když `wsSecurity` elementu `authenticationMode` je nastavena na hodnotu "Username".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="UserName        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security> </binding> </wsHttpBinding>`|  
|Zabezpečení|WSS protokolu SOAP zprávy X.509 certifikátu tokenu profil zabezpečení 1.1|[WSS protokolu SOAP zprávy X.509 certifikátu tokenu profil zabezpečení 1.1](http://go.microsoft.com/fwlink/?LinkId=95332)<br /><br /> Použití ochrany zpráva při `wsSecurity` elementu `authenticationMode` atribut je nastaven na "Username", "Certifikát" nebo "Žádný". Kromě toho tato používat pro ověřování klientů při `wsSecurity` elementu `authenticationMode` je nastavena na hodnotu "Certifikát".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Certificate"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpečení|Profil protokolu Kerberos Token zabezpečení zprávu protokolu SOAP WSS 1.1|[Profil protokolu Kerberos Token zabezpečení zprávu protokolu SOAP WSS 1.1](http://go.microsoft.com/fwlink/?LinkId=95333)<br /><br /> Použití pro ochranu ověřování a zpráva při `wsSecurity` elementu `authenticationMode` je nastavena na hodnotu "Systém Windows".<br /><br /> `<wsHttpBinding>   <binding name="MyBinding">     <security mode="Message>       <message           clientCredentialType="Windows"        negotiateServiceCredential="false"        establishSecurityContext="false"/>     </security>   </binding> </wsHttpBinding>`|  
|Zabezpečení|WS-SecureConversation|[WS-SecureConversation](http://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Použijte k zajištění zabezpečené relace při `security/@mode` je nastavena na hodnotu "Zpráva" a `message/@establishSecurityContext` atribut je nastaven na hodnotu "PRAVDA" (výchozí).|  
|Zabezpečení|WS-Trust|[WS-Trust](http://go.microsoft.com/fwlink/?LinkId=95318)<br /><br /> Používá WS-SecureConversation (viz výše).|  
|Spolehlivé zasílání zpráv|WS-ReliableMessaging|[WS-ReliableMessaging](http://go.microsoft.com/fwlink/?LinkId=95322)<br /><br /> Použijte, pokud vazba je nakonfigurovaný na použití `reliableSession`.<br /><br /> `<wsHttpBinding>  <binding name="myBinding">    <reliableSession/>   </binding> </wsHttpBinding>`|  
|Transakce|WS-AtomicTransaction|[WS-AtomicTransaction](http://go.microsoft.com/fwlink/?LinkId=95323)<br /><br /> Používáno pro komunikaci mezi správci transakcí. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]služby a klienti vždy používají místní transakce správce.|  
|Transakce|WS-spolupráce|[WS-spolupráce](http://go.microsoft.com/fwlink/?LinkId=95324)<br /><br /> Pomocí toku kontext transakce při `flowTransactions` je atribut nastaven na "Povoleno" nebo "Požadováno".<br /><br /> `<wsHttpBinding>   <binding transactionFlow="true"/> </wsHttpBinding>`|  
  
## <a name="wsfederationhttpbinding-and-ws2007federationhttpbinding"></a>– wsFederationHttpBinding a – ws2007FederationHttpBinding  
 [ \<– WsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) a [ \<– ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md) elementy byly zavedeny kvůli zajištění podpory pro federovaných scénářích, kde třetí strany vydá token používá k ověření klienta. Kromě protokolech používaných `wsHttpBinding`, `wsFederationHttpBinding` využívá:  
  
-   `WS-Trust`pro vystavování tokenů.  
  
-   WSS kontrolní výrazy jazyka SAML (Security Markup) Token profil 1.0 a 1.1 pro nejvíc běžně vydaný formát tokenu.  
  
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
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Federation](../../../../docs/framework/wcf/feature-details/federation.md) .  
  
## <a name="system-provided-metadata-bindings"></a>Vazby poskytované systémem metadat  
 Následující tabulky popisují protokoly nepodporuje vazby poskytované systémem umožňuje vzájemnou spolupráci metadata vystavené <xref:System.ServiceModel.Description.MetadataExchangeBindings?displayProperty=nameWithType> třídy.  
  
### <a name="mexhttpbinding"></a>mexHttpBinding  
 [ \<MexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md) vazba podporuje následující protokoly. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Pomocí této vazby, najdete v tématu [publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategorie|Protokol|Specifikace a využití|  
|--------------|--------------|-----------------------------|  
|Přenos|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)|  
|Zasílání zpráv|SOAP 1.2|[Úvod do](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Zasílání zpráv framework](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (včetně vazby HTTP)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|Zasílání zpráv|Adresování WS 2005/08|[Webové služby adresování 1.0 – základní](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Webové služby SOAP adresování 1.0-](http://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje WS-MetadataExchange pro načtení schématu XML, WSDL a WS-zásad.|  
  
### <a name="mexhttpsbinding"></a>mexHttpsBinding  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md) podporuje následující protokoly. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Pomocí této vazby, najdete v tématu [publikování metadat](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
|Kategorie|Protokol|Specifikace a využití|  
|--------------|--------------|-----------------------------|  
|Přenos|HTTP 1.1|[HTTP 1.1](http://go.microsoft.com/fwlink/?LinkId=84048)<br /><br /> Zabezpečení přenosu je povolena.|  
|Zasílání zpráv|SOAP 1.2|[Úvod do](http://go.microsoft.com/fwlink/?LinkId=48282)<br /><br /> [Zasílání zpráv framework](http://go.microsoft.com/fwlink/?LinkId=94664)<br /><br /> [Adjuncts (včetně vazby HTTP)](http://go.microsoft.com/fwlink/?LinkId=95329)|  
|Zasílání zpráv|Adresování WS 2005/08|[Webové služby adresování 1.0 – základní](http://go.microsoft.com/fwlink/?LinkId=90574)<br /><br /> [Webové služby SOAP adresování 1.0-](http://go.microsoft.com/fwlink/?LinkId=95330)|  
|Metadata|WS-MetadataExchange|[WS-MetadataExchange](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]implementuje WS-MetadataExchange pro načtení schématu XML, WSDL a WS-zásad.|  
  
## <a name="see-also"></a>Viz také  
 [Vazby poskytované systémem](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)  
 [\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)  
 [\<– wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)  
 [\<mexHttpsBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpsbinding.md)  
 [\<mexHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/mexhttpbinding.md)
