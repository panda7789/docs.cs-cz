---
title: <module> – element (nastavení sítě)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#module
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/defaultProxy/module
helpviewer_keywords:
- module element
- <module> element
ms.assetid: 10318725-9666-4d65-ab61-b94c64e59f13
ms.openlocfilehash: 15f4d10a70dc3c6abd32869f5b7b0006a799b4bf
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698033"
---
# <a name="module-element-network-settings"></a>@no__t – element > 0module (nastavení sítě)
Přidá do aplikace nový modul proxy.  
  
[ **@no__t – 2configuration >** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **@no__t -4system. NET >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<defaultProxy >** ](defaultproxy-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<module >**  
  
## <a name="syntax"></a>Syntaxe  
  
```xml  
<module   
  type="type_fullname, assembly_fullname"   
/>  
```  
  
## <a name="attributes-and-elements"></a>Atributy a elementy  
 Následující části popisují atributy, podřízené prvky a nadřazené prvky.  
  
### <a name="attributes"></a>Atributy  
  
|**Atribut**|**Popis**|  
|-------------------|---------------------|  
|`type`|Plně kvalifikovaný název typu (uvedený vlastností <xref:System.Type.FullName%2A>) a název sestavení (s vlastností <xref:System.Reflection.Assembly.FullName%2A>), které jsou odděleny čárkou, která implementuje proxy server.|  
  
### <a name="child-elements"></a>Podřízené elementy  
 Žádné  
  
### <a name="parent-elements"></a>Nadřazené elementy  
  
|**Element**|**Popis**|  
|-----------------|---------------------|  
|[defaultProxy](defaultproxy-element-network-settings.md)|Nakonfiguruje proxy server protokolu HTTP (Hypertext Transfer Protocol).|  
  
## <a name="remarks"></a>Poznámky  
 Element `module` registruje proxy třídy, které implementují rozhraní <xref:System.Net.IWebProxy>. Po registraci proxy třídy je možné použít `module` k vyžádání informací prostřednictvím podporovaného proxy serveru.  
  
 Hodnota pro atribut `type` by měla být název třídy modulu a název odpovídající knihovny DLL (Dynamic Link Library).  
  
## <a name="configuration-files"></a>Konfigurační soubory  
 Tento element lze použít v konfiguračním souboru aplikace nebo v konfiguračním souboru počítače (Machine. config).  
  
## <a name="example"></a>Příklad  
 Následující příklad registruje vlastní třídu proxy serveru.  
  
```xml  
<configuration>  
  <system.net>  
    <defaultProxy>  
      <module  
        type="Test.CustomWebProxy, TestProxy, Version=2.0.3600.0, Culture=neutral, PublicKeyToken=b23a5c561934e385"  
      />  
    </defaultProxy>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Net.IWebProxy?displayProperty=nameWithType>
- [Schéma nastavení sítě](index.md)
