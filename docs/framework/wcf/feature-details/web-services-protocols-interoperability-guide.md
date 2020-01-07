---
title: Průvodce interoperabilitou protokolů webových služeb
ms.date: 03/30/2017
ms.assetid: f2981678-ebdb-433d-899b-467f7df95fb2
ms.openlocfilehash: 1b949880b3ebbaf121b79a958d17cf5708affcf3
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75636143"
---
# <a name="web-services-protocols-interoperability-guide"></a>Průvodce interoperabilitou protokolů webových služeb

Windows Communication Foundation (WCF) implementuje několik protokolů webových služeb. Mnohé z těchto protokolů zahrnují řadu možností a bodů rozšíření, které jsou ponechány na uvážení implementátora. Toto téma poskytuje seznam protokolů webových služeb, které WCF implementuje. Další témata v této části poskytují podrobné informace o implementaci pro každý podporovaný protokol.

## <a name="web-services-protocols-implemented-by-wcf"></a>Protokoly webových služeb implementované službou WCF

Služba WCF poskytuje podporu pro protokoly infrastruktury webových služeb (WS) prostřednictvím kanálů a aplikačních protokolů webových služeb prostřednictvím funkce smlouvy. Vzájemná funkční spolupráce pro aplikační protokoly se dosahuje prostřednictvím schématu XML Description Language 1,0 (XSD) a jazyka WSDL (Web Services Description Language) 1,1.

Interoperabilita protokolů infrastruktury je poskytována specifikacemi WS-*. Kanály WCF poskytují podporu pro určitý počet protokolů infrastruktury WS-\*. Kanály WCF jsou nakonfigurovány pomocí prvků vazby. Následující tabulky obsahují úplný seznam protokolů infrastruktury WS-\* implementovaných různými prvky vazby WCF.

<xref:System.ServiceModel.Channels.HttpTransportBindingElement> podporuje specifikace v následující tabulce.

