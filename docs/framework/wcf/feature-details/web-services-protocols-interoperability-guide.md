---
title: Průvodce interoperabilitou protokolů webových služeb
ms.date: 03/30/2017
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
ms.openlocfilehash: 1ee8b485d8a46d2599958db2c71f4a6e84875169
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="web-services-protocols-interoperability-guide"></a>Průvodce interoperabilitou protokolů webových služeb
Windows Communication Foundation (WCF) implementuje počet protokoly webových služeb. Mnoho z těchto protokolů obsahuje mnoho možností a bodů rozšiřitelnosti ponechány na uvážení implementátor. Toto téma obsahuje seznam protokoly webových služeb, které implementuje WCF. Další témata v této části poskytují podrobné informace o nasazení pro každý protokol podporována.  
  
## <a name="web-services-protocols-implemented-by-wcf"></a>Protokoly implementované WCF webových služeb  
 WCF poskytuje podporu pro webové služby (WS) infrastruktury protokoly prostřednictvím kanálů a protokoly aplikací pomocí funkce kontrakty webových služeb. Vzájemná funkční spolupráce pro protokoly aplikací se provádí pomocí jazyka popis schématu XML 1.0 (XSD) a Web Services Description Language (WSDL) 1.1.  
  
 Poskytuje interoperabilitu infrastruktury protokoly WS-* specifikace. Kanály WCF poskytují podporu pro řadu WS -\* protokoly infrastruktury. Kanály WCF jsou nakonfigurované pomocí elementů vazby. Následující tabulky obsahují úplný seznam WS -\* infrastruktury protokoly implementované zprostředkovatelem různé prvky vazeb WCF.  
  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> podporuje specifikace v následující tabulce.  
  
