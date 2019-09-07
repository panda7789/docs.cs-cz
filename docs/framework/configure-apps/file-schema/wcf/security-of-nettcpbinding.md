---
title: <security> z <netTcpBinding>
ms.date: 03/30/2017
ms.assetid: 286cd191-4fd5-4c4e-a223-9c71cf7fdead
ms.openlocfilehash: 971b1ea979877f631766e438cc41bc0bdabfd346
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399803"
---
# <a name="security-of-nettcpbinding"></a>\<> zabezpečení > \<NetTcpBinding
Definuje nastavení zabezpečení pro vazbu.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> vazeb**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netTcpBinding >** ](nettcpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> vazby**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> zabezpečení**  
  
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
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|režim|Volitelný parametr. Určuje typ zabezpečení, který se použije. Platné hodnoty jsou uvedeny níže. Výchozí hodnota je `Transport`.<br /><br /> Tento atribut je typu <xref:System.ServiceModel.SecurityMode>.|  
  
## <a name="mode-attribute"></a>mode – atribut  
  
|Value|Popis|  
|-----------|-----------------|  
|Žádné|Zabezpečení je zakázané.|  
|Přepravu|Zabezpečení přenosu se zajišťuje pomocí protokolu TLS přes TCP nebo SPNego. Je možné, že služba bude muset být nakonfigurovaná s certifikáty SSL. Úroveň ochrany je možné řídit pomocí tohoto režimu.|  
|Message|Zabezpečení je k dispozici pomocí protokolu SOAP Message Security. Ve výchozím nastavení je tělo protokolu SOAP šifrované a podepsané. Tento režim nabízí celou řadu funkcí, například zda jsou přihlašovací údaje služby k dispozici na klientovi mimo IP síť, Sada algoritmů, která se má použít, a úroveň ochrany, která se má použít pro tělo zprávy. Ověřování klienta se provádí jednou pro každou relaci a výsledky ověřování se ukládají do mezipaměti po dobu trvání relace.|  
|TransportWithMessageCredential|Zabezpečení přenosu se zapojí se zabezpečením zpráv. Zabezpečení přenosu je zajišťováno protokolem TLS přes TCP nebo SPNego a zajišťuje integritu, důvěrnost a ověřování serveru. Zabezpečení zpráv SOAP poskytuje ověřování klientů. Ve výchozím nastavení se ověřování klientů provádí jednou pro každou relaci a výsledky ověřování jsou ukládány do mezipaměti po dobu trvání relace.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<> přenosu](transport-of-nettcpbinding.md)|Definuje nastavení zabezpečení pro přenos. Tento prvek je typu <xref:System.ServiceModel.Configuration.TcpTransportSecurityElement>.|  
|[\<> zprávy](message-element-of-nettcpbinding.md)|Definuje nastavení zabezpečení zprávy. Tento prvek je typu <xref:System.ServiceModel.Configuration.MessageSecurityOverTcpElement>.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|vazba|[ Prvek\<vazby > NetTcpBinding](nettcpbinding.md).|  
  
## <a name="remarks"></a>Poznámky  
 Každá ze standardních vazeb poskytuje parametry pro řízení požadavků na zabezpečení přenosu. Mezi tyto parametry obvykle patří režim zabezpečení, který určuje, jestli se používá zabezpečení na úrovni zprávy nebo přenosu, a volba typu přihlašovacích údajů klienta. V závislosti na výběru možností, které jsou k dispozici, je zásobník kanálů vytvořen s odpovídajícím zabezpečením.  
  
 Vazby poskytnuté systémem, které poskytuje Windows Communication Foundation (WCF), jsou sady navržené tak, aby splňovaly některé z nejběžnějších požadavků na scénář. Každá z těchto vazeb umožňuje specifikaci požadavků zabezpečení pro některé konkrétní cílené scénáře.  
  
 Tento prvek konfigurace poskytuje specifikace zabezpečení pro `netTcpBinding`. Toto je zabezpečená, spolehlivá a optimalizovaná vazba vhodná pro komunikaci mezi počítači. Ve výchozím nastavení vygeneruje komunikační zásobník za běhu podporující protokol TCP pro doručování zpráv a zabezpečení systému Windows pro zabezpečení a ověřování zpráv, WS-ReliableMessaging pro zajištění spolehlivosti a kódování binárních zpráv.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.NetTcpSecurity>
- <xref:System.ServiceModel.NetTcpBinding.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpBindingElement.Security%2A>
- <xref:System.ServiceModel.Configuration.NetTcpSecurityElement>
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
- [Vazby](../../../wcf/bindings.md)
- [Konfigurace vazeb poskytovaných systémem](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [Používání vazeb ke konfiguraci služeb a klientů](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<> vazby](../../../misc/binding.md)
