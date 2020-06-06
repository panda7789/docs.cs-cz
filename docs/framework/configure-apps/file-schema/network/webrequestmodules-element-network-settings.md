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
ms.openlocfilehash: 7f2805283f89e6165d336b3e593d34054e02115d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/06/2020
ms.locfileid: "79154540"
---
# <a name="webrequestmodules-element-network-settings"></a>\<webRequestModules> – element (nastavení sítě)
Určuje moduly, které se použijí k vyžádání informací od hostitelů v síti.  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;\<webRequestModules>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<webRequestModules>
</webRequestModules>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
 Žádné  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Objekt**|**Popis**|  
|-----------------|---------------------|  
|[add](add-element-for-webrequestmodules-network-settings.md)|Přidá do aplikace vlastní modul webové žádosti.|  
|[jejich](clear-element-for-webrequestmodules-network-settings.md)|Odebere z aplikace všechny registrované moduly webových požadavků.|  
|[odebrány](remove-element-for-webrequestmodules-network-settings.md)|Odebere z aplikace vlastní modul webové žádosti.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Objekt**|**Popis**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak se .NET Framework připojí k síti.|  
  
## <a name="remarks"></a>Poznámky  
 `webRequestModules`Element registruje následníky <xref:System.Net.WebRequest> třídy pro zpracování žádostí o informace na síťové hostitele. Moduly webových požadavků musí implementovat <xref:System.Net.IWebRequestCreate> rozhraní.  
  
 .NET Framework obsahuje moduly webových požadavků pro identifikátory URI, které začínají `http://` na, `https://` a `file://` . Výchozí moduly můžete přepsat pouze tím, že do konfiguračního souboru zaregistrujete vlastní modul.  
  
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
  
## <a name="see-also"></a>Viz také

- <xref:System.Net.WebRequest>
- <xref:System.Net.IWebRequestCreate>
- [Schéma nastavení sítě](index.md)
