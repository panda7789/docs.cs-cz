---
title: <webRequestModules> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: e119d9ce1f8bb6f07f8050612550db459a2f065c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697466"
---
# <a name="webrequestmodules-element-network-settings"></a>\<element > webRequestModules (nastavení sítě)
Určuje moduly, které se použijí k vyžádání informací od hostitelů v síti.  
  
[**Konfigurace \<>** ](../configuration-element.md)  
&nbsp;&nbsp;[ **\<System. NET >** ](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules >  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webRequestModules>   
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[add](add-element-for-webrequestmodules-network-settings.md)|Přidá do aplikace vlastní modul webové žádosti.|  
|[jejich](clear-element-for-webrequestmodules-network-settings.md)|Odebere z aplikace všechny registrované moduly webových požadavků.|  
|[remove](remove-element-for-webrequestmodules-network-settings.md)|Odebere z aplikace vlastní modul webové žádosti.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.|  
  
## <a name="remarks"></a>Poznámky  
 Element `webRequestModules` registruje následníky <xref:System.Net.WebRequest> třídy za účelem zpracování žádostí o informace na síťové hostitele. Moduly webových požadavků musí implementovat rozhraní <xref:System.Net.IWebRequestCreate>.  
  
 .NET Framework obsahuje moduly webových požadavků pro identifikátory URI, které začínají `http://`, `https://`a `file://`. Výchozí moduly můžete přepsat pouze tím, že do konfiguračního souboru zaregistrujete vlastní modul.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 Následující příklad registruje výchozí modul HTTP. Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.  
  
```xml  
<configuration>  
  <system.net>  
    <webRequestModules>  
      <add prefix="http"  
           type="System.Net.HttpRequestCreator, System, Version=2.0.3600.0,  
           Culture=neutral, PublicKeyToken=b77a5c561934e089"  
      />  
    </webRequestModules>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [Schéma nastavení sítě](index.md)