|Specifikace či dokumentu|Odkaz|  
|-----------------------------|----------|  
|HTTP 1.1|[RFC 2616](http://go.microsoft.com/fwlink/?LinkId=90372)|  
|SOAP 1.1 vazby HTTP|[Simple Object Access Protocol (SOAP) 1.1](http://go.microsoft.com/fwlink/?LinkId=90520), část 7|  
|SOAP 1.2 vazby HTTP|[Verze protokolu SOAP 1.2 část 2: Adjuncts (druhé vydání)](http://go.microsoft.com/fwlink/?LinkId=95329), část 7|  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> podporu specifikace v následující tabulce.  
  
|Specifikace či dokumentu|Odkaz|  
|-----------------------------|----------|  
|XML|[Extensible Markup Language (XML) 1.0 (čtvrté vydání)](http://go.microsoft.com/fwlink/?LinkId=15139)|  
|SOAP 1.1|[Simple Object Access Protocol (SOAP) 1.1](http://go.microsoft.com/fwlink/?LinkId=96687)|  
|SOAP 1.2 jádra|[Verze protokolu SOAP 1.2 část 1: Zasílání zpráv Framework (druhé vydání)](http://go.microsoft.com/fwlink/?LinkId=94664)|  
|Adresování WS 2004/08|[Webové služby adresování (WS-adresování)](http://go.microsoft.com/fwlink/?LinkId=81239)|  
|W3C webových služeb adresování 1.0 – základní|[Webové služby adresování 1.0 – základní](http://go.microsoft.com/fwlink/?LinkId=96688)|  
|W3C webových služeb adresování 1.0 - vazby protokolu SOAP|[Webové služby adresování 1.0 - vazby protokolu SOAP](http://go.microsoft.com/fwlink/?LinkId=96689)|  
|W3C webových služeb adresování 1.0 - WSDL vazby *|[Webové služby adresování 1.0 - vazby WSDL](http://go.microsoft.com/fwlink/?LinkId=96690)|  
|Adresování 1.0 Metadata W3C webové služby|[Webové služby adresování 1.0 - metadat](http://www.w3.org/TR/ws-addr-metadata/)|  
|Vazba SOAP1.1 WSDL|[Web Services Description Language (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=96160)|  
|Vazba SOAP1.2 WSDL|[1.1 vazba je očekáváno rozšíření WDSL pro SOAP 1.2](http://go.microsoft.com/fwlink/?LinkId=96691)|  
  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> podporuje specifikace v následující tabulce.  
  
|Specifikace či dokumentu|Odkaz|  
|-----------------------------|----------|  
|XOP|[XML – binární optimalizované balení](http://go.microsoft.com/fwlink/?LinkId=96714)|  
|MTOM + SOAP1.2 vazby|[Mechanismus Optimalizace přenosu zpráv protokolu SOAP](http://go.microsoft.com/fwlink/?LinkId=96713)|  
|MTOM SOAP 1.1 vazby|[SOAP 1.1 vazby pro MTOM 1.0](http://go.microsoft.com/fwlink/?LinkId=96712)|  
|MTOM WS-PolicyAssertions|K publikování.|  
  
 <xref:System.ServiceModel.Channels.SecurityBindingElement> podporuje specifikace v následující tabulce.  
  
|Specifikace či dokumentu|Odkaz|  
|-----------------------------|----------|  
|WSS: Zabezpečení zpráv protokolu SOAP 1.0|[Zabezpečení webové služby: Zabezpečení zpráv protokolu SOAP 1.0](http://go.microsoft.com/fwlink/?LinkId=94684)|  
|WSS: Uživatelské jméno Token profil 1.0|[Webové služby profil zabezpečení UsernameToken 1.0](http://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> vyžadovat Password/@Type= PasswordText (výchozí)|  
|WSS: X.509 tokenu profil 1.0|[Webové služby zabezpečení X.509 certifikátu tokenu profilu](http://go.microsoft.com/fwlink/?LinkId=95335)|  
|WSS: SAML 1.1 Token profil 1.0|[Zabezpečení webové služby: Profil tokenu SAML](http://go.microsoft.com/fwlink/?LinkId=96693)|  
|WSS: Zabezpečení zpráv SOAP 1.1|[Zabezpečení webové služby: Zabezpečení zpráv protokolu SOAP 1.1](http://go.microsoft.com/fwlink/?LinkId=91240)|  
|WSS uživatelské jméno tokenu Profile 1.1|[Webové služby zabezpečení UsernameToken Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> neimplementuje založené na heslech odvození klíče;<br /><br /> vyžadovat Password/@Type= PasswordText (výchozí)|  
|WSS: X509 Token Profile 1.1|[Webové služby zabezpečení X.509 certifikátu tokenu Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=95332)|  
|WSS: Token protokolu Kerberos Profile 1.1|[Webové služby zabezpečení Token protokolu Kerberos Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=95333)|  
|WSS: SAML 1.1 Token Profile 1.1|[Webové služby zabezpečení SAML Token Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=96694)|  
|WS zabezpečené konverzace|[Webové služby zabezpečené konverzace jazyk](http://go.microsoft.com/fwlink/?LinkId=95317)|  
|WS-Trust 1.4|[Webové služby důvěřovat jazyk](http://go.microsoft.com/fwlink/?LinkId=169514)|  
|WS-SecurityPolicy 2005/07|[Webové služby zabezpečené konverzace jazyk](http://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Ve znění chybující odeslána OASIS WS-SX technický výbor.<br /><br /> [ws-sx zpráv](http://go.microsoft.com/fwlink/?LinkId=96700)|  
|WS-ReliableMessaging 1.1|[Protokol spolehlivého zasílání zpráv verze 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)|  
  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> podporuje specifikace v následující tabulce.  
  
|Specifikace či dokumentu|Odkaz|  
|-----------------------------|----------|  
|WS-spolupráce|[Koordinace webové služby](http://go.microsoft.com/fwlink/?LinkId=95324)|  
|WS-AtomicTransaction|[Webové služby Atomic transakce](http://go.microsoft.com/fwlink/?LinkId=95323)|  
  
 <xref:System.ServiceModel.Description.MetadataExporter>, <xref:System.ServiceModel.Description.MetadataImporter>, <!--zz <xref:System.ServiceModel.Description.WSDLExporter>, <xref:System.ServiceModel.Description.WSDLImporter>, --> `System.ServiceModel.Description.MetadataImporter`, `System.ServiceModel.Description.WSDLImporter`, A <xref:System.ServiceModel.Description.MetadataResolver> třídy poskytují podporu pro tyto specifikace metadat:  
  
-   [XML schéma část 1: Struktury druhé vydání](http://go.microsoft.com/fwlink/?LinkId=3536)  
  
-   [XML schéma část 2: Datové typy druhé vydání](http://go.microsoft.com/fwlink/?LinkId=40138)  
  
-   [WSDL 1.1](http://go.microsoft.com/fwlink/?LinkId=96160)  
  
-   [WS-Policy 1.2](http://go.microsoft.com/fwlink/?LinkId=96705)  
  
-   [WS-Policy 1.5](http://go.microsoft.com/fwlink/?LinkId=96706)  
  
-   [WS-PolicyAttachment 1.2](http://go.microsoft.com/fwlink/?LinkId=96707)  
  
-   [WS-MetadataExchange 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)  
  
-   [Přenos WS Get pro načtení metadat](http://go.microsoft.com/fwlink/?LinkId=96708)  
  
 Kromě toho jsou následující profily interoperabilita implementované napříč WCF:  
  
-   [Basic Profile 1.1](http://go.microsoft.com/fwlink/?LinkId=69313)  
  
-   [Jednoduché SOAP vazby 1.0](http://go.microsoft.com/fwlink/?LinkId=96710)  
  
-   [Základní zabezpečení profilu 1.0 pracovní konceptu](http://go.microsoft.com/fwlink/?LinkId=96711)  
  
## <a name="see-also"></a>Viz také  
 [Protokoly webových služeb podporované vazbami interoperability poskytnutými systémem](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [Protokoly zasílání zpráv](../../../../docs/framework/wcf/feature-details/messaging-protocols.md)  
 [Schéma kontraktů dat – referenční informace](../../../../docs/framework/wcf/feature-details/data-contract-schema-reference.md)  
 [WSDL a zásady](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)  
 [Protokoly zabezpečení](../../../../docs/framework/wcf/feature-details/security-protocols.md)  
 [Protokol spolehlivého zasílání zpráv verze 1.0](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-0.md)  
 [Protokol spolehlivého zasílání zpráv verze 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)  
 [Protokoly transakcí](../../../../docs/framework/wcf/feature-details/transaction-protocols.md)  
 [Protokol kontextové výměny](../../../../docs/framework/wcf/feature-details/context-exchange-protocol.md)
