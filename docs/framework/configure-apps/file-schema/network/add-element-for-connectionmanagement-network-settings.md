---
title: <add> – element pro connectionManagement (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement/add
helpviewer_keywords:
- <add> element, connectionManagement
- <connectionManagement>, add element
- add element, connectionManagement
- connectionManagement, add element
ms.assetid: 856bf57d-1c63-46c7-a178-03d97b0a4149
ms.openlocfilehash: 608c591b910252dd60950bf2aa7565d6df04d5fc
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/21/2019
ms.locfileid: "69664233"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a>\<Přidat > element pro connectionManagement (nastavení sítě)
Přidá IP adresu nebo název DNS do seznamu správy připojení.  
  
 \<> Konfigurace  
\<system.net>  
\<connectionManagement >  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add   
  address="address expression"   
  maxconnection="integer"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Atribut**|**Popis**|  
|-------------------|---------------------|  
|`address`|Řetězec popisující IP adresu nebo název DNS.|  
|`maxconnection`|Maximální počet připojení povolených pro server. Pokud není zadaný, použije se výchozí hodnota 2.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|Určuje maximální počet připojení k síťovému hostiteli.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `address` atributu musí být buď hvězdička, která označuje všechna připojení, nebo řetězec formuláře `<schema>://<idn_hostname>[:<port>]`.  
  
 Pokud identifikátor URI předaný do libovolného rozhraní API http obsahuje Unicode, název se převede interně <xref:System.Uri.DnsSafeHost%2A> pomocí toho, který může vracet punicode řetězec (chování závisí na aktuální konfiguraci IDN).  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 Následující příklad nakonfiguruje aplikaci tak, aby používala čtyři připojení k `www.contoso.com` serveru a dvě připojení ke všem ostatním serverům.  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address="http://www.contoso.com" maxconnection="4" />  
      <add address="*" maxconnection="2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [Schéma nastavení sítě](index.md)
