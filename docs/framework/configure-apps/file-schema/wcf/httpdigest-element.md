---
title: Element &lt;httpDigest&gt;
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3da4f276-dfd9-4247-8c07-01d83618727c
caps.latest.revision: "12"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 22c89aa69ea686274bb232eb04eec930ffc5b51d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="lthttpdigestgt-element"></a>Element &lt;httpDigest&gt;
Určuje výtah zadejte pověření používaná při ověřování klienta ke službě.  
  
 \<systém. ServiceModel >  
\<chování >  
\<endpointBehaviors >  
\<chování >  
\<clientCredentials >  
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
|`impersonationLevel`|Nastaví zosobnění předvoleb, které klient komunikuje se serverem. Režim zosobnění, který klient vybere nevynucuje na serveru. Platné hodnoty patří:<br /><br /> -Identifikace: Na serveru můžete získat identitu a oprávnění klienta, ale nelze zosobnit klienta.<br />-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.<br />-Delegování: Server může zosobnit kontext zabezpečení klienta na vzdálené systémy.<br />-Anonymní: Server nelze zosobnit nebo identifikaci klienta.<br />-None: Není přiřazen úroveň zosobnění.<br /><br /> Výchozí hodnota je identifikace. Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Určuje pověření použitá k ověření klienta pro službu.|  
  
## <a name="remarks"></a>Poznámky  
 Algoritmu digest je hodnota hash určit pomocí algoritmu a sadu vstupy. Ověřovatele a ověřený odsouhlaste algoritmu a výměnu dat použít jako vstupy. Klienta můžete vypočítat hodnotu hash a odeslat do služby. Služba také vypočte hash a porovnává hodnoty. Shoda ověří klienta.  
  
 Musí být povolena tato funkce se službou Active Directory ve Windows a Internetové informační služby (IIS). [!INCLUDE[crdefault](../../../../../includes/crdefault-md.md)][Ve službě IIS 6.0 ověřování algoritmem digest](http://go.microsoft.com/fwlink/?LinkId=88443).  
  
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
