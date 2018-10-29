---
title: '&lt;Přidat&gt; – Element pro connectionManagement (nastavení sítě)'
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
ms.openlocfilehash: a3b8de254c28aedc21df5baf54bd67527e35b7f9
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50201290"
---
# <a name="ltaddgt-element-for-connectionmanagement-network-settings"></a>&lt;Přidat&gt; – Element pro connectionManagement (nastavení sítě)
Přidá do seznamu pro správu připojení IP adresu nebo název DNS.  
  
 \<Konfigurace >  
\<system.net>  
\<connectionManagement – >  
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
|`address`|Řetězec, který popisuje IP adresu nebo název DNS.|  
|`maxconnection`|Maximální počet povolených připojení k serveru. Pokud není zadán, výchozí hodnota je 2.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[connectionManagement –](../../../../../docs/framework/configure-apps/file-schema/network/connectionmanagement-element-network-settings.md)|Určuje maximální počet připojení k síti hostitele.|  
  
## <a name="remarks"></a>Poznámky  
 Hodnota `address` atribut by měl mít hvězdičky označující všechna připojení nebo řetězec ve formě `<schema>://<idn_hostname>[:<port>]`.  
  
 Pokud identifikátor URI předána žádná rozhraní HTTP API obsahuje kódování Unicode, název se převedou interně pomocí <xref:System.Uri.DnsSafeHost%2A> které může vrátit řetězec punicode (chování závisí na aktuální konfiguraci IDN).  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad nastaví použití čtyř připojení k serveru aplikace `www.contoso.com` a dvě spojení na všechny ostatní servery.  
  
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
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
