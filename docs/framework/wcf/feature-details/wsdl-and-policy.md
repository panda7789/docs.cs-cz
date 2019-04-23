---
title: WSDL a zásady
ms.date: 03/30/2017
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
ms.openlocfilehash: caaa54f04bbb10ed3b3dd65b53ace633b88f9126
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59151902"
---
# <a name="wsdl-and-policy"></a>WSDL a zásady
Toto téma popisuje Windows Communication Foundation (WCF) WSDL 1.1, WS-Policy a WS-PolicyAttachment podrobnosti implementace, stejně jako další WS-Policy kontrolní výrazy a rozšíření WSDL 1.1 zavedené WCF.  
  
 WCF implementuje specifikace WS-Policy a WS-PolicyAttachment odeslané do W3C s omezením a vyjasnění popsané v tomto dokumentu.  
  
 Tento dokument používá předpony a obory názvů uvedené v následující tabulce.  
  
|Předpona|Obor názvů|  
|------------|---------------|  
|soubor WSP (WS-Policy 1.2)|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|soubor WSP (WS-Policy 1.5)|http://www.w3.org/ns/ws-policy|  
|http|http://schemas.microsoft.com/ws/06/2004/policy/http|  
|msmq|http://schemas.microsoft.com/ws/06/2004/mspolicy/msmq|  
|msf|http://schemas.microsoft.com/ws/2006/05/framing/policy|  
|mssp|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
|msc|http://schemas.microsoft.com/ws/2005/12/wsdl/contract|  
|cdp|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="wcf-wsdl11-extensions"></a>WSDL1.1 rozšíření WCF  
 WCF používá následující rozšíření WSDL1.1 k popisu požadavky Smlouvy relace.  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 xs:Boolean, označuje, že tato operace spustí relaci WCF. Výchozí hodnota je `false`.  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 xs:Boolean, označuje, že tato operace ukončí relaci WCF. Výchozí hodnota je `false`.  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs:Boolean, označuje, že tato smlouva vyžaduje relaci navázat.  
  
### <a name="soap-1x-http-binding-transport-uris"></a>Identifikátory URI SOAP 1.x HTTP vazby přenosu  
 WCF následující identifikátory URI používá k označení přenosů má být použit pro elementy rozšíření vazby WSDL 1.1, SOAP 1.1 a SOAP 1.2.  
  
|Přenos|Identifikátor URI|  
|---------------|---------|  
|HTTP|http://schemas.xmlsoap.org/soap/http|  
|TCP|http://schemas.microsoft.com/soap/tcp|  
|MSMQ|http://schemas.microsoft.com/soap/msmq|  
|Pojmenované kanály|http://schemas.microsoft.com/soap/named-pipe|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>Kontrolní výrazy zásad implementované WCF  
 Kromě kontrolní výrazy zásad, které jsou součástí specifikace Web Services (WS-*) a uvedených v dalších částech tohoto dokumentu, WCF implementuje následující kontrolní výrazy zásad.  
  
|Kontrolní výraz zásad|Předmět zásad|Popis|  
|----------------------|--------------------|-----------------|  
|http:HttpBasicAuthentication|Koncový bod|Koncový bod používá HTTP Basic Authentication.|  
|http:HttpDigestAuthentication|Koncový bod|Koncový bod používá ověřování pomocí protokolu HTTP Digest.|  
|http:HttpNegotiateAuthentication|Koncový bod|Koncový bod používá ověřování vyjednávání protokolu HTTP.|  
|http:HttpNtlmAuthentication|Koncový bod|Koncový bod používá ověřování protokolem NTLM HTTP.|  
|msf:Streamed|Koncový bod|Koncový bod používá rámce datový proud zprávy. Tento kontrolní výraz se používá s protokolem rámce zpráv poskytuje pro přenosy, jako je například TCP a pojmenované kanály.|  
|msf:SslTransportSecurity|Koncový bod|Koncový bod používá zabezpečení přenosové vrstvy (TLS) s rámce zpráv.|  
|msf:WindowsTransportSecurity|Koncový bod|Koncový bod používá zprostředkovatel zabezpečení vyjednávání (SPNEGO) s rámce zpráv.|  
|msmq:MsmqBestEffort|Koncový bod|Služby MSMQ s best effort zárukami.|  
|MSMQ:MsmqSession|Koncový bod|Zaručuje služby MSMQ s relací.|  
|msmq:MsmqVolatile|Koncový bod|Volatile služby MSMQ.|  
|msmq:Authenticated|Koncový bod|Ověřování se používá u přenosu služby MSMQ.|  
|msmq:WindowsDomain|Koncový bod|Ověřování v doméně Windows používaný službou MSMQ.|  
|cdp:CompositeDuplex|Koncový bod|Koncový bod používá dvě samostatné opačný přenosové připojení pro ani výstupní zprávy.|  
|mssp:RsaToken|Vnořené|Výraz klíče tokenu RSA. Tento požadavek obvykle splněn serializovat přímo jako součást informací o klíči v podporujícími podpis klíčem RSA.|  
|mssp:SslContextToken|Vnořené|Vyžaduje použít SecurityContextToken pomocí binární TLS handshake pomocí WS-Trust. Vnořené výrazy zahrnují: sp:RequireDerivedKeys, mssp:MustNotSendCancel, mssp:RequireClientCertificate.|  
|mssp:MustNotSendCancel|Vnořené|Určuje, že žádost o token zabezpečení (RVNÍ) požádat o zprávy [WS-Trust] zrušit vazbu [WS-Trust, WS-SC] požadavek neposílali na vydavatele dané SecurityContextToken. Pokud tento kontrolní výraz je k dispozici, nesmí tyto zprávy žádosti odeslané na vydavatele. Pokud tento kontrolní výraz není k dispozici, můžete takové žádosti o zprávy odeslané na vydavatele.|  
|mssp:RequireClientCertificate|Vnořené|Tento volitelný prvek určuje požadavek na klientský certifikát, který se poskytuje jako součást TLSNEGO protokolu. Pokud tento kontrolní výraz je k dispozici, musí být zadaná klientský certifikát. Pokud tento kontrolní výraz není k dispozici, nesmí být zadaná klientský certifikát. Tento kontrolní výraz se nesmí používat mimo mssp:SslContextToken.|  
  
## <a name="see-also"></a>Viz také:

- [Vlastní publikování WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)
- [Postupy: Export vlastního WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)
- [Postupy: Import vlastního WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
