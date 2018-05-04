---
title: '&lt;Přidat&gt; Element pro webRequestModules – (nastavení sítě)'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/webRequestModules/add
- http://schemas.microsoft.com/.NetConfiguration/v2.0#add
helpviewer_keywords:
- <webRequestModules>, add element
- webRequestModules, add element
- add element, webRequestModules
- <add> element, webRequestModules
ms.assetid: 47ec4adc-f39f-4bcd-8680-1ec21fd26890
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 921f5f2bfda1a19d022d3f3f4131e3653fd17ea7
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-element-for-webrequestmodules-network-settings"></a>&lt;Přidat&gt; Element pro webRequestModules – (nastavení sítě)
Přidá vlastní modul žádost webové aplikaci.  
  
 \<Konfigurace >  
\<system.net>  
\<webRequestModules>  
\<add>  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<add   
  prefix="URI prefix"   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Atribut**|**Popis**|  
|-------------------|---------------------|  
|`prefix`|Předpony identifikátoru URI pro tento webový modul požadavek zpracovává požadavky.|  
|`type`|Plně kvalifikovaného názvu (indikován <xref:System.Type.FullName%2A> vlastnosti) a název sestavení (indikován <xref:System.Reflection.Assembly.FullName%2A> vlastnost), oddělené čárkou, který implementuje tento modul webové žádosti.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Určuje moduly sloužící k požadavku na informace z hostitelů v síti.|  
  
## <a name="remarks"></a>Poznámky  
 `prefix` Atribut definuje předpony identifikátoru URI, který používá zadaný modul webové žádosti. Webové žádosti moduly jsou běžně registrovány pro zpracování určitého protokolu, jako je například HTTP nebo FTP, ale lze zaregistrovat pro zpracování požadavku na konkrétní server nebo k adresáři na serveru.  
  
 Modul webové žádosti se vytvoří při porovnávání předpony identifikátoru URI je předána <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metoda.  
  
 Hodnota `prefix` atribut by měl mít počáteční znaky platný identifikátor URI – například "http", nebo "http://www.contoso.com".  
  
 Hodnota `type` atribut by měl mít název platného typu a odpovídající název sestavení, oddělených čárkou.  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad zaregistruje vlastní modul webové žádosti HTTP. Měli byste nahradit hodnoty verze a PublicKeyToken správné hodnoty pro zadaný modul.  
  
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
 [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
