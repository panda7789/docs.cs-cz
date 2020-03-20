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
ms.openlocfilehash: 093b68d31e03094bedefa96a2f2d53eb3d84edf0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155008"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a>\<přidat> Element pro connectionManagement (Nastavení sítě)
Přidá adresu IP nebo název DNS do seznamu správy připojení.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<connectionManagement>**](connectionmanagement-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**

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
|`address`|Řetězec popisující adresu IP nebo název DNS.|  
|`maxconnection`|Maximální počet připojení povolených na server. Pokud není zadán, výchozí hodnota je 2.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[connectionManagement](connectionmanagement-element-network-settings.md)|Určuje maximální počet připojení k síťovému hostiteli.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota atributu `address` by měla být hvězdičkou označující všechna připojení nebo `<schema>://<idn_hostname>[:<port>]`řetězcem formuláře .  
  
 Pokud identifikátor URI předaný libovolným chybám HTTP obsahuje kódování Unicode, bude název převeden interně pomocí <xref:System.Uri.DnsSafeHost%2A> který může vrátit řetězec punicode (chování závislé na aktuální konfiguraci IDN).  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad konfiguruje aplikaci tak, aby používala čtyři připojení k serveru `www.contoso.com` a dvě připojení ke všem ostatním serverům.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [Schéma nastavení sítě](index.md)
