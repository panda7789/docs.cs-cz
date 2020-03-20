---
title: <x509SecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: aca22c2c-5ae7-42af-9bbd-15c2524692ce
author: BrucePerlerMS
ms.openlocfilehash: 30ce69a35cfdd34e0dfea5c682347eb9187e04ed
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79152447"
---
# <a name="x509securitytokenhandlerrequirement"></a>\<x509SecurityTokenHandlerRequirement>
Poskytuje volitelnou <xref:System.IdentityModel.Tokens.X509SecurityTokenHandler> konfiguraci pro třídu nebo odvozené třídy.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityKonfigurace>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<přidat>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<x509je>**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
        <x509SecurityTokenHandlerRequirement>  
          mapToWindows=xs:boolean  
          certificateValidationMode="None||ChainTrust||PeerTrust||PeerOrChainTrust||Custom"  
          certificateValidator="Namespace.Class, Assembly"  
          revocationMode="NoCheck||Offline||Online"  
          trustedStoreLocation="CurrentUser||LocalMachine"  
        </x509SecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|certificateValidationMode|Hodnota, <xref:System.ServiceModel.Security.X509CertificateValidationMode> která určuje režim ověření pro certifikát X.509. Výchozí hodnota je "PeerOrChainTrust".|  
|mapToWindows|Určuje, zda má obslužná rutina tokenu mapovat ověřovací token na účet systému Windows pomocí příchozí deklarace hlavního název uživatele. Výchozí hodnota je "false".|  
|režim odvolání|Hodnota, <xref:System.Security.Cryptography.X509Certificates.X509RevocationMode> která určuje režim odvolání, který má být pro certifikát X.509 používán. Výchozí hodnota je "Online".|  
|trustedStoreLocation|Hodnota, <xref:System.Security.Cryptography.X509Certificates.StoreLocation> která určuje úložiště certifikátů X.509. Výchozí hodnota je "LocalMachine".|  
|certifikátValidator|Vlastní typ, který <xref:System.IdentityModel.Selectors.X509CertificateValidator>je odvozen od . Pokud `certificateValidationMode` je atribut "Vlastní", instance tohoto typu se používá pro ověření certifikátu vystavitho.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádný  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|Element|Popis|  
|-------------|-----------------|  
|[\<přidat>](add.md)|Přidá zadanou obslužnou rutinu tokenu do kolekce obslužné rutiny tokenu.|  
  
## <a name="example"></a>Příklad  
  
```xml  
<add type="System.IdentityModel.Tokens.X509SecurityTokenHandler, System.IdentityModel">  
    <x509SecurityTokenHandlerRequirement mapToWindows="true"
                                         certificateValidationMode="PeerOrChainTrust"
                                         revocationMode="Online"
                                         trustedStoreLocation="LocalMachine" />  
</add>  
```
