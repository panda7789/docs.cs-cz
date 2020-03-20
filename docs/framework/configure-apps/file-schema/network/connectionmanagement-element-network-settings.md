---
title: <connectionManagement> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/connectionManagement
- http://schemas.microsoft.com/.NetConfiguration/v2.0#connectionManagement
helpviewer_keywords:
- <connectionManagement> element
- connectionManagement element
ms.assetid: bedccaab-12a2-4511-8f67-e961f249aec6
ms.openlocfilehash: 9f1e382bbbaad2cb95e2c33bbbdfb4c505378c9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154891"
---
# <a name="connectionmanagement-element-network-settings"></a>\<connectionManagement> Element (Nastavení sítě)
Určuje maximální počet připojení k síťovému hostiteli.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionManagement>**

## <a name="syntax"></a>Syntaxe  
  
```xml  
<connectionManagement>
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Přidat](add-element-for-connectionmanagement-network-settings.md)|Přidá adresu IP nebo název DNS do seznamu správy připojení.|  
|[Jasné](clear-element-for-connectionmanagement-network-settings.md)|Vymaže seznam správy připojení.|  
|[Odebrat](remove-element-for-connectionmanagement-network-settings.md)|Odebere adresu IP nebo název DNS ze seznamu správy připojení.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak se rozhraní .NET Framework připojuje k síti.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `connectionManagement` definuje maximální počet připojení k serveru nebo skupině serverů.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad konfiguruje aplikaci tak, aby používala čtyři připojení k serveru `www.contoso.com` a dvě připojení ke všem ostatním serverům.  
  
```xml  
<configuration>  
  <system.net>  
    <connectionManagement>  
      <add address = "http://www.contoso.com" maxconnection = "4" />  
      <add address = "*" maxconnection = "2" />  
    </connectionManagement>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [Schéma nastavení sítě](index.md)
