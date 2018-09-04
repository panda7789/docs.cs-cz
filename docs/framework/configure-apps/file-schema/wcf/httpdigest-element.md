---
title: Element &lt;httpDigest&gt;
ms.date: 03/30/2017
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
ms.openlocfilehash: 4f3edb4a525429bfc55c4e4cfaffbfc5726dcef8
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521984"
---
# <a name="lthttpdigestgt-element"></a>Element &lt;httpDigest&gt;
Určuje výběru pověření používaný při ověřování klienta ke službě zadejte.  
  
 \<system.ServiceModel>  
\<chování >  
\<názvy endpointBehaviors >  
\<chování >  
\<třídu clientCredentials >  
\<httpDigest >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<digest impersonationLevel="Identification/Impersonation/Delegation/Anonymous/None" />  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`impersonationLevel`|Nastavuje předvolbu zosobnění, který klient komunikuje na server. Režim zosobnění, který klient vybere nevynucuje na serveru. Platné hodnoty patří:<br /><br /> -Identifikace: Na serveru můžete získat identit a oprávnění klienta, ale nelze zosobnit klienta.<br />-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.<br />-Delegování: Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.<br />-Anonymní: Server nelze zosobnit nebo identifikaci klienta.<br />-Žádný: Není přiřazena úroveň zosobnění.<br /><br /> Výchozí hodnota je identifikace. Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<třídu clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Určuje pověření pro ověření klienta ke službě.|  
  
## <a name="remarks"></a>Poznámky  
 Přehled je hodnota hash určit pomocí algoritmu a sadu vstupů. Ověřovacích a ověřeného odsouhlaste algoritmus a výměnu dat použít jako vstupy. Klient může vypočítat hodnotu hash a odesílat do služby. Služba také vypočítá hodnotu hash a porovnává hodnoty. Shoda ověří klienta.  
  
 Musí být povolena tato funkce se službou Active Directory na Windows a Internetové informační služby (IIS). Další informace najdete v tématu [ověřování algoritmem Digest ve službě IIS 6.0](https://go.microsoft.com/fwlink/?LinkId=88443).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement>  
 <xref:System.ServiceModel.Configuration.ClientCredentialsElement.HttpDigest%2A>  
 <xref:System.ServiceModel.Description.ClientCredentials>  
 <xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>  
 <xref:System.ServiceModel.Configuration.HttpDigestClientElement>  
 <xref:System.ServiceModel.Security.HttpDigestClientCredential>  
 [Chování zabezpečení](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)  
 [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
