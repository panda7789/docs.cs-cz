---
title: <windows> z <clientCredentials> – Element
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: b5e92745b9e39534d2a0bc35504c2dbc8346d2ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769717"
---
# <a name="windows-of-clientcredentials-element"></a>\<Windows > z \<clientCredentials > – Element
Určuje nastavení pro přihlašovací údaje Windows k provádět reprezentovalo klienta.  
  
 \<system.ServiceModel>  
\<chování >  
\<endpointBehaviors>  
\<chování >  
\<clientCredentials>  
\<windows>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<windows allowedImpersonationLevel="Identification/Impersonation/Delegation/Anonymous/None"
         allowNtlm="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|`allowedImpersonationLevel`|Nastavuje předvolbu zosobnění, který klient komunikuje na server. Režim zosobnění, který klient vybere nevynucuje na serveru. Platné hodnoty patří:<br /><br /> -Identifikace: Na serveru můžete získat identit a oprávnění klienta, ale nelze zosobnit klienta.<br />-Zosobnění: Server může zosobnit kontext zabezpečení klienta v místním systému.<br />-Delegování: Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.<br />-Anonymní: Server nelze zosobnit nebo identifikaci klienta.<br />-Žádný: Úroveň zosobnění není přiřazen.<br /><br /> Výchozí hodnota je identifikace. Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.|  
|`allowNtlm`|Nastavení této vlastnosti na `true` umožňuje ověřování na starší verzi NTLM, pokud není k dispozici protokol Kerberos.<br /><br /> Nastavení této vlastnosti na `false` způsobí, že Windows Communication Foundation (WCF), aby se snažíme vyvolá výjimku, pokud je použit protokol NTLM. Všimněte si, že nastavení této vlastnosti na `false` nemůže zabránit odeslání při přenosu přihlašovacích údajů protokolů NTLM.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)|Určuje pověření pro ověření klienta ke službě.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [Zabezpečení klientů](../../../../../docs/framework/wcf/securing-clients.md)
- [Práce s certifikáty](../../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [Zabezpečení služeb a klientů](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