|Specifikace/dokument|Odkaz|
|-----------------------------|----------|
|HTTP 1,1|[RFC 2616](https://www.rfc-editor.org/rfc/rfc2616.txt)|
|Vazba SOAP 1,1 HTTP|[Protokol SOAP (Simple Object Access Protocol) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), část 7|
|Vazba SOAP 1,2 HTTP|[SOAP verze 1,2 část 2: Adjuncts (Second Edition)](https://www.w3.org/TR/soap12-part2/), část 7|

<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement> a <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> podporují specifikace v následující tabulce.

|Specifikace/dokument|Odkaz|
|-----------------------------|----------|
|XML|[Jazyk XML (eXtensible Markup Language) (XML) 1,0 (čtvrtá edice)](https://www.w3.org/TR/REC-xml/)|
|PROTOKOL SOAP 1,1|[Protokol SOAP (Simple Object Access Protocol) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/)|
|Jádro protokolu SOAP 1,2|[SOAP verze 1,2 část 1: architektura pro zasílání zpráv (druhá edice)](https://www.w3.org/TR/2007/REC-soap12-part1-20070427/)|
|WS-Addressing 2004/08|[Adresování webových služeb (WS-Addressing)](https://www.w3.org/Submission/2004/SUBM-ws-addressing-20040810/)|
|Webové služby W3C Addressing 1,0 – jádro|[Webové služby Addressing 1,0 – Core](https://www.w3.org/TR/2006/REC-ws-addr-core-20060509/)|
|Webové služby W3C Addressing 1,0 – vazba SOAP|[Webové služby Addressing 1,0 – vazba SOAP](https://www.w3.org/TR/2006/REC-ws-addr-soap-20060509/)|
|Webové služby W3C Addressing 1,0-Binding WSDL *|[Webové služby Addressing 1,0 – Vazba WSDL](https://www.w3.org/TR/2006/CR-ws-addr-wsdl-20060529/)|
|Webové služby W3C Addressing 1,0 metadata|[Webové služby Addressing 1,0 – metadata](https://www.w3.org/TR/ws-addr-metadata/)|
|Vazba WSDL SOAP 1.1|[Jazyk WSDL (Web Services Description Language) 1,1](https://www.w3.org/TR/wsdl/)|
|Vazba WSDL SOAP 1.2|[Rozšíření vazby WSDL 1,1 pro SOAP 1,2](https://www.w3.org/Submission/wsdl11soap12/)|

<xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement> podporuje specifikace v následující tabulce.

|Specifikace/dokument|Odkaz|
|-----------------------------|----------|
|XOP|[Binární optimalizované balení XML](https://www.w3.org/TR/xop10/)|
|Vazba MTOM + SOAP 1.2|[Mechanismus optimalizace přenosu zpráv SOAP](https://www.w3.org/TR/soap12-mtom/)|
|Vazba MTOM SOAP 1,1|[Vazba SOAP 1,1 pro MTOM 1,0](https://www.w3.org/Submission/soap11mtom10/)|
|MTOM WS-PolicyAssertions|[Kontrolní výraz zásad serializace MTOM (WS-MTOMPolicy)](https://www.w3.org/Submission/WS-MTOMPolicy/)|

<xref:System.ServiceModel.Channels.SecurityBindingElement> podporuje specifikace v následující tabulce.

|Specifikace/dokument|Odkaz|
|-----------------------------|----------|
|WSS: zabezpečení zpráv SOAP 1,0|[Specifikace Web Services Security: zabezpečení zprávy SOAP 1,0](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf)|
|WSS: Profil tokenu uživatelského jména 1,0|[Specifikace Web Services Security UsernameToken Profile 1,0](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-username-token-profile-1.0.pdf)<br /><br /> vyžadovat Password/@Type= PasswordText (výchozí)|
|WSS: X. 509 – profil tokenu 1,0|[Specifikace Web Services Security profil tokenu certifikátu X. 509](https://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-x509-token-profile-1.0.pdf)|
|WSS: Profil tokenu SAML 1,1 1,0|[Specifikace Web Services Security: Profil tokenu SAML](https://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.0.pdf)|
|WSS: zabezpečení zpráv SOAP 1,1|[Specifikace Web Services Security: zabezpečení zprávy SOAP 1,1](https://www.oasis-open.org/committees/download.php/16790/wss-v1.1-spec-os-SOAPMessageSecurity.pdf)|
|Token uživatelského jména WSS – profil 1,1|[Specifikace Web Services Security UsernameToken Profile 1,1](https://www.oasis-open.org/committees/download.php/16782/wss-v1.1-spec-os-UsernameTokenProfile.pdf)<br /><br /> Neimplementujte odvození klíče založené na heslech;<br /><br /> vyžadovat Password/@Type= PasswordText (výchozí)|
|WSS: Profil tokenu x509 1,1|[Specifikace Web Services Security profil tokenu certifikátu X. 509 1,1](https://www.oasis-open.org/committees/download.php/16785/wss-v1.1-spec-os-x509TokenProfile.pdf)|
|WSS: Profil tokenu protokolu Kerberos 1,1|[Specifikace Web Services Security profil tokenu Kerberos 1,1](https://www.oasis-open.org/committees/download.php/16788/wss-v1.1-spec-os-KerberosTokenProfile.pdf)|
|WSS: Profil tokenu SAML 1,1 1,1|[Specifikace Web Services Security profil tokenu SAML 1,1](https://www.oasis-open.org/committees/download.php/16768/wss-v1.1-spec-os-SAMLTokenProfile.pdf)|
|Konverzace WS-Secure|[Jazyk zabezpečené konverzace webové služby](https://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)|
|WS-Trust 1,4|[Jazyk důvěryhodnosti webových služeb](https://docs.oasis-open.org/ws-sx/ws-trust/200802)|
|WS-SecurityPolicy 2005/07|[Jazyk zabezpečené konverzace webové služby](https://specs.xmlsoap.org/ws/2005/02/sc/ws-secureconversation.pdf)<br /><br /> Jak bylo upraveno službou seznam chyb odeslané technickému výboru OASIS WS-SX.<br /><br /> [zpráva WS-SX](https://lists.oasis-open.org/archives/ws-sx/200512/msg00017.html)|
|WS-ReliableMessaging 1,1|[Protokol spolehlivého zasílání zpráv verze 1.1](reliable-messaging-protocol-version-1-1.md)|

<xref:System.ServiceModel.Channels.TransactionFlowBindingElement> podporuje specifikace v následující tabulce.

|Specifikace/dokument|Odkaz|
|-----------------------------|----------|
|WS-koordinace|[Koordinace webových služeb](https://docs.microsoft.com/previous-versions/ms951231(v=msdn.10))|
|WS-AtomicTransaction|[Transakce Atom webové služby](https://specs.xmlsoap.org/ws/2004/10/wsat/wsat.pdf)|

Třídy <xref:System.ServiceModel.Description.MetadataExporter>, <xref:System.ServiceModel.Description.MetadataImporter>, <xref:System.ServiceModel.Description.WsdlExporter>, <xref:System.ServiceModel.Description.WsdlImporter>a <xref:System.ServiceModel.Description.MetadataResolver> poskytují podporu pro následující specifikace metadat:

- [Schéma XML – část 1: struktury druhé edice](https://www.w3.org/TR/xmlschema-1/)

- [Schéma XML – část 2: datové typy druhé edice](https://www.w3.org/TR/xmlschema-2/)

- [WSDL 1,1](https://www.w3.org/TR/wsdl/)

- [WS-Policy 1,2](https://www.w3.org/Submission/2006/SUBM-WS-Policy-20060425/)

- [WS-Policy 1,5](https://www.w3.org/TR/ws-policy/)

- [WS-PolicyAttachment 1,2](https://www.w3.org/Submission/2006/SUBM-WS-PolicyAttachment-20060425/)

- [WS-MetadataExchange 1,1](https://specs.xmlsoap.org/ws/2004/09/mex/WS-MetadataExchange.pdf)

- [WS-Transfer get pro načtení metadat](https://www.w3.org/Submission/2006/SUBM-WS-Transfer-20060315/)

Kromě toho jsou v rámci WCF implementovány následující profily vzájemné spolupráce:

- [Základní profil 1,1](http://www.ws-i.org/Profiles/BasicProfile-1.1-2004-08-24.html)

- [Jednoduchá vazba SOAP 1,0](http://www.ws-i.org/Profiles/SimpleSoapBindingProfile-1.0-2004-08-24.html)

- [Pracovní koncept základního profilu zabezpečení 1,0](http://www.ws-i.org/Profiles/BasicSecurityProfile-1.0-2006-03-29.html)

## <a name="see-also"></a>Viz také:

- [Protokoly webových služeb podporované vazbami interoperability poskytnutými systémem](web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [Protokoly zasílání zpráv](messaging-protocols.md)
- [Schéma kontraktů dat – referenční informace](data-contract-schema-reference.md)
- [WSDL a zásady](wsdl-and-policy.md)
- [Protokoly zabezpečení](security-protocols.md)
- [Protokol spolehlivého zasílání zpráv verze 1.0](reliable-messaging-protocol-version-1-0.md)
- [Protokol spolehlivého zasílání zpráv verze 1.1](reliable-messaging-protocol-version-1-1.md)
- [Protokoly transakcí](transaction-protocols.md)
- [Protokol kontextové výměny](context-exchange-protocol.md)
