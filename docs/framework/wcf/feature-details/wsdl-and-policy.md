---
title: WSDL a zásady
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cea87440-3519-4640-8494-b8a2b0e88c84
caps.latest.revision: ''
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: dd52e36199fc2412abb003d530dd5614cda8049b
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/26/2018
---
# <a name="wsdl-and-policy"></a>WSDL a zásady
Toto téma popisuje [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] WSDL 1.1, WS-zásady a WS-PolicyAttachment podrobnosti implementace, a také další služby WS-Policy kontrolní výrazy a rozšíření WSDL 1.1 zaváděné [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementuje specifikace WS-Policy a WS-PolicyAttachment odeslána W3C s omezení a objasnění, která jsou popsaná v tomto dokumentu.  
  
 Tento dokument používá předpony a obory názvů uvedené v následující tabulce.  
  
|Předpona|Obor názvů|  
|------------|---------------|  
|WSP (WS-Policy 1.2)|http://schemas.xmlsoap.org/ws/2004/09/policy|  
|WSP (WS-Policy 1.5)|http://www.w3.org/ns/ws-policy|  
|http|http://schemas.microsoft.com/ws/06/2004/policy/http|  
|msmq|http://schemas.microsoft.com/ws/06/2004/mspolicy/msmq|  
|msf|http://schemas.microsoft.com/ws/2006/05/framing/policy|  
|mssp|http://schemas.microsoft.com/ws/2005/07/securitypolicy|  
|msc|http://schemas.microsoft.com/ws/2005/12/wsdl/contract|  
|cdp|http://schemas.microsoft.com/net/2006/06/duplex|  
  
## <a name="wcf-wsdl11-extensions"></a>WSDL1.1 rozšíření WCF  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí následující přípony WSDL1.1 popisují požadavky relace kontrakt.  
  
 wsdl:portType/wsdl:operation/@msc:isInitiating  
 xs:Boolean, označuje tato operace spustí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] relace; výchozí hodnota je `false`.  
  
 wsdl:portType/wsdl:operation/@msc:isTerminating  
 xs:Boolean, označuje tato operace se ukončí [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] relace; výchozí hodnota je `false`.  
  
 wsdl:portType/wsdl:operation/@msc:usingSession  
 xs:Boolean, označuje, že tento kontrakt vyžaduje relace, která má být vytvořeno.  
  
### <a name="soap-1x-http-binding-transport-uris"></a>Identifikátory URI přenosu protokolu SOAP 1.x HTTP vazby  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pomocí následující identifikátory URI označuje přenosy má být použit pro WSDL 1.1, SOAP 1.1 a SOAP 1.2 prvky vazeb rozšíření.  
  
|Přenos|Identifikátor URI|  
|---------------|---------|  
|HTTP|http://schemas.xmlsoap.org/soap/http|  
|TCP|http://schemas.microsoft.com/soap/tcp|  
|MSMQ|http://schemas.microsoft.com/soap/msmq|  
|Pojmenované kanály|http://schemas.microsoft.com/soap/named-pipe|  
  
## <a name="policy-assertions-implemented-by-wcf"></a>Kontrolní výrazy zásad implementované WCF  
 Kromě kontrolních výrazů zásad byla zavedená v specifikace Web Services (WS-*) a uvedených v dalších částech tohoto dokumentu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] implementuje následující výrazy zásad.  
  
|Výraz zásad|Zásady subjektu|Popis|  
|----------------------|--------------------|-----------------|  
|http:HttpBasicAuthentication|Koncový bod|Koncový bod používá základní ověřování protokolu HTTP.|  
|http:HttpDigestAuthentication|Koncový bod|Koncový bod používá ověřování hodnotou hash protokolu HTTP.|  
|http:HttpNegotiateAuthentication|Koncový bod|Koncový bod používá ověřování vyjednávání protokolu HTTP.|  
|http:HttpNtlmAuthentication|Koncový bod|Koncový bod používá ověřování protokolem NTLM HTTP.|  
|msf:Streamed|Koncový bod|Koncový bod používá rámce přenášené datovými proudy zpráv. Tento kontrolní výraz součásti se používá s protokolem rámců zpráv poskytuje pro přenosy, jako je například TCP a pojmenované kanály.|  
|msf:SslTransportSecurity|Koncový bod|Koncový bod používá (TLS) transport layer security s rámce zpráv.|  
|msf:WindowsTransportSecurity|Koncový bod|Koncový bod používá zprostředkovatel zabezpečení vyjednávání (SPNEGO) s rámce zpráv.|  
|MSMQ:MsmqBestEffort|Koncový bod|MSMQ s best effort záruky.|  
|MSMQ:MsmqSession|Koncový bod|MSMQ s relace záruky.|  
|msmq:MsmqVolatile|Koncový bod|Volatile služby MSMQ.|  
|MSMQ: ověření|Koncový bod|Ověřování se používá s přenos MSMQ.|  
|msmq:WindowsDomain|Koncový bod|MSMQ používá ověřování domény systému Windows.|  
|cdp:CompositeDuplex|Koncový bod|Koncový bod používá dva samostatné opačný připojení přenosu pro vstup a výstup zprávy.|  
|mssp:RsaToken|Vnořené|Výraz klíče tokenu RSA. Tento požadavek je obvykle uspokojit klíč RSA serializovat přímo jako součást informace o klíči v či identifikaci podpisu.|  
|mssp:SslContextToken|Vnořené|Vyžaduje, že SecurityContextToken, získat pomocí binární TLS handshake pomocí WS-Trust používat. Zahrnout vnořené kontrolní výrazy: sp:RequireDerivedKeys, mssp:MustNotSendCancel, mssp:RequireClientCertificate.|  
|mssp:MustNotSendCancel|Vnořené|Určuje, že žádost o token zabezpečení (RVNÍ) požádat o zprávy [WS-Trust] zrušit vazbu [WS-Trust, WS-SC] požadavek nebyla posílá vystavitele daného SecurityContextToken. Pokud se nachází tento kontrolní výraz součásti, nesmí takové zprávy žádosti odeslané do vystavitele. Pokud tento kontrolní výraz součásti není k dispozici, můžete takové zprávy žádosti odeslané do vystavitele.|  
|mssp:RequireClientCertificate|Vnořené|Tento volitelný element určuje požadavek na klientský certifikát, který je třeba zadat jako součást TLSNEGO protokolu. Pokud se tento kontrolní výraz součásti nachází, je třeba zadat klientský certifikát. Pokud tento kontrolní výraz součásti není k dispozici, nesmí být zadán certifikát klienta. Tento kontrolní výraz součásti se nesmí používat mimo mssp:SslContextToken.|  
  
## <a name="see-also"></a>Viz také  
 [Vlastní publikování WSDL](../../../../docs/framework/wcf/samples/custom-wsdl-publication.md)  
 [Postupy: Export vlastního WSDL](../../../../docs/framework/wcf/extending/how-to-export-custom-wsdl.md)  
 [Postupy: Import vlastního WSDL](../../../../docs/framework/wcf/extending/how-to-import-custom-wsdl.md)
