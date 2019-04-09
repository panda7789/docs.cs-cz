---
title: <add> – Element pro webRequestModules (nastavení sítě)
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
ms.openlocfilehash: 4c1116c088c12ad3859714c8d75704d0156c12f7
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188236"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>\<Přidat > – Element pro webRequestModules (nastavení sítě)
Přidá vlastní modul webové žádosti do aplikace.  
  
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
|`prefix`|Předponu identifikátoru URI pro žádosti zpracovat tento modul webové žádosti.|  
|`type`|Plně kvalifikovaného názvu (indikován <xref:System.Type.FullName%2A> vlastnost) a název sestavení (indikován <xref:System.Reflection.Assembly.FullName%2A> vlastnost), oddělená čárkou, která implementuje tento modul webové žádosti.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Prvek**|**Popis**|  
|-----------------|---------------------|  
|[webRequestModules](../../../../../docs/framework/configure-apps/file-schema/network/webrequestmodules-element-network-settings.md)|Určuje moduly, které použijte k vyžádání informace z hostitelů v síti.|  
  
## <a name="remarks"></a>Poznámky  
 `prefix` Atribut definuje předponu identifikátoru URI, který používá zadaný modul webové žádosti. Webové žádosti moduly jsou běžně registrovány pro zpracování konkrétní protokolu, jako je například HTTP nebo FTP, ale může být registrován pro obsluhu žádost pro konkrétní server nebo cesta na serveru.  
  
 Webový požadavek modul se vytvoří při odpovídající předpony identifikátoru URI je předán <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> metody.  
  
 Hodnota `prefix` atribut by měl mít počáteční znaky platný identifikátor URI. Například `http` nebo `http://www.contoso.com`.
  
 Hodnota `type` atribut by měl být platný název typu a odpovídající název sestavení, oddělených čárkami.
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo konfiguračního souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad registruje vlastní modul webového požadavku pro protokol HTTP. Měli byste nahradit hodnoty pro verzi a PublicKeyToken správné hodnoty pro zadaný modul.  
  
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
- [Schéma nastavení sítě](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
