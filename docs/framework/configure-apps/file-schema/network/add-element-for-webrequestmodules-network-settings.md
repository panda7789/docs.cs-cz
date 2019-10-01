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
ms.openlocfilehash: 0248706ed78de160ef0131a0c7595374febf1aa9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71699578"
---
# <a name="add-element-for-webrequestmodules-network-settings"></a>@no__t – element > 0add pro webRequestModules (nastavení sítě)
Přidá do aplikace vlastní modul webové žádosti.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<webRequestModules >** ](webrequestmodules-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<add >**  
  
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
|`type`|Plně kvalifikovaný název typu (uvedený vlastností <xref:System.Type.FullName%2A>) a název sestavení (s vlastností <xref:System.Reflection.Assembly.FullName%2A>), které jsou odděleny čárkou, která implementuje tento modul webové žádosti.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[webRequestModules](webrequestmodules-element-network-settings.md)|Určuje moduly, které se použijí k vyžádání informací od hostitelů v síti.|  
  
## <a name="remarks"></a>Poznámky  
 Atribut `prefix` definuje předponu identifikátoru URI, která používá zadaný modul webové žádosti. Moduly webových požadavků jsou obvykle registrovány pro zpracování konkrétního protokolu, například HTTP nebo FTP, ale mohou být registrovány pro zpracování požadavku na konkrétní server nebo cestu na serveru.  
  
 Modul webové žádosti se vytvoří, když je předpona odpovídajícího identifikátoru URI předána metodě <xref:System.Net.WebRequest.Create%2A?displayProperty=nameWithType>.  
  
 Hodnota atributu `prefix` by měla být předními znaky platného identifikátoru URI. Například `http` nebo `http://www.contoso.com`.
  
 Hodnota pro atribut `type` by měla být platný název typu a odpovídající název sestavení oddělený čárkou.
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 Následující příklad registruje vlastní modul webové žádosti pro protokol HTTP. Hodnoty pro Version a PublicKeyToken byste měli nahradit správnými hodnotami pro zadaný modul.  
  
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
- [Schéma nastavení sítě](index.md)
