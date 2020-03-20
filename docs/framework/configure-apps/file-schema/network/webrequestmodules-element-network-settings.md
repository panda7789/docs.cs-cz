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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79154540"
---
# <a name="webrequestmodules-element-network-settings"></a>\<webRequestModules> Element (nastavení sítě)
Určuje moduly, které mají být používány k vyžádání informací od síťových hostitelů.  
  
[**\<>konfigurace**](../configuration-element.md)  
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
 Žádné.  
  
### <a name="child-elements"></a>Podřízené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[Přidat](add-element-for-webrequestmodules-network-settings.md)|Přidá do aplikace vlastní modul webového požadavku.|  
|[Jasné](clear-element-for-webrequestmodules-network-settings.md)|Odebere z aplikace všechny registrované moduly webových požadavků.|  
|[Odebrat](remove-element-for-webrequestmodules-network-settings.md)|Odebere z aplikace vlastní modul webového požadavku.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[system.net](system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak se rozhraní .NET Framework připojuje k síti.|  
  
## <a name="remarks"></a>Poznámky  
 Prvek `webRequestModules` registruje následníky <xref:System.Net.WebRequest> třídy pro zpracování požadavků na informace pro síťové hostitele. Moduly webových požadavků <xref:System.Net.IWebRequestCreate> musí implementovat rozhraní.  
  
 Rozhraní .NET Framework obsahuje moduly webových `http://`požadavků `https://`pro `file://`identifikátory URI, které začínají na rozhraní , a . Výchozí moduly můžete přepsat pouze registrací vlastního modulu v konfiguračním souboru.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad registruje výchozí modul HTTP. Hodnoty Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.  
  
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
