---
title: <servicePointManager> – Element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: 407ed85de109a671030eccff8ddd92af91628014
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59202206"
---
# <a name="servicepointmanager-element-network-settings"></a>\<Třída servicePointManager > – Element (nastavení sítě)
Nakonfiguruje připojení k síťovým prostředkům.  
  
 \<Konfigurace >  
\<system.net>  
\<settings>  
\<servicePointManager>  
  
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
|`checkCertificateName`|Určuje, zda systém měli ověřit, název certifikátu odpovídá názvu hostitele serveru před použitím certifikátu. Výchozí hodnota je `true`.|  
|`checkCertificateRevocationList`|Určuje, zda systém by měl kontrolovat, jestli certifikát byl odvolán. před použitím certifikátu. Výchozí hodnota je `false`.|  
|`dnsRefreshTimeout`|Určuje, jak dlouho služby DNS (Domain Name) jsou uložené v mezipaměti řešení ve spojení s parametrem kruhové dotazování DNS v milisekundách. Výchozí hodnota je 120 000 milisekund (dvě minuty).|  
|`enableDnsRoundRobin`|Určuje, zda rozlišení DNS hostitele názvy s více adres Internet Protocol (IP) vrácená všechny adresy, nebo jenom první shoda. Výchozí hodnota je `false`.|  
|`encryptionPolicy`|Určuje zásady šifrování použít relaci protokolu SSL/TLS na <xref:System.Net.ServicePointManager> instance. Možné hodnoty jsou ekvivalentem hodnoty <xref:System.Net.Security.EncryptionPolicy> výčtu. Použití <xref:System.Security.Authentication.CipherAlgorithmType.Null> se vyžaduje při šifrování zásady nastavíte `NoEncryption`. Výchozí hodnota je `RequireEncryption`.|  
|`expect100Continue`|Určuje, zda metody POST by měla by se měl zobrazit `100-continue` odpověď ze serveru. Výchozí hodnota je `true`.|  
|`useNagleAlgorithm`|Určuje, zda připojení řídí správce bodu služby používat Nagle algoritmus. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Prvek**|**Popis**|  
|-----------------|---------------------|  
|[Nastavení](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|Nakonfiguruje možnosti základní sítě pro <xref:System.Net> oboru názvů.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
