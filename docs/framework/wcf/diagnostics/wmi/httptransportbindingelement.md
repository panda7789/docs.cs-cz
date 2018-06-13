---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 1975fd2e04a5c9cdb68bc838802abafbd781b7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487017"
---
# <a name="httptransportbindingelement"></a>HttpTransportBindingElement
HttpTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class HttpTransportBindingElement : TransportBindingElement  
{  
  boolean AllowCookies;  
  string AuthenticationScheme;  
  boolean BypassProxyOnLocal;  
  string HostNameComparisonMode;  
  boolean KeepAliveEnabled;  
  sint32 MaxBufferSize;  
  string ProxyAddress;  
  string ProxyAuthenticationScheme;  
  string Realm;  
  string TransferMode;  
  boolean UnsafeConnectionNtlmAuthentication;  
  boolean UseDefaultWebProxy;  
};  
```  
  
## <a name="methods"></a>Metody  
 Třída HttpTransportBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída HttpTransportBindingElement má následující vlastnosti:  
  
### <a name="allowcookies"></a>allowCookies  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která určuje, jestli klient přijímá soubory cookie a rozšiřuje je na dalších požadavků.  
  
### <a name="authenticationscheme"></a>AuthenticationScheme  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Schéma ověřování používá k ověření klientských požadavků zpracovávaných naslouchací proces protokolu HTTP.  
  
### <a name="bypassproxyonlocal"></a>BypassProxyOnLocal  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která označuje, zda jsou ignorovány proxy pro místní adresy.  
  
### <a name="hostnamecomparisonmode"></a>hostNameComparisonMode  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která označuje, zda se ke zpřístupnění služby při shodujícím v identifikátoru URI používá název hostitele.  
  
### <a name="keepaliveenabled"></a>KeepAliveEnabled  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Když je povolené, udržely připojení prostřednictvím protokolu HTTP aktivní bez ohledu na úrovni aktivity.  
  
### <a name="maxbuffersize"></a>maxBufferSize  
 Datový typ: sint32  
  
 Přístup k typu: jen pro čtení  
  
 Maximální velikost fondu vyrovnávací paměti.  
  
### <a name="proxyaddress"></a>proxyAddress  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Identifikátor URI, který obsahuje adresu proxy, který chcete použít pro požadavky HTTP.  
  
### <a name="proxyauthenticationscheme"></a>ProxyAuthenticationScheme  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Schéma ověřování používá k ověření klientských požadavků zpracovávaných proxy serveru HTTP.  
  
### <a name="realm"></a>sféry  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Sféra ověření.  
  
### <a name="transfermode"></a>transferMode  
 Datový typ: řetězec  
  
 Přístup k typu: jen pro čtení  
  
 Hodnotu, která určuje, zda jsou zprávy do vyrovnávací paměti nebo prostřednictvím datového proudu nebo požadavku nebo odpovědi.  
  
### <a name="unsafeconnectionntlmauthentication"></a>UnsafeConnectionNtlmAuthentication  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která určuje, zda je na serveru povoleno sdílení nezabezpečené připojení.  
  
### <a name="usedefaultwebproxy"></a>useDefaultWebProxy  
 Datový typ: logická hodnota  
  
 Přístup k typu: jen pro čtení  
  
 Hodnota, která určuje, zda jsou nastavení proxy serveru celého systému použít místo nastavení specifická pro uživatele.  
  
## <a name="requirements"></a>Požadavky  
  
|MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
