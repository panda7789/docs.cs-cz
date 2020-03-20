---
title: <remove> – element pro webRequestModules (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/remove
- http://schemas.microsoft.com/.NetConfiguration/v2.0#remove
helpviewer_keywords:
- remove element, webRequestModules
- webRequestModules, remove element
- <remove> element, webRequestModules
- <webRequestModules>, remove element
ms.assetid: dd84d2fe-2f4f-457a-9d3c-441d0d21cc10
ms.openlocfilehash: afa1aef8ea71f43a136987ec5b6e1925c6d9fb40
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154722"
---
# <a name="remove-element-for-webrequestmodules-network-settings"></a>\<odebrat> element pro webRequestModules (Nastavení sítě)
Odebere z aplikace vlastní modul webového požadavku.  
  
[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<odebrat>**
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<remove
  prefix="URI prefix"
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Atribut**|**Popis**|  
|-------------------|---------------------|  
|`prefix`|Předpona identifikátoru URI pro požadavky zpracovávané tímto modulem webového požadavku.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Určuje moduly, které mají být používány k vyžádání informací od síťových hostitelů.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `remove` odebere registrovaný modul webového požadavku pro zadanou předponu URI.  
  
 Hodnota atributu `prefix` by měla být úvodníznaky platného identifikátoru`http`URI –`http://www.contoso.com`například " ", nebo " ".  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  

Následující příklad odebere existující modul webového požadavku pro protokol HTTP a poté zaregistruje nový vlastní modul webových požadavků pro požadavky HTTP. `www.contoso.com`
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <remove prefix="http">  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.WebRequest>
- [Schéma nastavení sítě](index.md)
