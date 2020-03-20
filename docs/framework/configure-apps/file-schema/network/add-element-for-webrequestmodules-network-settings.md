---
title: <add> – element pro webRequestModules (nastavení sítě)
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
ms.openlocfilehash: f4edce948033478aab59a2aff61abadc55a327ce
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79155021"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>\<přidat> element pro webRequestModules (Nastavení sítě)
Přidá do aplikace vlastní modul webového požadavku.  

[**\<>konfigurace**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<webRequestModules>**](webrequestmodules-element-network-settings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<přidat>**

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
|`prefix`|Předpona identifikátoru URI pro požadavky zpracovávané tímto modulem webového požadavku.|  
|`type`|Plně kvalifikovaný název typu (označený <xref:System.Type.FullName%2A> vlastností) a název sestavení <xref:System.Reflection.Assembly.FullName%2A> (označený vlastností), oddělený čárkou, který implementuje tento modul webového požadavku.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné.  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Určuje moduly, které mají být používány k vyžádání informací od síťových hostitelů.|  
  
## <a name="remarks"></a>Poznámky  
 Atribut `prefix` definuje předponu URI, která používá zadaný modul webového požadavku. Moduly webových požadavků jsou obvykle registrovány pro zpracování konkrétního protokolu, například PROTOKOLU HTTP nebo FTP, ale lze je zaregistrovat pro zpracování požadavku na konkrétní server nebo cestu na serveru.  
  
 Modul webového požadavku je vytvořen při předání metody <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType> odpovídající předponě identifikátoru URI.  
  
 Hodnota atributu `prefix` by měla být úvodníznaky platného identifikátoru URI. Příkladem je `http` nebo `http://www.contoso.com`.
  
 Hodnota atributu `type` by měla být platný název typu a odpovídající název sestavení oddělený čárkou.
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento prvek lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine.config).  
  
## <a name="example"></a>Příklad  
 Následující příklad registruje vlastní modul webového požadavku pro protokol HTTP. Hodnoty Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.  
  
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
- [Schéma nastavení sítě](index.md)
