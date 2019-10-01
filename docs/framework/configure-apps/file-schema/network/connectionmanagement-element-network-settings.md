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
ms.openlocfilehash: d377a77a4a1b4c57e9edd4fbfa364387f1bae479
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699432"
---
# <a name="connectionmanagement-element-network-settings"></a>@no__t – element > 0connectionManagement (nastavení sítě)
Určuje maximální počet připojení k síťovému hostiteli.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<connectionManagement >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<connectionManagement>   
</connectionManagement>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[add](add-element-for-connectionmanagement-network-settings.md)|Přidá IP adresu nebo název DNS do seznamu správy připojení.|  
|[jejich](clear-element-for-connectionmanagement-network-settings.md)|Vymaže seznam správy připojení.|  
|[remove](remove-element-for-connectionmanagement-network-settings.md)|Odebere IP adresu nebo název DNS ze seznamu správy připojení.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.|  
  
## <a name="remarks"></a>Poznámky  
 Element `connectionManagement` definuje maximální počet připojení k serveru nebo skupině serverů.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je nakonfiguruje aplikace tak, aby na všech ostatních serverech používala čtyři připojení k serveru `www.contoso.com` a dvě připojení.  
  
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
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.ServicePoint>
- <xref:System.Net.ServicePointManager>
- [Schéma nastavení sítě](index.md)
