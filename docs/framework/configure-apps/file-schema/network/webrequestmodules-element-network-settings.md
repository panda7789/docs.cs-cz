---
title: '&lt;webRequestModules –&gt; – Element (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules
- http://schemas.microsoft.com/.NetConfiguration/v2.0#webRequestModules
helpviewer_keywords:
- webRequestModules element
- <webRequestModules> element
ms.assetid: 1263de11-3e0a-4f94-97c9-710b2ae53817
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 7454099d8af0f2d656296be55677c648cc0c36c9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32742689"
---
# <a name="ltwebrequestmodulesgt-element-network-settings"></a>&lt;webRequestModules –&gt; – Element (nastavení sítě)
Určuje moduly sloužící k požadavku na informace z hostitelů v síti.  
  
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
|[add](../../../../../docs/framework/configure-apps/file-schema/network/add-element-for-webrequestmodules-network-settings.md)|Přidá vlastní modul žádost webové aplikaci.|  
|[Zrušte zaškrtnutí](../../../../../docs/framework/configure-apps/file-schema/network/clear-element-for-webrequestmodules-network-settings.md)|Odebere všechny registrované moduly žádost webové aplikace.|  
|[remove](../../../../../docs/framework/configure-apps/file-schema/network/remove-element-for-webrequestmodules-network-settings.md)|Odebere vlastní modul žádost webové aplikaci.|  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[System.NET](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|Obsahuje nastavení, které určují, jak rozhraní .NET Framework připojí k síti.|  
  
## <a name="remarks"></a>Poznámky  
 `webRequestModules` Element zaregistruje následníků <xref:System.Net.WebRequest> třídy pro zpracování požadavků na informace na síti hostitele. Musí implementovat moduly webové žádosti <xref:System.Net.IWebRequestCreate> rozhraní.  
  
 Rozhraní .NET Framework obsahuje webové žádosti modulů pro identifikátory URI, který začíná http://, https:// a file://. Můžete přepsat výchozí moduly pouze tak, že zaregistrujete vlastní modul v konfiguračním souboru.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad zaregistruje výchozí modulu protokolu HTTP. Měli byste nahradit hodnoty verze a PublicKeyToken správné hodnoty pro zadaný modul.  
  
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
 <xref:System.Net.WebRequest>  
 <xref:System.Net.IWebRequestCreate>  
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
