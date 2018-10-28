---
title: Průvodce interoperabilitou protokolů webových služeb
ms.date: 03/30/2017
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
ms.openlocfilehash: 9aeceff9dc2b714016d2f7c379e538d885489bb9
ms.sourcegitcommit: 4621e67f69e7a9503ea93313ff60d69683207889
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2018
ms.locfileid: "49995396"
---
# <a name="web-services-protocols-interoperability-guide"></a>Průvodce interoperabilitou protokolů webových služeb
Windows Communication Foundation (WCF) implementuje řadu protokoly webové služby. Mnohé z těchto protokolů zahrnout několik možností a bodů rozšiřitelnosti ponecháno na rozhodnutí implementátora. Toto téma obsahuje seznam protokoly webové služby, které implementuje WCF. Další témata v této části poskytují podrobné informace o implementaci pro každý protokol podporován.  
  
## <a name="web-services-protocols-implemented-by-wcf"></a>Protokoly implementované WCF webových služeb  
 WCF poskytuje podporu pro webové služby (WS) protokoly infrastruktury prostřednictvím kanálů a protokoly aplikací pomocí funkce kontrakty webových služeb. Vzájemná funkční spolupráce pro aplikační protokoly se provádí prostřednictvím jazyk pro popis schématu XML (XSD) 1.0 a Web Services Description Language (WSDL) 1.1.  
  
 Poskytuje interoperabilitu protokoly infrastruktury WS-* specifikace. Kanály WCF poskytovat podporu pro několik WS -\* protokoly infrastruktury. Kanály WCF se konfigurují pomocí elementů vazby. Následující tabulky obsahují seznam všech WS -\* infrastruktury protokoly implementované zprostředkovatelem různé prvky vazeb WCF.  
  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement> podporuje specifikace v následující tabulce.  
  
