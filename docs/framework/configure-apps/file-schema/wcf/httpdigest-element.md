---
title: Element <httpDigest>
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 121df39c7e4ce4de5c1f0ef87921f6269d7cc1c0
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70785823"
---
# <a name="httpdigest-element"></a>\<httpDigest – element >
Určuje typ Digest, který se použije při ověřování klienta ke službě.  
  
[ **\<> Konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. serviceModel >** ](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> chování**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> clientCredentials**](clientcredentials.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<httpDigest >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<httpDigest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`impersonationLevel`|Nastaví předvolbu zosobnění, kterou klient komunikuje se serverem. Režim zosobnění, který klient vybere, není na serveru vynutil. Platné hodnoty jsou následující:<br /><br /> Identifikace Server může získat identitu a oprávnění klienta, ale nemůže zosobnit klienta.<br />Zosobnění Server může zosobnit kontext zabezpečení klienta v místním systému.<br />Delegování Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.<br />Anonymous Server nemůže zosobnit nebo identifikovat klienta.<br />NTato Úroveň zosobnění není přiřazena.<br /><br /> Výchozí hodnota je identifikace. Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Určuje přihlašovací údaje, které se používají k ověření klienta ke službě.|  
  
## <a name="remarks"></a>Poznámky  
 Výtah je hodnota hash určená pomocí algoritmu a sady vstupů. Ověřovatel a ověřené souhlas s algoritmem a vyměňují data použitá jako vstupy. Klient může vypočítat hodnotu hash a odeslat ji do služby. Služba také vypočítá hodnotu hash a porovná hodnoty. Shoda ověří klienta.  
  
 Tato funkce musí být povolená se službou Active Directory ve Windows a Internetová informační služba (IIS). Další informace najdete v tématu [ověřování algoritmem Digest ve službě IIS 6,0](https://go.microsoft.com/fwlink/?LinkId=88443).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>
- <xref:System.ServiceModel.Configuration.HttpDigestClientElement>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential>
- [Chování zabezpečení](../../../wcf/feature-details/security-behaviors-in-wcf.md)
- [Zabezpečení klientů](../../../wcf/securing-clients.md)
- [Práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
