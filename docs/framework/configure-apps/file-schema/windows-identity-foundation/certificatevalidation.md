---
title: <certificateValidation>
ms.date: 03/30/2017
ms.assetid: 6c54c704-b55e-4631-88ff-4d4a5621554c
author: BrucePerlerMS
ms.openlocfilehash: c2d1a5d36cb5616ef06eedc093dd70a68a164a81
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252135"
---
# \<certificateValidation>
Určuje nastavení, které obslužné rutiny tokenů používají k ověření certifikátů. Tato nastavení jsou přepsána, pokud je konkrétní obslužná rutina nakonfigurována pomocí vlastního validátoru.  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<certificateValidation>**  
  
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
|certificateValidationMode|<xref:System.ServiceModel.Security.X509CertificateValidationMode>Hodnota, která určuje režim ověřování, který má být použit pro certifikát X. 509. Výchozí hodnota je "PeerOrChainTrust". Chcete-li určit vlastní validátor, nastavte tento atribut na hodnotu "Custom" a určete validátor pomocí [\<certificateValidator>](certificatevalidator.md) elementu. Nepovinný parametr.|  
|revocationMode|<xref:System.Security.Cryptography.X509Certificates.X509RevocationMode>Hodnota, která určuje režim odvolání, který se má použít pro certifikát X. 509. Výchozí hodnota je "online". Nepovinný parametr.|  
|trustedStoreLocation|<xref:System.Security.Cryptography.X509Certificates.StoreLocation>Hodnota, která určuje úložiště certifikátů X. 509. Výchozí hodnota je "LocalMachine". Nepovinný parametr.|  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<certificateValidator>](certificatevalidator.md)|Určuje vlastní typ pro ověření certifikátu. Tento typ se používá jenom v případě, že `certificateValidationMode` [\<certificateValidation>](certificatevalidation.md) je atribut elementu nastavený na Custom (vlastní).|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Prvek|Description|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|Určuje nastavení identity na úrovni služby.|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|Poskytuje konfiguraci pro kolekci obslužných rutin tokenů zabezpečení.|  
  
## <a name="remarks"></a>Poznámky  
 `<certificateValidation>`Element lze zadat na úrovni služby pod `<identityConfiguration>` prvkem nebo na úrovni kolekce obslužné rutiny tokenu zabezpečení pod `<securityTokenHandlerConfiguration>` prvkem. Nastavení v kolekci obslužných rutin tokenu přepíší hodnoty zadané ve službě. Některé obslužné rutiny tokenů umožňují zadat nastavení ověřování certifikátů v konfiguraci. Nastavení u jednotlivých obslužných rutin tokenů přepíší ty zadané na úrovni služby i v kolekci obslužné rutiny tokenů zabezpečení.  
  
## <a name="example"></a>Příklad  
  
```xml  
<certificateValidation certificateValidationMode="PeerOrChainTrust"  
                       revocationMode="Online"  
                       trustedStoreLocation="LocalMachine" />  
```
