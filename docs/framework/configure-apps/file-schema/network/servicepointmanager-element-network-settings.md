---
title: <servicePointManager> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: 95ad1880cbb832a17311e7e63e9203f53257f65f
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697718"
---
# <a name="servicepointmanager-element-network-settings"></a>@no__t – element > 0servicePointManager (nastavení sítě)
Nakonfiguruje připojení k síťovým prostředkům.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<settings >** ](settings-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<servicePointManager >**  
  
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
|`checkCertificateName`|Určuje, zda má systém před použitím certifikátu ověřit, zda název certifikátu odpovídá názvu hostitele serveru. Výchozí hodnota je `true`.|  
|`checkCertificateRevocationList`|Určuje, zda má systém před použitím certifikátu ověřit, zda byl certifikát odvolán. Výchozí hodnota je `false`.|  
|`dnsRefreshTimeout`|Určuje, jak dlouho se překlad služby DNS (Domain Name Service) ukládá do mezipaměti v kombinaci s možností kruhové dotazování DNS (v milisekundách). Výchozí hodnota je 120 000 milisekund (dvě minuty).|  
|`enableDnsRoundRobin`|Určuje, jestli překlad DNS názvů hostitelů s více adresami Internet Protocol (IP) vrací všechny adresy, nebo jenom první z nich. Výchozí hodnota je `false`.|  
|`encryptionPolicy`|Určuje zásady šifrování použité pro relaci SSL/TLS na instanci <xref:System.Net.ServicePointManager>. Možné hodnoty jsou ekvivalentní hodnotám pro výčet <xref:System.Net.Security.EncryptionPolicy>. Je-li zásada šifrování nastavena na hodnotu `NoEncryption`, je nutné použít <xref:System.Security.Authentication.CipherAlgorithmType.Null>. Výchozí hodnota je `RequireEncryption`.|  
|`expect100Continue`|Určuje, zda mají metody POST očekávat přijetí odpovědi `100-continue` ze serveru. Výchozí hodnota je `true`.|  
|`useNagleAlgorithm`|Určuje, jestli připojení řízená správcem servisního bodu používají algoritmus Nagle. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Nastavení](settings-element-network-settings.md)|Konfiguruje základní možnosti sítě pro obor názvů <xref:System.Net>.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [Schéma nastavení sítě](index.md)
