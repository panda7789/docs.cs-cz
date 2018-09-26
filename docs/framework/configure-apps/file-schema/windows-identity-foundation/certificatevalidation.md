---
title: '&lt;certificateValidation&gt;'
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: 29881be43f02d275ad135efd97dc8b25a7409beb
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/25/2018
ms.locfileid: "47074785"
---
# <a name="ltcertificatevalidationgt"></a>&lt;certificateValidation&gt;
Určuje nastavení, které obslužné rutiny tokenů používat ověřování certifikátů. Tato nastavení jsou přepsány, pokud jsou nakonfigurované vlastní validátor konkrétní obslužnou rutinou.  
  
 \<system.identityModel>  
\<identityConfiguration >  
\<certificateValidation >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <certificateValidation  
      certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
      revocationMode="NoCheck||Offline||Online"  
      trustedStoreLocation="CurrentLocation||LocalMachine" >  
    </certificateValidation>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|certificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode> Hodnota, která určuje režim ověřování, který chcete použít pro certifikát X.509. Výchozí hodnota je "PeerOrChainTrust". Pokud chcete zadat vlastní validátor, tento atribut nastaven na "Vlastní" a zadejte validátor pomocí [ \<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md) elementu. Volitelné.|  
|revocationMode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> Hodnota, která určuje režim odvolání pro certifikát X.509. Výchozí hodnota je "Online". Volitelné.|  
|trustedStoreLocation|A <xref:System.Security.Cryptography.X509Certificates.StoreLocation> hodnota, která určuje úložiště certifikátů X.509. Výchozí hodnota je "LocalMachine". Volitelné.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<certificateValidator >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidator.md)|Určuje vlastní typ pro ověření certifikátu. Tento typ se používá jenom v případě, `certificateValidationMode` atribut [ \<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md) prvek je nastaven na "Vlastní".|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Popis|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|Určuje nastavení identit na úrovni služby.|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|Konfigurace pro kolekci zabezpečení poskytuje obslužné rutiny tokenů.|  
  
## <a name="remarks"></a>Poznámky  
 A `<certificateValidation>` element se dá nastavit na úrovni služby v rámci `<identityConfiguration>` element nebo na úrovni kolekce obslužné rutiny tokenů zabezpečení v rámci `<securityTokenHandlerConfiguration>` elementu. Nastavení kolekce obslužné rutiny tokenů přepíšou nastavení zadané ve službě. Některé obslužné rutiny tokenů vám umožňují určit nastavení ověření certifikátu v konfiguraci. Nastavení na jednotlivých obslužné rutiny tokenů přepsat zadaný na úrovni služby a na kolekci obslužné rutiny tokenů zabezpečení.  
  
## <a name="example"></a>Příklad  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
