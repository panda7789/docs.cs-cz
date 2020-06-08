---
title: <servicePointManager> – element (nastavení sítě)
description: <servicePointManager>Prvek nastavení sítě konfiguruje připojení k možnostem síťových prostředků v .NET Framework.
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#servicePointManager
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/servicePointManager
helpviewer_keywords:
- servicePointManager element
- <servicePointManager> element
ms.assetid: 6e5def51-3646-4ef6-a7bd-c69151321bec
ms.openlocfilehash: eb27716ec7c2936f32a7e4d4c983d1e175c4d044
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504521"
---
# <a name="servicepointmanager-element-network-settings"></a>\<servicePointManager> – element (nastavení sítě)
Nakonfiguruje připojení k síťovým prostředkům.  

[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<settings>**](settings-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<servicePointManager>**

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
|`encryptionPolicy`|Určuje zásady šifrování použité pro relaci SSL/TLS na <xref:System.Net.ServicePointManager> instanci. Možné hodnoty jsou ekvivalentní hodnotám pro <xref:System.Net.Security.EncryptionPolicy> výčet. <xref:System.Security.Authentication.CipherAlgorithmType.Null>Pokud je zásada šifrování nastavena na hodnotu, použití je povinné `NoEncryption` . Výchozí hodnota je `RequireEncryption`.|  
|`expect100Continue`|Určuje, zda by metody POST měly očekávat `100-continue` odpověď ze serveru. Výchozí hodnota je `true`.|  
|`useNagleAlgorithm`|Určuje, jestli připojení řízená správcem servisního bodu používají algoritmus Nagle. Výchozí hodnota je `true`.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Objekt**|**Popis**|  
|-----------------|---------------------|  
|[Nastavení](settings-element-network-settings.md)|Nakonfiguruje základní možnosti sítě pro <xref:System.Net> obor názvů.|  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.ServicePointManager>
- <xref:System.Net.Security.EncryptionPolicy>
- [Schéma nastavení sítě](index.md)
