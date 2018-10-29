---
title: '&lt;Element webRequestModules&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
ms.openlocfilehash: 1d421009e8b2e0d4074679939092180c6037a0c7
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/28/2018
ms.locfileid: "50200441"
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a>&lt;Element webRequestModules&gt; – Element (nastavení sítě)
Určuje moduly, které použijte k vyžádání informace z hostitelů v síti.  
  
 \<Konfigurace >  
\<system.net>  
\<webRequestModules>  
  
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
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|Přidá vlastní modul webové žádosti do aplikace.|  
|[Vymazat](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|Odebere všechny registrované moduly webové žádosti z aplikace.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|Vlastní modul požadavku webového odstraní z aplikace.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Obsahuje nastavení, která určují, jak rozhraní .NET Framework připojí k síti.|  
  
## <a name="remarks"></a>Poznámky  
 `webRequestModules` Zaregistruje následníky elementu <xref:System.Net.WebRequest> třídy pro zpracování požadavků na informace na síť hostitele. Musí implementovat moduly webové žádosti <xref:System.Net.IWebRequestCreate> rozhraní.  
  
 Rozhraní .NET Framework zahrnuje webové žádosti moduly pro identifikátory URI, které začínají `http://`, `https://`, a `file://`. Moduly, ve výchozím nastavení můžete přepsat jenom, když si zaregistrujete vlastní modul v konfiguračním souboru.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad registruje výchozí modul HTTP. Měli byste nahradit hodnoty pro verzi a PublicKeyToken správné hodnoty pro zadaný modul.  
  
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
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
