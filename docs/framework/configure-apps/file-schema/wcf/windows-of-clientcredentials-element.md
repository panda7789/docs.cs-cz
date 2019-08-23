---
title: <windows><clientCredentials> elementu
ms.date: 03/30/2017
ms.assetid: 793e41c2-31ea-4159-abbc-2123bf097233
ms.openlocfilehash: e9f0ed9879cc42ea25b83e6b626139a40a593112
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940299"
---
# <a name="windows-of-clientcredentials-element"></a>\<> \<prvku ClientCredentials > elementu Windows
Určuje nastavení pro přihlašovací údaje systému Windows, které se mají použít k reprezentaci klienta.  
  
 \<system.ServiceModel>  
\<> chování  
\<endpointBehaviors>  
\<> chování  
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
|`allowedImpersonationLevel`|Nastaví předvolbu zosobnění, kterou klient komunikuje se serverem. Režim zosobnění, který klient vybere, není na serveru vynutil. Platné hodnoty jsou následující:<br /><br /> Identifikace Server může získat identitu a oprávnění klienta, ale nemůže zosobnit klienta.<br />Zosobnění Server může zosobnit kontext zabezpečení klienta v místním systému.<br />Delegování Server může zosobnit kontext zabezpečení klienta ve vzdálených systémech.<br />Anonymous Server nemůže zosobnit nebo identifikovat klienta.<br />NTato Úroveň zosobnění není přiřazena.<br /><br /> Výchozí hodnota je identifikace. Tento atribut je typu <xref:System.Security.Principal.TokenImpersonationLevel>.|  
|`allowNtlm`|Nastavením této vlastnosti `true` umožníte, aby se ověřování downgradal na NTLM, pokud není k dispozici protokol Kerberos.<br /><br /> Nastavení této vlastnosti na `false` způsobí, že Windows Communication Foundation (WCF) vyvolá výjimku, pokud se používá protokol NTLM. Všimněte si, že nastavení této `false` vlastnosti na nemusí bránit v posílání přihlašovacích údajů NTLM přes tento kabel.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|Určuje přihlašovací údaje, které se použijí k ověření klienta ke službě.|  
  
## <a name="see-also"></a>Viz také:

- <xref:System.ServiceModel.Configuration.WindowsClientElement>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Configuration.ClientCredentialsElement.Windows%2A>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>
- <xref:System.ServiceModel.Security.WindowsClientCredential>
- [Zabezpečení klientů](../../../wcf/securing-clients.md)
- [Práce s certifikáty](../../../wcf/feature-details/working-with-certificates.md)
- [Zabezpečení služeb a klientů](../../../wcf/feature-details/securing-services-and-clients.md)
