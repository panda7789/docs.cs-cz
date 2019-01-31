---
title: <security> z <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: be3417296a401c002e59487cd4903e15e6301a63
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/30/2019
ms.locfileid: "55279796"
---
# <a name="security-of-nettcpbinding"></a>\<zabezpečení > z \<netTcpBinding >
Definuje nastavení zabezpečení pro vazbu.  
  
 \<system.ServiceModel>  
\<vazby >  
\<netTcpBinding>  
\<Vytvoření vazby >  
\<security>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<security mode="Message/None/Transport/TransportWithCredential">
  <transport clientCredentialType="Basic/Certificate/Digest/None/Ntlm/Windows"
             protectionLevel="None/Sign/EncryptAndSign" />
  <message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
           clientCredentialType="Certificate/IssuedToken/None/UserName/Windows" />
</security>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené elementy  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim|Volitelné. Určuje typ zabezpečení, který se použije. Platné hodnoty jsou uvedeny níže. Výchozí hodnota je `Transport`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>režim atribut  
  
|Hodnota|Popis|  
|-----------|-----------------|  
|Žádná|Zabezpečení je zakázaná.|  
|Přenos|Zabezpečení přenosu pomocí protokolu TLS přes protokol TCP nebo SPNego poskytuje. Služba možná potřeba nakonfigurovat s využitím certifikátů SSL. Je možné kontrolovat úroveň ochrany s tímto režimem.|  
|Zpráva|Poskytuje zabezpečení pomocí zabezpečení zprávy protokolu SOAP. Ve výchozím nastavení je SOAP body šifrované a podepsaný. Tento režim nabízí širokou škálu funkcí, jako je například, jestli přihlašovací údaje služby najdete na adrese klienta vzdáleně, sada algoritmů, které chcete použít a jaké úroveň ochrany a platí pro tělo zprávy. Ověření klienta se provádí jednou na relaci a výsledky ověření jsou ukládány do mezipaměti po dobu trvání relace.|  
|TransportWithMessageCredential|Zabezpečení přenosu je párována s zabezpečení zpráv. Zabezpečení přenosu pomocí protokolu TLS poskytuje přes protokol TCP nebo SPNego a zajistí integritu, šifrování a ověřování serveru. Zabezpečení zpráv SOAP poskytuje ověření klienta. Ve výchozím nastavení ověření klienta se provádí jednou na relaci a výsledky ověření jsou ukládány do mezipaměti po dobu trvání relace.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<transport>](../../../../../docs/framework/configure-apps/file-schema/wcf/transport-of-nettcpbinding.md)|Definuje nastavení zabezpečení pro přenos. Tento prvek je typu <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.|  
|[\<message>](../../../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)|Definuje nastavení zabezpečení pro zprávu. Tento prvek je typu <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|vazba|Prvek vazby [ \<netTcpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).|  
  
## <a name="remarks"></a>Poznámky  
 Všechny standardní vazby poskytuje parametry pro řízení požadavky na zabezpečení přenosu. Tyto parametry zahrnují obvykle režim zabezpečení, který určuje, zda se používá zabezpečení na úrovni zpráv nebo transportní vrstvy a výběr typu pověření klienta. Na základě volby možností tyto k dispozici, parametry zásobníku kanál je vytvořený pomocí příslušné zabezpečení.  
  
 Vazby poskytované systémem zadaný ve Windows Communication Foundation (WCF) jsou sady jsou navržené pro některé z nejčastějších požadavků scénáře. Každá z těchto vazeb umožňuje volbu specifikace požadavky na zabezpečení pro některé konkrétní cílové scénáře.  
  
 Tento prvek konfigurace obsahuje specifikace zabezpečení pro `netTcpBinding`. Toto je zabezpečená, spolehlivá a optimalizovaná vazby vhodné pro komunikaci mezi počítači. Ve výchozím nastavení vygeneruje podpora TCP pro doručování zpráv a zabezpečení Windows pro ověřování, WS-ReliableMessaging spolehlivost a kódování binární zprávy a zabezpečení zpráv komunikace zásobník modulu runtime.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../../../docs/framework/wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [\<Vytvoření vazby >](../../../../../docs/framework/misc/binding.md)
