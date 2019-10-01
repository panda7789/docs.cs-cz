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
ms.openlocfilehash: 3742a040e8c16c38e495a0fd886c4c1f23780758
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698385"
---
# <a name="add-element-for-connectionmanagement-network-settings"></a>@no__t – element > 0add pro connectionManagement (nastavení sítě)
Přidá IP adresu nebo název DNS do seznamu správy připojení.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<connectionManagement >** ](connectionmanagement-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**  
  
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
 Hodnota atributu `address` by měla být buď hvězdička, která označuje všechna připojení, nebo řetězec formuláře `<schema>://<idn_hostname>[:<port>]`.  
  
 Pokud identifikátor URI předaný do libovolného rozhraní API HTTP obsahuje Unicode, název se převede interně pomocí <xref:System.Uri.DnsSafeHost%2A>, což může vracet punicode řetězec (chování závisí na aktuální konfiguraci IDN).  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je nakonfiguruje aplikace tak, aby na všech ostatních serverech používala čtyři připojení k serveru `www.contoso.com` a dvě připojení.  
  
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
