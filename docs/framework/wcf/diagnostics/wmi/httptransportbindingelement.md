---
title: HttpTransportBindingElement
ms.date: 03/30/2017
ms.assetid: 088a7bce-6bb2-4839-ad74-f68d4b1aa0f9
ms.openlocfilehash: 2376a0ec25539b97a37b1827e3e4c148eb8d5838
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54610770"
---
# <a name="httptransportbindingelement"></a>HttpTransportBindingElement
HttpTransportBindingElement  
  
## <a name="syntax"></a>Syntaxe  
  
```csharp
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
 Třída elementu HttpTransportBindingElement nedefinuje žádné metody.  
  
## <a name="properties"></a>Vlastnosti  
 Třída elementu HttpTransportBindingElement má následující vlastnosti:  
  
### <a name="allowcookies"></a>AllowCookies  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Hodnota, která určuje, zda klient přijímá soubory cookie a šíří je v budoucích požadavcích.  
  
### <a name="authenticationscheme"></a>AuthenticationScheme  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Schéma ověření použité pro ověřování požadavků klientů, jenž jsou zpracovány při naslouchání protokolu HTTP.  
  
### <a name="bypassproxyonlocal"></a>BypassProxyOnLocal  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Hodnota, která určuje, zda jsou proxy servery pro lokální adresy ignorovány.  
  
### <a name="hostnamecomparisonmode"></a>HostNameComparisonMode  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Hodnota, která určuje, zda je ke zpřístupnění služby při shodě s identifikátoru URI používá název hostitele.  
  
### <a name="keepaliveenabled"></a>KeepAliveEnabled  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Při povolení připojení protokolu HTTP jsou zachováno bez ohledu na úroveň činnosti.  
  
### <a name="maxbuffersize"></a>MaxBufferSize  
 Datový typ: sint32  
  
 Typ přístupu: jen pro čtení  
  
 Maximální velikost fondu vyrovnávacích pamětí.  
  
### <a name="proxyaddress"></a>ProxyAddress  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Identifikátor URI, který obsahuje adresu proxy serveru použitého pro požadavky HTTP.  
  
### <a name="proxyauthenticationscheme"></a>ProxyAuthenticationScheme  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Schéma ověření použité pro ověřování požadavků klientů zpracovávaných HTTP proxy.  
  
### <a name="realm"></a>Sféra  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Sféra ověření.  
  
### <a name="transfermode"></a>TransferMode  
 Datový typ: řetězec  
  
 Typ přístupu: jen pro čtení  
  
 Hodnota, která určuje, zda jsou zprávy ukládány do vyrovnávací paměti nebo prostřednictvím datového proudu nebo žádost nebo odpověď.  
  
### <a name="unsafeconnectionntlmauthentication"></a>UnsafeConnectionNtlmAuthentication  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Hodnota, která určuje, zda je na serveru povoleno nezabezpečené sdílení připojení.  
  
### <a name="usedefaultwebproxy"></a>useDefaultWebProxy  
 Datový typ: boolean  
  
 Typ přístupu: jen pro čtení  
  
 Hodnota, která určuje, jestli uživatelovo specifické nastavení jsou upřednostňována nastavení proxy pro celý počítač.  
  
## <a name="requirements"></a>Požadavky  
  
|SOUBOR MOF|Deklarované v Servicemodel.mof.|  
|---------|-----------------------------------|  
|Obor názvů|Definované v root\ServiceModel|  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
