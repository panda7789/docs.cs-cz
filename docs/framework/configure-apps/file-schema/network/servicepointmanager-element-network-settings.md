---
title: '&lt;ServicePointManager –&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 5903174f125938923a63fc031421a8d5a020e56d
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32753583"
---
# <a name="ltservicepointmanagergt-element-network-settings"></a>&lt;ServicePointManager –&gt; – Element (nastavení sítě)
Nakonfiguruje připojení k síťovým prostředkům.  
  
 \<Konfigurace >  
\<system.net>  
\<Nastavení >  
\<ServicePointManager – >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<servicePointManager  
  checkCertificateName="true|false"  
  checkCertificateRevocationList="true|false"  
  encryptionPolicy="AllowNoEncryption|NoEncryption|RequireEncryption"  
  expect100Continue="true|false"  
  useNagleAlgorithm="true|false"  
  enableDnsRoundRobin="true|false"  
  dnsRefreshTimeout="time"  
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Atribut**|**Popis**|  
|-------------------|---------------------|  
|`checkCertificateName`|Určuje, zda systém by měl ověřit, jestli názvem na certifikátu odpovídá název hostitele serveru před použitím certifikátu. Výchozí hodnota je `true`.|  
|`checkCertificateRevocationList`|Určuje, zda systému měli zkontrolovat, zda certifikát byl odvolán. před použitím certifikátu. Výchozí hodnota je `false`.|  
|`dnsRefreshTimeout`|Určuje, jak dlouho služby DNS (Domain Name) v mezipaměti řešení ve spojení s parametrem kruhové dotazování DNS v milisekundách. Výchozí hodnota je 120 000 milisekund (dvě minuty).|  
|`enableDnsRoundRobin`|Určuje, zda rozlišení DNS hostitele názvy s více adres Internet Protocol (IP), návratový všechny adresy nebo pouze první z nich. Výchozí hodnota je `false`.|  
|`encryptionPolicy`|Určuje zásady šifrování použít relaci SSL/TLS na <xref:System.Net.ServicePointManager> instance. Možné hodnoty jsou ekvivalentem hodnoty <xref:System.Net.Security.EncryptionPolicy> výčtu. Použití <xref:System.Security.Authentication.CipherAlgorithmType.Null> je požadované zásady šifrování je nastavena na `NoEncryption`. Výchozí hodnota je `RequireEncryption`.|  
|`expect100Continue`|Určuje, zda by měl očekávat metody POST `100-continue` odpověď ze serveru. Výchozí hodnota je `true`.|  
|`useNagleAlgorithm`|Určuje, zda řídí správce služby bodu připojení používat Nagle algoritmus. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Nastavení](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Nakonfiguruje možnosti základní sítě <xref:System.Net> oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Net.ServicePointManager>  
 <xref:System.Net.Security.EncryptionPolicy>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
