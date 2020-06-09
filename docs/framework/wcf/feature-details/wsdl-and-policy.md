---
title: WSDL a zásady
ms.date: 03/30/2017
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
ms.openlocfilehash: 201920a8ebf639c74acfb20b2e990c8bbc0c5b55
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84600098"
---
# <a name="wsdl-and-policy"></a>WSDL a zásady
Toto téma se věnuje Windows Communication Foundation (WCF) WSDL 1,1, WS-Policy a WS-PolicyAttachment Details a také další kontrolní výrazy WS-Policy a rozšíření WSDL 1,1 zavedené službou WCF.  
  
 Služba WCF implementuje specifikace WS-Policy a WS-PolicyAttachment odeslané na W3C s omezeními a vyjasněmi popsanými v tomto dokumentu.  
  
 Tento dokument používá předpony a obory názvů uvedené v následující tabulce.  
  
|Předpona|Obor názvů|  
|------------|---------------|  
|WSP (WS-Policy 1,2)|`http://schemas.xmlsoap.org/ws/2004/09/policy`|  
|WSP (WS-Policy 1,5)|`http://www.w3.org/ns/ws-policy`|  
|HTTP|`http://schemas.microsoft.com/ws/06/2004/policy/http`|  
|mezi|`http://schemas.microsoft.com/ws/06/2004/mspolicy/msmq`|  
|MSF|`http://schemas.microsoft.com/ws/2006/05/framing/policy`|  
|mssp|`http://schemas.microsoft.com/ws/2005/07/securitypolicy`|  
|přípon|`http://schemas.microsoft.com/ws/2005/12/wsdl/contract`|  
|bod|`http://schemas.microsoft.com/net/2006/06/duplex`|  
  
## <a name="wcf-wsdl11-extensions"></a>Rozšíření WCF WSDL 1.1  
 WCF používá následující rozšíření WSDL 1.1 k popisu požadavků na relaci smlouvy.  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 xs: Boolean označuje, že tato operace inicializuje relaci WCF; Výchozí hodnota je `false` .  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 xs: Boolean označuje, že tato operace ukončuje relaci WCF. Výchozí hodnota je `false` .  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs: Boolean znamená, že tato smlouva vyžaduje, aby byla vytvořena relace.  
  
### <a name="soap-1x-http-binding-transport-uris"></a>Identifikátory URI přenosu vazby protokolu SOAP 1. x  
 WCF používá následující identifikátory URI k označení přenosů, které se mají použít pro elementy rozšíření vazby WSDL 1,1, SOAP 1,1 a SOAP 1,2.  
  
|Přenos|Identifikátor URI|  
|---------------|---------|  
|HTTP|`http://schemas.xmlsoap.org/soap/http`|  
|TCP|`http://schemas.microsoft.com/soap/tcp`|  
|MSMQ|`http://schemas.microsoft.com/soap/msmq`|  
|Pojmenované kanály|`http://schemas.microsoft.com/soap/named-pipe`|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>Kontrolní výrazy zásad implementované službou WCF  
 Kromě kontrolních výrazů zásad zavedených ve specifikacích webových služeb (WS-*) a uvedených v dalších částech tohoto dokumentu WCF implementuje následující kontrolní výrazy zásad.  
  
|Kontrolní výraz zásady|Předmět zásad|Popis|  
|----------------------|--------------------|-----------------|  
|http: HttpBasicAuthentication|Koncový bod|Koncový bod používá základní ověřování HTTP.|  
|http: HttpDigestAuthentication|Koncový bod|Koncový bod používá ověřování pomocí protokolu HTTP Digest.|  
|http: HttpNegotiateAuthentication|Koncový bod|Koncový bod používá ověřování HTTP Negotiate.|  
|http: HttpNtlmAuthentication|Koncový bod|Koncový bod používá ověřování HTTP NTLM.|  
|MSF: streamované|Koncový bod|Koncový bod používá rámce streamování zpráv. Tento kontrolní výraz se používá spolu s protokolem rámců zpráv, který je k dispozici pro přenosy, jako je TCP a pojmenované kanály.|  
|MSF: SslTransportSecurity|Koncový bod|Koncový bod používá protokol TLS (Transport Layer Security) s rámcem zprávy.|  
|MSF: WindowsTransportSecurity|Koncový bod|Koncový bod používá vyjednávání poskytovatele zabezpečení (SPNEGO) s rámcem zprávy.|  
|MSMQ: MsmqBestEffort|Koncový bod|Služba MSMQ s doporučenými zárukami.|  
|MSMQ: MsmqSession|Koncový bod|Služba MSMQ s zárukami relací.|  
|MSMQ: MsmqVolatile|Koncový bod|Služba MSMQ je nestálá.|  
|MSMQ: ověřeno|Koncový bod|Ověřování se používá s přenosem MSMQ.|  
|MSMQ: WindowsDomain|Koncový bod|Služba MSMQ používá ověřování domény systému Windows.|  
|CDP: CompositeDuplex|Koncový bod|Koncový bod používá ke zprávám v a na odchozích dvou samostatných přenosů v opačném přenosu.|  
|mssp:RsaToken|Vnořen|Kontrolní výraz tokenu klíče RSA. Tento požadavek obvykle splňuje klíč RSA, který je serializován přímo jako součást informací o klíči v signatuře.|  
|mssp:SslContextToken|Vnořen|Vyžaduje, aby byl použit SecurityContextToken získaný pomocí binárního ověřování TLS metodou handshake pomocí protokolu WS-Trust. Vnořené kontrolní výrazy zahrnují: SP: RequireDerivedKeys, mssp: MustNotSendCancel, mssp: RequireClientCertificate.|  
|mssp:MustNotSendCancel|Vnořen|Určuje požadavek, aby žádosti o zprávy s žádostí o token zabezpečení (RST) požadavku (WS-Trust) s použitím zrušení vazby [WS-Trust, WS-SC] nebyly odesílány vystaviteli daného SecurityContextToken. Pokud je tento kontrolní výraz přítomen, nesmí být takové zprávy žádosti odesílány vystaviteli. Pokud tento kontrolní výraz není k dispozici, mohou být tyto zprávy žádosti odeslány vystaviteli.|  
|mssp:RequireClientCertificate|Vnořen|Tento volitelný prvek určuje požadavek, aby byl klientský certifikát poskytnut jako součást protokolu TLSNEGO. Pokud je tento kontrolní výraz k dispozici, je nutné zadat klientský certifikát. Pokud tento kontrolní výraz není k dispozici, nesmí být uveden klientský certifikát. Tento kontrolní výraz nesmí být použit mimo mssp: SslContextToken.|  
  
## <a name="see-also"></a>Viz také

- [Vlastní publikování WSDL](../samples/custom-wsdl-publication.md)
- [Postupy: Export vlastního WSDL](../extending/how-to-export-custom-wsdl.md)
- [Postupy: Import vlastního WSDL](../extending/how-to-import-custom-wsdl.md)
