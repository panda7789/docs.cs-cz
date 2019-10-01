---
title: <mailSettings> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#mailSettings
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/mailSettings
helpviewer_keywords:
- mailSettings element
- <mailSettings> element
ms.assetid: 54f0f153-17e5-4f49-afdc-deadb940c9c1
ms.openlocfilehash: fb4c8844ed3eb13af483c214d659090c0c563c33
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698081"
---
# <a name="mailsettings-element-network-settings"></a>@no__t – element > 0mailSettings (nastavení sítě)
Nakonfiguruje možnosti odesílání pošty.  

[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<mailSettings >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<mailSettings>
  <smtp>...</smtp>  
</mailSettings>
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|Atribut|Popis|  
|---------------|-----------------|  
|[@no__t – element > 1smtp (nastavení sítě)](smtp-element-network-settings.md)|Nakonfiguruje možnosti jednoduchého poštovního transportního protokolu.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[@no__t – element .NET > 1System (nastavení sítě)](system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.|  
  
## <a name="example"></a>Příklad  
 Následující příklad určuje vhodné parametry protokolu SMTP pro odesílání e-mailů s použitím výchozích síťových přihlašovacích údajů.  
  
```xml  
<configuration>  
  <system.net>  
    <mailSettings>  
      <smtp deliveryMethod="Network">  
        <network  
          host="localhost"  
          port="25"  
          defaultCredentials="true"  
        />  
      </smtp>  
    </mailSettings>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.Mail.SmtpClient>
- [Schéma nastavení sítě](index.md)