|Specifikace/dokumentu|Odkaz|  
|-----------------------------|----------|  
|HTTP 1.1|[RFC 2616](https://go.microsoft.com/fwlink/?LinkId=90372)|  
|Ze SOAP 1.1 vazbu protokolu HTTP|[Simple Object Access Protocol (SOAP) 1.1](https://go.microsoft.com/fwlink/?LinkId=90520), část 7|  
|Ze SOAP 1.2 vazbu protokolu HTTP|[Verze SOAP 1.2 – část 2: Adjuncts (Second Edition)](https://go.microsoft.com/fwlink/?LinkId=95329), část 7|  
  
 <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> podporují požadavky v následující tabulce.  
  
|Specifikace/dokumentu|Odkaz|  
|-----------------------------|----------|  
|XML|[Extensible Markup Language (XML) 1.0 (čtvrtým vydáním)](https://go.microsoft.com/fwlink/?LinkId=15139)|  
|PROTOKOL SOAP 1.1|[Simple Object Access Protocol (SOAP) 1.1](https://go.microsoft.com/fwlink/?LinkId=96687)|  
|Ze SOAP 1.2 Core|[Verze SOAP 1.2 – část 1: Messaging Framework (Second Edition)](https://go.microsoft.com/fwlink/?LinkId=94664)|  
|WS-Addressing 2004/08|[Základní adresování (WS-Addressing) na webové služby](https://go.microsoft.com/fwlink/?LinkId=81239)|  
|W3C webových služeb adresování Core 1.0-|[Webové služby adresování Core 1.0-](https://go.microsoft.com/fwlink/?LinkId=96688)|  
|W3C webových služeb adresování 1.0 - vazba SOAP|[Webové služby adresování 1.0 - vazba SOAP](https://go.microsoft.com/fwlink/?LinkId=96689)|  
|W3C webových služeb adresování 1.0 - WSDL vazby *|[Webové služby adresování 1.0 - Vazba WSDL](https://go.microsoft.com/fwlink/?LinkId=96690)|  
|Adresování 1.0 metadat W3C webové služby|[Webové služby adresování 1.0 - metadat](https://www.w3.org/TR/ws-addr-metadata/)|  
|Vazba WSDL SOAP1.1|[Web Services Description Language (WSDL) 1.1](https://go.microsoft.com/fwlink/?LinkId=96160)|  
|Vazba WSDL SOAP1.2|[Rozšíření WSDL 1.1 vazbu pro protokol SOAP 1.2](https://go.microsoft.com/fwlink/?LinkId=96691)|  
  
 <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> podporuje specifikace v následující tabulce.  
  
|Specifikace/dokumentu|Odkaz|  
|-----------------------------|----------|  
|XOP|[XML – binární optimalizované balení](https://go.microsoft.com/fwlink/?LinkId=96714)|  
|MTOM + SOAP1.2 vazby|[Mechanismus optimalizaci přenosu zprávy protokolu SOAP](https://go.microsoft.com/fwlink/?LinkId=96713)|  
|MTOM SOAP 1.1 vazbu|[Ze SOAP 1.1 vazbu pro MTOM 1.0](https://go.microsoft.com/fwlink/?LinkId=96712)|  
|MTOM WS-PolicyAssertions|K publikování.|  
  
 <xref:System.ServiceModel.Channels.SecurityBindingElement> podporuje specifikace v následující tabulce.  
  
|Specifikace/dokumentu|Odkaz|  
|-----------------------------|----------|  
|WSS: Zabezpečení zpráv SOAP 1.0|[Zabezpečení webové služby: Zabezpečení zpráv SOAP 1.0](https://go.microsoft.com/fwlink/?LinkId=94684)|  
|Doplněk WSS: Token uživatelského jména profilu 1.0|[Webové služby UsernameToken profil zabezpečení 1.0](https://go.microsoft.com/fwlink/?LinkId=95334)<br /><br /> vyžadovat Password/@Type= PasswordText (výchozí)|  
|Doplněk WSS: X.509 Token profilu 1.0|[Webové služby zabezpečení X.509 certifikátu tokenu profilu](https://go.microsoft.com/fwlink/?LinkId=95335)|  
|Doplněk WSS: SAML 1.1 Token profilu 1.0|[Zabezpečení webové služby: Profil Token SAML](https://go.microsoft.com/fwlink/?LinkId=96693)|  
|Doplněk WSS: Zabezpečení zpráv SOAP 1.1|[Zabezpečení webové služby: Zabezpečení zpráv SOAP 1.1](https://go.microsoft.com/fwlink/?LinkId=91240)|  
|Doplněk WSS uživatelské jméno Token Profile 1.1|[Webové služby zabezpečení UsernameToken Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=95331)<br /><br /> neimplementují založené na heslech odvození klíče;<br /><br /> vyžadovat Password/@Type= PasswordText (výchozí)|  
|Doplněk WSS: X509 Token Profile 1.1|[Webové služby zabezpečení X.509 certifikátu tokenu Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=95332)|  
|Doplněk WSS: Token protokolu Kerberos Profile 1.1|[Webové služby Security Token protokolu Kerberos Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=95333)|  
|Doplněk WSS: SAML 1.1 Token Profile 1.1|[Webové služby zabezpečení SAML Token Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=96694)|  
|WS-Secure Conversation|[Webové služby zabezpečené konverzace jazyka](https://go.microsoft.com/fwlink/?LinkId=95317)|  
|WS-Trust 1.4|[Důvěřovat webových služeb jazyka](https://go.microsoft.com/fwlink/?LinkId=169514)|  
|WS-SecurityPolicy 2005/07|[Webové služby zabezpečené konverzace jazyka](https://go.microsoft.com/fwlink/?LinkId=95317)<br /><br /> Ve znění chyby odeslání technického výboru OASIS WS-SX.<br /><br /> [zprávy ws-sx](https://go.microsoft.com/fwlink/?LinkId=96700)|  
|WS-ReliableMessaging 1.1|[Protokol spolehlivého zasílání zpráv verze 1.1](../../../../docs/framework/wcf/feature-details/reliable-messaging-protocol-version-1-1.md)|  
  
 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> podporuje specifikace v následující tabulce.  
  
|Specifikace/dokumentu|Odkaz|  
|-----------------------------|----------|  
|Koordinace WS|[Koordinace webové služby](https://go.microsoft.com/fwlink/?LinkId=95324)|  
|WS-AtomicTransaction|[Webové služby atomické transakce](https://go.microsoft.com/fwlink/?LinkId=95323)|  
  
 <xref:System.ServiceModel.Description.MetadataExporter>, <xref:System.ServiceModel.Description.MetadataImporter>, <xref:System.ServiceModel.Description.WsdlExporter>, <xref:System.ServiceModel.Description.WsdlImporter>, A <xref:System.ServiceModel.Description.MetadataResolver> třídy poskytují podporu pro následující specifikace metadat:  
  
-   [XML schématu část 1: Struktury druhé vydání](https://go.microsoft.com/fwlink/?LinkId=3536)  
  
-   [XML schématu část 2: Datové typy druhé vydání](https://go.microsoft.com/fwlink/?LinkId=40138)  
  
-   [WSDL 1.1](https://go.microsoft.com/fwlink/?LinkId=96160)  
  
-   [1.2 WS-Policy](https://go.microsoft.com/fwlink/?LinkId=96705)  
  
-   [1.5 WS-Policy](https://go.microsoft.com/fwlink/?LinkId=96706)  
  
-   [WS-PolicyAttachment 1.2](https://go.microsoft.com/fwlink/?LinkId=96707)  
  
-   [WS-MetadataExchange 1.1](https://go.microsoft.com/fwlink/?LinkId=94868)  
  
-   [Přenos WS Get pro načtení metadat](https://go.microsoft.com/fwlink/?LinkId=96708)  
  
 Kromě toho jsou implementovány následující profily vzájemná funkční spolupráce mezi WCF:  
  
-   [Basic Profile 1.1](https://go.microsoft.com/fwlink/?LinkId=69313)  
  
-   [Simple SOAP vazby 1.0](https://go.microsoft.com/fwlink/?LinkId=96710)  
  
-   [1.0 pracovní profil základní zabezpečení návrhu](https://go.microsoft.com/fwlink/?LinkId=96711)  
  
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
